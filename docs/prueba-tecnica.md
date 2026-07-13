# Prueba Técnica — Analista de Conversión y Optimización Digital (Colsubsidio)

## Qué es

Assessment de selección para el cargo de **Analista de Conversión y Optimización Digital** en Vivienda Colsubsidio.

## Contexto del negocio

Colsubsidio Vivienda capta leads para proyectos de vivienda por dos canales:

- **Landing** de proyectos con formularios de contacto.
- **Canal WhatsApp** comercial con flujo de autogestión (bot) y desbordamiento a asesor cuando se requiere gestión humana.

El flujo del lead es: **generado → contactado → agendado (cita comercial) → vendido**. La operación busca fortalecer la conversión en cada etapa y el seguimiento del lead hasta la venta.

## Objetivo del assessment

Evaluar la capacidad del candidato para:

- Leer datos de operación digital y calcular correctamente KPIs y tasas de conversión por etapa.
- Identificar los puntos de fuga del funnel con evidencia numérica y comparar el desempeño entre canales.
- Definir un set de KPIs y un esquema de control/seguimiento de la venta desde el lead.
- Diseñar y documentar una prueba A/B para una oportunidad de mejora concreta.
- Priorizar iniciativas y aterrizar el impacto esperado en términos de negocio.

## Caso práctico — datos de enero 2026

**Objetivo de negocio:** incrementar la eficiencia del funnel digital y la conversión a venta. Meta de WhatsApp: 600 ventas en 2026 (~50/mes). Landing no tiene meta formal — es parte del reto proponerla.

### 1. Canal WhatsApp

| Etapa del flujo | Volumen |
|---|---|
| Conversaciones entrantes al bot | 8.200 |
| Resueltas en autogestión (sin asesor) | 2.700 |
| Desbordadas a asesor (= leads recibidos) | 5.500 |
| Leads contactados | 2.900 |
| Agendamientos (citas) | 607 |
| Ventas | 13 |

### 2. Tipificación de "no agendamiento" (sobre leads contactados que no agendaron)

| Motivo | Participación |
|---|---|
| Reportado en centrales de riesgo | 39% |
| Desiste por ubicación | 21% |
| Desiste por precio | 14% |
| Compra en otro proyecto | 7% |
| Otros / sin tipificar | 19% |

### 3. Canal Landing

| Etapa del flujo | Volumen |
|---|---|
| Sesiones en la landing | 48.000 |
| Formularios iniciados | 3.200 |
| Formularios completados (leads) | 1.850 |
| Leads contactados | 1.200 |
| Agendamientos (citas) | 210 |
| Ventas | 8 |

### 4. Datos operativos (ambos canales)

| Indicador operativo | Valor |
|---|---|
| Tiempo promedio de primer contacto — WhatsApp | 8 h 20 min |
| Tiempo promedio de primer contacto — Landing | 26 h |
| % de leads sin gestionar — WhatsApp | 47% |
| % de agendamientos con tipificación registrada | 62% |

Nota: las tasas de conversión no se entregan de forma intencional — forman parte del análisis esperado.

## Entregables esperados

### 1. Diagnóstico y lectura de KPIs
- Tasas de conversión etapa a etapa para cada canal (autogestión, contactación, contactado→agenda, agenda→venta, venta sobre lead).
- Comparación landing vs. WhatsApp e identificación de los 2–3 puntos de mayor fuga, con cifra que lo sustente.
- Interpretación de la tipificación de no agendamiento y los datos operativos: qué frena la conversión y qué es accionable por el equipo digital.

### 2. KPIs y esquema de control de la venta
- Set de KPIs: indicador norte + indicadores por etapa.
- Por cada KPI: fórmula, frecuencia de medición, meta o benchmark y fuente del dato.
- Esquema de control y seguimiento del lead hasta la venta: estados del lead, alertas de SLA de contacto, atribución por canal/UTM, tablero. **Este es el núcleo del rol.**

### 3. Hipótesis y diseño de una prueba A/B
- Elegir un punto de fuga y diseñar un experimento para atacarlo.
- Documentar: hipótesis, variable a modificar, métrica primaria de éxito, criterio de decisión, duración/volumen aproximado, riesgos o sesgos.

### 4. Plan de acción priorizado
- Mínimo 4 iniciativas para cerrar la brecha hacia la meta en WhatsApp y Landing (enero cerró en 13 ventas vs. ~50/mes requeridas en WhatsApp).
- Priorización con un modelo explícito y estimación de impacto: cuánto movería cada iniciativa la aguja del funnel.
