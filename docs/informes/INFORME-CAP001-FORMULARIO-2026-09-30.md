> **Archivo histórico incorporado el 30/09/2026.** El cuerpo conserva las afirmaciones y pruebas reportadas en aquella sesión; no son comprobaciones ejecutadas en esta entrega ni acreditan el estado actual de Google. Las referencias a archivos de código son rutas de procedencia, no código incorporado. Se adaptaron únicamente enlaces locales y se añadió esta advertencia.

> Este informe precede al [ensayo nativo completo](INFORME-RECORRIDO-FORMS-CAP001.md). Sus estados «sin publicar» y «trigger pendiente» quedan como antecedentes históricos.

# Informe final CAP-001 · Formulario y destino de respuestas · 30/09/2026

Entrega cerrada para el alcance solicitado: revisión indicada, destino comprobado, verificación/reparación automática preparada y función de lead piloto implementada y ejecutada. Esto no cierra toda la Fase 1 ni acredita captación operativa. Se continúa en el mismo proyecto; no se abrieron tareas nuevas.

## Resultado comprobado

El [formulario editable](https://docs.google.com/forms/d/1iSoQyIpBrjpxiERn1Sjcx-VLz4mSyvP8Z1MSbrL5d1w/edit) existe y permanece sin publicar. Ya estaba conectado al [Google Sheet configurado](https://docs.google.com/spreadsheets/d/1s2TK8HBivcdSXspIzyrzOYw-mB02uqqbYAPPNzRm8Ww/edit). La ejecución real de verificarDestinoCAP001 devolvió destino_verificado=true, vinculo_creado=false y encabezados_operativos=verificados.

Se añadió **Verificacion.gs** al [proyecto Apps Script existente](https://script.google.com/home/projects/10m5_f2jeDqo_EDl2DLZkZDC_TLf-CpSzPPACPzyG8K20It9e8DB-WFk9/edit). Su contenido guardado se comparó con la fuente local. Code.gs se conservó. No se creó otro proyecto ni formulario.

## Qué revisar en el formulario

1. Título y oferta: Diagnóstico Financiero Familiar Gratuito; mantener el aviso de prueba mientras se ensaya. No prometer cita confirmada, resultados financieros ni duración no aprobada.
2. Nombre, estado, canal preferido y contacto correspondiente obligatorios; tema de interés opcional. Revisar los 15 estados configurados contra el territorio realmente atendible antes del lanzamiento.
3. En vista previa, probar ambos recorridos: correo debe pedir solo email y terminar; llamada debe pedir solo teléfono y terminar. El editor mostró «Continuar a la siguiente sección» al final de la sección de correo: queda **pendiente verificar esa navegación** antes de habilitar recepción, para evitar exigir ambos contactos.
4. Consentimiento: solicitud de contacto para coordinar el diagnóstico por el canal elegido, sin convertirlo en permiso para campañas posteriores. La casilla del fixture es ficticia, no autorización de una persona.
5. Confirmación: indicar solicitud recibida y siguiente paso; no afirmar que una cita ya está reservada. Revisar legibilidad móvil, mensajes de validación y acceso de participantes.

## Cómo verificar el vínculo

En el formulario: **Respuestas → icono verde / Ver en Hojas de cálculo**. Debe abrir el libro cuyo ID es `1s2TK8HBivcdSXspIzyrzOYw-mB02uqqbYAPPNzRm8Ww`.

En Apps Script: seleccionar **verificarDestinoCAP001 → Ejecutar** y leer `destino_verificado:true`. La función comprueba ID y tipo del destino y encabezados operativos. Si falta vínculo, lo crea con ese libro existente; si encuentra otro, se detiene sin sustituirlo. Usa los métodos nativos [getDestinationId, getDestinationType y setDestination](https://developers.google.com/apps-script/reference/forms/form).

## Prueba realizada y límites

`probarCAP001` usa el nombre «PRUEBA CONTROLADA CAP-001 NO CONTACTAR», correo reservado `cap001-piloto@example.invalid`, estado NJ e ID fijo `GF-PILOT-CAP001-CONTROL-R1`. Marca es_prueba=si, asigna Miriam (prueba) y próxima acción conforme al mapeo existente. Fecha de fixture fija 30/09/2026 12:00 UTC; no es una fecha comercial real.

| Ejecución real | Resultado |
| --- | --- |
| 14:26:00 UTC | 1 entrada y 1 contacto; ambos agregados |
| 14:26:22 UTC | 1 entrada y 1 contacto; ambos indicadores de agregado false |

Se verificó la escritura en **Entradas y Seguimiento** y la repetición sin duplicados. No se enviaron mensajes. La prueba escribe directamente en Sheets utilizando el mapeo de captación: **no crea una respuesta nativa en Forms, no aumenta su contador y no prueba el trigger**. El contador observado de Forms fue 0; esto es compatible con la prueba realizada.

Pruebas locales: 22 aprobadas, incluidas conexión ausente, destino ajeno, repetición preservando atención/bajas y recuperación simulada tras fallo parcial. Sintaxis de Verificacion.js y git diff --check aprobados. Los fallos y concurrencia reales de Google no se simularon en producción.

Evidencia: [primera inserción](../evidencias/CAP-001/cap001-prueba-insercion.png) y [repetición sin duplicados](../evidencias/CAP-001/cap001-prueba-repetida.png).

## Archivos creados

- Remoto: nuevo **Verificacion.gs**, en el proyecto existente.
- Fuente local: integrations/google/Verificacion.js (ruta histórica: `cap001-piloto/integrations/google/Verificacion.js`; fuente no incorporada).
- Pruebas: test/google-verificacion.test.mjs (ruta histórica: `cap001-piloto/test/google-verificacion.test.mjs`; fuente no incorporada).
- Este informe y las dos capturas de evidencia.

## Archivos modificados

- integrations/google/README.md (ruta histórica: `cap001-piloto/integrations/google/README.md`; fuente no incorporada): estado verificado, funciones e instrucciones de uso.
- README.md (ruta histórica: `cap001-piloto/README.md`; fuente no incorporada): resumen vigente de la entrega.
- CONTINUAR.md (ruta histórica: `cap001-piloto/CONTINUAR.md`; fuente no incorporada): evidencia, alcance y punto de continuación, conservando el historial.

El código y la documentación del piloto quedaron en la rama local `codex/captacion-citas`, commit `6f39a97`. El árbol del piloto se comprobó limpio al cierre. El informe y capturas están en outputs, fuera de ese repositorio local. No se subió este cambio a GitHub ni se fusionó una rama.

## Pruebas ejecutadas y errores

| Comprobación | Resultado y alcance |
| --- | --- |
| `npm test` | 22 aprobadas, 0 fallidas; incluye 4 nuevas pruebas de verificación/piloto |
| `npm run check` | Sintaxis del servidor y clientes aprobada |
| `node --check integrations/google/Verificacion.js` | Sintaxis aprobada |
| `git diff --check` | Sin errores de formato |
| Comparación de código guardado en Google con fuente local | Coincidencia confirmada |
| `verificarDestinoCAP001` en Google | Destino y encabezados correctos; vínculo existente preservado |
| `probarCAP001` en Google, dos ejecuciones | Primera inserta 1/1; segunda conserva 1/1 sin duplicar |

No hubo errores de ejecución en las funciones de Google durante esta entrega. Los errores provocados por las pruebas locales —destino distinto, FORM_ID distinto y fallo parcial de escritura— fueron rechazados o recuperados según lo esperado; no son fallos pendientes del resultado.

Avisos del entorno: Node informó que SQLite es experimental; Git no pudo leer el archivo global de exclusiones `C:\Users\Angel\.config\git\ignore` por permisos. Los comandos de prueba, commit y estado finalizaron correctamente. No se cambiaron permisos del sistema para ocultar esos avisos.

Hallazgo pendiente: navegación al finalizar la sección de correo, descrita arriba. No se declara defectuosa ni aprobada sin probar el recorrido. Tampoco se verificaron instalación del trigger, envío nativo, recepción pública ni operación comercial.

## Enlaces y estado actual

Los enlaces al formulario, Sheet y Apps Script incluidos arriba son recursos existentes verificados; **no se generó una URL pública nueva ni un despliegue**. Los únicos enlaces nuevos de entrega son los archivos locales de este informe, código, pruebas y capturas.

| Componente | Estado al cierre |
| --- | --- |
| Formulario | Creado, editable, sin publicar |
| Destino de respuestas | Conectado al libro configurado y comprobado |
| Entradas y Seguimiento | Escritura ficticia y repetición comprobadas en Google |
| Trigger y recorrido Forms completo | Pendiente de verificación |
| Landing | Local, independiente de Google Forms |
| Campañas / comunicaciones / APIs externas / video | No ejecutados en esta entrega |

## Próximos pasos

Revisar la navegación y los textos anteriores. Después verificar/instalar el trigger del mismo formulario y definir acceso de prueba para comprobar un envío ficticio completo: respuesta nativa → Entradas → Seguimiento. La función instalarTriggerCAP001 ya existe, pero su instalación/ejecución no se verificó en esta entrega. La landing continúa local y sin conexión a este formulario.

No se publicaron formularios ni campañas, no se enviaron datos reales, no se conectaron APIs externas, no se generó video ni se compraron servicios. No se requiere una decisión adicional para conservar esta preparación; habilitar recepción para el ensayo completo será un paso posterior con alcance de acceso definido.
