# Azure Data Platform End2End -2

En este taller aprenderá sobre los conceptos principales relacionados con la analítica avanzada y el procesamiento de Big Data y cómo se puede utilizar Azure Data Services para implementar una arquitectura de almacenamiento de datos moderna. Así mismo Aprenderá qué servicios de Azure puede aprovechar para establecer una plataforma de datos sólida para ingerir, procesar y visualizar rápidamente datos de una gran variedad de fuentes de datos. Se ha demostrado que la arquitectura de referencia que creará como parte de este ejercicio le brinda la flexibilidad y escalabilidad para crecer y manejar grandes volúmenes de datos y mantener un nivel óptimo de rendimiento.

En los ejercicios de este laboratorio, creará canalizaciones de datos utilizando datos relacionados con la ciudad de Nueva York. El taller fue diseñado para implementar progresivamente una arquitectura de plataforma de datos moderna extendida a partir de una canalización de datos relacionales tradicional. Luego simularemos escenarios de big data con archivos de datos y computación distribuida. Agregamos datos no estructurados e inteligencia artificial a la mezcla y terminamos con análisis de transmisión en tiempo real. Habrá hecho todo eso al final del taller.

**Nota** Este taller es parte de un curso que estará publicado en la plataforma Udemy con el objetivo de ofrecer certificación que valide las competencias realizadas en este taller. Por otro lado, cabe destacar que no fue posible ofrecer en esta plataforma la integración de este taller junto con sus laboratorios por temas de precios. Esto obedece a que - en udemy - todos los cursos publicados no tienen un costo fijo - sino que, por el contrario, son elásticos; es decir, si este taller tiene un costo entre la teoría + los laboratorios en entornos reales Azure alrededor de 100 dólares - Udemy, a través de sus algoritmos podrían rebajarlo a 20 o 15 dólares lo que, en la practica, sería imposible ofrecer los laboratorios bajo esta primicia ya que, como todos ustedes sabrán, estos laboratorios tienen costos fijo en nuestra plataforma Azure.

Por esto, y para las personas que a futuro tomarán este curso a través de udemy - tendrán dos opciones – realizarlo con sus propias suscripciones Azure o a través de nuestra plataforma con un costo fijo sin comprometer sus tarjetas de crédito para estos laboratorios.

**Nota2** ¿Por qué deberías realizar este taller junto con sus laboratorios? Si bien, la teoría de la nube es de muy alto valor - pero la practica es lo que realmente añade el valor agregado en los entornos Cloud - Por esto los talleres + laboratorios tienden a reforzar los conocimientos adquiridos ampliando todo el contexto de aprendizaje.

## Workshop Agenda Propuesta
El taller se puede completar a su propio ritmo dependiendo de su experiencia previa con las herramientas de Azure DP. Las diapositivas de apoyo estarán disponibles para cada formato.

### **1-Día Formato**

#### Slides: [Azure Data Platform End2End - 1 Day](https://bit.ly/2SEqPPB)

Actividad | Duración
-------- | ---------
Resumen del taller | 15 minutos
Conceptos de la plataforma de datos moderna: Parte I | 15 minutos
**Almacenamiento de datos moderno** |
Lab 1: Carga de datos en Azure Synapse Analytics mediante Azure Data Factory Pipelines    | 45 minutos
Conceptos de la plataforma de datos moderna: Parte II | 15 minutos
Lab 2: Transformar macrodatos utilizando Azure Data Factory & Mapping Data Flows    | 60 minutos
**Advanced Analytics** |
Conceptos de la plataforma de datos moderna: Parte III | 15 minutes
Lab 3:  Explore Big Data con Azure Databricks    | 45 minutes
Conceptos de la plataforma de datos moderna: Parte IV | 15 minutes
Lab 4: Agregue IA a su Pipeline de Big Data con Cognitive Services    | 75 minutes
**Real-time Analytics** |
Conceptos de la plataforma de datos moderna: Parte V | 15 minutes
Lab 5: Ingesta y analiza datos en tiempo real con Event Hubs y Stream Analytics   | 45 minutes

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
Los datos de la ciudad de Nueva York utilizados en este laboratorio se obtuvieron del sitio web de datos abiertos de la ciudad de Nueva York: https://opendata.cityofnewyork.us/. Se utilizaron los siguientes conjuntos de datos
    <br>- NYPD Motor Vehicle Collisions: https://data.cityofnewyork.us/Public-Safety/NYPD-Motor-Vehicle-Collisions/h9gi-nx95
    <br>- TLC Yellow Taxi Trip Data: https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page

## Implementación y requisitos previos del laboratorio
Se deben completar los siguientes requisitos previos antes de comenzar con estos labs:

* Debe estar conectado a Internet.

* Utilice Edge o Chrome al ejecutar los labs. Internet Explorer puede tener problemas al representar la interfaz de usuario para servicios específicos de Azure.

* Debe tener una cuenta de Azure Pay-As-You-Go con acceso de nivel de administrador o colaborador en su suscripción. Si no tiene una cuenta, puede registrarse para obtener una siguiendo las instrucciones aquí: https://azure.microsoft.com/en-au/pricing/purchase-options/pay-as-you-go/.

    <br>**IMPORTANTE**: las suscripciones gratuitas de Azure tienen restricciones de cuota que impiden que los recursos del taller se implementen correctamente. En su lugar, utilice una suscripción de pago por uso.

    <br>**IMPORTANTE**:Cuando implementa los recursos del laboratorio en su propia suscripción, usted es responsable de los cargos relacionados con el uso de los servicios proporcionados. Para obtener más información sobre la lista de servicios y sugerencias sobre cómo ahorrar dinero al ejecutar estos laboratorios, nosotros te proporcionaremos, una vez comiences con estos labs,  tips para la administración y reducción de costos.

* Los laboratorios 1 a 4 requieren que abra una conexión de escritorio remoto (RDP) a Azure Virtual Machines. Si está utilizando una Mac, asegúrese de tener instalada la última versión del software Microsoft Remote Desktop: https://apps.apple.com/us/app/microsoft-remote-desktop-10/id1295203466?mt=12

* Lab 5 requiere que tenga una cuenta de Power BI Pro. Si no tiene una cuenta, puede registrarse para una prueba gratuita de 60 días aquí: https://powerbi.microsoft.com/en-us/power-bi-pro/
  
## Guía de laboratorio

A lo largo de una serie de 5 laboratorios, implementará progresivamente una arquitectura de plataforma de datos moderna utilizando conjuntos de datos de la ciudad de Nueva York.

Comenzará a ingerir datos relacionales sobre colisiones de vehículos motorizados en Manhattan alojados en una base de datos SQL de Azure en su almacén de datos de Azure Synapse Analytics. Luego, presentaremos los conceptos de lago de datos y desafíos de big data y los pondrá en práctica mediante la ingesta y el procesamiento de más de 50 millones de registros de viajes en taxis amarillos almacenados como archivos de datos grandes almacenados en su lago de datos.

Luego, usará Databricks y el poder de los clústeres Spark para explorar archivos de big data. Luego, incorporará AI en su canal de datos invocando la API de Cognitive Services Computer Vision para generar automáticamente metadatos para fotografías de calles de la ciudad de Nueva York y almacenar los metadatos en una base de datos de Cosmos DB. Finalmente, utilizará una LogicApp para simular transacciones de compra de acciones de alta frecuencia como fuente de transmisión de eventos que capturará, almacenará y procesará en tiempo real con Event Hubs, Stream Analytics y Power BI.

Al final del taller, habrá implementado la arquitectura del laboratorio a la que se hace referencia a continuación:

![](./Media/LabArchitecture.jpg)

### [Lab 0: Deploy Azure Data Platform End2End to your subscription](https://bit.ly/2SEqPPB)

**IMPORTANTE**: debe omitir este laboratorio si está ejecutando los labs a través de las suscripciones proporcionadas por TeamWorks. Todos los servicios de Azure se implementarán cuando active su registro.

En esta sección, proporcionará automáticamente todos los recursos de Azure necesarios para completar los laboratorios del 1 al 5. Usaremos una plantilla ARM predefinida con la definición de todos los servicios de Azure utilizados para ingerir, almacenar, procesar y visualizar datos.

El tiempo estimado para completar esta práctica de laboratorio es de: **30 minutos**.

### [Lab 1: Carga de datos en Azure Synapse Analytics mediante Azure Data Factory Pipelines]

En este laboratorio, el conjunto de datos que usará contiene datos sobre colisiones de vehículos motorizados que ocurrieron en New York City desde 2012 hasta 2019 almacenados en una base de datos relacional. Configurará el entorno de Azure para permitir que los datos relacionales se transfieran desde una base de datos SQL de Azure a un almacén de datos de Azure Synapse Analytics utilizando Azure Data Factory que también se almacena en Azure Data Lake. Utilizará Power BI para visualizar los datos de colisión cargados desde su almacén de datos de Azure Synapse.

El tiempo estimado para completar esta práctica de laboratorio es de: **45 minutos**.

Step     | Description
-------- | -----
![1](./Media/Black1.png) | Cree una canalización de Azure Data Factory para copiar datos de una tabla de Azure SQL Database
![2](./Media/Black2.png) | Use Azure Data Lake Storage Gen2 como área de preparación para Polybase
![3](./Media/Black3.png) | Cargar datos en una tabla de Azure Synapse Analytics con Polybase
![4](./Media/Black4.png) | VVisualice datos de Azure Synapse Analytics con Power BI

![](./Lab/Lab1/Media/Lab1-Image51.png)

### [Lab 2: Transformar macrodatos utilizando flujos de datos de mapeo de Azure Data Factory](https://bit.ly/2SEqPPB)
En este laboratorio, el conjunto de datos que usará contiene viajes detallados en taxis amarillos de la ciudad de Nueva York durante el primer semestre de 2019. Utilizará Azure Data Factory para descargar archivos de datos grandes en su lago de datos. Generará un resumen agregado diario de todos los viajes desde el lago de datos mediante Mapeo de flujos de datos y guardará el conjunto de datos resultante en Azure Synapse Analytics. Utilizará Power BI para visualizar datos resumidos de viajes en taxi.

El tiempo estimado para completar esta práctica de laboratorio es de: **60 minutos**.

 
Step     | Descripción
-------- | -----
![](./Media/Green1.png) | Cree una canalización de Azure Data Factory para copiar archivos de big data desde Azure Storage compartido
![](./Media/Green2.png) | Ingesta archivos de datos en tu lago de datos
![](./Media/Green3.png) | Use Mapping Data Flows para generar un resumen diario agregado y guarde el conjunto de datos resultante en su almacén de datos de Azure Synapse.
![](./Media/Green4.png) | Visualice datos de Azure Synapse Analytics con Power BI

![](./Lab/Lab2/Media/Lab2-Image40.png)

### [Lab 3: Explore Big Data using Azure Databricks](https://bit.ly/2SEqPPB)
En este laboratorio, usará Azure Databricks para explorar los archivos de datos de taxis de Nueva York que guardó en su lago de datos en el Laboratorio 2. Con un cuaderno de Databricks, se conectará al lago de datos y consultará los detalles del viaje en taxi para la limpieza de datos y para aplicar la columna estándar. definiciones para el conjunto de datos resultante. Al finalizar, el conjunto de datos resultante debe guardarse en una tabla Spark utilizando archivos Parquet que se encuentran en el contenedor NYCTaxiData-Curated en su cuenta de almacenamiento SynapseDataLake.

El tiempo estimado para completar esta práctica de laboratorio es:  **45 minutos**.

Step     | Description
-------- | -----
![](./Media/Red1.png) |Build an Azure Databricks notebook to explore the data files you saved in your data lake in the previous exercise. You will use Python and SQL commands to open a connection to your data lake and query data from data files.
![](./Media/Red2.png) |Integrate datasets from Azure Synapse Analytics data warehouse to your big data processing pipeline. Databricks becomes the bridge between your relational and non-relational data stores.

![](./Lab/Lab3/Media/Lab3-Image14.png)

### [Lab 4: Agregue IA a su canalización de Big Data con Cognitive Services](https://bit.ly/2SEqPPB)
En este laboratorio, utilizará Azure Data Factory para descargar imágenes de la ciudad de Nueva York en su lago de datos. Luego, como parte de la misma canalización, usará un cuaderno de Azure Databricks para invocar el Servicio cognitivo de visión por computadora para generar documentos de metadatos y guardarlos en su lago de datos. Luego, la canalización de Azure Data Factory finaliza al guardar toda la información de metadatos en una colección de Cosmos DB. Utilizará Power BI para visualizar imágenes de la ciudad de Nueva York y sus metadatos generados por IA.

El tiempo estimado para completar esta práctica de laboratorio es: **75 minutos**.

Step     | Description
-------- | -----
![](./Media/Blue1.png) | Cree una canalización de Azure Data Factory para copiar archivos de imagen desde Azure Storage compartido
![](./Media/Blue2.png) | Guarde archivos de imagen en su lago de datos
![](./Media/Blue3.png) | Para cada imagen en su lago de datos, invoque un cuaderno de Azure Databricks que tomará la URL de la imagen como parámetro.
![](./Media/Blue4.png) | Para cada imagen, llame al servicio Cognitivo de Azure Computer Vision para generar metadatos de imagen. Los archivos de metadatos se guardan nuevamente en su lago de datos
![](./Media/Blue5.png) | Copie documentos JSON de metadatos en su base de datos de Cosmos DB
![](./Media/Blue6.png) | Visualice imágenes y metadatos asociados con Power BI

![](./Lab/Lab4/Media/Lab4-Image70.png)

### [Lab 5: Ingest and Analyse real-time data with Event Hubs and Stream Analytics](./Lab/Lab5/Lab5.md)
In this lab you will use an Azure Logic App to simulate a NYSE stream of stock purchase transactions. The logic app will then send the messages to Event Hubs. You will then use Stream Analytics to receive and process the stream and perform aggregations to calculate the number of transactions and amount traded in the last 10 seconds. Stream Analytics will send the results to a real-time dataset in Power BI.

The estimated time to complete this lab is: **45 minutes**.

Step     | Description
-------- | -----
![](./Media/Orange1.png) | Review the Azure Logic App logic that simmulates the NYSE transaction stream sent to EventHubs
![](./Media/Orange2.png) | Save simulated NYSE stock transaction messages into your data lake for future analysis (cold path)
![](./Media/Orange3.png) | Send stream of NYSE stock transaction messages to Stream Analytics for real-time analytics (hot path)
![](./Media/Orange4.png) | Incorporate Stock Company reference data into your stream processing logic
![](./Media/Orange5.png) | Visualize real-time data generated by Stream Analytics with Power BI

![](./Lab/Lab5/Media/Lab5-Image66.png)
