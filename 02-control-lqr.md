---
layout: default
title: Control LQR
nav_order: 3
---

# Diseño del control LQR

## Objetivo

Regular cabeceo y guiñada hacia las referencias deseadas mediante retroacción de estados. El diseño debe equilibrar el error de estado y el esfuerzo aplicado a los motores.

El criterio continuo que se minimizará es:

```text
J = integral desde 0 hasta infinito de (xᵀ Q x + uᵀ R u) dt
```

`Q` pondera los estados y `R` pondera las entradas. Ambas matrices deben ser simétricas; `Q` semidefinida positiva y `R` definida positiva.

## Diseño y ajuste

Documentar aquí:

1. Modelo y parámetros empleados, enlazados desde [Modelo del Quanser Aero 2](01-modelo-aero2.md).
2. Criterio para elegir los elementos de `Q` y `R`, con unidades o normalización usada.
3. Solución de la ecuación algebraica de Riccati y ganancia `K` obtenida.
4. Polos de lazo cerrado y comprobación de estabilidad.
5. Límites de voltaje del equipo y tratamiento de saturación.

Para regulación al origen, la ley de control es `u = −Kx`. Para seguir referencias no nulas de ángulo, documentar además cómo se genera el equilibrio o se corrige el error estacionario; la retroacción LQR por sí sola no garantiza seguimiento exacto.

## Resultados

Agregar gráficas con unidades, leyendas y condiciones iniciales. Como mínimo, mostrar referencias y respuestas de cabeceo/guiñada, así como los voltajes `Vp` y `Vy`.

| Prueba | Referencia `(θp, θy)` | Condición inicial | Resultado |
| --- | --- | --- | --- |
| Simulación nominal | Pendiente | Pendiente | Pendiente |
| Variación de parámetros | Pendiente | Pendiente | Pendiente |
| Prueba de laboratorio | Pendiente | Pendiente | Pendiente |

Discutir tiempo de establecimiento, sobreimpulso, error estacionario, esfuerzo de control y diferencias entre el modelo y la planta física.