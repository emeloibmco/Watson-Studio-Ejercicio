# Ejercicio Watson Studio  :robot::cloud:

<br />

## Índice  📰
1. [Pre-Requisitos](#pre-requisitos-pencil)
2. [Crear proyecto en Watson](#Crear-proyecto-en-Watson-open_file_folder)
3. [Cargar y correr notebook Jupiter](#Cargar-y-correr-notebook-Jupiter-closed_book)
4. [Exploración de los datos](#Exploración-de-los-datos-mag)
5. [Transformación de los datos](#Transformación-de-los-datos-arrows_counterclockwise)
6. [Visualización de los datos](#Visualización-de-los-datos-bar_chart)
7. [Referencias](#Referencias-book)
8. [Autores](#Autores-black_nib)

## Pre Requisitos :pencil:
* Contar con una cuenta en <a href="https://cloud.ibm.com/"> IBM Cloud</a>.
* Contar con un servicio de <a href="https://github.com/emeloibmco/IBM-Cloud-Crear-Volumen-Almacenamiento#Crear-servicio-Object-Storage-file_cabinet">Object Storage</a>.
<br />

## Crear proyecto en Watson :open_file_folder:

1. Regístrese o inicie sesión en IBM Cloud.

2. Haga clic en ```Catalogo / Catalog``` en la parte superior de la página. Ingrese en la barra de búsqueda ```Watson Studio```, ingrese al recurso, a continuación complete:

* ```Ubicación / Location```: Seleccione la ubicación donde desea desplegar el recurso.
* ```Plan```: Lite.
* ```Nombre de servicio / Service name```: Elija un nombre para el recurso.
* ``` Grupo de recursos / Resource group```: Seleccione el grupo de recursos donde desea desplegar el recurso.

Asegurese de aceptar los terminos y de click en ```Crear```.

3. Espere a que se despliegue el recurso. Una vez desplegado ingrese al botón ``` Launch in IBM Cloud Pak for Data```. 
4. Cuando haya cargado la plataforma de click en ```Proyectos / Projects``` y a continuación en ``` Nuevo proyecto / New project``` > ```Crear un proyecto vacio / Create an empty project```, a continuación complete lo siguiente:

* ```Nombre del proyecto / Project name```: Elija un nombre para el recurso.
* ```Almacenamiento / Storage```: Seleccione el almacenamiento donde desea desplegar el recurso. Si no tiene uno creado, siga estos <a href="https://github.com/emeloibmco/IBM-Cloud-Crear-Volumen-Almacenamiento#Crear-servicio-Object-Storage-file_cabinet"> pasos </a>.

Por último de click en ```Crear / Create```. 


## Cargar y correr notebook Jupiter :closed_book:

1. Ingrese en el botón ```Añadir al proyecto / Add to project```.
2. Seleccione la opción ```Notebook``` y complete:
* ```Nombre / Name```: Elija un nombre para el notebook.
Las demás opciones pueden dejarse por defecto. De click en ```Crear / Create```. Y espere a que cargue el notebook.
Tenga en cuenta que:
- Para ejecutar el código, seleccione la celda haciendo clic en ella, y luego haga clic en el Runbotón en la parte superior del cuaderno (o use Shift+Enter), para ejecutar las celdas en el cuaderno.
- Los números delante de las celdas le indican en qué orden los ha ejecutado, por ejemplo [1]
- Cuando vea un [\*] la celda se está ejecutando actualmente y [] significa que aún no ha ejecutado la celda.

## Exploración de los datos :mag:
1. Cargue las librerias a utilizar para realizar la exploración:
```
import numpy as np
import pandas as pd
```

2. Ejecute el siguiente código para leer datos de un archivo CSV usando la función read_csv:
```
df  =  pd . read_csv ( 'https://raw.githubusercontent.com/IBMDeveloperUK/Python-Pandas-Workshop/master/london-borough-profiles.csv' , encoding  =  'unicode_escape' )
```

3. Visualice las primeras filas de la base de datos:
```
df.head()
```

4. Visualice los nombres de las columnas de la base de datos:
```
df.columns
```

5. Verifique el tipo de datos de cada una de las columnas de la base de datos:
```
df.dtypes
```

6. Conozca el número de filas de la base de datos:
```
len(df)
```

7. Conozca el número de filas y columnas de la base de datos:
```
df.shape
```

## Transformación de los datos :arrows_counterclockwise:

## Visualización de los datos :bar_chart:

## Referencias :book:
* [Data analysis in python](https://developer.ibm.com/learningpaths/data-analysis-using-python/data-analysis-in-python-using-pandas/).

## Autores :black_nib:
Equipo IBM Cloud Tech Sales Colombia.
<br />

