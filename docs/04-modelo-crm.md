# 04 · Modelo de Datos CRM

## Separación por capas
- **Estrategia**: qué información permite segmentar, priorizar y convertir.
- **Operación**: qué campos necesita el asesor para ejecutar seguimiento.
- **Configuración técnica**: tipos de campo, reglas y validaciones.

## Entidades principales

## 1) Contacto (Lead)
### Campos obligatorios (operación)
- Nombre completo
- Teléfono (E.164)
- Email
- Estado (EE. UU.)
- Idioma
- Fuente
- Campaña
- Interés principal
- Edad aproximada
- Estado civil
- Hijos/dependientes
- Ingreso estimado
- Ocupación
- Seguro actual
- Urgencia
- Puntuación del lead
- Próxima acción
- Última interacción
- Notas
- Resultado
- consent_sms
- consent_email
- consent_whatsapp
- opt_out_status

### Configuración técnica sugerida
| Campo | Tipo | Regla |
|---|---|---|
| lead_id | Texto/UUID | Único, no editable |
| phone_e164 | Texto | Obligatorio, normalizado |
| source | Lista | Catálogo cerrado |
| lead_score | Número | 0–100 |
| next_action_at | Fecha/hora | Obligatorio si etapa activa |

## 2) Oportunidad
- opportunity_id
- lead_id
- etapa del pipeline
- asesor asignado
- fecha de cita
- estado de presentación
- estado de aplicación
- resultado final
- motivo de pérdida

## 3) Actividad
- Tipo de actividad (llamada, SMS, WhatsApp, email, nota, tarea)
- Resultado de actividad
- Fecha/hora
- Usuario o automatización

## Reglas de calidad de datos
1. No crear oportunidad sin lead_id válido.
2. No marcar perdido sin motivo de pérdida.
3. No mantener más de 48h una oportunidad sin próxima acción.
4. Toda cita requiere fecha/hora y confirmación.

## Pendientes de validación humana
- Definir lista final de motivos de pérdida.
- Confirmar campos financieros permitidos por compliance.
