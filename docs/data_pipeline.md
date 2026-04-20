# Pipeline de Datos

Este documento describe el flujo completo de datos desde los archivos fuente hasta el modelo analítico utilizado en Power BI.

El pipeline está estructurado en múltiples capas para mejorar:

* mantenimiento
* reutilización
* claridad del modelo
* escalabilidad

---

# Arquitectura general

El flujo de datos sigue la siguiente estructura:

SharePoint
↓
files
↓
bases
↓
total
↓
modelo Power BI

Cada capa tiene un propósito específico dentro del proceso de transformación de datos.

---

# 1. Origen de datos

Los datos provienen de archivos almacenados en SharePoint.

Cada dominio del sistema tiene su propio conjunto de archivos:

* SII
* CUP
* Errores
* Gestión

Los archivos se actualizan periódicamente y contienen información operacional del sistema médico.

---

# 2. Capa Files

Consultas:

* sii_files
* cup_files
* errores_files
* gestion_files

## Objetivo

Centralizar la conexión al origen de datos.

Estas consultas:

* acceden a SharePoint
* filtran las carpetas correspondientes
* identifican los archivos relevantes
* preparan la lista de archivos a procesar

## Características

* contienen el único **source dinámico**
* utilizan parámetros para definir la ubicación de los archivos
* no transforman los datos

Esto permite cambiar fácilmente el origen sin modificar el resto del modelo.

---

# 3. Capa Bases

Consultas que procesan cada archivo individual.

Ejemplos:

* SII_Base
* CUP_Base
* Errores_Base
* Gestion_Base

## Objetivo

Transformar la estructura original de los archivos.

Incluye:

* limpieza de columnas
* cambio de tipos de datos
* normalización de nombres
* eliminación de columnas innecesarias

Cada consulta transforma **un archivo individual**.

---

# 4. Capa Total

Consultas que consolidan todos los archivos de una misma fuente.

Ejemplos:

* SII_Total
* CUP_Total
* Errores_Total
* Gestion_Total

## Objetivo

Unificar la información histórica.

Estas consultas:

* combinan todos los archivos procesados
* generan claves del modelo
* agregan columnas derivadas necesarias para el análisis

En esta capa se crean claves como:

* PK_Gestion
* FK_Nomenclador
* FK_Internacion

---

# 5. Modelo analítico

Las tablas finales se cargan en el modelo de Power BI.

Las relaciones principales se estructuran alrededor de tres claves:

PK_Gestion
PK_Nomenclador
PK_Internacion

Estas claves permiten conectar las tablas operacionales con dimensiones analíticas.

---

# Flujo resumido

Archivos operacionales
↓
files (conexión a SharePoint)
↓
bases (limpieza y transformación)
↓
total (consolidación y generación de claves)
↓
modelo analítico Power BI

---

# Beneficios de esta arquitectura

Separar el pipeline en capas permite:

* modificar el origen de datos sin romper el modelo
* reutilizar transformaciones
* mejorar la trazabilidad del proceso
* facilitar la documentación del sistema
* escalar el modelo a nuevas fuentes de datos
