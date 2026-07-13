# Paso 2 — KPIs y esquema de control de la venta

## KPI Norte

**Tasa de conversión Lead → Venta (%)**, por canal, medida mensualmente contra la meta de negocio (WhatsApp: implícita en 600 ventas/año ≈ 50/mes; Landing: meta a proponer). Es el indicador que más directamente conecta el trabajo del equipo digital con el resultado de negocio, y permite comparar canales en igualdad de condiciones (independiente del volumen de entrada).

**Meta propuesta para Landing:** **~15 ventas/mes (180/año)** a 6 meses, revisable trimestralmente — objetivo deliberadamente conservador frente al 0,43% de venta/lead actual, para no comprometer una cifra que la operación no ha sostenido en el tiempo.

## KPIs por etapa

Metas recalibradas a un nivel exigente pero alcanzable, unificadas entre canales donde aplica (en vez de metas divergentes por canal).

| KPI | Fórmula | Frecuencia | Meta / Benchmark | Fuente |
|---|---|---|---|---|
| Venta / Lead (norte) | Ventas / Leads generados | Mensual | WhatsApp ≥0,9% · Landing ≥0,8% | CRM |
| Tasa de autogestión | Resueltas bot / Conversaciones entrantes | Diaria | ≥35% (vs. 32,9% actual) | Logs del bot |
| % leads sin gestionar | No contactados / Leads recibidos | Diaria (alerta) | <15% (vs. 47% actual) | CRM |
| SLA de primer contacto | Tiempo lead → 1er contacto | Diaria | <4h (vs. 8h20 WhatsApp / 26h Landing actual) | CRM / timestamps |
| Tasa de contactación | Contactados / Leads recibidos | Semanal | ≥80% (vs. 52,7% WhatsApp / 64,9% Landing actual) | CRM |
| Tasa de agendamiento | Agendados / Contactados | Semanal | ≥20-22% (vs. 20,9% WhatsApp / 17,5% Landing actual) | CRM |
| Tasa de asistencia a cita | Asistencias / Agendas | Semanal | ≥70% (nuevo — no medido hoy) | Agenda comercial |
| Tasa de cierre | Ventas / Agendas | Mensual | ≥5% (vs. 2,1% WhatsApp / 3,8% Landing actual) | CRM / backoffice ventas |
| % tipificación completa | Con causa / No-agenda total | Semanal | ≥90% (vs. 62% actual) | CRM |
| CPL | Inversión en medios / Leads generados | Mensual | Benchmark sector | Ads Manager |
| CPA | Inversión en medios / Ventas | Mensual | A definir con Finanzas | Pauta + CRM |

*Nota: la meta de agendamiento y cierre se bajó frente a la versión inicial (25% y 10%) a niveles más realistas y defendibles (20-22% y 5%), evitando comprometer una mejora que triplicaría el desempeño actual en pocos meses.*

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

- Alerta a las 2h sin contactar; escalamiento automático a supervisor a las 4h si el lead sigue en "Nuevo" — meta <4h de primer contacto en ambos canales.
- Reporte diario de leads "huérfanos" (vencidos de SLA) por asesor.
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
