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

El recorte final trabajado en el notebook (`secop_recorte.csv`) contiene **39,928 filas y 85 columnas**.

De las 85 columnas disponibles, el análisis se concentró en un subconjunto reducido: `id_contrato`, `nombre_entidad`, `ciudad`, `proveedor_adjudicado`, `documento_proveedor`, `tipo_de_contrato`, `modalidad_de_contratacion`, `valor_del_contrato`, `fecha_de_firma`, `fecha_de_inicio_del_contrato`, `fecha_de_fin_del_contrato`, y dos variables derivadas calculadas en el notebook: `duracion_dias` (fecha de fin menos fecha de inicio) y `valor_mensual_equivalente` (valor del contrato dividido entre la duración aproximada en meses).

##  Qué se analizó en el notebook

**Descripción del valor del contrato.** Se calcularon media, mediana y percentiles (25, 75, 90) de `valor_del_contrato`, junto con un histograma de la distribución (vista hasta el percentil 99). 

**Revisión de calidad de los datos.** Se revisaron faltantes, valores únicos y duplicados en las columnas clave (`id_contrato`, `nombre_entidad`, `ciudad`, `proveedor_adjudicado`, `documento_proveedor`, `valor_del_contrato`, fechas y `duracion_dias`), además de contratos con valor $0

**Valor, duración y valor mensual equivalente.** Se creó el conjunto de datos `case_data` dejando solo los contratos con valor y duración mayores a cero. Luego, se calcularon las estadísticas de estas tres variables, mostrándolas tanto en notación científica como en números enteros redondeados para facilitar su lectura.

