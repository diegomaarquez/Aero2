---
layout: default
title: Implementación y entrega
nav_order: 5
---

# Entrega y proceso de evaluación

## 1. Fechas y modalidad

El proyecto debe presentarse en la sesión de laboratorio del día viernes 2 de octubre de 2026. La evaluación se realiza por equipos y, además, la calificación final dependerá del desempeño individual al momento de la explicación y del compromiso demostrado para con el equipo.

Se deberán entregar en Brightspace lo siguiente:

- Portafolio digital del proyecto, detallando claramente el desarrollo metodológico, la arquitectura, la generación de controladores y la ejecución de los puntos solicitados.
- Programas realizados, archivos legibles, bien estructurados y comentados.
- Video o enlace a una carpeta con el video del sistema físico funcionando en el laboratorio.

## 2. Entregables solicitados

Los resultados deben documentarse e integrarse en el portafolio digital, el cual debe contener:

1. Descripción y procedimiento del sistema: modelado y demostración paso a paso de la dinámica linealizada en el espacio de estados.
2. Cálculo de ganancias `K` para LQR: descripción del proceso realizado para ajustar las matrices de ponderación y el cálculo de la ganancia `K` de la retroalimentación LQR.
3. Cálculo de ganancias para el observador de estados: demostración y diseño del cálculo de las ganancias del observador para garantizar la estabilidad y convergencia del error de estimación para cada estado.
4. Definición de ecuaciones del observador: demostración de la obtención de las ecuaciones que definen al observador para cada estado a partir del diagrama.
5. Análisis y discusión de resultados: gráficas de los estados y su estimación bajo distintos escenarios, discutiendo la relación entre las métricas de control y las metodologías empleadas.

## 3. Evidencia y material del proyecto

| Evidencia | Estado |
| --- | --- |
| Modelo y simulación | Archivo o enlace del modelo y simulación |
| Programa del controlador | Archivo o enlace del controlador implementado |
| Programa del observador | Archivo o enlace del observador implementado |
| Gráficas de estados y estimaciones | Figuras finales del comportamiento del sistema |
| Video del sistema físico | Enlace o archivo del sistema funcionando |

<div class="report-figure">
  <img src="{{ '/assets/css/imag/modelo_lqr_observ_final.png' | relative_url }}" alt="Resultado final del lazo cerrado LQR con el observador planteado" class="report-figure__image">
  <p class="report-figure__caption">Figura 7. Resultado final del lazo cerrado LQR con el observador planteado.</p>
</div>

<div class="report-figure">
  <div class="video-wrapper">
    <iframe src="https://www.youtube.com/embed/Ow0opi5Q_fY?rel=0" title="Video de demostración: lecturas observador vs real de LQR con lazo cerrado mediante el observador" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
  </div>
  <p class="report-figure__caption">Video de demostración lecturas observador vs real de LQR con lazo cerrado mediante el observador.</p>
</div>

## 4. Resultados esperados

La parte final del proyecto debe incluir análisis y discusión de resultados con los siguientes elementos:

- gráficas de los estados y su estimación,
- comparación de respuesta en distintas pruebas,
- relación entre las métricas de control y la estrategia de diseño,
- análisis de desviaciones entre modelo y planta real.

| Indicador | Descripción |
| --- | --- |
| Tiempo de establecimiento | Indica la rapidez de respuesta |
| Sobreimpulso | Evaluación del comportamiento transitorio |
| Error estacionario | Precisión de seguimiento |
| Esfuerzo de control | Voltaje aplicado por los motores |
| Error de estimación | Calidad del observador |

## 5. Criterios de evaluación

La rúbrica del proyecto considera los siguientes aspectos:

| Criterio | Evidencia en este portafolio |
| --- | --- |
| Implementación técnica (hardware y Simulink) | Modelos, programas y pruebas reproducibles |
| Diseño y ajuste de parámetros | Justificación de `Q`, `R`, `K` y ganancias del observador |
| Análisis de resultados | Gráficas, métricas y comparación con la planta real |
| Discusión y argumentación | Interpretación de resultados y limitaciones |
| Portafolio y repositorio | Estructura clara, archivos comentados y evidencia completa |
| Evaluación oral individual | Explicación del diseño, implementación y resultados |

## 6. Cierre

La práctica finaliza con la integración del modelo, el controlador LQR y el observador de estados. La calidad del portafolio se mide por la claridad del desarrollo metodológico, la consistencia del diseño y la capacidad de sustentación individual frente a la evaluación final.
