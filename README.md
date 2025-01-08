# Implementación de un modelo para crear una herramienta que permita determinar perfiles de cliente de un banco usando Clustering.
 
Presenta: Haile Jacobo Meneses Moreno

**Introducción**

Este trabajo forma parte del Curso de Machine Learning Aplicado al Negocio de la IT Academy de Barcelona Activa.

EL dataset con el que trabajo tiene datos provenientes de una campaña de marketing directo de una institución bancaria de Portugal que he denominado Joonie, Luna & Doria Banking Group. Esta campaña está basada en llamadas telefónicas que tienen como objetivo que los clientes contraten un depósito a plazo fijo. 

Estas llamadas con diversa duración y frecuencia obtenían como resultado en estos datos que el depósito era contratado o no (si/no), los resultados basados en frecuencia y duración obtienen diversos resultados según el momento de la temporada.

**Objetivo del Proyecto** 

Crear un instrumento que permita clasificar a los clientes y poder ayudar a crear una oferta de productos bancarios orientada en estos perfiles; buscando evitar un sesgo que limite la cantidad de clientes que puedan contratar servicios con la entidad.

**Metodología Utilizada**

Segmentar a los clientes para encontrar grupos homogéneos en los datos me ha hecho decantarme por un algoritmo como K-Means Clustering; el objetivo es agrupar a los clientes según su perfil para identificar a qué grupo pertenece cada cliente, permitiendo a la entidad tomar la decisión de crear productos y estrategias orientados a cada perfil y así aumentar las contrataciones.

La idea básica es que el algoritmo intentará agrupar a los clientes en K grupos (clusters), donde cada cliente dentro de un grupo es similar entre sí y diferente de los otros grupos.

Después de aplicar K-Means, cada cliente pertenece a uno de los clusters, y podemos interpretar estos grupos y saber a qué tipo de perfil de cliente representa cada cluster.

Una vez que tenemos los clientes agrupados en perfiles, la entidad financiera podría crear y ofrecer productos específicos a cada grupo.

Para evaluar el rendimiento de este algoritmo se tiene que utilizar una métrica distinta a los modelos supervisados, ya que en el clustering no se utilizan etiquetas.

En este caso utilizo Silhouette Score  o Índice de Silueta, que es una de las métricas más utilizadas para evaluar la calidad de un clustering. Mide qué tan cerca están los puntos dentro del mismo cluster y qué tan alejados están de los otros clusters. Toma un valor entre -1 y 1, donde:

*	Valor cercano a 1: Los puntos están bien agrupados y claramente separados de los otros clusters.
*	Valor cercano a 0: Los puntos están en el borde de un cluster o mal agrupados.
*	Valor negativo: Los puntos probablemente están asignados al cluster incorrecto.

Adicionalmente, poder implementar otras métricas dará una visión más robusta de la calidad de la segmentación y garantizará que se puedan tomar mejores decisiones a la hora de aplicar las agrupaciones.

Una de las que utilizo es la Calinski-Harabasz Index, la cual mide la relación entre la dispersión dentro de los clusters y la dispersión entre los clusters. 

Esta métrica es muy eficiente desde el punto de vista computacional y funciona bien para evaluar la calidad general del clustering. Permite medir qué tan "bueno" es el agrupamiento en términos de la dispersión dentro de los clusters y la separación entre ellos.

Una vez entrenado y evaluado el modelo, utilizo Streamlit para crear una APP para desplegar el modelo, donde podrán probarse con datos nuevos a través de este enlace:

[Bank Clustering](https://clusteringbanco-zinrsjan2krdhefbducbe7.streamlit.app/?utm_medium=social)

**Datos Disponibles**

Dentro del conjunto de datos relacionados con el perfil de los clientes disponibles para trabajar con este algoritmo utilizo:

*	Edad
*	Estado Civil
*	Educación
*	Trabajo
*	Balance de cuenta bancaria
*	Hipoteca (Sí/No)
*	Préstamos personales (Sí/No)
*	Deposito ((Sí/No)

**Responsabilidades Éticas y Sociales** 

La principal meta de implementar un proyecto como el que se presenta, radica en evitar el sesgo y que la entidad se plantee ofrecer nuevos productos a más clientes que pueden ser diferenciados o excluidos si se implementa un modelo que los excluya por razones que tradicionalmente les puede hacer inviables a contratar un producto financiero (edad, estado civil, antecedentes bancarios, etc.).

Pero adicionalmente se tendrían en cuenta las siguientes consideraciones:

*	Evitar el sesgo y la discriminación mediante la revisión de los datos y el monitoreo de los clusters generados.
*	Ser transparentes sobre cómo se toman las decisiones y por qué se asignan productos a determinados grupos.
*	Respetar la privacidad y los derechos de los clientes, manejando los datos de manera responsable y con su consentimiento.
*	Fomentar la inclusión financiera en lugar de la exclusión, ofreciendo productos a un espectro más amplio de clientes.
*	Garantizar la supervisión humana y la posibilidad de que los clientes apelen decisiones automatizadas.

Archivos que contiene el repositorio:

* `HAILE_BANK_EDA.ipynb`: Análisis Exploratorio de los Datos
* `HAILE_BANK_KMEANS`: Entrenamiento y Prueba del Modelo
* `app_bank.py`: Archivo para desplegar el modelo con Streamlit
* `kmeans.pkl`: Modelo entrenado para utilizar en Streamlit
* `label_encoders.pkl`: Datos pertenecientes a la codificación de las variables categóricas del modelo
* `requeriments.txt`: Lista de dependencias necesarias para ejecutar el proyecto
* `scaler.pkl`: Escalador utilizado para normalizar los datos

**Resultado del Proyecto:**

La aplicación de este algoritmo de clustering sugiere una segmentación útil para personalizar la oferta de productos. Aunque los índices de calidad indican áreas de mejora (como la superposición de clusters), los perfiles identificados permiten diseñar estrategias enfocadas en las necesidades y comportamiento de cada grupo.

Los clusters parecen estar razonablemente bien definidos, aunque se podría explorar el uso de diferentes características o técnicas de preprocesamiento para mejorar la definición de los clusters, además de considerar otros algoritmos de clustering para complementar el utilizado.

