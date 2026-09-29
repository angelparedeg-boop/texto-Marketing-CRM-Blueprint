# Día 6 del Sprint 1: Campañas, avatares, voces y registro de respuesta del mercado

Versión documental 1.0 · 29/09/2026 · Estado: especificado, producción y lanzamiento pendientes.
Ampliación estratégica del Sprint 1. Su preparación se adelanta a captación; conserva el plan original de cinco días y la numeración.
Se revisó el documento local 26, que referencia el paquete CAP-001; los activos permanecen en su proyecto original. No se verificaron sus archivos audiovisuales en esta entrega, que no exporta videos ni sustituye el piloto local.

## 1. Objetivo del Día 6
Conectar mensaje, campaña, presentador, voz y formulario con las solicitudes y su seguimiento, para observar respuesta del mercado sin confundir atribución con causalidad.

## 2. Alcance
Documentar brief, guiones, producción, catálogo audiovisual, registro de origen, métricas y revisión previa. No conectar APIs, configurar herramientas externas, crear credenciales, publicar ni activar campañas. Público: familias hispanas de 30–65 en EE. UU.; oferta CAP-001: Diagnóstico Financiero Familiar Gratuito; CTA: “Solicita tu diagnóstico gratuito”. Duración pública pendiente de confirmación.

## 3. Tipos de campañas iniciales
| Campaña / uso | Ángulo | Subsegmentos y canal |
|---|---|---|
| CAP-001 educativa | Protección familiar y claridad de necesidades | 30–40, 41–55 y 56–65; Facebook/Instagram |
| Variante educativa de CAP-001 | Retiro, legado o revisión de pólizas según necesidad | 41–55 y 56–65; separar prueba de mensaje |
| Difusión orgánica | Pregunta educativa y diagnóstico | Facebook/Instagram orgánicos |
| Publicidad pagada propuesta | Misma oferta y destino | Meta Ads; presupuesto y activación pendientes |

30–40: protección inicial, hijos pequeños y estabilidad familiar temprana. 41–55: consolidación, ahorro, educación de hijos y retiro. 56–65: pre-retiro, legado, revisión de pólizas y protección patrimonial. Segmentación comunicativa no determina elegibilidad.
Comparar aperturas manteniendo oferta/destino y demás condiciones; no convertir muestras pequeñas en conclusiones estadísticas.

## 4. Uso de avatares
Distinguir avatar del cliente (segmento) y avatar presentador (personaje). La continuidad local registra elección de personaje ficticio y Miriam; se conserva esa decisión sin volver a elegir a Ángel por defecto. Presentador ficticio AV-FIC-01-R1: chaqueta azul, camisa marfil, fondo verde suave y plano medio. La propuesta estática existente no acredita animación.
Para Miriam: autorización y materiales privados pendientes según el registro consultado. No subir retratos personales al repositorio público. Registrar avatar_id, versión, autorización privada cuando corresponda y estado. Comprobar consistencia visual, gestos y sincronía labial antes de aprobar clip.

## 5. Uso de voces grabadas o generadas
voice_type: grabada, sintetica, clonada, sin_voz o pendiente. voice_version identifica una versión reproducible; documentar idioma, pronunciación y ajustes.
La continuidad local registra voz sintética del ficticio por seleccionar y clonación de Miriam pendiente de autorización, muestra privada y proveedor. No se presupone permiso por la intención de obtenerlo. Una pista genérica temporal no satisface clonación.
Guía preparatoria: habitación silenciosa, micrófono estable, sin música ni voces ajenas, lectura natural, conservar original sin compresión destructiva. Duración/formato definitivos dependen de requisitos vigentes del proveedor, aún no seleccionado. Guardar permisos/muestras en almacenamiento privado; Git solo lleva referencias sin secretos.

## 6. Videos para redes sociales
Objetivos de trabajo: vertical 9:16 (1080×1920) para Reels/Stories y 4:5 (1080×1350) para feed. Son objetivos, no especificaciones vigentes certificadas; verificar destino antes de exportar.
Montaje previsto: presentador, narración, imágenes de apoyo, textos, subtítulos, música autorizada si se utiliza y cierre CTA. Revisar zonas cubiertas por interfaz, legibilidad móvil, sincronización y volumen.
Paquete requerido: video reproducible, versión sin subtítulos incrustados, portada, imagen, SRT sincronizado, audio separado, fuentes/proyecto editable o instrucciones reproducibles. No existen exportaciones finales acreditadas en esta consolidación.
Estados: borrador → exportado y revisado técnicamente → listo para cargar → publicado → campaña activa. “Listo para cargar” exige archivos finales, destino funcional y revisiones resueltas; publicación/activación requieren autorización aparte.

## 7. Guiones base
Borrador principal CAP-001, duración estimada 30–45 s que debe medirse con narración real:
“¿Hace cuánto revisaste cómo está protegida tu familia? Las necesidades cambian con los hijos, el trabajo y los planes de retiro. En un Diagnóstico Financiero Familiar Gratuito podemos conversar sobre tus prioridades, revisar qué protección tienes y ordenar las preguntas que conviene resolver. Recibirás una orientación inicial para identificar el siguiente paso según tu situación. Solicita tu diagnóstico gratuito en el formulario y elige cómo prefieres que coordinemos la conversación.”

Apertura alternativa: “Tu familia cambia. ¿Tu plan de protección también?” Mantener el resto del guion y la oferta.
Cierre visual: “Diagnóstico Financiero Familiar Gratuito · Solicita tu diagnóstico gratuito”. No prometer duración, licencia ni resultados sin revisión.
| Tiempo orientativo | Plano/recurso | Texto visual |
|---|---|---|
| 0–5 s | Presentador, plano medio | ¿Cómo está protegida tu familia? |
| 5–15 s | Apoyo visual familiar autorizado | Tus necesidades cambian |
| 15–30 s | Presentador + tres puntos legibles | Prioridades · Protección · Próximo paso |
| 30–40 s | Cierre con CTA | Solicita tu diagnóstico gratuito |

Ejemplo técnico opcional para una pieza distinta: visual “Seguro de vida indexado IUL”; voz “Seguro de vida indexado, conocido como ai-yu-el”. No añadir afirmaciones sobre impuestos, rentabilidad o garantías sin revisión de producto.
Calendario propuesto, sin programar publicaciones: día 1 principal orgánico, día 3 apertura alternativa, día 5 contenido educativo, día 7 revisión de solicitudes y atención. Piloto pagado depende de presupuesto, capacidad y aprobación.

## 8. Campos necesarios para registrar respuesta del mercado
Usar [contrato del Día 2](22-sprint-01-dia-02-datos-crm.md): submission_id, lead_id, fecha, campaign_id, campaign_name, ad_id, adset_id, platform, source_channel, creative_id, creative_version, creative_type, avatar_used, voice_version, message_angle, landing_page, form_version, utm_source, utm_medium, utm_campaign y utm_content. Añadir responsable, próxima acción y evidencia de solicitud.
ID propuesto: CAP-001 / CAP-001-V01 / R1; avatar y voz tienen versiones independientes. Campos no aplicables o desconocidos se distinguen.
Ejemplo ilustrativo no operativo: https://example.invalid/diagnostico?campaign_id=CAP-001&creative_id=CAP-001-V01&creative_version=R1&utm_source=facebook&utm_medium=paid_social&utm_campaign=CAP-001&utm_content=CAP-001-V01-R1
No incluir email/teléfono en enlaces. Guardar solicitud antes de agenda. Reintentar no duplica evento; otra campaña conserva nuevo evento. UTM no prueba envío de conversiones a Meta.

## 9. Cómo se relaciona con GoHighLevel
Destino comercial objetivo para contactos, oportunidades, tareas y citas. Vincular eventos y versiones de piezas; conservar primer origen conocido y eventos posteriores. No interpretar el rol aprobado como cuenta configurada. No se crea conexión en esta entrega.

## 10. Cómo se relaciona con Airtable
Control/QA y reporting por campaña, pieza, voz, segmento y cohorte; referencias al contacto y oportunidad, mínima información personal. Detectar faltantes, atribución desconocida y atención pendiente. GHL conserva autoridad comercial tras el corte.

## 11. Cómo se relaciona con Google Sheets
Registro auxiliar de catálogo de campañas, entradas, revisión, importación/exportación, presupuesto y reportes simples. No sustituye GHL ni Airtable; un respaldo parcial no cubre conversaciones, adjuntos ni configuración. La continuidad local describe una hoja de prueba; no se verificó ni modificó en esta entrega.

## 12. Métricas mínimas de campaña
| Métrica | Definición y límite |
|---|---|
| Solicitudes | submission_id distintos de la cohorte; excluir reintentos |
| Leads válidos únicos | lead_id consolidados con contacto válido; separar identidad por revisar |
| Intentos / conversaciones | Actividades clasificadas; intento no equivale a respuesta |
| Citas / asistencias | Citas distintas y asistencia comprobada; desconocida no es no-show |
| Pendientes | Leads activos con próxima acción y responsable; faltantes separados |
| CPL válido | Gasto atribuible / leads válidos únicos del mismo alcance |
| CTR | Clics / impresiones de la misma fuente y período |
| Conversión landing | Solicitudes / visitas medidas con definición de sesión consistente |

Guardar cohorte, corte, zona, numeradores, denominadores y fuente del gasto. Denominador cero o medición ausente: “sin datos”. Separar orgánico/pagado; no atribuir ingreso a primas ni confundir atribución con causalidad. No existen resultados comerciales de prueba en esta entrega.

## 13. Reglas de cumplimiento para mensajes audiovisuales
Criterios internos pendientes de revisión final contra producto, aseguradora, territorio y reglas vigentes antes de publicar; no constituyen certificación legal.
Evitar testimonios inventados, credenciales no verificadas, promesas absolutas, resultados garantizados y equivalencias engañosas entre seguro e inversión. Identificar presentador ficticio y obtener autorización para representación/voz personal. Verificar música/imágenes y derechos de uso comercial. Alinear promesa del anuncio, landing y confirmación. Separar coordinación solicitada de marketing posterior y respetar bajas por canal/finalidad.

## 14. Reglas de pronunciación y locución para términos técnicos
Regla obligatoria: en pantalla puede mostrarse **IUL**; el guion de voz debe escribirlo fonéticamente.
- Inglés: **eye-you-ell**.
- Español para audiencia hispana: **ai-yu-el**.
- Primera mención recomendada: **“Indexed Universal Life, conocido como ai-yu-el”**.
- Menciones posteriores: **“ai-yu-el”**.

No enviar IUL literal al motor de voz. Separar texto visual y locución; escuchar la prueba y corregir acento, pausas, ritmo y pronunciación antes de producir narración completa.

## 15. Checklist antes de publicar
- [ ] Mensaje/producto/territorio y datos públicos del asesor verificados.
- [ ] Titular de voz, autorización privada y derechos del presentador resueltos.
- [ ] Voz y avatar revisados; clonación/animación acreditadas si se anuncian.
- [ ] Locución fonética comprobada por escucha.
- [ ] Montaje completo revisado con sonido en ambos formatos.
- [ ] MP4, portada, audio, SRT y fuentes finales disponibles.
- [ ] Landing funcional, solicitud persistida antes de agenda y reintentos comprobados.
- [ ] Origen, permiso, responsable, próxima acción y bajas verificados en destino real.
- [ ] Presupuesto máximo, horario, capacidad, criterios de pausa y autorización de publicación resueltos.
Ninguna casilla se da por cumplida solo por documentación o por un retrato estático.

## 16. Qué queda fuera de alcance hasta Sprint 2
Make, sincronizaciones y automatizaciones avanzadas, conversiones server-side, atribución multicanal avanzada y escalado. La producción audiovisual y captación siguen siendo compromisos de Fase 1; sus pendientes no desaparecen al aplazar integraciones.

## 17. Próximo paso después del Día 6
Revisar el contrato 22 y el paquete creativo local existente; resolver materiales privados, proveedor/costo, destino, atención y condiciones de lanzamiento. Después, en alcance autorizado, producir/exportar, comprobar recepción y atención real y ejecutar piloto acotado. Solo con captación verificada concentrar desarrollo en CRM completo. Hoy: documentación lista para revisión; avatar hablado, clonación, exportaciones y conexión operativa siguen pendientes.
