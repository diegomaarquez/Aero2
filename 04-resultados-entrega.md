---
layout: default
title: Integración y evidencia
nav_order: 5
---

# Integración y evidencia experimental

El sistema integra el modelo linealizado del Quanser Aero 2, el controlador LQR y el observador de estados. La evidencia visual de la arquitectura y de su funcionamiento se presenta a continuación; el desarrollo metodológico, las gráficas y el análisis cuantitativo están reunidos en el [informe técnico]({{ '/05-informe-tecnico/' | relative_url }}).

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

## Análisis de resultados

El informe técnico reúne los procedimientos, las respuestas del sistema, las métricas de control y estimación, y la comparación entre el modelo y la planta. El documento completo puede consultarse en la sección [Informe técnico]({{ '/05-informe-tecnico/' | relative_url }}).
