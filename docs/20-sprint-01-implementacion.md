# 20 · Sprint 01 · Implementación Operativa

## 1) Objetivo del Sprint 1
Ejecutar la preparación operativa mínima viable para iniciar la implementación del sistema Marketing Digital + CRM con base en tareas **P0**, asegurando consistencia de datos, trazabilidad de KPIs y activación controlada del flujo de lead nuevo, sin integrar herramientas externas ni conectar APIs.

## 2) Alcance del Sprint 1
Este sprint se enfoca en estandarización operativa interna de CRM y modelo de medición.

### Incluye
- Definición y normalización de campos CRM críticos.
- Construcción del diccionario operativo de KPIs.
- Diseño y activación interna del flujo de lead nuevo (mensaje, tarea y SLA).
- Validaciones humanas para aprobar reglas de negocio antes de escalar automatizaciones.

### No incluye
- Conexiones API.
- Configuración de herramientas externas.
- Creación de credenciales.
- Modificaciones de integraciones externas.

## 3) Tareas P0 incluidas
| Tarea P0 | Objetivo operativo | Resultado esperado |
|---|---|---|
| Estandarizar campos CRM | Definir campos obligatorios, tipos y validaciones | Datos consistentes y utilizables |
| Diccionario operativo KPI | Unificar definiciones, fórmulas y fuentes | Reportería confiable y comparable |
| Activar flujo lead nuevo | Implementar trigger, tarea inicial, mensaje y SLA | Mayor velocidad de contacto inicial |

## 4) Tareas fuera de alcance
| Tema | Estado Sprint 1 | Motivo |
|---|---|---|
| Integraciones Make | Fuera de alcance | Requiere contrato de datos y reglas ya estabilizadas |
| APIs | Fuera de alcance | Riesgo alto sin validación operativa previa |
| Sincronización GHL-Airtable | Fuera de alcance | Depende de estructura final de campos y KPIs |
| Automatizaciones externas | Fuera de alcance | Deben iniciar en Sprint 2 tras validación humana |

## 5) Plan día por día (Día 1 a Día 5)
| Día | Enfoque | Actividades clave | Entregable del día |
|---|---|---|---|
| Día 1 | Alineación operativa | Kickoff, validación de alcance, responsables nominales, revisión de backlog P0 | Acta de arranque + matriz de responsables |
| Día 2 | Datos CRM | Definir campos obligatorios, catálogo de valores, reglas de validación y criterios por etapa | Especificación de campos CRM v1 |
| Día 3 | KPI operativo | Definir diccionario KPI (fórmula, fuente, frecuencia, owner, criterio de corte) | KPI Dictionary Operativo v1 |
| Día 4 | Flujo lead nuevo | Diseñar/ajustar trigger, tarea inicial, mensaje base, SLA y alertas internas | Flujo Lead Nuevo en estado listo para validación |
| Día 5 | QA y cierre sprint | Validación cruzada, checklist final, riesgos abiertos y plan de continuidad | Cierre Sprint 1 + plan de Sprint 2 |

## 6) Responsable sugerido por tarea
| Tarea | Responsable sugerido | Soporte |
|---|---|---|
| Estandarizar campos CRM | CRM Ops | Comercial + Ventas Ops |
| Diccionario operativo KPI | BI Ops | RevOps + CRM Ops |
| Activar flujo lead nuevo | Automatización | Ventas Ops + Marketing Ops |
| QA de Sprint 1 | RevOps | Leads funcionales de cada área |

> Nota: la asignación nominal final se valida por liderazgo operativo.

## 7) Dependencias
| Tarea | Depende de | Tipo de dependencia |
|---|---|---|
| Estandarizar campos CRM | Aprobación comercial | Crítica |
| Diccionario operativo KPI | Fuentes de datos definidas y campos CRM estandarizados | Crítica |
| Activar flujo lead nuevo | Campos CRM estandarizados + pipeline validado + SLA acordado | Crítica |

### Secuencia recomendada
1. Estandarizar campos CRM.
2. Cerrar diccionario KPI operativo.
3. Activar flujo lead nuevo.

## 8) Checklist de configuración GoHighLevel
- [ ] Crear/validar pipeline base con criterios de entrada/salida por etapa.
- [ ] Crear campos personalizados CRM con convención de nombres.
- [ ] Definir campos obligatorios por etapa comercial.
- [ ] Configurar validaciones de formato (email, teléfono, listas controladas).
- [ ] Definir tags operativos mínimos (origen, estado, prioridad).
- [ ] Configurar borrador de flujo “Lead Nuevo”:
  - [ ] Trigger de lead nuevo.
  - [ ] Creación de tarea inicial.
  - [ ] Mensaje base de primer contacto.
  - [ ] Temporizador SLA y alerta interna.
- [ ] Definir asignación de owner (manual o regla interna inicial).
- [ ] Documentar causas de no contacto / no show.

## 9) Checklist de configuración Airtable
- [ ] Crear/validar base operativa para seguimiento interno.
- [ ] Definir tablas mínimas: Leads, Actividades, KPI Definitions.
- [ ] Homologar nombres de campos con CRM (equivalencia de datos).
- [ ] Crear catálogos controlados (source, stage, status, owner, outcome).
- [ ] Estandarizar formato de fecha/hora y zona horaria.
- [ ] Crear vistas de control operativo:
  - [ ] Leads incompletos.
  - [ ] Leads nuevos del día.
  - [ ] SLA por vencer / SLA vencido.
- [ ] Prototipar fórmulas KPI base sin automatizaciones externas.
- [ ] Definir control de calidad de dato y revisión de duplicados.

## 10) Lista de validaciones humanas
- [ ] Aprobación comercial de campos obligatorios CRM.
- [ ] Aprobación de criterios de calificación y avance por etapa.
- [ ] Aprobación de definiciones KPI por liderazgo comercial/operativo.
- [ ] Aprobación del SLA objetivo de primer contacto.
- [ ] Aprobación de mensajes base por lineamientos de marca/compliance.
- [ ] Confirmación de responsables nominales por tarea y etapa.
- [ ] Confirmación de capacidad semanal real para ejecución.

## 11) Riesgos y mitigaciones
| Riesgo | Impacto | Mitigación |
|---|---|---|
| Campos mal definidos | Datos incompletos/no comparables | Validación de catálogo y QA de campos antes de activación |
| KPI ambiguos | Decisiones erróneas | Diccionario KPI con fórmula explícita + owner |
| Flujo lead nuevo sin reglas claras | Tareas duplicadas o seguimiento inconsistente | Prueba operativa interna + revisión diaria en Sprint 1 |
| Owners no definidos | Leads sin atención | Asignación nominal obligatoria antes de go-live interno |
| SLA no realista | Saturación del equipo y baja adherencia | Ajuste de SLA según capacidad de atención validada |
| Inconsistencia de timezone | Métricas y SLA distorsionados | Estándar único de zona horaria documentado |

## 12) Criterios de Done por tarea
| Tarea | Done cuando… |
|---|---|
| Estandarizar campos CRM | Existe documento v1 aprobado con campos, tipos, obligatoriedad y validaciones por etapa |
| Diccionario operativo KPI | Existe documento v1 aprobado con definición, fórmula, fuente, frecuencia y owner por KPI |
| Activar flujo lead nuevo | Flujo está configurado internamente con trigger, tarea, mensaje y SLA, y pasó validación operativa |

## 13) Entregables finales del Sprint 1
- Documento de campos CRM estandarizados (v1 aprobado).
- Diccionario operativo KPI (v1 aprobado).
- Flujo Lead Nuevo configurado a nivel interno (sin integraciones externas).
- Checklists de GHL y Airtable completados o con pendientes explícitos.
- Registro de riesgos abiertos + mitigaciones activas.
- Acta de cierre de Sprint 1 con decisiones y pendientes para Sprint 2.

## 14) Qué queda preparado para Sprint 2
- Base de datos CRM normalizada para escalamiento.
- Definiciones KPI listas para automatizar reportería.
- Flujo lead nuevo estabilizado para evolucionar secuencias.
- Precondiciones listas para evaluar integración Make y sincronización GHL-Airtable.
- Lista de validaciones humanas cerradas como gate previo a automatizaciones externas.
