---
layout: default
title: Portada
nav_order: 1
---

<section class="aero-hero" aria-labelledby="aero-title">
  <div class="aero-hero__copy">
    <p class="aero-kicker">PROYECTO PRÁCTICO · CONTROL AVANZADO</p>
    <h1 id="aero-title">Quanser<br><span>Aero 2</span></h1>
    <p class="aero-hero__lead">Implementación de un regulador LQR y un observador de estados para una plataforma de dos grados de libertad.</p>
    <dl class="aero-meta">
      <div>
        <dt>Asignatura</dt>
        <dd>Control Avanzado y Robótica</dd>
      </div>
      <div>
        <dt>Docentes</dt>
        <dd>Dr. Andrés Molano<br>Mtro. Julio Caballero</dd>
      </div>
      <div>
        <dt>Entrega</dt>
        <dd>2 oct 2026</dd>
      </div>
    </dl>
  </div>
  <figure class="aero-hero__figure">
    <img src="{{ '/assets/aero2-product.jpg' | relative_url }}" alt="Plataforma Quanser Aero 2 con dos rotores protegidos y estructura de cabeceo y guiñada" fetchpriority="high">
    <figcaption>Quanser Aero 2 · Plataforma de prueba</figcaption>
  </figure>
</section>

<section class="aero-intro" aria-labelledby="project-overview">
  <p class="aero-kicker">DESCRIPCIÓN DEL PROYECTO</p>
  <h2 id="project-overview">Control avanzado y observación de estados</h2>
  <p>El proyecto se divide en dos partes generales: la primera consiste en implementar un control por retroalimentación de estados LQR para mantener la estabilidad y regular el comportamiento de la planta asignada; la segunda parte corresponde al diseño e implementación de un observador de estados para estimar variables no medidas y perturbaciones del sistema en tiempo real. En este portafolio se documenta la parte correspondiente al equipo asignado a la plataforma Quanser Aero 2.</p>
</section>

<section class="aero-status" aria-labelledby="status-heading">
  <div class="aero-section-heading">
    <div>
      <p class="aero-kicker">OBJETIVOS</p>
      <h2 id="status-heading">Objetivos generales</h2>
    </div>
    <p>Modelado · Control · Observación · Evaluación</p>
  </div>

  <ul>
    <li>Diseñar controladores óptimos LQR para sistemas lineales en el espacio de estados e implementarlos con tecnología electrónica digital.</li>
    <li>Usar herramientas de espacios de estados para plantear esquemas de control y observadores robustos para sistemas lineales y linealizados.</li>
    <li>Apoyar la competencia de comunicación lingüística y lógico matemática mediante la estructuración de un repositorio y la evaluación oral del proyecto.</li>
  </ul>
</section>

<section class="aero-chapters" aria-labelledby="chapter-heading">
  <div class="aero-section-heading">
    <div>
      <p class="aero-kicker">RECORRIDO</p>
      <h2 id="chapter-heading">Estructura del proyecto</h2>
    </div>
    <p>Primera parte: control LQR · Segunda parte: observador de estados.</p>
  </div>
  <div class="aero-chapter-grid">
    <a class="aero-chapter" href="{{ '/01-modelo-aero2/' | relative_url }}">
      <span class="aero-chapter__number">01</span>
      <span class="aero-chapter__text"><strong>Modelo del sistema</strong><small>Descripción, matrices, parámetros y validación</small></span>
    </a>
    <a class="aero-chapter" href="{{ '/02-control-lqr/' | relative_url }}">
      <span class="aero-chapter__number">02</span>
      <span class="aero-chapter__text"><strong>Control LQR</strong><small>Diseño de Q, R, ganancia K y pruebas de desempeño</small></span>
    </a>
    <a class="aero-chapter" href="{{ '/03-observador/' | relative_url }}">
      <span class="aero-chapter__number">03</span>
      <span class="aero-chapter__text"><strong>Observador</strong><small>Estimación de estados y convergencia del error</small></span>
    </a>
    <a class="aero-chapter" href="{{ '/04-resultados-entrega/' | relative_url }}">
      <span class="aero-chapter__number">04</span>
      <span class="aero-chapter__text"><strong>Entrega y resultados</strong><small>Entregables, evidencia y evaluación final</small></span>
    </a>
  </div>
</section>

<section class="aero-status" aria-labelledby="status-heading-2">
  <div class="aero-section-heading">
    <div>
      <p class="aero-kicker">PRIMERA PARTE</p>
      <h2 id="status-heading-2">Equipo A: Quanser Aero 2</h2>
    </div>
    <p>Helicóptero de 2 grados de libertad.</p>
  </div>

  <p>El objetivo del controlador será regular los ángulos de cabeceo (pitch) y guiñada (yaw) hacia un conjunto de referencias deseadas. El desarrollo del control debe usar el modelo linealizado del sistema, fijando la atención en las entradas de voltaje del motor de cabeceo y del motor de guiñada.</p>
</section>

