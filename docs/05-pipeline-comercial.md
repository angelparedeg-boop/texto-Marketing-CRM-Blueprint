# 05 · Pipeline Comercial Recomendado

## Estrategia
Pipeline orientado a visibilidad de conversión desde lead nuevo hasta venta cerrada y reactivación.

## Etapas
1. Nuevo Lead
2. Contacto Intentado
3. Contactado
4. Calificación Inicial
5. Cita Agendada
6. Cita Confirmada
7. Presentación Realizada
8. Documentación Solicitada
9. Aplicación Enviada
10. Venta Cerrada
11. No Calificado
12. Nutrición Largo Plazo
13. Perdido

## Operación por etapa
| Etapa | Objetivo | Acción mínima |
|---|---|---|
| Nuevo Lead | Respuesta rápida | Mensaje + tarea de llamada |
| Contactado | Confirmar interés | Preguntas de calificación |
| Cita Agendada | Asegurar asistencia | Confirmación + recordatorios |
| Presentación Realizada | Avanzar decisión | Resolver objeciones |
| Aplicación Enviada | Cerrar proceso | Seguimiento de documentación |

## SLA
- Primer contacto: 0–15 minutos.
- Segundo intento: dentro de 2 horas.
- Actualización de etapa: inmediata tras interacción.

## Configuración técnica
- Campo obligatorio `next_action_at` en etapas activas.
- Cambio automático a `no_show` cuando no hay asistencia registrada.
- Bloqueo de cierre perdido sin `disposition_reason`.

## Pendientes de validación humana
- Acordar umbral de permanencia máxima por etapa.
- Definir SLA por asesor y horario de operación.
