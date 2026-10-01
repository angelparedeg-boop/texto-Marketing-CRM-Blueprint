> **Archivo histórico incorporado el 30/09/2026.** El cuerpo conserva las afirmaciones y pruebas reportadas en aquella sesión; no son comprobaciones ejecutadas en esta entrega ni acreditan el estado actual de Google. Las referencias a archivos de código son rutas de procedencia, no código incorporado. Se adaptaron únicamente enlaces locales y se añadió esta advertencia.

# Informe final · Forms → Sheets → Seguimiento · CAP-001

30/09/2026. **Recorrido técnico controlado verificado con una respuesta ficticia enviada desde la interfaz de Google Forms.** No equivale a captación comercial operativa ni cierra los demás entregables de CAP-001.

## Resultado de los nueve puntos

| Punto | Resultado comprobado |
| --- | --- |
| 1. Puede enviar respuestas | Inicialmente no: estaba sin publicar. Tras autorización «continua», se habilitó temporalmente con acceso restringido al propietario y se envió una respuesta ficticia. Al finalizar se cerró la recepción. |
| 2. Destino correcto | verificarDestinoCAP001 confirmó nuevamente el libro configurado, tipo de destino y encabezados; no se cambió el vínculo. |
| 3. Trigger | Inicialmente 0 visibles en la cuenta actual. Se instaló uno y se verificó en la lista. |
| 4. Función y evento | alEnviarCAP001, origen Google Forms, evento On form submit, versión Head. Instalado mediante instalarTriggerCAP001 del proyecto existente. |
| 5. Lead ficticio | PRUEBA RECORRIDO CAP001 NO CONTACTAR; NJ; email; cap001-recorrido@example.invalid; tema Ensayo Forms R1 sin contacto. |
| 6. Respuesta original | Forms muestra 1 respuesta. Se leyó A1:H2 de Form Responses 1: la fila 2 contiene el ensayo en la tabla Form_Responses, con teléfono vacío. |
| 7. Entradas y Seguimiento | Una entrada y un contacto asociados a esa respuesta; es_prueba=si; Miriam (prueba); próxima acción Revisar solicitud de prueba. |
| 8. Segunda ejecución | Se reprocesó la misma respuesta mediante capProcess: 1 entrada antes/después y 1 contacto antes/después, sin cambios en sus filas. |
| 9. Informe | Este documento, con evidencias y estado final. |

## Evidencia técnica

El registro de Apps Script muestra **alEnviarCAP001 — Trigger — Completed**, inicio 30/09/2026 15:02:38 según la interfaz, duración 2.989 segundos. La fila nativa muestra 19:02:38 en su formato de hoja; no se modificaron zonas horarias para hacer coincidir representaciones.

ID de evento ficticio: `GF-2_ABaOnuf5VczPvkTVzq2Too878twAnJRYgK6SyhSyRHX5j8GElLr4_k1rf6Ac_bKDHeiljEg`.

Próxima acción almacenada: `2026-10-01T19:02:37.794Z`, convención técnica de +24 horas, no SLA comercial aprobado.

El helper verificarReintentoFormsCAP001 exige que ya existan la entrada y el contacto antes de reprocesar. Así, su ejecución no puede ocultar un trigger fallido creando los registros faltantes. También exige una sola respuesta ficticia y una sola fila nativa; compara las filas operativas completas antes/después. La ejecución real terminó correctamente y devolvió seguimiento_preservado=true.

Se envió el formulario **una sola vez**. La segunda ejecución repite el procesamiento de ese mismo ID, no crea otra respuesta. Un envío nuevo obtiene otro evento y no debe confundirse con un reintento. Tampoco se presentó un envío por script como prueba del trigger: Google indica que FormResponse.submit() no lo dispara. [Documentación oficial](https://developers.google.com/apps-script/guides/triggers/installable).

## Estado final de acceso

El formulario quedó en estado **Published de Google Forms, acceso Restringido / Specific people y Not accepting responses**. Su único usuario con acceso comprobado era el propietario. Se retiró el acceso de participantes «Anyone with the link» antes del ensayo. No se restauró ese acceso amplio al terminar.

La recepción está cerrada; no se declara que el formulario volvió a estado «sin publicar». La publicación técnica restringida permitió el ensayo autorizado y no fue una publicación de campaña. El trigger permanece instalado para futuros ensayos autorizados. No se modificaron preguntas, diseño, oferta ni campaña.

La rama email mostró directamente Submit tras completar el correo, sin exigir teléfono. Queda verificada para este caso. No se ensayó la rama teléfono ni acceso con otra cuenta, ni se hicieron pruebas de carga o fallos reales del proveedor.

## Archivos y recursos

- Modificado remoto: Verificacion.gs; añadido verificarReintentoFormsCAP001. Code.gs conservado.
- Modificado local: cap001-piloto/integrations/google/Verificacion.js.
- Modificados: README.md, CONTINUAR.md e integrations/google/README.md del piloto para reflejar el estado vigente.
- Creado y actualizado: este informe.
- Evidencias nuevas: cap001-trigger-ausente.png, cap001-formulario-sin-recepcion.png, cap001-envio-forms.png, cap001-trigger-ejecutado.png, cap001-recepcion-cerrada-final.png y cap001-forms-reintento.png.
- Recurso configurado: un trigger instalable alEnviarCAP001 para el formulario existente.
- Datos añadidos: una respuesta nativa ficticia y su entrada/contacto. Se conservan los pilotos anteriores, sin borrarlos.

## Pruebas y errores

- npm test: **22 aprobadas, 0 fallidas**; regresión del piloto y mapeo existente. No son 22 pruebas nuevas del helper.
- npm run check: aprobado.
- node --check integrations/google/Verificacion.js: aprobado.
- git diff --check: aprobado.
- Prueba real de Forms, trigger, escritura nativa, filas operativas y reproceso: aprobada.
- No hubo errores de ejecución de las funciones en Google durante el ensayo. Hubo una selección de casilla que no cambió y navegación del editor interferida por el menú superpuesto; se corrigieron en la interfaz antes de continuar. No generaron envíos duplicados ni cambios de diseño.
- Node emitió el aviso conocido de SQLite experimental. No impidió las pruebas.

## Enlaces

- [Formulario editable](https://docs.google.com/forms/d/1iSoQyIpBrjpxiERn1Sjcx-VLz4mSyvP8Z1MSbrL5d1w/edit).
- [Sheet de prueba](https://docs.google.com/spreadsheets/d/1s2TK8HBivcdSXspIzyrzOYw-mB02uqqbYAPPNzRm8Ww/edit).
- [Apps Script](https://script.google.com/home/projects/10m5_f2jeDqo_EDl2DLZkZDC_TLf-CpSzPPACPzyG8K20It9e8DB-WFk9/edit).
- [Enlace de participante, restringido y cerrado](https://docs.google.com/forms/d/e/1FAIpQLSeIo3jwKvtgW6WvNVy9F28FiidlDjJd8rQ99oah27zFKkeb0g/viewform).
- [Trigger automático completado](../evidencias/CAP-001/cap001-trigger-ejecutado.png).
- [Reproceso sin duplicados](../evidencias/CAP-001/cap001-forms-reintento.png).
- [Recepción cerrada y acceso específico](../evidencias/CAP-001/cap001-recepcion-cerrada-final.png).

## Próximos pasos recomendados

Conservar este estado cerrado y las evidencias. En una futura entrega, comprobar la rama teléfono y definir permisos de participantes, condiciones de atención y conexión de la landing antes de habilitar captación. La landing local sigue independiente de Forms. No activar publicidad ni comunicaciones como consecuencia automática de esta prueba.

No se usaron datos reales en el lead, no se enviaron comunicaciones, no se conectaron APIs externas ni se generó video. No se crearon nuevas tareas ni se cambió de proyecto.
