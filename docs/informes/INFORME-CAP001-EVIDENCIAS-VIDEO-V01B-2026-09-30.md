# Informe · CAP-001 · Evidencias históricas y video V01B

Fecha: 30/09/2026. Rama: `codex/cap001-evidencias-video-v01b`. Base remota auténtica: `f55c76cd6c99002321433b640473d6406b0bf8db`.

## Nota de actualización posterior · 01/10/2026

El cuerpo original que sigue describe la primera incorporación del 30/09, no el estado vigente del PR. Sus referencias a avatar no encontrado, asset pendiente, materialización de AV-HOMBRE-01 y status listo_para_produccion son antecedentes históricos superados. El PNG aprobado ya está incorporado como binario en `assets/avatars/AV-HOMBRE-01/asesor_financiero_en_oficina_calida.png`, commit `98379d2b4fa90b425a9464b370055d7534bae493`; su SHA-256 es `fce7c8e9470c83c388f9debdbc644e71db3351e17357299bd7ac25101232c3b4`.

El PR contiene actualmente **21 archivos respecto de main**. Los documentos [27](../27-continuidad-captacion.md) y [28](../28-video-cap001-v01b-avatar-hombre.md) fueron corregidos; el documento 28 vigente quedó en el commit `94379dc4ced643e7b9e76607b5af21c6497621ea`. Su estado es `documentacion_preparada_pendiente_revision`; distingue beneficio por fallecimiento y beneficios en vida sujetos a riders/coberturas, elegibilidad y aprobación. La expresión «beneficio de vida» no se conserva como frase aprobada. Mantiene IUL visible y aiuel en voz. El guion completo tiene **281 palabras, aproximadamente 116–135 segundos antes de pausas**, pendiente de validación en lectura autorizada; la versión de **60–75 segundos** es una pieza futura separada, sin recorte automático ni eliminación de condiciones esenciales.

Esta nota no revalida Google ni autoriza ejecución. No se generó video/audio, no se modificó Google ni se incorporó código Google o tests, no se publicaron campañas ni se enviaron comunicaciones. Capturas y hashes históricos permanecen intactos. El PR #7 continúa abierto, en borrador y sin fusionar; no debe fusionarse automáticamente ni marcarse como listo por esta actualización.

## Resumen ejecutivo

Primera incorporación documental aprobada: dos informes históricos, 13 capturas originales, índice de hashes, continuidad corregida y paquete CAP-001-V01B. No se reincorporan los 14 documentos ya idénticos a main ni se mezclan historias de reconstrucciones locales. No se añade código ejecutable ni se accede a Google. No se genera video, campaña o comunicación.

## Archivos creados

- `docs/informes/INFORME-CAP001-FORMULARIO-2026-09-30.md`.
- `docs/informes/INFORME-RECORRIDO-FORMS-CAP001.md`.
- `docs/27-continuidad-captacion.md`.
- `docs/28-video-cap001-v01b-avatar-hombre.md`.
- `docs/evidencias/CAP-001/README.md` y los 13 PNG enumerados allí.
- Este informe: `docs/informes/INFORME-CAP001-EVIDENCIAS-VIDEO-V01B-2026-09-30.md`.

## Archivos modificados y eliminados

Ningún archivo preexistente de main modificado o eliminado. Las adaptaciones se hacen en copias nuevas de los informes: advertencia histórica y enlaces locales ajustados. README principal y documentos 01–26 permanecen intactos. Fuentes originales, capturas y repositorios reconstruidos preservados.

## Comandos ejecutados y método

- `git status --short`, `git rev-parse HEAD origin/main` y `git ls-remote origin refs/heads/main refs/heads/codex/cap001-evidencias-video-v01b`: comprobación de base y rama nueva.
- `git switch -c codex/cap001-evidencias-video-v01b f55c76cd6c99002321433b640473d6406b0bf8db`: rama creada directamente desde la base auténtica.
- Script de preparación fuera del repositorio: copia byte a byte de PNG, SHA-256, adaptación limitada de informes y extracción literal del guion del adjunto.
- Revisión visual de capturas para confirmar contexto ficticio/histórico; no consulta de recursos Google.
- Validación documental fuera del repositorio: enlaces locales, títulos, cercas, formato de tablas, guiones/textos exactos, metadata y límite de extensiones/rutas.
- `git diff --check`, revisión del índice y del diff contra la base antes de commit.
- Registro Git y publicación de rama/PR: estado y referencia exactos en el apartado de trazabilidad y en la entrega final.

## Pruebas y resultados

Validación documental aprobada: 19 archivos nuevos (6 Markdown y 13 capturas), 28 enlaces locales resueltos, 13 hashes idénticos a originales, 6 secciones cotejadas literalmente con el adjunto, 10 escenas y metadata requerida. Cero archivos preexistentes modificados/eliminados y cero archivos ejecutables incorporados. git diff --check aprobado. No se cuentan las 22 pruebas históricas como ejecutadas hoy. No se ejecutan tests Google, helpers, triggers ni pruebas de integración. Las capturas reportan una respuesta ficticia, trigger Completed y reproceso 1/1 preservado; no acreditan el estado actual.

## Errores o advertencias

Validaciones iniciales detectaron que la extensión .png no corresponde al formato JPEG; se ajustó la comprobación al formato real sin cambiar evidencia. Los controles de título inicial y texto de advertencia se ajustaron a informes con aviso previo y capitalización; no son fallos del contenido. Git advierte que no puede leer el archivo global de exclusiones del perfil; no se cambian permisos ni configuración global. El entorno cambia de identidad sandbox entre turnos; se usa excepción safe.directory limitada al comando cuando procede, sin alterar el repositorio. No se incorpora un asset de avatar no encontrado. Las 13 capturas tienen extensión histórica .png pero firma JPEG; se conservan sin conversión y con hashes idénticos, y la discrepancia queda registrada en su índice.

## Decisiones asumidas

1. Informes bajo docs/informes; evidencias bajo docs/evidencias/CAP-001, preservando nombres originales.
2. Estado final histórico del ensayo: Published, acceso específico, recepción cerrada; no se presenta como campaña publicada ni estado actual comprobado.
3. Se preservan pruebas directas de Sheets como antecedentes distintos del envío nativo y el reproceso del mismo ID.
4. V01B usa IUL visible y aiuel unido en voz. La pauta anterior del documento 26 no se aplica a esta pieza, sin modificar ese documento.
5. Metadata status listo_para_produccion conservada, con advertencia de asset pendiente y falta de autorización audiovisual.
6. La duración sugerida no autoriza recortar el guion. El documento 28 incluye estimación orientativa y validación de duración pendiente.

## Riesgos y validaciones humanas requeridas

- Estado actual de Google desconocido: comprobar acceso, recepción, destino, versión de código y triggers antes de operar, sin instalar otro automáticamente.
- Código Google excluido: revisión e incorporación separadas con dependencias y pruebas propias.
- Pendiente rama teléfono; piloto local no demuestra conexión de landing con Forms.
- Confirmar responsable nominal, capacidad, horario, SLA, territorio y consentimiento antes de atención comercial.
- Materializar AV-HOMBRE-01; confirmar voz, herramienta, derechos/costo, duración y condiciones de producto/compliance. No sustituir por assets antiguos.
- Informes históricos pueden narrar estados distintos por su secuencia; las advertencias y continuidad corrigen su interpretación sin inventar una revalidación.

## Próximo paso recomendado

Revisar el PR documental. Tras aprobación, realizar revisión separada de código Google y autorizar, si corresponde, verificación actual. Producción audiovisual requiere autorización posterior y asset aprobado. No fusionar automáticamente el PR.

## Trazabilidad Git

Base: `f55c76cd6c99002321433b640473d6406b0bf8db`. Rama: `codex/cap001-evidencias-video-v01b`. Commit local de contenido comprobado: c03a6207d0a06f45c7eac704627c03dc880dab0f, creado desde la base auténtica. Cierre documental posterior para registrar esta referencia sin autorreferencia del hash. Estado inicial comprobado: árbol limpio. El hash del commit que contiene la versión final de este informe se obtiene con `git log -1 --format=%H -- docs/informes/INFORME-CAP001-EVIDENCIAS-VIDEO-V01B-2026-09-30.md`.

git status --short quedó sin entradas tras el commit de contenido. El push HTTPS por terminal falló por falta de credenciales (terminal prompts disabled); GitHub CLI no está autenticado. Se usa el conector GitHub existente para publicar un commit equivalente sobre la misma base y árbol de archivos; la rama local se sincronizará solo tras comprobar identidad de árbol y parent remoto. No se importan historias reconstruidas ni se crean credenciales. El hash final publicado y el enlace del PR se entregan en el chat y pueden consultarse en el historial de la rama.
