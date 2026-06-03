# Netflix Data Insight
### *Detrás de la Pantalla*

> **Pregunta de investigación:** ¿Existe alguna relación entre el comportamiento de los usuarios de Netflix y la calidad del sueño de las personas?

**Equipo:** Aparo · Filizzola · Hernandez · Cioffi  
**Materia:** Ciencia de Datos — Universidad Católica Argentina, Sede Mendoza · 2026  
**Herramientas:** Python · Pandas · Matplotlib · Google Colab · Kaggle

---

## Datasets

| Dataset | Registros | Variables |
|---|---|---|
| `netflix_cleaned_20251011_141144.csv` | 25.000+ | 15 |
| `sleep_health_dataset.csv` | 374 | 20 |

Variable compartida para unir ambos datasets: **`age`**

---

##  Índice de Celdas

1. [Carga del dataset Netflix](#1-carga-del-dataset-netflix)
2. [Exploración inicial](#2-exploración-inicial)
3. [Exploración de variables categóricas](#3-exploración-de-variables-categóricas)
4. [Género favorito por país](#4-género-favorito-por-país)
5. [Definición de regiones Este / Oeste](#5-definición-de-regiones-este--oeste)
6. [Top 3 géneros — región Este](#6-top-3-géneros--región-este)
7. [Top 3 géneros — región Oeste](#7-top-3-géneros--región-oeste)
8. [Géneros por sexo del usuario](#8-géneros-por-sexo-del-usuario)
9. [Top 3 por grupo de género](#9-top-3-por-grupo-de-género)
10. [Tiempo de visualización promedio por género](#10-tiempo-de-visualización-promedio-por-género)
11. [Tasa de abandono global](#11-tasa-de-abandono-global)
12. [Configuración visual estilo Netflix](#12-configuración-visual-estilo-netflix)
13. [Separación por tipo de contenido](#13-separación-por-tipo-de-contenido)
14. [Score de géneros recomendados (modelo ponderado v1)](#14-score-de-géneros-recomendados-modelo-ponderado-v1)
15. [Gráfico: Composición del catálogo (dona)](#15-gráfico-composición-del-catálogo-dona)
16. [Gráfico: Distribución de duración de películas](#16-gráfico-distribución-de-duración-de-películas)
17. [Gráfico: Volumen de consumo por género](#17-gráfico-volumen-de-consumo-por-género)
18. [Gráfico: Rentabilidad por género (ROI)](#18-gráfico-rentabilidad-por-género-roi)
19. [Gráfico: Preferencias regionales Este vs. Oeste](#19-gráfico-preferencias-regionales-este-vs-oeste)
20. [Gráfico: Tasa de abandono por género](#20-gráfico-tasa-de-abandono-por-género)
21. [Score de géneros recomendados (modelo ponderado v2)](#21-score-de-géneros-recomendados-modelo-ponderado-v2)
22. [Carga del dataset de sueño](#22-carga-del-dataset-de-sueño)
23. [Filtrado por país (USA y Canadá)](#23-filtrado-por-país-usa-y-canadá)
24. [Merge Netflix + Sueño](#24-merge-netflix--sueño)

---

## Celdas explicadas

### 1. Carga del dataset Netflix

```python
from google.colab import files
uploaded = files.upload()
```

Abre el explorador de archivos de Colab para subir el CSV manualmente desde la computadora. Es el primer paso obligatorio antes de cualquier análisis. Sin este paso, ninguna celda posterior puede leer los datos.

---

### 2. Exploración inicial

```python
import pandas as pd
df = pd.read_csv("netflix_cleaned_20251011_141144.csv")
```

Carga el CSV en un DataFrame de pandas llamado `df`, que es la estructura base con la que se trabaja en todo el proyecto. A partir de acá todos los análisis toman `df` como punto de partida.

---

### 3. Exploración de variables categóricas

```python
df.head()

df["genre_primary"].value_counts()
df["genre_secondary"].value_counts()
df["country"].value_counts()
df["gender"].value_counts()
df["device_type"].value_counts()
df["quality"].value_counts()
df["state_province"].value_counts()
df["city"].value_counts()
```

Sirven para entender qué valores únicos tiene cada columna y detectar datos sucios o desbalanceados antes de hacer análisis más complejos.

---

### 4. Género favorito por país

```python
generos_paises = df.groupby("country")["genre_primary"].describe()
preferencias_paises = generos_paises[["top"]].reset_index()
preferencias_paises.columns = ["País", "Genero Favorito"]
preferencias_paises
```

Agrupa el dataset por país y extrae el género más visto en cada uno usando `.describe()`, que devuelve estadísticas de frecuencia para columnas de texto. El resultado es una tabla País → Género Favorito que permite ver diferencias culturales de consumo a nivel global.

---

### 5. Definición de regiones Este / Oeste

```python
eastern_provinces_states = [
    'North Carolina', 'Tennessee', 'Indiana', 'Michigan', 'Florida', 'Illinois', 'Georgia',
    'Massachusetts', 'Maryland', 'New York', 'New Jersey', 'Ohio', 'Virginia', 'Pennsylvania',
    'Nova Scotia', 'Quebec', 'Prince Edward Island', 'Newfoundland and Labrador', 'New Brunswick',
    'Wisconsin', 'Ontario'
]

western_provinces_states = [
    'Texas', 'California', 'Missouri', 'Washington', 'Arizona',
    'Manitoba', 'Alberta', 'British Columbia', 'Saskatchewan'
]
```

Define manualmente las listas de estados y provincias de EE.UU. y Canadá que pertenecen a cada costa. Estas listas se usan en las celdas siguientes para filtrar el DataFrame. Incluye provincias canadienses porque el dataset cubre Norteamérica.

---

### 6. Top 3 géneros — región Este

```python
# Filtramos primero
df_eastern = df[df['state_province'].isin(eastern_provinces_states)]

# Sacamos el conteo, tomamos los 3 primeros y reseteamos el índice para que quede como tabla
top3_este = df_eastern['genre_primary'].value_counts().head(3).reset_index()

# Renombramos columnas para que sea "auto-explicativo"
top3_este.columns = ['Género (Este)', 'Cantidad de Visualizaciones']

print("--- TOP 3 GÉNEROS EN EL ESTE ---")
display(top3_este)
```

Filtra el DataFrame solo con los estados/provincias del Este y calcula los 3 géneros más vistos por cantidad de registros. El resultado muestra qué contenido domina en esa región.

---

### 7. Top 3 géneros — región Oeste

```python
# Filtramos primero (ojo con no cruzar las variables aquí)
df_western = df[df['state_province'].isin(western_provinces_states)]

# Sacamos el conteo del oeste
top3_oeste = df_western['genre_primary'].value_counts().head(3).reset_index()

# Renombramos columnas
top3_oeste.columns = ['Género (Oeste)', 'Cantidad de Visualizaciones']

print("\n--- TOP 3 GÉNEROS EN EL OESTE ---")
display(top3_oeste)
```

Idéntica lógica que la celda anterior pero aplicada a la región Oeste. Permite comparar directamente ambas costas. Resultado: Aventura domina en el Oeste, Historia en el Este.

---

### 8. Géneros por sexo del usuario

```python
import pandas as pd
import plotly.express as px

df_mujeres = df[df['gender'] == 'Female']
df_hombres = df[df['gender'] == 'Male']
df_Other = df[df['gender'] == 'Other']
df_Prefer = df[df['gender'] == 'Prefer not to say']

total_mujeres = len(df_mujeres)
total_hombres = len(df_hombres)
total_other = len(df_Other)
total_prefer = len(df_Prefer)

conteo_mujeres = df_mujeres['genre_primary'].value_counts().reset_index()
conteo_mujeres.columns = ['Genero de pelicula', 'cantidad de Mujeres que ven ese genero']
conteo_hombres = df_hombres['genre_primary'].value_counts().reset_index()
conteo_hombres.columns = ['Genero de pelicula', 'cantidad de Hombres que ven ese genero']
conteo_otros = df_Other['genre_primary'].value_counts().reset_index()
conteo_otros.columns = ['Genero de pelicula', 'cantidad de otros que ven ese genero']
conteo_prefer = df_Prefer['genre_primary'].value_counts().reset_index()
conteo_prefer.columns = ['Genero de pelicula', 'cantidad de Prefer not to say que ven ese genero']

df_temporal = pd.merge(conteo_mujeres, conteo_hombres, on='Genero de pelicula')
df_temporal['promedio mujeres que ven ese genero'] = (df_temporal['cantidad de Mujeres que ven ese genero'] / total_mujeres * 100).round(2).astype(str) + '%'
df_temporal['promedio hombres que ven ese genero'] = (df_temporal['cantidad de Hombres que ven ese genero'] / total_hombres * 100).round(2).astype(str) + '%'
df_final = pd.merge(df_temporal, conteo_otros, on='Genero de pelicula')
df_final['promedio otros que ven ese genero'] = (df_final['cantidad de otros que ven ese genero'] / total_other * 100).round(2).astype(str) + '%'
df_final = pd.merge(df_final, conteo_prefer, on='Genero de pelicula')
df_final['promedio Prefer not to say que ven ese genero'] = (df_final['cantidad de Prefer not to say que ven ese genero'] / total_prefer * 100).round(2).astype(str) + '%'

df_final['Total'] = df_final[['cantidad de Mujeres que ven ese genero',
                             'cantidad de Hombres que ven ese genero', ...
```

Separa el dataset en cuatro grupos por género del usuario y calcula el conteo y porcentaje de visualizaciones por género de contenido para cada grupo. Luego une todo con `merge()` en un solo DataFrame (`df_final`) que permite comparar preferencias entre grupos en una sola tabla.

---

### 9. Top 3 por grupo de género

```python
# 1. Top 3 Mujeres
top3_mujeres = df_final[['Genero de pelicula', 'cantidad de Mujeres que ven ese genero', 'promedio mujeres que ven ese genero']] \
    .sort_values(by='cantidad de Mujeres que ven ese genero', ascending=False).head(3)

# 2. Top 3 Hombres
top3_hombres = df_final[['Genero de pelicula', 'cantidad de Hombres que ven ese genero', 'promedio hombres que ven ese genero']] \
    .sort_values(by='cantidad de Hombres que ven ese genero', ascending=False).head(3)

# 3. Top 3 Otros
top3_otros = df_final[['Genero de pelicula', 'cantidad de otros que ven ese genero', 'promedio otros que ven ese genero']] \
    .sort_values(by='cantidad de otros que ven ese genero', ascending=False).head(3)

# 4. Top 3 Prefer not to say
top3_prefer = df_final[['Genero de pelicula', 'cantidad de Prefer not to say que ven ese genero', 'promedio Prefer not to say que ven ese genero']] \
    .sort_values(by='cantidad de Prefer not to say que ven ese genero', ascending=False).head(3)

print("TOP 3: PREFERENCIAS POR SEXO")
print("MUJERES:")
display(top3_mujeres)
print("HOMBRES:")
display(top3_hombres)
print("OTROS:")
display(top3_otros)
print("PREFIEREN NO DECIR:")
display(top3_prefer)
```

Extrae los 3 géneros más vistos para cada grupo usando `sort_values().head(3)` sobre el `df_final` construido en la celda anterior. Permite identificar perfiles de consumo diferenciados: Historia y Aventura dominan en todos los grupos, con leves variaciones.

---

### 10. Tiempo de visualización promedio por género

```python
genre_analysis = df.groupby('genre_primary').agg(
    average_watch_time=('watch_duration_minutes', 'mean'),
    total_watch_time=('watch_duration_minutes', 'sum'),
    content_count=('watch_duration_minutes', 'count'),
).reset_index()

genre_analysis_sorted = genre_analysis.sort_values(by='average_watch_time', ascending=False)

display(genre_analysis_sorted.head(20))
```

Calcula por género el tiempo promedio de visualización, el tiempo total acumulado y la cantidad de registros, usando `.agg()`. Es la base para el modelo de score de géneros recomendados que se construye en celdas posteriores.

---

### 11. Tasa de abandono global

```python
df[df['progress_percentage'] < 40]
tasa_de_abandono = (len(df[df['progress_percentage'] < 40]) / len(df))*100
print(tasa_de_abandono)
```

Calcula qué porcentaje del total de sesiones terminaron antes del 40% del contenido. Es un número de referencia general antes de hacer el análisis por género (gráfico 3). Nota: el gráfico posterior usa un umbral del 90%, que es más estricto y más representativo.

---

### 12. Configuración visual estilo Netflix

```python
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
import warnings
import logging

logging.getLogger('matplotlib.font_manager').setLevel(logging.ERROR)
warnings.filterwarnings("ignore", category=UserWarning)

plt.style.use('dark_background')
plt.rcParams['font.family'] = 'DejaVu Sans'
plt.rcParams['axes.facecolor'] = '#000000'
plt.rcParams['figure.facecolor'] = '#000000'

netflix_red = '#E50914'
dark_grey = '#333333'
light_grey = '#888888'

print("Configuración lista. Los avisos de fuentes han sido desactivados.")
```

Importa las librerías necesarias y define la paleta de colores y estilo visual (fondo negro, rojo Netflix `#E50914`). También silencia los warnings de fuentes de Matplotlib que aparecen en Colab. Esta celda debe ejecutarse antes de cualquier gráfico.

---

### 13. Separación por tipo de contenido

```python
df_peliculas = df[df['content_type'] == 'Movie'].copy()
df_series = df[df['content_type'] == 'TV Series'].copy()
df_miniseries = df[df['content_type'] == 'Limited Series'].copy()
df_documentales = df[df['content_type'] == 'Documentary'].copy()
df_standup = df[df['content_type'] == 'Stand-up Comedy'].copy()
```

Crea DataFrames separados para cada tipo de contenido de la plataforma. Permite hacer análisis específicos por formato (por ejemplo, el histograma de duración solo aplica a películas). Solo `df_peliculas` se usa en el gráfico de duración.

---

### 14. Score de géneros recomendados (modelo ponderado v1)

```python
import pandas as pd
import numpy as np

genre_analysis = df.groupby('genre_primary').agg(
    average_watch_time=('watch_duration_minutes', 'mean'),
    total_watch_time=('watch_duration_minutes', 'sum'),
    content_count=('watch_duration_minutes', 'count')
).reset_index()

# VARIABLE 1: Volumen de Consumo (Peso: 0.6)
max_tiempo = genre_analysis['total_watch_time'].max()
genre_analysis['score_volumen'] = (genre_analysis['total_watch_time'] / max_tiempo) * 100

# VARIABLE 2: Segmentación por Duración Óptima (Peso: 0.4)
def calcular_score_duracion_real(minutos):
    if 90 <= minutos <= 150:
        return 100
    elif 40 <= minutos < 90:
        return 50
    else:
        return 0

genre_analysis['score_duracion'] = genre_analysis['average_watch_time'].apply(calcular_score_duracion_real)

# SCORE FINAL
genre_analysis['SCORE_FINAL'] = (genre_analysis['score_volumen'] * 0.6) + (genre_analysis['score_duracion'] * 0.4)
genre_analysis['SCORE_FINAL'] = genre_analysis['SCORE_FINAL'].round(2)

top_generos_recomendados = genre_analysis.sort_values(by='SCORE_FINAL', ascending=False)
print("--- TOP GÉNEROS RECOMENDADOS (BASADO EN DURACIÓN ÓPTIMA) ---")
display(top_generos_recomendados[['genre_primary', 'score_volumen', 'score_duracion', 'SCORE_FINAL']].head(10))
```

Construye un modelo de scoring con dos variables ponderadas: volumen de consumo total (60%) y duración promedio óptima (40%). La duración óptima se define en rangos inspirados en el histograma del gráfico de duración. El resultado es un ranking de géneros más recomendables para la plataforma.

---

### 15. Gráfico: Composición del catálogo (dona)

```python
# Gráfico 5: Distribución de Contenido (Dona Centrada y Limpia)
fig5, ax5 = plt.subplots(figsize=(10, 8))

conteo_tipo = df[c_tipo].value_counts()
colores = [n_red, '#444444']
total_t = sum(conteo_tipo.values)

explode = [0.0] * len(conteo_tipo)
if len(conteo_tipo) > 0:
    explode[0] = 0.05
explode = tuple(explode)

wedges, texts, autotexts = ax5.pie(
    conteo_tipo.values,
    labels=conteo_tipo.index,
    autopct=lambda pct: f'{pct:.1f}%\n({int(round(pct * total_t / 100.0)):,})',
    startangle=90,
    colors=colores,
    pctdistance=0.70,
    labeldistance=1.1,
    explode=explode,
    wedgeprops={'linewidth': 2, 'edgecolor': 'black'}
)

for text in texts:
    text.set_color('white')
    text.set_fontsize(16)
    text.set_fontweight('bold')

for autotext in autotexts:
    autotext.set_color('white')
    autotext.set_fontsize(14)
    autotext.set_fontweight('bold')

centre_circle = plt.Circle((0,0), 0.55, fc='black')
ax5.add_artist(centre_circle)

ax5.text(0, 0.1, "TOTAL", ha='center', va='center', color=n_light_grey, fontsize=16, fontweight='bold')
ax5.text(0, -0.1, f"{total_t:,}", ha='center', va='center', color='white', fontsize=35, fontweight='bold')

plt.suptitle('COMPOSICIÓN DEL CATÁLOGO: PELÍCULAS VS SERIES', color='white', fontsize=22, fontweight='bold', y=0.98)
plt.tight_layout()
plt.show()
```

Genera un gráfico de dona que muestra la proporción de películas vs. series en el catálogo, con el total de títulos en el centro. Usa `ax5.pie()` con `wedgeprops` para el formato dona y un `Circle` superpuesto para el hueco. Las etiquetas muestran porcentaje y cantidad absoluta simultáneamente.

---

### 16. Gráfico: Distribución de duración de películas

```python
# Gráfico 1: Distribución de Duración con nuevos rangos (0-45, 45-90, etc.)
fig1, ax1 = plt.subplots(figsize=(12, 6))

df_movies = df[df[c_tipo] == valor_movie].copy()
df_movies['dur_num'] = pd.to_numeric(
    df_movies[c_duracion].astype(str).str.replace(' min', '', regex=False), errors='coerce'
).fillna(0).astype(int)

def cat_dur(min):
    if min <= 45: return '0-45 min'
    elif min <= 90: return '45-90 min'
    elif min <= 135: return '90-135 min'
    elif min <= 180: return '135-180 min'
    else: return '+180 min'

df_movies['rango'] = df_movies['dur_num'].apply(cat_dur)
orden_rangos = ['0-45 min', '45-90 min', '90-135 min', '135-180 min', '+180 min']
frec_dur = df_movies['rango'].value_counts().reindex(orden_rangos).fillna(0)

ax1.bar(frec_dur.index, frec_dur.values, color='#E50914', width=0.75, zorder=3)
ax1.grid(axis='y', linestyle='--', alpha=0.3, zorder=0)
ax1.spines['top'].set_visible(False)
ax1.spines['right'].set_visible(False)
ax1.set_ylabel('CANTIDAD DE TÍTULOS', color='#888888', fontweight='bold', labelpad=15)
ax1.set_xlabel('RANGOS DE DURACIÓN (BLOQUES DE 45 MIN)', color='#888888', fontweight='bold', labelpad=15)

plt.suptitle('DISTRIBUCIÓN DE DURACIÓN: CATÁLOGO DE PELÍCULAS', color='white', fontsize=22, fontweight='bold', y=1.02)
plt.title('Análisis de frecuencia basado en bloques temporales de 45 minutos', color='#888888', fontsize=12, pad=15)

for i, v in enumerate(frec_dur.values):
    ax1.text(i, v + (max(frec_dur.values)*0.015), f"{int(v):,}", color='white', ha='center', fontweight='bold', fontsize=11)

plt.tight_layout()
plt.show()
```

Histograma de frecuencias que categoriza las películas en rangos de 45 minutos. Primero limpia la columna de duración (puede venir como texto `"90 min"`), luego aplica una función para asignar cada película a su rango. Revela que la mayoría del catálogo se concentra en el rango 90-135 minutos.

---

### 17. Gráfico: Volumen de consumo por género

```python
# Gráfico 2: Volumen de Consumo por Género
fig2, ax2 = plt.subplots(figsize=(12, 7))

totales_gen = df[c_genero].value_counts().head(10)
generos = totales_gen.index[::-1]
valores = totales_gen.values[::-1]

bars2 = ax2.barh(generos, valores, color='#E50914', height=0.6, zorder=3)
ax2.grid(axis='x', linestyle='--', alpha=0.3, zorder=0)
ax2.spines['top'].set_visible(False)
ax2.spines['right'].set_visible(False)
ax2.spines['left'].set_visible(False)
ax2.set_xlabel('NÚMERO TOTAL DE VISUALIZACIONES', color='#888888', fontweight='bold', labelpad=15)

plt.suptitle('VOLUMEN DE CONSUMO POR GÉNERO', color='white', fontsize=22, fontweight='bold', y=1.02)
plt.title('Top 10 categorías con mayor demanda en la plataforma', color='#888888', fontsize=12, pad=15)

for bar in bars2:
    width = bar.get_width()
    ax2.text(width + (max(valores)*0.01), bar.get_y() + bar.get_height()/2, f'{int(width):,}',
             va='center', ha='left', color='white', fontweight='bold', fontsize=11)

plt.tight_layout()
plt.show()
```

Gráfico de barras horizontales con los 10 géneros más vistos por cantidad de registros. Invierte el orden con `[::-1]` para que el mayor quede arriba. Cada barra muestra su valor exacto como etiqueta flotante a la derecha.

---

### 18. Gráfico: Rentabilidad por género (ROI)

```python
# Gráfico 6: Rentabilidad por Género (ROI Sin Etiquetas Borrosas)
fig6, ax6 = plt.subplots(figsize=(12, 7))

df_rent = df.dropna(subset=[c_presupuesto, c_recaudacion, c_genero]).copy()
df_rent['roi'] = df_rent[c_recaudacion] / df_rent[c_presupuesto]

rentabilidad = df_rent.groupby(c_genero)['roi'].mean().sort_values(ascending=False).head(10)
generos_rent = rentabilidad.index[::-1].tolist()
roi_valores = rentabilidad.values[::-1].tolist()

bars_rent = ax6.barh(generos_rent, roi_valores, color=n_red, height=0.6, zorder=3)
ax6.grid(axis='x', linestyle='--', alpha=0.3, zorder=0)

for spine in ax6.spines.values(): spine.set_visible(False)
ax6.spines['bottom'].set_color(n_light_grey)
ax6.spines['left'].set_color(n_light_grey)
ax6.set_ylabel('Top 10 Categorías', color=n_light_grey, fontweight='bold', labelpad=15)
ax6.set_xlabel('Multiplicador de Retorno de Inversión (ROI Promedio)', color=n_light_grey, fontweight='bold', labelpad=15)

plt.suptitle('ANÁLISIS DE EFICIENCIA FINANCIERA (ROI)', color='white', fontsize=22, fontweight='bold', y=1.02)
ax6.axvline(x=1.0, color='white', linestyle=':', linewidth=2, zorder=2)

for bar in bars_rent:
    width = bar.get_width()
    ax6.text(width + (max(roi_valores)*0.01), bar.get_y() + bar.get_height()/2, f'{width:.2f}x', va='center', ha='left', color='white', fontweight='bold', fontsize=11, zorder=4)

plt.tight_layout()
plt.show()
```

Calcula el ROI promedio por género como `box_office_revenue / production_budget` y grafica el top 10 en barras horizontales. La línea punteada vertical en `x=1.0` marca el punto de equilibrio financiero (break-even). Géneros por encima recuperan más de lo que costaron producir.

---

### 19. Gráfico: Preferencias regionales Este vs. Oeste

```python
# Gráfico 4: Análisis por Costas (Totales Visibles y Tarjetas Separadas)
fig4 = plt.figure(figsize=(16, 9))
gs = fig4.add_gridspec(1, 2, width_ratios=[1.8, 1])
ax4_bars = fig4.add_subplot(gs[0])
ax4_text = fig4.add_subplot(gs[1])

def clasificar_costa(estado):
    if estado in eastern_provinces_states:
        return 'Este'
    elif estado in western_provinces_states:
        return 'Oeste'
    else:
        return 'Desconocido'

df_coast = df.dropna(subset=[c_genero, c_estado]).copy()
df_coast['region_costa'] = df_coast[c_estado].apply(clasificar_costa)

totales_cost = df_coast[c_genero].value_counts().head(10)
generos_cost = totales_cost.index[::-1].tolist()
volumen_cost = totales_cost.values[::-1].tolist()

bars_cost = ax4_bars.barh(generos_cost, volumen_cost, color=n_red, height=0.6, zorder=3)
ax4_bars.barh(generos_cost, [max(volumen_cost) * 1.1]*len(generos_cost), color='#1a1a1a', height=0.6, zorder=1)

for spine in ax4_bars.spines.values(): spine.set_visible(False)
ax4_bars.set_xticks([])
ax4_bars.tick_params(axis='y', colors='white', labelsize=11)
ax4_bars.text(0, 10.5, 'VOLUMEN DE CONSUMO Y PREFERENCIAS REGIONALES', color='white', fontsize=20, fontweight='bold')

for bar in bars_cost:
    width = bar.get_width()
    ax4_bars.text(width - (max(volumen_cost)*0.02), bar.get_y() + bar.get_height()/2, f'{int(width):,}', va='center', ha='right', color='white', fontweight='bold', fontsize=10, zorder=4)

ax4_text.axis('off')
top_este = df_coast[df_coast['region_costa'] == 'Este'][c_genero].value_counts().head(3)
top_oeste = df_coast[df_coast['region_costa'] == 'Oeste'][c_genero].value_counts().head(3)

total_peliculas_este = len(df_coast[df_coast['region_costa'] == 'Este'])
total_peliculas_oeste = len(df_coast[df_coast['region_costa'] == 'Oeste'])

def crear_tarjeta_costa(ax, y_pos, titulo, items, total_visto):
    # ...
```

Usa `GridSpec` para dividir la figura en dos paneles: barras horizontales con volumen total (izquierda) y tarjetas de texto con el top 3 por región (derecha). La función `clasificar_costa()` asigna cada fila a Este, Oeste o Desconocido. Es el gráfico más complejo visualmente del proyecto.

---

### 20. Gráfico: Tasa de abandono por género

```python
# Gráfico 3: Tasa de Abandono (< 90% de la duración)
fig3, ax3 = plt.subplots(figsize=(12, 6))

df_aba = df.dropna(subset=[c_duracion, c_vista, c_genero]).copy()

df_aba['abandono_real'] = df_aba[c_vista] < (df_aba[c_duracion] * 0.90)

tasa_abandono = df_aba.groupby(c_genero)['abandono_real'].mean() * 100
peores = tasa_abandono.nlargest(3).sort_values(ascending=True)
mejores = tasa_abandono.nsmallest(3).sort_values(ascending=True)

generos_aba = mejores.index.tolist() + peores.index.tolist()
tasas_aba = mejores.values.tolist() + peores.values.tolist()
colores_aba = [n_green, n_green, n_green, n_red, n_red, n_red]

bars_aba = ax3.barh(generos_aba, tasas_aba, color=colores_aba, height=0.6, zorder=3)
ax3.barh(generos_aba, [100]*len(generos_aba), color='#1a1a1a', height=0.6, zorder=1)
ax3.axhline(y=2.5, color='#444444', linestyle='--', linewidth=2)

for spine in ax3.spines.values(): spine.set_visible(False)
ax3.set_xlabel('Tasa de Abandono (% que vió menos del 90% del título)', color=n_light_grey, fontweight='bold')
plt.suptitle('TASA DE ABANDONO POR GÉNERO', color='white', fontsize=22, fontweight='bold', y=1.02)
plt.title('Top 3 géneros con mayor fidelidad (verde) vs. Top 3 con mayor deserción (rojo)', color=n_light_grey, fontsize=14, pad=20)

for bar in bars_aba:
    width = bar.get_width()
    ax3.text(width + 1, bar.get_y() + bar.get_height()/2, f'{width:.1f}%', va='center', ha='left', color='white', fontweight='bold', fontsize=12)

plt.tight_layout()
plt.show()
```

Define abandono como sesiones donde el tiempo visto es menor al 90% de la duración del título. Calcula la tasa por género y muestra los 3 con mayor fidelidad (verde) y los 3 con mayor deserción (rojo) en el mismo gráfico. El Crimen retiene mejor; la Fantasía pierde más usuarios antes de terminar.

---

### 21. Score de géneros recomendados (modelo ponderado v2)

```python
# Creamos la columna 'score' sumando tus 3 variables multiplicadas por sus pesos
genre_analysis['score'] = (
    genre_analysis['average_watch_time'] * 0.2 +
    genre_analysis['total_watch_time'] * 0.5 +
    genre_analysis['content_count'] * 0.3
)

genre_analysis_sorted = genre_analysis.sort_values(by='score', ascending=False)
display(genre_analysis_sorted.head(20))

display(genre_analysis_sorted[["genre_primary","score"]].head(20))
```

Segunda versión del modelo de scoring, con tres variables: tiempo promedio (20%), tiempo total (50%) y cantidad de contenidos (30%). A diferencia de la v1, no normaliza los valores antes de sumar, por lo que el `total_watch_time` —que tiene valores muy grandes— domina el score. Es válida como comparación pero la v1 es más robusta metodológicamente.

---

### 22. Carga del dataset de sueño

```python
from google.colab import files
uploaded = files.upload()

import pandas as pd
df2 = pd.read_csv('sleep_health_dataset.csv')
```

Carga el segundo dataset (salud del sueño) en `df2` para el análisis cruzado. Este dataset tiene 374 registros y se filtra en la celda siguiente.

---

### 23. Filtrado por país (USA y Canadá)

```python
df2 = df2[df2['country'].isin(['USA', 'Canada'])]
display(f'Registros de países trabajados: {len(df2)}')
display(df2['country'].value_counts())

print(f'Total registros: {len(df2)}')
print(f'Países en el dataset: {df2["country"].unique()}')

df2['country'].value_counts()
```

Filtra `df2` para trabajar solo con registros de USA y Canadá, que son los países que también están presentes en el dataset de Netflix, facilitando el cruce posterior.

---

### 24. Merge Netflix + Sueño

```python
pd.merge(df, df2, on="age", how="inner")
```

Une ambos datasets por la columna `age` (edad), que es la variable compartida entre los dos. El `how="inner"` devuelve solo los registros donde la edad aparece en ambas tablas. Es el punto de conexión entre el comportamiento de consumo en Netflix y los indicadores de calidad del sueño.

---


Proyecto académico — no afiliado a Netflix Inc.*
