# PI2---Data-Analytics---Horacio-Morazzo

Introducción

En este proyecto se analiza un dataset de la Ciudad Autónoma de Buenos Aires (Argentina) que recopila información respecto a víctimas fatales en accidentes de tránsito, para el período 2016 - 2021.
En base a nuestro análisis, el gobierno de la ciudad podrá tomar decisiones que contribuyan a un descenso en la cantidad de víctimas fatales en el futuro.

Podemos dividir el trabajo en 2 etapas:

* EDA
* Informe en Power Bi

EDA (Análisis exploratorio de datos)

Aquí se analiza el dataset para buscar datos faltantes, repetidos, errores, problemas de codificación, etc.
Una vez que tenemos nuestro dataset limpio y completo, procedemos a buscar relaciones entre las columnas que nos puedan aportar información de interés para nuestro trabajo.
La información de interés se graficará utilizando las librerías matplotlib y seaborn en Python.
Los gráficos más relevantes se incorporarán a Power Bi para aportar información.
En el archivo 'eda.ipynb' además de mostrarse todos los gráficos calculados, se incluyen algunas conclusiones que surgen de la observación de los mismos.

Power Bi y KPI's

El trabajo encomienda la visualización de 2 KPI´s. 
El primero de ellos establece una meta de disminución de un 10% del semestre actual respecto al semestre previo en la la tasa de víctimas fatales. 
El segundo fija una meta de reducción de un 7% del año actual respecto al año previo de la tasa de víctimas fatales en motos.
El tercer KPI es de elaboración propia.
Quiero lograr en un lapso de 4 años una disminución del 50% del número de peatones víctimas de homicidio por vehículos de transporte público de pasajeros. 

Para ello necesitamos una disminución interanual del 16% de los casos.

La fórmula aplicada para mi KPI será: 
((número de casos año previo ) - (número de casos año actual))/(número de casos año previo) * 100 >= 16

La resolución del primer KPI fue la más dificultosa.
Power Bi no es la mejor herramienta para ello. Las medidas rápidas de Power Bi incorporan medidas rápidas de inteligencia de tiempo que no permiten semestre anterior vs. semestre previo en media acumulada. Para ello utilicé una combinación de Python y Power Bi. La otra opción era usar otra herramienta (Google Analytics por ejemplo) que permite esta medida.
Primero armé una tabla con la lista de años y tasa anual de víctimas.
Procesé esa tabla con la medida 'Media acumulada' en las medidas rápidas de Power Bi (archivo 'KPI1.pbix').
Resulta una nueva tabla con la lista de años y media acumulada mes a mes de los seis meses previos, incluído el actual.
Para tener una comparación de semestre previo vs. actual necesito 2 semestres completos, por lo cual los primeros valores a comparar de la tabla anterior son los 2 semestres de 2016, el primero finaliza el 30 de junio de 2016 y el segundo el 31 de diciembre.
Ahora armo una nueva tabla con 3 columnas:

Fecha ----	Media acumulada -6M	---   Media desplazada 

31/12/2016	---------0,347---------------- 0,432

31/1/2016  ----------0,363-----------------0,427

28/2/2017 -----------0,368-----------------0,416

31/3/2017 -----------0,363---------------- 0,416

30/4/2017------------0,368-----------------0,4

   ...           ...                     ...


El primer valor de 'Media acumulada -6M' es el valor correspondiente al 30/6/2016 de la media acumulada calculada por Power Bi y corresponde al primer semestre de 2016.
El primer valor de 'Media desplazada' es el valor correspondiente al 31/12/2016 de la media acumulada calculada por Power Bi y corresponde al segundo semestre de 2016.
Sigo completando con la misma mecánica hasta completar toda la tabla. A ésta tabla la llamo 'Final1.xlsx'.
Esta tabla alimenta a 'PI2 Data Analytics.pbix' para hacer el cálculo final.

La del segundo KPI corresponde a una comparación año a año utilizando una medida rápida.

La del tercer KPI se calcula análogamente a la anterior.

En Power Bi se reúne toda la información previa para mostrarla adecuadamente.





