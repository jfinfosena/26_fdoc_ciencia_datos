---
title: "Graficos en  Streamlit"
position: 5
---

Streamlit es una biblioteca de Python que permite crear aplicaciones web interactivas con código Python. Una de las características más importantes de Streamlit es su capacidad para crear gráficos interactivos.

[https://docs.streamlit.io/library/api-reference/charts](https://docs.streamlit.io/library/api-reference/charts)

### st.line_chart

```python 

import streamlit as st
import pandas as pd

# Creamos un DataFrame de ejemplo con información de vehículos
vehiculos_data = {
    'Modelo': ['Ford', 'Toyota', 'Honda', 'Chevrolet', 'Nissan', 'Kia'],
    'Ventas 2020': [100000, 90000, 80000, 70000, 60000, 50000],
    'Ventas 2021': [120000, 95000, 85000, 75000, 65000, 55000]
}
vehiculos_df = pd.DataFrame(vehiculos_data)

# Establecemos la columna 'Modelo' como índice del DataFrame
vehiculos_df.set_index('Modelo', inplace=True)

# Creamos un gráfico de línea con las ventas de los vehículos por año
st.line_chart(vehiculos_df[['Ventas 2020', 'Ventas 2021']])
```

### st.area_chart

```python 
import streamlit as st
import pandas as pd
import numpy as np

# Crear el DataFrame con los ingresos de tres tiendas en cuatro trimestres
data = {
    'Tienda': ['Tienda 1', 'Tienda 1', 'Tienda 1', 'Tienda 1', 'Tienda 2', 'Tienda 2', 'Tienda 2', 'Tienda 2', 'Tienda 3', 'Tienda 3', 'Tienda 3', 'Tienda 3'],
    'Trimestre': ['Q1', 'Q2', 'Q3', 'Q4', 'Q1', 'Q2', 'Q3', 'Q4', 'Q1', 'Q2', 'Q3', 'Q4'],
    'Ingresos': [100, 120, 110, 130, 80, 190, 100, 110, 270, 80, 85, 90]
}

df = pd.DataFrame(data)

# Mostrar el DataFrame
st.write(df)

# Graficar el DataFrame con un gráfico de área
df_pivot = df.pivot(index='Tienda', columns='Trimestre', values='Ingresos')
st.area_chart(df_pivot)
```

### st.bar_chart

```python 

import streamlit as st
import pandas as pd

# Crear el DataFrame con la cantidad de animales por tipo
data = {
    'Tipo': ['Perro', 'Gato', 'Pájaro', 'Conejo', 'Hamster'],
    'Cantidad': [50, 30, 20, 10, 5]
}

df = pd.DataFrame(data)

# Mostrar el DataFrame
st.write(df)

# Graficar el DataFrame con un gráfico de barras
st.bar_chart(df.set_index('Tipo'))
```

### st.pyplot

```python 
import streamlit as st 
import matplotlib.pyplot as plt
import numpy as np

# Datos de insectos
mosca = 100
hormiga = 50 
mariposa = 20
escarabajo = 30

# Categorías de insectos
insectos = ['Moscas', 'Hormigas', 'Mariposas', 'Escarabajos']

# Frecuencia de insectos
frecuencias = [mosca, hormiga, mariposa, escarabajo]

# Crear el gráfico 
fig = plt.figure(figsize=(8,4))
ax = fig.add_subplot(111)  
ax.bar(insectos, frecuencias)

# Mostrar el gráfico  
st.pyplot(fig)
```

### st.altair_chart

```python 

import streamlit as st
import altair as alt
import pandas as pd

# Sport popularity data
sports = ['Football', 'Basketball', 'Baseball', 'Tennis']
popularity = [300, 150, 100, 50]

# Create DataFrame
data = pd.DataFrame({
    'sport': sports,
    'popularity': popularity
})

# Create chart
c = alt.Chart(data).mark_circle().encode(
    x='sport',
    y='popularity',
    size='popularity'
)

st.altair_chart(c, use_container_width=True)
```

### st.vega_lite_chart

```python 
import streamlit as st
import pandas as pd

datos_peces = pd.DataFrame({
    'Especie': ['Trucha', 'Salmón', 'Bacalao', 'Atún', 'Sardina'],
    'Longitud (cm)': [30, 45, 60, 75, 20],
    'Peso (kg)': [2.5, 3.2, 4.8, 6.1, 0.5]
})

st.vega_lite_chart(datos_peces, {
    'mark': {'type': 'circle', 'tooltip': True},
    'encoding': {
        'x': {'field': 'Longitud (cm)', 'type': 'quantitative'},
        'y': {'field': 'Peso (kg)', 'type': 'quantitative'},
        'size': {'field': 'Longitud (cm)', 'type': 'quantitative'},
        'color': {'field': 'Especie', 'type': 'nominal'},
    },
})
```

## Librerias graficos en Streamlit

### Matplotlib

- [https://matplotlib.org/](https://matplotlib.org/)
- [https://docs.streamlit.io/library/api-reference/charts/st.pyplot](https://docs.streamlit.io/library/api-reference/charts/st.pyplot)

### Vega-Altair

- [https://altair-viz.github.io/index.html](https://altair-viz.github.io/index.html)
- [https://docs.streamlit.io/library/api-reference/charts/st.altair_chart](https://docs.streamlit.io/library/api-reference/charts/st.altair_chart)
  
### Vega-Lite

- [https://vega.github.io/](https://vega.github.io/)
- [https://docs.streamlit.io/library/api-reference/charts/st.vega_lite_chart](https://docs.streamlit.io/library/api-reference/charts/st.vega_lite_chart)
  
### Plotly 

- [https://plotly.com/python/](https://plotly.com/python/)
- [https://docs.streamlit.io/library/api-reference/charts/st.plotly_chart](https://docs.streamlit.io/library/api-reference/charts/st.plotly_chart)
  
### Bokeh 

- [https://docs.bokeh.org/en/latest/](https://docs.bokeh.org/en/latest/)
- [https://docs.streamlit.io/library/api-reference/charts/st.bokeh_chart](https://docs.streamlit.io/library/api-reference/charts/st.bokeh_chart)
  




## Gráficos Seaborn

Seaborn es una biblioteca de visualización de datos de Python **basada en Matplotlib**, pero **diseñada para crear gráficos estadísticos atractivos y informativos de forma más fácil y rápida.** 

En otras palabras, Seaborn te permite:

* **Crear gráficos con diseños más elegantes y atractivos:** Seaborn ofrece una gama de paletas de colores armoniosas y estilos predeterminados que mejoran la estética de tus visualizaciones.
* **Visualizar relaciones entre variables:** Seaborn facilita la creación de gráficos que muestran la relación entre dos o más variables, como diagramas de dispersión, gráficos de violín y gráficos de caja.
* **Explorar y analizar datos de forma gráfica:** Seaborn ofrece herramientas para visualizar la distribución de datos, identificar valores atípicos y explorar patrones en conjuntos de datos complejos.
* **Crear gráficos personalizados:** Aunque Seaborn ofrece muchos estilos y configuraciones predefinidas, también permite personalizar los gráficos para que se adapten a tus necesidades específicas.

**Seaborn es una herramienta poderosa para la visualización de datos estadísticos que te ayuda a:**

* **Entender mejor tus datos.**
* **Comunicar tus hallazgos de manera efectiva.**
* **Crear gráficos visualmente atractivos y profesionales.**

**¿Por qué elegir Seaborn?**

* **Facilidad de uso:** Seaborn está diseñado para ser fácil de usar, incluso para usuarios que no son expertos en Python.
* **Calidad de los gráficos:** Seaborn produce gráficos de alta calidad que son atractivos y fáciles de entender.
* **Personalización:** Seaborn ofrece opciones de personalización para adaptar los gráficos a tus necesidades específicas.

**Algunos ejemplos de tipos de gráficos que puedes crear con Seaborn:**

* **Diagramas de dispersión:** para mostrar la relación entre dos variables numéricas.
* **Gráficos de violín:** para mostrar la distribución de una variable numérica para diferentes grupos.
* **Gráficos de caja:** para mostrar la distribución de una variable numérica para diferentes grupos.
* **Mapas de calor:** para visualizar la relación entre dos variables categóricas.
* **Diagramas de pares:** para visualizar la relación entre todas las parejas de variables en un conjunto de datos.
* **Y muchos más...**

**Si necesitas más información, puedes consultar la documentación oficial de Seaborn:** [https://seaborn.pydata.org/](https://seaborn.pydata.org/)

### Configuración Inicial

Primero, necesitamos instalar las bibliotecas necesarias:

```bash
pip install streamlit seaborn pandas matplotlib
```

Importaciones básicas para todos los ejemplos:

```python
import streamlit as st
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt
```

### Scatter Plot

El scatter plot es útil para visualizar relaciones entre dos variables continuas.

```python
import streamlit as st
import seaborn as sns
import matplotlib.pyplot as plt

# Cargar datos de ejemplo
df_tips = sns.load_dataset("tips")

# Crear la página
st.title("Scatter Plot con Seaborn")
st.write("Visualización de la relación entre cuenta total y propina")

# Crear el gráfico
fig, ax = plt.subplots(figsize=(10, 6))
sns.scatterplot(
    data=df_tips, 
    x="total_bill", 
    y="tip", 
    hue="time",  # Color según tiempo de comida
    size="size"  # Tamaño según número de personas
)
plt.title("Relación entre Cuenta Total y Propina")

# Mostrar el gráfico
st.pyplot(fig)
```

#### Características principales:
- `hue`: Agrega una tercera dimensión mediante colores
- `size`: Representa una cuarta dimensión mediante el tamaño de los puntos
- Útil para detectar patrones y correlaciones

### Box Plot

El box plot muestra la distribución de datos numéricos a través de cuartiles.

```python
import streamlit as st
import seaborn as sns
import matplotlib.pyplot as plt

# Cargar datos
df_tips = sns.load_dataset("tips")

st.title("Box Plot con Seaborn")
st.write("Distribución de propinas por día")

# Crear el gráfico
fig, ax = plt.subplots(figsize=(10, 6))
sns.boxplot(
    data=df_tips,
    x="day",
    y="tip",
    hue="time"  # Separar por tiempo de comida
)
plt.title("Distribución de Propinas por Día")

st.pyplot(fig)
```

#### Elementos del Box Plot:
- Línea central: mediana
- Caja: rango intercuartil (IQR)
- Bigotes: 1.5 * IQR
- Puntos: valores atípicos

### Violin Plot

El violin plot combina un box plot con un plot de densidad de kernel.

```python
import streamlit as st
import seaborn as sns
import matplotlib.pyplot as plt

# Cargar datos
df_iris = sns.load_dataset("iris")

st.title("Violin Plot con Seaborn")
st.write("Distribución de medidas de pétalos por especie")

# Crear el gráfico
fig, ax = plt.subplots(figsize=(10, 6))
sns.violinplot(
    data=df_iris,
    x="species",
    y="petal_length",
    inner="box"  # Mostrar box plot dentro del violin
)
plt.title("Distribución de Longitud de Pétalos por Especie")

st.pyplot(fig)
```

#### Ventajas:
- Muestra la distribución completa de los datos
- Permite ver la densidad en diferentes valores
- Útil para comparar distribuciones entre grupos

### Heat Map

El heatmap es excelente para visualizar matrices de correlación y datos tabulares.

```python
import streamlit as st
import seaborn as sns
import matplotlib.pyplot as plt

# Cargar datos
df_iris = sns.load_dataset("iris")

st.title("Heat Map con Seaborn")
st.write("Matriz de correlación del dataset iris")

# Seleccionar solo columnas numéricas
numeric_columns = df_iris.select_dtypes(include=['float64', 'int64']).columns

# Crear el gráfico
fig, ax = plt.subplots(figsize=(10, 8))
sns.heatmap(
    df_iris[numeric_columns].corr(),  # Solo usar columnas numéricas
    annot=True,     # Mostrar valores
    cmap='coolwarm', # Esquema de colores
    center=0        # Centrar el colormap en 0
)
plt.title("Matriz de Correlación - Dataset Iris")

st.pyplot(fig)
```

#### Opciones útiles:
- `annot`: Muestra valores numéricos
- `cmap`: Define el esquema de colores
- `center`: Define el punto central del colormap

### Pair Plot

El pair plot crea una matriz de gráficos que muestra relaciones entre múltiples variables.

```python
import streamlit as st
import seaborn as sns

# Cargar datos
df_iris = sns.load_dataset("iris")

st.title("Pair Plot con Seaborn")
st.write("Visualización de múltiples variables")

# Crear el gráfico
fig = sns.pairplot(
    df_iris,
    hue="species",    # Color por especie
    diag_kind="kde"   # Tipo de gráfico en la diagonal
)

st.pyplot(fig)
```

#### Características:
- Muestra scatter plots para cada par de variables
- Histogramas o KDE en la diagonal
- Útil para exploración inicial de datos


Te proporciono la estructura similar pero para un histograma:

### Histogram Plot

El histograma es útil para visualizar la distribución de una variable continua y detectar su forma, dispersión y valores atípicos.

```python
import streamlit as st
import seaborn as sns
import matplotlib.pyplot as plt

# Cargar datos de ejemplo
df_tips = sns.load_dataset("tips")

# Crear la página
st.title("Histogram Plot con Seaborn")
st.write("Visualización de la distribución de propinas")

# Crear el gráfico
fig, ax = plt.subplots(figsize=(10, 6))
sns.histplot(
    data=df_tips,
    x="tip",
    hue="time",     # Color según tiempo de comida
    multiple="stack",# Apilar los histogramas
    bins=20,        # Número de barras
    kde=True        # Agregar línea de densidad
)
plt.title("Distribución de Propinas por Tiempo de Comida")

# Mostrar el gráfico
st.pyplot(fig)
```

#### Características principales:
- `bins`: Define el número de barras en el histograma
- `kde`: Agrega una curva de estimación de densidad
- `multiple`: Controla cómo se muestran múltiples histogramas ("layer", "stack", "dodge")
- `stat`: Puede ser "count", "frequency", "density", "probability"

### Consejos Adicionales para Streamlit

1. **Configuración de la página:**
```python
st.set_page_config(
    page_title="Mi App de Visualización",
    layout="wide",
    initial_sidebar_state="expanded"
)
```

2. **Personalización de gráficos:**
```python
# Establecer el estilo de Seaborn
sns.set_style("whitegrid")
sns.set_palette("husl")
```

3. **Interactividad:**
```python
# Selector en sidebar
variable_x = st.sidebar.selectbox("Variable X", df.columns)
variable_y = st.sidebar.selectbox("Variable Y", df.columns)
```

4. **Caché para mejor rendimiento:**
```python
@st.cache_data
def load_data():
    return sns.load_dataset("tips")
```

## Interpretando y Entendiendo los Tipos de Gráficos

Los gráficos son herramientas visuales esenciales para comprender y comunicar información a partir de datos.  A continuación, se presenta una guía para interpretar y entender algunos de los tipos de gráficos más comunes:

### **Gráficos de Dispersión (Scatter Plots):**

* **Propósito:** Mostrar la relación entre dos variables numéricas.
* **Interpretación:** Cada punto en el gráfico representa una observación. La posición del punto en el eje horizontal (X) representa el valor de la primera variable, y la posición en el eje vertical (Y) representa el valor de la segunda variable.
    * **Patrones:** Observar si los puntos forman un patrón lineal, curvo o aleatorio.  Un patrón lineal sugiere una correlación entre las variables.
    * **Concentración:**  Verificar si los puntos están agrupados o dispersos. La concentración puede indicar la fuerza de la relación entre las variables.
    * **Valores Atípicos:** Identificar puntos que se alejan del patrón general.  Estos puntos pueden ser errores de datos o indicar observaciones inusuales.

### **Gráficos de Caja (Box Plots):**

* **Propósito:** Mostrar la distribución de una variable numérica para diferentes grupos.
* **Interpretación:**
    * **Caja:** La caja representa el rango intercuartil (IQR), que contiene el 50% central de los datos.
    * **Línea Central:** La línea dentro de la caja representa la mediana, el valor que divide los datos a la mitad.
    * **Bigotes:** Las líneas que se extienden desde la caja (bigotes) representan el rango de los datos, excluyendo los valores atípicos.
    * **Puntos Individuales:** Los puntos fuera de los bigotes representan valores atípicos, que son observaciones significativamente diferentes del resto de los datos.

### **Gráficos de Violín (Violin Plots):**

* **Propósito:** Mostrar la distribución de una variable numérica para diferentes grupos, combinando un gráfico de caja con un gráfico de densidad.
* **Interpretación:**
    * **Forma del Violín:** La forma del violín muestra la densidad de los datos. Una forma más ancha indica una mayor concentración de datos en ese rango de valores.
    * **Caja and Bigotes:**  Similar al gráfico de caja, la caja y los bigotes muestran la mediana, el rango intercuartil y los valores atípicos.

**Mapas de Calor (Heat Maps):**

* **Propósito:** Visualizar la relación entre dos variables categóricas o mostrar la intensidad de un valor en una matriz.
* **Interpretación:**
    * **Celdas:** Cada celda en el mapa de calor representa la intersección de dos categorías.
    * **Color:** El color de la celda indica la intensidad o valor asociado a esa combinación de categorías.
    * **Escala de Color:** La escala de color proporciona una referencia para interpretar los colores y la intensidad de los valores.

### **Diagramas de Pares (Pair Plots):**

* **Propósito:** Mostrar las relaciones entre todas las parejas de variables en un conjunto de datos.
* **Interpretación:**
    * **Matriz de Gráficos:** El diagrama de pares crea una matriz de gráficos, donde cada gráfico muestra la relación entre dos variables.
    * **Gráficos de Dispersión:** Los gráficos fuera de la diagonal son gráficos de dispersión que muestran la relación entre dos variables numéricas.
    * **Histogramas o KDE:** Los gráficos en la diagonal suelen ser histogramas o gráficos de densidad de kernel (KDE), que muestran la distribución de una sola variable.

Te proporciono la estructura similar para el histograma:

### **Gráficos de Histograma:**

* **Propósito:** Mostrar la distribución y frecuencia de una variable numérica.
* **Interpretación:** Cada barra representa un rango de valores (bin) y su altura indica la frecuencia o cantidad de observaciones en ese rango.
    * **Forma:** Observar si la distribución es simétrica, sesgada a la derecha/izquierda, unimodal, bimodal o multimodal.
    * **Dispersión:** Verificar qué tan extendidos están los datos y si hay concentraciones en ciertos rangos.
    * **Valores Atípicos:** Identificar barras aisladas en los extremos que pueden indicar valores inusuales o errores en los datos.


## Ejemplo Streamlit con graficos Seaborn

<Tabs>
   <TabItem value="datos_tecnologia_co.csv" label="datos_tecnologia_co.csv" default>
   ```csv        
   Región,Departamento,Municipio,Población,Hogares con acceso a internet,Penetración de internet (%),Uso de internet,Dispositivos móviles,Uso de teléfonos inteligentes (%),Acceso a computadores (%),Uso de redes sociales (%),Compras online (%),Nivel educativo,Edad promedio,Ingresos promedio
   Amazonía,Amazonas,Leticia,43000,10000,23,1.5,1.2,70,5,80,15,8,30,1000000
   Amazonía,Caquetá,Florencia,150000,30000,20,1,1,65,5,75,10,9,31,1200000
   Amazonía,Putumayo,Mocoa,50000,10000,20,1,1,60,5,70,10,8,29,1000000
   Amazonía,Vaupés,Mitú,30000,5000,17,1,1,50,2,55,5,6,28,800000
   Andina,Antioquia,Medellín,2500000,1200000,48,2.5,1.8,85,15,90,30,11,34,2000000
   Andina,Boyacá,Tunja,150000,50000,33,1.5,1.2,70,8,85,20,10,32,1300000
   Andina,Caldas,Manizales,400000,150000,38,2,1.5,75,12,88,25,10,33,1500000
   Andina,Cundinamarca,Bogotá,8000000,5000000,63,3,2.2,90,20,95,40,12,36,2500000
   Caribe,Atlántico,Barranquilla,1200000,600000,50,2,1.6,80,12,88,25,10,32,1600000
   Caribe,Bolívar,Cartagena,900000,400000,44,1.8,1.4,75,10,85,20,9,31,1300000
   Caribe,Cesar,Valledupar,400000,100000,25,1.2,1,60,5,75,15,8,30,1000000
   Caribe,Córdoba,Montería,450000,150000,33,1.5,1.2,65,8,80,18,9,31,1100000
   Insular,San Andrés,San Andrés,70000,40000,57,3,2,90,20,95,50,12,33,1800000
   Insular,Providencia,Providencia,5000,3000,60,3,2,85,15,90,40,11,32,1600000
   Orinoquía,Arauca,Arauca,70000,20000,29,1.2,1,60,5,70,10,8,29,900000
   Orinoquía,Casanare,Yopal,120000,30000,25,1,1,60,5,70,10,8,30,900000
   Orinoquía,Meta,Villavicencio,400000,100000,25,1.2,1,60,5,70,10,8,30,900000
   Pacífica,Cauca,Popayán,250000,80000,32,1,1,65,5,75,15,9,31,1100000
   Pacífica,Chocó,Quibdó,150000,40000,27,1,1,55,3,65,10,7,29,800000
   Pacífica,Nariño,Pasto,400000,120000,30,1.5,1.2,60,5,70,15,9,31,1000000
   Amazonía,Amazonas,Puerto Nariño,3000,500,17,1,1,45,2,50,5,6,27,700000
   Amazonía,Caquetá,San Vicente del Caguán,30000,5000,17,1,1,50,2,55,5,6,28,800000
   Amazonía,Putumayo,Puerto Asís,35000,7000,20,1,1,55,3,60,10,7,28,900000
   Amazonía,Vaupés,Caruru,2000,300,15,1,1,40,1,45,5,5,26,600000
   Andina,Antioquia,Envigado,200000,100000,50,2.5,1.8,80,12,88,25,10,33,1800000
   Andina,Boyacá,Chiquinquirá,50000,15000,30,1.2,1,65,5,75,15,9,31,1000000
   Andina,Caldas,Pereira,450000,180000,40,2,1.5,75,10,85,20,10,32,1600000
   Andina,Cundinamarca,Soacha,500000,250000,50,2,1.5,75,10,85,20,10,32,1500000
   Caribe,Atlántico,Sabanalarga,100000,40000,40,1.2,1,60,5,75,15,8,30,1000000
   Caribe,Bolívar,Magangué,100000,30000,30,1,1,55,3,65,10,8,29,900000
   Caribe,Cesar,Aguachica,80000,20000,25,1,1,55,3,65,10,7,28,800000
   Caribe,Córdoba,Sincelejo,250000,80000,32,1.2,1,60,5,70,15,8,30,900000
   Insular,San Andrés,Providencia,4000,2500,63,3,2,85,15,90,40,11,32,1500000
   Insular,Providencia,Santa Catalina,1000,600,60,2.5,2,80,12,88,35,10,31,1400000
   Orinoquía,Arauca,Tame,40000,10000,25,1,1,55,3,65,10,7,28,800000
   Orinoquía,Casanare,Paz de Ariporo,25000,6000,24,1,1,55,3,65,10,7,28,700000
   Orinoquía,Meta,Puerto López,40000,8000,20,1,1,50,2,55,5,6,27,700000
   Pacífica,Cauca,Santander de Quilichao,100000,30000,30,1,1,60,5,70,10,8,29,900000
   Pacífica,Chocó,Istmina,20000,4000,20,1,1,50,2,55,5,6,27,700000
   Pacífica,Nariño,Ipiales,70000,20000,29,1.2,1,60,5,70,10,8,29,900000
   Amazonía,Amazonas,Tarapacá,2000,250,13,1,1,40,1,45,5,5,26,500000
   Amazonía,Caquetá,Curillo,5000,800,16,1,1,45,2,50,5,6,27,600000
   Amazonía,Putumayo,Valle del Guamuez,20000,3000,15,1,1,45,2,50,5,6,27,600000
   Amazonía,Vaupés,Pacoa,1000,100,10,1,1,35,1,40,5,4,25,400000
   Andina,Antioquia,Rionegro,150000,40000,27,1.5,1.2,60,5,70,15,8,30,1000000
   Andina,Boyacá,Nobsa,5000,1000,20,1,1,50,2,55,5,6,27,700000
   Andina,Caldas,Marmato,10000,2000,20,1,1,50,2,55,5,6,27,700000
   Andina,Cundinamarca,La Calera,10000,4000,40,1.5,1.2,70,8,85,20,9,32,1200000
   Caribe,Atlántico,Luruaco,15000,3000,20,1,1,50,2,55,5,6,27,700000
   Caribe,Bolívar,San Pablo,15000,2000,13,1,1,45,2,50,5,5,26,600000
   Caribe,Cesar,El Copey,10000,1000,10,1,1,40,1,45,5,5,26,500000
   Caribe,Córdoba,Puerto Escondido,15000,2000,13,1,1,45,2,50,5,5,26,600000
   Insular,San Andrés,Serrana Bank,10,5,50,2,2,70,10,80,25,9,30,1200000
   Insular,Providencia,Quitasueño Bank,10,5,50,2,2,70,10,80,25,9,30,1200000
   Orinoquía,Arauca,Fortul,20000,3000,15,1,1,45,2,50,5,6,27,600000
   Orinoquía,Casanare,Hato Corozal,20000,3000,15,1,1,45,2,50,5,6,27,600000
   Orinoquía,Meta,Granada,40000,5000,13,1,1,40,1,45,5,5,26,500000
   Pacífica,Cauca,Bolivar,10000,1500,15,1,1,45,2,50,5,6,27,600000
   Pacífica,Chocó,Juradó,2000,300,15,1,1,40,1,45,5,5,26,500000
   Pacífica,Nariño,Samaniego,15000,2000,13,1,1,45,2,50,5,5,26,600000
   Amazonía,Amazonas,Puerto Alegría,500,50,10,1,1,35,1,40,5,4,25,400000
   Amazonía,Caquetá,Belén de los Andaquies,5000,500,10,1,1,40,1,45,5,5,26,500000
   Amazonía,Putumayo,Orito,10000,800,8,1,1,35,1,40,5,4,25,400000
   Amazonía,Vaupés,Taraira,200,20,10,1,1,30,1,35,3,4,24,300000
   Andina,Antioquia,Girardota,100000,25000,25,1.2,1,60,5,70,15,8,30,900000
   Andina,Boyacá,Santa Sofía,5000,800,16,1,1,45,2,50,5,6,27,600000
   Andina,Caldas,Salamina,40000,10000,25,1.2,1,60,5,70,15,8,30,800000
   Andina,Cundinamarca,Cajicá,50000,20000,40,1.5,1.2,70,8,85,20,9,32,1200000
   Caribe,Atlántico,Usiacurí,20000,3000,15,1,1,45,2,50,5,6,27,600000
   Caribe,Bolívar,San Juan Nepomuceno,30000,4000,13,1,1,40,1,45,5,5,26,500000
   Caribe,Cesar,La Jagua de Ibirico,20000,2000,10,1,1,40,1,45,5,5,26,500000
   Caribe,Córdoba,Montelíbano,50000,10000,20,1,1,50,2,55,5,6,27,700000
   Insular,San Andrés,Johnny Cay,50,5,100,2,2,70,10,80,25,9,30,1200000
   Insular,Providencia,Roncador Cay,10,5,50,2,2,70,10,80,25,9,30,1200000
   Orinoquía,Arauca,Arauquita,30000,4000,13,1,1,40,1,45,5,5,26,500000
   Orinoquía,Casanare,Tauramena,20000,3000,15,1,1,45,2,50,5,6,27,600000
   Orinoquía,Meta,San Martín,40000,5000,13,1,1,40,1,45,5,5,26,500000
   Pacífica,Cauca,Caloto,25000,2000,8,1,1,35,1,40,5,4,25,400000
   Pacífica,Chocó,Bahía Solano,5000,400,8,1,1,35,1,40,5,4,25,400000
   Pacífica,Nariño,La Unión,25000,3000,12,1,1,40,1,45,5,5,26,500000
   ``` 
   </TabItem>
   <TabItem value="app.py" label="app.py" >
   ```python
   import streamlit as st
   import pandas as pd
   import seaborn as sns
   import matplotlib.pyplot as plt

   # Cargar los datos del CSV
   df = pd.read_csv("static\datasets\datos_tecnologia_co.csv")

   # Título de la aplicación
   st.title("Análisis de Penetración de Internet en Colombia")

   # Menú lateral para seleccionar las variables
   st.sidebar.header("Opciones de visualización")
   region = st.sidebar.selectbox("Región", df["Región"].unique())
   variable_x = st.sidebar.selectbox("Variable X", df.columns[3:])
   variable_y = st.sidebar.selectbox("Variable Y", df.columns[3:])

   # Selector de tipo de gráfico
   chart_type = st.sidebar.selectbox(
      "Tipo de gráfico",
      ("Dispersión", "Histograma", "Boxplot", "Heatmap"),
   )

   # Filtrar los datos según la región seleccionada
   filtered_df = df[df["Región"] == region]

   # Crear el gráfico según el tipo seleccionado
   if chart_type == "Dispersión":
      fig, ax = plt.subplots(figsize=(10, 6))
      sns.scatterplot(
         x=variable_x, y=variable_y, data=filtered_df, hue="Departamento", ax=ax
      )
      ax.set_xlabel(variable_x)
      ax.set_ylabel(variable_y)
      ax.set_title(f"Relación entre {variable_x} y {variable_y} en {region}")
   elif chart_type == "Histograma":
      fig, ax = plt.subplots(figsize=(10, 6))
      sns.histplot(x=variable_x, data=filtered_df, hue="Departamento", ax=ax)
      ax.set_xlabel(variable_x)
      ax.set_title(f"Histograma de {variable_x} en {region}")
   elif chart_type == "Boxplot":
      fig, ax = plt.subplots(figsize=(10, 6))
      sns.boxplot(x="Departamento", y=variable_y, data=filtered_df, ax=ax)
      ax.set_ylabel(variable_y)
      ax.set_title(f"Boxplot de {variable_y} por Departamento en {region}")
   elif chart_type == "Heatmap":
      fig, ax = plt.subplots(figsize=(10, 6))
      # Seleccionar solo las columnas numéricas
      numeric_cols = filtered_df.select_dtypes(include=['number'])
      corr_matrix = numeric_cols.corr()
      sns.heatmap(corr_matrix, annot=True, cmap="coolwarm", ax=ax)
      ax.set_title(f"Correlación de variables en {region}")

   st.pyplot(fig)

   # Información de cómo interpretar cada gráfico
   st.subheader("Interpretación de los gráficos")

   if chart_type == "Dispersión":
      st.write(
         f"El gráfico de dispersión muestra la relación entre {variable_x} y "
         f"{variable_y} para cada departamento en la región {region}. Puedes "
         f"观察 general de la relación, si hay una "
         f"correlación positiva o negativa, y si hay algún punto atípico."
      )
   elif chart_type == "Histograma":
      st.write(
         f"El histograma muestra la distribución de {variable_x} para los "
         f"departamentos en la región {region}. Puedes observar la frecuencia "
         f"de cada valor de {variable_x} y la forma general de la "
         f"distribución (si es normal, sesgada, etc.)."
      )
   elif chart_type == "Boxplot":
      st.write(
         f"El boxplot muestra la distribución de {variable_y} para cada "
         f"departamento en la región {region}. Puedes observar la mediana, "
         f"los cuartiles, los valores atípicos y la dispersión de los datos "
         f"para cada departamento."
      )
   elif chart_type == "Heatmap":
      st.write(
         f"El mapa de calor muestra la correlación entre las variables "
         f"numéricas en la región {region}. Un color más rojo indica una "
         f"correlación positiva más fuerte, mientras que un color más azul "
         f"indica una correlación negativa más fuerte. Una correlación "
         f"cercana a 1 indica una fuerte correlación positiva, una "
         f"correlación cercana a -1 indica una fuerte correlación "
         f"negativa, y una correlación cercana a 0 indica que no hay "
         f"correlación."
      )

   # Mostrar tabla de datos
   st.subheader("Tabla de datos")
   st.dataframe(filtered_df)

   # Descripción de las variables
   st.subheader("Descripción de las variables")
   st.write("""
      * **Región:** Región geográfica de Colombia.
      * **Departamento:** Departamento de Colombia.
      * **Municipio:** Municipio de Colombia.
      * **Población:** Población total del municipio.
      * **Hogares con acceso a internet:** Número de hogares con acceso a internet.
      * **Penetración de internet (%):** Porcentaje de hogares con acceso a internet.
      * **Uso de internet:** Frecuencia de uso de internet.
      * **Dispositivos móviles:** Número de dispositivos móviles por hogar.
      * **Uso de teléfonos inteligentes (%):** Porcentaje de hogares que usan teléfonos inteligentes.
      * **Acceso a computadores (%):** Porcentaje de hogares con acceso a computadores.
      * **Uso de redes sociales (%):** Porcentaje de hogares que usan redes sociales.
      * **Compras online (%):** Porcentaje de hogares que realizan compras online.
      * **Nivel educativo:** Nivel educativo promedio de la población.
      * **Edad promedio:** Edad promedio de la población.
      * **Ingresos promedio:** Ingresos promedio de la población.
   """)

   # Añadir información adicional
   st.subheader("Información adicional")
   st.write("""
      * Los datos se basan en una encuesta realizada en 2023.
      * La penetración de internet se refiere al porcentaje de hogares con acceso a internet.
      * El uso de internet se refiere a la frecuencia de uso de internet por parte de los hogares.
   """)
   ``` 
   </TabItem>  
</Tabs>
