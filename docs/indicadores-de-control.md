# Indicadores de control y estándares de desempeño

Según el ciclo de control de la cátedra: se establece el estándar, se mide el desempeño, se compara con el estándar y, si hay desvío, se aplica una acción correctiva. K1 a K4 retoman las metas de la Entrega N.º 2; K5 y K6 son propuestas de la Entrega N.º 4 que debe validar la Dirección.

| ID | Indicador y medición | Estándar | Fuente y responsable | Acción correctiva |
|---|---|---|---|---|
| K1 | Tiempo de sincronización: segundos entre la venta o el ingreso y la actualización del stock publicado (percentil 99). | ≤ 1,5 s en el 99% de las transacciones (Entrega 2, meta 1). | Registros del módulo; Gerencia de Sistemas. | Optimizar consultas y escalar el servicio en la nube. |
| K2 | Desfasaje de stock: unidades con diferencia entre sistema y conteo físico, sobre el total contado (%). | 0% en los primeros 60 días de producción (Entrega 2, meta 3). | Conteo cíclico contra Producto y Movimiento_Stock; Auditoría Interna. | Registrar el ajuste, investigar la causa y corregir el proceso. |
| K3 | Capacidad: SKU activos y solicitudes concurrentes de consulta sin degradación. | 10.000 SKU y 500 solicitudes concurrentes (Entrega 2, meta 2). | Pruebas de carga previas al despliegue; Especialista QA. | Ajustar la infraestructura y repetir la prueba. |
| K4 | Cumplimiento del cronograma: fases del Gantt terminadas en plazo sobre las planificadas (%). | 100% en 10 semanas (Entrega 2, meta 4). | Diagrama de Gantt; Líder de Proyecto. | Replanificar y reasignar recursos. |
| K5 | Faltantes físicos: pedidos anulados por faltante físico sobre pedidos confirmados (%). | 0% (propuesto; deriva de K2). | Pedido cancelado y Movimiento_Stock de ajuste; Operaciones y Logística. | Revisar la reserva y reforzar el control de recepción. |
| K6 | Tiempo de preparación: horas entre los estados En preparación y Despachado. | ≤ 24 h hábiles (propuesto). | Estados del Pedido; Operaciones y Logística. | Reasignar personal de depósito y revisar la orden de preparación. |

## Auditoría técnica (a cargo de Auditoría Interna)

- **Integridad:** se cumplen las claves foráneas y no existen pedidos sin detalle.
- **Trazabilidad:** toda variación de `stock_actual` tiene su registro en `Movimiento_Stock`.
- **Estados:** solo se aceptan las transiciones de la matriz de estados.
- **Concordancia:** conteos cíclicos contra el stock del sistema (K2).
- **Documentación:** lo publicado en el repositorio coincide con lo entregado.
