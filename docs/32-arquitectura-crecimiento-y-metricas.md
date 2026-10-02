# 32 · Arquitectura de crecimiento y métricas

Fecha local: 02/10/2026 · Diseño documental, sin instrumentación ni resultados operativos.

## Arquitectura objetivo

Contenido → Redes/SEO → Landing/Formulario → CRM → Lead scoring → Seguimiento → Cita → Presentación → Aplicación → Cierre → Referidos → Reactivación → Reportes.

Es una secuencia futura, no una integración existente. GHL conserva el rol comercial objetivo; Airtable, control/QA/reporting; Sheets, apoyo y exportaciones parciales. Ninguna cuenta se configura aquí. Referidos y reactivación requieren finalidad, consentimiento y exclusiones vigentes; un dato existente no autoriza contactar.

| Tramo | Registro mínimo propuesto | Responsable sugerido | Condición de avance |
|---|---|---|---|
| Contenido / redes / SEO | content_id, creative_id, versión, plataforma | Contenido | Revisión y permiso de publicar |
| Landing / formulario | visita, submission_id, origen, versión del aviso | Web/operaciones | Recepción autorizada y probada |
| CRM / scoring / seguimiento | lead_id, estado, criterio de score, responsable, próxima acción | CRM/comercial | Datos mínimos, trazabilidad, permisos y bajas |
| Cita / presentación / aplicación | IDs de eventos y fechas separadas | Comercial | Confirmaciones verificables; cita no equivale a venta |
| Aprobación / emisión / cierre | estados distintos y evidencia autorizada | Operaciones/producto | Emisión no presumida por aprobación |
| Referidos / reactivación / reportes | finalidad, cohorte, exclusiones y corte | Comercial/analítica | No contactar sin autorización pertinente |

Tomar campos existentes del [contrato CRM](22-sprint-01-dia-02-datos-crm.md) y conservar las definiciones del [diccionario KPI](13-kpi-dictionary.md). Este documento añade vistas, no cambia sus fórmulas. No usar atributos de salud para segmentación publicitaria o scoring sin evaluación específica; no recopilar datos sensibles en esta fase.

## Métricas sociales

| Métrica | Definición operativa propuesta | Límite |
|---|---|---|
| Alcance | Cuentas alcanzadas según la plataforma | No sumar redes como personas únicas |
| Impresiones | Exposiciones reportadas por canal | Una persona puede generar varias |
| Reproducciones | Conteo según umbral y definición del proveedor | No comparar sin igualar criterios |
| Retención | Tiempo medio o porcentaje que alcanza un punto definido | Registrar duración y denominador |
| Clics | Clics al destino; separar todos los clics | Misma fuente y periodo |
| Comentarios / compartidos / guardados | Acciones por pieza | No equivalen a intención de compra |
| Crecimiento de seguidores | Seguidores finales menos iniciales; porcentaje sobre iniciales | Base cero: sin tasa calculable |

## Captación y métricas comerciales

| Métrica | Conteo / fórmula | Fuente futura propuesta |
|---|---|---|
| Visitas | Sesiones bajo definición consistente | Analítica web autorizada |
| Formularios iniciados | Eventos de inicio distintos | Instrumentación pendiente |
| Formularios completados | submission_id aceptados, sin reintentos duplicados | Recepción/formulario |
| Conversión landing | Leads / visitas landing, según documento 13 | Landing + CRM |
| Conversión formulario | Enviados / visitas formulario, según documento 13 | Formulario + analítica |
| Finalización entre iniciados | Completados / iniciados; KPI adicional distinto | Misma cohorte |
| CPL | Inversión / leads, según documento 13 | Gasto aprobado + CRM |
| Fuente/campaña | Origen conocido o desconocido por evento | UTM y registro de entrada |
| Leads contactados | Personas con contacto efectivo; intentos por separado | CRM |
| Citas agendadas / completadas | IDs distintos y asistencia comprobada | Agenda autorizada + CRM |
| Aplicaciones iniciadas / enviadas | Estados distintos con fecha y evidencia | Registro comercial autorizado |
| Aprobaciones / pólizas emitidas | Eventos distintos; no contar como equivalentes | Evidencia de aseguradora autorizada |
| Referidos | Solicitudes con origen referido verificado | CRM; permisos independientes |

Primas no equivalen a ingresos del negocio. Close rate, ROI y costo por cliente conservan definición del documento 13; confirmar fuente financiera antes de calcular. No inventar gasto, clientes, aprobación o ingresos.

## Métricas de contenido y reglas de comparación

Evaluar avatar, guion, plataforma, horario, CTA y tema como dimensiones, mediante retención, clics o solicitudes con el mismo alcance/cohorte. «Mejor avatar» significa mejor resultado para un KPI definido dentro de esa prueba; no es superioridad general ni causalidad. Mantener oferta/destino comparables y cambiar una variable por experimento; el tamaño mínimo y criterio de decisión deberán aprobarse antes del piloto. No elegir ganadores con muestras insuficientes.

Ficha de métrica: nombre, definición, numerador, denominador, fuente, periodo, zona horaria, cohorte, orgánico/pagado, versión, exclusiones y responsable. Sin medición o denominador cero: «sin datos», no cero rendimiento. Deduplicar reintentos sin borrar eventos posteriores legítimos; preservar primer origen conocido y eventos sucesivos. No poner contactos personales en UTM.

## Tres estados de evidencia y mejora

| Estado | Qué permite afirmar |
|---|---|
| Documental | KPI definido; no medido ni instrumentado |
| Piloto | Resultado ficticio o acotado, identificado; no performance comercial |
| Operación real | Medición autorizada, periodo/fuente/corte y QA verificables |

Crear → Publicar → Medir → Aprender → Ajustar → Volver a publicar es un ciclo futuro sujeto a autorizaciones. Ahora solo se documenta. Revisión semanal propuesta: QA de datos, comparación de cohortes, hipótesis y backlog; revisión mensual del negocio sin extrapolar pilotos. Cadencia a confirmar con capacidad real.

Done documental: definiciones enlazadas, responsabilidades sugeridas y límites claros. Pendientes: baseline, instrumentación autorizada, objetivos y responsables nominales. [Roadmap](36-roadmap-siguiente-fase-cap001.md).
