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

Las matrices `Q` y `R` establecen el equilibrio entre el seguimiento de los estados y el esfuerzo de los motores. En la implementación presentada, las ponderaciones son `Q = diag(500, 80, 0, 0)` y `R = diag(0.02, 0.02)`.

## 4. Cálculo de la ganancia K

La ganancia del regulador se obtiene resolviendo la ecuación algebraica de Riccati:

```text
AᵀP + PA - PBR⁻¹BᵀP + Q = 0
```

y luego:

```text
K = R⁻¹BᵀP
```

La matriz `K` define la retroalimentación de estados. El script calcula la ganancia con `lqr` y obtiene los polos del lazo cerrado; los valores numéricos y el análisis de estabilidad se presentan en el [informe técnico]({{ '/05-informe-tecnico/' | relative_url }}).

### Script MATLAB del modelo y el controlador

El siguiente código construye las matrices con los parámetros nominales, resuelve la ecuación de Riccati mediante `lqr` y calcula los polos del lazo cerrado:

```matlab
clear; clc;

Ksp = 0.0130;
Jp = 0.0231885;
Dp = 0.00266;
Dy = 0.00175;
Jy = 0.0238104;
Dt = 0.16743;
Kpp = 0.00323;
Kpy = 0.00149;
Kyy = 0.00571;
Kyp = -0.00235;

A_modelo = [0 0 1 0;
      0 0 0 1;
      -Ksp/Jp 0 -Dp/Jp 0;
      0 0 0 -Dy/Jy];

B_modelo = [0 0;
      0 0;
      Dt*Kpp/Jp Dt*Kpy/Jp;
      Dt*Kyp/Jy Dt*Kyy/Jy];

C = [1 0 0 0;
  0 1 0 0];
D = [0 0;
  0 0];

Q = [500 0 0 0;
  0 80 0 0;
  0 0 0 0;
  0 0 0 0];
R = [0.02 0;
  0 0.02];

K_lqr = lqr(A_modelo, B_modelo, Q, R)
A_cl = A_modelo - B_modelo*K_lqr;
polos_lazo_cerrado = eig(A_cl)
```

La ley calculada es `u = -K_lqr x`. Los valores que MATLAB muestra para `K_lqr` y `polos_lazo_cerrado` corresponden a estos parámetros y ponderaciones; los polos permiten comprobar la estabilidad del modelo en lazo cerrado.

<div class="report-figure">
  <img src="{{ '/assets/css/imag/modelo_LQR.png' | relative_url }}" alt="Lazo cerrado LQR del modelo con el filtro Quanser que proporciona los estados actuales" class="report-figure__image">
  <p class="report-figure__caption">Figura 3. Lazo cerrado del modelo LQR con el filtro Quanser proporcionando los estados actuales.</p>
</div>

## 5. Implementación

La implementación calcula la ganancia LQR a partir del modelo linealizado y las ponderaciones indicadas, y evalúa los polos de la matriz de lazo cerrado. Las respuestas de cabeceo y guiñada, las señales de control y la comparación experimental se presentan en [Resultados y conclusiones]({{ '/04-resultados-entrega/' | relative_url }}).

<div class="report-figure">
  <img src="{{ '/assets/css/imag/modelo_lqr_observador_separado.png' | relative_url }}" alt="Modelo LQR con observador para visualizar su respuesta, manteniendo cerrado el lazo con el filtro Quanser" class="report-figure__image">
  <p class="report-figure__caption">Figura 4. Respuesta del LQR con el observador; el lazo permanece cerrado con el filtro Quanser.</p>
</div>
