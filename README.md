# Ejercicio Watson Studio  :robot::cloud:
En esta guía se muestra el desarrollo de un notebook en Jupyter que estará desplegado en un proyecto de Watson Studio de IBM Cloud. En este notebook se realiza la exploración, transformación y visualización de una base de datos de distritos de Londres. 
<br />

## Índice  📰
1. [Pre-Requisitos](#pre-requisitos-pencil)
2. [Crear proyecto en Watson](#Crear-proyecto-en-Watson-open_file_folder)
3. [Cargar y correr notebook Jupyter](#Cargar-y-correr-notebook-Jupyter-closed_book)
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
<br />

<p align="center"><img width="700" src="https://github.com/emeloibmco/Watson-Studio-Ejercicio/blob/main/Imagenes/watson.gif"></p>
<br />

## Cargar y correr notebook Jupyter :closed_book:

1. Ingrese en el botón ```Añadir al proyecto / Add to project```.
2. Seleccione la opción ```Notebook``` y complete:
* ```Nombre / Name```: Elija un nombre para el notebook.
Las demás opciones pueden dejarse por defecto. De click en ```Crear / Create```. Y espere a que cargue el notebook.

Tenga en cuenta que:
- Para ejecutar el código, seleccione la celda haciendo clic en ella, y luego haga clic en el Runbotón en la parte superior del cuaderno (o use Shift+Enter), para ejecutar las celdas en el cuaderno.
- Los números delante de las celdas le indican en qué orden los ha ejecutado, por ejemplo [1]
- Cuando vea un [\*] la celda se está ejecutando actualmente y [] significa que aún no ha ejecutado la celda.
<br />

<p align="center"><img width="700" src="https://github.com/emeloibmco/Watson-Studio-Ejercicio/blob/main/Imagenes/notebook.gif"></p>
<br />

Recuerde añadir una nueva celda, como se observa en el video, para ejecutar cada porción de código que se muestra a continuación y asi poder evidenciar los resultados.

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
8. Visualice las estadisticas por cada columna de la base de datos:
```
df.describe()
```
9. Observe una columna en especifico:
```
df.iloc[0]
```
10. Filtre los datos:
```
df['Average_Age,_2017'] > 39
```
<br />

<p align="center"><img width="700" src="https://github.com/emeloibmco/Watson-Studio-Ejercicio/blob/main/Imagenes/explora.gif"></p>
<br />

## Transformación de los datos :arrows_counterclockwise:

1. Agregue una nueva columna a la base de datos y visualicelo:
```
df['new']= 1 
df.head()
```

2. Elimine la columna agregada y visualicelo:
```
df = df.drop(columns='new')
df.head()
```

3. Renombre algunas columnas de la base de datos:
```
df.rename(columns={'Area_name':'Name',
                'Inner/_Outer_London':'Inner/Outer',
                'GLA_Population_Estimate_2017':'Population',
                'Inland_Area_(Hectares)':'Area (ha)',
                'Average_Age,_2017':'Average Age',
                'Political_control_in_council':'Political control',
                'Population_density_(per_hectare)_2017':'Population density (/ha)',
                'New_migrant_(NINo)_rates,_(2015/16)':'New migrant rates',
                'Happiness_score_2011-14_(out_of_10)':'Happiness score',
                '%_of_resident_population_born_abroad_(2015)':'Population born abroad (%)',
                'Employment_rate_(%)_(2015)':'Employment rate (%)',
                'Turnout_at_2014_local_elections':'Turnout at local elections',
                'Median_House_Price,_2015':'Median House Price',
                "Largest_migrant_population_by_country_of_birth_(2011)":'Largest migrant population',
                'Gross_Annual_Pay_-_Female_(2016)':'Gross Pay (Female)',
                'Gross_Annual_Pay_-_Male_(2016)':'Gross Pay (Male)',
                '%_of_area_that_is_Greenspace,_2005':'Greenspace (%)'},
                 inplace=True)
df.head()
```
4. Elimine las filas con los datos NaN
```
df['Population density (/ha)'].dropna()
df.head()
```
<br />

<p align="center"><img width="700" src="https://github.com/emeloibmco/Watson-Studio-Ejercicio/blob/main/Imagenes/transforma.gif"></p>
<br />

## Visualización de los datos :bar_chart:

1. Pandas utiliza Matplotlib como predeterminado para las visualizaciones. Importe la libreria.
```
import matplotlib.pyplot as plt

%matplotlib inline
```

2. Visualice el gráfico de linea de una de las columnas:
```
df['Employment rate (%)'].plot();
```

3. Para el ejemplo anterior, un histograma podría funcionar mejor:
```
df['Employment rate (%)'].plot.hist(bins=10);
```

4. Cambie el tamaño del histograma:
```
df['Employment rate (%)'].plot.hist(bins=15,figsize=(10,5));
```
5. Visualice un diagrama de caja:
```
import seaborn as sns
sns.catplot(x='Employment rate (%)', y='Largest migrant population', kind="box", data=df);
```
<br />

<p align="center"><img width="700" src="https://github.com/emeloibmco/Watson-Studio-Ejercicio/blob/main/Imagenes/visualiza.gif"></p>
<br />

## Referencias :book:
* [Data analysis in python](https://developer.ibm.com/learningpaths/data-analysis-using-python/data-analysis-in-python-using-pandas/).

## Autores :black_nib:
Equipo IBM Cloud Tech Sales Colombia.
<br />

