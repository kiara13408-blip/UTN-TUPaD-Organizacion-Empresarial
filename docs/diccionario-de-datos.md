# Diccionario de datos inicial

Entidades críticas del Sistema de Gestión de Inventario y Stock en Tiempo Real de Portalú (Entrega N.º 3). Las claves son: **PK** (clave primaria), **FK** (clave foránea) y **Único** (valor sin repeticiones).

## Cliente
Datos personales y de contacto de los consumidores registrados en la tienda web.

| Campo | Tipo de dato | Clave | Descripción funcional |
|---|---|---|---|
| id_cliente | Integer | PK | Identificador único autoincremental del cliente. |
| nombre | String(60) | — | Nombre de pila. |
| apellido | String(60) | — | Apellido. |
| correo_electronico | String(120) | Único | Correo para acceso, autenticación y notificaciones. |
| telefono | String(20) | — | Teléfono de contacto, con prefijo. |
| direccion_envio | String(200) | — | Domicilio principal de entrega. |
| fecha_registro | DateTime | — | Fecha y hora de creación de la cuenta. |

## Producto
Catálogo de indumentaria. Cada registro es una variante vendible (prenda, talle y color) identificada por un SKU.

| Campo | Tipo de dato | Clave | Descripción funcional |
|---|---|---|---|
| id_producto | Integer | PK | Identificador único de la variante. |
| sku | String(20) | Único | Código de la variante. |
| nombre_prenda | String(100) | — | Denominación comercial. |
| talle | String(5) | — | Talle (S, M, L, XL). |
| color | String(30) | — | Color. |
| precio_unitario | Decimal(10,2) | — | Precio de venta vigente, en pesos argentinos. |
| stock_actual | Integer | — | Unidades disponibles; se actualiza en tiempo real y nunca es negativo. |
| stock_minimo | Integer | — | Umbral de reposición: al alcanzarlo se emite la alerta. |
| activo | Boolean | — | Indica si la variante está publicada y habilitada para la compra. |

## Pedido
Órdenes de compra y estado del proceso logístico.

| Campo | Tipo de dato | Clave | Descripción funcional |
|---|---|---|---|
| id_pedido | Integer | PK | Identificador único de la orden. |
| id_cliente | Integer | FK | Cliente que realizó el pedido (Cliente). |
| fecha_pedido | DateTime | — | Fecha y hora de la compra. |
| monto_total | Decimal(12,2) | — | Importe total, con el envío incluido. |
| estado_pedido | String(20) | — | Pendiente, En preparación, Despachado, Entregado o Cancelado. |
| codigo_seguimiento | String(30) | — | Código del correo; se completa al despachar. |

## Detalle_Pedido
Resuelve la relación de muchos a muchos entre Pedido y Producto.

| Campo | Tipo de dato | Clave | Descripción funcional |
|---|---|---|---|
| id_detalle | Integer | PK | Identificador único de la línea. |
| id_pedido | Integer | FK | Pedido al que pertenece (Pedido). |
| id_producto | Integer | FK | Variante solicitada (Producto). |
| cantidad | Integer | — | Unidades pedidas; mayor que cero. |
| precio_unitario | Decimal(10,2) | — | Precio al momento de la compra (histórico). |

## Movimiento_Stock
Registro histórico de ingresos, egresos y ajustes de stock.

| Campo | Tipo de dato | Clave | Descripción funcional |
|---|---|---|---|
| id_movimiento | Integer | PK | Identificador único del movimiento. |
| id_producto | Integer | FK | Variante afectada (Producto). |
| id_pedido | Integer | FK | Pedido que originó el movimiento, si corresponde (opcional). |
| tipo_movimiento | String(10) | — | Ingreso, Egreso o Ajuste. |
| cantidad | Integer | — | Unidades que suman (positivo) o restan (negativo). |
| fecha_movimiento | DateTime | — | Fecha y hora del registro. |

## Relaciones

| Relación | Cardinalidad |
|---|---|
| Cliente – Pedido | 1 a N |
| Pedido – Detalle_Pedido | 1 a N |
| Producto – Detalle_Pedido | 1 a N |
| Producto – Movimiento_Stock | 1 a N |
| Pedido – Movimiento_Stock | 1 a N (opcional) |
