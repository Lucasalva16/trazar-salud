# Relaciones del modelo

## Dimensión Calendario

Alta_Complejidad (Fecha) → Calendario (Fecha)
SII_Total (Fecha) → Calendario (Fecha)
OME_Imagenes (Fecha) → Calendario (Fecha)
Errores_Transmision (Periodo) → Calendario (Fecha)

---

## Dimensión Nomenclador

Alta_Complejidad (FK_Nomenclador) → Nomenclador (PK)
SII_Total (FK_Nomenclador) → Nomenclador (PK)
CUP_Total (FK_Nomenclador) → Nomenclador (PK)
OME_Imagenes (FK_Nomenclador) → Nomenclador (PK)

---

## Dimensión Gestión

SII_Total (FK_Gestion) → Gestion_Total (PK_Gestion)
CUP_Total (FK_Gestion) → Gestion_Total (PK_Gestion)
Errores_Transmision_Amb (FK_Gestion) → Gestion_Total (PK_Gestion)

---

## Internaciones

SII_Total (FK_Internacion) → Detalles_Internacion_Total (PK)

---

## Padrón de afiliados

CUP_Total (nro_afiliado) → Padron (nro_afiliado)

---

## Relaciones especiales

Errores_Transmision_Int_OP ↔ Errores_Transmision_Amb
Relación many-to-many para trazabilidad de errores.
