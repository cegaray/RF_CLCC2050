C�digo realizado por Carlos F. Morantes A. 
Estimaci�n de cobertura de la tierra para el a�o 2050 a partir de la cobertura Corine Land Cover adaptada para Colombia entre 2010 � 2012. Este c�digo ejecuta un clasificador para el valor de pixel basado en la extracci�n de caracter�sticas de los r�steres de origen y r�steres para las variables que desea usar para predecir.
Esta divido en tres secciones principales. Cada secci�n le pedir� proporcionar informaci�n adicional para el proceso. Se debe responder seg�n la pregunta (si o no) para lo cual debe responderse literalmente o escoger la respuesta de un men� de opciones. Para el �ltimo caso, se debe escribir el n�mero correspondiente a la opci�n que se tenga. 
Las secciones anteriormente mencionadas deben cumplir con unos archivos necesarios para poder ser ejecutados. A continuaci�n, la lista de secciones y sus requerimientos. 
- Secci�n 1: Extrayendo Datos
o Se carga las bibliotecas necesarias para todo el c�digo. 
* Requiere
* Un r�ster de origen con la proyecci�n que utilizar� para todo el proceso.
* El conjunto de r�ster que utilizar� para crear el modelo, el cual debe estar dentro de la extensi�n de todos los dem�s r�ster. No es necesario tener la misma proyecci�n que el archivo de origen puesto que el c�digo los reproyectar� de forma autom�tica.
* Un shapefile de puntos (shp) con un campo llamado �id�que contiene el identificador de n�mero entero para cada uno de los puntos en el r�ster que desea usar para crear el modelo.
* Elegir un nombre para un archivo de texto para almacenar los datos para la construcci�n del modelo.
o El resultado de este secci�n es un archivo que contiene la baso de datos de valores extra�dos para el modelo.
- Secci�n 2: Bosque aleatorio
o Se construye el modelo
* Requiere
* Un nombre para el archivo donde se almacena la informaci�n del modelo.
* Seleccionar la variable objetivo en el modelo (lo que se desea predecir) y las variables que se desea utilizar para predecir dicho valor.
* Elegir la cantidad de n�cleos que se desea usar para ejecutar el c�digo. 
* Elegir la cantidad de �rboles para el bosque. Si no se est� seguro de la cantidad, se sugiere usar 150, luego ejecute el c�digo y use la gr�fica de error frente a la cantidad de �rboles para evaluar el tama�o del bosque adecuado. Luego, ejecute nuevamente esta secci�n ajustada. 
o El resultado de esta secci�n es el modelo Random Forest.
- Secci�n 3: Predicci�n de valores
o Se utiliza el modelo construido para predecir valores futuros basados en un conjunto de variables predictiva. Para esta secci�n se debe tener los raster que contienen tales variables almacenados dentro de una carpeta llamada �futurerasters�. Tenga en cuenta que debe estar en el mismo directoro donde se ejecuta este c�digo y los raster deben estar en la misma proyecci�n que el shapefile.
* Requiere
* Que todo el raster que se usar� para predecir tenga el mismo nombre (exacto) que los que us� para crear el modelo de la secci�n anterior.
* Elegir un nombre para un archivo de texto para almacenar los datos de las variables para predecir los valores objetivo.
* Seleccionar como desea que se llame la variable de destino en el archivo de base de datos final que se usar� para rasterizar la predicci�n. Se recomienda evitar usar espacios y empezar con n�meros y guiones. 
* La salida de esta secci�n es un archivo de texto con los valores predichos para cada punto del shapefile correspondiente a una posici�n en el archivo raster. 
* Tambi�n producir�
* Grafica de importancia para cada variable
* Una grafica de error frente al n�mero de �rboles. Para este valor, debe seleccionar un n�mero m�ximo de �rboles para probar. Debe ser superior a 16, el n�mero m�nimo de �rboles se fija en 15. Dependiendo del n�mero m�ximo de �rboles podr�a tomar alg�n tiempo.
