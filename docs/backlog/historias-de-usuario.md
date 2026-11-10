# Historias de Usuario

Formato: «Como [usuario], quiero [funcionalidad], para [beneficio]». Las tres historias parten de las interacciones del módulo con Comercial, Depósito y Administración y Compras (Entrega N.º 1). Columnas del tablero: **Por Hacer**, **En Progreso** y **Listo**.

| ID | Historia de Usuario | Criterios de aceptación | Estado |
|---|---|---|---|
| HU-01 | Como cliente de la tienda web, quiero ver la disponibilidad real de cada prenda por talle, para no comprar productos que no están disponibles. | El stock publicado se actualiza en ≤ 1,5 s (K1); el botón de compra se deshabilita con `stock_actual` = 0; no hay sobreventas (K5). | Listo |
| HU-02 | Como operario de depósito, quiero recibir una orden de preparación al confirmarse una venta y una alerta cuando una prenda llega a su stock mínimo, para reponer a tiempo y reducir los tiempos de empaque. | La orden se genera al pasar el pedido a En preparación; la alerta se emite con `stock_actual` ≤ `stock_minimo`; K6 ≤ 24 h hábiles. | En Progreso |
| HU-03 | Como responsable de compras, quiero acceder a reportes de las prendas de mayor rotación, para negociar con los proveedores según la demanda real y evitar stock inmovilizado. | El reporte se arma con `Detalle_Pedido` y `Movimiento_Stock` y ordena las prendas por unidades vendidas en un período. | Por Hacer |

| Historia | Issue | Rama |
|---|---|---|
| HU-01 | #1 | `docs/bpmn-fase-1` |
| HU-02 | #2 | `docs/bpmn-fase-2` |
| HU-03 | #3 | `docs/indicadores-de-control` |
