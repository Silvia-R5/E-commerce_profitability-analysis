# E-commerce_profitability-analysis
Análisis de punta a punta del servicio de suscripción para responder si el negocio es rentable, dónde se pierden los usuarios, si regresan y si un cambio en el checkout genera impacto.
## Preguntas de negocio
| 1 | ¿Podemos confiar en los datos? | Python (Pandas) | Datasets limpios |
| 2 | ¿El negocio es rentable? | Python (Pandas) | Revenue, costos y profit |
| 3 | ¿Dónde se pierden los usuarios? | SQL | Funnel de conversión |
| 4 | ¿Los usuarios regresan? | SQL | Retención por cohortes |
| 5 | ¿Los cambios generan impacto? | Python (statsmodels) | Test Z de proporciones |
| 6 | ¿Cómo comunicamos los resultados? | Power BI | Dashboard ejecutivo |

## Hallazgos principales
**Rentabilidad (ene-jun 2025)**
- Revenue total: **$9,649,136.76**
- Costo de producto: $3,834,482.61 (39.7% del revenue)
- Profit bruto: $5,814,654.15 (60.3% de margen)
- Inversión en marketing: $2,871,843.53 (29.8% del revenue)
- **Profit neto: $2,942,810.62 (30.5% de margen)**
- Ticket promedio: $385.97 | Productos por orden: 1.51
- El revenue es estable (~$1.6 M al mes) pero **sin tendencia de crecimiento**.
- Hogar, Electrónica y Moda, y México, Colombia y Argentina, aportan de forma muy pareja.
- Hay órdenes con profit negativo, por ejemplo en Laptop-Gaming-16GB.

  **Funnel de conversión**
- De 7,796 usuarios que inician visita, 6,240 compran (**80% de conversión global**).
- La mayor fuga está entre *begin_checkout* y *add_payment_info* (13.3%, 958 usuarios).
- 99.8% de quienes ingresan su pago completan la compra.

**Retención por cohortes**
- La retención se mantiene en **~40-44%** durante las semanas 1 a 3 en todas las cohortes (ene-may).
- Las acciones de retención deberían concentrarse en la primera semana tras el registro.

**Experimento A/B (UI del checkout)**
- Conversión: control 15.69% vs. tratamiento 16.29%.
- Test Z de dos proporciones: z = -0.813, p = 0.416 (α = 0.05).
- **No hay evidencia estadísticamente significativa** de que la nueva UI mejore la conversión.

## Recomendaciones

1. Aumentar el ticket con ventas cruzadas y envío gratis desde cierto monto (1.51 productos por orden).
2. Impulsar con campañas los tres productos de menor volumen (Laptop, Tablet y Phone Pro).
3. Auditar descuentos y precios de las órdenes con profit negativo.
4. Medir el retorno de marketing por canal y reasignar presupuesto.
5. Revisar la experiencia entre checkout y pago (costos de envío, formularios, métodos de pago).

## Limitaciones

- Solo hay 6 meses de datos: no es posible comparar contra el año anterior ni ver estacionalidad.
- El profit de los pedidos con nulos puede estar sobrestimado.
- En el funnel, *add_to_cart* supera ligeramente a *select_item* (conversión de 100.7%), lo que sugiere validar el tracking de eventos.
- 6.2% del gasto de marketing no tiene canal asignado.

