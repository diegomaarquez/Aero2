---
layout: default
title: Portada
nav_order: 1
---

<section class="aero-hero" aria-labelledby="aero-title">
	<div class="aero-hero__copy">
		<p class="aero-kicker">PORTAFOLIO · CONTROL AVANZADO</p>
		<h1 id="aero-title">Quanser<br><span>Aero 2</span></h1>
		<p class="aero-hero__lead">Control LQR y observación de estados para una plataforma aérea de dos grados de libertad.</p>
		<dl class="aero-meta">
			<div>
				<dt>Asignatura</dt>
				<dd>Control Avanzado</dd>
			</div>
			<div>
				<dt>Presentación</dt>
				<dd>02 oct 2026</dd>
			</div>
		</dl>
	</div>
	<figure class="aero-hero__figure">
		<img src="{{ '/assets/aero2-product.jpg' | relative_url }}" alt="Plataforma Quanser Aero 2 con dos rotores protegidos y estructura de cabeceo y guiñada" fetchpriority="high">
		<figcaption>Quanser Aero 2 · Imagen: <a href="https://www.quanser.com/products/aero-2/" target="_blank" rel="noopener noreferrer">Quanser</a></figcaption>
	</figure>
</section>

<section class="aero-intro" aria-labelledby="project-overview">
	<p class="aero-kicker">EL PROYECTO</p>
	<h2 id="project-overview">Control y estimación de estados</h2>
	<p>Diseñar, implementar y evaluar un controlador por retroacción de estados LQR y un observador para regular los ángulos de cabeceo (<em>pitch</em>) y guiñada (<em>yaw</em>). El portafolio reúne el modelo, las decisiones de diseño y la evidencia de simulación y laboratorio.</p>
</section>

<section class="aero-chapters" aria-labelledby="chapter-heading">
	<div class="aero-section-heading">
		<div>
			<p class="aero-kicker">RECORRIDO</p>
			<h2 id="chapter-heading">Desarrollo del proyecto</h2>
		</div>
		<p>Cuatro etapas, de la planta física a los resultados.</p>
	</div>
	<div class="aero-chapter-grid">
		<a class="aero-chapter" href="{{ '/01-modelo-aero2/' | relative_url }}">
			<span class="aero-chapter__number">01</span>
			<span class="aero-chapter__text"><strong>Modelo de la planta</strong><small>Estados, matrices y parámetros nominales</small></span>
		</a>
		<a class="aero-chapter" href="{{ '/02-control-lqr/' | relative_url }}">
			<span class="aero-chapter__number">02</span>
			<span class="aero-chapter__text"><strong>Control LQR</strong><small>Ponderaciones, ganancia y seguimiento</small></span>
		</a>
		<a class="aero-chapter" href="{{ '/03-observador/' | relative_url }}">
			<span class="aero-chapter__number">03</span>
			<span class="aero-chapter__text"><strong>Observador</strong><small>Estimación de estados y convergencia</small></span>
		</a>
		<a class="aero-chapter" href="{{ '/04-resultados-entrega/' | relative_url }}">
			<span class="aero-chapter__number">04</span>
			<span class="aero-chapter__text"><strong>Pruebas y entrega</strong><small>Implementación, gráficas y evaluación</small></span>
		</a>
	</div>
</section>

<section class="aero-status" aria-labelledby="status-heading">
	<div class="aero-section-heading">
		<div>
			<p class="aero-kicker">BITÁCORA</p>
			<h2 id="status-heading">Avance</h2>
		</div>
		<p>Se actualizará con los resultados del equipo.</p>
	</div>

| Parte | Estado |
| --- | --- |
| Modelo matemático y parámetros | Por validar en laboratorio |
| Diseño LQR | Pendiente de documentar |
| Diseño del observador | Pendiente de documentar |
| Simulación y pruebas físicas | Pendiente de documentar |

</section>