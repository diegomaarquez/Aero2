---
layout: default
title: Modelo Aero 2
nav_order: 2
---

# Modelo del Quanser Aero 2

## 1. Descripción del sistema

La plataforma Quanser Aero 2 es un helicóptero de dos grados de libertad (2 DOF). Para el diseño del control se utiliza el siguiente modelo linealizado en tiempo continuo:

```text
ẋ = A x + B u
y = C x + D u
```

Las variables de entrada de control son el voltaje del motor de cabeceo (`Vp`) y el voltaje del motor de guiñada (`Vy`). Las matrices del sistema están definidas por sus parámetros físicos de la siguiente forma.

## 2. Variables de estado, entrada y salida

| Vector | Descripción |
| --- | --- |
| Estado `x` | `[θp, θy, θ̇p, θ̇y]^T` |
| Entrada `u` | `[Vp, Vy]^T` |
| Salida `y` | `[θp, θy]^T` |

Donde `θp` es el ángulo de cabeceo y `θy` es el ángulo de guiñada.

## 3. Matrices del modelo linealizado

```text
A = [ 0          0      1      0      ]
    [ 0          0      0      1      ]
    [-Ksp/Jp     0     -Dp/Jp   0      ]
    [ 0          0      0     -Dy/Jy   ]

B = [ 0              0             ]
    [ 0              0             ]
    [ Dt*Kpp/Jp      Dt*Kpy/Jp      ]
    [ Dt*Kyp/Jy      Dt*Kyy/Jy      ]

C = [ 1  0  0  0 ]
    [ 0  1  0  0 ]

D = [ 0  0 ]
    [ 0  0 ]
```

Esta estructura corresponde al modelo empleado en la síntesis del controlador y del observador. Los parámetros nominales se contrastan con la identificación experimental presentada en el [informe técnico]({{ '/05-informe-tecnico/' | relative_url }}).

## 4. Parámetros nominales del fabricante

El Cuadro 1 del proyecto muestra los parámetros nominales del sistema Quanser Aero 2. Estos valores se usan como referencia inicial, pero el estudiantado tiene la responsabilidad de validarlos según los datos experimentales obtenidos en clase.

| Parámetro | Símbolo | Valor nominal | Unidades |
| --- | --- | ---: | --- |
| Distancia del pivote al centro del rotor | `Dt` | 0.16743 | m |
| Masa total del cuerpo aerodinámico | `Mb` | 1.07 | kg |
| Distancia del plano al centro de masa inferior | `Dm` | 2.4 × 10⁻³ | m |
| Momento de inercia (cabeceo) | `Jp` | 0.0231885 | kg·m² |
| Momento de inercia (guiñada) | `Jy` | 0.0238104 | kg·m² |
| Gravedad | `g` | 9.81 | m/s² |
| Rigidez (cabeceo) | `Ksp` | 0.0130 | N·m/V |
| Amortiguamiento (cabeceo) | `Dp` | 0.00266 | N·m/V |
| Ganancia de empuje de cabeceo | `Kpp` | 0.00323 | N/V |
| Empuje cruzado (cabeceo desde guiñada) | `Kpy` | 0.00149 | N/V |
| Amortiguamiento (guiñada) | `Dy` | 0.00175 | N·m/V |
| Ganancia de empuje de guiñada | `Kyy` | 0.00571 | N/V |
| Empuje cruzado (guiñada desde cabeceo) | `Kyp` | -0.00235 | N/V |

## 5. Procedimiento de validación

La validación contrasta la respuesta del modelo con las mediciones experimentales y considera unidades, signos, acoplamiento e incertidumbre de los parámetros. La evidencia experimental se presenta en [Integración y evidencia]({{ '/04-resultados-entrega/' | relative_url }}).

<div class="report-figure">
  <img src="{{ '/assets/css/imag/modelo_lqr_observador_separado.png' | relative_url }}" alt="Diagrama del modelo del sistema y su esquema controlado con LQR y observador" class="report-figure__image">
  <p class="report-figure__caption">Figura 2. Comparación del modelo con la respuesta experimental del sistema.</p>
</div>

## 6. Controlabilidad y observabilidad

La controlabilidad y la observabilidad caracterizan, respectivamente, la posibilidad de estabilizar la planta mediante retroalimentación de estados y de reconstruir sus variables internas a partir de las salidas medidas. La comprobación numérica correspondiente se presenta en [Integración y evidencia]({{ '/04-resultados-entrega/' | relative_url }}).
