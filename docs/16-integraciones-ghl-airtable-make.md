# 16 · Integraciones GHL · Airtable · Make

## Rol por herramienta
- **GoHighLevel (GHL)**: CRM operativo, pipeline, comunicaciones y citas.
- **Airtable**: capa de control, reporting, vistas administrativas y QA.
- **Make**: orquestación avanzada, transformación de datos y flujos complejos.

## Qué debe vivir en cada sistema
| Dominio | Sistema principal |
|---|---|
| Estado comercial en tiempo real | GHL |
| Reporting extendido y control | Airtable |
| Integración avanzada y orquestación | Make |

## Contrato de datos (mínimo)
- lead_id
- phone_e164
- email
- source, campaign
- pipeline_stage
- lead_score
- next_action_at
- last_interaction_at
- consent_sms
- consent_email
- consent_whatsapp
- opt_out_status

## Eventos
- lead_created
- lead_updated
- appointment_booked
- appointment_confirmed
- no_show
- presentation_completed
- closed_won
- closed_lost
- reactivation_started

## Reglas de sincronización
- GHL como fuente operativa primaria.
- Sincronización incremental por timestamp.
- Resolución de conflicto por `updated_at` más reciente.

## Errores y retries
- Registro de error con contexto.
- Reintentos con backoff.
- Cola de revisión manual para fallos persistentes.

## Prevención de duplicados
- Llave por teléfono + email + source.
- Bloqueo de creación si lead_id ya existe.

## Pendientes de validación humana
- Confirmar política final de resolución de conflictos.
