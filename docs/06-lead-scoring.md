# 06 · Lead Scoring (0–100)

## Estrategia
Priorizar leads por intención, capacidad y urgencia para mejorar tasa de citas y tasa de cierre.

## Modelo base
| Regla | Puntos |
|---|---:|
| Tiene hijos o dependientes | +15 |
| Tiene ingreso estable | +20 |
| Quiere proteger a su familia | +15 |
| Quiere ahorrar para retiro | +15 |
| Tiene seguro actual | +10 |
| Quiere cita en 7 días | +25 |
| Solo información general | +5 |
| No responde tras 3 intentos | -15 |
| No tiene ingreso estable | -20 |

## Bandas
- **80–100**: Muy caliente → llamada inmediata.
- **60–79**: Calificado → secuencia + cita.
- **40–59**: Tibio → nutrición educativa.
- **20–39**: Frío → contenido + remarketing.
- **0–19**: No prioritario.

## Operación
- Recalcular score tras quiz, respuesta, agenda, no-show y reactivación.
- Aplicar tag automático por temperatura.

## Configuración técnica
- Guardar `score_version`.
- Limitar resultado a 0–100; cada regla cuenta una vez y condiciones opuestas no se aplican juntas. Desconocidos no son negativos; sin información pertinente usar null/sin_datos. Es prioridad operativa provisional, no probabilidad validada ni elegibilidad; véase el contrato del Día 2.
- Guardar `score_updated_at`.
- No sobrescribir score manualmente sin nota de auditoría.

## Pendientes de validación humana
- Ajustar ponderaciones con 30 días de datos reales.
