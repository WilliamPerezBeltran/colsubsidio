# Paso 3 — Hipótesis y diseño de prueba A/B

## Punto de fuga elegido

**WhatsApp: 47% de leads sin gestionar** (fuga #2 del diagnóstico). Se elige sobre "agenda→venta" porque es 100% accionable por el equipo digital (cambio en el flujo del bot, no depende del proceso comercial/ventas) y es la palanca más rápida de probar con impacto medible en pocas semanas.

## Hipótesis

*Si el bot envía un mensaje de seguimiento automático con opción de auto-agendamiento a los leads desbordados que no han sido contactados por un asesor en 2 horas, entonces aumentará la tasa de agendamiento sin necesitar más capacidad humana, porque se reduce la pérdida de leads "huérfanos" en cola de espera.*

## Variable a modificar

Presencia/ausencia de un mensaje automático de seguimiento (con link de auto-agendamiento) disparado a las 2h sin contacto humano.

- **Control (A):** flujo actual — el lead espera en cola hasta que un asesor lo contacte.
- **Variante (B):** a las 2h sin contacto humano, el bot envía mensaje automático + opción de agendar cita directamente, sin esperar al asesor.

## Métrica primaria de éxito

**Tasa de agendamiento sobre leads recibidos** (Agendados / Leads recibidos). Línea base actual: 607/5.500 = **11,0%**.

*Métricas secundarias (guardrail):* % de leads sin gestionar a 48h, tasa de asistencia a cita, tasa de cierre (agenda→venta) — para verificar que el aumento de agendamientos no sea de baja calidad.

## Criterio de decisión

B gana si mejora la tasa de agendamiento en **≥ 3 puntos porcentuales** (11,0% → 14,0%, +~27% relativo) con significancia estadística al 95% (test de dos proporciones, una cola dado que la hipótesis es direccional), **sin degradar** la tasa de asistencia a cita más de 5 puntos frente al control.

## Duración / volumen aproximado

Con p1=11,0%, p2=14,0%, α=0,05, potencia=80%: se requieren **~1.900 leads por grupo (~3.800 en total)**. Con ~5.500 leads/mes en WhatsApp repartidos 50/50, esto se alcanza en **3-4 semanas**; se recomienda correr un ciclo completo de 4 semanas para evitar sesgo por día de la semana.

## Riesgos y sesgos

- **Contaminación entre grupos:** los mismos asesores atienden ambos grupos y podrían cambiar su comportamiento al notar el efecto de la variante. Mitigación: asignación aleatoria a nivel de lead dentro del propio bot, de forma transparente para el asesor.
- **Estacionalidad:** enero puede no ser representativo (post-fin de año); si el test corre en otro mes, validar que el resultado generalice.
- **Calidad vs. cantidad:** el auto-agendamiento sin filtro de asesor podría inflar citas de baja calidad (leads con riesgo/ubicación/precio no aptos). Por eso la tasa de asistencia y de cierre van como guardrail, no solo el agendamiento.
- **Muestra insuficiente para "venta":** con solo 13 ventas/mes en la base total, la tasa de cierre no alcanzará significancia estadística en 4 semanas — se reporta como exploratoria, no como criterio de decisión.
- **Saturación de agenda comercial:** si se agenda más sin aumentar capacidad de atención, puede bajar la tasa de asistencia/cierre por sobrecarga — monitorear capacidad del equipo comercial en paralelo.
