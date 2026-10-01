---
layout: default
title: Modelo Aero 2
nav_order: 2
---

# Modelo del Quanser Aero 2

## Variables del sistema

El modelo linealizado continuo tiene cuatro estados: los ángulos de cabeceo y guiñada, y sus velocidades angulares. Las entradas son los voltajes aplicados a los motores; las salidas medidas son ambos ángulos.

| Vector | Orden |
| --- | --- |
| Estado `x` | `[θp, θy, θ̇p, θ̇y]ᵀ` |
| Entrada `u` | `[Vp, Vy]ᵀ` |
| Salida `y` | `[θp, θy]ᵀ` |

La representación en espacio de estados es `ẋ = Ax + Bu`, `y = Cx + Du`.

## Matrices del modelo

```text
A = [ 0            0     1       0       ]
    [ 0            0     0       1       ]
    [-Ksp/Jp       0    -Dp/Jp   0       ]
    [ 0            0     0      -Dy/Jy   ]

B = [ 0               0              ]
    [ 0               0              ]
    [ Dt*Kpp/Jp       Dt*Kpy/Jp       ]
    [ Dt*Kyp/Jy       Dt*Kyy/Jy       ]

C = [ 1  0  0  0 ]
    [ 0  1  0  0 ]

D = [ 0  0 ]
    [ 0  0 ]
```

`θp` es el ángulo de cabeceo, `θy` el ángulo de guiñada, `Vp` el voltaje del motor de cabeceo y `Vy` el del motor de guiñada.

## Parámetros nominales

| Parámetro | Descripción | Valor nominal | Unidad |
| --- | --- | ---: | --- |
| `Dt` | Distancia del pivote al centro del rotor | 0.16743 | m |
| `Mb` | Masa total del cuerpo aerodinámico | 1.07 | kg |
| `Dm` | Distancia al centro de masa inferior | 2.4 × 10⁻³ | m |
| `Jp` | Momento de inercia de cabeceo | 0.0231885 | kg·m² |
| `Jy` | Momento de inercia de guiñada | 0.0238104 | kg·m² |
| `g` | Gravedad | 9.81 | m/s² |
| `Ksp` | Rigidez de cabeceo | 0.0130 | N·m/V |
| `Dp` | Amortiguamiento de cabeceo | 0.00266 | N·m/V |
| `Kpp` | Ganancia de empuje de cabeceo | 0.00323 | N/V |
| `Kpy` | Empuje cruzado: guiñada a cabeceo | 0.00149 | N/V |
| `Dy` | Amortiguamiento de guiñada | 0.00175 | N·m/V |
| `Kyy` | Ganancia de empuje de guiñada | 0.00571 | N/V |
| `Kyp` | Empuje cruzado: cabeceo a guiñada | −0.00235 | N/V |

## Validación experimental

Los valores nominales son el punto de partida, no sustituyen la identificación realizada en las prácticas. Completar esta sección con:

- Parámetros identificados y método de estimación.
- Diferencias respecto a los valores nominales y su posible origen.
- Modelo final utilizado en simulación y en el controlador.
- Comprobación de controlabilidad y observabilidad del modelo elegido.

## Pendiente

- [ ] Confirmar unidades, signos y parámetros con los datos de laboratorio.
- [ ] Sustituir los parámetros nominales por los identificados cuando corresponda.
- [ ] Adjuntar el procedimiento de linealización y las pruebas del modelo.