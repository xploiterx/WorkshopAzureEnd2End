# Azure Modern Data Platform End2End V2

En este taller aprenderá sobre los conceptos principales relacionados con la analítica avanzada y el procesamiento de Big Data y cómo se puede utilizar Azure Data Services para implementar una arquitectura de almacenamiento de datos moderna. Así mismo Aprenderá qué servicios de Azure puede aprovechar para establecer una plataforma de datos sólida para ingerir, procesar y visualizar rápidamente datos de una gran variedad de fuentes de datos. Se ha demostrado que la arquitectura de referencia que creará como parte de este ejercicio le brinda la flexibilidad y escalabilidad para crecer y manejar grandes volúmenes de datos y mantener un nivel óptimo de rendimiento.

En los ejercicios de este laboratorio, creará canalizaciones de datos utilizando datos relacionados con la ciudad de Nueva York. El taller fue diseñado para implementar progresivamente una arquitectura de plataforma de datos moderna extendida a partir de una canalización de datos relacionales tradicional. Luego simularemos escenarios de big data con archivos de datos y computación distribuida. Agregamos datos no estructurados e inteligencia artificial a la mezcla y terminamos con análisis de transmisión en tiempo real. Habrá hecho todo eso al final del taller.

**Nota** ¿Por qué deberías realizar este taller junto con sus laboratorios? Si bien, la teoría de la nube es de muy alto valor - pero la practica es lo que realmente añade el valor agregado en los entornos Cloud - Por esto los talleres + laboratorios tienden a reforzar los conocimientos adquiridos ampliando todo el contexto de aprendizaje.

## Workshop Agenda Propuesta
El taller se puede completar a su propio ritmo dependiendo de su experiencia previa con las herramientas de Azure DP. Las diapositivas de apoyo estarán disponibles para cada formato.

### **Formato**

#### Slides: [Azure Data Platform End2End - 1 Day](https://bit.ly/2SEqPPB)

Actividad | Duración
-------- | ---------
Resumen del taller | 15 minutos
Conceptos de la plataforma de datos moderna: Parte I | 30 minutos
**Almacenamiento de datos moderno** |
Lab 1: Carga de datos en Azure Synapse Analytics mediante Azure Data Factory Pipelines    | 60 minutos
Conceptos de la plataforma de datos moderna: Parte II | 15 minutos
Lab 2: Transformar macrodatos utilizando Azure Data Factory & Mapping Data Flows    | 60 minutos
**Advanced Analytics** |
Conceptos de la plataforma de datos moderna: Parte III | 15 minutes
Lab 3:  Explore Big Data con Azure Databricks    | 60 minutes
Conceptos de la plataforma de datos moderna: Parte IV | 15 minutes
Lab 4: Agregue IA a su Pipeline de Big Data con Cognitive Services    | 120 minutes
**Real-time Analytics** |
Conceptos de la plataforma de datos moderna: Parte V | 15 minutes
Lab 5: Ingesta y analiza datos en tiempo real con Event Hubs y Stream Analytics   | 60 minutes

**IMPORTANT**:

* La arquitectura de referencia propuesta en este taller tiene como objetivo explicar lo suficiente del papel de cada uno de los servicios de datos de Azure incluidos en la arquitectura general de la plataforma de datos moderna. Este taller no reemplaza la necesidad de capacitación en profundidad sobre cada servicio de Azure cubierto.

* Los servicios cubiertos en este curso son solo un subconjunto de una familia mucho más grande de servicios de Azure. Se pueden lograr resultados similares aprovechando otros servicios y / o características que no se cubren en este taller. Los requisitos comerciales específicos pueden requerir el uso de diferentes servicios o características que no se incluyen en este taller.

* Algunos conceptos presentados en este curso pueden ser bastante complejos y es posible que deba buscar más información de diferentes fuentes para complementar su comprensión de los servicios de Azure cubiertos.

![](./Media/ModernDataPlatformReferenceArchitecture.jpg)

### Azure Synapse Analytics

Microsoft anunció recientemente Azure Synapse Analytics como la evolución de Azure SQL Data Warehouse, que combina big data, almacenamiento de datos e integración de datos en un solo servicio para análisis de extremo a extremo a escala de la nube. Esta arquitectura de referencia y el contenido del taller se actualizarán a medida que las características anunciadas en la hoja de ruta estén disponibles públicamente. Para obtener más información, visite: https://azure.microsoft.com/en-au/services/synapse-analytics/

![](./Media/AzureSynapse.png)

## Estructura del documento
Este documento contiene instrucciones detalladas paso a paso sobre cómo implementar una arquitectura de plataforma de datos moderna mediante Azure Data Services. Se recomienda que lea atentamente la descripción detallada contenida en este documento para tener una experiencia exitosa con todos los servicios de Azure. 

Verá la etiqueta IMPORTANTE siempre que haya un paso crítico en el laboratorio. Preste mucha atención a las instrucciones dadas.

También verá la etiqueta IMPORTANTE al comienzo de cada sección de laboratorio. Como algunas instrucciones deben ejecutarse en su computadora host, mientras que otras deben ejecutarse en una conexión de escritorio remoto (RDP), esta etiqueta IMPORTANTE indica dónde debe ejecutar la sección de laboratorio. Vea el ejemplo a continuación:

**IMPORTANTE**|
-------------|
**Ejecute estos pasos en su computadora host**|

## Referencias de fuentes de datos
Los datos New York City utilizados en este laboratorio se obtuvieron del sitio web de datos abiertos de New York City: https://opendata.cityofnewyork.us/. Se utilizaron los siguientes conjuntos de datos
    <br>- NYPD Motor Vehicle Collisions: https://data.cityofnewyork.us/Public-Safety/NYPD-Motor-Vehicle-Collisions/h9gi-nx95
    <br>- TLC Yellow Taxi Trip Data: https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page

## Implementación y requisitos previos del laboratorio
Se deben completar los siguientes requisitos previos antes de comenzar con estos labs:

* Debe estar conectado a Internet.

* Utilice Edge o Chrome al ejecutar los labs. Internet Explorer puede tener problemas al representar la interfaz de usuario para servicios específicos de Azure.


    <br>**IMPORTANTE**: Si implementa los recursos del laboratorio en su propia suscripción, usted es responsable de los cargos relacionados con el uso de los servicios proporcionados. 
  
## Guía de laboratorio

A lo largo de una serie de 5 laboratorios, implementará progresivamente una arquitectura de plataforma de datos moderna utilizando conjuntos de datos New York City.

Comenzará a ingerir datos relacionales sobre colisiones de vehículos motorizados en Manhattan alojados en una base de datos SQL de Azure en su almacén de datos de Azure Synapse Analytics. Luego, presentaremos los conceptos de lago de datos y desafíos de big data y los pondrá en práctica mediante la ingesta y el procesamiento de más de 50 millones de registros de viajes en taxis amarillos almacenados como archivos de datos grandes almacenados en su lago de datos.

Luego, usará Databricks y el poder de los clústeres Spark para explorar archivos de big data. Luego, incorporará AI en su canal de datos invocando la API de Cognitive Services Computer Vision para generar automáticamente metadatos para fotografías de calles de la ciudad de Nueva York y almacenará los metadatos en una base de datos de Cosmos DB. Finalmente, utilizará LogicApp para simular transacciones de compra de acciones de alta frecuencia como fuente de transmisión de eventos que capturará, almacenará y procesará en tiempo real con Event Hubs, Stream Analytics y Power BI.

Al final del taller, habrá implementado la arquitectura del laboratorio a la que se hace referencia a continuación:

![](./Media/LabArchitecture.jpg)

### [Lab 1: Carga de datos en Azure Synapse Analytics mediante Azure Data Factory Pipelines](https://bit.ly/2SEqPPB)

En este laboratorio, el conjunto de datos que usará contiene datos sobre colisiones de vehículos motorizados que ocurrieron en New York City desde 2012 hasta 2019 almacenados en una base de datos relacional. Configurará el entorno de Azure para permitir que los datos relacionales se transfieran desde una base de datos SQL de Azure a un almacén de datos de Azure Synapse Analytics utilizando Azure Data Factory que también se almacena en Azure Data Lake. Utilizará Power BI para visualizar los datos de colisión cargados desde su almacén de datos de Azure Synapse.

El tiempo estimado para completar esta práctica de laboratorio es de: **45 minutos**.

Step     | Description
-------- | -----
![1](./Media/Black1.png) | Cree una canalización de Azure Data Factory para copiar datos de una tabla de Azure SQL Database
![2](./Media/Black2.png) | Use Azure Data Lake Storage Gen2 como área de preparación para Polybase
![3](./Media/Black3.png) | Cargar datos en una tabla de Azure Synapse Analytics con Polybase
![4](./Media/Black4.png) | VVisualice datos de Azure Synapse Analytics con Power BI

![](./Media/Lab1-Image51.png)

### [Lab 2: Transformar macrodatos utilizando flujos de datos de mapeo de Azure Data Factory](https://bit.ly/2SEqPPB)
En este laboratorio, el conjunto de datos que usará contiene viajes detallados en taxis amarillos de la ciudad de Nueva York durante el primer semestre de 2019. Utilizará Azure Data Factory para descargar archivos de datos grandes en su lago de datos. Generará un resumen agregado diario de todos los viajes desde el lago de datos mediante Mapeo de flujos de datos y guardará el conjunto de datos resultante en Azure Synapse Analytics. Utilizará Power BI para visualizar datos resumidos de viajes en taxi.

El tiempo estimado para completar esta práctica de laboratorio es de: **60 minutos**.

 
Step     | Descripción
-------- | -----
![](./Media/Green1.png) | Cree una canalización de Azure Data Factory para copiar archivos de big data desde Azure Storage compartido
![](./Media/Green2.png) | Ingesta archivos de datos en tu lago de datos
![](./Media/Green3.png) | Use Mapping Data Flows para generar un resumen diario agregado y guarde el conjunto de datos resultante en su almacén de datos de Azure Synapse.
![](./Media/Green4.png) | Visualice datos de Azure Synapse Analytics con Power BI

![](./Media/Lab2-Image40.png)

### [Lab 3: Explore Big Data using Azure Databricks](https://bit.ly/2SEqPPB)
En este laboratorio, usará Azure Databricks para explorar los archivos de datos de taxis de Nueva York que guardó en su lago de datos en el Laboratorio 2. Con un cuaderno de Databricks, se conectará al lago de datos y consultará los detalles del viaje en taxi para la limpieza de datos y para aplicar la columna estándar. definiciones para el conjunto de datos resultante. Al finalizar, el conjunto de datos resultante debe guardarse en una tabla Spark utilizando archivos Parquet que se encuentran en el contenedor NYCTaxiData-Curated en su cuenta de almacenamiento SynapseDataLake.

El tiempo estimado para completar esta práctica de laboratorio es:  **45 minutos**.

Step     | Description
-------- | -----
![](./Media/Red1.png) |Cree un cuaderno de Azure Databricks para explorar los archivos de datos que guardó en su lago de datos en el ejercicio anterior. Utilizará comandos de Python y SQL para abrir una conexión a su lago de datos y consultar datos de archivos de datos.
![](./Media/Red2.png) |Integré conjuntos de datos del almacén de datos de Azure Synapse Analytics a su canalización de procesamiento de big data. Databricks se convierte en el puente entre sus almacenes de datos relacionales y no relacionales.

![](./Media/Lab3-Image14.png)

### [Lab 4: Agregue IA a su canalización de Big Data con Cognitive Services](https://bit.ly/2SEqPPB)
En este laboratorio, utilizará Azure Data Factory para descargar imágenes de la ciudad de Nueva York en su lago de datos. Luego, como parte de la misma canalización, usará un cuaderno de Azure Databricks para invocar el Servicio Computer Vision Cognitive Service para generar documentos de metadatos y guardarlos en su lago de datos. Luego, la canalización de Azure Data Factory finaliza al guardar toda la información de metadatos en una colección de Cosmos DB. Utilizará Power BI para visualizar imágenes de la ciudad de Nueva York y sus metadatos generados por IA.

El tiempo estimado para completar esta práctica de laboratorio es: **75 minutos**.

Step     | Description
-------- | -----
![](./Media/Blue1.png) | Cree una canalización de Azure Data Factory para copiar archivos de imagen desde Azure Storage compartido
![](./Media/Blue2.png) | Guarde archivos de imagen en su lago de datos
![](./Media/Blue3.png) | Para cada imagen en su lago de datos, invoque un cuaderno de Azure Databricks que tomará la URL de la imagen como parámetro.
![](./Media/Blue4.png) | Para cada imagen, llame al servicio Cognitivo de Azure Computer Vision para generar metadatos de imagen. Los archivos de metadatos se guardan nuevamente en su lago de datos
![](./Media/Blue5.png) | Copie documentos JSON de metadatos en su base de datos de Cosmos DB
![](./Media/Blue6.png) | Visualice imágenes y metadatos asociados con Power BI

![](./Media/Lab4-Image70.png)

### [Lab 5: Ingesta y analiza datos en tiempo real con Event Hubs y Stream Analytics](https://bit.ly/2SEqPPB)
En este laboratorio, utilizará una aplicación Azure Logic para simular un flujo de transacciones de compra de acciones de NYSE. La aplicación lógica enviará los mensajes a Event Hubs. Luego, utilizará Stream Analytics para recibir y procesar el flujo y realizar agregaciones para calcular el número de transacciones y la cantidad negociada en los últimos 10 segundos. Stream Analytics enviará los resultados a un conjunto de datos en tiempo real en Power BI.

El tiempo estimado para completar esta práctica de laboratorio es: **45 minutos**.

Step     | Description
-------- | -----
![](./Media/Orange1.png) | Revise la lógica de la aplicación Azure Logic que simula el flujo de transacciones de NYSE enviado a EventHubs
![](./Media/Orange2.png) | Guarde los mensajes de transacciones de acciones de NYSE simulados en su lago de datos para análisis futuros (ruta fría)
![](./Media/Orange3.png) | Envíe el flujo de mensajes de transacciones de acciones de NYSE a Stream Analytics para análisis en tiempo real (ruta activa)
![](./Media/Orange4.png) | Incorpore datos de referencia de la compañía de valores en su lógica de procesamiento de flujo
![](./Media/Orange5.png) | Visualice datos en tiempo real generados por Stream Analytics con Power BI

![](./Media/Lab5-Image66.png)
