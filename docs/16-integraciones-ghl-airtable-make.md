# 16 · Integraciones GHL · Airtable · Make

## Rol por herramienta
- **GoHighLevel (GHL)**: CRM operativo, pipeline, comunicaciones y citas.
- **Airtable**: capa de control, reporting, vistas administrativas y QA.
- **Google Sheets**: registro auxiliar, exportaciones parciales de respaldo, importación/exportación, revisión rápida y reportes simples. No sustituye GHL ni Airtable.
- **Make**: orquestación avanzada, transformación de datos y flujos complejos; fuera de alcance hasta Sprint 2.

## Qué debe vivir en cada sistema
| Dominio | Sistema principal |
|---|---|
| Estado comercial en tiempo real | GHL |
| Reporting extendido y control | Airtable |
| Registro auxiliar y revisión rápida | Google Sheets |
| Integración avanzada y orquestación (Sprint 2) | Make |

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
- Autoridad por campo: GHL gobierna estado comercial tras el corte; Airtable analiza y Sheets auxilia. Un timestamp reciente no permite sobrescribir la fuente autorizada.
- Marcar discrepancias para conciliación; estos contratos no acreditan sincronización instalada.

## Errores y retries
- Registro de error con contexto.
- Reintentos con backoff.
- Cola de revisión manual para fallos persistentes.

## Prevención de duplicados
- Identidad por lead_id; teléfono/email son candidatos de coincidencia, no identidad verificada. Una campaña diferente crea un evento, no otro contacto por defecto; ambigüedades requieren revisión.
- Bloqueo de creación si lead_id ya existe.

## Pendientes de validación humana
- Confirmar corte, permisos de acceso, retención y resolución manual de discrepancias.
- Consultar el [contrato de datos](22-sprint-01-dia-02-datos-crm.md) antes de configurar; no se conectan APIs en esta entrega.
