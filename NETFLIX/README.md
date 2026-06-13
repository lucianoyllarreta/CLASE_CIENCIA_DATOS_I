# 🎬 Netflix Data Insight
### *Detrás de la Pantalla*

> **Pregunta de investigación:** ¿Existe alguna relación entre el comportamiento de los usuarios de Netflix y la calidad del sueño de las personas?

**Equipo:** Aparo · Filizzola · Hernandez · Cioffi
**Materia:** Ciencia de Datos — Universidad Católica Argentina, Sede Mendoza · 2026
**Herramientas:** Python · Pandas · Matplotlib · Plotly · Seaborn · Statsmodels · Scikit-learn · Google Colab · Kaggle

---

## 📁 Datasets

| Dataset | Registros | Variables |
|---|---|---|
| `netflix_cleaned_20251011_141144.csv` | 25.000+ | 15 |
| `sleep_health_dataset.csv` | 374 | 20 |

> Variable compartida para unir ambos datasets: **`age`**

---

## 📋 Índice

**Primer análisis — Netflix**
1. [Carga del dataset Netflix](#1-carga-del-dataset-netflix)
2. [Exploración inicial](#2-exploración-inicial)
3. [Distribución y conteo de variables categóricas](#3-distribución-y-conteo-de-variables-categóricas)
4. [Género favorito por país](#4-género-favorito-por-país)
5. [Definición de regiones Este / Oeste](#5-definición-de-regiones-este--oeste)
6. [Top 3 géneros — región Este](#6-top-3-géneros--región-este)
7. [Top 3 géneros — región Oeste](#7-top-3-géneros--región-oeste)
8. [Consumo por género y perfil demográfico](#8-consumo-por-género-y-perfil-demográfico)
9. [Top 3 por grupo de género](#9-top-3-por-grupo-de-género)
10. [Tiempo de visualización promedio por género](#10-tiempo-de-visualización-promedio-por-género)
11. [Tasa de abandono global (< 40%)](#11-tasa-de-abandono-global--40)
12. [Configuración visual estilo Netflix](#12-configuración-visual-estilo-netflix)
13. [Segmentación de formatos y sistema de puntuación (Scoring) por género](#13-segmentación-de-formatos-y-scoring-por-género)
14. [Score de géneros recomendados — modelo ponderado v1](#14-score-de-géneros-recomendados--modelo-ponderado-v1)
15. [Gráfico: Composición del catálogo (dona)](#15-gráfico-composición-del-catálogo-dona)
16. [Gráfico: Frecuencia de películas por rango de duración](#16-gráfico-frecuencia-de-películas-por-rango-de-duración)
17. [Gráfico: Top 10 géneros con mayor demanda](#17-gráfico-top-10-géneros-con-mayor-demanda)
18. [Gráfico: Análisis de eficiencia financiera — ROI por género](#18-gráfico-análisis-de-eficiencia-financiera--roi-por-género)
19. [Gráfico: Volumen de consumo segmentado por región Este y Oeste](#19-gráfico-volumen-de-consumo-segmentado-por-región-este-y-oeste)
20. [Gráfico: Tasa de abandono — regla del 90% y fidelidad por género](#20-gráfico-tasa-de-abandono--regla-del-90-y-fidelidad-por-género)
21. [Score de géneros recomendados — modelo ponderado v2 + Score compuesto](#21-score-de-géneros-recomendados--modelo-ponderado-v2--score-compuesto)

**Segundo análisis — Salud del sueño**

22. [Carga del dataset de sueño](#22-carga-del-dataset-de-sueño)
23. [Filtrado por país (USA y Canadá)](#23-filtrado-por-país-usa-y-canadá)
24. [Cruce de variables por edad: plataforma vs. calidad de sueño](#24-cruce-de-variables-por-edad-plataforma-vs-calidad-de-sueño)
25. [KPIs estratégicos: análisis de retención y calidad de sueño (Dashboard)](#25-kpis-estratégicos-dashboard)
26. [Correlaciones avanzadas: intensidad de género y éxito de taquilla vs. insomnio](#26-correlaciones-avanzadas-intensidad-de-género-y-taquilla-vs-insomnio)
27. [Comparativa de formatos: retención e insomnio (Series vs. Películas)](#27-comparativa-de-formatos-series-vs-películas)
28. [Impacto de la profesión en el estrés y uso de pantallas](#28-impacto-de-la-profesión-en-el-estrés-y-uso-de-pantallas)
29. [Segmentación por salud mental: Netflix vs. tiempo total en pantalla](#29-segmentación-por-salud-mental-netflix-vs-tiempo-total-en-pantalla)
30. [Análisis de tendencia: impacto del streaming vs. estrés](#30-análisis-de-tendencia-impacto-del-streaming-vs-estrés)
31. [Cálculo de Score Avanzado de Sueño (escala 0-100)](#31-cálculo-de-score-avanzado-de-sueño-escala-0-100)
32. [Correlación estadística interactiva: ¿qué afecta realmente al sueño?](#32-correlación-estadística-interactiva-qué-afecta-realmente-al-sueño)
33. [Modelo de regresión lineal múltiple OLS y extracción de coeficientes](#33-modelo-de-regresión-lineal-múltiple-ols)
34. [Simulador interactivo: proyección poblacional a 12 meses](#34-simulador-interactivo-proyección-poblacional-a-12-meses)
35. [Forecast predictivo: el desacople entre pantallas y bienestar](#35-forecast-predictivo-el-desacople-entre-pantallas-y-bienestar)
36. [Carga de los DataFrames iniciales (merge final)](#36-carga-de-los-dataframes-iniciales-merge-final)
37. [Filtrado y preparación de datos clave](#37-filtrado-y-preparación-de-datos-clave)
38. [Creación del perfil promedio de sueño](#38-creación-del-perfil-promedio-de-sueño)
39. [Diagnóstico: verificación de claves para el merge](#39-diagnóstico-verificación-de-claves-para-el-merge)
40. [Realización del merge (unión)](#40-realización-del-merge-unión)
41. [Análisis Planteamiento N°1: correlación entre tiempo de Netflix y salud del sueño](#41-análisis-planteamiento-n1-correlación-entre-tiempo-de-netflix-y-salud-del-sueño)
42. [Cálculo de correlaciones](#42-cálculo-de-correlaciones)
43. [Visualización de correlaciones (Heatmap)](#43-visualización-de-correlaciones-heatmap)
44. [KPIs relevantes y accionables](#44-kpis-relevantes-y-accionables)
45. [Scoring 1: impacto de genre_primary en la salud del sueño](#45-scoring-1-impacto-de-genre_primary-en-la-salud-del-sueño)
46. [Scoring 2: impacto de device_type en la salud del sueño](#46-scoring-2-impacto-de-device_type-en-la-salud-del-sueño)
47. [Predicción del riesgo de abandono (Churn)](#47-predicción-del-riesgo-de-abandono-churn)
48. [Pronóstico del rendimiento de nuevos contenidos](#48-pronóstico-del-rendimiento-de-nuevos-contenidos)
49. [Conclusión del Forecast: visualización de regresión](#49-conclusión-del-forecast-visualización-de-regresión)
50. [KPI 1: compromiso de contenido vs. patrones de sueño no saludables](#50-kpi-1-compromiso-de-contenido-vs-patrones-de-sueño-no-saludables)
51. [KPI 2: géneros con mayor correlación negativa en la calidad del sueño](#51-kpi-2-géneros-con-mayor-correlación-negativa-en-la-calidad-del-sueño)
52. [KPI 3: rendimiento cognitivo y duración de sesión por tipo de dispositivo](#52-kpi-3-rendimiento-cognitivo-y-duración-de-sesión-por-dispositivo)
53. [Proyecciones avanzadas: rentabilidad, edad y categorías de impacto](#53-proyecciones-avanzadas-rentabilidad-edad-y-categorías-de-impacto)

---

## 🔍 Descripción de celdas

---

## PARTE 1 — Análisis Netflix

### 1. Carga del dataset Netflix
Abre el explorador de archivos de Colab para subir el CSV manualmente. Es el primer paso obligatorio: sin este paso ninguna celda posterior puede leer los datos.

---

### 2. Exploración inicial
Carga el CSV en un DataFrame llamado `df` usando `pd.read_csv()`. Este es el objeto base con el que se trabaja en todo el proyecto. A partir de acá todos los análisis parten de `df`.

---

### 3. Distribución y conteo de variables categóricas
Aplica `.value_counts()` a las columnas clave: `genre_primary`, `genre_secondary`, `country`, `gender`, `device_type`, `quality`, `state_province` y `city`. Sirve para entender qué valores únicos tiene cada variable y detectar datos sucios o desbalanceados antes de hacer análisis más complejos.

---

### 4. Género favorito por país
Agrupa el dataset por país y extrae el género más visto en cada uno usando `.describe()`, que devuelve estadísticas de frecuencia para columnas de texto. El resultado es una tabla **País → Género Favorito** que permite ver diferencias culturales de consumo a nivel global.

---

### 5. Definición de regiones Este / Oeste
Define manualmente las listas de estados y provincias de EE.UU. y Canadá que pertenecen a cada costa. Incluye provincias canadienses porque el dataset cubre todo Norteamérica. Estas listas son usadas en las celdas de filtrado regional subsiguientes.

---

### 6. Top 3 géneros — región Este
Filtra `df` usando `.isin()` sobre los estados del Este y calcula los 3 géneros más vistos por cantidad de registros.

---

### 7. Top 3 géneros — región Oeste
Misma lógica que la celda anterior, aplicada a la región Oeste.

> **Resultado:** Aventura domina en el Oeste · Historia domina en el Este.

---

### 8. Consumo por género y perfil demográfico
Separa el dataset en cuatro grupos por género del usuario (Female, Male, Other, Prefer not to say). Calcula el conteo y porcentaje de visualizaciones por género de contenido para cada grupo y une todo con `merge()` en `df_final`. Incluye una visualización interactiva con **Plotly** en barras agrupadas con colores diferenciados por sexo. El gráfico incluye hover con representación porcentual por grupo.

---

### 9. Top 3 por grupo de género
Extrae los 3 géneros más vistos para cada uno de los cuatro grupos usando `sort_values().head(3)` sobre el `df_final` de la celda anterior.

> **Resultado:** Historia y Aventura dominan en todos los grupos, con leves variaciones entre ellos.

---

### 10. Tiempo de visualización promedio por género
Calcula por género el tiempo promedio de visualización, el tiempo total acumulado y la cantidad de registros usando `.agg()`. Es la base estadística que alimenta el modelo de scoring de las celdas siguientes.

---

### 11. Tasa de abandono global (< 40%)
Calcula qué porcentaje del total de sesiones terminaron antes del 40% del contenido. Es un número de referencia global previo al análisis detallado por género. El umbral más estricto (90%) se aplica en el gráfico posterior.

---

### 12. Configuración visual estilo Netflix
Importa las librerías necesarias (`matplotlib`, `numpy`, `pandas`) y define la paleta de colores: fondo negro `#000000`, rojo Netflix `#E50914`, grises. También silencia los warnings de fuentes de Matplotlib.

> ⚠️ Esta celda debe ejecutarse **antes** de cualquier gráfico.

---

### 13. Segmentación de formatos y Scoring por género
Crea DataFrames separados para cada tipo de contenido: `df_peliculas`, `df_series`, `df_miniseries`, `df_documentales` y `df_standup`. Define también las variables de columnas clave (`c_tipo`, `c_duracion`, `c_genero`, `c_presupuesto`, etc.) que se reutilizan en todos los gráficos siguientes.

---

### 14. Score de géneros recomendados — modelo ponderado v1
Construye un modelo de scoring con dos variables ponderadas:

| Variable | Peso | Criterio |
|---|---|---|
| Volumen de consumo total (normalizado 0–100) | 60% | Mayor total = mejor score |
| Duración promedio óptima | 40% | 90–150 min = 100 pts · 40–90 min = 50 pts · resto = 0 |

El resultado es un ranking de géneros más recomendables para la plataforma.

---

### 15. Gráfico: Composición del catálogo (dona)
Gráfico de dona que muestra la proporción de **películas vs. series** en el catálogo, con el total de títulos en el centro. Las etiquetas muestran porcentaje y cantidad absoluta de forma simultánea. Usa un `Circle` de matplotlib superpuesto para crear el hueco central.

---

### 16. Gráfico: Frecuencia de películas por rango de duración
Histograma de frecuencias que categoriza las películas en rangos de 45 minutos (0–45 / 45–90 / 90–135 / 135–180 / +180). Primero limpia la columna de duración que puede venir como string tipo `"90 min"` y luego asigna cada película a su rango con una función personalizada.

> **Resultado:** La mayoría del catálogo se concentra en el rango **90–135 minutos**.

---

### 17. Gráfico: Top 10 géneros con mayor demanda
Gráfico de barras horizontales con los 10 géneros más vistos por cantidad de registros. Invierte el orden con `[::-1]` para que el género mayor quede arriba. Cada barra muestra su valor exacto como etiqueta flotante.

---

### 18. Gráfico: Análisis de eficiencia financiera — ROI por género
Calcula el ROI promedio por género como `box_office_revenue / production_budget` y grafica el top 10 en barras horizontales. La línea punteada vertical en `x = 1.0` marca el punto de equilibrio financiero (break-even). Géneros por encima recuperan más de lo que costó producirlos.

---

### 19. Gráfico: Volumen de consumo segmentado por región Este y Oeste
Usa `GridSpec` para dividir la figura en dos paneles: barras horizontales con volumen total (izquierda) y tarjetas de texto con el top 3 por región (derecha). La función `clasificar_costa()` asigna cada fila a Este, Oeste o Desconocido. Es el gráfico más complejo visualmente del proyecto.

---

### 20. Gráfico: Tasa de abandono — regla del 90% y fidelidad por género
Define abandono como sesiones donde el tiempo visto es menor al **90% de la duración** del título. Muestra los 3 géneros con mayor fidelidad (🟢 verde) y los 3 con mayor deserción (🔴 rojo) en el mismo gráfico.

> **Resultado:** Crimen retiene mejor · Fantasía pierde más usuarios antes de terminar.

---

### 21. Score de géneros recomendados — modelo ponderado v2 + Score compuesto
Segunda versión del scoring con tres variables:

| Variable | Peso |
|---|---|
| Tiempo promedio de visualización | 20% |
| Tiempo total acumulado | 50% |
| Cantidad de contenidos | 30% |

Luego calcula un **Content Engagement Score** combinando el score normalizado de género (40%), la tasa de retención (30%) y una penalización basada en la latencia promedio del sueño extraída de `df2` (30%). El gráfico final compara el score original de Netflix vs. el Content Engagement Score con penalización de sueño en barras horizontales dobles.

---

## PARTE 2 — Análisis Salud del Sueño

---

### 22. Carga del dataset de sueño
Carga `sleep_health_dataset.csv` en `df2` mediante `files.upload()` de Colab.

---

### 23. Filtrado por país (USA y Canadá)
Filtra `df2` para retener solo registros de USA y Canadá, que son los mismos países presentes en el dataset de Netflix, facilitando el cruce posterior por `age`.

---

### 24. Cruce de variables por edad: plataforma vs. calidad de sueño
Agrupa ambos datasets por `age` para obtener promedios de `duration_minutes` (Netflix) y `sleep_quality_score` (sueño) y los une con `pd.merge()` sobre la clave común `age`. Es el primer merge del proyecto y el punto de partida del análisis cruzado.

---

### 25. KPIs estratégicos — Dashboard
Calcula seis métricas clave y las visualiza en un **dashboard de 9 tarjetas** (3×3):

**Fila Netflix (rojo):** Retención promedio · Minutos por sesión · Abandono crítico (< 40%)

**Fila Sueño (verde):** Déficit de sueño (< 7 horas) · Calidad de sueño promedio · Nivel de estrés promedio

**Fila Combinada (azul/blanco):** Correlación retención/pantalla nocturna · Calidad de sueño heavy users · Calidad de sueño light users

Cada tarjeta muestra el valor real y el **objetivo ideal** en amarillo. Incluye además dos gráficos de dona adicionales (tasa de abandono crítico y déficit de sueño) y un gráfico de barras comparando calidad de sueño entre heavy y light users.

---

### 26. Correlaciones avanzadas: intensidad de género y taquilla vs. insomnio
Clasifica los géneros del catálogo en tres grupos según su intensidad emocional: **Tranquilo** (Documental, Animación, Romance, Familia, Música), **Intenso** (Acción, Terror, Thriller, Sci-Fi, Guerra, Crimen) y **Neutro/Otro**. Calcula:
- Correlación entre % de contenido tranquilo y calidad de sueño
- Correlación entre % de contenido intenso y nivel de estrés

Luego evalúa el impacto de los **blockbusters** (películas en el cuartil superior de recaudación): compara minutos vistos en éxitos de taquilla vs. películas normales, y cruza el consumo por edad con latencia del sueño e horas de descanso.

---

### 27. Comparativa de formatos: Series vs. Películas
Clasifica el contenido en Series y Películas usando la función `clasificar_formato()`. Calcula el promedio de minutos vistos por sesión para cada formato y la correlación entre preferencia por series y latencia del sueño. Visualización doble:
- **Panel izquierdo:** Adicción por formato (minutos por sesión)
- **Panel derecho:** Latencia del sueño según perfil (amante del cine vs. maratonista de series)

---

### 28. Impacto de la profesión en el estrés y uso de pantallas
Usa **Seaborn** para graficar el nivel de estrés promedio y el tiempo en pantalla antes de dormir, ordenados de mayor a menor por profesión. Luego cruza Netflix y sueño por `country`, `age` y `gender` para crear el **cuadrante del insomnio**: un scatter plot con estrés en el eje Y y minutos en Netflix en el eje X, con cada punto siendo una profesión etiquetada. Las líneas de promedio dividen el cuadrante en cuatro zonas.

---

### 29. Segmentación por salud mental: Netflix vs. tiempo total en pantalla
Cruza ambos datasets por `country`, `age` y `gender` para comparar, por condición de salud mental (Saludable / Depresión / Ansiedad / Ansiedad + Depresión):
- Minutos promedio viendo Netflix por sesión → **todos los grupos son iguales** (el verdadero hallazgo)
- Minutos de pantalla total antes de dormir → **varía significativamente** entre grupos

La visualización doble con Seaborn demuestra que el problema no es Netflix específicamente sino el escapismo digital general.

---

### 30. Análisis de tendencia: impacto del streaming vs. estrés
Dos scatter plots con línea de regresión lineal (`sns.regplot`) que demuestran visualmente la conclusión central del proyecto:
1. **Netflix vs. calidad del sueño** → sin correlación significativa (pendiente plana)
2. **Estrés vs. calidad del sueño** → correlación negativa fuerte (pendiente pronunciada hacia abajo)

> **Conclusión visual:** El uso de Netflix **no se relaciona** con mal sueño. El estrés laboral sí.

---

### 31. Cálculo de Score Avanzado de Sueño (escala 0-100)
Desarrolla la función `calcular_score_avanzado()` que consolida múltiples variables fisiológicas en un único índice clínico de salud del sueño:

| Variable | Peso | Tope |
|---|---|---|
| Duración del sueño | 25 pts | máx. 25 |
| Calidad subjetiva reportada | 25 pts | — |
| % de sueño REM | 15 pts | máx. 15 |
| % de sueño profundo | 15 pts | máx. 15 |
| Penalización por latencia | −0.5 pts/min | — |
| Penalización por despertares | −4 pts/episodio | — |

El resultado se clampea entre 0 y 100. La tabla muestra las primeras 10 filas con duración, calidad reportada, latencia y score clínico calculado.

---

### 32. Correlación estadística interactiva: ¿qué afecta realmente al sueño?
Gráfico de barras horizontales **interactivo con Plotly** que compara los coeficientes de correlación de Pearson de las dos variables clave sobre `sleep_quality_score`:
- **Estrés:** correlación negativa fuerte (rojo)
- **Netflix:** correlación casi nula (verde)

Una línea punteada vertical marca el cero. La conclusión queda visualmente contundente: el estrés destruye el sueño, Netflix no.

---

### 33. Modelo de regresión lineal múltiple OLS
Entrena un modelo **OLS** (*Ordinary Least Squares* / Mínimos Cuadrados Ordinarios) con la librería `statsmodels` usando cuatro variables predictoras:

| Variable independiente | Impacto esperado |
|---|---|
| Minutos en Netflix | casi nulo |
| Nivel de estrés | negativo fuerte |
| Horas de trabajo | negativo |
| Época de vacaciones | positivo |

El gráfico de barras horizontales muestra los coeficientes del modelo (verde = ayuda al sueño, rojo = perjudica). Incluye un **pronóstico de ejemplo**: un oficinista estresado que ve 2 horas de Netflix obtiene una predicción de calidad de sueño estimada.

---

### 34. Simulador interactivo: proyección poblacional a 12 meses
Herramienta interactiva con menú desplegable en Colab (parámetro de formulario) que permite seleccionar un Score Clínico del 1 al 10 y visualizar la proyección a 12 meses de cuatro métricas basadas en los datos reales de usuarios con ese perfil:
1. Consumo de Netflix (minutos)
2. Nivel de estrés
3. Calidad de sueño
4. Despertares por noche

El color de los gráficos cambia según el score (rojo para 1–3, naranja para 4–6, verde para 7–8, azul para 9–10).

---

### 35. Forecast predictivo: el desacople entre pantallas y bienestar
Serie temporal a 10 años (2021–2030) con doble eje Y que muestra cómo tres curvas evolucionan en paralelo:
- **Consumo de Netflix** (eje izquierdo, rojo): se estabiliza y baja levemente
- **Estrés global** (eje derecho, naranja): sube sostenidamente
- **Calidad del sueño** (eje derecho, azul): baja sostenidamente

El gráfico divide la figura en zona histórica (2021–2025) y zona de forecast (2026–2030). La conclusión: **la crisis del descanso empeora independientemente del consumo de streaming**.

---

### 36. Carga de los DataFrames iniciales (merge final)
Recarga limpiamente ambos datasets para el bloque final del análisis. Usa manejo especial de encoding con `errors="replace"` para evitar fallos al leer el CSV de sueño. Detecta automáticamente la fila de encabezado de `sleep_health_dataset.csv` buscando las columnas `person_id` y `country`.

---

### 37. Filtrado y preparación de datos clave
Filtra ambos datasets para retener solo USA y Canadá, limpia la columna `duration_minutes` de strings (`"90 min"` → `90`), calcula `completion_rate` como `watch_duration_minutes / duration_num` y construye los DataFrames agrupados por `age` con promedios de minutos vistos y calidad de sueño.

---

### 38. Creación del perfil promedio de sueño
Genera el perfil estadístico promedio del dataset de sueño: latencia media, horas de sueño, calidad promedio, despertares, % REM y % sueño profundo. Este perfil es el benchmark contra el que se comparan los distintos grupos de usuarios de Netflix.

---

### 39. Diagnóstico: verificación de claves para el merge
Verifica que las columnas clave (`age`, `country`, `gender`) existan en ambos datasets antes de ejecutar el merge, y muestra los valores únicos de cada una para detectar inconsistencias de formato (ej. "USA" vs "United States") que impedirían el cruce correcto.

---

### 40. Realización del merge (unión)
Une ambos datasets por `age` usando `pd.merge(..., on="age", how="inner")`. El `inner join` retorna solo los registros donde la edad aparece en ambas tablas. Es el punto de conexión entre comportamiento de consumo en Netflix e indicadores clínicos de salud del sueño.

---

### 41. Análisis Planteamiento N°1: correlación entre tiempo de Netflix y salud del sueño
Primer análisis formal post-merge. Construye el DataFrame cruzado por `age` y `gender` que combina minutos en Netflix con `sleep_quality_score`, `stress_score` y `work_hours_that_day`. Es la base para todos los cálculos de correlación del bloque final.

---

### 42. Cálculo de correlaciones
Calcula los coeficientes de Pearson entre el tiempo de visualización en Netflix y los indicadores de sueño del dataset combinado. Genera la matriz de correlación completa del DataFrame cruzado.

---

### 43. Visualización de correlaciones (Heatmap)
Visualiza la matriz de correlación en un mapa de calor (`heatmap`) estilo Netflix con fondo oscuro. Permite identificar visualmente qué pares de variables se relacionan entre sí y cuáles son independientes.

---

### 44. KPIs relevantes y accionables
Extrae del modelo cruzado los indicadores más relevantes para la toma de decisiones: diferencia de calidad de sueño entre heavy y light users, correlación entre retención y pantalla nocturna, y tasa de déficit de sueño en la muestra norteamericana.

---

### 45. Scoring 1: impacto de `genre_primary` en la salud del sueño
Asigna a cada género un puntaje de **intensidad emocional** (1 = baja, 2 = media, 3 = alta) y calcula el `sleep_risk_score` promedio por género combinando:
- Intensidad emocional normalizada (40%)
- Duración de sesión normalizada, con tope en 135 min (35%)
- Screen time promedio del dataset de sueño, normalizado (25%)

El resultado es un ranking de géneros ordenado de mayor a menor riesgo para el sueño.

---

### 46. Scoring 2: impacto de `device_type` en la salud del sueño
Extiende el análisis de riesgo de sueño segmentando por tipo de dispositivo utilizado para ver Netflix. Evalúa si el formato de pantalla (TV, celular, computadora, tablet) tiene impacto en la latencia y calidad del descanso.

---

### 47. Predicción del riesgo de abandono (Churn)
Desarrolla un modelo predictivo para estimar la probabilidad de abandono de contenido. Cruza variables de comportamiento de visualización (completion rate, géneros consumidos) con indicadores de sueño para identificar perfiles de usuario con mayor riesgo de churn.

---

### 48. Pronóstico del rendimiento de nuevos contenidos
Proyecta el rendimiento esperado de nuevos géneros o formatos de contenido en función de las métricas de engagement y los patrones de sueño identificados en el análisis. Combina el modelo de scoring de géneros con los coeficientes del modelo OLS.

---

### 49. Conclusión del Forecast: visualización de regresión
Consolida los resultados del modelo OLS en una serie de visualizaciones finales que demuestran el impacto diferencial de cada variable predictora. Incluye gráficos de tendencia por franja etaria, proyección de latencia del sueño según consumo de pantalla (optimista / actual / pesimista) y el forecast de score clínico a 20 años.

---

### 50. KPI 1: compromiso de contenido vs. patrones de sueño no saludables
Cruza el Content Engagement Score (calculado en la celda 21) con el porcentaje de usuarios de cada género que presentan patrones de sueño problemáticos (latencia > 30 min o score clínico < 25). Identifica los géneros donde el alto engagement coexiste con mayor deterioro del sueño.

---

### 51. KPI 2: géneros con mayor correlación negativa en la calidad del sueño
Ordena los géneros del catálogo según la magnitud de su correlación negativa con `sleep_quality_score`. Permite identificar cuáles tipos de contenido están más asociados (aunque no necesariamente causan) a menor calidad de descanso en los usuarios de la muestra.

---

### 52. KPI 3: rendimiento cognitivo y duración de sesión por dispositivo
Evalúa cómo varía la duración de sesión y la latencia del sueño según el tipo de dispositivo. Genera el indicador de rendimiento cognitivo post-sesión como proxy del impacto en la concentración y el descanso según el formato de pantalla utilizado.

---

### 53. Proyecciones avanzadas: rentabilidad, edad y categorías de impacto
Bloque final de proyecciones que combina tres dimensiones: la rentabilidad financiera de los géneros (ROI), la franja etaria de los usuarios y las categorías de impacto en el sueño. Genera un mapa estratégico que permite a la plataforma identificar qué contenidos son simultáneamente rentables y respetuosos del bienestar del usuario.

---

## 🏁 Conclusión

El análisis combinado de ambos datasets permitió estudiar en profundidad la relación entre el consumo de Netflix y la calidad del sueño en usuarios de Norteamérica.

**La conclusión principal es que Netflix en sí no afecta significativamente la calidad del sueño.** El modelo OLS y los coeficientes de Pearson demuestran que el tiempo de visualización en la plataforma tiene una correlación casi nula con el score de sueño. Los verdaderos predictores negativos son el **estrés** y las **horas de trabajo**.

El screen time total antes de dormir sí tiene un efecto medible sobre la latencia, pero ese efecto es independiente de Netflix específicamente. La diferencia entre heavy y light users de la plataforma en calidad de sueño es mínima.

El forecast a 10 años proyecta que la crisis del descanso empeorará por factores estructurales (estrés laboral, salud mental) independientemente de cómo evolucione el consumo de streaming.

