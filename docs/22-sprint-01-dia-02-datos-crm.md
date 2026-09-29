# Día 2 del Sprint 1: Datos CRM y contrato de información

Versión documental 1.0 · 29/09/2026 · Estado: especificado, pendiente de aprobación y configuración.
Nuevo respecto de main f990992. Se revisó el documento 22 de la reconstrucción local R1 y se conservan sus principios de eventos, permisos acotados e identidad ambigua. El original local no se modifica; esto no recupera el commit 531f410 ni acredita configuración GHL.

## 1. Objetivo del Día 2
Definir datos mínimos, autoridad y reglas para captar una solicitud, atenderla y seguir su resultado sin duplicar personas ni perder origen. Primero captación; después CRM e integraciones.

## 2. Alcance del contrato de datos CRM
Especificación lógica independiente del proveedor. Nombres técnicos propuestos, no nombres de campos nativos ni formato de importación GHL validado. No se conectan APIs, crean credenciales ni configuran cuentas.

## 3. Principios del modelo de datos
Una persona puede tener varias captaciones, oportunidades y citas. Conservar eventos originales y distinguir datos declarados de datos verificados. Fechas ISO 8601 UTC más zona IANA cuando corresponda. Null significa desconocido/no recopilado; nunca rechazo ni consentimiento. No pedir salud, ingresos ni documentos en la captación mínima. Confirmar recepción solo después de persistencia durable; guardar antes de agenda.

## 4. Entidades principales
| Entidad | Identificador y relación | Función |
|---|---|---|
| Contacto / Lead | lead_id, UUID estable | Identidad y seguimiento consolidado |
| Evento de captación | submission_id, relacionado con lead_id | Solicitud inmutable, origen, formulario y evidencia |
| Oportunidad | opportunity_id → lead_id | Proceso comercial independiente |
| Actividad | activity_id → lead_id; opportunity_id opcional | Intento, conversación, tarea o nota |
| Cita | appointment_id → lead_id y oportunidad si aplica | Agenda y resultado independiente |
| Campaña / pieza | campaign_id; creative_id + creative_version | Oferta, mensaje y versión audiovisual |
| Registro de consentimiento | consent_id → lead_id; submission_id si existe | Canal, finalidad, evidencia y revocación |
| Secuencia de automatización | sequence_run_id → lead_id; trigger_event_id | Ejecución, pausas y resultados; solo especificada |
| Registro auxiliar de Google Sheets | google_sheet_row_id → lead_id / submission_id | Copia identificable, nunca nueva identidad |

## 5. Campos obligatorios del contacto/lead
| Campo | Tipo | Obligatoriedad y regla |
|---|---|---|
| lead_id | UUID | Siempre; generado de forma controlada, inmutable |
| full_name | Texto | Obligatorio; no separar nombres automáticamente |
| first_name, last_name | Texto nullable | Enriquecimiento opcional; no inventar apellidos |
| phone_e164 | Texto nullable | Obligatorio si canal telefónico; normalizar cuando país y número lo permitan |
| email | Texto nullable | Obligatorio si canal email; al menos teléfono o email válido |
| preferred_channel | Enum | email, telefono, sms, whatsapp; habilitar solo canales atendibles |
| preferred_language | Enum | es, en, otro, desconocido; registrar declarado o contexto del formulario |
| state_us | Texto | Código de estado EE. UU. o DC; atendibilidad se revisa aparte |
| product_interest | Enum nullable | proteccion_familiar, vida, iul, retiro, legado, revision_poliza, otro, desconocido |
| avatar_segment | Enum | 30_40, 41_55, 56_65, fuera_rango, desconocido; solo si se conoce, sin exigir edad |
| created_at, updated_at | Fecha/hora | Generadas por el sistema responsable |
| source | Enum | meta, referido, manual, otro, desconocido; primer origen conocido |
| source_channel | Enum | facebook_paid, instagram_paid, facebook_organic, instagram_organic, referral, manual, other, unknown |
| owner_advisor | ID interno | Todo lead activo debe tener responsable; no un nombre ficticio en producción |
| lifecycle_status | Enum | nuevo, en_seguimiento, cliente, inactivo; independiente del opt-out |
| next_action, next_action_at | Texto + fecha/hora | Obligatorios en lead activo; no prometer SLA sin confirmarlo |
| last_interaction_at | Fecha/hora nullable | Solo interacción registrada; ausencia no implica falta de respuesta |

No exigir ambos contactos. Origen observado desconocido se conserva como tal; no rechazar una solicitud válida por ausencia de UTM.

## 6. Campos de oportunidad
opportunity_id y lead_id obligatorios; pipeline_stage, owner_advisor, created_at, updated_at, next_action, next_action_at y disposition_reason condicional. presentation_status y application_status separan presentación, solicitud, evaluación y emisión. Una emisión no prueba cliente efectivo ni comisión cobrada.

pipeline_stage propuesto: nuevo, contacto_intentado, conversacion_iniciada, cita_agendada, presentacion, solicitud, evaluacion, emitida, cliente, perdido. Antes de mapear al pipeline nativo conciliar con [05](05-pipeline-comercial.md); etiquetas visibles pueden variar sin cambiar significados. Perdido requiere disposition_reason; cita_agendada requiere appointment_id y appointment_datetime.

## 7. Campos de actividad e interacción
activity_id, lead_id, occurred_at, actor_id, activity_type, outcome y nota mínima. activity_type: llamada, sms, whatsapp, email, nota, tarea. outcome: intento, conversacion, completada, fallida, pendiente, desconocido. delivery_status y provider_message_id solo cuando exista evidencia del proveedor. Un intento no equivale a conversación ni un log a entrega.

## 8. Campos de cita
appointment_id, lead_id, appointment_datetime, appointment_timezone, appointment_status, confirmation_status, attendance_status, rescheduled_from_id y updated_at.
appointment_status: agendada, cancelada, reprogramada, completada.
confirmation_status: pendiente, confirmada, rechazada.
attendance_status: desconocida, asistio, no_asistio_confirmado.
Una cita pasada sin evidencia mantiene asistencia desconocida. Reprogramar conserva historial y debe invalidar recordatorios obsoletos.

## 9. Campos de campaña y atribución
Por evento: submission_id, lead_id, submitted_at, campaign_id, campaign_name, ad_id, adset_id, platform, source, source_channel, utm_source, utm_medium, utm_campaign, utm_content, landing_page, form_version.
platform: facebook, instagram, otra, desconocida. source_channel describe adquisición, no canal preferido de contacto.
Todo lead digital conserva source y campaign_id o campaign_name cuando se conocen; usar source=desconocido y una bandera de calidad si no hay información. No inventar campaña para llenar un campo.
Mantener primer origen conocido del contacto y todas las captaciones posteriores. Las UTM son atribución observada, no identidad ni conversión transmitida a Meta. No incluir contactos en URLs.

## 10. Campos para campañas audiovisuales, avatares y voces
| Campo | Uso y validación |
|---|---|
| creative_id, creative_version | Identificador estable y versión; cambio de pieza genera versión |
| creative_type | imagen, video_presentador, video_avatar, video_broll, texto, otro, desconocido |
| avatar_used | ID y versión del presentador; no es avatar_segment |
| voice_version | Referencia a versión de voz; sin muestras personales |
| message_angle | proteccion_familiar, retiro, legado, revision_poliza, educativo, otro |
| voice_type | grabada, sintetica, clonada, sin_voz, pendiente |
| asset_status | borrador, exportado_revisado, listo_para_cargar, publicado, activa |

Campañas audiovisuales deben resolver creative_type, avatar_used, voice_version y message_angle cuando apliquen. Ausencia no demuestra “sin voz/avatar”: marcar pendiente/desconocido y revisar el catálogo. Datos de pieza se contrastan con el catálogo, no se confían ciegamente a parámetros de URL.

## 11. Campos de consentimiento y opt-out
consent_sms, consent_email, consent_whatsapp: true, false o null; solo true con evidencia habilita el alcance autorizado. Son resúmenes por finalidad del registro, nunca autorización universal.
Registro: consent_id, lead_id, channel, purpose, consent_status (otorgado, denegado, revocado, desconocido), consent_timestamp, text_version, evidence_ref, revoked_at. Solicitud de llamada también requiere evidencia de canal y finalidad.
opt_out_status: ninguno_registrado, parcial, total, desconocido. Guardar canal/finalidad afectados y fecha; ninguno_registrado no prueba permiso.
Comprobar permiso y baja justo antes de enviar. Una nueva solicitud no revoca automáticamente una baja. No activar SMS, email ni WhatsApp sin permiso correspondiente; una solicitud solo permite el alcance explícito de respuesta.

## 12. Campos para lead scoring
lead_score: entero 0–100 nullable; score_band: muy_caliente, calificado, tibio, frio, no_prioritario, sin_datos. score_version, score_updated_at, score_inputs y manual_override_reason permiten reproducirlo.
Propuesta existente de [06](06-lead-scoring.md): 80–100, 60–79, 40–59, 20–39, 0–19. Aplicar max(0, min(100, suma)); desconocidos no son respuestas negativas. Sin respuestas pertinentes: null/sin_datos. Condiciones opuestas no suman simultáneamente; cada regla cuenta una vez. Modelo provisional para prioridad, no probabilidad validada ni elegibilidad del seguro.
Todo lead caliente debe tener próxima acción; la misma protección se extiende a cualquier lead activo.

## 13. Campos para seguimiento comercial
owner_advisor, next_action, next_action_at, last_interaction_at, attempt_count, followup_status y disposition_reason.
followup_status: nuevo, contacto_intentado, conversacion_iniciada, cita_agendada, cerrado_sin_cita. Baja se registra aparte.
Secuencias: sequence_run_id, trigger_event_id, sequence_version, run_status, current_step, scheduled_at, attempt_count, last_error y idempotency_key. run_status: pendiente, activa, pausada, completada, cancelada, fallida. Respuesta, cita, cierre o baja debe reevaluar pendientes. Límite de intentos, horario y responsable pendientes de aprobación; no hay envíos en esta entrega.

## 14. Campos para reporting en Airtable
airtable_record_id nullable, lead_id, opportunity_id, submission_id, campaign_id, creative_id, creative_version, source_channel, cohort_date, cutoff_at, owner_advisor, pipeline_stage, quality_flags y source_updated_at. Replicar datos mínimos; sin muestras de voz ni evidencia privada completa.
Métricas: solicitudes, leads válidos únicos, intentos, conversaciones, citas, asistencias, pendientes y gasto atribuible. Conservar numerador, denominador, fechas y fuente; cero denominador produce “sin datos”.

## 15. Campos para registro auxiliar en Google Sheets
google_sheet_row_id: ID estable de registro auxiliar, no número físico de fila.
google_sheet_sync_status: no_configurado, pendiente, conciliado, error, conflicto. “Conciliado” solo tras comprobación; no implica sincronización automática.
Áreas propuestas: Entradas (submission_id/origen/permiso), Seguimiento (lead_id/responsable/próxima acción), Campañas (IDs/versiones/estado), Control (export_id/fecha/conteos/discrepancias). Operación auxiliar con acceso restringido. No se crea hoja en esta entrega.

## 16. Valores permitidos por campo
Enums definidos en secciones 5–15 constituyen el catálogo v1. IDs: texto/UUID según sistema de origen y mapa estable de equivalencias, nunca posición de fila. Texto opcional: null si ausente. UTM y nombres de campaña son texto controlado, no enums inventados. Estado: abreviatura postal válida; fechas: ISO 8601.
disposition_reason: sin_interes, fuera_territorio, no_contactable, pospuesto, duplicado_confirmado, otro. “Otro” exige nota; falta de respuesta no es rechazo. Versionar ampliaciones del catálogo y revisar datos previos; no sustituir valores silenciosamente.

## 17. Reglas de validación
Validar en servidor o mecanismo equivalente: mínimos, formato de contacto, estado, enums y relaciones. No crear oportunidad sin contacto. No mover a perdido sin motivo ni a cita_agendada sin fecha y cita. Rechazar IDs/eventos inconsistentes sin éxito falso. Texto se almacena como datos y se escapa al mostrar; neutralizar fórmulas al exportar CSV. Vistas internas restringidas; logs sin datos personales.

## 18. Reglas de deduplicación
Reintento con mismo submission_id y contenido: devolver el resultado original sin nueva tarea/contacto. Mismo ID con contenido distinto: conflicto para revisión.
Coincidencia de email/teléfono: buscar antes de crear; no crear automáticamente otro contacto cuando la identidad esté confirmada. Teléfono compartido, nombre distinto o email y teléfono apuntando a contactos diferentes: conservar evento pendiente y revisión de identidad, sin fusión automática ni nuevos envíos.
Campaña diferente de persona confirmada conserva el mismo lead_id y un evento nuevo. El piloto local R1 usa email + nombre y revisión de teléfono; es una heurística de prueba, no verificación de titularidad. Cualquier fusión futura conserva IDs anteriores, eventos y evidencia.

## 19. Reglas de calidad de datos
Medir completitud sobre campos aplicables, contactos válidos, duplicados confirmados, pendientes de identidad, origen desconocido y leads activos sin próxima acción. Mostrar conteos y denominadores de la misma cohorte/corte. Los umbrales antiguos 95/90/100 no se adoptan sin definición y aprobación.
Retención, eliminación, accesos y responsable de revisión pendientes antes de datos reales. Una exportación parcial no respalda conversaciones, adjuntos y configuración.

## 20. Qué debe vivir en GoHighLevel
Contacto, oportunidad, pipeline, actividades, citas, tareas, responsable, próximas acciones, permisos/bajas y referencia a eventos. Tras un corte verificado, GHL es autoridad del estado comercial. Primero comprobar funciones nativas y mapeo real; no afirmar cuenta configurada.

## 21. Qué debe replicarse en Airtable
Control, QA, métricas y referencias mínimas de trazabilidad según sección 14. No sobrescribir estado comercial de GHL por un updated_at más nuevo. Discrepancias van a conciliación; dirección, frecuencia y acceso se especificarán al autorizar integración.

## 22. Qué puede registrarse en Google Sheets
Entradas auxiliares, exportaciones parciales de respaldo, preparación de importaciones, revisión rápida, presupuesto y reportes. No sustituye GHL ni Airtable y no es fuente principal de verdad comercial. Un piloto provisional se identifica como tal hasta transferencia reconciliada.

## 23. Qué queda fuera de alcance hasta Sprint 2
Make, conexiones API, sincronizaciones, activación de secuencias externas y migración de producción. Preparar después mapa real de campos, muestra ficticia, ensayo repetible, conteos/discrepancias, corte y recuperación. No inventar importaciones admitidas por proveedor.

## 24. Checklist de cierre del Día 2
- [x] Entidades, campos, catálogos y autoridad documentados.
- [x] Captación separada de identidad, oportunidades y citas.
- [x] Deduplicación, permisos y origen desconocido especificados.
- [ ] Aprobar mapeo nativo, responsables, SLA, retención y accesos.
- [ ] Probar reintentos, errores y migración con datos ficticios en entorno autorizado.
- [ ] Conciliar conteos y verificar bajas antes de operación.
Estado de esta entrega: revisión documental; los checks no acreditan ejecución externa.

## 25. Próximo paso: Día 3 - Pipeline comercial
Contrastar [pipeline existente](05-pipeline-comercial.md) con entradas/salidas, motivos, citas y próximas acciones de este contrato. Existe un borrador local 23-sprint-01-dia-03-pipeline.md que debe compararse antes de cualquier incorporación; no renombrarlo ni reconstruirlo como si estuviera perdido. La preparación de campaña del [Día 6](26-sprint-01-dia-06-campanas-avatares-voces-registro.md) se adelanta en la secuencia de captación.
