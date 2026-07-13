# Paso 2 — KPIs y esquema de control de la venta

## KPI Norte

**Tasa de conversión Lead → Venta (%)**, por canal, medida mensualmente contra la meta de negocio (WhatsApp: implícita en 600 ventas/año ≈ 50/mes; Landing: meta a proponer). Es el indicador que más directamente conecta el trabajo del equipo digital con el resultado de negocio, y permite comparar canales en igualdad de condiciones (independiente del volumen de entrada).

**Meta propuesta para Landing:** con 1.850 leads/mes y una tasa de venta/lead objetivo de ~1% (el doble de lo actual), la meta razonable de arranque sería **~18-20 ventas/mes**, revisable trimestralmente según la curva de mejora real.

## KPIs por etapa

| KPI | Fórmula | Frecuencia | Meta / Benchmark | Fuente |
|---|---|---|---|---|
| Tasa de autogestión (bot) | Resueltas bot / Conversaciones entrantes | Diaria | ≥35% (vs. 32,9% actual) | Logs del bot |
| % leads sin gestionar | Leads no contactados / Leads recibidos | Diaria | <15% (vs. 47% actual) | CRM |
| SLA de primer contacto | % de leads contactados dentro de la ventana objetivo (ej. <4h WhatsApp, <12h Landing) | Diaria | 90% dentro de SLA | CRM / timestamps |
| Tasa de contactación | Contactados / Leads recibidos | Semanal | WhatsApp ≥70%, Landing ≥75% | CRM |
| Tasa de agendamiento | Agendados / Contactados | Semanal | ≥25% ambos canales | CRM |
| Tasa de asistencia a cita (show rate) | Citas asistidas / Citas agendadas | Semanal | ≥70% (no medido hoy — implementar) | CRM / agenda comercial |
| Tasa de cierre | Ventas / Agendados | Mensual | ≥10% (vs. 2,1%–3,8% actual) | CRM / backoffice ventas |
| % tipificación completa | Gestiones tipificadas / Gestiones totales | Semanal | ≥90% (vs. 62% actual) | CRM |
| CPL (costo por lead) | Inversión en medios / Leads generados | Mensual | Benchmark sector vivienda | Pauta / Ads Manager |
| CPA (costo por venta) | Inversión en medios / Ventas | Mensual | Definir con Finanzas | Pauta + CRM |
| Venta / Lead (norte por canal) | Ventas / Leads generados | Mensual | WhatsApp ≥0,9%, Landing ≥1% | CRM |

## Esquema de control y seguimiento del lead hasta la venta

### 1. Estados del lead (máquina de estados única en el CRM, cruce de canales)

```
Nuevo → En gestión (contacto en curso) → Contactado
  → Agendado → Cita realizada (asistió / no asistió)
  → En negociación → Ganado (Venta) / Perdido (con motivo tipificado)
  → [Perdido con motivo "riesgo/precio/ubicación" → Descartado, no se recicla]
  → [Perdido con motivo recuperable → Reciclado, vuelve a "En gestión" en N días]
```

Cada cambio de estado queda con timestamp y responsable — es la base de todos los KPIs de tiempo y de las alertas.

### 2. Alertas de SLA de contacto

- Alerta automática cuando un lead lleva > umbral definido (ej. 4h WhatsApp / 12h Landing) en estado "Nuevo" sin pasar a "En gestión".
- Reporte diario de leads "huérfanos" (vencidos de SLA) a supervisión comercial.
- Alerta de cita sin confirmar 24h antes de la fecha agendada.
- Alerta de cita realizada sin tipificación registrada a las 48h (cierra el hueco del 38% sin tipificar).

### 3. Atribución por canal/UTM

- Todo lead nace con UTM (source/medium/campaign/content) capturado en el formulario o en el punto de entrada al WhatsApp (anuncio click-to-chat, botón en landing, orgánico).
- El UTM viaja con el lead como campo fijo en el CRM durante todo su ciclo de vida, hasta la venta — permite atribuir cada venta a la campaña que la originó (no solo al canal).
- Modelo de atribución: **first-touch** para comparar canales/campañas de adquisición, complementado con registro de **último touch antes de agendar** para detectar qué remedia mejor la conversión media-funnel.

### 4. Tablero

- **Vista ejecutiva** (mensual): ventas vs. meta por canal, KPI norte, tendencia.
- **Vista de funnel** (semanal): tasas etapa a etapa por canal, comparativo período anterior.
- **Vista operativa** (diaria): SLA de contacto, cola de leads sin gestionar, alertas activas.
- **Vista de calidad de dato** (semanal): % tipificación completa, % UTM presente.
- Filtros cruzados por canal, campaña/UTM, proyecto de vivienda y asesor.
