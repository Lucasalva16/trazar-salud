# Keys estructurales del modelo

El modelo analítico utiliza tres claves estructurales que permiten conectar la mayoría de las tablas del sistema.

Estas claves se generan en Power Query a partir de campos operacionales del sistema SII y garantizan la integridad relacional del modelo.

---

# 1. PK_Gestion

## Descripción

Clave que identifica una **prestación médica individual realizada a un afiliado**.

Es la clave más utilizada del modelo y representa la unidad básica de actividad médica.

---

## Composición

Fecha de prestación
+
Número de afiliado
+
Código de práctica

---

## Ejemplo

7/7/2025-1402283780030-820113

---

## Tablas donde aparece

Tabla donde es **PK**

* Gestion_Total

Tablas donde aparece como **FK**

* SII_Total
* CUP_Total
* Errores_Transmision_Amb
* Errores_Transmision_Int_OP
* Errores_Transmision_Int_AC
* OME_Imagenes
* Alta_Complejidad

---

## Uso en el modelo

Permite:

* vincular eventos de gestión con prácticas registradas
* analizar errores de transmisión
* conectar prácticas con estudios o eventos asociados

Funciona como **identificador transversal de prestaciones médicas**.

---

# 2. PK_Nomenclador

## Descripción

Clave que identifica una práctica médica dentro del **nomenclador vigente en un período determinado**.

Se utiliza para versionar el catálogo de prácticas.

---

## Composición

Fecha inicio de mes
+
Código de práctica

---

## Ejemplo

1/1/2025-340213

---

## Tablas donde aparece

Tabla donde es **PK**

* Nomenclador

Tablas donde aparece como **FK**

* SII_Total
* CUP_Total
* Errores_Transmision_Amb
* Errores_Transmision_Int_OP
* Errores_Transmision_Int_AC
* OME_Imagenes
* Alta_Complejidad

---

## Uso en el modelo

Permite:

* identificar prácticas médicas
* acceder a atributos del nomenclador
* mantener historial de cambios en valores o categorías de prácticas

Actúa como **dimensión central de prácticas médicas**.

---

# 3. PK_Internacion

## Descripción

Clave que identifica un episodio de internación para un afiliado.

Se utiliza para conectar prestaciones realizadas durante una internación con los datos del episodio.

---

## Composición

Número de afiliado
+
Número de prestación

---

## Ejemplo

150412664401-662

---

## Tablas donde aparece

Tabla donde es **PK**

* Detalles_Internacion_Total

Tabla donde aparece como **FK**

* SII_Total

---

## Uso en el modelo

Permite:

* analizar prácticas realizadas durante internaciones
* vincular prestaciones con información del episodio clínico
* verificar relaciones de parentesco o afiliación

Funciona como **identificador de episodios de internación**.
