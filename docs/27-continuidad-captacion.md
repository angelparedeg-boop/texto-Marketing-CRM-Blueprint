# 27 · CAP-001 · Continuidad documental corregida

Fecha de incorporación: 30/09/2026. Base auténtica: `f55c76cd6c99002321433b640473d6406b0bf8db`. Esta página sustituye para esta rama las propuestas locales de tracker; no importa sus historias Git ni afirma recuperar sus commits.

## Estado que puede afirmarse

Las evidencias y los dos informes son **históricos**. No acreditan el estado actual de Google, sus permisos, el destino, las filas ni los triggers. Esta entrega no abrió ni modificó Google.

Según el informe posterior, hubo una prueba ficticia completa: formulario → envío desde la interfaz → Form Responses 1 → Entradas → Seguimiento. Se registró una respuesta nativa, una entrada y un contacto asociados. La ejecución automática de `alEnviarCAP001` figura como Completed. Reprocesar la misma respuesta conservó 1 entrada y 1 contacto sin alterar sus filas; no fue un segundo envío ni otra ejecución automática del trigger.

El formulario quedó históricamente **Published, acceso Specific people y recepción cerrada / Not accepting responses**. El informe registra un trigger instalado para ese ensayo. No se afirma que hoy conserve esos estados. Publicación técnica restringida no equivale a publicación de campaña.

No hay campañas publicadas como resultado del trabajo documentado ni de esta entrega. No se realizó una auditoría actual de cuentas publicitarias. La landing del piloto local seguía independiente de Forms; las capturas de confirmación, cita y móvil no acreditan su conexión ni disponibilidad pública. No se usaron leads reales ni se enviaron comunicaciones en los ensayos reportados.

## Secuencia histórica y límites

| Etapa | Evidencia disponible | Interpretación |
|---|---|---|
| Piloto local | Confirmación, cita manual y vista móvil | Prueba ficticia local; no agenda ni CRM externo |
| Autorización Google | Capturas de autorización pendiente | Antecedente superado según informe posterior; no bloqueo actual comprobado |
| Verificación de destino | Primer informe y capturas de inserción/repetición | Escritura directa en Sheets; no prueba nativa de Forms ni trigger |
| Antes del ensayo nativo | Trigger ausente y formulario sin recepción | Estado inicial del ensayo; no estado final |
| Ensayo nativo completo | Envío, trigger Completed y reproceso | Una respuesta ficticia procesada; mismo ID conservado en reintento |
| Cierre del ensayo | Recepción cerrada y acceso específico | Estado histórico final; debe comprobarse antes de cualquier operación |

## Verificación necesaria antes de operar

- [ ] Comprobar existencia del formulario, acceso restringido y recepción cerrada sin habilitarla automáticamente.
- [ ] Confirmar el Sheet de destino, encabezados y filas ficticias preservadas.
- [ ] Revisar por separado el código Google y su versión remota antes de aprobar su incorporación o ejecución.
- [ ] Verificar handler, origen, evento y número de triggers existentes; no instalar ni duplicar por asumir que faltan.
- [ ] Verificar rama teléfono en un ensayo futuro autorizado; la evidencia histórica cubre la rama email.
- [ ] Distinguir reintento del mismo ID de una nueva solicitud y validar tratamiento de coincidencias ambiguas.
- [ ] Confirmar responsable nominal, horarios, capacidad, SLA, territorio y condiciones de consentimiento.
- [ ] Obtener aprobación explícita antes de abrir captación comercial, publicar campañas o enviar comunicaciones.

## Documentos y siguiente paso

- [Informe histórico de formulario y destino](informes/INFORME-CAP001-FORMULARIO-2026-09-30.md).
- [Informe histórico del recorrido nativo](informes/INFORME-RECORRIDO-FORMS-CAP001.md).
- [Índice y hashes de evidencias](evidencias/CAP-001/README.md).
- [Paquete documental CAP-001-V01B](28-video-cap001-v01b-avatar-hombre.md).
- [Informe de incorporación](informes/INFORME-CAP001-EVIDENCIAS-VIDEO-V01B-2026-09-30.md).

Próximo paso: revisar este paquete documental. El código Google queda para revisión separada; no se incorporan Mapping.js, Setup.js, Verificacion.js, tests ni instrucciones de instalación como una activación autorizada. El asset aprobado AV-HOMBRE-01 ya fue incorporado como binario en [la ruta aprobada](../assets/avatars/AV-HOMBRE-01/asesor_financiero_en_oficina_calida.png), con formato PNG, dimensiones 1122 × 1402 y hash verificados; véase el [informe del asset del 01/10/2026](informes/INFORME-CAP001-ASSET-AV-HOMBRE-01-2026-10-01.md). El video permanece sin generar. El siguiente paso audiovisual es revisar contenido, producto/compliance, herramienta, voz y duración antes de autorizar producción; después revisar el primer render antes de publicar. La incorporación del PNG no autoriza generar video ni lanzar campañas.
