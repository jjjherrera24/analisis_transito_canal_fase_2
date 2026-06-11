# Predicción del Tiempo de Tránsito y Espera en el Canal de Panamá

Este repositorio contiene el código, los datos y las visualizaciones utilizadas para el análisis del tránsito en el Canal de Panamá y la creación de modelos predictivos basados en variables operativas, técnicas, meteorológicas e hidrológicas históricas. El estudio cubre el período **2019–2023** e integra información sobre características de embarcaciones, registros operativos del Canal, datos climáticos y el nivel del Lago Gatún.


---

## Entorno de desarrollo: Google Colab

**Importante:** Los notebooks de este proyecto fueron desarrollados íntegramente en **Google Colab**.

Para garantizar la correcta ejecución del código, la compatibilidad de las librerías y replicar las condiciones de desarrollo, **se recomienda abrir y ejecutar los notebooks en Google Colab**.

---

## Estructura del repositorio

```
📁 Fase I - Especificaciones de Buques + Viento
📁 Fase II - Nivel de Agua Lago Gatun + Factores Climaticas Varios
📁 datasets
📄 README.md
```

---

### 📁 Fase I — Especificaciones de Buques + Viento

Contiene el trabajo correspondiente a la primera etapa del proyecto, enfocada en el análisis de las características técnicas de los buques y variables de viento.

| Archivo | Descripción |
|---|---|
| `Análisis_de_Tránsito_del_Canal_de_Panamá.ipynb` | Notebook principal de la Fase I con el flujo completo de ETL, EDA y modelado predictivo inicial. |
| `ANTEPROYECTO_v2_GrupoJeremías.docx` | Documento Word con la formulación inicial del anteproyecto. |
| `Artículo_científico_GrupoCanal.pdf` | Versión en PDF del artículo científico correspondiente a esta fase. |
| `Presentación Final.pbix` | Dashboard de Power BI utilizado en la presentación final de la Fase I. |
| `Resumen Modelos Predictivos.pbix` | Tablero interactivo de Power BI con los resultados y métricas de los modelos predictivos de la Fase I. |

---

### 📁 Fase II — Nivel de Agua Lago Gatún + Factores Climáticos Varios

Contiene el trabajo de la segunda etapa del proyecto, que amplía el análisis incorporando el nivel hidrológico del Lago Gatún y un conjunto más completo de variables climáticas.
| Archivo | Descripción |
|---|---|
| `Proyecto_Integrador_III_EDA.ipynb` | Notebook principal de la Fase II. Contiene el pipeline completo: ETL avanzado, EDA, alineación temporal de variables meteorológicas e hidrológicas, entrenamiento y evaluación de modelos predictivos (Random Forest, XGBoost, KNN, LightGBM y Redes Neuronales) para `transit_time` y `waiting_time`. |
| `Artículo_científico_v3_GrupoCanal.docx` | Versión 3 del artículo científico del proyecto. |
| `Artículo_científico_v4_GrupoCanal.docx` | Versión final del artículo científico publicado. |
| `Dashboard.pbix` | Dashboard de Power BI con las visualizaciones e interpretación de resultados de la Fase II. |
| `Hoja de Ruta_ModeloPredictivodelCanaldePanamá.pdf` | Documento que describe la hoja de ruta metodológica con las mejoras para esta fase del proyecto. |

---

### 📁 datasets

Carpeta que almacena todos los conjuntos de datos utilizados en ambas fases del proyecto.

| Archivo | Descripción |
|---|---|
| `transit.parquet` | Registro detallado e histórico de los tránsitos realizados a través del Canal (2019–2023). |
| `locks_visit.parquet` | Datos sobre las visitas y operaciones en las diferentes esclusas del Canal. |
| `specs.parquet` | Especificaciones técnicas de las embarcaciones: Gross Tonnage, Deadweight, LBP, potencia instalada, entre otras. |
| `clima_total_2015_2024.csv` | Registro histórico de variables climáticas (2015–2024) con frecuencia de cuatro horas: temperatura, humedad relativa, velocidad del viento, ráfagas, déficit de presión de vapor y componentes del viento a 950 hPa. |
| `climate-vars.csv` | Variables climáticas adicionales utilizadas en el análisis de la Fase II. |
| `Gatun_Lake_Water_Level_History.csv` | Registro histórico del nivel del Lago Gatún, utilizado como variable hidrológica representativa de la capacidad operativa del Canal. |

---

## Resumen de resultados (Fase II)

Las variables objetivo del estudio son el **tiempo de tránsito** (`transit_time`) y el **tiempo de espera** (`waiting_time`). El mejor desempeño fue obtenido con **XGBoost**:

| Variable | Modelo | MAE | MAPE | R² |
|---|---|---|---|---|
| Tiempo de tránsito | XGBoost | 0.69 h | 7.82% | 0.73 |
| Tiempo de espera | XGBoost | 11.85 h | 600.67% | 0.52 |

El tiempo de tránsito resultó más predecible, determinado principalmente por variables técnicas del buque (Deadweight, LBP, Gross Tonnage, tipo de esclusa). El tiempo de espera mostró mayor variabilidad, influenciado por factores operativos no directamente observables como la asignación de cupos, restricciones hídricas y programación de tránsitos.

---

## Contribuyentes

Este proyecto fue desarrollado por estudiantes de la **Universidad Tecnológica de Panamá**:

* Katherine Batista
* Kely Feng
* Jeremías Herrera
* Victoria Rodríguez
* Miguel Valzania
* Dr. Juan Marcos Castillo *(docente supervisor y autor de correspondencia)*

## Agradecimientos

Agradecemos al *Dr. Juan Marcos Castillo* por su acompañamiento, orientación y valiosas correcciones a lo largo del desarrollo del proyecto, las cuales permitieron fortalecer el enfoque metodológico y la calidad del estudio.
