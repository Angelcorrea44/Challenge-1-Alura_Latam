# AluraStoreLatam - Análisis de Tiendas

Este proyecto analiza el desempeño de cuatro tiendas de la empresa Alura Store Latam, con el objetivo de identificar cuál de ellas representa el menor beneficio y recomendarla como candidata a ser vendida. El análisis se realiza utilizando Python y la biblioteca pandas, y se complementa con visualizaciones generadas con matplotlib.

---

## Tabla de Contenidos

- [Descripción del Proyecto](#descripción-del-proyecto)
- [Estructura del Notebook](#estructura-del-notebook)
- [Requisitos](#requisitos)
- [Explicación Paso a Paso](#explicación-paso-a-paso)
    - [1. Importación de datos](#1-importación-de-datos)
    - [2. Análisis de facturación](#2-análisis-de-facturación)
    - [3. Ventas por categoría](#3-ventas-por-categoría)
    - [4. Calificación promedio de la tienda](#4-calificación-promedio-de-la-tienda)
    - [5. Productos más y menos vendidos](#5-productos-más-y-menos-vendidos)
    - [6. Envío promedio por tienda](#6-envío-promedio-por-tienda)
    - [7. Visualizaciones](#7-visualizaciones)
    - [8. Informe Final y Conclusión](#8-informe-final-y-conclusión)
- [Notas adicionales](#notas-adicionales)

---

## Descripción del Proyecto

El objetivo es analizar los datos de ventas, calificaciones, categorías de productos y costos de envío de cuatro tiendas, para determinar cuál de ellas es la menos rentable y, por tanto, la mejor candidata para ser vendida. El análisis se realiza de manera comparativa y se apoya en visualizaciones para facilitar la interpretación de los resultados.

---

## Estructura del Notebook

El notebook está organizado en secciones numeradas, cada una abordando un aspecto específico del análisis:

1. **Importación de datos**
2. **Análisis de facturación**
3. **Ventas por categoría**
4. **Calificación promedio de la tienda**
5. **Productos más y menos vendidos**
6. **Envío promedio por tienda**
7. **Visualizaciones**
8. **Informe Final y Conclusión**

---

## Requisitos

- Python 3.8+
- pandas
- matplotlib

Instala los requisitos con:

```bash
pip install pandas matplotlib
```

---

## Explicación Paso a Paso

### 1. Importación de datos

Se importan las bibliotecas necesarias (`pandas` y `matplotlib.pyplot`) y se cargan los datos de las cuatro tiendas desde archivos CSV alojados en GitHub. Cada tienda se almacena en un DataFrame independiente (`tienda`, `tienda2`, `tienda3`, `tienda4`).

```python
import pandas as pd

# URLs de los archivos CSV
url = "..."
# ... (urls de las otras tiendas)

# Carga de datos
tienda = pd.read_csv(url)
# ... (carga de las otras tiendas)
```

---

### 2. Análisis de facturación

Se calcula el ingreso total de cada tienda sumando la columna `Precio`. Los resultados se imprimen para comparar rápidamente el desempeño de cada tienda.

```python
ingreso_tienda1 = tienda['Precio'].sum()
# ... (para las otras tiendas)
print(f'Ingreso total Tienda 1: ${ingreso_tienda1:,.2f}')
```

---

### 3. Ventas por categoría

Se analiza la distribución de ventas por categoría de producto usando `value_counts()` sobre la columna `Categoría del Producto` de cada tienda. Esto permite identificar las categorías más populares en cada tienda.

```python
ventas_categoria_tienda1 = tienda['Categoría del Producto'].value_counts()
# ... (para las otras tiendas)
```

---

### 4. Calificación promedio de la tienda

Se calcula la calificación promedio de cada tienda usando la columna `Calificación`. Esto ayuda a evaluar la satisfacción de los clientes en cada tienda.

```python
calificacion_promedio_tienda1 = tienda['Calificación'].mean()
# ... (para las otras tiendas)
```

---

### 5. Productos más y menos vendidos

Se identifican los productos más y menos vendidos en cada tienda utilizando `value_counts()` sobre la columna `Producto`. Se imprime el nombre y la cantidad de ventas de cada uno.

```python
ventas_productos_tienda1 = tienda['Producto'].value_counts()
mas_vendido_tienda1 = ventas_productos_tienda1.idxmax()
menos_vendido_tienda1 = ventas_productos_tienda1.idxmin()
```

---

### 6. Envío promedio por tienda

Se calcula el costo de envío promedio de cada tienda usando la columna `Costo de envío`. Esto permite comparar la eficiencia logística entre tiendas.

```python
envio_promedio_tienda1 = tienda['Costo de envío'].mean()
# ... (para las otras tiendas)
```

---

### 7. Visualizaciones

Se generan varias gráficas para facilitar la interpretación de los datos:

- **Gráfico de barras de ingresos totales por tienda:** Compara visualmente los ingresos de cada tienda.
- **Gráfico de pastel de ventas por categoría (Tienda 1):** Muestra la proporción de ventas por categoría.
- **Gráfico de líneas de calificación promedio por tienda:** Permite comparar la satisfacción de los clientes.
- **Gráfico de barras de costos promedios de envío:** Compara el costo logístico entre tiendas.

Ejemplo de la gráfica de costos de envío:

```python
import matplotlib.pyplot as plt

costos_envio = [
    envio_promedio_tienda1,
    envio_promedio_tienda2,
    envio_promedio_tienda3,
    envio_promedio_tienda4
]
nombres_tiendas = ['Tienda 1', 'Tienda 2', 'Tienda 3', 'Tienda 4']

plt.figure(figsize=(8,5))
plt.bar(nombres_tiendas, costos_envio, color='orange')
plt.title('Costo de envío promedio por tienda')
plt.ylabel('Costo de envío promedio ($)')
plt.xlabel('Tienda')
plt.show()
```

---

### 8. Informe Final y Conclusión

Se presenta un resumen ejecutivo con los principales hallazgos del análisis, incluyendo:

- Ingresos totales por tienda
- Calificaciones promedio
- Costos de envío promedio
- Ventas por categoría
- Productos más y menos vendidos

Finalmente, se recomienda la tienda menos rentable como candidata para la venta, justificando la decisión con base en los datos analizados.

---

## Notas adicionales

- El análisis es reproducible y puede adaptarse fácilmente a nuevos datos.
- Las visualizaciones pueden personalizarse según las necesidades del usuario.
- El notebook está diseñado para ser claro y didáctico, facilitando su comprensión incluso para usuarios sin experiencia previa en análisis de datos.

---

¿Dudas o sugerencias? ¡No dudes en abrir un issue o contactarme!
