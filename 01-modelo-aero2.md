---
layout: default
title: Modelo Aero 2
nav_order: 2
---

# Modelo del Quanser Aero 2

## 1. Descripción del sistema

La plataforma Quanser Aero 2 es un helicóptero de 2 grados de libertad (2 DOF). Para el desarrollo del control, los estudiantes deben usar las siguientes matrices del sistema linealizado del Quanser Aero 2 en tiempo continuo:

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

Esta es la estructura del modelo usado para la síntesis del controlador y del observador. El estudiante debe asegurarse de que los valores físicos sean consistentes con los identificados en laboratorio.

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

La validación del modelo se lleva a cabo mediante la comparación entre la respuesta esperada del modelo y las mediciones experimentales del sistema. El estudiante debe verificar:

1. Consistencia de las unidades y los signos de las ecuaciones.
2. Relación entre variables de entrada y salida del sistema.
3. Compatibilidad de los parámetros nominales con los valores identificados en laboratorio.
4. Posibles desajustes por amortiguamiento, acoplamiento e incertidumbre del montaje.

En la práctica final, este apartado se complementa con los datos reales de identificación y con el análisis de controlabilidad y observabilidad del modelo elegido.

<div class="report-figure">
  <img src="{{ '/assets/css/imag/modelo_lqr_observador_separado.png' | relative_url }}" alt="Diagrama del modelo del sistema y su esquema controlado con LQR y observador" class="report-figure__image">
  <p class="report-figure__caption">Figura 2. Comparación del modelo con la respuesta experimental del sistema.</p>
</div>

## 6. Controlabilidad y observabilidad

El modelo debe comprobarse en términos de controlabilidad y observabilidad. Esta fase es clave para garantizar que el sistema pueda ser estabilizado mediante retroalimentación de estados y que sus variables internas puedan estimarse a partir de las salidas medidas.

En la versión final del informe se incluye la comprobación numérica con las matrices pertinentes y la discusión de los resultados.

## 7. Conclusión del modelado

El modelo linealizado del Quanser Aero 2 permite formular una representación adecuada del sistema para el control. Sin embargo, la validez del modelo depende de la identificación experimental y de la comparación con la planta real. Este bloque se completa con los resultados de laboratorio y la versión final del modelo usado en simulación y control.
