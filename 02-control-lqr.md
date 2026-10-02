---
layout: default
title: Control LQR
nav_order: 3
---

# Primera parte de la evaluación: Control LQR

## 1. Objetivo

El algoritmo del Regulador Cuadrático Lineal (LQR) calculará una ley de control `u` que minimice el criterio de desempeño o función de costo, utilizando matrices de ponderación (`Q` y `R`) para equilibrar el error de seguimiento de las variables de estado y la agresividad del esfuerzo de control de los motores.

Para el equipo A, la plataforma es el Quanser Aero 2, un helicóptero de 2 grados de libertad (2 DOF). El objetivo del controlador será regular los ángulos de cabeceo (pitch) y guiñada (yaw) hacia un conjunto de referencias deseadas.

## 2. Estructura del problema

La formulación en espacio de estados corresponde a:

```text
ẋ = A x + B u
y = C x + D u
```

donde el vector de estado y las entradas son los definidos previamente para el Aero 2. El objetivo es encontrar una ganancia `K` tal que la ley de retroalimentación:

```text
u = -Kx
```

genere un comportamiento estable y con un desempeño aceptable frente a las referencias y perturbaciones esperadas.

## 3. Función de costo y ponderaciones

La lógica del LQR está basada en la minimización del criterio:

```text
J = ∫ (xᵀQx + uᵀRu) dt
```

Donde:

- `Q` pondera el error de estado,
- `R` pondera la agresividad del control.

El diseño debe equilibrar la velocidad de respuesta con el esfuerzo de los motores. En la práctica, se debe justificar la elección de las matrices `Q` y `R` según la escala de cada variable y la exigencia del desempeño deseado.

## 4. Cálculo de la ganancia K

La ganancia del regulador se obtiene resolviendo la ecuación algebraica de Riccati:

```text
AᵀP + PA - PBR⁻¹BᵀP + Q = 0
```

y luego:

```text
K = R⁻¹BᵀP
```

La matriz `K` es la que define la retroalimentación de estados. En la sección final, se debe documentar el valor concreto obtenido, así como la comprobación del lazo cerrado y la estabilidad del sistema.

<div class="report-figure">
  <img src="{{ '/assets/css/imag/modelo_LQR.png' | relative_url }}" alt="Diagrama del lazo de control LQR aplicado al Aero 2" class="report-figure__image">
  <p class="report-figure__caption">Figura 3. Estructura del regulador LQR y posición de los polos en lazo cerrado.</p>
</div>

## 5. Diseño y ajuste práctico

El proceso se desarrolla en varias etapas:

1. Se usa el modelo linealizado y sus parámetros nominales.
2. Se eligen `Q` y `R` según la prioridad de cada estado y la limitación de actuación.
3. Se resuelve el problema de Riccati para obtener `K`.
4. Se validan la estabilidad, el error y la actuación de los motores.
5. Se analiza la influencia de la saturación de voltaje y la diferencia con la planta real.

| Aspecto | Resultado esperado |
| --- | --- |
| Matriz `Q` | Ponderación de errores de estado |
| Matriz `R` | Ponderación del esfuerzo de control |
| Ganancia `K` | Valor final obtenido del LQR |
| Polos del lazo cerrado | Verificación de estabilidad |
| Saturación | Tratamiento de límites físicos |

## 6. Resultados esperados

La validación del control debe incluir, como mínimo, las gráficas de:

- referencia versus respuesta de `θp` y `θy`,
- señales de entrada `Vp` y `Vy`,
- comparación de desempeño para distintas condiciones iniciales o referencias.

| Prueba | Referencia `(θp, θy)` | Condición inicial | Resultado esperado |
| --- | --- | --- | --- |
| Simulación nominal | Valor de referencia | Condición inicial del sistema | Respuesta del lazo cerrado |
| Variación de parámetros | Valor de referencia | Condición inicial del sistema | Comportamiento con parámetros modificados |
| Prueba de laboratorio | Valor de referencia | Condición inicial del sistema | Respuesta de la planta real |

<div class="report-figure">
  <img src="{{ '/assets/css/imag/observador_diagrama.png' | relative_url }}" alt="Diagrama del sistema con control LQR, observación y retroalimentación" class="report-figure__image">
  <p class="report-figure__caption">Figura 4. Respuesta del sistema en lazo cerrado y esfuerzo de control.</p>
</div>

## 7. Conclusión

El regulador LQR permite equilibrar precisión y esfuerzo de control para la plataforma Aero 2. El diseño final debe justificar ordenadamente la elección de ponderaciones y la ganancia obtenida, además de discutir la comparación entre la simulación y la planta física en laboratorio.
