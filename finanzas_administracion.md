# Finanzas y Administración — Memoria y estado de salud de PLIEGUE

> Registro vivo del área de Finanzas y Administración (Dpto. 5) de PLIEGUE (Bahía Blanca, Argentina).
> Se actualiza a medida que cambian los números o se toman decisiones. Lo más nuevo va arriba en la Bitácora.
> Convención de datos: **[V]** verificado (con fuente y fecha) · **[E]** estimado (con supuestos) · **[C]** criterio u opinión.
> No es asesoramiento impositivo: es material de trabajo para validar con el contador.

**Última actualización:** 23/10/2026
**Responsables:** Nacho y Antu (socios) · Analista financiero: Claude (proyecto "Pliegue. Finanzas y administración")

---

## 0. Índice

1. Herramientas: planilla y tablero
2. Definiciones y supuestos
3. Foto al 22/10/2026 (último movimiento cargado)
4. Alarmas abiertas
5. Acciones recomendadas
6. Datos a revisar en la planilla
7. Decisiones tomadas
8. Pendientes y responsables
9. Bitácora
10. Cómo actualizar este archivo

---

## 1. Herramientas: planilla y tablero

| Herramienta | Qué es | Dónde |
|---|---|---|
| Cashflow PLIEGUE v3 (Google Sheets) | Fuente única de verdad: VENTAS, STOCK, REGISTRO_GLOBAL, CUENTA_CORRIENTE, DASHBOARD, CONFIG | [Abrir planilla](https://docs.google.com/spreadsheets/d/1vxFdhclX2NQILiNtMxygpmZjoWcCGnMtBqud87XRmnE/edit) |
| Tablero PLIEGUE (artefacto de Claude) | Panel de salud del negocio. Lee la planilla en vivo por Google Drive cada vez que se abre o se toca "Actualizar datos" | [Abrir tablero](https://claude.ai/artifact/HmTBhCg3L5mvFr6EcLNqpL) |

**Qué muestra el tablero**

- Arriba, 4 cifras clave: facturación acumulada, margen de contribución, caja (pesos + dólares) y stock valuado a costo landed.
- Pestañas: Rentabilidad (por mes y venta por venta), Canales (ganador por margen), Productos y stock (mayor y menor demanda, cobertura), IVA e IIBB, Movimientos (egresos por categoría, aportes, caja).
- Panel derecho: alarmas (pagos, stock, ventas, datos) con filtros, y acciones recomendadas por prioridad.
- Cada número es auditable: en "Fuentes" se ve la fórmula de cada cálculo y la fila de la planilla de donde sale.

**Límites conocidos**

- Los vencimientos que salen de Gmail son una lectura manual del 23/10/2026: no se actualizan solos (ver pendiente 6).
- Quien abra el tablero necesita acceso propio a la planilla en Google Drive.
- Las tipografías de marca (Cormorant Garamond, DM Sans) se ven si están instaladas; si no, el tablero usa sus fuentes por defecto.

---

## 2. Definiciones y supuestos

| Concepto | Definición usada |
|---|---|
| Margen de contribución | Precio de venta − IVA débito − IIBB − costo landed (columna COSTO de STOCK × cantidad). No descuenta comisiones de plataforma. |
| Retención de plataforma | Precio − neto acreditado (el ingreso cargado en REGISTRO_GLOBAL para esa venta, mismo día o hasta 7 días después). |
| Margen después de retención | Margen de contribución − retención. Aproximación: la retención incluye comisión, envío y costo de cuotas sin separar. |
| Gastos operativos | Filas de REGISTRO_GLOBAL con Movimiento = "Gasto Operativo". En pesos: Monto ARS, o Valor USD × TC Cristal (si falta, × Dólar Pampa de CONFIG). |
| Resultado | Margen de contribución − gastos operativos. No incluye "Pagos" (aranceles, fletes, ZF, compra de dólares), porque forman parte del costo landed o son movimientos de caja. |
| Caja | "Estado de caja $" + "Estado de caja US$" × Dólar Pampa (CONFIG, hoy $1.598), según CUENTA_CORRIENTE. |
| Stock bajo | 1 unidad por color. Sin stock: 0. |
| IVA | Débito = columna IVA Debe de VENTAS (precio × 21/121). Crédito = IVA a favor > 0 en REGISTRO_GLOBAL. |
| IIBB | 3,5% sobre precio de venta (columna IIBB DEBE de VENTAS), menos lo pagado. Alícuota tomada de la planilla: **validar con el contador**. |

---

## 3. Foto al 22/10/2026 (último movimiento cargado)

Fuente de todo este bloque: planilla Cashflow PLIEGUE v3, leída el 23/10/2026 [V]. Octubre es un mes en curso.

### 3.1 Cifras clave

| Indicador | Valor |
|---|---|
| Facturación acumulada (ago–oct) | $11.396.426 · 11 ventas · 13 unidades (incluye 1 entrega interna a socio sin precio) |
| Margen de contribución | $2.007.796 · **17,6%** |
| Resultado después de gastos operativos | **−$472.868** (acumulado ago–oct) |
| Caja | $3.565.128 + US$ 4.481,82 ≈ **$10,7 M** (a $1.598). Caja $ ajustada en col. E: $2.492.263 |
| Stock | 25 unidades · **$12,15 M** a costo landed |

### 3.2 Rentabilidad por mes

| Mes | Facturación | Margen | Margen % | Gastos op. | Resultado |
|---|---|---|---|---|---|
| Ago 2026 | $5.928.676 | $861.762 | 14,5% | $583.364 | $278.398 |
| Sep 2026 | $3.468.000 | $464.192 | 13,4% | $1.020.136 | −$555.944 |
| Oct 2026 (parcial) | $1.999.750 | $681.843 | 34,1% | $877.165 | −$195.322 |

Lectura [C]: con ~4 ventas por mes el margen no cubre los gastos fijos (suscripciones, contador, autónomo, Bairex, cargos de MELI). Dos ventas dejaron margen negativo: PLG-003 (BORA por Tiendanube a $800.100: −$19.107) y PLG-010 (LEVO liquidación: −$1.766).

### 3.3 Canales

| Canal | Ventas · u | Facturación | Margen % | Retención observada | Margen después de retención |
|---|---|---|---|---|---|
| **Mercado Libre** (ganador) | 5 · 5 | $6.653.750 | 24,4% | 22,0% | 2,4% |
| Tiendanube | 4 · 5 | $3.722.676 | 8,6% | 7,6% | 1,0% |
| Particular | 2 · 3 | $1.020.000 | 6,5% | 0% | 6,5% (sin factura) |

Lectura [C]: Mercado Libre gana por ticket (promedio $1,33 M contra $0,93 M en Tiendanube), no por costo. Tiendanube vende más barato y casi no deja margen.

### 3.4 Productos

| Modelo | Vendidas | Stock | Cobertura | Lectura |
|---|---|---|---|---|
| BORA (YY-01) | 5 | 0 | agotado | Mayor demanda, sin stock |
| BLOCK (YY-82) | 3 | 1 | ~0,9 meses | Alta demanda, casi agotado |
| LEVO (YY-85) | 3 | 7 | ~6,3 meses | Rota lento |
| AMBA (AP-01) | 2 | 7 | ~9,4 meses | $6,3 M inmovilizados |
| LUMBO (YY-86) | 0 | 10 | sin ventas | Menor demanda: $3,0 M inmovilizados |

### 3.5 Impuestos (material para el contador)

| Concepto | Monto | Control |
|---|---|---|
| IVA débito (ventas) | $1.800.829 | |
| IVA crédito (compras e importación) | $4.246.677 | Incluye $3.360.749 del VEP de julio |
| **Saldo IVA a favor** | **$2.442.842** | Coincide con CUENTA_CORRIENTE |
| IIBB devengado | $363.175 | |
| IIBB pagado | $5.447 | |
| **IIBB a pagar** | **$357.728** | Coincide con CUENTA_CORRIENTE |

---

## 4. Alarmas abiertas (al 23/10/2026)

| Nivel | Tipo | Alarma | Fuente |
|---|---|---|---|
| Crítica | Pagos | OCA FC A-2001-00588370 (emitida 30/09) sin pago registrado. El pedido de detalle del 03/10 rebotó. Monto y vencimiento a completar desde el PDF | Gmail [V] |
| Crítica | Stock | BORA Arena y BORA Gris Topo sin stock; BLOCK Arena sin stock | STOCK [V] |
| Crítica | Ventas | 5 ventas sin factura marcada: PLG-006, 007, 008, 009, 011 ($6.366.750) | VENTAS [V] |
| Crítica | Ventas | PLG-011 (AMBA, MELI, 04/10) con envío PENDIENTE | VENTAS [V] |
| Alerta | Pagos | Suscripción Tiendanube y suscripción Claude de octubre sin registrar | REGISTRO_GLOBAL [V] |
| Alerta | Pagos | Factura de Mercado Libre de noviembre: cierre ~16/11, vence ~22/11 | Patrón de Gmail [E] |
| Alerta | Stock | LEVO Gris Plata y BLOCK Gris Plata con 1 unidad | STOCK [V] |
| Resuelta | Pagos | Factura de octubre de Mercado Libre ($155.942,85) pagada el 22/10 | Gmail + REGISTRO [V] |

---

## 5. Acciones recomendadas [C]

1. **Reponer BORA (~6 u) y BLOCK (~3 u)**: 3 meses de venta al ritmo actual. Capital estimado a costo actual ≈ $6,1 M [E]. Con ~100 días de ciclo de importación conviene cotizar ya y evaluar sumarlo al consolidado de las lámparas (ver Pliegue_I+D.md).
2. **Mover el sobrestock de LUMBO, AMBA y LEVO** ($11,4 M a costo): pauta dedicada, combos o precio de lanzamiento. LUMBO no registra ventas.
3. **Completar la columna FACTURA** de las 5 ventas sin marcar y confirmar con el contador las 2 ventas particulares sin factura.
4. **Regularizar pagos**: OCA (pedir el detalle por otra vía), Tiendanube y Claude de octubre.
5. **Revisar precios de Tiendanube** frente a Mercado Libre: deja 1,0% contra 2,4% después de retención.
6. **Reservar $357.728 para IIBB** y validar alícuota y vencimiento con el contador.
7. **Validar el saldo de IVA a favor ($2,44 M)** con el contador: que esté computado en las DDJJ.
8. **Despachar o actualizar el estado de PLG-011** (AMBA, vendido el 04/10).

---

## 6. Datos a revisar en la planilla

| Pestaña | Qué | Efecto |
|---|---|---|
| REGISTRO_GLOBAL fila 41 | "Venta BORA Arena TN" con fecha 25/08/**2023** | El tablero la toma como 25/08/2026 |
| STOCK | AMBA Gris Plata sin COSTO cargado | Se usa el costo del modelo ($900.859) |
| REGISTRO vs VENTAS | IVA débito difiere en $3.006 (22/09: $176.376,45 en REGISTRO vs $173.376,45 en VENTAS) | Revisar cuál es el correcto |
| VENTAS / STOCK | Códigos de color 3217-3 guardados como fecha en algunas celdas | El tablero los corrige al leer; conviene formatear la columna como texto |
| CUENTA_CORRIENTE E6 | Caja ajustada con un descuento manual de $1.072.865,10 sin explicación | Documentar a qué corresponde |

---

## 7. Decisiones tomadas

| Fecha | Decisión | Motivo |
|---|---|---|
| 23/10/2026 | Medir la rentabilidad por margen de contribución (precio − IVA − IIBB − costo landed) y el resultado restando gastos operativos | Separar lo que deja cada venta de la estructura fija |
| 23/10/2026 | Alarma de stock bajo con 1 unidad por color | ~2 ventas por mes en total: 1 unidad ya es crítico |
| 23/10/2026 | Cifras clave del tablero: ventas, margen, caja y stock | Pedido de los socios |

---

## 8. Pendientes y responsables

| # | Pendiente | Responsable | Estado |
|---|---|---|---|
| 1 | Cargar monto y vencimiento de OCA FC A-2001-00588370 y pedir el detalle por otra vía | Antu | Pendiente |
| 2 | Registrar Tiendanube y Claude de octubre si ya se pagaron | Nacho / Antu | Pendiente |
| 3 | Completar FACTURA en VENTAS (PLG-006 a PLG-011) | Nacho | Pendiente |
| 4 | Corregir fecha de la fila 41 y el COSTO de AMBA Gris Plata | Antu | Pendiente |
| 5 | Cotizar reposición de BORA y BLOCK | Antu | Pendiente |
| 6 | Decidir si se agenda una revisión automática de Gmail para los vencimientos | Socios | Pendiente |
| 7 | Validar IVA a favor e IIBB con el contador | Contador | Pendiente |

---

## 9. Bitácora (lo más nuevo arriba)

### 23/10/2026
- Se crea este archivo como memoria del área de Finanzas y Administración.
- Se publica el **Tablero PLIEGUE**: lee la planilla Cashflow PLIEGUE v3 en vivo, con 4 cifras clave, 5 pestañas, alarmas y acciones recomendadas, en la paleta del brandbook (Classic Linen, Jet Black, Caramel Brown, Obsidian Black).
- Revisión de Gmail: factura de MELI de octubre pagada el 22/10; factura OCA del 30/09 sin pago registrado.
- Controles: la Cuenta IVA y la Cuenta IIBB de CUENTA_CORRIENTE coinciden con el recálculo del tablero.

---

## 10. Cómo actualizar este archivo

1. Sumar una entrada nueva **arriba** en la Bitácora con la fecha y lo que pasó.
2. Actualizar la Foto (3) con los números del tablero y las Alarmas (4), Decisiones (7) y Pendientes (8).
3. Si cambia un número, anotar en la Bitácora el valor anterior y el nuevo.
4. Etiquetar cada dato nuevo como [V], [E] o [C].
5. Para normas impositivas o cambiarias, citar la fuente oficial vigente y dejar la validación al contador.
