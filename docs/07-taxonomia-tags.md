# 07 · Taxonomía de Tags

## Estrategia
Estandarizar segmentación para automatizaciones, reporting y seguimiento comercial.

## Catálogo principal
### Fuente
- `source_meta`
- `source_referral`
- `source_manual_prospecting`
- `source_organic`

### Interés
- `interest_protection`
- `interest_iul`
- `interest_retirement`
- `interest_children`
- `interest_business`

### Temperatura
- `hot_lead`
- `warm_lead`
- `cold_lead`

### Estado operativo
- `appointment_booked`
- `appointment_confirmed`
- `no_show`
- `follow_up`
- `client`
- `lost`

### Idioma
- `spanish`
- `english`

### Segmento
- `segment_family_30_55`
- `segment_business_owner`
- `segment_w2_worker`
- `segment_pre_retiree`

## Reglas operativas
1. No crear tags libres fuera de catálogo.
2. Un lead puede tener varios tags de interés, pero solo uno de temperatura activa.
3. Cualquier nuevo tag requiere registro en changelog interno.

## Pendientes de validación humana
- Validar si se agregan tags por estado geográfico.
