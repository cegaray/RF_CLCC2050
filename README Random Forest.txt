Código realizado por Carlos F. Morantes A. 
Estimación de cobertura de la tierra para el año 2050 a partir de la cobertura Corine Land Cover adaptada para Colombia entre 2010 – 2012. Este código ejecuta un clasificador para el valor de pixel basado en la extracción de características de los rásteres de origen y rásteres para las variables que desea usar para predecir.
Esta divido en tres secciones principales. Cada sección le pedirá proporcionar información adicional para el proceso. Se debe responder según la pregunta (si o no) para lo cual debe responderse literalmente o escoger la respuesta de un menú de opciones. Para el último caso, se debe escribir el número correspondiente a la opción que se tenga. 
Las secciones anteriormente mencionadas deben cumplir con unos archivos necesarios para poder ser ejecutados. A continuación, la lista de secciones y sus requerimientos. 
- Sección 1: Extrayendo Datos
o Se carga las bibliotecas necesarias para todo el código. 
* Requiere
* Un ráster de origen con la proyección que utilizará para todo el proceso.
* El conjunto de ráster que utilizará para crear el modelo, el cual debe estar dentro de la extensión de todos los demás ráster. No es necesario tener la misma proyección que el archivo de origen puesto que el código los reproyectará de forma automática.
* Un shapefile de puntos (shp) con un campo llamado “id”que contiene el identificador de número entero para cada uno de los puntos en el ráster que desea usar para crear el modelo.
* Elegir un nombre para un archivo de texto para almacenar los datos para la construcción del modelo.
o El resultado de este sección es un archivo que contiene la baso de datos de valores extraídos para el modelo.
- Sección 2: Bosque aleatorio
o Se construye el modelo
* Requiere
* Un nombre para el archivo donde se almacena la información del modelo.
* Seleccionar la variable objetivo en el modelo (lo que se desea predecir) y las variables que se desea utilizar para predecir dicho valor.
* Elegir la cantidad de núcleos que se desea usar para ejecutar el código. 
* Elegir la cantidad de árboles para el bosque. Si no se está seguro de la cantidad, se sugiere usar 150, luego ejecute el código y use la gráfica de error frente a la cantidad de árboles para evaluar el tamaño del bosque adecuado. Luego, ejecute nuevamente esta sección ajustada. 
o El resultado de esta sección es el modelo Random Forest.
- Sección 3: Predicción de valores
o Se utiliza el modelo construido para predecir valores futuros basados en un conjunto de variables predictiva. Para esta sección se debe tener los raster que contienen tales variables almacenados dentro de una carpeta llamada “futurerasters”. Tenga en cuenta que debe estar en el mismo directoro donde se ejecuta este código y los raster deben estar en la misma proyección que el shapefile.
* Requiere
* Que todo el raster que se usará para predecir tenga el mismo nombre (exacto) que los que usó para crear el modelo de la sección anterior.
* Elegir un nombre para un archivo de texto para almacenar los datos de las variables para predecir los valores objetivo.
* Seleccionar como desea que se llame la variable de destino en el archivo de base de datos final que se usará para rasterizar la predicción. Se recomienda evitar usar espacios y empezar con números y guiones. 
* La salida de esta sección es un archivo de texto con los valores predichos para cada punto del shapefile correspondiente a una posición en el archivo raster. 
* También producirá
* Grafica de importancia para cada variable
* Una grafica de error frente al número de árboles. Para este valor, debe seleccionar un número máximo de árboles para probar. Debe ser superior a 16, el número mínimo de árboles se fija en 15. Dependiendo del número máximo de árboles podría tomar algún tiempo.
