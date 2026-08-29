# Data Analytics Lab 2

## Objetivo

Un conglomerado de 150 empresas está alarmado por el aumento sostenido en los reportes de accidentes laborales. El costo de las incapacidades y el impacto humano asociado están afectando la productividad global del conglomerado. Ante esta situación, la gerencia no solo necesita saber cuántos accidentes ocurren, sino comprender por qué ocurren: identificar qué condiciones (jornada, capacitación, sector, antigüedad, entre otras) están asociadas a un mayor riesgo de accidentalidad.

El objetivo de este laboratorio es aplicar la metodología CRISP-DM (Cross Industry Standard Process for Data Mining) para abordar este problema de negocio de forma estructurada. En términos concretos, el análisis busca:

- **Comprensión y preparación de los datos:** consolidar tres fuentes de datos dispersas (trabajadores, empresas y accidentes), que por sí solas no permiten responder la pregunta de negocio, en un único conjunto de datos analizable.
- **Modelado descriptivo:** generar evidencia visual (gráficos de barras, conteos, tasas porcentuales) que muestre cómo varía la accidentalidad según distintos factores de riesgo: jornada laboral, capacitación, sector económico, antigüedad, nivel educativo, sistema de gestión de seguridad y salud en el trabajo (SG-SST), tipo de lesión y tipo de empresa.
- **Evaluación e interpretación:** a partir de los patrones observados, identificar los factores que más se asocian con la ocurrencia de accidentes, distinguiendo entre relaciones que representan un riesgo real y aquellas que pueden deberse a grupos con muy pocos datos (por ejemplo, categorías con un solo trabajador).
- **Despliegue (en términos de negocio):** traducir los hallazgos en reglas de negocio y recomendaciones concretas de prevención que la gerencia pueda implementar, como capacitación obligatoria de ingreso o auditorías de seguridad en los sectores más críticos.

En síntesis, el rol del analista en este ejercicio es transformar datos operativos dispersos en evidencia accionable que respalde una estrategia de prevención de accidentes laborales.

## Datos

El análisis parte de tres fuentes de datos independientes, que deben integrarse para poder relacionar las características de los trabajadores y las empresas con la ocurrencia de accidentes.

| Archivo | detalle | Contenido principal |
|---|---|---|
| `trabajadores.csv` | Un registro por trabajador | Variables como jornada laboral, si está capacitado, antigüedad en la empresa, nivel educativo, edad, y la empresa a la que pertenece. |
| `empresas.csv` | Un registro por empresa (150 en total) | Sector económico, tipo de empresa (pública o privada), y si cuenta con un sistema de gestión de seguridad y salud en el trabajo (SG-SST) implementado. |
| `accidentes.csv` | Un registro por accidente reportado | Identificador del trabajador accidentado y el tipo de lesión sufrida (fractura, lesión múltiple, entre otras). |

**Dimensiones generales del conjunto de datos:**
- 3.000 trabajadores.
- 150 empresas.
- 1.067 registros de accidentes laborales (un trabajador puede tener uno o más accidentes registrados, o ninguno).

**Proceso de consolidación (integración de datos):**
1. Se unen `trabajadores.csv` y `empresas.csv` a través del identificador de empresa, de modo que cada trabajador queda asociado a las características de la empresa donde labora (sector, tipo de empresa, SG-SST).
2. Al resultado anterior se une `accidentes.csv` mediante un left join sobre el identificador del trabajador. 


**Consideraciones de privacidad:** el análisis se realiza siempre de forma agregada, por grupos (por ejemplo, por jornada, sector o rango de antigüedad) y no se publican ni se hace referencia a nombres de trabajadores ni de empresas específicas del conglomerado.

## Instrucciones

Para reproducir el análisis paso a paso:

* Colocar los archivos `trabajadores.csv`, `empresas.csv` y `accidentes.csv` en la misma carpeta donde se encuentra el notebook
2. Instalar las dependencias 
3. Ejecutar el notebook en orden secuencial
   
4. unión de trabajadores, empresas y accidentes en un único dataframe (`df_final`), y creación de la variable `incidente`.
 5. Revisión general de los datos
6. - **Visualización de evidencia inicial:** tasas de accidentalidad según jornada laboral, si el trabajador está capacitado o no, y los sectores económicos con mayor riesgo.
   - análisis adicionales propuestos sobre antigüedad, nivel educativo, sistema de gestión de SST, tipo de lesión y tipo de empresa

   - **Análisis general, conclusiones y recomendaciones:** se sintetizan los hallazgos y se proponen acciones de prevención.


## Hallazgos

A continuación se detallan los hallazgos obtenidos 

- **Jornada y capacitación (evidencia inicial):** los turnos nocturnos y mixtos muestran tasas de accidentalidad más altas que la jornada diurna. Este efecto se agrava cuando se combina con falta de capacitación: los trabajadores que además no han completado su capacitación presentan una condición de mayor vulnerabilidad. Esto se interpreta como resultado combinado de fatiga asociada a horarios nocturnos, menor disponibilidad de supervisión en esos turnos y falta de preparación para ejecutar ciertas tareas de forma segura.

- **Sector económico:** al identificar los cinco sectores con mayor tasa de accidentalidad, se evidencia que el riesgo no se distribuye de forma uniforme entre sectores, sino que se concentra en algunos de ellos, lo que respalda priorizar esfuerzos de prevención de forma diferenciada por sector (por ejemplo, construcción y minería, señalados en las recomendaciones).

- **Antigüedad en la empresa:** no se observa una tendencia lineal clara, es decir, el riesgo no aumenta ni disminuye de manera constante y proporcional a los años de vinculación. No obstante, sí se identifican patrones relevantes:
  - Los trabajadores con 1 año de antigüedad presentan la tasa más alta entre los grupos con un número representativo de trabajadores, cercana al 45,5 por ciento.
  - También se observan tasas elevadas en 5 años (40,4 por ciento), 15 años (40,3 por ciento) y 19 años (39,3 por ciento) de antigüedad.
  - La mayoría de los grupos entre 2 y 20 años se mueven en un rango relativamente similar, entre aproximadamente 30 y 40 por ciento.
  - En 24 años de antigüedad aparece una tasa del 100 por ciento, sin embargo, este valor corresponde a un único trabajador en esa categoría, por lo que el porcentaje extremo es producto del tamaño muestral tan pequeño y no debe interpretarse como un riesgo real elevado para ese grupo. 
- **Nivel educativo:** las diferencias entre categorías son moderadas, con tasas que se mantienen en un rango de aproximadamente 31 a 37 por ciento. El nivel técnico registra la tasa más alta (cercana al 36,8 por ciento), seguido de bachillerato (35,1 por ciento) y nivel universitario (33,6 por ciento). La conclusión es que el nivel educativo formal, por sí solo, no es un factor determinante para reducir la accidentalidad, probablemente incide más el tipo de labor desempeñada que el nivel de estudios en sí.

- **Sistema de gestión de seguridad y salud en el trabajo (SG-SST):** este es uno de los hallazgos más claros del análisis. Las empresas que cuentan con un SG-SST estructurado e implementado registran una menor tasa de accidentalidad frente a aquellas que no lo tienen o que están en etapas iniciales de implementación. 

- **Tipo de lesión:** al analizar la distribución de los accidentes según el tipo de lesión sufrida, la fractura es la más frecuente, con más de 300 casos registrados, seguida por las lesiones múltiples, con aproximadamente 212 registros. La concentración de accidentes en golpes y fracturas severas indica que los trabajadores están expuestos a mecanismos de riesgo de alta severidad, no solo a incidentes menores.

- **Tipo de empresa (pública vs. privada):** la tasa de trabajadores accidentados es prácticamente la misma en ambos tipos de empresa, situándose entre 35 y 36 por ciento aproximadamente. Esto indica que la naturaleza pública o privada de la empresa no es, por sí sola, un factor explicativo del riesgo, los accidentes ocurren de forma similar en ambos sectores.

### Conclusiones principales

2. **El primer año de vinculación requiere un acompañamiento especial.** La concentración de incidentes entre los trabajadores con menor antigüedad evidencia la importancia de fortalecer los procesos de inducción, adaptación al puesto de trabajo y supervisión durante las primeras etapas.
3. **Existe una falta de estandarización en la gestión de la seguridad entre las empresas ** Las diferencias en los niveles de accidentalidad entre las 150 empresas pueden estar relacionadas con la diversidad en el grado de implementación de sus respectivos SG-SST, más que con su tamaño, sector o naturaleza pública o privada.

### Recomendaciones

- **Rotación y pausas activas:** reestructurar los turnos nocturnos y mixtos, implementando pausas activas obligatorias y límites a las horas extra, con el fin de reducir la fatiga de los trabajadores expuestos a estos horarios.
- **Capacitación obligatoria de ingreso:** establecer como regla de negocio que ningún trabajador del área operativa inicie labores sin haber completado un módulo de inducción y capacitación básica en seguridad.
- **Auditorías permanentes de seguridad y salud en el trabajo**, priorizando su implementación en los sectores identificados como de mayor riesgo, entre ellos construcción y minería.