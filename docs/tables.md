# Tablas y Claves

Este documento describe las claves primarias (PK) y foráneas (FK) utilizadas en el modelo de datos.

Las claves compuestas se generan en Power Query para asegurar unicidad y permitir relaciones eficientes en el modelo.

---

# Nomenclador

**Tipo de Key:**
PK

**Nombre:**
PK

**Composición:**
Fecha + Código de Práctica

**Ejemplo:**
1/2/2024-250121

**Comentarios:**
Fecha corresponde al inicio de mes utilizado para versionar el nomenclador.

---

# Gestion_Total

**Tipo de Key:**
PK

**Nombre:**
PK_Gestion

**Composición:**
Fecha + NroAfiliado + Código de Práctica

**Ejemplo:**
7/7/2025-1402283780030-820113

**Comentarios:**
Fecha de prestación.

---

# Errores_Transmision_Amb

### FK_Gestion

**Tipo:** FK
**Composición:** Fecha + NroAfiliado + Código de Práctica

**Ejemplo:**
7/7/2025-1402283780030-820113

**Comentario:**
Fecha de prestación.

### FK_Nomenclador

**Tipo:** FK
**Composición:** Fecha + Código de Práctica

**Ejemplo:**
1/1/2025-340213

**Comentario:**
Fecha inicio de mes.

---

# Errores_Transmision_Int_OP

### FK_Gestion

**Tipo:** FK
**Composición:** Fecha + NroAfiliado + Código de Práctica

**Ejemplo:**
7/7/2025-1402283780030-820113

**Comentario:**
Fecha de prestación.

### FK_Nomenclador

**Tipo:** FK
**Composición:** Fecha + Código de Práctica

**Ejemplo:**
1/1/2025-340213

**Comentario:**
Fecha inicio de mes.

---

# Errores_Transmision_Int_AC

### FK_Gestion

**Tipo:** FK
**Composición:** Fecha + NroAfiliado + Código de Práctica

**Ejemplo:**
7/7/2025-1402283780030-820113

**Comentario:**
Fecha de prestación.

### FK_Nomenclador

**Tipo:** FK
**Composición:** Fecha + Código de Práctica

**Ejemplo:**
1/1/2025-340213

**Comentario:**
Fecha inicio de mes.

---

# CUP_Total

### FK_Gestion

**Tipo:** FK
**Composición:** Fecha + NroAfiliado + Código de Práctica

**Ejemplo:**
7/7/2025-1402283780030-820113

**Comentario:**
Turno asociado a prestación.

### FK_Nomenclador

**Tipo:** FK
**Composición:** Fecha + Código de Práctica

**Ejemplo:**
1/1/2025-340213

**Comentario:**
Fecha inicio de mes.

---

# Detalles_Internacion_Total

**Tipo:** PK

**Composición:**
NroAfiliado + NroPrestacion

**Ejemplo:**
150412664401-662

**Comentarios:**
Permite verificar relaciones de afiliación o parentesco en internaciones.

---

# SII_Total

### FK_Internacion

**Tipo:** FK

**Composición:**
NroAfiliado + NroPrestacion

**Ejemplo:**
150412664401-662

**Comentarios:**
Referencia a detalles de internación.

---

### FK_Gestion

**Tipo:** FK

**Composición:**
Fecha + NroAfiliado + Código de Práctica

**Ejemplo:**
7/7/2025-1402283780030-820113

**Comentarios:**
Fecha de prestación.

---

### FK_Nomenclador

**Tipo:** FK

**Composición:**
Fecha + Código de Práctica

**Ejemplo:**
1/1/2025-340213

**Comentarios:**
Fecha inicio de mes.

---

# OME_Imagenes

### FK_Gestion

**Tipo:** FK

**Composición:**
Fecha + NroAfiliado + Código de Práctica

**Ejemplo:**
7/7/2025-1402283780030-820113

**Comentarios:**
Fecha de prestación.

---

### FK_Nomenclador

**Tipo:** FK

**Composición:**
Fecha + Código de Práctica

**Ejemplo:**
1/1/2025-340213

**Comentarios:**
Fecha inicio de mes.

---

# Alta_Complejidad

### FK_Gestion

**Tipo:** FK

**Composición:**
Fecha + NroAfiliado + Código de Práctica

**Ejemplo:**
7/7/2025-1402283780030-820113

**Comentarios:**
Fecha de prestación.

---

### FK_Nomenclador

**Tipo:** FK

**Composición:**
Fecha + Código de Práctica

**Ejemplo:**
1/1/2025-340213

**Comentarios:**
Fecha inicio de mes.
