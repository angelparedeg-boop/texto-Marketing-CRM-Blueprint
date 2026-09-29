# Sistema Estratégico de Marketing Digital + CRM

Repositorio: `angelparedeg-boop/texto-Marketing-CRM-Blueprint`. Seguros de vida indexados, IUL, protección familiar y productos financieros. Consolidación documental del 29/09/2026 basada en `main` (`f990992`).

Blueprint técnico y operativo del sistema de Marketing Digital + CRM para captación, seguimiento, calificación, nutrición, agendamiento y conversión de leads en seguros de vida, IUL, protección familiar y planificación financiera para el mercado hispano en Estados Unidos.

## Objetivo
Construir un sistema comercial automatizado que conecte:

Fuente de lead → Anuncio / campaña / video / avatar → Landing page → Formulario / Quiz → CRM → Lead scoring → Automatización → Cita → Presentación → Aplicación → Cierre → Referidos → Reactivación → Reporting y optimización.

## Decisiones vigentes

Público: **Familias hispanas de 30 a 65 años en Estados Unidos**, con subsegmentos 30–40, 41–55 y 56–65. Oferta: **Diagnóstico Financiero Familiar Gratuito**. Primero campaña y captación, después CRM completo y finalmente integraciones. Canal inicial: Meta Ads + landing/formulario + CRM; separar orgánico de pagado.

| Herramienta | Rol objetivo |
|---|---|
| GoHighLevel | CRM operativo principal; no se afirma configurado |
| Airtable | Control, QA, reporting y análisis operativo |
| Google Sheets | Registro auxiliar, exportaciones parciales de respaldo, importación/exportación, revisión rápida y reportes simples |
| Make | Automatización avanzada fuera de alcance hasta Sprint 2 |

Sheets no sustituye GoHighLevel ni Airtable. Un piloto provisional no cambia la autoridad comercial prevista en GHL. Una hoja exportada no es un respaldo completo del CRM.

## Estructura de documentación
- `docs/01-system-map.md`
- `docs/02-arquitectura-tecnica.md`
- `docs/03-avatar-oferta-posicionamiento.md`
- `docs/04-modelo-crm.md`
- `docs/05-pipeline-comercial.md`
- `docs/06-lead-scoring.md`
- `docs/07-taxonomia-tags.md`
- `docs/08-automatizaciones.md`
- `docs/09-funnel-principal.md`
- `docs/10-sop-seguimiento-comercial.md`
- `docs/11-biblioteca-mensajes.md`
- `docs/12-compliance-consentimiento.md`
- `docs/13-kpi-dictionary.md`
- `docs/14-dashboard-operativo.md`
- `docs/15-matriz-experimentacion.md`
- `docs/16-integraciones-ghl-airtable-make.md`
- `docs/17-qa-checklists.md`
- `docs/18-roadmap-30-60-90.md`
- `docs/19-backlog-tecnico.md`
- `docs/20-sprint-01-implementacion.md`
- `docs/21-sprint-01-dia-01-alineacion.md`
- [Día 2: Datos CRM y contrato de información](docs/22-sprint-01-dia-02-datos-crm.md)
- [Día 6: Campañas, avatares, voces y registro de respuesta](docs/26-sprint-01-dia-06-campanas-avatares-voces-registro.md)

Los documentos 23–25 solicitados no existen con esos nombres en `main`. Hay equivalentes locales con nombres abreviados, conservados en su ubicación original. No se renumeran ni se presentan como fusionados. El Día 6 amplía el plan original de cinco días; su preparación creativa se adelanta a captación.

## Documentos legado
- `docs/legacy/09-dashboard-kpis.md`
- `docs/legacy/10-compliance-consentimiento.md`

## Alcance actual
Esta fase documenta estrategia, operación y configuración técnica recomendada. No conecta APIs, no configura herramientas externas y no usa credenciales.
