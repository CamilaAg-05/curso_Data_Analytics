# Laboratorio SECOP - Expediente 1A: ¿Vale la pena contratar con el Estado?

## Integrantes del equipo 
- Camila Alejandra Aguado Urrego
- Vanesa Tatiana Caminos Boyaca
- Samuel Felipe Bustos Munca 

## Presentación del Caso 
**Expediente asignado:** A — *¿Vale la pena contratar con el Estado?*
**Recorte asignado:** Vigencia 2024-2025 · Territorio: Distrito Capital de Bogotá

### Afirmación objeto de verificación

> Para un profesional que comienza su vida laboral, la contratación por prestación de servicios con el Estado puede ser una alternativa económicamente atractiva.

## Criterio previo del equipo

**¿Qué entenderemos por "económicamente atractiva"?**

**Dimensiones a tener en cuenta:**

1. **Valor mensual equivalente estimado** — cuánto representa el contrato por mes, y si esto varía mucho entre contratos o es parecido para la mayoría.
2. **Duración contractual** — qué tan largos son los contratos, como una forma de ver si el ingreso sería estable o se interrumpiría seguido.
3. **Punto de comparación** — para saber si un valor mensual es "bueno" o no, lo compararemos con una referencia conocida (por ejemplo, el salario mínimo vigente en Colombia), en vez de mirar el número solo.

**Evidencia que consideraríamos A FAVOR:**
- La mayoría de los contratos (no solo el promedio) tienen un valor mensual por encima del salario mínimo y parecido o mejor a lo que ganaría un profesional junior en un empleo formal en Bogotá.
- Los contratos duran, en general, varios meses o más.
- No hay muchos casos con valores mensuales muy bajos que arrastren el resultado hacia abajo.

**Evidencia que consideraríamos EN CONTRA:**
- La mayoría de los contratos tienen un valor mensual bajo, cercano o por debajo del salario mínimo.
- Los contratos duran poco tiempo (pocos meses), lo que significaría ingresos que se cortan seguido.
- Hay un grupo importante de contratos con valores mensuales muy bajos, aunque el promedio general se vea razonable.


## Preparación de los datos

El recorte final trabajado en el notebook (`secop_recorte.csv`) contiene **50,000 filas y 85 columnas**.

De las 85 columnas disponibles, el análisis se concentró en un subconjunto reducido: `id_contrato`, `nombre_entidad`, `ciudad`, `proveedor_adjudicado`, `documento_proveedor`, `tipo_de_contrato`, `modalidad_de_contratacion`, `valor_del_contrato`, `fecha_de_firma`, `fecha_de_inicio_del_contrato`, `fecha_de_fin_del_contrato`, y dos variables derivadas calculadas en el notebook: `duracion_dias` (fecha de fin menos fecha de inicio) y `valor_mensual_equivalente` (valor del contrato dividido entre la duración aproximada en meses).

##  Qué se hizo en el notebook 

**Carga y preparación inicial.** Se cargó el archivo `data/secop_recorte.csv`, que contiene **50,000 filas y 85 columnas**. A partir de las columnas originales se construyeron dos variables nuevas necesarias para el análisis: `duracion_dias` (fecha de fin menos fecha de inicio del contrato) y `valor_mensual_equivalente` (valor del contrato dividido entre la duración aproximada en meses).

**Descripción del valor de los contratos.** Se calcularon la media, la mediana y los percentiles de `valor_del_contrato`, junto con un histograma de la distribución. Se encontró que la media ($74.606.090) es casi el doble de la mediana ($33.475.980), lo que indica que unos pocos contratos con valores muy altos (hasta $161.290.800.000) inflan el promedio. Por eso se usa la mediana, y no la media, para describir un contrato típico del recorte.

**Revisión de calidad de los datos.** Se revisaron los faltantes, duplicados y valores atípicos de las columnas principales. Se encontraron: 0 contratos duplicados, 88 contratos con valor $0, 2.804 posibles valores extremos 

**Comprobación** Antes de decidir qué hacer con los ceros o los valores extremos, se comparó la mediana bajo tres tratamientos distintos (con ceros, solo positivos, y positivos sin el 1% superior). La diferencia entre los tres resultó mínima, lo que respaldó la decisión de no eliminar esos casos del análisis principal.

**Valor mensual equivalente** Se calculó el resumen estadístico de `valor_del_contrato`, `duracion_dias` y `valor_mensual_equivalente` juntos, filtrando solo los contratos con valor y duración positivos (49.765 de los 50.000 originales). La mediana del valor mensual equivalente resultó en $5.341.131/mes, mucho más moderada que la media ($12.066.342/mes)

**Exploración adicional del caso más extremo** Se identificaron los contratos en el percentil 99 de valor mensual equivalente y se graficó su duración: la mayoría (cerca de 155 casos) dura entre 0 y 2 meses, lo que explica por qué su valor mensual sale tan alto 

**Patrones de fecha.** Se graficó en qué mes del año inician y se firman los contratos del recorte. En ambos casos se encontró una fuerte concentración en enero y febrero, coherente con el ciclo de renovación de contratos al iniciar el año fiscal.

**Revisión de los contratos en $0.** Se graficó en qué entidades se concentran los 88 contratos con valor $0, para verificar si son un patrón puntual de alguna entidad o casos dispersos.

**Se incorporó una objeción al análisis inicial**: un contrato con un valor total alto puede parecer más atractivo simplemente porque tiene una duración mayor. Para comprobarlo, se comparó la relación entre `valor_del_contrato` y `duracion_dias` y posteriormente se utilizó `valor_mensual_equivalente` como una medida normalizada para comparar contratos con diferentes duraciones.

**Relación entre valor total y duración.** Se calculó la correlación de Spearman entre `valor_del_contrato` y `duracion_dias`, obteniendo un valor de **0,711**, lo que muestra una relación positiva considerable entre ambas variables. Sin embargo, al dividir los contratos en cuatro grupos según su duración, la mediana del valor total se mantuvo relativamente estable, entre aproximadamente **$5,04 millones y $5,57 millones**. Esto muestra que una mayor duración no implica necesariamente un aumento proporcional del valor mediano del contrato.

**Valor mensual equivalente y duración.** Se utilizó `valor_mensual_equivalente` para comparar contratos de distinta duración bajo una misma unidad de tiempo. La mediana global fue de aproximadamente **$5,34 millones por mes**, mientras que la media fue de aproximadamente **$12,07 millones por mes**, nuevamente afectada por valores extremos. La comparación mostró que la mediana del valor mensual se mantiene relativamente estable en los contratos de distintas duraciones. Los contratos muy cortos pueden presentar valores mensuales equivalentes mucho más altos porque el valor total se divide entre pocos días o meses.

**Análisis de valores extremos del valor mensual.** Se identificaron los contratos ubicados en el percentil 99 del `valor_mensual_equivalente` y se analizó su duración. Cerca de **155 contratos** de este grupo tienen una duración entre **0 y 2 meses**, mientras que los contratos de mayor duración son poco frecuentes. Esto ayuda a explicar algunos de los valores mensuales extremadamente altos observados en el análisis: no necesariamente representan contratos completos de valor excepcional, sino que el cálculo mensual puede aumentar considerablemente cuando el valor contractual se distribuye sobre un periodo muy corto.

**Comparación visual de duración y valor mensual.** Se realizó una visualización general y un zoom de los contratos con duración de hasta 36 meses y valores mensuales hasta el percentil 99. La mayoría de los contratos se concentra entre **1 y 12 meses** y alrededor de **$5 millones mensuales**. La mediana por duración permanece relativamente cercana a la mediana global, por lo que no se observa que los contratos más largos tengan sistemáticamente un mayor valor mensual equivalente.

**Modalidad de contratación.** Se analizó la cantidad de contratos según `modalidad_de_contratacion`. La **Contratación Directa** concentra la mayoría de los registros del recorte, seguida por **Contratación régimen especial**, mientras que las demás modalidades presentan una participación considerablemente menor. Esto indica que el comportamiento general del conjunto está fuertemente condicionado por estas dos modalidades.

**Concentración alrededor de $5 millones por entidad.** Se analizó el porcentaje de contratos de cada entidad cuyo `valor_mensual_equivalente` se encuentra entre **$4,5 y $5,5 millones**. Algunas entidades presentan más del **50 %** de sus contratos dentro de este rango y la entidad con mayor concentración se acerca al **80 %**. Esto evidencia una concentración importante alrededor de ese nivel para determinadas entidades, aunque no permite afirmar por sí sola que exista un tope institucional de $5 millones.

**Variables de confusión identificadas.** La comparación de la segunda semana permitió identificar variables que no están suficientemente representadas en el dataset y que pueden afectar la interpretación de la relación entre duración y valor. Entre ellas se encuentran la **dedicación horaria**, el **nivel de cualificación o perfil profesional**, la **complejidad del objeto contractual**, los **topes presupuestales o límites administrativos** y el **tipo de contratista (persona natural o jurídica)**. Estas variables podrían explicar parte de las diferencias observadas entre contratos.

**Limitación causal.** El análisis es observacional y utiliza contratos históricos, por lo que no permite afirmar que una mayor duración cause un menor o mayor valor mensual equivalente. La ausencia de variables como horas de dedicación, perfil profesional y características detalladas del servicio limita la posibilidad de controlar variables de confusión. Por esta razón, los resultados deben interpretarse como asociaciones y patrones presentes en el recorte, no como efectos causales.




