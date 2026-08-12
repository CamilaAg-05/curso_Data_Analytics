# Análisis de ventas del restaurante

## Objetivo

Analizar los registros de ventas del restaurante para identificar el comportamiento de los productos, comparar el desempeño entre las semanas, conocer la recurrencia de los clientes y observar qué perfiles de clientes generan mayores ingresos.

## Datos utilizados

| Archivo                           | Contenido                                      |
| --------------------------------- | ---------------------------------------------- |
| `data/Restaurant-Foods.csv`       | Catálogo de productos y precios (10 ítems).    |
| `data/Restaurant-Customers.csv`   | Información de clientes (ID, ocupación, etc.). |
| `data/Restaurant-Week1-Sales.csv` | 250 registros de venta de la Semana 1.         |
| `data/Restaurant-Week2-Sales.csv` | 250 registros de venta de la Semana 2.         |

En total se analizaron 500 registros de venta correspondientes a las dos semanas.

No se publican nombres de clientes ni información que permita identificarlos.

## Instrucciones

1. Cargar los archivos de datos en Google Colab.
2. Importar las librerías necesarias para realizar el análisis.
3. Revisar y preparar los datos antes de realizar las uniones.
4. Unir la información de ventas con los datos de productos y clientes.
5. Analizar los productos según su frecuencia de compra e ingresos generados.
6. Comparar los resultados de la semana 1 y la semana 2.
7. Calcular la tasa de recurrencia de los clientes.
8. Analizar los ingresos agrupados por ocupación.
9. Realizar visualizaciones para facilitar la interpretación de los resultados.
10. No mostrar nombres de clientes en las tablas, gráficos o resultados publicados.

## Hallazgos

### Desempeño del menú

El producto que más compran los clientes es el Drink. Sin embargo, teniendo en cuenta que muchas personas compran una bebida para acompañar su comida, también se puede destacar que, entre los productos de comida, el Burrito es el que tiene mayor frecuencia de compra.

Por otro lado, el Steak es el producto que genera más ingresos para el restaurante. Esto demuestra que el producto que más se vende no necesariamente es el que genera más ingresos.

El producto que presenta el peor desempeño es la Pizza, ya que tiene una menor frecuencia de compra y genera menos ingresos en comparación con los demás productos.

### Comparación semanal

Las dos semanas tuvieron la misma cantidad de registros de venta, con 250 registros cada una.

Los ingresos disminuyeron de 1962.68 en la semana 1 a 1923.88 en la semana 2. Esto representa una reducción de 38.80.

También disminuyó el ingreso promedio por registro, pasando de 7.85072 en la semana 1 a 7.69552 en la semana 2.

En general, la semana 2 tuvo la misma cantidad de ventas, pero generó un poco menos de ingresos.

### Recurrencia

La tasa de recurrencia fue de 20.8%. En la semana 1 hubo 221 clientes únicos, de los cuales 46 también realizaron una compra durante la segunda semana.

Esto muestra que una parte de los clientes regresó al restaurante, aunque la mayoría de los clientes de la primera semana no volvieron a aparecer en la segunda.

### Perfil agregado

Las ocupaciones que concentraron mayores ingresos fueron:

* Compensation Analyst
* Sales Representative
* Marketing Manager
* Cost Accountant
* Assistant Media Planner

Estos datos permiten identificar los grupos de clientes que generaron mayores ingresos durante el periodo analizado.

### Limitaciones de los datos

Una de las principales limitaciones es que solo se están analizando dos semanas. Sería mejor contar con un periodo de tiempo más largo para conocer mejor el comportamiento de las ventas y saber si los resultados se mantienen.

También sería importante saber si durante esas semanas se realizaron descuentos o promociones en algunos productos, ya que esto podría haber influido en las ventas.

Otra limitación es que los datos no permiten conocer las razones por las que un producto se vende más que otro. Para analizar esto sería necesario contar con información adicional sobre las preferencias de los clientes.
