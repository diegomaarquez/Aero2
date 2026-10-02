---
layout: default
title: Observador de estados
nav_order: 4
---

# Segunda parte de la evaluación: Observador de Estados

## 1. Objetivo

A diferencia de un sensor físico que puede estar sujeto a fallos o altos niveles de ruido, las técnicas de estimación de estados permiten utilizar el modelo matemático del sistema para reconstruir las variables de interés. En esta segunda fase, el estudiantado debe implementar un observador de estados acoplado a la salida medida de la planta.

El observador debe estimar las variables no medidas y, en la medida de lo posible, evaluar perturbaciones del sistema en tiempo real. Para este proyecto, el observador no recibe la información del comando, sino que solo estima los estados para ser usados por la ley de control LQR.

## 2. Arquitectura del observador

El observador se acopla a la salida medida de la planta, como se indica en el diagrama del proyecto. La forma general de este observador es:

```text
x̂̇ = A x̂ + B u + L (y − C x̂)
```

donde:

- `x̂` es el vector estimado de estados,
- `u` es la entrada conocida,
- `y` es la salida medida,
- `L` es la matriz de ganancias del observador.

La dinámica del error de estimación se obtiene como:

```text
ė = (A − LC)e
```

Esto muestra claramente que el diseño del observador depende de la ubicación de los polos del sistema `A − LC`. La estabilidad del error resulta garantizada si estos polos tienen parte real negativa.

## 3. Diseño de la ganancia del observador

La ganancia `L` debe elegirse de forma que la convergencia del error sea rápida y estable. En la práctica, esto se hace mediante la ubicación de polos o mediante una sintonización basada en una estimación de la respuesta dinámica del sistema.

Se debe documentar:

- matriz `L` obtenida,
- criterio de diseño,
- polos del error,
- condiciones de inicialización del observador.

### Polinomio característico y selección de coeficientes

Para la realización de tercer orden usada en el cálculo, el polinomio característico se obtiene de `det(sI - A)`. Las matrices `B` y `C` se incluyen como en el código original; el determinante característico depende de `A`.

```matlab
syms s l beta m

A = [0 1 0;
    -l 0 m;
    -1 0 beta];

B = [0; l; 1];
C = [1 0 0];

% characteristic polynomial (expanded)
pc = collect(det(s*eye(size(A)) - A), s)
```

La expansión es `pc = s^3 - beta*s^2 + l*s - l*beta + m`. Si se desean tres polos en `-p`, se iguala con `(s + p)^3`. El cálculo de coeficientes queda:

```matlab
p = 100;
pol_des = expand((s + p)^3);

eq1 = -beta == 3*p;
eq2 = l == 3*p^2;
eq3 = -l*beta + m == p^3;

solucion = solve([eq1, eq2, eq3], [beta, l, m]);
beta = double(solucion.beta)
l = double(solucion.l)
m = double(solucion.m)
```

Para `p = 100`, el polinomio deseado es `s^3 + 300s^2 + 30000s + 1000000` y los coeficientes son `beta = -300`, `l = 30000` y `m = -8000000`. Estos valores corresponden a la matriz auxiliar `A` de tercer orden mostrada aquí; no son la matriz de ganancias `L` del observador de cuarto orden del modelo Aero 2. Para obtener `L` se necesita formular y resolver la asignación de polos de `A_modelo - L*C`.

| Elemento | Descripción |
| --- | --- |
| Ganancia `L` | Valor final del observador |
| Polos de error | Ubicación computada del error de estimación |
| Estabilidad | Verificación de la convergencia del error |
| Inicialización `x̂` | Condición inicial de la estimación |

## 4. Validación del observador

La validación debe realizarse comparando cada estado real y su estimación. Los resultados más relevantes son:

- error de estimación por estado,
- rapidez de convergencia,
- estabilidad bajo cambios de referencia,
- comportamiento ante ruido y perturbaciones.

En este punto se incluirán las gráficas superpuestas para cada estado y el análisis del error respecto al comportamiento real del sistema.

<div class="report-figure">
  <img src="{{ '/assets/css/imag/observador.png' | relative_url }}" alt="Diagrama del observador de estados implementado" class="report-figure__image">
  <p class="report-figure__caption">Figura 5. Diagrama del observador de estados implementado.</p>
</div>

<div class="report-figure">
  <img src="{{ '/assets/css/imag/observador_diagrama.png' | relative_url }}" alt="Implementación integrada de la planta Quanser y el observador de estados" class="report-figure__image">
  <p class="report-figure__caption">Figura 6. Integración del observador de estados con la planta Quanser.</p>
</div>

## 5. Resultados y discusión

La discusión debe centrarse en la relación entre las métricas de control y la capacidad del observador para reconstruir las variables faltantes. Se debe analizar si la estimación es suficientemente precisa para alimentar la ley de control LQR, así como la sensibilidad del sistema al ruido y a la incertidumbre del modelo.

## 6. Conclusión

El observador de estados es necesario para estimar variables no medidas y, en particular, para proporcionar a la ley de control una información más completa del sistema. La clave del diseño es garantizar que el error de estimación converja de manera estable y con rapidez suficiente para no degradar el desempeño del sistema real.
