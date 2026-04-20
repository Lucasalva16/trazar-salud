# Modelo de Datos – Proyecto Trazar

Este documento describe la estructura del modelo analítico utilizado en los dashboards de clínicas.

El modelo está implementado en Microsoft Power BI y utiliza datos provenientes del sistema SII y de archivos operativos almacenados en SharePoint.

## Componentes principales

### Dimensiones

* Calendario
* Nomenclador
* Gestión_Total
* Padrón
* Detalles_Internacion_Total
* Capitas_Valor

Estas tablas contienen información descriptiva utilizada para segmentar y filtrar los datos.

### Tablas de hechos

* SII_Total
* CUP_Total
* Errores_Transmision_Amb
* Errores_Transmision_Int_OP
* Errores_Transmision_Int_AC
* OME_Imagenes
* Alta_Complejidad
* Capitas_Cantidad

Estas tablas contienen registros de actividad clínica, prácticas médicas o eventos operativos.

### Principios del modelo

* Modelo tipo **estrella extendida**
* Claves compuestas generadas en Power Query
* Uso intensivo del **Nomenclador** como dimensión central de prácticas
* El calendario controla la mayoría de los cortes temporales
