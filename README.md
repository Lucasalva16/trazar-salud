# Trazar Salud — Data Model

Este repositorio documenta la arquitectura de datos utilizada para construir dashboards analíticos sobre información operacional de clínicas dentro del ecosistema Trazar Salud.

El objetivo del proyecto es mejorar la **trazabilidad de prestaciones médicas**, conectando distintas fuentes operacionales para detectar inconsistencias, analizar actividad clínica y facilitar auditorías.

---

# Objetivo del modelo

Los sistemas operacionales generan distintos registros relacionados con la atención médica:

* turnos médicos
* prácticas realizadas
* nomenclador de prácticas
* errores de transmisión
* episodios de internación

Sin embargo, estos registros se encuentran distribuidos en diferentes archivos y sistemas.

El modelo desarrollado en este proyecto permite **integrar esas fuentes en un modelo analítico único**, que permite responder preguntas como:

* ¿Qué prácticas médicas fueron realizadas?
* ¿Qué prácticas estaban asociadas a un turno?
* ¿Existen prácticas registradas sin turno previo?
* ¿Qué errores de transmisión se produjeron?
* ¿Cómo se relacionan las prácticas con el nomenclador vigente?
* ¿Qué prestaciones están asociadas a internaciones?

Este modelo permite construir dashboards de control operativo, auditoría y análisis de actividad clínica.

---

# Arquitectura del pipeline de datos

El pipeline de datos está implementado en Power Query y sigue una arquitectura de capas que facilita el mantenimiento y la reutilización del modelo.

Flujo general:

SharePoint
↓
files
↓
bases
↓
total
↓
modelo analítico

Cada capa tiene una responsabilidad específica dentro del proceso de transformación.

---

## 1. Files

Consultas encargadas de conectarse a las carpetas de SharePoint y detectar los archivos disponibles.

Ejemplos:

* sii_files
* cup_files
* errores_files
* gestion_files

Responsabilidades:

* conectarse a SharePoint
* filtrar carpetas relevantes
* listar archivos disponibles

Esta capa contiene el **source del pipeline**.

---

## 2. Bases

Transformación de cada archivo individual.

Ejemplos:

* SII_Base
* CUP_Base
* Errores_Base
* Gestion_Base

Responsabilidades:

* limpieza de columnas
* normalización de nombres
* tipado de campos
* eliminación de columnas innecesarias

Cada consulta transforma **un archivo individual**.

---

## 3. Total

Consolidación histórica de cada dominio de datos.

Ejemplos:

* SII_Total
* CUP_Total
* Errores_Total
* Gestion_Total

Responsabilidades:

* combinar todos los archivos históricos
* generar claves estructurales del modelo
* agregar columnas derivadas para análisis

Estas tablas son las que finalmente alimentan el modelo analítico.

---

# Modelado de datos

El modelo se basa en un conjunto de **claves estructurales** que permiten relacionar las distintas tablas del sistema.

Las tres claves principales del modelo son:

### PK_Gestion

Identifica una prestación médica realizada.

Composición:

fecha de prestación
+
número de afiliado
+
código de práctica

Esta clave permite conectar:

* prácticas registradas
* errores de transmisión
* estudios asociados
* registros administrativos

---

### PK_Nomenclador

Identifica una práctica dentro del nomenclador vigente en un período determinado.

Composición:

inicio de mes
+
código de práctica

Esto permite mantener histórico del nomenclador y analizar cambios en el tiempo.

---

### PK_Internacion

Identifica un episodio de internación.

Composición:

número de afiliado
+
número de prestación

Permite vincular prácticas médicas con episodios de internación.

---

# Modelo conceptual

El modelo conecta diferentes dominios de información clínica.

Relación simplificada:

Nomenclador
↑
Prácticas médicas (SII / CUP / Gestión)
↑
Errores de transmisión
↑
Internaciones

Esto permite analizar la actividad médica desde diferentes perspectivas:

* operativa
* administrativa
* clínica
* auditoría

---

# Reutilización del modelo

El mismo modelo se utiliza para diferentes clínicas.

Las diferencias entre implementaciones se encuentran únicamente en la ubicación de los archivos fuente en SharePoint.

Ejemplos de sitios utilizados:

* VillaDolores
* Parque
* SanRoque

La estructura de carpetas y archivos es idéntica entre clínicas, lo que permite reutilizar el mismo pipeline cambiando únicamente el origen de datos.

---

# Documentación adicional

El repositorio incluye documentación detallada del modelo:

docs/tables.md
docs/relationships.md
docs/structural_keys.md
docs/pipeline.md

Estos documentos describen en detalle:

* tablas del modelo
* relaciones
* claves estructurales
* flujo de datos
