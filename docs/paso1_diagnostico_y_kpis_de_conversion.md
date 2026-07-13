# Paso 1 — Diagnóstico y lectura de KPIs

## Tasas de conversión etapa a etapa

### WhatsApp

| Transición | Cálculo | Tasa |
|---|---|---|
| Autogestión (bot resuelve sin asesor) | 2.700 / 8.200 | **32,9%** |
| Desbordamiento a asesor | 5.500 / 8.200 | 67,1% |
| Desbordado → Contactado | 2.900 / 5.500 | **52,7%** |
| Contactado → Agenda | 607 / 2.900 | **20,9%** |
| Agenda → Venta | 13 / 607 | **2,1%** |
| Venta / Lead (sobre 5.500) | 13 / 5.500 | 0,24% |

### Landing

| Transición | Cálculo | Tasa |
|---|---|---|
| Sesión → Formulario iniciado | 3.200 / 48.000 | **6,7%** |
| Iniciado → Completado (lead) | 1.850 / 3.200 | 57,8% |
| Lead → Contactado | 1.200 / 1.850 | **64,9%** |
| Contactado → Agenda | 210 / 1.200 | **17,5%** |
| Agenda → Venta | 8 / 210 | **3,8%** |
| Venta / Lead (sobre 1.850) | 8 / 1.850 | 0,43% |

## Comparación landing vs. WhatsApp

| Métrica | WhatsApp | Landing | Mejor |
|---|---|---|---|
| Contactación | 52,7% | 64,9% | Landing |
| Contactado→Agenda | 20,9% | 17,5% | WhatsApp |
| Agenda→Venta | 2,1% | 3,8% | Landing (pero ambos muy bajos) |
| Venta/Lead | 0,24% | 0,43% | Landing casi el doble |

## Los 3 puntos de mayor fuga (con evidencia numérica y costo estimado)

**1. WhatsApp: 47% de leads sin gestionar** (2.600 de 5.500 leads nunca contactados) — **la fuga de mayor costo real**.
Aplicando las tasas actuales aguas abajo (20,9% contactado→agenda, 2,1% agenda→venta), esos 2.600 leads representan **≈11 ventas/mes potenciales perdidas**. El tiempo promedio de primer contacto es rápido (8h20) cuando sí ocurre — es un problema de cobertura/capacidad, no de velocidad. 100% accionable por el equipo digital/operación (enrutamiento, dimensionamiento del equipo comercial, priorización de cola).

**2. Agenda→Venta — 98% de las citas agendadas no cierran.**
WhatsApp convierte solo **2,1%** de las citas en venta (607→13) y Landing **3,8%** (210→8). Se pierden **594 citas de WhatsApp** y **202 de Landing** sin convertir — la fuga de mayor gravedad relativa, aunque más difícil de intervenir solo desde digital porque depende del proceso comercial.

**3. Landing: abandono de formulario 42%** (1.350 de 3.200 formularios iniciados no completados).
Es además la fuga de mayor volumen absoluto de todo el funnel: 93,3% de las 48.000 sesiones nunca llega a iniciar formulario.

## Interpretación de la tipificación de "no agendamiento" y datos operativos

- **39% reportado en centrales de riesgo** → no accionable por el equipo digital; es una restricción de política de crédito/riesgo aguas arriba. Sugiere revisar si vale la pena prefiltrar por scoring antes de invertir en contactar/agendar a estos leads (ahorro de esfuerzo comercial, no de conversión).
- **21% ubicación + 14% precio = 35%** → desajuste entre lo que promete la campaña/landing y el producto real. Esto **sí es accionable por digital**: mejor segmentación de pauta, filtros de calificación más tempranos en el bot, expectativas claras en la landing (rango de precio, zona) para no atraer leads que no calzan.
- **19% "otros/sin tipificar" + solo 62% de tipificación registrada** → hay un **problema de calidad de dato**: cerca de 4 de cada 10 gestiones no quedan con motivo registrado. Esto limita la confiabilidad del diagnóstico mismo — es una fuga "invisible" que hay que cerrar con disciplina de CRM antes de poder optimizar con precisión.
- **Contraste de SLA:** WhatsApp contacta más rápido (8h20) pero contacta a menos leads (52,7%); Landing contacta más lento (26h) pero a más leads (64,9%) porque su volumen es mucho menor y más manejable. La velocidad no es el cuello de botella real en WhatsApp — la **capacidad/cobertura** sí.
