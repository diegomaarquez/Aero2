---
layout: default
title: Integración y evidencia
nav_order: 5
---

# Integración y evidencia

El sistema integra el modelo linealizado del Quanser Aero 2, el controlador LQR y el observador de estados. A continuación se presentan la evidencia de funcionamiento y la síntesis de resultados; los procedimientos, las gráficas y el análisis cuantitativo completo están disponibles en el [informe técnico]({{ '/05-informe-tecnico/' | relative_url }}).

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

## Resultados

El video muestra la respuesta del observador frente a las mediciones reales durante el control en lazo cerrado. El informe técnico reúne las respuestas del sistema, las métricas de control y estimación, y la comparación entre el modelo y la planta.

## Conclusiones

El modelo linealizado proporciona la base común para el diseño del controlador LQR y del observador de estados. La integración de ambos permite utilizar las estimaciones de estado en la ley de control y evaluar conjuntamente el seguimiento de referencias y la reconstrucción de las variables internas. La comparación entre las señales estimadas y medidas, junto con las métricas experimentales, permite valorar el desempeño del sistema completo; el detalle cuantitativo se encuentra en el [informe técnico]({{ '/05-informe-tecnico/' | relative_url }}).
