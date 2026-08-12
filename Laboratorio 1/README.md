# Restaurant Analytics — Laboratorio Semana 2 (Data Analytics)

## Objetivo
Consolidar los datos de productos, clientes y ventas de un restaurante (Semana 1 y Semana 2) para construir indicadores de ingresos, frecuencia de compra y recurrencia de clientes que apoyen decisiones sobre el menú y la fidelización, documentando el proceso en un notebook reproducible y en un informe ejecutivo de una página.

## Datos utilizados
| Archivo | Contenido |
|---|---|
| `data/Restaurant-Foods.csv` | Catálogo de productos y precios (10 ítems). |
| `data/Restaurant-Customers.csv` | Información de clientes (ID, ocupación, etc.). |
| `data/Restaurant-Week1-Sales.csv` | 250 registros de venta de la Semana 1. |
| `data/Restaurant-Week2-Sales.csv` | 250 registros de venta de la Semana 2. |

**Alcance:** los archivos contienen precios de venta pero no costos, cantidades ni descuentos. Por eso el análisis cubre ingresos, frecuencia de compra y recurrencia, y no rentabilidad, utilidad ni margen.

> ⚠️ Por privacidad, `Restaurant-Customers.csv` (que contiene nombres de clientes) **no se publica** en este repositorio público. El notebook tampoco muestra nombres de clientes en sus salidas.

## Instrucciones de ejecución
1. Clonar el repositorio y ubicar los 4 archivos CSV dentro de la carpeta `data/` (no incluida en el repo por privacidad; solicitarla al docente/administrador de los datos).
2. Instalar dependencias: `pandas`, `matplotlib`, `sqlite3` (incluida en la librería estándar de Python).
3. Abrir y ejecutar `lab_Sem2_DA.ipynb` de principio a fin, sin modificaciones manuales de código (salvo la carga inicial de archivos si se usa Google Colab).
4. El notebook valida las llaves y uniones, construye los indicadores (KPIs), genera las visualizaciones y responde las preguntas de análisis.

## Principales hallazgos
- **Ingresos totales:** $3,886.56 en 500 registros de venta (250 por semana).
- **Semana 1 vs. Semana 2:** mismos registros de venta (250 y 250), pero los ingresos bajaron de $1,962.68 a $1,923.88 (–$38.80) y el ingreso promedio por registro bajó de $7.85 a $7.70. La causa no puede atribuirse con solo dos semanas de datos.
- **Desempeño del menú:** el producto más pedido es Drink (59 registros), pero el que más ingresos genera es Steak ($1,249.50; 50 registros) — frecuencia e ingresos no son equivalentes. Pizza es el producto menos pedido (39 veces) y Donut es el de menor ingreso total.
- **Recurrencia:** de 221 clientes únicos en la Semana 1, 46 volvieron en la Semana 2 (tasa de recurrencia del 20.8%).
- **Perfil por ocupación:** las ocupaciones con mayor ingreso agregado son Compensation Analyst, Sales Representative, Marketing Manager, Cost Accountant y Assistant Media Planner (análisis agregado, no individual).

## Entregables
- `lab_Sem2_DA.ipynb` — notebook ejecutado.
- `Informe_Ejecutivo_La_Analitica.docx` — informe ejecutivo de una página para el dueño del restaurante.
- Este `README.md`.
