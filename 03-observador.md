---
layout: default
title: Observador de estados
nav_order: 4
---

# Segunda parte de la evaluación: Observador de Estados

## 1. Objetivo

A diferencia de un sensor físico adicional, el observador utiliza el modelo matemático y las salidas medidas para reconstruir las variables de estado no disponibles directamente.

En esta implementación, el observador estima los estados a partir de la salida medida y entrega esas estimaciones a la ley de control LQR. La arquitectura integrada con la planta se muestra en las figuras de esta página.

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

La ganancia `L` determina la rapidez y estabilidad de la convergencia del error. Su cálculo, los polos resultantes y las condiciones de inicialización del observador Aero 2 se presentan en [Integración y evidencia]({{ '/04-resultados-entrega/' | relative_url }}).

## 4. Validación del observador

La evaluación compara los estados de la planta con sus estimaciones y considera el error, la convergencia y la respuesta ante cambios de referencia. Las gráficas y el análisis se presentan en [Integración y evidencia]({{ '/04-resultados-entrega/' | relative_url }}).

<div class="report-figure">
  <img src="{{ '/assets/css/imag/observador.png' | relative_url }}" alt="Diagrama del observador de estados implementado" class="report-figure__image">
  <p class="report-figure__caption">Figura 5. Diagrama del observador de estados implementado.</p>
</div>

<div class="report-figure">
  <img src="{{ '/assets/css/imag/observador_diagrama.png' | relative_url }}" alt="Implementación integrada de la planta Quanser y el observador de estados" class="report-figure__image">
  <p class="report-figure__caption">Figura 6. Integración del observador de estados con la planta Quanser.</p>
</div>
