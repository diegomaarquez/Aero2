---
layout: default
title: Observador de estados
nav_order: 4
---

# Observador de estados

## Propósito

Estimar en tiempo real los estados que no se miden directamente a partir del modelo de la plataforma y de las salidas medidas. Para el modelo de Aero 2, las mediciones son los ángulos de cabeceo y guiñada; el observador también debe estimar sus velocidades angulares.

## Arquitectura y ecuaciones

Documentar las ecuaciones obtenidas a partir del diagrama del enunciado, definir cada ganancia y explicar cómo se acopla la salida medida `y` a la estimación `x̂`.

En un observador de Luenberger clásico con entrada conocida, la forma de referencia es:

```text
ẋ̂ = A x̂ + B u + L(y − C x̂)
```

La dinámica del error depende de `A − LC`; por ello, justificar la selección de polos o el método usado para calcular `L` y verificar que el error converge.

**Punto por aclarar del enunciado:** el texto indica que el observador no recibe el comando de control. La forma clásica anterior sí usa `u`. Antes de implementar, especificar la arquitectura que se seguirá y derivar su ecuación de error; si se omite `Bu`, demostrar cómo se conserva la convergencia durante las entradas aplicadas. No presentar la forma clásica como si cumpliera automáticamente esa restricción.

## Diseño y validación

- Matrices y parámetros usados: pendiente.
- Ganancias del observador y criterio de selección: pendiente.
- Polos de error y comprobación de estabilidad: pendiente.
- Inicialización de `x̂` y condiciones de prueba: pendiente.
- Gráficas superpuestas de cada estado real y estimado: pendiente.
- Error de estimación por estado y discusión de convergencia: pendiente.

Evaluar el observador en simulación y, cuando sea posible, con datos de laboratorio. Discutir ruido de medición, incertidumbre del modelo y efecto de las perturbaciones.