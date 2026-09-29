# 02 · Arquitectura Técnica Recomendada

## Stack objetivo
- **CRM operativo**: GoHighLevel.
- **Base extendida / control**: Airtable.
- **Registro auxiliar**: Google Sheets para revisión rápida, importación/exportación y reportes simples; no sustituye GHL ni Airtable.
- **Automatización avanzada**: Make, fuera de alcance hasta Sprint 2.
- **Adquisición**: Meta Ads.
- **Seguimiento**: WhatsApp, SMS y email.
- **Documentación**: GitHub / Markdown.

## Diseño lógico
1. Ingreso de lead con metadatos de fuente y campaña.
2. Normalización de datos (teléfono, idioma, fuente, tags).
3. Alta o actualización en CRM.
4. Cálculo de lead scoring.
5. Disparo de automatizaciones según estado y temperatura.
6. Gestión de cita y seguimiento comercial.
7. Consolidación de datos en Airtable para dashboard.

## Reglas técnicas
- Buscar coincidencias por teléfono/email antes de crear contacto; resolver coincidencias ambiguas según el documento 22 sin fusionar automáticamente.
- Registrar `created_at`, `updated_at` y `last_interaction_at`.
- Toda automatización debe tener condición de salida (respuesta, cita, opt-out, cierre).
- Mantener nomenclatura consistente en campos, tags y campañas.
