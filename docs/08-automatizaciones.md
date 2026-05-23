# 08 · Catálogo de Automatizaciones

## Separación
- **Estrategia**: aumentar contacto, citas y cierres.
- **Operación**: secuencias por estado.
- **Configuración técnica**: trigger, condiciones, salida y control de errores.

## Flujos principales
| Flujo | Trigger | Acción clave | Salida |
|---|---|---|---|
| Lead nuevo | lead_created | mensaje inmediato + tarea llamada | respuesta, cita u opt-out |
| Seguimiento 7 días | sin respuesta | cadencia multicanal | respuesta, cita u opt-out |
| Cita agendada | appointment_booked | confirmación + recordatorios | asistencia o no-show |
| No-show | no asistencia | recuperación + reagenda | nueva cita o nutrición |
| Post-presentación | presentación completada | seguimiento por objeción | aplicación o perdido |
| Venta cerrada | closed_won | onboarding + referidos | cliente activo |
| Reactivación | reactivation_started | secuencia educativa | respuesta o no interés |

## Reglas técnicas
- Cada flujo debe tener límite de intentos.
- Implementar ventanas horarias de envío.
- Evitar duplicados con llave: `lead_id + workflow_id + step`.
- Registrar errores y retries.

## Pendientes de validación humana
- Definir horarios de contacto por zona.
- Aprobar textos finales de cada canal.
