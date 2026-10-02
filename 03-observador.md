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

| Elemento | Pendiente del informe |
| --- | --- |
| Ganancia `L` | Incluir valor final |
| Polos de error | Mostrar ubicación computada |
| Estabilidad | Verificar convergencia del error |
| Inicialización `x̂` | Describir la condición inicial |

## 4. Validación del observador

La validación debe realizarse comparando cada estado real y su estimación. Los resultados más relevantes son:

- error de estimación por estado,
- rapidez de convergencia,
- estabilidad bajo cambios de referencia,
- comportamiento ante ruido y perturbaciones.

En este punto se incluirán las gráficas superpuestas para cada estado y el análisis del error respecto al comportamiento real del sistema.

<div class="report-figure">
  <div class="img-placeholder">
    <span>Imagen 5<br>Gráficas comparando estados reales y estimados</span>
  </div>
  <p class="report-figure__caption">Figura 5. Estados reales frente a estimaciones del observador.</p>
</div>

## 5. Resultados y discusión

La discusión debe centrarse en la relación entre las métricas de control y la capacidad del observador para reconstruir las variables faltantes. Se debe analizar si la estimación es suficientemente precisa para alimentar la ley de control LQR, así como la sensibilidad del sistema al ruido y a la incertidumbre del modelo.

## 6. Conclusión

El observador de estados es necesario para estimar variables no medidas y, en particular, para proporcionar a la ley de control una información más completa del sistema. La clave del diseño es garantizar que el error de estimación converja de manera estable y con rapidez suficiente para no degradar el desempeño del sistema real.
