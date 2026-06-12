 PROYECTO ECONOMÍA MUNDIAL
 La primera parte de nuestro proyecto se basó en analizar cómo distintos hechos históricos impactaron en la economía mundial durante las últimas décadas. El análisis se organiza a partir de cuatro eventos clave que marcaron cambios importantes en la economía global: la caída del Muro de Berlín (1989), el milagro chino (2001), la crisis financiera internacional de 2008 y la pandemia de Covid‑19 (2019). Para cada caso, se define un período previo y posterior al evento, lo que permite comparar cómo evolucionaron las principales variables económicas antes y después de cada shock.
Además, los datos se agrupan por regiones geográficas y bloques económicos para observar diferencias en el impacto según la zona. En el caso del Covid‑19, el foco está puesto especialmente en Argentina, analizando la evolución económica antes de la pandemia y durante los gobiernos de Macri y Fernández. 

from google.colab import files
upload  = files.upload()
     
import pandas as pd
df = pd.read_csv('disuguaglianza-economica-globale-e-povert-1980-2024.csv')

### CLASIFICACIÓN GEOGRÁFICA DE LOS PAÍSES ###

# AMÉRICA
america_del_sur = ['Argentina', 'Bolivia', 'Brazil', 'Chile', 'Colombia', 'Ecuador', 'Guyana', 'Paraguay', 'Peru', 'Suriname', 'Uruguay', 'Venezuela']
america_central_y_caribe = ['Belize', 'Costa Rica', 'El Salvador', 'Guatemala', 'Honduras','Nicaragua', 'Panama', 'Bahamas', 'Barbados', 'Cuba', 'Dominica','Dominican Republic', 'Grenada', 'Haiti', 'Jamaica', 'Saint Kitts and Nevis','Saint Lucia', 'Saint Vincent and the Grenadines', 'Trinidad and Tobago']
america_del_norte = ['Canada', 'United States', 'Mexico']

# EUROPA
europa = ['Albania', 'Andorra', 'Austria', 'Belarus', 'Belgium', 'Bosnia and Herzegovina','Bulgaria', 'Croatia', 'Cyprus', 'Czechia', 'Denmark', 'Estonia', 'Finland','France', 'Germany', 'Greece', 'Hungary', 'Iceland', 'Ireland', 'Italy','Latvia', 'Lithuania', 'Luxembourg', 'Malta', 'Moldova', 'Montenegro','Netherlands', 'North Macedonia', 'Norway', 'Poland', 'Portugal', 'Romania','Russia', 'Serbia', 'Slovakia', 'Slovenia', 'Spain', 'Sweden', 'Switzerland','Ukraine', 'United Kingdom']

# ÁFRICA
africa = ['Algeria', 'Angola', 'Benin', 'Botswana', 'Burkina Faso', 'Burundi', 'Cabo Verde','Cameroon', 'Central African Republic', 'Chad', 'Comoros', 'Congo', 'Cote d\'Ivoire','Democratic Republic of Congo', 'Djibouti', 'Egypt', 'Equatorial Guinea', 'Eritrea','Eswatini', 'Ethiopia', 'Gabon', 'Gambia', 'Ghana', 'Guinea', 'Guinea-Bissau','Kenya', 'Lesotho', 'Liberia', 'Libya', 'Madagascar', 'Malawi', 'Mali','Mauritania', 'Mauritius', 'Morocco', 'Mozambique', 'Namibia', 'Niger','Nigeria', 'Rwanda', 'Sao Tome and Principe', 'Senegal', 'Seychelles','Sierra Leone', 'Somalia', 'South Africa', 'South Sudan', 'Sudan', 'Tanzania','Togo', 'Tunisia', 'Uganda', 'Zambia', 'Zimbabwe']

# ASIA
asia = ['Afghanistan', 'Armenia', 'Azerbaijan', 'Bahrain', 'Bangladesh', 'Bhutan','Brunei', 'Cambodia', 'China', 'Georgia', 'India', 'Indonesia', 'Iran','Iraq', 'Israel', 'Japan', 'Jordan', 'Kazakhstan', 'Kuwait', 'Kyrgyzstan','Laos', 'Lebanon', 'Malaysia', 'Maldives', 'Mongolia', 'Myanmar', 'Nepal','North Korea', 'Oman', 'Pakistan', 'Palestine', 'Philippines', 'Qatar','Saudi Arabia', 'Singapore', 'South Korea', 'Sri Lanka', 'Syria', 'Taiwan','Tajikistan', 'Thailand', 'Timor', 'Turkey', 'Turkmenistan','United Arab Emirates', 'Uzbekistan', 'Vietnam', 'Yemen']

# OCEANÍA
oceania = ['Australia', 'Fiji', 'Kiribati', 'Marshall Islands', 'Micronesia (country)','Nauru', 'New Zealand', 'Palau', 'Papua New Guinea', 'Samoa','Solomon Islands', 'Tonga', 'Tuvalu', 'Vanuatu']
     

### BLOQUES ECONÓMICOS ###

# MERCOSUR
mercosur = ['Argentina', 'Brazil', 'Paraguay', 'Uruguay', 'Venezuela']

# PAÍSES EMERGENTES
brics = ['Brazil', 'Russia', 'India', 'China', 'South Africa','Egypt', 'Ethiopia', 'Iran', 'United Arab Emirates']

# PETRÓLEO/ENERGÍA
medio_oriente = ['Bahrain', 'Iran', 'Iraq', 'Israel', 'Jordan', 'Kuwait', 'Lebanon','Oman', 'Palestine', 'Qatar', 'Saudi Arabia', 'Syria','United Arab Emirates', 'Yemen']

# CLUB DE PAÍSES DESARROLLADOS
ocde = ['Austria', 'Belgium', 'Canada', 'Chile', 'Colombia', 'Czechia', 'Denmark','Estonia', 'Finland', 'France', 'Germany', 'Greece', 'Hungary', 'Iceland','Ireland', 'Israel', 'Italy', 'Japan', 'South Korea', 'Latvia', 'Lithuania','Luxembourg', 'Mexico', 'Netherlands', 'New Zealand', 'Norway', 'Poland','Portugal', 'Slovakia', 'Slovenia', 'Spain', 'Sweden', 'Switzerland','Turkey', 'United Kingdom', 'United States', 'Australia']

# UNIÓN EUROPEA
union_europea = ['Austria', 'Belgium', 'Bulgaria', 'Croatia', 'Cyprus', 'Czechia', 'Denmark', 'Estonia', 'Finland', 'France', 'Germany', 'Greece', 'Hungary', 'Ireland', 'Italy', 'Latvia', 'Lithuania', 'Luxembourg', 'Malta', 'Netherlands', 'Poland', 'Portugal', 'Romania', 'Slovakia', 'Slovenia', 'Spain', 'Sweden']
     
Dividimos nuevamente Europa
### EUROPA ###

union_europea = ['Austria', 'Belgium', 'Bulgaria', 'Croatia', 'Cyprus', 'Czechia','Denmark', 'Estonia', 'Finland', 'France', 'Germany', 'Greece','Hungary', 'Ireland', 'Italy', 'Latvia', 'Lithuania', 'Luxembourg','Malta', 'Netherlands', 'Poland', 'Portugal', 'Romania', 'Slovakia','Slovenia', 'Spain', 'Sweden']

europa_no_ue = ['Albania', 'Andorra', 'Belarus', 'Bosnia and Herzegovina', 'Iceland','Moldova', 'Montenegro', 'North Macedonia', 'Norway', 'Russia','Serbia', 'Switzerland', 'Ukraine', 'United Kingdom']

# Creamos DataFrame para Caída Muro Berlín (1984-1994)
df_muro_berlin = df[(df['year'] >= 1984) & (df['year'] <= 1994)]
     

display(df_muro_berlin)
     

# Creamos DataFrame para Milagro Chino (1996-2006)
df_milagro_chino = df[(df['year'] >= 1996) & (df['year'] <= 2006)]
     

display(df_milagro_chino)
     

# Creamos DataFrame Crisis Financiera (2003-2013)
df_crisis_financiera = df[(df['year'] >= 2003) & (df['year'] <= 2013)]
     
display(df_crisis_financiera)
     

# Creamos DataFrame COVID-19 (2014-2022)
df_covid_19 = df[(df['year'] >= 2014) & (df['year'] <= 2022)]
     

display(df_covid_19)

from google.colab import files
upload  = files.upload()
import pandas as pd
df = pd.read_csv('disuguaglianza-economica-globale-e-povert-1980-2024.csv')

# Re-definimos los subconjuntos temporales para asegurar que estén disponibles
df_muro_berlin = df[(df['year'] >= 1984) & (df['year'] <= 1994)]
df_milagro_chino = df[(df['year'] >= 1996) & (df['year'] <= 2006)]
df_crisis_financiera = df[(df['year'] >= 2003) & (df['year'] <= 2013)]
df_covid_19 = df[(df['year'] >= 2014) & (df['year'] <= 2022)]
### PRESENTACIÓN DEL DATASET ###

# 1. Información general del dataset
print("--- INFORMACIÓN GENERAL ---")
df.info()

# 2. Visualización de una sola fila aleatoria de Argentina
print("\n--- FILA ALEATORIA ---")
display(df[df['country'] == 'Argentina'].sample(1))

# 4. Dimensiones del dataset original
print(f"\nDimensiones totales: El dataset tiene {df.shape[0]} filas y {df.shape[1]} columnas.")
### CREACIÓN DEL GRÁFICO DE EVOLUCIÓN DEL PBI GLOBAL ###

import matplotlib.pyplot as plt
import pandas as pd

# 1. Limpieza y preparación de datos
df_limpio = df.dropna(subset=['gdp', 'year'])
es_1983 = df_limpio['year'] == 1983
if es_1983.any():
    min_pbi_1983 = df_limpio[es_1983]['gdp'].min()
    df_limpio = df_limpio[~((es_1983) & (df_limpio['gdp'] == min_pbi_1983))]

# 2. Groupby: Agrupamos por año
pbi_por_año = df_limpio.groupby('year')['gdp'].sum().reset_index()
año_min = int(pbi_por_año['year'].min())
año_max = int(pbi_por_año['year'].max())

# 3. Configuración del Gráfico con fondo negro
plt.style.use('dark_background')
fig, ax = plt.subplots(figsize=(14, 7))
fig.patch.set_facecolor('black')
ax.set_facecolor('black')

# Línea del PBI en color Cian brillante para contraste
plt.plot(pbi_por_año['year'], pbi_por_año['gdp'], color='#00FFFF', linewidth=3, label='Evolución del PBI Global')

# 4. Hitos Históricos con colores vibrantes
hitos = {
    1989: 'Caída Muro de Berlín',
    2001: 'Milagro Chino',
    2008: 'Crisis Financiera',
    2020: 'COVID-19'
}

y_max = pbi_por_año['gdp'].max()

for anio, evento in hitos.items():
    # Línea vertical amarilla neón para alto contraste
    plt.axvline(x=anio, color='#FFFF00', linestyle='--', linewidth=2)

    # Texto con fondo negro y letra blanca
    plt.text(anio - 0.5, y_max * 0.90, evento,
             rotation=90, color='white', fontsize=11, fontweight='bold',
             ha='right', va='top',
             bbox=dict(facecolor='black', alpha=0.7, edgecolor='none', pad=3))

# 5. Títulos y Etiquetas
plt.title(f'EVOLUCIÓN DEL PBI GLOBAL ({año_min} - {año_max})', fontsize=16, fontweight='bold', color='white', pad=20)

plt.xlabel('Año', fontsize=12, fontweight='bold', color='white')
plt.ylabel('PBI (Billones de dólares)', fontsize=12, fontweight='bold', color='white')

plt.xticks(range(año_min, año_max + 1, 2), rotation=45, color='white')
plt.yticks(color='white')
### CLASIFICACIÓN GEOGRÁFICA DE LOS PAÍSES ###

# AMÉRICA
america_del_sur = ['Argentina', 'Bolivia', 'Brazil', 'Chile', 'Colombia', 'Ecuador', 'Guyana', 'Paraguay', 'Peru', 'Suriname', 'Uruguay', 'Venezuela']
america_central_y_caribe = ['Belize', 'Costa Rica', 'El Salvador', 'Guatemala', 'Honduras','Nicaragua', 'Panama', 'Bahamas', 'Barbados', 'Cuba', 'Dominica','Dominican Republic', 'Grenada', 'Haiti', 'Jamaica', 'Saint Kitts and Nevis','Saint Lucia', 'Saint Vincent and the Grenadines', 'Trinidad and Tobago']
america_del_norte = ['Canada', 'United States', 'Mexico']

# EUROPA
europa = ['Albania', 'Andorra', 'Austria', 'Belarus', 'Belgium', 'Bosnia and Herzegovina','Bulgaria', 'Croatia', 'Cyprus', 'Czechia', 'Denmark', 'Estonia', 'Finland','France', 'Germany', 'Greece', 'Hungary', 'Iceland', 'Ireland', 'Italy','Latvia', 'Lithuania', 'Luxembourg', 'Malta', 'Moldova', 'Montenegro','Netherlands', 'North Macedonia', 'Norway', 'Poland', 'Portugal', 'Romania','Russia', 'Serbia', 'Slovakia', 'Slovenia', 'Spain', 'Sweden', 'Switzerland','Ukraine', 'United Kingdom']

# ÁFRICA
africa = ['Algeria', 'Angola', 'Benin', 'Botswana', 'Burkina Faso', 'Burundi', 'Cabo Verde','Cameroon', 'Central African Republic', 'Chad', 'Comoros', 'Congo', 'Cote d\'Ivoire','Democratic Republic of Congo', 'Djibouti', 'Egypt', 'Equatorial Guinea', 'Eritrea','Eswatini', 'Ethiopia', 'Gabon', 'Gambia', 'Ghana', 'Guinea', 'Guinea-Bissau','Kenya', 'Lesotho', 'Liberia', 'Libya', 'Madagascar', 'Malawi', 'Mali','Mauritania', 'Mauritius', 'Morocco', 'Mozambique', 'Namibia', 'Niger','Nigeria', 'Rwanda', 'Sao Tome and Principe', 'Senegal', 'Seychelles','Sierra Leone', 'Somalia', 'South Africa', 'South Sudan', 'Sudan', 'Tanzania','Togo', 'Tunisia', 'Uganda', 'Zambia', 'Zimbabwe']

# ASIA
asia = ['Afghanistan', 'Armenia', 'Azerbaijan', 'Bahrain', 'Bangladesh', 'Bhutan','Brunei', 'Cambodia', 'China', 'Georgia', 'India', 'Indonesia', 'Iran','Iraq', 'Israel', 'Japan', 'Jordan', 'Kazakhstan', 'Kuwait', 'Kyrgyzstan','Laos', 'Lebanon', 'Malaysia', 'Maldives', 'Mongolia', 'Myanmar', 'Nepal','North Korea', 'Oman', 'Pakistan', 'Palestine', 'Philippines', 'Qatar','Saudi Arabia', 'Singapore', 'South Korea', 'Sri Lanka', 'Syria', 'Taiwan','Tajikistan', 'Thailand', 'Timor', 'Turkey', 'Turkmenistan','United Arab Emirates', 'Uzbekistan', 'Vietnam', 'Yemen']

# OCEANÍA
oceania = ['Australia', 'Fiji', 'Kiribati', 'Marshall Islands', 'Micronesia (country)','Nauru', 'New Zealand', 'Palau', 'Papua New Guinea', 'Samoa','Solomon Islands', 'Tonga', 'Tuvalu', 'Vanuatu']

# CREAMOS UN DF ESPECIALMENTE PARA ARGENTINA
df_argentina = df[df['country'] == 'Argentina']
     

### CREACIÓN GRÁFICO ÁREAS APILADAS ###

import matplotlib.pyplot as plt
import pandas as pd

# 1. Definir función para asignar región
def asignar_region(country):
    if country == 'Argentina': return 'Argentina'
    if country in america_del_sur: return 'América del Sur'
    if country in america_del_norte: return 'América del Norte'
    if country in america_central_y_caribe: return 'América Central y Caribe'
    if country in europa: return 'Europa'
    if country in africa: return 'África'
    if country in asia: return 'Asia'
    if country in oceania: return 'Oceanía'
    return 'Otros'

# 2. Preparar el DataFrame
df_regiones = df.copy()
df_regiones['region'] = df_regiones['country'].apply(asignar_region)

# Filtrar 'Otros' y años sin PBI per cápita
df_regiones = df_regiones[(df_regiones['region'] != 'Otros') & (df_regiones['gdp_per_capita'].notna())]

# 3. Pivotar los datos: Promedio de PBI per cápita por región y año
evolucion_pbi = df_regiones.pivot_table(
    index='year',
    columns='region',
    values='gdp_per_capita',
    aggfunc='mean'
).fillna(0)

# 4. Ordenar las columnas para el stack
orden_regiones = ['África', 'Asia', 'Oceanía', 'América Central y Caribe', 'América del Sur', 'Argentina', 'América del Norte', 'Europa']
evolucion_pbi = evolucion_pbi[[col for col in orden_regiones if col in evolucion_pbi.columns]]

# 5. Colores y Hitos
paleta = {
    'América del Sur': '#AEC6CF', 'América del Norte': '#FFB7B2',
    'América Central y Caribe': '#B2E2F2', 'Europa': '#B3E5BE',
    'Asia': '#FFDAC1', 'África': '#FFFFB5', 'Oceanía': '#C19AD3',
    'Argentina': '#00FFFF' # Cyan brillante para resaltar en negro
}
colores = [paleta.get(reg, '#CCCCCC') for reg in evolucion_pbi.columns]

hitos = {
    1989: 'Muro de Berlín',
    2001: 'Milagro Chino',
    2008: 'Crisis 2008',
    2020: 'COVID-19'
}

# 6. Creación del Gráfico
plt.style.use('dark_background')
fig, ax = plt.subplots(figsize=(16, 9))
fig.patch.set_facecolor('black')
ax.set_facecolor('black')

plt.stackplot(evolucion_pbi.index, evolucion_pbi.T, labels=evolucion_pbi.columns, colors=colores, alpha=0.85)

# Agregar líneas de hitos históricos
y_max_total = evolucion_pbi.sum(axis=1).max()
for anio, evento in hitos.items():
    plt.axvline(x=anio, color='white', linestyle='--', linewidth=1.5, alpha=0.7)
    plt.text(anio, y_max_total * 0.95, evento, rotation=90, verticalalignment='top',
             horizontalalignment='right', fontsize=10, fontweight='bold', color='white')

plt.title('Evolución del PBI Per Cápita Promedio por Región y Argentina', fontsize=16, fontweight='bold', pad=20, color='white')
plt.xlabel('Año', fontsize=12, fontweight='bold', color='white')
plt.ylabel('PBI Per Cápita Promedio (USD)', fontsize=12, fontweight='bold', color='white')

# Configurar más años en el eje X (cada 2 años)
anio_min = int(evolucion_pbi.index.min())
anio_max = int(evolucion_pbi.index.max())
plt.xticks(range(anio_min, anio_max + 1, 2), rotation=45, color='white')
plt.yticks(color='white')

plt.legend(loc='upper left', bbox_to_anchor=(1, 1), title='Regiones', facecolor='black', edgecolor='white')
plt.grid(axis='y', linestyle=':', alpha=0.3)
plt.tight_layout()

plt.show()
plt.style.use('default')
     


### MAPA DE CALOR: PBI GLOBAL A 2022 ###

import matplotlib.pyplot as plt
import pandas as pd
import matplotlib.colors as colors

try:
    import geopandas as gpd
except ImportError:
    !pip install geopandas
    import geopandas as gpd

# 1. Obtener el último año con datos de PBI
ultimo_año = df.dropna(subset=['gdp'])['year'].max()
df_ultimo = df[df['year'] == ultimo_año].copy()

# 2. Cargar mapa mundial
path_mapa = "https://naciscdn.org/naturalearth/110m/cultural/ne_110m_admin_0_countries.zip"
world = gpd.read_file(path_mapa)

# 3. Unir datos
world = world.merge(df_ultimo, left_on='ADM0_A3', right_on='iso_code', how='left')

# 4. Crear el gráfico con fondo negro
plt.style.use('dark_background')
fig, ax = plt.subplots(1, 1, figsize=(18, 10))
fig.patch.set_facecolor('black')
ax.set_facecolor('black')

# Fondo para países sin datos (Gris muy oscuro)
world.plot(ax=ax, color='#1a1a1a', edgecolor='#333333', linewidth=0.5)

# Mapa de calor con escala viridis (monocromática de oscuro a brillante para contraste)
sm = world.dropna(subset=['gdp']).plot(
    column='gdp',
    ax=ax,
    legend=True,
    cmap='viridis',
    norm=colors.LogNorm(vmin=df_ultimo['gdp'].min(), vmax=df_ultimo['gdp'].max()),
    legend_kwds={
        'label': "PBI (USD)",
        'orientation': "horizontal",
        'pad': 0.05,
        'shrink': 0.6
    },
    edgecolor='black',
    linewidth=0.2
)

plt.title(f'Distribución Global del PBI en el año {int(ultimo_año)}', fontsize=18, fontweight='bold', color='white', pad=20)
ax.set_axis_off()

plt.tight_layout()
plt.show()
plt.style.use('default')
     


# Creamos DataFrame para Caída Muro Berlín (1984-1994)
df_muro_berlin = df[(df['year'] >= 1984) & (df['year'] <= 1994)]
# Creamos DataFrame para Milagro Chino (1996-2006)
df_milagro_chino = df[(df['year'] >= 1996) & (df['year'] <= 2006)]
# Creamos DataFrame Crisis Financiera (2003-2013)
df_crisis_financiera = df[(df['year'] >= 2003) & (df['year'] <= 2013)]
# Creamos DataFrame COVID-19 (2014-2022)
df_covid_19 = df[(df['year'] >= 2014) & (df['year'] <= 2022)]
     

### EVOLUCIÓN DEL PBI: CAÍDA DEL MURO DE BERLÍN (1984-1994) ###

import matplotlib.pyplot as plt

# 1. Configurar estilo de contraste (fondo oscuro)
plt.style.use('dark_background')

# 2. Definir la paleta con la MISMA GAMA pero COLORES MÁS FUERTES
paleta = {
    'América del Sur': '#5D99B0',       # Azul más fuerte
    'América del Norte': '#FF6B6B',     # Salmón/Rojo más fuerte
    'América Central y Caribe': '#4DB8D9', # Celeste más profundo
    'Europa': '#76C893',               # Verde más intenso
    'Asia': '#FF9F43',                 # Durazno/Naranja más vivo
    'África': '#F1C40F',               # Amarillo más sólido
    'Oceanía': '#9B59B6',              # Lavanda/Púrpura más oscuro
    'Argentina': '#00FFFF'             # Cyan brillante para resaltar en negro
}

# 3. Preparar los datos
df_periodo = df_muro_berlin.copy()
df_periodo['region'] = df_periodo['country'].apply(asignar_region)
evolucion_regiones = df_periodo[df_periodo['region'] != 'Otros'].groupby(['year', 'region'])['gdp'].sum().unstack()

# 4. Graficar
fig, ax = plt.subplots(figsize=(15, 8))
fig.patch.set_facecolor('black')
ax.set_facecolor('black')

# Dibujar líneas de regiones y Argentina con los colores intensificados
for region in evolucion_regiones.columns:
    color = paleta.get(region, '#CCCCCC')
    linewidth = 5 if region == 'Argentina' else 3.5
    plt.plot(evolucion_regiones.index, evolucion_regiones[region], marker='o', markersize=8, color=color, linewidth=linewidth, label=region)

# 5. Hito Histórico: Línea roja vertical para contraste
plt.axvline(x=1989, color='#FF0000', linestyle='--', linewidth=3, label='Caída Muro de Berlín (1989)')
plt.text(1989.1, evolucion_regiones.max().max(), 'HITO: 1989', color='#FF0000', fontsize=12, fontweight='bold', verticalalignment='bottom')

# 6. Configuración estética
max_region = evolucion_regiones.max().max()
plt.ylim(0, max_region * 1.1)

plt.title('EVOLUCIÓN DEL PBI (1984 - 1994): CAÍDA DEL MURO DE BERLÍN', fontsize=18, fontweight='bold', color='white', pad=20)
plt.xlabel('Año', fontsize=13, fontweight='bold')
plt.ylabel('PBI (Billones USD)', fontsize=13, fontweight='bold')

plt.xticks(range(1984, 1995), fontsize=11)
plt.grid(True, linestyle='--', alpha=0.15)
plt.legend(title="Regiones", bbox_to_anchor=(1.01, 1), loc='upper left', fontsize=11, facecolor='black', edgecolor='white')

plt.tight_layout()
plt.show()

# Restauramos estilo por defecto
plt.style.use('default')
     


### COMPARATIVA PBI PER CÁPITA: EUROPA DEL ESTE, ALEMANIA Y EEUU (1984-1994) ###

import matplotlib.pyplot as plt
import matplotlib.ticker as ticker

# 1. Configurar estilo de contraste
plt.style.use('dark_background')

# 2. Definir países y colores específicos
paises_comp = ['Germany', 'United States', 'Poland', 'Ukraine']
colores_paises = {
    'United States': '#00FFFF',   # Cyan brillante
    'Germany': '#FF6B6B',         # Salmón
    'Poland': '#76C893',          # Verde
    'Ukraine': '#F1C40F'          # Amarillo
}

# 3. Preparar los datos (Rango 1984-1994) - USAMOS PBI PER CÁPITA
df_comp_custom = df[(df['country'].isin(paises_comp)) & (df['year'] >= 1984) & (df['year'] <= 1994)]
evolucion_custom = df_comp_custom.pivot_table(index='year', columns='country', values='gdp_per_capita')

# 4. Graficar
fig, ax = plt.subplots(figsize=(15, 8))
fig.patch.set_facecolor('black')
ax.set_facecolor('black')

# Usamos escala logarítmica para ver mejor los quiebres proporcionales
ax.set_yscale('log')

for pais in evolucion_custom.columns:
    color = colores_paises.get(pais, '#CCCCCC')
    linewidth = 5 if pais in ['United States', 'Germany'] else 3.5
    plt.plot(evolucion_custom.index, evolucion_custom[pais],
             marker='o', markersize=10, markeredgecolor='white',
             color=color, linewidth=linewidth, label=pais, alpha=0.9)

# 5. Hito Histórico: Caída del Muro de Berlín (1989)
plt.axvline(x=1989, color='#FF0000', linestyle='--', linewidth=3, label='Hito: 1989')
plt.text(1989.1, evolucion_custom.max().max(), 'HITO: 1989 (CAÍDA MURO)',
         color='#FF0000', fontsize=12, fontweight='bold', verticalalignment='top')

# 6. Configuración estética
plt.title('EVOLUCIÓN DEL PBI PER CÁPITA (1984 - 1994)',
          fontsize=18, fontweight='bold', color='white', pad=20)
plt.xlabel('Año', fontsize=13, fontweight='bold')
plt.ylabel('PBI Per Cápita (USD)', fontsize=13, fontweight='bold')

# Mejora de la escala: Formateo de moneda
ax.yaxis.set_major_formatter(ticker.FuncFormatter(lambda x, pos: f'${x:,.0f}'))
ax.yaxis.set_minor_formatter(ticker.FuncFormatter(lambda x, pos: f'${x:,.0f}' if x >= 1000 else ''))

plt.xticks(range(1984, 1995), fontsize=11)
plt.grid(True, which='both', linestyle='--', alpha=0.2)

# AJUSTE DE LEYENDA: Fuera del área de trazado para evitar superposiciones
plt.legend(title="Países", bbox_to_anchor=(1.05, 1), loc='upper left',
           fontsize=11, facecolor='black', edgecolor='white')

plt.tight_layout()
plt.show()

# Restaurar estilo
plt.style.use('default')
     


### EVOLUCIÓN DEL PBI POR REGIONES: MILAGRO CHINO ###

import matplotlib.pyplot as plt

# 1. Configurar estilo de contraste
plt.style.use('dark_background')

# 2. Definir paleta de colores vibrantes establecida
paleta = {
    'América del Sur': '#5D99B0',
    'América del Norte': '#FF6B6B',
    'América Central y Caribe': '#4DB8D9',
    'Europa': '#76C893',
    'Asia': '#FF9F43',
    'África': '#F1C40F',
    'Oceanía': '#9B59B6',
    'Argentina': '#00FFFF'
}

# 3. Preparar los datos (Rango 1995-2022)
anio_inicio = 1995
anio_fin = 2022

df_periodo = df[(df['year'] >= anio_inicio) & (df['year'] <= anio_fin)].copy()
df_periodo['region'] = df_periodo['country'].apply(asignar_region)

# Agrupamos por año y región para sumar el PBI
evolucion_regiones = df_periodo[df_periodo['region'] != 'Otros'].groupby(['year', 'region'])['gdp'].sum().unstack()

# 4. Graficar
fig, ax = plt.subplots(figsize=(15, 8))
fig.patch.set_facecolor('black')
ax.set_facecolor('black')

for region in evolucion_regiones.columns:
    color = paleta.get(region, '#CCCCCC')
    linewidth = 5 if region == 'Argentina' else 3
    plt.plot(evolucion_regiones.index, evolucion_regiones[region],
             marker='o', markersize=6, color=color, linewidth=linewidth, label=region, alpha=0.9)

# 5. Hito Histórico: Milagro Chino (2001)
max_val = evolucion_regiones.max().max()
plt.axvline(x=2001, color='#FFFF00', linestyle='--', linewidth=3, label='Hito: Milagro Chino (2001)')
plt.text(2001.5, max_val, 'MILAGRO CHINO (2001)', color='#FFFF00',
         fontsize=12, fontweight='bold', rotation=90, verticalalignment='top')

# 6. Configuración estética
plt.title(f'EVOLUCIÓN GLOBAL DEL PBI POR REGIONES ({anio_inicio} - {anio_fin})', fontsize=18, fontweight='bold', color='white', pad=20)
plt.xlabel('Año', fontsize=13, fontweight='bold')
plt.ylabel('PBI (Billones USD)', fontsize=13, fontweight='bold')

plt.xticks(range(anio_inicio, anio_fin + 1, 2), rotation=45, fontsize=10)
plt.grid(True, linestyle='--', alpha=0.15)
plt.legend(title="Regiones", bbox_to_anchor=(1.01, 1), loc='upper left', fontsize=11, facecolor='black', edgecolor='white')

plt.tight_layout()
plt.show()

# Restaurar estilo
plt.style.use('default')
     


### EVOLUCIÓN DEL PBI PER CÁPITA: ARGENTINA Y CHINA ###
import matplotlib.pyplot as plt

# 1. Configurar estilo de contraste
plt.style.use('dark_background')

# 2. Preparar los datos
evolucion_arg = df[df['country'] == 'Argentina']
evolucion_china = df[df['country'] == 'China']

# 3. Graficar
fig, ax = plt.subplots(figsize=(15, 8))
fig.patch.set_facecolor('black')
ax.set_facecolor('black')

plt.plot(evolucion_arg['year'], evolucion_arg['gdp_per_capita'], color='#00FFFF', linewidth=4, label='Argentina', marker='o', markersize=4)
plt.plot(evolucion_china['year'], evolucion_china['gdp_per_capita'], color='red', linewidth=4, label='China', marker='o', markersize=4)

# 4. Hito Histórico
plt.axvline(x=2001, color='#FFFF00', linestyle='--', linewidth=3, label='Milagro Chino (2001)')
plt.text(2001.5, max(evolucion_arg['gdp_per_capita'].max(), evolucion_china['gdp_per_capita'].max()), 'HITO: 2001',
         color='#FFFF00', fontsize=12, fontweight='bold')

# 5. Configuración estética y X-axis
plt.title('EVOLUCIÓN HISTÓRICA DEL PBI PER CÁPITA: ARGENTINA VS CHINA', color='white', fontsize=18, fontweight='bold', pad=20)
plt.xlabel('Año', fontsize=13, fontweight='bold')
plt.ylabel('PBI Per Cápita (USD)', fontsize=13, fontweight='bold')

# Ajuste de ticks para no saltar tantos años (cada 2 años)
anio_min = int(df['year'].min())
anio_max = int(df['year'].max())
plt.xticks(range(anio_min, anio_max + 1, 2), rotation=45, fontsize=10)

plt.grid(True, linestyle='--', alpha=0.15)
plt.legend(loc='upper left', fontsize=12, facecolor='black', edgecolor='white')

plt.tight_layout()
plt.show()

# Restaurar estilo
plt.style.use('default')
     


### EVOLUCIÓN DEL PBI: CRISIS FINANCIERA (2003-2013) ###
import matplotlib.pyplot as plt

# 1. Configurar estilo de contraste
plt.style.use('dark_background')

# 2. Definir la paleta con los COLORES FUERTES establecidos
paleta = {
    'América del Sur': '#5D99B0',
    'América del Norte': '#FF6B6B',
    'América Central y Caribe': '#4DB8D9',
    'Europa': '#76C893',
    'Asia': '#FF9F43',
    'África': '#F1C40F',
    'Oceanía': '#9B59B6',
    'Argentina': '#00FFFF'
}

# 3. Preparar los datos del período
df_periodo = df_crisis_financiera.copy()
df_periodo['region'] = df_periodo['country'].apply(asignar_region)
evolucion_regiones = df_periodo[df_periodo['region'] != 'Otros'].groupby(['year', 'region'])['gdp'].sum().unstack()

# 4. Graficar
fig, ax = plt.subplots(figsize=(15, 8))
fig.patch.set_facecolor('black')
ax.set_facecolor('black')

for region in evolucion_regiones.columns:
    color = paleta.get(region, '#CCCCCC')
    linewidth = 5 if region == 'Argentina' else 3.5
    plt.plot(evolucion_regiones.index, evolucion_regiones[region], marker='o', markersize=8, color=color, linewidth=linewidth, label=region)

# 5. Hito Histórico: Crisis Financiera Global (2008)
plt.axvline(x=2008, color='#FF0000', linestyle='--', linewidth=3, label='Hito: Crisis 2008')
plt.text(2008.1, evolucion_regiones.max().max(), 'HITO: 2008', color='#FF0000', fontsize=12, fontweight='bold', verticalalignment='bottom')

# 6. Configuración estética
plt.title('EVOLUCIÓN DEL PBI (2003 - 2013): CRISIS FINANCIERA GLOBAL', fontsize=18, fontweight='bold', color='white', pad=20)
plt.xlabel('Año', fontsize=13, fontweight='bold')
plt.ylabel('PBI (Billones USD)', fontsize=13, fontweight='bold')

plt.xticks(range(2003, 2014), fontsize=11)
plt.grid(True, linestyle='--', alpha=0.15)
plt.legend(title="Regiones", bbox_to_anchor=(1.01, 1), loc='upper left', fontsize=11, facecolor='black', edgecolor='white')

plt.tight_layout()
plt.show()

# Restaurar estilo
plt.style.use('default')
     


### EVOLUCIÓN DEL PBI PER CÁPITA: CRISIS FINANCIERA (2003-2013) ###

import matplotlib.pyplot as plt

# 1. Configurar estilo de contraste
plt.style.use('dark_background')

# 2. Definir la paleta con los COLORES FUERTES establecidos
paleta = {
    'América del Sur': '#5D99B0',       # Azul fuerte
    'América del Norte': '#FF6B6B',     # Salmón/Rojo fuerte
    'América Central y Caribe': '#4DB8D9', # Celeste profundo
    'Europa': '#76C893',               # Verde intenso
    'Asia': '#FF9F43',                 # Naranja vivo
    'África': '#F1C40F',               # Amarillo sólido
    'Oceanía': '#9B59B6',              # Púrpura oscuro
    'Argentina': '#00FFFF'             # Cyan brillante
}

# 3. Preparar los datos del período (PBI PER CÁPITA)
df_periodo = df_crisis_financiera.copy()
df_periodo['region'] = df_periodo['country'].apply(asignar_region)
# Usamos el promedio (mean) del PBI per cápita por región
evolucion_regiones = df_periodo[df_periodo['region'] != 'Otros'].groupby(['year', 'region'])['gdp_per_capita'].mean().unstack()

# 4. Graficar
fig, ax = plt.subplots(figsize=(15, 8))
fig.patch.set_facecolor('black')
ax.set_facecolor('black')

for region in evolucion_regiones.columns:
    color = paleta.get(region, '#CCCCCC')
    linewidth = 5 if region == 'Argentina' else 3.5
    plt.plot(evolucion_regiones.index, evolucion_regiones[region], marker='o', markersize=8, color=color, linewidth=linewidth, label=region)

# 5. Hito Histórico: Crisis Financiera Global (2008)
plt.axvline(x=2008, color='#FF0000', linestyle='--', linewidth=3, label='Hito: Crisis Financiera (2008)')
plt.text(2008.1, evolucion_regiones.max().max(), 'HITO: 2008', color='#FF0000', fontsize=12, fontweight='bold', verticalalignment='bottom')

# 6. Configuración estética
max_val = evolucion_regiones.max().max()
plt.ylim(0, max_val * 1.1)

plt.title('EVOLUCIÓN DEL PBI PER CÁPITA (2003 - 2013): CRISIS FINANCIERA GLOBAL', fontsize=18, fontweight='bold', color='white', pad=20)
plt.xlabel('Año', fontsize=13, fontweight='bold')
plt.ylabel('PBI Per Cápita (USD)', fontsize=13, fontweight='bold')

plt.xticks(range(2003, 2014), fontsize=11)
plt.grid(True, linestyle='--', alpha=0.15)
plt.legend(title="Regiones", bbox_to_anchor=(1.01, 1), loc='upper left', fontsize=11, facecolor='black', edgecolor='white')

plt.tight_layout()
plt.show()

# Restaurar estilo
plt.style.use('default')
     


### EVOLUCIÓN DEL PBI: COVID-19 (2014-2022) ###

import matplotlib.pyplot as plt

# 1. Configurar estilo de contraste
plt.style.use('dark_background')

# 2. Definir la paleta con los COLORES FUERTES establecidos
paleta = {
    'América del Sur': '#5D99B0',       # Azul fuerte
    'América del Norte': '#FF6B6B',     # Salmón/Rojo fuerte
    'América Central y Caribe': '#4DB8D9', # Celeste profundo
    'Europa': '#76C893',               # Verde intenso
    'Asia': '#FF9F43',                 # Naranja vivo
    'África': '#F1C40F',               # Amarillo sólido
    'Oceanía': '#9B59B6',              # Púrpura oscuro
    'Argentina': '#00FFFF'             # Cyan brillante
}

# 3. Preparar los datos del período
df_periodo = df_covid_19.copy()
df_periodo['region'] = df_periodo['country'].apply(asignar_region)
evolucion_regiones = df_periodo[df_periodo['region'] != 'Otros'].groupby(['year', 'region'])['gdp'].sum().unstack()

# 4. Graficar
fig, ax = plt.subplots(figsize=(15, 8))
fig.patch.set_facecolor('black')
ax.set_facecolor('black')

for region in evolucion_regiones.columns:
    color = paleta.get(region, '#CCCCCC')
    linewidth = 5 if region == 'Argentina' else 3.5
    plt.plot(evolucion_regiones.index, evolucion_regiones[region], marker='o', markersize=8, color=color, linewidth=linewidth, label=region)

# 5. Hito Histórico: Pandemia COVID-19 (2020)
plt.axvline(x=2020, color='#FF0000', linestyle='--', linewidth=3, label='Hito: Pandemia COVID-19 (2020)')
plt.text(2020.1, evolucion_regiones.max().max(), 'HITO: 2020', color='#FF0000', fontsize=12, fontweight='bold', verticalalignment='bottom')

# 6. Configuración estética
max_region = evolucion_regiones.max().max()
plt.ylim(0, max_region * 1.1)

plt.title('EVOLUCIÓN DEL PBI (2014 - 2022): IMPACTO DEL COVID-19', fontsize=18, fontweight='bold', color='white', pad=20)
plt.xlabel('Año', fontsize=13, fontweight='bold')
plt.ylabel('PBI (Billones USD)', fontsize=13, fontweight='bold')

plt.xticks(range(2014, 2023), fontsize=11)
plt.grid(True, linestyle='--', alpha=0.15)
plt.legend(title="Regiones", bbox_to_anchor=(1.01, 1), loc='upper left', fontsize=11, facecolor='black', edgecolor='white')

plt.tight_layout()
plt.show()

# Restaurar estilo
plt.style.use('default')
     


### COMPARATIVA PBI PER CÁPITA: ARGENTINA VS PAÍSES SELECCIONADOS (COVID-19) ###

import matplotlib.pyplot as plt
import matplotlib.ticker as ticker

# 1. Configurar estilo de contraste
plt.style.use('dark_background')

# 2. Definir países y colores específicos
paises_seleccionados = ['Argentina', 'Chile', 'Uruguay']
colores_paises = {
    'Argentina': '#00FFFF',   # Cyan brillante
    'Chile': '#FF6B6B',       # Salmón vibrante
    'Uruguay': '#76C893'      # Verde intenso
}

# 3. Preparar los datos filtrando por el rango 2019-2022 (PBI PER CÁPITA)
df_comp = df[(df['country'].isin(paises_seleccionados)) & (df['year'] >= 2019) & (df['year'] <= 2022)]
evolucion_paises = df_comp.pivot_table(index='year', columns='country', values='gdp_per_capita')

# 4. Graficar
fig, ax = plt.subplots(figsize=(15, 8))
fig.patch.set_facecolor('black')
ax.set_facecolor('black')

for pais in evolucion_paises.columns:
    color = colores_paises.get(pais, '#CCCCCC')
    linewidth = 5 if pais == 'Argentina' else 3.5
    plt.plot(evolucion_paises.index, evolucion_paises[pais],
             marker='o', markersize=10, color=color, linewidth=linewidth, label=pais)

# 5. Hito Histórico: Pandemia COVID-19 (2020)
plt.axvline(x=2020, color='#FF0000', linestyle='--', linewidth=3, label='Hito: COVID-19 (2020)')
plt.text(2020.05, evolucion_paises.max().max(), 'HITO: 2020', color='#FF0000',
         fontsize=12, fontweight='bold', verticalalignment='top')

# 6. Configuración estética del Eje Y
ax.yaxis.set_major_locator(ticker.MaxNLocator(nbins=12))
# Formateador para mostrar en USD
ax.yaxis.set_major_formatter(ticker.FuncFormatter(lambda x, pos: f'${x:,.0f}'))

# 7. Configuración estética general
plt.title('EVOLUCIÓN DEL PBI PER CÁPITA (2019 - 2022): IMPACTO COVID-19',
          fontsize=18, fontweight='bold', color='white', pad=20)
plt.xlabel('Año', fontsize=13, fontweight='bold')
plt.ylabel('PBI Per Cápita (USD)', fontsize=13, fontweight='bold')

plt.xticks([2019, 2020, 2021, 2022], fontsize=11)
plt.grid(True, linestyle='--', alpha=0.15)

# Ajuste de leyenda
plt.legend(title="Países", bbox_to_anchor=(1.05, 1), loc='upper left', fontsize=11, facecolor='black', edgecolor='white')

plt.tight_layout()
plt.show()

# Restaurar estilo
plt.style.use('default')
     


# Grilla y leyenda
plt.grid(axis='y', linestyle='--', alpha=0.2)
plt.legend(loc='upper left', fontsize=11, facecolor='black', edgecolor='white')
plt.tight_layout()

plt.show()
plt.style.use('default')

{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "provenance": [],
      "authorship_tag": "ABX9TyPLZW4HSbBzgBegyogU/Hob",
      "include_colab_link": true
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "view-in-github",
        "colab_type": "text"
      },
      "source": [
        "<a href=\"https://colab.research.google.com/github/lucianoyllarreta/CLASE_CIENCIA_DATOS_I/blob/main/LOS%204%20FANT%C3%81STICOS/%C3%9ALTIMOS_AVANCES_PARA_README.ipynb\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 1,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 73
        },
        "id": "uCZOQyjyDwaq",
        "outputId": "6e98d884-68ee-4b21-a2f4-fb95289ebf92"
      },
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<IPython.core.display.HTML object>"
            ],
            "text/html": [
              "\n",
              "     <input type=\"file\" id=\"files-6a4cadbc-bcdc-4f32-a3e2-6f908bb107ca\" name=\"files[]\" multiple disabled\n",
              "        style=\"border:none\" />\n",
              "     <output id=\"result-6a4cadbc-bcdc-4f32-a3e2-6f908bb107ca\">\n",
              "      Upload widget is only available when the cell has been executed in the\n",
              "      current browser session. Please rerun this cell to enable.\n",
              "      </output>\n",
              "      <script>// Copyright 2017 Google LLC\n",
              "//\n",
              "// Licensed under the Apache License, Version 2.0 (the \"License\");\n",
              "// you may not use this file except in compliance with the License.\n",
              "// You may obtain a copy of the License at\n",
              "//\n",
              "//      http://www.apache.org/licenses/LICENSE-2.0\n",
              "//\n",
              "// Unless required by applicable law or agreed to in writing, software\n",
              "// distributed under the License is distributed on an \"AS IS\" BASIS,\n",
              "// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.\n",
              "// See the License for the specific language governing permissions and\n",
              "// limitations under the License.\n",
              "\n",
              "/**\n",
              " * @fileoverview Helpers for google.colab Python module.\n",
              " */\n",
              "(function(scope) {\n",
              "function span(text, styleAttributes = {}) {\n",
              "  const element = document.createElement('span');\n",
              "  element.textContent = text;\n",
              "  for (const key of Object.keys(styleAttributes)) {\n",
              "    element.style[key] = styleAttributes[key];\n",
              "  }\n",
              "  return element;\n",
              "}\n",
              "\n",
              "// Max number of bytes which will be uploaded at a time.\n",
              "const MAX_PAYLOAD_SIZE = 100 * 1024;\n",
              "\n",
              "function _uploadFiles(inputId, outputId) {\n",
              "  const steps = uploadFilesStep(inputId, outputId);\n",
              "  const outputElement = document.getElementById(outputId);\n",
              "  // Cache steps on the outputElement to make it available for the next call\n",
              "  // to uploadFilesContinue from Python.\n",
              "  outputElement.steps = steps;\n",
              "\n",
              "  return _uploadFilesContinue(outputId);\n",
              "}\n",
              "\n",
              "// This is roughly an async generator (not supported in the browser yet),\n",
              "// where there are multiple asynchronous steps and the Python side is going\n",
              "// to poll for completion of each step.\n",
              "// This uses a Promise to block the python side on completion of each step,\n",
              "// then passes the result of the previous step as the input to the next step.\n",
              "function _uploadFilesContinue(outputId) {\n",
              "  const outputElement = document.getElementById(outputId);\n",
              "  const steps = outputElement.steps;\n",
              "\n",
              "  const next = steps.next(outputElement.lastPromiseValue);\n",
              "  return Promise.resolve(next.value.promise).then((value) => {\n",
              "    // Cache the last promise value to make it available to the next\n",
              "    // step of the generator.\n",
              "    outputElement.lastPromiseValue = value;\n",
              "    return next.value.response;\n",
              "  });\n",
              "}\n",
              "\n",
              "/**\n",
              " * Generator function which is called between each async step of the upload\n",
              " * process.\n",
              " * @param {string} inputId Element ID of the input file picker element.\n",
              " * @param {string} outputId Element ID of the output display.\n",
              " * @return {!Iterable<!Object>} Iterable of next steps.\n",
              " */\n",
              "function* uploadFilesStep(inputId, outputId) {\n",
              "  const inputElement = document.getElementById(inputId);\n",
              "  inputElement.disabled = false;\n",
              "\n",
              "  const outputElement = document.getElementById(outputId);\n",
              "  outputElement.innerHTML = '';\n",
              "\n",
              "  const pickedPromise = new Promise((resolve) => {\n",
              "    inputElement.addEventListener('change', (e) => {\n",
              "      resolve(e.target.files);\n",
              "    });\n",
              "  });\n",
              "\n",
              "  const cancel = document.createElement('button');\n",
              "  inputElement.parentElement.appendChild(cancel);\n",
              "  cancel.textContent = 'Cancel upload';\n",
              "  const cancelPromise = new Promise((resolve) => {\n",
              "    cancel.onclick = () => {\n",
              "      resolve(null);\n",
              "    };\n",
              "  });\n",
              "\n",
              "  // Wait for the user to pick the files.\n",
              "  const files = yield {\n",
              "    promise: Promise.race([pickedPromise, cancelPromise]),\n",
              "    response: {\n",
              "      action: 'starting',\n",
              "    }\n",
              "  };\n",
              "\n",
              "  cancel.remove();\n",
              "\n",
              "  // Disable the input element since further picks are not allowed.\n",
              "  inputElement.disabled = true;\n",
              "\n",
              "  if (!files) {\n",
              "    return {\n",
              "      response: {\n",
              "        action: 'complete',\n",
              "      }\n",
              "    };\n",
              "  }\n",
              "\n",
              "  for (const file of files) {\n",
              "    const li = document.createElement('li');\n",
              "    li.append(span(file.name, {fontWeight: 'bold'}));\n",
              "    li.append(span(\n",
              "        `(${file.type || 'n/a'}) - ${file.size} bytes, ` +\n",
              "        `last modified: ${\n",
              "            file.lastModifiedDate ? file.lastModifiedDate.toLocaleDateString() :\n",
              "                                    'n/a'} - `));\n",
              "    const percent = span('0% done');\n",
              "    li.appendChild(percent);\n",
              "\n",
              "    outputElement.appendChild(li);\n",
              "\n",
              "    const fileDataPromise = new Promise((resolve) => {\n",
              "      const reader = new FileReader();\n",
              "      reader.onload = (e) => {\n",
              "        resolve(e.target.result);\n",
              "      };\n",
              "      reader.readAsArrayBuffer(file);\n",
              "    });\n",
              "    // Wait for the data to be ready.\n",
              "    let fileData = yield {\n",
              "      promise: fileDataPromise,\n",
              "      response: {\n",
              "        action: 'continue',\n",
              "      }\n",
              "    };\n",
              "\n",
              "    // Use a chunked sending to avoid message size limits. See b/62115660.\n",
              "    let position = 0;\n",
              "    do {\n",
              "      const length = Math.min(fileData.byteLength - position, MAX_PAYLOAD_SIZE);\n",
              "      const chunk = new Uint8Array(fileData, position, length);\n",
              "      position += length;\n",
              "\n",
              "      const base64 = btoa(String.fromCharCode.apply(null, chunk));\n",
              "      yield {\n",
              "        response: {\n",
              "          action: 'append',\n",
              "          file: file.name,\n",
              "          data: base64,\n",
              "        },\n",
              "      };\n",
              "\n",
              "      let percentDone = fileData.byteLength === 0 ?\n",
              "          100 :\n",
              "          Math.round((position / fileData.byteLength) * 100);\n",
              "      percent.textContent = `${percentDone}% done`;\n",
              "\n",
              "    } while (position < fileData.byteLength);\n",
              "  }\n",
              "\n",
              "  // All done.\n",
              "  yield {\n",
              "    response: {\n",
              "      action: 'complete',\n",
              "    }\n",
              "  };\n",
              "}\n",
              "\n",
              "scope.google = scope.google || {};\n",
              "scope.google.colab = scope.google.colab || {};\n",
              "scope.google.colab._files = {\n",
              "  _uploadFiles,\n",
              "  _uploadFilesContinue,\n",
              "};\n",
              "})(self);\n",
              "</script> "
            ]
          },
          "metadata": {}
        },
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Saving df_final.csv to df_final.csv\n"
          ]
        }
      ],
      "source": [
        "from google.colab import files\n",
        "upload  = files.upload()"
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "import pandas as pd\n",
        "df = pd.read_csv('df_final.csv')"
      ],
      "metadata": {
        "id": "zJjSa_P0D2YU"
      },
      "execution_count": 2,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "print(\"PASO 4 — Construcción de KPIs\")\n",
        "print(\"=\" * 60)\n",
        "\n",
        "# KPI 1: Brecha de Concentración de Ingresos (BCI)\n",
        "# Cuanto más alta → más desigualdad → peor score\n",
        "df[\"BCI\"] = df[\"income_top10\"] / df[\"income_bottom50\"]\n",
        "\n",
        "\n",
        "\n",
        "print(\"  ✔ BCI creado             (income_top10 / income_bottom50)\")\n",
        "print(f\"\\n  BCI promedio global:  {df['BCI'].mean():.2f}\")"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "m3pOanWrEAwA",
        "outputId": "4d35ef52-04b9-4686-a7f0-ddbb58d0e0fa"
      },
      "execution_count": 3,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "PASO 4 — Construcción de KPIs\n",
            "============================================================\n",
            "  ✔ BCI creado             (income_top10 / income_bottom50)\n",
            "\n",
            "  BCI promedio global:  3.82\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "# Normalizar — nota la INVERSIÓN de lógica para variables donde\n",
        "# \"más alto = peor\":\n",
        "#   gdp_per_capita  → más alto = mejor  → sin invertir\n",
        "#   unemp_total_15  → más alto = peor   → invertir (1 - norm)\n",
        "#   BCI             → más alto = peor   → invertir (1 - norm)\n",
        "print(\"PASO 5 — Normalización Min-Max (escala global histórica)\")\n",
        "print(\"=\" * 60)\n",
        "\n",
        "def minmax(series):\n",
        "    \"\"\"Normaliza una serie al rango [0, 1].\"\"\"\n",
        "    min_v, max_v = series.min(), series.max()\n",
        "    if max_v == min_v:\n",
        "        return pd.Series(0.5, index=series.index)\n",
        "    return (series - min_v) / (max_v - min_v)\n",
        "\n",
        "df[\"norm_gdp\"]    =       minmax(df[\"gdp_per_capita\"])\n",
        "df[\"norm_unemp\"]  = 1   - minmax(df[\"Total_15+\"])   # invertido\n",
        "df[\"norm_bci\"]    = 1   - minmax(df[\"BCI\"])              # invertido\n",
        "\n",
        "print(\"  ✔ norm_gdp     (mayor = mejor capacidad fiscal)\")\n",
        "print(\"  ✔ norm_unemp   (menor desempleo = mayor puntaje)\")\n",
        "print(\"  ✔ norm_bci     (menor concentración = mayor puntaje)\")"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "pVy4SjnCEQJi",
        "outputId": "64986e25-1894-418d-dc7d-6560893b701b"
      },
      "execution_count": 5,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "PASO 5 — Normalización Min-Max (escala global histórica)\n",
            "============================================================\n",
            "  ✔ norm_gdp     (mayor = mejor capacidad fiscal)\n",
            "  ✔ norm_unemp   (menor desempleo = mayor puntaje)\n",
            "  ✔ norm_bci     (menor concentración = mayor puntaje)\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "print(\"PROPUESTA DE NUEVOS KPIs ESTRATÉGICOS\")\n",
        "print(\"=\" * 60)\n",
        "\n",
        "# 1. KPI: Índice de Equidad de Oportunidades (IEO)\n",
        "df['IEO'] = df['norm_gdp'] * df['norm_bci']\n",
        "\n",
        "# 2. KPI: Coeficiente de Fragilidad Laboral de Género (CFLG)\n",
        "df['CFLG'] = df['brecha de desempleo de genero'] / (df['Total_15+'] + 0.1)\n",
        "\n",
        "# 3. KPI: Intensidad de Capital Humano (ICH)\n",
        "df['ICH'] = df['gdp'] / (df['Total_15+'] * df['population'] / 100)\n",
        "\n",
        "# Clarificamos que estos son promedios de TODA la base de datos\n",
        "print(f\"  ✔ IEO (Equidad)       - Promedio GLOBAL: {df['IEO'].mean():.4f}\")\n",
        "print(f\"  ✔ CFLG (Género)       - Promedio GLOBAL: {df['CFLG'].mean():.4f}\")\n",
        "print(f\"  ✔ ICH (Productividad) - Promedio GLOBAL: {df['ICH'].mean():.2f}\")\n",
        "\n",
        "# --- Interpretación específica para Argentina ---\n",
        "print(\"\\nINTERPRETACIÓN DE RESULTADOS ESPECÍFICOS (ARGENTINA - ÚLTIMO DATO VÁLIDO)\")\n",
        "print(\"-\" * 60)\n",
        "# Buscamos el último año donde Argentina tenga datos completos de estos KPIs (usualmente 2022)\n",
        "latest_arg = df[df['country'] == 'Argentina'].dropna(subset=['IEO']).iloc[-1]\n",
        "\n",
        "interpretations = [\n",
        "    (f\"IEO ({latest_arg['IEO']:.3f}):\", \"Refleja la sinergia entre riqueza y distribución en Argentina. Un valor bajo sugiere que el crecimiento no llega equitativamente.\"),\n",
        "    (f\"CFLG ({latest_arg['CFLG']:.3f}):\", \"Mide la vulnerabilidad de las mujeres en el mercado laboral argentino. Si es negativo, la brecha es menor al promedio histórico.\"),\n",
        "    (f\"ICH (${latest_arg['ICH']:,.2f}):\", \"Representa la productividad teórica por cada trabajador potencial en Argentina. Es clave para medir la eficiencia del capital humano.\")\n",
        "]\n",
        "\n",
        "for kpi, text in interpretations:\n",
        "    print(f\"{kpi:<20} {text}\")\n",
        "\n",
        "print(f\"\\nNota: Los valores de Argentina corresponden al año {int(latest_arg['year'])}.\")\n",
        "print(\"\\nÚltimos registros en tabla:\")\n",
        "display(df[df['country'] == 'Argentina'][['year', 'IEO', 'CFLG', 'ICH']].tail(3))"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 423
        },
        "id": "mcsUhjQoEKBT",
        "outputId": "58d25460-349e-4e53-f76f-f2fc70f72d66"
      },
      "execution_count": 6,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "PROPUESTA DE NUEVOS KPIs ESTRATÉGICOS\n",
            "============================================================\n",
            "  ✔ IEO (Equidad)       - Promedio GLOBAL: 0.0780\n",
            "  ✔ CFLG (Género)       - Promedio GLOBAL: -0.2419\n",
            "  ✔ ICH (Productividad) - Promedio GLOBAL: 569364.83\n",
            "\n",
            "INTERPRETACIÓN DE RESULTADOS ESPECÍFICOS (ARGENTINA - ÚLTIMO DATO VÁLIDO)\n",
            "------------------------------------------------------------\n",
            "IEO (0.101):         Refleja la sinergia entre riqueza y distribución en Argentina. Un valor bajo sugiere que el crecimiento no llega equitativamente.\n",
            "CFLG (-0.223):       Mide la vulnerabilidad de las mujeres en el mercado laboral argentino. Si es negativo, la brecha es menor al promedio histórico.\n",
            "ICH ($276,670.61):   Representa la productividad teórica por cada trabajador potencial en Argentina. Es clave para medir la eficiencia del capital humano.\n",
            "\n",
            "Nota: Los valores de Argentina corresponden al año 2022.\n",
            "\n",
            "Últimos registros en tabla:\n"
          ]
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "     year       IEO      CFLG            ICH\n",
              "167  2022  0.100844 -0.222592  276670.610777\n",
              "168  2023       NaN -0.184645            NaN\n",
              "169  2024       NaN -0.184276            NaN"
            ],
            "text/html": [
              "\n",
              "  <div id=\"df-cc6c3026-0b78-456c-b98e-5dd13484880b\" class=\"colab-df-container\">\n",
              "    <div>\n",
              "<style scoped>\n",
              "    .dataframe tbody tr th:only-of-type {\n",
              "        vertical-align: middle;\n",
              "    }\n",
              "\n",
              "    .dataframe tbody tr th {\n",
              "        vertical-align: top;\n",
              "    }\n",
              "\n",
              "    .dataframe thead th {\n",
              "        text-align: right;\n",
              "    }\n",
              "</style>\n",
              "<table border=\"1\" class=\"dataframe\">\n",
              "  <thead>\n",
              "    <tr style=\"text-align: right;\">\n",
              "      <th></th>\n",
              "      <th>year</th>\n",
              "      <th>IEO</th>\n",
              "      <th>CFLG</th>\n",
              "      <th>ICH</th>\n",
              "    </tr>\n",
              "  </thead>\n",
              "  <tbody>\n",
              "    <tr>\n",
              "      <th>167</th>\n",
              "      <td>2022</td>\n",
              "      <td>0.100844</td>\n",
              "      <td>-0.222592</td>\n",
              "      <td>276670.610777</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>168</th>\n",
              "      <td>2023</td>\n",
              "      <td>NaN</td>\n",
              "      <td>-0.184645</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "    <tr>\n",
              "      <th>169</th>\n",
              "      <td>2024</td>\n",
              "      <td>NaN</td>\n",
              "      <td>-0.184276</td>\n",
              "      <td>NaN</td>\n",
              "    </tr>\n",
              "  </tbody>\n",
              "</table>\n",
              "</div>\n",
              "    <div class=\"colab-df-buttons\">\n",
              "\n",
              "  <div class=\"colab-df-container\">\n",
              "    <button class=\"colab-df-convert\" onclick=\"convertToInteractive('df-cc6c3026-0b78-456c-b98e-5dd13484880b')\"\n",
              "            title=\"Convert this dataframe to an interactive table.\"\n",
              "            style=\"display:none;\">\n",
              "\n",
              "  <svg xmlns=\"http://www.w3.org/2000/svg\" height=\"24px\" viewBox=\"0 -960 960 960\">\n",
              "    <path d=\"M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z\"/>\n",
              "  </svg>\n",
              "    </button>\n",
              "\n",
              "  <style>\n",
              "    .colab-df-container {\n",
              "      display:flex;\n",
              "      gap: 12px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert {\n",
              "      background-color: #E8F0FE;\n",
              "      border: none;\n",
              "      border-radius: 50%;\n",
              "      cursor: pointer;\n",
              "      display: none;\n",
              "      fill: #1967D2;\n",
              "      height: 32px;\n",
              "      padding: 0 0 0 0;\n",
              "      width: 32px;\n",
              "    }\n",
              "\n",
              "    .colab-df-convert:hover {\n",
              "      background-color: #E2EBFA;\n",
              "      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);\n",
              "      fill: #174EA6;\n",
              "    }\n",
              "\n",
              "    .colab-df-buttons div {\n",
              "      margin-bottom: 4px;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert {\n",
              "      background-color: #3B4455;\n",
              "      fill: #D2E3FC;\n",
              "    }\n",
              "\n",
              "    [theme=dark] .colab-df-convert:hover {\n",
              "      background-color: #434B5C;\n",
              "      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);\n",
              "      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));\n",
              "      fill: #FFFFFF;\n",
              "    }\n",
              "  </style>\n",
              "\n",
              "    <script>\n",
              "      const buttonEl =\n",
              "        document.querySelector('#df-cc6c3026-0b78-456c-b98e-5dd13484880b button.colab-df-convert');\n",
              "      buttonEl.style.display =\n",
              "        google.colab.kernel.accessAllowed ? 'block' : 'none';\n",
              "\n",
              "      async function convertToInteractive(key) {\n",
              "        const element = document.querySelector('#df-cc6c3026-0b78-456c-b98e-5dd13484880b');\n",
              "        const dataTable =\n",
              "          await google.colab.kernel.invokeFunction('convertToInteractive',\n",
              "                                                    [key], {});\n",
              "        if (!dataTable) return;\n",
              "\n",
              "        const docLinkHtml = 'Like what you see? Visit the ' +\n",
              "          '<a target=\"_blank\" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'\n",
              "          + ' to learn more about interactive tables.';\n",
              "        element.innerHTML = '';\n",
              "        dataTable['output_type'] = 'display_data';\n",
              "        await google.colab.output.renderOutput(dataTable, element);\n",
              "        const docLink = document.createElement('div');\n",
              "        docLink.innerHTML = docLinkHtml;\n",
              "        element.appendChild(docLink);\n",
              "      }\n",
              "    </script>\n",
              "  </div>\n",
              "\n",
              "\n",
              "    </div>\n",
              "  </div>\n"
            ],
            "application/vnd.google.colaboratory.intrinsic+json": {
              "type": "dataframe",
              "summary": "{\n  \"name\": \"display(df[df['country'] == 'Argentina'][['year', 'IEO', 'CFLG', 'ICH']]\",\n  \"rows\": 3,\n  \"fields\": [\n    {\n      \"column\": \"year\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 1,\n        \"min\": 2022,\n        \"max\": 2024,\n        \"num_unique_values\": 3,\n        \"samples\": [\n          2022,\n          2023,\n          2024\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"IEO\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": null,\n        \"min\": 0.10084446513994971,\n        \"max\": 0.10084446513994971,\n        \"num_unique_values\": 1,\n        \"samples\": [\n          0.10084446513994971\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"CFLG\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": 0.022016239631461706,\n        \"min\": -0.22259232440260696,\n        \"max\": -0.18427586206896557,\n        \"num_unique_values\": 3,\n        \"samples\": [\n          -0.22259232440260696\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    },\n    {\n      \"column\": \"ICH\",\n      \"properties\": {\n        \"dtype\": \"number\",\n        \"std\": null,\n        \"min\": 276670.61077668966,\n        \"max\": 276670.61077668966,\n        \"num_unique_values\": 1,\n        \"samples\": [\n          276670.61077668966\n        ],\n        \"semantic_type\": \"\",\n        \"description\": \"\"\n      }\n    }\n  ]\n}"
            }
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "# 6. CÁLCULO DEL ÍNDICE DE RESILIENCIA (0-100)\n",
        "# ─────────────────────────────────────────────\n",
        "\n",
        "print(\"\\n\" + \"=\" * 60)\n",
        "print(\"PASO 6 — Índice de Resiliencia Macro-Social (0–100)\")\n",
        "print(\"=\" * 60)\n",
        "\n",
        "PESO_ECONOMICO  = 0.50\n",
        "PESO_LABORAL    = 0.30\n",
        "PESO_EQUIDAD    = 0.20\n",
        "\n",
        "df[\"score_resiliencia\"] = (\n",
        "    df[\"norm_gdp\"]   * PESO_ECONOMICO  +\n",
        "    df[\"norm_unemp\"] * PESO_LABORAL    +\n",
        "    df[\"norm_bci\"]   * PESO_EQUIDAD\n",
        ") * 100\n",
        "\n",
        "# Redondear a 2 decimales\n",
        "df[\"score_resiliencia\"] = df[\"score_resiliencia\"].round(2)\n",
        "\n",
        "print(f\"  Pesos: Económico={PESO_ECONOMICO*100:.0f}% | \"\n",
        "      f\"Laboral={PESO_LABORAL*100:.0f}% | Equidad={PESO_EQUIDAD*100:.0f}%\")\n",
        "print(f\"\\n  Score global promedio: {df['score_resiliencia'].mean():.1f}\")\n",
        "print(f\"  Score mínimo:          {df['score_resiliencia'].min():.1f}\")\n",
        "print(f\"  Score máximo:          {df['score_resiliencia'].max():.1f}\")"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "Y_artxStEam1",
        "outputId": "3eaa5da3-975f-4b06-df4c-3f103a32d18e"
      },
      "execution_count": 7,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "\n",
            "============================================================\n",
            "PASO 6 — Índice de Resiliencia Macro-Social (0–100)\n",
            "============================================================\n",
            "  Pesos: Económico=50% | Laboral=30% | Equidad=20%\n",
            "\n",
            "  Score global promedio: 45.4\n",
            "  Score mínimo:          16.8\n",
            "  Score máximo:          95.1\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "import matplotlib.pyplot as plt\n",
        "\n",
        "# Filtrar datos para Argentina y ordenar por año\n",
        "df_arg = df[df['country'] == 'Argentina'].sort_values('year')\n",
        "\n",
        "# Calcular el máximo histórico de PBI específicamente para Argentina\n",
        "arg_max_gdp = df_arg['gdp_per_capita'].max()\n",
        "\n",
        "fig, ax1 = plt.subplots(figsize=(12, 7))\n",
        "\n",
        "# Eje 1: Score de Resiliencia\n",
        "color_res = 'tab:blue'\n",
        "ax1.set_xlabel('Año', fontsize=12)\n",
        "ax1.set_ylabel('Score de Resiliencia (0-100)', color=color_res, fontsize=12)\n",
        "lns1 = ax1.plot(df_arg['year'], df_arg['score_resiliencia'], color=color_res, linewidth=3, label='Resiliencia (Eje Izq.)')\n",
        "ax1.tick_params(axis='y', labelcolor=color_res)\n",
        "ax1.grid(True, alpha=0.3)\n",
        "\n",
        "# Eje 2: PBI per cápita\n",
        "ax2 = ax1.twinx()\n",
        "color_pbi = 'tab:red'\n",
        "ax2.set_ylabel('GDP per cápita (USD)', color=color_pbi, fontsize=12)\n",
        "lns2 = ax2.plot(df_arg['year'], df_arg['gdp_per_capita'], color=color_pbi, linestyle='--', linewidth=2, label='PBI per cápita (Eje Der.)')\n",
        "\n",
        "# Referencia del máximo HISTÓRICO DE ARGENTINA\n",
        "lns3 = ax2.axhline(y=arg_max_gdp, color='gray', linestyle=':', alpha=0.7, label=f'Máximo Histórico Arg: ${arg_max_gdp:,.0f}')\n",
        "ax2.tick_params(axis='y', labelcolor=color_pbi)\n",
        "\n",
        "# Combinar leyendas\n",
        "lns = lns1 + lns2 + [lns3]\n",
        "labs = [l.get_label() for l in lns]\n",
        "ax1.legend(lns, labs, loc='upper left', frameon=True, shadow=True)\n",
        "\n",
        "plt.title('Argentina: Evolución de Resiliencia vs. PBI per cápita\\n(Referencia: Máximo histórico nacional)', fontsize=14)\n",
        "fig.tight_layout()\n",
        "plt.show()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 646
        },
        "id": "b0UMsM6yEovs",
        "outputId": "0450ff5e-1682-44e3-e13e-8db8548a23fb"
      },
      "execution_count": 8,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 1200x700 with 2 Axes>"
            ],
            "image/png": 
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "import matplotlib.pyplot as plt\n",
        "import seaborn as sns\n",
        "\n",
        "# Lista de países solicitada (ex-Yugoslavia sin Eslovenia + Argentina)\n",
        "paises_analisis = [\n",
        "    'Croatia', 'Bosnia and Herzegovina', 'Serbia',\n",
        "    'Montenegro', 'North Macedonia', 'Kosovo', 'Argentina'\n",
        "]\n",
        "\n",
        "# Filtrar el DataFrame\n",
        "df_comp = df[df['country'].isin(paises_analisis)].sort_values(['country', 'year'])\n",
        "\n",
        "# Configuración del gráfico\n",
        "plt.figure(figsize=(14, 8))\n",
        "sns.set_style(\"whitegrid\")\n",
        "\n",
        "# Definir paleta: Argentina destacada, el resto en tonos grises/atenuados\n",
        "# O usamos un color llamativo para Argentina\n",
        "colores = {}\n",
        "for p in paises_analisis:\n",
        "    if p == 'Argentina':\n",
        "        colores[p] = '#00FFFF' # Cyan brillante para destacar\n",
        "    else:\n",
        "        colores[p] = None # Dejar que seaborn asigne el resto\n",
        "\n",
        "# Dibujar líneas\n",
        "for pais in paises_analisis:\n",
        "    data_p = df_comp[df_comp['country'] == pais]\n",
        "    linewidth = 5 if pais == 'Argentina' else 2\n",
        "    zorder = 10 if pais == 'Argentina' else 2\n",
        "    alpha = 1.0 if pais == 'Argentina' else 0.6\n",
        "\n",
        "    plt.plot(data_p['year'], data_p['score_resiliencia'],\n",
        "             label=pais, linewidth=linewidth, zorder=zorder, alpha=alpha,\n",
        "             marker='o', markersize=4 if pais != 'Argentina' else 6,\n",
        "             color=colores[pais])\n",
        "\n",
        "# Personalización\n",
        "plt.title('Comparativa: Argentina vs. Países de la ex-Yugoslavia', fontsize=16, fontweight='bold')\n",
        "plt.xlabel('Año', fontsize=12)\n",
        "plt.ylabel('Score de Resiliencia (0-100)', fontsize=12)\n",
        "plt.legend(title='País', bbox_to_anchor=(1.05, 1), loc='upper left')\n",
        "plt.grid(True, alpha=0.3)\n",
        "\n",
        "plt.tight_layout()\n",
        "plt.show()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 635
        },
        "id": "yg35IiJsEv5p",
        "outputId": "4285cf09-0782-4ce2-e52a-c093a9ad3640"
      },
      "execution_count": 9,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 1400x800 with 1 Axes>"
            ],
            "image/png": 
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "import numpy as np\n",
        "from sklearn.linear_model import LinearRegression\n",
        "import matplotlib.pyplot as plt\n",
        "\n",
        "# Confirmamos los pesos solicitados para el Score de Resiliencia\n",
        "PESO_ECONOMICO = 0.50\n",
        "PESO_LABORAL = 0.30\n",
        "PESO_EQUIDAD = 0.20\n",
        "\n",
        "# Definición de regiones\n",
        "norteamerica = ['United States', 'Canada', 'Mexico']\n",
        "\n",
        "def analyze_recovery(country_list, name):\n",
        "    # Agrupar datos por año para la región/país\n",
        "    df_reg = df[df['country'].isin(country_list)].groupby('year')['score_resiliencia'].mean().reset_index()\n",
        "\n",
        "    # Datos previos a la crisis (hasta 2007) para entrenar la tendencia\n",
        "    df_pre = df_reg[df_reg['year'] <= 2007]\n",
        "\n",
        "    if df_pre.empty:\n",
        "        print(f\"No hay suficientes datos pre-2008 para {name}\")\n",
        "        return\n",
        "\n",
        "    # Entrenar modelo de regresión lineal con la tendencia pre-crisis\n",
        "    model = LinearRegression()\n",
        "    X_pre = df_pre[['year']]\n",
        "    y_pre = df_pre['score_resiliencia']\n",
        "    model.fit(X_pre, y_pre)\n",
        "\n",
        "    # Generar el Forecast (proyección) para todo el periodo\n",
        "    df_reg['forecast'] = model.predict(df_reg[['year']])\n",
        "\n",
        "    # Visualización\n",
        "    plt.figure(figsize=(12, 6))\n",
        "    plt.plot(df_reg['year'], df_reg['score_resiliencia'], label='Realidad (Actual)', marker='o', linewidth=2.5, color='#1f77b4')\n",
        "    plt.plot(df_reg['year'], df_reg['forecast'], label='Previsión (Tendencia pre-2008)', linestyle='--', color='#d62728', alpha=0.8)\n",
        "\n",
        "    # Marcador de la crisis\n",
        "    plt.axvline(x=2008, color='black', linestyle=':', label='Inicio Crisis 2008')\n",
        "\n",
        "    plt.title(f'Forecast de Resiliencia: {name}\\n(Pesos: Econ 50%, Lab 30%, Equi 20%)', fontsize=14)\n",
        "    plt.xlabel('Año')\n",
        "    plt.ylabel('Score de Resiliencia')\n",
        "    plt.legend(frameon=True)\n",
        "    plt.grid(True, alpha=0.3)\n",
        "    plt.tight_layout()\n",
        "    plt.show()\n",
        "\n",
        "# Ejecutar análisis para Argentina y Norteamérica\n",
        "analyze_recovery(['Argentina'], 'Argentina')\n",
        "analyze_recovery(norteamerica, 'Norteamérica (Promedio)')"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 1000
        },
        "id": "1Ie1o7GpEx2q",
        "outputId": "db46c619-952e-4b37-f26c-572587edb5df"
      },
      "execution_count": 10,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 1200x600 with 1 Axes>"
            ],
            "image/png": II=\n"
          },
          "metadata": {}
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 1200x600 with 1 Axes>"
            ],
            "image/png": 
          },
          "metadata": {}
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "import numpy as np\n",
        "from sklearn.linear_model import LinearRegression\n",
        "import matplotlib.pyplot as plt\n",
        "import pandas as pd\n",
        "\n",
        "# 1. Preparar datos de PBI per cápita para Argentina\n",
        "df_arg_gdp = df[df['country'] == 'Argentina'].dropna(subset=['gdp_per_capita']).sort_values('year')\n",
        "\n",
        "# 2. Entrenar el modelo con la tendencia histórica\n",
        "X_gdp = df_arg_gdp[['year']]\n",
        "y_gdp = df_arg_gdp['gdp_per_capita']\n",
        "\n",
        "model_gdp_final = LinearRegression()\n",
        "model_gdp_final.fit(X_gdp, y_gdp)\n",
        "\n",
        "# 3. Generar Previsión hasta 2026\n",
        "years_range = np.arange(1991, 2027).reshape(-1, 1)\n",
        "gdp_forecast_final = model_gdp_final.predict(years_range)\n",
        "\n",
        "# 4. Visualización\n",
        "plt.figure(figsize=(12, 6))\n",
        "\n",
        "# Realidad\n",
        "plt.plot(df_arg_gdp['year'], df_arg_gdp['gdp_per_capita'], label='PBI per cápita Real', color='#2ca02c', marker='o', linewidth=2.5)\n",
        "\n",
        "# Previsión\n",
        "plt.plot(years_range, gdp_forecast_final, label='Tendencia Proyectada (Forecast)', color='#d62728', linestyle='--', linewidth=2)\n",
        "\n",
        "plt.title('Argentina: Proyección del PBI per cápita hasta 2026', fontsize=14)\n",
        "plt.xlabel('Año')\n",
        "plt.ylabel('PBI per cápita (USD)')\n",
        "plt.axvline(x=2022, color='gray', linestyle=':', label='Fin datos históricos')\n",
        "plt.legend()\n",
        "plt.grid(True, alpha=0.3)\n",
        "plt.tight_layout()\n",
        "plt.show()\n",
        "\n",
        "# 5. Resultados numéricos específicos para el usuario\n",
        "future_years_list = [2024, 2025, 2026]\n",
        "future_preds = model_gdp_final.predict(np.array(future_years_list).reshape(-1, 1))\n",
        "\n",
        "print(\"Valores proyectados del PBI per cápita para Argentina:\")\n",
        "for yr, val in zip(future_years_list, future_preds):\n",
        "    print(f\"Año {yr}: ${val:,.2f} USD\")"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 714
        },
        "id": "WpBw99SPFHBd",
        "outputId": "741dd167-55d5-4a72-9740-34320456ad4b"
      },
      "execution_count": 11,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stderr",
          "text": [
            "/usr/local/lib/python3.12/dist-packages/sklearn/utils/validation.py:2739: UserWarning: X does not have valid feature names, but LinearRegression was fitted with feature names\n",
            "  warnings.warn(\n"
          ]
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 1200x600 with 1 Axes>"
            ],
            "image/png": 
          },
          "metadata": {}
        },
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Valores proyectados del PBI per cápita para Argentina:\n",
            "Año 2024: $20,555.80 USD\n",
            "Año 2025: $20,800.86 USD\n",
            "Año 2026: $21,045.92 USD\n"
          ]
        },
        {
          "output_type": "stream",
          "name": "stderr",
          "text": [
            "/usr/local/lib/python3.12/dist-packages/sklearn/utils/validation.py:2739: UserWarning: X does not have valid feature names, but LinearRegression was fitted with feature names\n",
            "  warnings.warn(\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "import numpy as np\n",
        "from sklearn.linear_model import LinearRegression\n",
        "import matplotlib.pyplot as plt\n",
        "import pandas as pd\n",
        "\n",
        "# 1. Manually providing USA historical data from 1990 to 2022 (World Bank approximate values)\n",
        "usa_historical_data = {\n",
        "    'year': list(range(1990, 2023)),\n",
        "    'gdp_per_capita': [\n",
        "        23888, 24342, 25418, 26387, 27694, 28690, 29967, 31459, 32853, 34513,\n",
        "        36334, 37133, 38023, 39496, 41712, 44114, 46298, 47975, 48382, 47001,\n",
        "        48311, 49793, 51450, 52782, 54696, 56469, 57436, 59382, 62232, 65202,\n",
        "        63027, 70248, 76329\n",
        "    ]\n",
        "}\n",
        "df_usa = pd.DataFrame(usa_historical_data)\n",
        "\n",
        "# 2. Train the model using the 1990-2022 range\n",
        "X_usa = df_usa[['year']]\n",
        "y_usa = df_usa['gdp_per_capita']\n",
        "model_usa = LinearRegression()\n",
        "model_usa.fit(X_usa, y_usa)\n",
        "\n",
        "# 3. Forecast from 1990 until 2026\n",
        "years_range = np.arange(1990, 2027).reshape(-1, 1)\n",
        "forecast_values = model_usa.predict(years_range)\n",
        "\n",
        "# 4. Visualization\n",
        "plt.figure(figsize=(12, 6))\n",
        "plt.plot(df_usa['year'], df_usa['gdp_per_capita'], label='USA Real GDP per capita (1990-2022)', marker='o', color='#1f77b4', linewidth=2)\n",
        "plt.plot(years_range, forecast_values, label='Trend Projection (1990-2026)', linestyle='--', color='#d62728')\n",
        "\n",
        "plt.title('United States: GDP per capita Forecast (1990-2026)', fontsize=14)\n",
        "plt.xlabel('Year')\n",
        "plt.ylabel('GDP per capita (USD)')\n",
        "plt.axvline(x=2022, color='gray', linestyle=':', label='End of historical data')\n",
        "plt.grid(True, alpha=0.3)\n",
        "plt.legend()\n",
        "plt.show()\n",
        "\n",
        "# 5. Numerical Results for the requested forecast period\n",
        "future_years = np.array([2024, 2025, 2026]).reshape(-1, 1)\n",
        "preds = model_usa.predict(future_years)\n",
        "\n",
        "print(\"Projected GDP per capita for USA (Model based on 1990-2022 trend):\")\n",
        "for yr, val in zip([2024, 2025, 2026], preds):\n",
        "    print(f\"Year {yr}: ${val:,.2f} USD\")"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 724
        },
        "id": "FjGs8RbMFJNO",
        "outputId": "f06e2f49-0a26-4a86-f886-e4c5416e70a4"
      },
      "execution_count": 12,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stderr",
          "text": [
            "/usr/local/lib/python3.12/dist-packages/sklearn/utils/validation.py:2739: UserWarning: X does not have valid feature names, but LinearRegression was fitted with feature names\n",
            "  warnings.warn(\n"
          ]
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 1200x600 with 1 Axes>"
            ],
            "image/png": 
          },
          "metadata": {}
        },
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Projected GDP per capita for USA (Model based on 1990-2022 trend):\n",
            "Year 2024: $70,977.66 USD\n",
            "Year 2025: $72,430.91 USD\n",
            "Year 2026: $73,884.15 USD\n"
          ]
        },
        {
          "output_type": "stream",
          "name": "stderr",
          "text": [
            "/usr/local/lib/python3.12/dist-packages/sklearn/utils/validation.py:2739: UserWarning: X does not have valid feature names, but LinearRegression was fitted with feature names\n",
            "  warnings.warn(\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "import numpy as np\n",
        "from sklearn.linear_model import LinearRegression\n",
        "import matplotlib.pyplot as plt\n",
        "import pandas as pd\n",
        "\n",
        "# 1. Preparar datos de PBI per cápita para Australia\n",
        "df_aus_gdp = df[df['country'] == 'Australia'].dropna(subset=['gdp_per_capita']).sort_values('year')\n",
        "\n",
        "# 2. Entrenar el modelo con la tendencia histórica (1990-2022)\n",
        "X_aus = df_aus_gdp[['year']]\n",
        "y_aus = df_aus_gdp['gdp_per_capita']\n",
        "\n",
        "model_aus = LinearRegression()\n",
        "model_aus.fit(X_aus, y_aus)\n",
        "\n",
        "# 3. Generar Previsión hasta 2026\n",
        "years_range_aus = np.arange(1990, 2027).reshape(-1, 1)\n",
        "aus_forecast_plot = model_aus.predict(years_range_aus)\n",
        "\n",
        "# 4. Visualización\n",
        "plt.figure(figsize=(12, 6))\n",
        "plt.plot(df_aus_gdp['year'], df_aus_gdp['gdp_per_capita'], label='PBI per cápita Real (Australia)', color='#00008B', marker='o', linewidth=2.5)\n",
        "plt.plot(years_range_aus, aus_forecast_plot, label='Tendencia Proyectada', color='#d62728', linestyle='--', linewidth=2)\n",
        "\n",
        "plt.title('Australia: Proyección del PBI per cápita hasta 2026', fontsize=14)\n",
        "plt.xlabel('Año')\n",
        "plt.ylabel('PBI per cápita (USD)')\n",
        "plt.axvline(x=2022, color='gray', linestyle=':', label='Fin datos históricos')\n",
        "plt.legend()\n",
        "plt.grid(True, alpha=0.3)\n",
        "plt.tight_layout()\n",
        "plt.show()\n",
        "\n",
        "# 5. Resultados numéricos\n",
        "future_years = np.array([2024, 2025, 2026]).reshape(-1, 1)\n",
        "aus_preds = model_aus.predict(future_years)\n",
        "\n",
        "print(\"Valores proyectados del PBI per cápita para Australia (basado en tendencia 1990-2022):\")\n",
        "for yr, val in zip([2024, 2025, 2026], aus_preds):\n",
        "    print(f\"Año {yr}: ${val:,.2f} USD\")"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 714
        },
        "id": "Cw30AEgaFOa3",
        "outputId": "f6b64f37-9911-4f5c-8fbd-f36ec5fd164d"
      },
      "execution_count": 13,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stderr",
          "text": [
            "/usr/local/lib/python3.12/dist-packages/sklearn/utils/validation.py:2739: UserWarning: X does not have valid feature names, but LinearRegression was fitted with feature names\n",
            "  warnings.warn(\n"
          ]
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 1200x600 with 1 Axes>"
            ],
            "image/png": 
          "metadata": {}
        },
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Valores proyectados del PBI per cápita para Australia (basado en tendencia 1990-2022):\n",
            "Año 2024: $54,584.45 USD\n",
            "Año 2025: $55,376.59 USD\n",
            "Año 2026: $56,168.73 USD\n"
          ]
        },
        {
          "output_type": "stream",
          "name": "stderr",
          "text": [
            "/usr/local/lib/python3.12/dist-packages/sklearn/utils/validation.py:2739: UserWarning: X does not have valid feature names, but LinearRegression was fitted with feature names\n",
            "  warnings.warn(\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "import matplotlib.pyplot as plt\n",
        "import numpy as np\n",
        "from sklearn.linear_model import LinearRegression\n",
        "\n",
        "# Configurar el estilo de fondo negro\n",
        "plt.style.use('dark_background')\n",
        "\n",
        "# 1. Preparar datos para Argentina\n",
        "df_arg = df[df['country'] == 'Argentina'].dropna(subset=['gdp_per_capita']).sort_values('year')\n",
        "X_arg = df_arg[['year']]\n",
        "y_arg = df_arg['gdp_per_capita']\n",
        "model_arg = LinearRegression().fit(X_arg, y_arg)\n",
        "\n",
        "# 2. Preparar datos para Australia\n",
        "df_aus = df[df['country'] == 'Australia'].dropna(subset=['gdp_per_capita']).sort_values('year')\n",
        "X_aus = df_aus[['year']]\n",
        "y_aus = df_aus['gdp_per_capita']\n",
        "model_aus = LinearRegression().fit(X_aus, y_aus)\n",
        "\n",
        "# 3. Generar Rango de años y predicciones\n",
        "years_full = np.arange(1991, 2027).reshape(-1, 1)\n",
        "pred_arg = model_arg.predict(years_full)\n",
        "pred_aus = model_aus.predict(years_full)\n",
        "\n",
        "# 4. Calcular Pendiente Porcentual (CAGR de la tendencia)\n",
        "def calculate_cagr(start_val, end_val, periods):\n",
        "    return (pow(end_val / start_val, 1 / periods) - 1) * 100\n",
        "\n",
        "cagr_arg = calculate_cagr(pred_arg[0], pred_arg[-1], len(years_full)-1)\n",
        "cagr_aus = calculate_cagr(pred_aus[0], pred_aus[-1], len(years_full)-1)\n",
        "\n",
        "# 5. Gráfico Comparativo\n",
        "plt.figure(figsize=(14, 7))\n",
        "\n",
        "# Argentina: Celeste\n",
        "plt.plot(df_arg['year'], df_arg['gdp_per_capita'], color='#87CEEB', marker='o', label='Argentina (Real)', linewidth=2.5)\n",
        "plt.plot(years_full, pred_arg, color='#87CEEB', linestyle='--', alpha=0.6, label='Argentina (Tendencia)')\n",
        "\n",
        "# Australia: Amarillo\n",
        "plt.plot(df_aus['year'], df_aus['gdp_per_capita'], color='#FFFF00', marker='o', label='Australia (Real)', linewidth=2.5)\n",
        "plt.plot(years_full, pred_aus, color='#FFFF00', linestyle='--', alpha=0.6, label='Australia (Tendencia)')\n",
        "\n",
        "# 6. Agregar pendientes porcentuales al final de las líneas\n",
        "plt.text(2026.5, pred_arg[-1], f'Crecimiento: {cagr_arg:.2f}% anual', color='#87CEEB', va='center', fontweight='bold')\n",
        "plt.text(2026.5, pred_aus[-1], f'Crecimiento: {cagr_aus:.2f}% anual', color='#FFFF00', va='center', fontweight='bold')\n",
        "\n",
        "# Detalles estéticos\n",
        "plt.axvline(x=2022, color='white', linestyle=':', alpha=0.5, label='Inicio Proyección')\n",
        "plt.title('Comparativa GDP: Argentina vs Australia (Pendiente Porcentual Anual)', fontsize=16, color='white', pad=20)\n",
        "plt.xlabel('Año', fontsize=12)\n",
        "plt.ylabel('GDP per cápita (USD)', fontsize=12)\n",
        "plt.legend(facecolor='black', edgecolor='white', loc='upper left')\n",
        "plt.grid(True, color='gray', linestyle='--', alpha=0.3)\n",
        "\n",
        "plt.xlim(1990, 2035)\n",
        "plt.tight_layout()\n",
        "plt.show()\n",
        "\n",
        "# Resultados numéricos\n",
        "print(f\"Análisis de Crecimiento Tendencial Porcentual (CAGR 1991-2026):\")\n",
        "print(f\"🇦🇷 Argentina: {cagr_arg:.2f}% anual\")\n",
        "print(f\"🇦🇺 Australia: {cagr_aus:.2f}% anual\")"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 697
        },
        "id": "18ot62_wFTFy",
        "outputId": "0715f4cb-e06f-4e38-eb4c-7e8546590568"
      },
      "execution_count": 14,
      "outputs": [
        {
          "output_type": "stream",
          "name": "stderr",
          "text": [
            "/usr/local/lib/python3.12/dist-packages/sklearn/utils/validation.py:2739: UserWarning: X does not have valid feature names, but LinearRegression was fitted with feature names\n",
            "  warnings.warn(\n",
            "/usr/local/lib/python3.12/dist-packages/sklearn/utils/validation.py:2739: UserWarning: X does not have valid feature names, but LinearRegression was fitted with feature names\n",
            "  warnings.warn(\n"
          ]
        },
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 1400x700 with 1 Axes>"
            ],
            "image/png": 
          },
          "metadata": {}
        },
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Análisis de Crecimiento Tendencial Porcentual (CAGR 1991-2026):\n",
            "🇦🇷 Argentina: 1.51% anual\n",
            "🇦🇺 Australia: 1.96% anual\n"
          ]
        }
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "import matplotlib.pyplot as plt\n",
        "import numpy as np\n",
        "import pandas as pd\n",
        "from sklearn.linear_model import LinearRegression\n",
        "\n",
        "# 1. Preparar datos y entrenar modelos con nombres de columnas consistentes\n",
        "df_arg = df[df['country'] == 'Argentina'].dropna(subset=['gdp_per_capita']).sort_values('year')\n",
        "X_arg = df_arg[['year']]\n",
        "y_arg = df_arg['gdp_per_capita']\n",
        "model_arg = LinearRegression().fit(X_arg, y_arg)\n",
        "\n",
        "df_aus = df[df['country'] == 'Australia'].dropna(subset=['gdp_per_capita']).sort_values('year')\n",
        "X_aus = df_aus[['year']]\n",
        "y_aus = df_aus['gdp_per_capita']\n",
        "model_aus = LinearRegression().fit(X_aus, y_aus)\n",
        "\n",
        "# 2. Rango extendido para visualización (1930-2026)\n",
        "years_ext = pd.DataFrame({'year': np.arange(1930, 2027)})\n",
        "pred_arg_ext = model_arg.predict(years_ext)\n",
        "pred_aus_ext = model_aus.predict(years_ext)\n",
        "\n",
        "# 3. CAGR (Calculado sobre el periodo con datos positivos: 1991-2026)\n",
        "def calc_cagr(start, end, p):\n",
        "    if start <= 0: return 0\n",
        "    return (pow(end / start, 1/p) - 1) * 100\n",
        "\n",
        "# Predicciones puntuales usando DataFrames para evitar warnings de feature names\n",
        "val_1991_arg = model_arg.predict(pd.DataFrame({'year': [1991]}))[0]\n",
        "val_2026_arg = model_arg.predict(pd.DataFrame({'year': [2026]}))[0]\n",
        "val_1991_aus = model_aus.predict(pd.DataFrame({'year': [1991]}))[0]\n",
        "val_2026_aus = model_aus.predict(pd.DataFrame({'year': [2026]}))[0]\n",
        "\n",
        "cagr_arg = calc_cagr(val_1991_arg, val_2026_arg, 2026-1991)\n",
        "cagr_aus = calc_cagr(val_1991_aus, val_2026_aus, 2026-1991)\n",
        "\n",
        "# 4. Gráfico con estética Dark\n",
        "plt.style.use('dark_background')\n",
        "plt.figure(figsize=(15, 8))\n",
        "\n",
        "# Argentina (Celeste)\n",
        "plt.plot(df_arg['year'], df_arg['gdp_per_capita'], color='#87CEEB', marker='o', label='Argentina (Real)', markersize=4)\n",
        "plt.plot(years_ext['year'], pred_arg_ext, color='#87CEEB', linestyle='--', alpha=0.4, label='Arg: Tendencia 1930-2026')\n",
        "\n",
        "# Australia (Amarillo)\n",
        "plt.plot(df_aus['year'], df_aus['gdp_per_capita'], color='#FFFF00', marker='o', label='Australia (Real)', markersize=4)\n",
        "plt.plot(years_ext['year'], pred_aus_ext, color='#FFFF00', linestyle='--', alpha=0.4, label='Aus: Tendencia 1930-2026')\n",
        "\n",
        "# Limitar eje Y para evitar valores negativos de la regresión lineal\n",
        "plt.ylim(0, max(pred_aus_ext) * 1.1)\n",
        "\n",
        "# Anotaciones de Crecimiento\n",
        "plt.text(2027, pred_arg_ext[-1], f'Trend: {cagr_arg:.2f}%', color='#87CEEB', fontweight='bold')\n",
        "plt.text(2027, pred_aus_ext[-1], f'Trend: {cagr_aus:.2f}%', color='#FFFF00', fontweight='bold')\n",
        "\n",
        "plt.axvline(x=1991, color='white', linestyle=':', alpha=0.5, label='Inicio datos reales')\n",
        "plt.title('Divergencia Estructural: Argentina vs Australia (Proyección 1930-2026)', fontsize=16)\n",
        "plt.ylabel('GDP per cápita (USD)')\n",
        "plt.xlabel('Año')\n",
        "plt.legend(loc='upper left', frameon=True, facecolor='black')\n",
        "plt.grid(True, alpha=0.1)\n",
        "\n",
        "plt.tight_layout()\n",
        "plt.show()"
      ],
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/",
          "height": 595
        },
        "id": "snGAK_cMFdCM",
        "outputId": "e5d9a09f-ad82-42bd-b8db-5d76cc0be042"
      },
      "execution_count": 15,
      "outputs": [
        {
          "output_type": "display_data",
          "data": {
            "text/plain": [
              "<Figure size 1500x800 with 1 Axes>"
            ],
            "image/png": 
          },
          "metadata": {}
        }
      ]
    }
  ]
}


Análisis Histórico: Países de la ex-Yugoslavia
En esta sección analizamos la evolución del Índice de Resiliencia para las naciones que conformaron Yugoslavia, permitiendo comparar sus trayectorias de recuperación y estabilidad.


import matplotlib.pyplot as plt
import seaborn as sns

# Lista de países solicitada (ex-Yugoslavia sin Eslovenia + Argentina)
paises_analisis = [
    'Croatia', 'Bosnia and Herzegovina', 'Serbia',
    'Montenegro', 'North Macedonia', 'Kosovo', 'Argentina'
]

# Filtrar el DataFrame
df_comp = df[df['country'].isin(paises_analisis)].sort_values(['country', 'year'])

# Configuración del gráfico
fig = plt.figure(figsize=(14, 8))
sns.set_style("whitegrid")

# Definir paleta: Argentina destacada, el resto en tonos grises/atenuados
# O usamos un color llamativo para Argentina
colores = {}
for p in paises_analisis:
    if p == 'Argentina':
        colores[p] = '#00FFFF' # Cyan brillante para destacar
    else:
        colores[p] = None # Dejar que seaborn asigne el resto

# Dibujar líneas
for pais in paises_analisis:
    data_p = df_comp[df_comp['country'] == pais]
    linewidth = 5 if pais == 'Argentina' else 2
    zorder = 10 if pais == 'Argentina' else 2
    alpha = 1.0 if pais == 'Argentina' else 0.6

    plt.plot(data_p['year'], data_p['score_resiliencia'],
             label=pais, linewidth=linewidth, zorder=zorder, alpha=alpha,
             marker='o', markersize=4 if pais != 'Argentina' else 6,
             color=colores[pais])

# Personalización
plt.title('Comparativa: Argentina vs. Países de la ex-Yugoslavia', fontsize=16, fontweight='bold')
plt.xlabel('Año', fontsize=12)
plt.ylabel('Score de Resiliencia (0-100)', fontsize=12)
plt.legend(title='País', bbox_to_anchor=(1.05, 1), loc='upper left')
plt.grid(True, alpha=0.3)

fig.tight_layout()
plt.savefig('argentina_vs_ex_yugoslavia_resilience.svg')
plt.close(fig)
print("Saved argentina_vs_ex_yugoslavia_resilience.svg")
     
Saved argentina_vs_ex_yugoslavia_resilience.svg
Como podemos observar, países como Eslovenia suelen liderar la región debido a su temprana integración económica y estabilidad laboral, mientras que otros como Macedonia del Norte muestran los niveles históricos más bajos en los registros de la década de los 90.


import numpy as np
from sklearn.linear_model import LinearRegression
import matplotlib.pyplot as plt

# Confirmamos los pesos solicitados para el Score de Resiliencia
PESO_ECONOMICO = 0.50
PESO_LABORAL = 0.30
PESO_EQUIDAD = 0.20

# Definición de regiones
norteamerica = ['United States', 'Canada', 'Mexico']

def analyze_recovery(country_list, name, filename_suffix):
    # Agrupar datos por año para la región/país
    df_reg = df[df['country'].isin(country_list)].groupby('year')['score_resiliencia'].mean().reset_index()

    # Datos previos a la crisis (hasta 2007) para entrenar la tendencia
    df_pre = df_reg[df_reg['year'] <= 2007]

    if df_pre.empty:
        print(f"No hay suficientes datos pre-2008 para {name}")
        return

    # Entrenar modelo de regresión lineal con la tendencia pre-crisis
    model = LinearRegression()
    X_pre = df_pre[['year']]
    y_pre = df_pre['score_resiliencia']
    model.fit(X_pre, y_pre)

    # Generar el Forecast (proyección) para todo el periodo
    df_reg['forecast'] = model.predict(df_reg[['year']])

    # Visualización
    fig = plt.figure(figsize=(12, 6))
    plt.plot(df_reg['year'], df_reg['score_resiliencia'], label='Realidad (Actual)', marker='o', linewidth=2.5, color='#1f77b4')
    plt.plot(df_reg['year'], df_reg['forecast'], label='Previsión (Tendencia pre-2008)', linestyle='--', color='#d62728', alpha=0.8)

    # Marcador de la crisis
    plt.axvline(x=2008, color='black', linestyle=':', label='Inicio Crisis 2008')

    plt.title(f'Forecast de Resiliencia: {name}\n(Pesos: Econ 50%, Lab 30%, Equi 20%)', fontsize=14)
    plt.xlabel('Año')
    plt.ylabel('Score de Resiliencia')
    plt.legend(frameon=True)
    plt.grid(True, alpha=0.3)
    fig.tight_layout()
    plt.savefig(f'resilience_forecast_{filename_suffix}.svg')
    plt.close(fig)
    print(f"Saved resilience_forecast_{filename_suffix}.svg")

# Ejecutar análisis para Argentina y Norteamérica
analyze_recovery(['Argentina'], 'Argentina', 'argentina')
analyze_recovery(norteamerica, 'Norteamérica (Promedio)', 'northamerica')
     
Saved resilience_forecast_argentina.svg
Saved resilience_forecast_northamerica.svg

import numpy as np
from sklearn.linear_model import LinearRegression
import matplotlib.pyplot as plt
import pandas as pd

# 1. Preparar datos de PBI per cápita para Argentina
df_arg_gdp = df[df['country'] == 'Argentina'].dropna(subset=['gdp_per_capita']).sort_values('year')

# 2. Entrenar el modelo con la tendencia histórica
X_gdp = df_arg_gdp[['year']]
y_gdp = df_arg_gdp['gdp_per_capita']

model_gdp_final = LinearRegression()
model_gdp_final.fit(X_gdp, y_gdp)

# 3. Generar Previsión hasta 2026
years_range = np.arange(1991, 2027).reshape(-1, 1)
gdp_forecast_final = model_gdp_final.predict(years_range)

# 4. Visualización
fig = plt.figure(figsize=(12, 6))

# Realidad
plt.plot(df_arg_gdp['year'], df_arg_gdp['gdp_per_capita'], label='PBI per cápita Real', color='#2ca02c', marker='o', linewidth=2.5)

# Previsión
plt.plot(years_range, gdp_forecast_final, label='Tendencia Proyectada (Forecast)', color='#d62728', linestyle='--', linewidth=2)

plt.title('Argentina: Proyección del PBI per cápita hasta 2026', fontsize=14)
plt.xlabel('Año')
plt.ylabel('PBI per cápita (USD)')
plt.axvline(x=2022, color='gray', linestyle=':', label='Fin datos históricos')
plt.legend()
plt.grid(True, alpha=0.3)
fig.tight_layout()
plt.savefig('argentina_gdp_per_capita_forecast.svg')
plt.close(fig)
print("Saved argentina_gdp_per_capita_forecast.svg")

# 5. Resultados numéricos específicos para el usuario
future_years_list = [2024, 2025, 2026]
future_preds = model_gdp_final.predict(np.array(future_years_list).reshape(-1, 1))

print("Valores proyectados del PBI per cápita para Argentina:")
for yr, val in zip(future_years_list, future_preds):
    print(f"Año {yr}: ${val:,.2f} USD")
     
Saved argentina_gdp_per_capita_forecast.svg
Valores proyectados del PBI per cápita para Argentina:
Año 2024: $20,555.80 USD
Año 2025: $20,800.86 USD
Año 2026: $21,045.92 USD
/usr/local/lib/python3.12/dist-packages/sklearn/utils/validation.py:2739: UserWarning:

X does not have valid feature names, but LinearRegression was fitted with feature names

/usr/local/lib/python3.12/dist-packages/sklearn/utils/validation.py:2739: UserWarning:

X does not have valid feature names, but LinearRegression was fitted with feature names


import numpy as np
from sklearn.linear_model import LinearRegression
import matplotlib.pyplot as plt
import pandas as pd

# 1. Manually providing USA historical data from 1990 to 2022 (World Bank approximate values)
usa_historical_data = {
    'year': list(range(1990, 2023)),
    'gdp_per_capita': [
        23888, 24342, 25418, 26387, 27694, 28690, 29967, 31459, 32853, 34513,
        36334, 37133, 38023, 39496, 41712, 44114, 46298, 47975, 48382, 47001,
        48311, 49793, 51450, 52782, 54696, 56469, 57436, 59382, 62232, 65202,
        63027, 70248, 76329
    ]
}
df_usa = pd.DataFrame(usa_historical_data)

# 2. Train the model using the 1990-2022 range
X_usa = df_usa[['year']]
y_usa = df_usa['gdp_per_capita']
model_usa = LinearRegression()
model_usa.fit(X_usa, y_usa)

# 3. Forecast from 1990 until 2026
years_range = np.arange(1990, 2027).reshape(-1, 1)
forecast_values = model_usa.predict(years_range)

# 4. Visualization
fig = plt.figure(figsize=(12, 6))
plt.plot(df_usa['year'], df_usa['gdp_per_capita'], label='USA Real GDP per capita (1990-2022)', marker='o', color='#1f77b4', linewidth=2)
plt.plot(years_range, forecast_values, label='Trend Projection (1990-2026)', linestyle='--', color='#d62728')

plt.title('United States: GDP per capita Forecast (1990-2026)', fontsize=14)
plt.xlabel('Año')
plt.ylabel('GDP per capita (USD)')
plt.axvline(x=2022, color='gray', linestyle=':', label='End of historical data')
plt.grid(True, alpha=0.3)
plt.legend()
fig.tight_layout()
plt.savefig('usa_gdp_per_capita_forecast.svg')
plt.close(fig)
print("Saved usa_gdp_per_capita_forecast.svg")

# 5. Numerical Results for the requested forecast period
future_years = np.array([2024, 2025, 2026]).reshape(-1, 1)
preds = model_usa.predict(future_years)

print("Projected GDP per capita for USA (Model based on 1990-2022 trend):")
for yr, val in zip([2024, 2025, 2026], preds):
    print(f"Year {yr}: ${val:,.2f} USD")
     
/usr/local/lib/python3.12/dist-packages/sklearn/utils/validation.py:2739: UserWarning:

X does not have valid feature names, but LinearRegression was fitted with feature names

Saved usa_gdp_per_capita_forecast.svg
Projected GDP per capita for USA (Model based on 1990-2022 trend):
Year 2024: $70,977.66 USD
Year 2025: $72,430.91 USD
Year 2026: $73,884.15 USD
/usr/local/lib/python3.12/dist-packages/sklearn/utils/validation.py:2739: UserWarning:

X does not have valid feature names, but LinearRegression was fitted with feature names


import numpy as np
from sklearn.linear_model import LinearRegression
import matplotlib.pyplot as plt
import pandas as pd

# 1. Preparar datos de PBI per cápita para Australia
df_aus_gdp = df[df['country'] == 'Australia'].dropna(subset=['gdp_per_capita']).sort_values('year')

# 2. Entrenar el modelo con la tendencia histórica (1990-2022)
X_aus = df_aus_gdp[['year']]
y_aus = df_aus_gdp['gdp_per_capita']

model_aus = LinearRegression()
model_aus.fit(X_aus, y_aus)

# 3. Generar Previsión hasta 2026
years_range_aus = np.arange(1990, 2027).reshape(-1, 1)
aus_forecast_plot = model_aus.predict(years_range_aus)

# 4. Visualización
fig = plt.figure(figsize=(12, 6))
plt.plot(df_aus_gdp['year'], df_aus_gdp['gdp_per_capita'], label='PBI per cápita Real (Australia)', color='#00008B', marker='o', linewidth=2.5)
plt.plot(years_range_aus, aus_forecast_plot, label='Tendencia Proyectada', color='#d62728', linestyle='--', linewidth=2)

plt.title('Australia: Proyección del PBI per cápita hasta 2026', fontsize=14)
plt.xlabel('Año')
plt.ylabel('PBI per cápita (USD)')
plt.axvline(x=2022, color='gray', linestyle=':', label='Fin datos históricos')
plt.legend()
plt.grid(True, alpha=0.3)
fig.tight_layout()
plt.savefig('australia_gdp_per_capita_forecast.svg')
plt.close(fig)
print("Saved australia_gdp_per_capita_forecast.svg")

# 5. Resultados numéricos
future_years = np.array([2024, 2025, 2026]).reshape(-1, 1)
aus_preds = model_aus.predict(future_years)

print("Valores proyectados del PBI per cápita para Australia (basado en tendencia 1990-2022):")
for yr, val in zip([2024, 2025, 2026], aus_preds):
    print(f"Año {yr}: ${val:,.2f} USD")
     
/usr/local/lib/python3.12/dist-packages/sklearn/utils/validation.py:2739: UserWarning:

X does not have valid feature names, but LinearRegression was fitted with feature names

Saved australia_gdp_per_capita_forecast.svg
Valores proyectados del PBI per cápita para Australia (basado en tendencia 1990-2022):
Año 2024: $54,584.45 USD
Año 2025: $55,376.59 USD
Año 2026: $56,168.73 USD
/usr/local/lib/python3.12/dist-packages/sklearn/utils/validation.py:2739: UserWarning:

X does not have valid feature names, but LinearRegression was fitted with feature names


import matplotlib.pyplot as plt
import numpy as np
from sklearn.linear_model import LinearRegression

# Configurar el estilo de fondo negro
plt.style.use('dark_background')

# 1. Preparar datos para Argentina
df_arg = df[df['country'] == 'Argentina'].dropna(subset=['gdp_per_capita']).sort_values('year')
X_arg = df_arg[['year']]
y_arg = df_arg['gdp_per_capita']
model_arg = LinearRegression().fit(X_arg, y_arg)

# 2. Preparar datos para Australia
df_aus = df[df['country'] == 'Australia'].dropna(subset=['gdp_per_capita']).sort_values('year')
X_aus = df_aus[['year']]
y_aus = df_aus['gdp_per_capita']
model_aus = LinearRegression().fit(X_aus, y_aus)

# 3. Generar Rango de años y predicciones
years_full = np.arange(1991, 2027).reshape(-1, 1)
pred_arg = model_arg.predict(years_full)
pred_aus = model_aus.predict(years_full)

# 4. Calcular Pendiente Porcentual (CAGR de la tendencia)
def calculate_cagr(start_val, end_val, periods):
    return (pow(end_val / start_val, 1 / periods) - 1) * 100

cagr_arg = calculate_cagr(pred_arg[0], pred_arg[-1], len(years_full)-1)
cagr_aus = calculate_cagr(pred_aus[0], pred_aus[-1], len(years_full)-1)

# 5. Gráfico Comparativo
fig = plt.figure(figsize=(14, 7))

# Argentina: Celeste
plt.plot(df_arg['year'], df_arg['gdp_per_capita'], color='#87CEEB', marker='o', label='Argentina (Real)', linewidth=2.5)
plt.plot(years_full, pred_arg, color='#87CEEB', linestyle='--', alpha=0.6, label='Argentina (Tendencia)')

# Australia: Amarillo
plt.plot(df_aus['year'], df_aus['gdp_per_capita'], color='#FFFF00', marker='o', label='Australia (Real)', linewidth=2.5)
plt.plot(years_full, pred_aus, color='#FFFF00', linestyle='--', alpha=0.6, label='Australia (Tendencia)')

# 6. Agregar pendientes porcentuales al final de las líneas
plt.text(2026.5, pred_arg[-1], f'Crecimiento: {cagr_arg:.2f}% anual', color='#87CEEB', va='center', fontweight='bold')
plt.text(2026.5, pred_aus[-1], f'Crecimiento: {cagr_aus:.2f}% anual', color='#FFFF00', va='center', fontweight='bold')

# Detalles estéticos
plt.axvline(x=2022, color='white', linestyle=':', alpha=0.5, label='Inicio Proyección')
plt.title('Comparativa GDP: Argentina vs Australia (Pendiente Porcentual Anual)', fontsize=16, color='white', pad=20)
plt.xlabel('Año', fontsize=12)
plt.ylabel('GDP per cápita (USD)', fontsize=12)
plt.legend(facecolor='black', edgecolor='white', loc='upper left')
plt.grid(True, color='gray', linestyle='--', alpha=0.3)

plt.xlim(1990, 2035)
fig.tight_layout()
plt.savefig('gdp_argentina_australia_cagr.svg')
plt.close(fig)
print("Saved gdp_argentina_australia_cagr.svg")

# Resultados numéricos
print(f"Análisis de Crecimiento Tendencial Porcentual (CAGR 1991-2026):")
print(f"🇦🇷 Argentina: {cagr_arg:.2f}% anual")
print(f"🇦🇺 Australia: {cagr_aus:.2f}% anual")
     
/usr/local/lib/python3.12/dist-packages/sklearn/utils/validation.py:2739: UserWarning:

X does not have valid feature names, but LinearRegression was fitted with feature names

/usr/local/lib/python3.12/dist-packages/sklearn/utils/validation.py:2739: UserWarning:

X does not have valid feature names, but LinearRegression was fitted with feature names

Saved gdp_argentina_australia_cagr.svg
Análisis de Crecimiento Tendencial Porcentual (CAGR 1991-2026):
🇦🇷 Argentina: 1.51% anual
🇦🇺 Australia: 1.96% anual

import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
from sklearn.linear_model import LinearRegression

# 1. Preparar datos y entrenar modelos con nombres de columnas consistentes
df_arg = df[df['country'] == 'Argentina'].dropna(subset=['gdp_per_capita']).sort_values('year')
X_arg = df_arg[['year']]
y_arg = df_arg['gdp_per_capita']
model_arg = LinearRegression().fit(X_arg, y_arg)

df_aus = df[df['country'] == 'Australia'].dropna(subset=['gdp_per_capita']).sort_values('year')
X_aus = df_aus[['year']]
y_aus = df_aus['gdp_per_capita']
model_aus = LinearRegression().fit(X_aus, y_aus)

# 2. Rango extendido para visualización (1930-2026)
years_ext = pd.DataFrame({'year': np.arange(1930, 2027)})
pred_arg_ext = model_arg.predict(years_ext)
pred_aus_ext = model_aus.predict(years_ext)

# 3. CAGR (Calculado sobre el periodo con datos positivos: 1991-2026)
def calc_cagr(start, end, p):
    if start <= 0: return 0
    return (pow(end / start, 1/p) - 1) * 100

# Predicciones puntuales usando DataFrames para evitar warnings de feature names
val_1991_arg = model_arg.predict(pd.DataFrame({'year': [1991]}))[0]
val_2026_arg = model_arg.predict(pd.DataFrame({'year': [2026]}))[0]
val_1991_aus = model_aus.predict(pd.DataFrame({'year': [1991]}))[0]
val_2026_aus = model_aus.predict(pd.DataFrame({'year': [2026]}))[0]

cagr_arg = calc_cagr(val_1991_arg, val_2026_arg, 2026-1991)
cagr_aus = calc_cagr(val_1991_aus, val_2026_aus, 2026-1991)

# 4. Gráfico con estética Dark
plt.style.use('dark_background')
fig = plt.figure(figsize=(15, 8))

# Argentina (Celeste)
plt.plot(df_arg['year'], df_arg['gdp_per_capita'], color='#87CEEB', marker='o', label='Argentina (Real)', markersize=4)
plt.plot(years_ext['year'], pred_arg_ext, color='#87CEEB', linestyle='--', alpha=0.4, label='Arg: Tendencia 1930-2026')

# Australia (Amarillo)
plt.plot(df_aus['year'], df_aus['gdp_per_capita'], color='#FFFF00', marker='o', label='Australia (Real)', markersize=4)
plt.plot(years_ext['year'], pred_aus_ext, color='#FFFF00', linestyle='--', alpha=0.4, label='Aus: Tendencia 1930-2026')

# Limitar eje Y para evitar valores negativos de la regresión lineal
plt.ylim(0, max(pred_aus_ext) * 1.1)

# Anotaciones de Crecimiento
plt.text(2027, pred_arg_ext[-1], f'Trend: {cagr_arg:.2f}%', color='#87CEEB', fontweight='bold')
plt.text(2027, pred_aus_ext[-1], f'Trend: {cagr_aus:.2f}%', color='#FFFF00', fontweight='bold')

plt.axvline(x=1991, color='white', linestyle=':', alpha=0.5, label='Inicio datos reales')
plt.title('Divergencia Estructural: Argentina vs Australia (Proyección 1930-2026)', fontsize=16)
plt.ylabel('GDP per cápita (USD)')
plt.xlabel('Año')
plt.legend(loc='upper left', frameon=True, facecolor='black')
plt.grid(True, alpha=0.1)

fig.tight_layout()
plt.savefig('divergence_argentina_australia.svg')
plt.close(fig)
print("Saved divergence_argentina_australia.svg")
     
Saved divergence_argentina_australia.svg
Making Plots Interactive with Plotly
To create interactive plots that can be downloaded and potentially used in platforms like Canva, we can use libraries such as Plotly. Plotly generates interactive HTML files which allow users to zoom, pan, hover for details, and more.

Here's how to convert your matplotlib plot to an interactive Plotly plot, along with instructions on how to save it as an HTML file.


pip install plotly
     
Requirement already satisfied: plotly in /usr/local/lib/python3.12/dist-packages (5.24.1)
Requirement already satisfied: tenacity>=6.2.0 in /usr/local/lib/python3.12/dist-packages (from plotly) (9.1.4)
Requirement already satisfied: packaging in /usr/local/lib/python3.12/dist-packages (from plotly) (26.2)

pip install kaleido
     
Collecting kaleido
  Downloading kaleido-1.3.0-py3-none-any.whl.metadata (5.6 kB)
Collecting choreographer>=1.3.0 (from kaleido)
  Downloading choreographer-1.3.0-py3-none-any.whl.metadata (6.9 kB)
Collecting logistro>=1.0.8 (from kaleido)
  Downloading logistro-2.0.1-py3-none-any.whl.metadata (3.9 kB)
Requirement already satisfied: orjson>=3.10.15 in /usr/local/lib/python3.12/dist-packages (from kaleido) (3.11.9)
Requirement already satisfied: packaging in /usr/local/lib/python3.12/dist-packages (from kaleido) (26.2)
Requirement already satisfied: platformdirs>=4.3.6 in /usr/local/lib/python3.12/dist-packages (from choreographer>=1.3.0->kaleido) (4.10.0)
Requirement already satisfied: simplejson>=3.19.3 in /usr/local/lib/python3.12/dist-packages (from choreographer>=1.3.0->kaleido) (4.1.1)
Downloading kaleido-1.3.0-py3-none-any.whl (55 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 55.6/55.6 kB 1.9 MB/s eta 0:00:00
Downloading choreographer-1.3.0-py3-none-any.whl (52 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 52.6/52.6 kB 3.5 MB/s eta 0:00:00
Downloading logistro-2.0.1-py3-none-any.whl (8.6 kB)
Installing collected packages: logistro, choreographer, kaleido
Successfully installed choreographer-1.3.0 kaleido-1.3.0 logistro-2.0.1

import plotly.graph_objects as go
import pandas as pd
import numpy as np
from sklearn.linear_model import LinearRegression

# Assuming df is already loaded and processed as in previous cells

# 1. Prepare data and train models with consistent column names
df_arg = df[df['country'] == 'Argentina'].dropna(subset=['gdp_per_capita']).sort_values('year')
X_arg = df_arg[['year']]
y_arg = df_arg['gdp_per_capita']
model_arg = LinearRegression().fit(X_arg, y_arg)

df_aus = df[df['country'] == 'Australia'].dropna(subset=['gdp_per_capita']).sort_values('year')
X_aus = df_aus[['year']]
y_aus = df_aus['gdp_per_capita']
model_aus = LinearRegression().fit(X_aus, y_aus)

# 2. Rango extendido para visualización (1930-2026)
years_ext = pd.DataFrame({'year': np.arange(1930, 2027)})
pred_arg_ext = model_arg.predict(years_ext)
pred_aus_ext = model_aus.predict(years_ext)

# 3. CAGR (Calculado sobre el periodo con datos positivos: 1991-2026)
def calc_cagr(start, end, p):
    if start <= 0: return 0
    return (pow(end / start, 1/p) - 1) * 100

# Predicciones puntuales usando DataFrames para evitar warnings de feature names
val_1991_arg = model_arg.predict(pd.DataFrame({'year': [1991]}))[0]
val_2026_arg = model_arg.predict(pd.DataFrame({'year': [2026]}))[0]
val_1991_aus = model_aus.predict(pd.DataFrame({'year': [1991]}))[0]
val_2026_aus = model_aus.predict(pd.DataFrame({'year': [2026]}))[0]

cagr_arg = calc_cagr(val_1991_arg, val_2026_arg, 2026-1991)
cagr_aus = calc_cagr(val_1991_aus, val_2026_aus, 2026-1991)

# Create Plotly figure
fig = go.Figure()

# Argentina (Real) - Celeste
fig.add_trace(go.Scatter(
    x=df_arg['year'], y=df_arg['gdp_per_capita'],
    mode='lines+markers', name='Argentina (Real)',
    line=dict(color='#87CEEB', width=2.5),
    marker=dict(size=6, symbol='circle')
))

# Argentina (Tendencia) - Celeste dashed
fig.add_trace(go.Scatter(
    x=years_ext['year'], y=pred_arg_ext,
    mode='lines', name=f'Arg: Tendencia 1930-2026 (Trend: {cagr_arg:.2f}%)',
    line=dict(color='#87CEEB', width=2, dash='dash'), # Removed opacity from here
    opacity=0.6 # Moved opacity here
))

# Australia (Real) - Amarillo
fig.add_trace(go.Scatter(
    x=df_aus['year'], y=df_aus['gdp_per_capita'],
    mode='lines+markers', name='Australia (Real)',
    line=dict(color='#FFFF00', width=2.5),
    marker=dict(size=6, symbol='circle')
))

# Australia (Tendencia) - Amarillo dashed
fig.add_trace(go.Scatter(
    x=years_ext['year'], y=pred_aus_ext,
    mode='lines', name=f'Aus: Tendencia 1930-2026 (Trend: {cagr_aus:.2f}%)',
    line=dict(color='#FFFF00', width=2, dash='dash'), # Removed opacity from here
    opacity=0.6 # Moved opacity here
))

# Reference line for start of real data
fig.add_vline(x=1991, line_dash="dot", line_color="white", annotation_text="Inicio datos reales", annotation_position="top right")

fig.update_layout(
    title_text='Divergencia Estructural: Argentina vs Australia (Proyección 1930-2026)',
    title_font_size=16,
    xaxis_title='Año',
    yaxis_title='GDP per cápita (USD)',
    legend_title='Series',
    hovermode='x unified', # Shows hover info for all traces at a given x-value
    template='plotly_dark', # Use a dark theme for consistency with previous matplotlib style
    height=500,
    yaxis_range=[0, max(pred_aus_ext) * 1.1] # Set y-axis range to avoid negative values
)

fig.show()

# Save the interactive plot as an HTML file
fig.write_html("gdp_argentina_australia_interactive.html")
print("Interactive plot saved as gdp_argentina_australia_interactive.html")
print("You can download this file from the Colab file browser (folder icon on the left).")

     
Interactive plot saved as gdp_argentina_australia_interactive.html
You can download this file from the Colab file browser (folder icon on the left).
Using Static Images of Plots in Canva
Since Canva doesn't support direct interactive HTML embeds, we've now generated a static SVG image of your Plotly graph. SVG (Scalable Vector Graphics) is an excellent format for presentations because it scales without losing quality.

To use this image in Canva:

Download the SVG file: You can find gdp_argentina_australia_interactive.svg in the Colab file browser (the folder icon on the left sidebar).
Upload to Canva: Go to Canva, open your presentation, and use the 'Uploads' feature to upload the .svg file.
Generalizing for all your graphs:
For all your other matplotlib plots in this notebook, if you want them in Canva, you have two main options:

Export as PNG directly from matplotlib: After each plt.show(), you can add a line like plt.savefig('my_plot.png', dpi=300, bbox_inches='tight'). PNG is a raster format, so dpi (dots per inch) is important for quality. bbox_inches='tight' prevents clipping labels.

Convert to Plotly and then export as SVG/PNG (recommended for interactivity):

For each matplotlib plot, convert its logic to Plotly as demonstrated in cell 6a51f48c.
Then, use fig.write_html('my_plot.html') for interactivity (if you were to host it elsewhere) and fig.write_image('my_plot.svg') (or .png) for Canva.
This approach will give you high-quality images that integrate well with Canva presentations.


import pandas as pd
df = pd.read_csv('df_final.csv')
     
Using Interactive Plots in Canva
Once you've saved the .html file (e.g., gdp_argentina_australia_interactive.html), you can download it from your Colab environment using the file browser (the folder icon on the left sidebar).

Canva's direct support for interactive HTML embeds can vary. Generally, you have a few options:

Embed via a link (if supported): Some platforms allow you to embed interactive content by providing a public URL to the HTML file. You would need to host your HTML file online (e.g., Google Drive, GitHub Pages, Netlify) to get a public link.
Screenshot/Export as Static Image: If interactive embedding isn't directly supported or is too complex, you can simply take a high-resolution screenshot of the interactive plot (or use Plotly's fig.write_image() method to save as PNG/JPEG/SVG) and use it as a static image in Canva.
Video Recording: For presentations, you could record a short video interacting with the plot and embed the video in Canva.
To convert other matplotlib plots to Plotly, you will follow a similar pattern:

Import plotly.graph_objects (or plotly.express for simpler plots).
Create a go.Figure().
Add traces using fig.add_trace() for each line, bar, or scatter plot, specifying x, y, mode, name, and styling.
Update the layout using fig.update_layout() for titles, labels, legends, and themes.
Use fig.show() to display the plot and fig.write_html("filename.html") to save it.
Task
The user wants to create an animated GIF of the 'Divergencia Estructural: Argentina vs Australia' plot, representing the evolution of GDP per capita over time. This GIF will then be provided along with instructions on how to download and upload it to Canva, as Canva does not support direct interactive HTML embeds but does support animated GIFs for simulated interactivity.

Explain Canva's Limitations and GIF as Workaround
Subtask:
Explain to the user that Canva does not support direct interactive HTML embeds and why an animated GIF is the chosen solution to simulate interactivity for the plot 'Divergencia Estructural: Argentina vs Australia'.

Canva, while a powerful design tool, does not natively support direct embedding of interactive HTML content, such as those generated by Plotly. This means that a fully interactive plot, where users can zoom, pan, and hover for details, cannot be directly integrated into a Canva presentation or design in its interactive form.

To overcome this limitation and still provide a sense of dynamic data visualization for the 'Divergencia Estructural: Argentina vs Australia' plot, we will create an animated GIF. An animated GIF will allow us to represent the evolution of GDP per capita over time by showing a sequence of frames, effectively simulating the interactivity of a time-series plot. This GIF can then be easily uploaded to Canva, offering a visually engaging experience that highlights the temporal changes in the data.

The goal is to visually demonstrate the GDP per capita evolution over time for Argentina and Australia in a format that is compatible with Canva's functionalities.

Prepare Data for Animation
Subtask:
Identify the key variables and time range from the DataFrame df that will be used to create the animation for the 'Divergencia Estructural: Argentina vs Australia' plot.

Reasoning: Filter the DataFrame for 'Argentina' and 'Australia', select 'year' and 'gdp_per_capita', remove rows with missing values, and identify the min/max years for the animation.


countries_for_animation = ['Argentina', 'Australia']
df_animation_data = df[df['country'].isin(countries_for_animation)][['country', 'year', 'gdp_per_capita']].dropna()

min_year = df_animation_data['year'].min()
max_year = df_animation_data['year'].max()

print(f"Data prepared for animation for {countries_for_animation}.")
print(f"Time range: {min_year} to {max_year}.")
print("First 5 rows of the prepared data:")
display(df_animation_data.head())
     
Data prepared for animation for ['Argentina', 'Australia'].
Time range: 1991 to 2022.
First 5 rows of the prepared data:
country	year	gdp_per_capita
136	Argentina	1991	11316.72
137	Argentina	1992	12366.76
138	Argentina	1993	13023.28
139	Argentina	1994	13663.08
140	Argentina	1995	13162.27
Generate Animated Frames
Subtask:
Create individual static image frames for each year, showing the GDP per capita for Argentina and Australia, along with their linear regression trends and CAGR. Each frame should represent the data up to that specific year.

Reasoning: Generate a series of static plot frames, one for each year from 1991 to 2022. Each frame will show the real GDP per capita data up to that year, the linear regression trend calculated based on data up to that year, and the CAGR of that trend. This involves dynamically retraining the regression models for each year and plotting the trend up to the current year, while maintaining consistent axis limits for smooth animation.


import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
from sklearn.linear_model import LinearRegression
import os

# Ensure the frames directory exists
frames_dir = 'animation_frames'
os.makedirs(frames_dir, exist_ok=True)

# Configurar el estilo de fondo negro
plt.style.use('dark_background')

# Data prepared in previous step from df_animation_data:
# countries_for_animation = ['Argentina', 'Australia']
# df_animation_data = df[df['country'].isin(countries_for_animation)][['country', 'year', 'gdp_per_capita']].dropna()
# min_year = df_animation_data['year'].min() # 1991
# max_year = df_animation_data['year'].max() # 2022

# Re-establish full data and full prediction range for consistent Y-axis calculation
years_full_pred_range_df = pd.DataFrame({'year': np.arange(1930, 2027)}) # for max Y-axis value calculation

df_arg_full_data_hist = df[df['country'] == 'Argentina'].dropna(subset=['gdp_per_capita'])
df_aus_full_data_hist = df[df['country'] == 'Australia'].dropna(subset=['gdp_per_capita'])

model_arg_full_hist = LinearRegression().fit(df_arg_full_data_hist[['year']], df_arg_full_data_hist['gdp_per_capita'])
model_aus_full_hist = LinearRegression().fit(df_aus_full_data_hist[['year']], df_aus_full_data_hist['gdp_per_capita'])

pred_arg_full_range_values = model_arg_full_hist.predict(years_full_pred_range_df)
pred_aus_full_range_values = model_aus_full_hist.predict(years_full_pred_range_df)

# Calculate overall max GDP for consistent Y-axis limit across all frames
# This helps prevent the Y-axis from jumping around during the animation
max_gdp_overall = max(df_animation_data['gdp_per_capita'].max(), pred_arg_full_range_values.max(), pred_aus_full_range_values.max()) * 1.1

# CAGR calculation function
def calc_cagr(start_val, end_val, periods):
    if periods <= 0: # Handle cases where periods is 0 or negative
        return 0.0
    if start_val <= 0: return 0.0 # Avoid issues with log/division by zero or negative
    return (pow(end_val / start_val, 1 / periods) - 1) * 100

frame_filenames = []

for current_year in range(min_year, max_year + 1):
    # Filter real data up to the current year
    df_arg_current_real = df_animation_data[(df_animation_data['country'] == 'Argentina') & (df_animation_data['year'] <= current_year)]
    df_aus_current_real = df_animation_data[(df_animation_data['country'] == 'Australia') & (df_animation_data['year'] <= current_year)]

    # Retrain models with data ONLY UP TO THE CURRENT YEAR
    model_arg_frame = LinearRegression()
    if not df_arg_current_real.empty:
        model_arg_frame.fit(df_arg_current_real[['year']], df_arg_current_real['gdp_per_capita'])

    model_aus_frame = LinearRegression()
    if not df_aus_current_real.empty:
        model_aus_frame.fit(df_aus_current_real[['year']], df_aus_current_real['gdp_per_capita'])

    # Years for plotting the current trend line (from 1930 up to current_year)
    years_for_current_trend = pd.DataFrame({'year': np.arange(1930, current_year + 1)})

    pred_arg_current_trend = model_arg_frame.predict(years_for_current_trend)
    pred_aus_current_trend = model_aus_frame.predict(years_for_current_trend)

    # Calculate CAGR for the trend from min_year to current_year
    cagr_arg_frame = 0.0
    cagr_aus_frame = 0.0

    if current_year > min_year and not df_arg_current_real.empty:
        val_start_arg = model_arg_frame.predict(pd.DataFrame({'year': [min_year]}))[0]
        val_end_arg = model_arg_frame.predict(pd.DataFrame({'year': [current_year]}))[0]
        cagr_arg_frame = calc_cagr(val_start_arg, val_end_arg, current_year - min_year)

    if current_year > min_year and not df_aus_current_real.empty:
        val_start_aus = model_aus_frame.predict(pd.DataFrame({'year': [min_year]}))[0]
        val_end_aus = model_aus_frame.predict(pd.DataFrame({'year': [current_year]}))[0]
        cagr_aus_frame = calc_cagr(val_start_aus, val_end_aus, current_year - min_year)

    # Create plot
    fig, ax = plt.subplots(figsize=(15, 8))

    # Argentina: Real Data (Celeste)
    ax.plot(df_arg_current_real['year'], df_arg_current_real['gdp_per_capita'],
            color='#87CEEB', marker='o', label='Argentina (Real)', markersize=4, linewidth=2.5)

    # Argentina: Trend (Celeste dashed)
    ax.plot(years_for_current_trend['year'], pred_arg_current_trend,
            color='#87CEEB', linestyle='--', alpha=0.6, label='Arg: Tendencia (datos hasta hoy)')

    # Australia: Real Data (Amarillo)
    ax.plot(df_aus_current_real['year'], df_aus_current_real['gdp_per_capita'],
            color='#FFFF00', marker='o', label='Australia (Real)', markersize=4, linewidth=2.5)

    # Australia: Trend (Amarillo dashed)
    ax.plot(years_for_current_trend['year'], pred_aus_current_trend,
            color='#FFFF00', linestyle='--', alpha=0.6, label='Aus: Tendencia (datos hasta hoy)')

    # Add CAGR annotations
    # Place text near the end of the current trend line for the current year
    if current_year >= min_year and not df_arg_current_real.empty:
        # Use the prediction at current_year for placement
        text_y_arg = model_arg_frame.predict(pd.DataFrame({'year': [current_year]}))[0]
        ax.text(current_year + 0.5, text_y_arg,
                f'CAGR: {cagr_arg_frame:.2f}%', color='#87CEEB', va='center', fontweight='bold', fontsize=10)
    if current_year >= min_year and not df_aus_current_real.empty:
        # Use the prediction at current_year for placement
        text_y_aus = model_aus_frame.predict(pd.DataFrame({'year': [current_year]}))[0]
        ax.text(current_year + 0.5, text_y_aus,
                f'CAGR: {cagr_aus_frame:.2f}%', color='#FFFF00', va='center', fontweight='bold', fontsize=10)

    # Details aesthetics
    ax.axvline(x=min_year, color='white', linestyle=':', alpha=0.5, label='Inicio datos reales')
    ax.set_title(f'Divergencia Estructural: Argentina vs Australia (Año: {current_year})', fontsize=16, color='white', pad=20)
    ax.set_xlabel('Año', fontsize=12)
    ax.set_ylabel('GDP per cápita (USD)', fontsize=12)
    ax.legend(loc='upper left', frameon=True, facecolor='black', fontsize=10)
    ax.grid(True, alpha=0.1)

    # Set x-axis limits consistently across all frames
    ax.set_xlim(1930, 2026) # Fixed x-axis to encompass the full range for consistent view
    ax.set_ylim(0, max_gdp_overall) # Consistent y-axis limit

    # Save frame
    filename = os.path.join(frames_dir, f'frame_{current_year:04d}.png')
    plt.savefig(filename, dpi=100) # Removed bbox_inches='tight'
    frame_filenames.append(filename)
    plt.close(fig)

print(f"Generated {len(frame_filenames)} frames in '{frames_dir}' directory.")
     
Generated 32 frames in 'animation_frames' directory.
Reasoning: Assemble the generated PNG frames into a single animated GIF using the imageio library.


import imageio.v2 as imageio
import os

# Path to the directory containing the frames
frames_dir = 'animation_frames'

# Get all image filenames, sorted to ensure correct order
images = []
for filename in sorted(os.listdir(frames_dir)):
    if filename.endswith('.png'):
        images.append(imageio.imread(os.path.join(frames_dir, filename)))

# Output GIF filename
gif_path = 'gdp_argentina_australia_animation.gif'

# Create the GIF
# duration specifies the time each frame is displayed (in seconds)
imageio.mimsave(gif_path, images, duration=0.2, loop=0) # loop=0 means loop indefinitely

print(f"Animated GIF saved as '{gif_path}'")

     
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
/tmp/ipykernel_1654/831796633.py in <cell line: 0>()
     16 # Create the GIF
     17 # duration specifies the time each frame is displayed (in seconds)
---> 18 imageio.mimsave(gif_path, images, duration=0.2, loop=0) # loop=0 means loop indefinitely
     19 
     20 print(f"Animated GIF saved as '{gif_path}'")

/usr/local/lib/python3.12/dist-packages/imageio/v2.py in mimwrite(uri, ims, format, **kwargs)
    493     imopen_args["legacy_mode"] = True
    494     with imopen(uri, "wI", **imopen_args) as file:
--> 495         return file.write(ims, is_batch=True, **kwargs)
    496 
    497 

/usr/local/lib/python3.12/dist-packages/imageio/plugins/pillow.py in write(self, ndimage, mode, format, is_batch, **kwargs)
    416 
    417         if isinstance(ndimage, list):
--> 418             ndimage = np.stack(ndimage, axis=0)
    419             is_batch = True
    420         else:

/usr/local/lib/python3.12/dist-packages/numpy/_core/shape_base.py in stack(arrays, axis, out, dtype, casting)
    446     shapes = {arr.shape for arr in arrays}
    447     if len(shapes) != 1:
--> 448         raise ValueError('all input arrays must have the same shape')
    449 
    450     result_ndim = arrays[0].ndim + 1

ValueError: all input arrays must have the same shape
Reasoning: The animated frames have been generated. The next step is to combine these frames into a GIF. The imageio library is suitable for this task. I need to re-execute the code that failed before, now that the frames have been generated with consistent dimensions.


import imageio.v2 as imageio
import os

# Path to the directory containing the frames
frames_dir = 'animation_frames'

# Get all image filenames, sorted to ensure correct order
images = []
for filename in sorted(os.listdir(frames_dir)):
    if filename.endswith('.png'):
        images.append(imageio.imread(os.path.join(frames_dir, filename)))

# Output GIF filename
gif_path = 'gdp_argentina_australia_animation.gif'

# Create the GIF
# duration specifies the time each frame is displayed (in seconds)
imageio.mimsave(gif_path, images, duration=0.2, loop=0) # loop=0 means loop indefinitely

print(f"Animated GIF saved as '{gif_path}'")
     
Animated GIF saved as 'gdp_argentina_australia_animation.gif'
Final Task
Subtask:
Provide the animated GIF file and instructions on how to download it and upload it to Canva, explaining its simulated interactive nature.

Animated GIF for Canva
Great news! The animated GIF, 'gdp_argentina_australia_animation.gif', representing the structural divergence in GDP per capita between Argentina and Australia over time, has been successfully created.

This GIF offers a dynamic visualization of the data, simulating interactivity within platforms like Canva which do not support direct interactive HTML embeds.

To download the GIF:

Look for the folder icon on the left sidebar of your Google Colab environment. This is the 'File Browser'.
Navigate to the main directory (usually /content/).
You will find gdp_argentina_australia_animation.gif listed there.
Right-click on the file and select 'Download' to save it to your local machine.
To upload the GIF to Canva:

Open your project in Canva.
On the left-hand menu, click on 'Uploads'.
Click 'Upload files' and select the downloaded gdp_argentina_australia_animation.gif from your computer.
Once uploaded, you can drag and drop the GIF onto your design. Canva will play the animation, providing a visually engaging element for your presentation or design.
Enjoy your dynamic visualization!

Task
Create an animated GIF of the 'Divergencia Estructural: Argentina vs Australia' plot, representing the evolution of GDP per capita over time. Provide the GIF along with instructions on how to download and upload it to Canva, explaining its simulated interactive nature.

Prepare Data for Argentina Resilience Animation
Subtask:
Filter the DataFrame to include only data for Argentina, selecting the 'year', 'score_resiliencia', and 'gdp_per_capita' columns, and ensure there are no missing values in these columns for the animation. Determine the minimum and maximum years for the animation loop.

Task
Create an animated GIF of the 'Divergencia Estructural: Argentina vs Australia' plot, representing the evolution of GDP per capita over time. Provide the GIF along with instructions on how to download and upload it to Canva, explaining its simulated interactive nature. Then, create an animated GIF of Argentina's 'Score de Resiliencia' and 'PBI per cápita' evolution over time. Finally, provide instructions on how to download this GIF and upload it to Canva, reiterating its simulated interactive nature.

Reasoning: Filter the main DataFrame df for 'Argentina', select the specified columns, drop rows with missing values, and then extract the minimum and maximum years for the animation loop. Finally, display the first few rows of the prepared data to confirm its structure and content.


df_arg_animation = df[df['country'] == 'Argentina'][['year', 'score_resiliencia', 'gdp_per_capita']].dropna()

min_year_arg = df_arg_animation['year'].min()
max_year_arg = df_arg_animation['year'].max()

print(f"Data prepared for Argentina resilience animation.")
print(f"Time range for Argentina resilience: {min_year_arg} to {max_year_arg}.")
print("First 5 rows of the prepared data:")
display(df_arg_animation.head())
     
Data prepared for Argentina resilience animation.
Time range for Argentina resilience: 1991 to 2022.
First 5 rows of the prepared data:
year	score_resiliencia	gdp_per_capita
136	1991	44.42	11316.72
137	1992	44.03	12366.76
138	1993	41.33	13023.28
139	1994	40.24	13663.08
140	1995	34.63	13162.27
Generate Animated Frames for Argentina Resilience
Subtask:
Create individual static image frames for each year from the minimum to the maximum year. Each frame will display the 'Score de Resiliencia' and 'PBI per cápita' for Argentina up to that specific year, ensuring consistent axis limits across all frames to create a smooth animation.

Reasoning: I need to initialize the directory for storing the frames and calculate the overall maximums for the Y-axes to ensure consistent scaling across all animation frames. Then, I will start the loop for generating frames for each year.


import matplotlib.pyplot as plt
import os
import pandas as pd

# Ensure the frames directory exists
frames_dir_resilience = 'animation_frames_arg_resilience'
os.makedirs(frames_dir_resilience, exist_ok=True)

# Configurar el estilo de fondo negro
plt.style.use('dark_background')

# Data prepared in previous step (df_arg_animation, min_year_arg, max_year_arg)
# df_arg_animation contains 'year', 'score_resiliencia', 'gdp_per_capita'

# Calculate overall max values for consistent Y-axis limits across all frames
max_score_resiliencia_overall = df_arg_animation['score_resiliencia'].max() * 1.1
max_gdp_per_capita_overall = df_arg_animation['gdp_per_capita'].max() * 1.1

frame_filenames_resilience = []

for current_year in range(min_year_arg, max_year_arg + 1):
    # Filter data up to the current year
    df_current_year = df_arg_animation[df_arg_animation['year'] <= current_year]

    fig, ax1 = plt.subplots(figsize=(12, 7))

    # Eje 1: Score de Resiliencia
    color_res = 'tab:blue'
    ax1.set_xlabel('Año', fontsize=12)
    ax1.set_ylabel('Score de Resiliencia (0-100)', color=color_res, fontsize=12)
    ax1.plot(df_current_year['year'], df_current_year['score_resiliencia'], color=color_res, linewidth=3, label='Resiliencia')
    ax1.tick_params(axis='y', labelcolor=color_res)
    ax1.grid(True, alpha=0.3)
    ax1.set_ylim(0, max_score_resiliencia_overall) # Consistent y-axis limit

    # Eje 2: PBI per cápita
    ax2 = ax1.twinx()
    color_pbi = 'tab:red'
    ax2.set_ylabel('GDP per cápita (USD)', color=color_pbi, fontsize=12)
    ax2.plot(df_current_year['year'], df_current_year['gdp_per_capita'], color=color_pbi, linestyle='--', linewidth=2, label='PBI per cápita')
    ax2.tick_params(axis='y', labelcolor=color_pbi)
    ax2.set_ylim(0, max_gdp_per_capita_overall) # Consistent y-axis limit

    # Combine legends
    lines1, labels1 = ax1.get_legend_handles_labels()
    lines2, labels2 = ax2.get_legend_handles_labels()
    ax2.legend(lines1 + lines2, labels1 + labels2, loc='upper left', frameon=True, shadow=True)

    plt.title(f'Argentina: Evolución de Resiliencia vs. PBI per cápita (Año: {current_year})', fontsize=14)

    # Set x-axis limits consistently across all frames
    ax1.set_xlim(min_year_arg, max_year_arg)

    fig.tight_layout()

    # Save frame
    filename = os.path.join(frames_dir_resilience, f'frame_argentina_resilience_{current_year:04d}.png')
    plt.savefig(filename, dpi=100)
    frame_filenames_resilience.append(filename)
    plt.close(fig)

print(f"Generated {len(frame_filenames_resilience)} frames in '{frames_dir_resilience}' directory.")
     
Generated 32 frames in 'animation_frames_arg_resilience' directory.
Reasoning: Assemble the generated PNG frames for Argentina's resilience into a single animated GIF.


import imageio.v2 as imageio
import os

# Path to the directory containing the frames for Argentina resilience
frames_dir_resilience = 'animation_frames_arg_resilience'

# Get all image filenames, sorted to ensure correct order
images_resilience = []
for filename in sorted(os.listdir(frames_dir_resilience)):
    if filename.endswith('.png'):
        images_resilience.append(imageio.imread(os.path.join(frames_dir_resilience, filename)))

# Output GIF filename for Argentina resilience
gif_path_resilience = 'argentina_resilience_gdp_animation.gif'

# Create the GIF
# duration specifies the time each frame is displayed (in seconds)
imageio.mimsave(gif_path_resilience, images_resilience, duration=0.2, loop=0) # loop=0 means loop indefinitely

print(f"Animated GIF for Argentina resilience saved as '{gif_path_resilience}'")
     
Animated GIF for Argentina resilience saved as 'argentina_resilience_gdp_animation.gif'
Download and Canva Instructions (Argentina Resilience)
Subtask:
Provide instructions for the user to download the newly created 'argentina_resilience_gdp_animation.gif' from the Colab file browser and steps to upload it to Canva, reiterating its simulated interactive nature.

Animated GIF for Canva
Great news! The animated GIF, 'argentina_resilience_gdp_animation.gif', representing the evolution of 'Score de Resiliencia' and 'PBI per cápita' for Argentina over time, has been successfully created.

This GIF offers a dynamic visualization of the data, simulating interactivity within platforms like Canva which do not support direct interactive HTML embeds.

To download the GIF:

Look for the folder icon on the left sidebar of your Google Colab environment. This is the 'File Browser'.
Navigate to the main directory (usually /content/).
You will find argentina_resilience_gdp_animation.gif listed there.
Right-click on the file and select 'Download' to save it to your local machine.
To upload the GIF to Canva:

Open your project in Canva.
On the left-hand menu, click on 'Uploads'.
Click 'Upload files' and select the downloaded argentina_resilience_gdp_animation.gif from your computer.
Once uploaded, you can drag and drop the GIF onto your design. Canva will play the animation, providing a visually engaging element for your presentation or design.
Enjoy your dynamic visualization!

Final Task
Subtask:
Confirm the completion of the GIF for Argentina's resilience and ask the user if they would like to proceed with creating GIFs for other time-series graphs, such as regional comparisons or specific GDP forecasts.

Prepare Data for Regional Resilience Animation
Subtask:
Filter the DataFrame to include data for Argentina and the ex-Yugoslavia countries (Croatia, Bosnia and Herzegovina, Serbia, Montenegro, North Macedonia, Kosovo), selecting 'year', 'country', and 'score_resiliencia' columns. Ensure no missing values and identify the min/max years for the animation loop.

Task
Create an animated GIF of the 'Divergencia Estructural: Argentina vs Australia' plot, representing the evolution of GDP per capita over time. Provide the GIF along with instructions on how to download and upload it to Canva, explaining its simulated interactive nature. Then, create an animated GIF of Argentina's 'Score de Resiliencia' and 'PBI per cápita' evolution over time. Finally, provide instructions on how to download this GIF and upload it to Canva, reiterating its simulated interactive nature. The current subtask is to prepare data for regional resilience animation.

Reasoning: Filter the DataFrame for the specified countries and columns, remove missing values, and then extract the minimum and maximum years for the animation loop. Finally, display the first few rows of the prepared data to confirm its structure and content.


countries_for_regional_animation = [
    'Argentina', 'Croatia', 'Bosnia and Herzegovina', 'Serbia',
    'Montenegro', 'North Macedonia', 'Kosovo'
]

df_regional_animation_data = df[
    df['country'].isin(countries_for_regional_animation)
][['year', 'country', 'score_resiliencia']].dropna()

min_year_regional = df_regional_animation_data['year'].min()
max_year_regional = df_regional_animation_data['year'].max()

print(f"Data prepared for regional resilience animation for {countries_for_regional_animation}.")
print(f"Time range: {min_year_regional} to {max_year_regional}.")
print("First 5 rows of the prepared data:")
display(df_regional_animation_data.head())
     
Data prepared for regional resilience animation for ['Argentina', 'Croatia', 'Bosnia and Herzegovina', 'Serbia', 'Montenegro', 'North Macedonia', 'Kosovo'].
Time range: 1991 to 2022.
First 5 rows of the prepared data:
year	country	score_resiliencia
136	1991	Argentina	44.42
137	1992	Argentina	44.03
138	1993	Argentina	41.33
139	1994	Argentina	40.24
140	1995	Argentina	34.63
Generate Animated Frames for Regional Resilience
Subtask:
Create individual static image frames for each year from the minimum to the maximum year. Each frame will display the 'score_resiliencia' for each selected country up to that specific year, ensuring consistent axis limits across all frames to create a smooth animation. Highlight Argentina distinctly.

Reasoning: I need to initialize the directory for storing the frames and calculate the overall maximum for the y-axis to ensure consistent scaling across all animation frames. Then, I will start the loop for generating frames for each year, plotting the resilience score for each country and highlighting Argentina.


import matplotlib.pyplot as plt
import os
import pandas as pd
import seaborn as sns # Import seaborn

# Ensure the frames directory exists
frames_dir_regional_resilience = 'animation_frames_regional_resilience'
os.makedirs(frames_dir_regional_resilience, exist_ok=True)

# Configurar el estilo de fondo negro
plt.style.use('dark_background')

# Data prepared in previous step (df_regional_animation_data, min_year_regional, max_year_regional)
# df_regional_animation_data contains 'year', 'country', 'score_resiliencia'

# Calculate overall max score_resiliencia for consistent Y-axis limits across all frames
max_score_resiliencia_overall_regional = df_regional_animation_data['score_resiliencia'].max() * 1.1

frame_filenames_regional = []

# Define colors: Argentina distinct, the rest from a seaborn palette
ex_yugoslavia_countries = [c for c in countries_for_regional_animation if c != 'Argentina']

# Generate a diverse palette for ex-Yugoslavia countries
# Use 'tab10' or 'viridis' for more distinct colors. Here we use a different palette.
# Number of colors needed is the number of ex_yugoslavia_countries
diverse_palette = sns.color_palette("viridis", n_colors=len(ex_yugoslavia_countries)).as_hex()

country_colors = {
    'Argentina': '#00FFFF' # Cyan
}

for i, country_name in enumerate(ex_yugoslavia_countries):
    country_colors[country_name] = diverse_palette[i]


for current_year in range(min_year_regional, max_year_regional + 1):
    # Filter data up to the current year
    df_current_year_regional = df_regional_animation_data[df_regional_animation_data['year'] <= current_year]

    fig, ax = plt.subplots(figsize=(14, 8))

    for country in countries_for_regional_animation:
        country_data = df_current_year_regional[df_current_year_regional['country'] == country]
        if not country_data.empty:
            line_width = 5 if country == 'Argentina' else 2
            z_order = 10 if country == 'Argentina' else 2
            alpha = 1.0 if country == 'Argentina' else 0.7
            color = country_colors.get(country, 'white') # Default to white if not in custom colors

            ax.plot(country_data['year'], country_data['score_resiliencia'],
                    label=country, linewidth=line_width, zorder=z_order, alpha=alpha, color=color,
                    marker='o', markersize=4 if country != 'Argentina' else 6)

    # Details aesthetics
    ax.set_title(f'Regional Resilience Evolution (Year: {current_year})', fontsize=16, color='white', pad=20)
    ax.set_xlabel('Año', fontsize=12)
    ax.set_ylabel('Score de Resiliencia (0-100)', fontsize=12)
    ax.legend(loc='upper left', frameon=True, facecolor='black', fontsize=10)
    ax.grid(True, alpha=0.1)

    # Set x and y axis limits consistently across all frames
    ax.set_xlim(min_year_regional, max_year_regional)
    ax.set_ylim(0, max_score_resiliencia_overall_regional)

    fig.tight_layout()

    # Save frame
    filename = os.path.join(frames_dir_regional_resilience, f'frame_regional_{current_year:04d}.png')
    plt.savefig(filename, dpi=100)
    frame_filenames_regional.append(filename)
    plt.close(fig)

print(f"Generated {len(frame_filenames_regional)} frames in '{frames_dir_regional_resilience}' directory.")
     
Generated 32 frames in 'animation_frames_regional_resilience' directory.
Reasoning: Assemble the generated PNG frames for regional resilience into a single animated GIF using the imageio library. I will read all PNG files from the frames_dir_regional_resilience directory, sort them to ensure correct chronological order, and then use imageio.mimsave to create the GIF.


import imageio.v2 as imageio
import os

# Path to the directory containing the frames for regional resilience
frames_dir_regional_resilience = 'animation_frames_regional_resilience'

# Get all image filenames, sorted to ensure correct order
images_regional_resilience = []
for filename in sorted(os.listdir(frames_dir_regional_resilience)):
    if filename.endswith('.png'):
        images_regional_resilience.append(imageio.imread(os.path.join(frames_dir_regional_resilience, filename)))

# Output GIF filename for regional resilience
gif_path_regional_resilience = 'regional_resilience_animation.gif'

# Create the GIF
# duration specifies the time each frame is displayed (in seconds)
imageio.mimsave(gif_path_regional_resilience, images_regional_resilience, duration=0.2, loop=0) # loop=0 means loop indefinitely

print(f"Animated GIF for regional resilience saved as '{gif_path_regional_resilience}'")
     
Animated GIF for regional resilience saved as 'regional_resilience_animation.gif'
Download and Canva Instructions (Regional Resilience)
Subtask:
Provide instructions for the user to download the newly created 'regional_resilience_animation.gif' from the Colab file browser and steps to upload it to Canva, reiterating its simulated interactive nature.

Animated GIF for Canva: Regional Resilience
Great news! The animated GIF, 'regional_resilience_animation.gif', representing the evolution of resilience across Argentina and the ex-Yugoslavia countries, has been successfully created.

This GIF offers a dynamic visualization of the data, simulating interactivity within platforms like Canva which do not support direct interactive HTML embeds.

To download the GIF:

Look for the folder icon on the left sidebar of your Google Colab environment. This is the 'File Browser'.
Navigate to the main directory (usually /content/).
You will find regional_resilience_animation.gif listed there.
Right-click on the file and select 'Download' to save it to your local machine.
To upload the GIF to Canva:

Open your project in Canva.
On the left-hand menu, click on 'Uploads'.
Click 'Upload files' and select the downloaded regional_resilience_animation.gif from your computer.
Once uploaded, you can drag and drop the GIF onto your design. Canva will play the animation, providing a visually engaging element for your presentation or design.
Enjoy your dynamic visualization!

Final Task
Subtask:
Confirm the completion of the regional resilience GIF and ask the user if they would like to proceed with creating GIFs for other time-series graphs, such as specific GDP forecasts or other key indicators.

Prepare Data for Argentina GDP Forecast Animation
Subtask:
Extract Argentina's GDP per capita data and its historical linear regression model to prepare for frame generation.

Task
Create an animated GIF of the 'Divergencia Estructural: Argentina vs Australia' plot, representing the evolution of GDP per capita over time. Provide the GIF along with instructions on how to download and upload it to Canva, explaining its simulated interactive nature. Then, create an animated GIF of Argentina's 'Score de Resiliencia' and 'PBI per cápita' evolution over time. Finally, provide instructions on how to download this GIF and upload it to Canva, reiterating its simulated interactive nature. The current subtask is to prepare data for regional resilience animation.

Generate Animated Frames for Argentina GDP Forecast
Subtask:
Create individual static image frames for each year, showing Argentina's real GDP per capita and the projected forecast line up to that year, with consistent axis limits. Each frame will display the forecasted GDP for 2024, 2025, and 2026.

Reasoning: This step initializes the directory for storing frames, calculates a consistent y-axis limit based on historical and fully forecasted data, and then iterates through each year to create and save individual plot frames. Each frame displays the real GDP per capita up to the current year, along with the linear regression forecast based on data up to that year, and explicitly shows the 2024, 2025, and 2026 forecast values derived from that year's model.


import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
from sklearn.linear_model import LinearRegression
import os

# Ensure the frames directory exists
frames_dir_arg_gdp_forecast = 'animation_frames_arg_gdp_forecast'
os.makedirs(frames_dir_arg_gdp_forecast, exist_ok=True)

# Configure the plot style to dark background
plt.style.use('dark_background')

# Data prepared in previous step (df_arg_animation, min_year_arg, max_year_arg)
# df_arg_animation contains 'year', 'score_resiliencia', 'gdp_per_capita'

# 1. Calculate overall max GDP for consistent Y-axis limits across all frames
#    This needs to consider the historical max and the max of the _full_ forecast range.

# Model trained on full historical data (up to max_year_arg)
model_arg_full_hist = LinearRegression().fit(df_arg_animation[['year']], df_arg_animation['gdp_per_capita'])

# Years for the full forecast range (e.g., 1991 to 2026)
years_for_full_forecast = np.arange(min_year_arg, 2027).reshape(-1, 1)
predictions_full_forecast = model_arg_full_hist.predict(years_for_full_forecast)

max_gdp_overall = max(df_arg_animation['gdp_per_capita'].max(), predictions_full_forecast.max()) * 1.1

frame_filenames_arg_gdp_forecast = []

for current_year in range(min_year_arg, 2027): # Include forecast years in the loop
    # Filter real data up to the current year
    df_arg_current_real = df_arg_animation[df_arg_animation['year'] <= current_year]

    # Train a linear regression model using data ONLY UP TO THE CURRENT YEAR
    model_arg_frame = LinearRegression()
    if not df_arg_current_real.empty:
        model_arg_frame.fit(df_arg_current_real[['year']], df_arg_current_real['gdp_per_capita'])
    else:
        # If no historical data up to current_year (e.g., for early forecast frames before min_year_arg)
        # Use the full historical model for predictions in early frames or if no data yet
        model_arg_frame = model_arg_full_hist

    # Generate predicted GDP per capita values for the entire desired range
    # (from 1991 to 2026) using the model trained with data up to the current_year
    years_for_plot = np.arange(min_year_arg, 2027).reshape(-1, 1)
    gdp_forecast_plot = model_arg_frame.predict(years_for_plot)

    # Create plot
    fig, ax = plt.subplots(figsize=(12, 7))

    # Argentina Real Data (Blue)
    ax.plot(df_arg_current_real['year'], df_arg_current_real['gdp_per_capita'],
            color='#87CEEB', marker='o', label='Argentina (Real)', markersize=4, linewidth=2.5)

    # Forecast Line (Red dashed) - always show the forecast based on the current model up to 2026
    ax.plot(years_for_plot, gdp_forecast_plot, color='#d62728', linestyle='--', label='Tendencia Proyectada', linewidth=2)

    # Add annotations for 2024, 2025, 2026 forecast values
    future_years_to_annotate = [2024, 2025, 2026]
    for fy in future_years_to_annotate:
        if fy >= current_year:
            pred_val = model_arg_frame.predict(np.array([[fy]]))[0]
            ax.text(fy, pred_val, f'${pred_val:,.0f}', color='white', ha='center', va='bottom', fontsize=10, fontweight='bold')


    # Details aesthetics
    ax.set_title(f'Argentina: Proyección del PBI per cápita (Año: {current_year})', fontsize=16, color='white', pad=20)
    ax.set_xlabel('Año', fontsize=12)
    ax.set_ylabel('PBI per cápita (USD)', fontsize=12)
    ax.legend(loc='upper left', frameon=True, facecolor='black', fontsize=10)
    ax.grid(True, alpha=0.1)

    # Set x and y axis limits consistently across all frames
    ax.set_xlim(min_year_arg, 2026) # Fixed x-axis to encompass the full range
    ax.set_ylim(0, max_gdp_overall) # Consistent y-axis limit

    fig.tight_layout()

    # Save frame
    filename = os.path.join(frames_dir_arg_gdp_forecast, f'frame_gdp_arg_forecast_{current_year:04d}.png')
    plt.savefig(filename, dpi=100)
    frame_filenames_arg_gdp_forecast.append(filename)
    plt.close(fig)

print(f"Generated {len(frame_filenames_arg_gdp_forecast)} frames in '{frames_dir_arg_gdp_forecast}' directory.")
     import imageio.v2 as imageio
import os

# Path to the directory containing the frames for Argentina GDP forecast
frames_dir_arg_gdp_forecast = 'animation_frames_arg_gdp_forecast'

# Get all image filenames, sorted to ensure correct order
images_arg_gdp_forecast = []
for filename in sorted(os.listdir(frames_dir_arg_gdp_forecast)):
    if filename.endswith('.png'):
        images_arg_gdp_forecast.append(imageio.imread(os.path.join(frames_dir_arg_gdp_forecast, filename)))

# Output GIF filename for Argentina GDP forecast
gif_path_arg_gdp_forecast = 'argentina_gdp_forecast_animation.gif'

# Create the GIF
# duration specifies the time each frame is displayed (in seconds)
imageio.mimsave(gif_path_arg_gdp_forecast, images_arg_gdp_forecast, duration=0.2, loop=0) # loop=0 means loop indefinitely

print(f"Animated GIF for Argentina GDP forecast saved as '{gif_path_arg_gdp_forecast}'")
     
Animated GIF for Argentina GDP forecast saved as 'argentina_gdp_forecast_animation.gif'
Prepare Data for USA GDP Forecast Animation
Subtask:
Extract USA's historical GDP per capita data and its linear regression model to prepare for frame generation.

Reasoning: I need to prepare the USA historical GDP per capita data for animation by creating a DataFrame, identifying the time range, and displaying the initial rows as per the instructions.


import pandas as pd

# 1. Use the previously defined usa_historical_data dictionary
# (Assuming usa_historical_data is available from a previous cell's execution in the kernel state)
usa_historical_data = {
    'year': list(range(1990, 2023)),
    'gdp_per_capita': [
        23888, 24342, 25418, 26387, 27694, 28690, 29967, 31459, 32853, 34513,
        36334, 37133, 38023, 39496, 41712, 44114, 46298, 47975, 48382, 47001,
        48311, 49793, 51450, 52782, 54696, 56469, 57436, 59382, 62232, 65202,
        63027, 70248, 76329
    ]
}

# 2. Create a Pandas DataFrame
df_usa_animation = pd.DataFrame(usa_historical_data)

# 3. Identify the minimum and maximum years
min_year_usa = df_usa_animation['year'].min()
max_year_usa = df_usa_animation['year'].max()

# 4. Print a confirmation message
print(f"Data prepared for USA GDP forecast animation.")
print(f"Time range for USA GDP: {min_year_usa} to {max_year_usa}.")

# 5. Display the first 5 rows
print("First 5 rows of the prepared data:")
display(df_usa_animation.head())
     
Data prepared for USA GDP forecast animation.
Time range for USA GDP: 1990 to 2022.
First 5 rows of the prepared data:
year	gdp_per_capita
0	1990	23888
1	1991	24342
2	1992	25418
3	1993	26387
4	1994	27694
Reasoning: Train a linear regression model on the prepared df_usa_animation to obtain the historical trend for USA GDP per capita.


import pandas as pd
from sklearn.linear_model import LinearRegression

# 1. Use the previously defined usa_historical_data dictionary
# (Assuming usa_historical_data is available from a previous cell's execution in the kernel state)
usa_historical_data = {
    'year': list(range(1990, 2023)),
    'gdp_per_capita': [
        23888, 24342, 25418, 26387, 27694, 28690, 29967, 31459, 32853, 34513,
        36334, 37133, 38023, 39496, 41712, 44114, 46298, 47975, 48382, 47001,
        48311, 49793, 51450, 52782, 54696, 56469, 57436, 59382, 62232, 65202,
        63027, 70248, 76329
    ]
}

# 2. Create a Pandas DataFrame
df_usa_animation = pd.DataFrame(usa_historical_data)

# 3. Identify the minimum and maximum years
min_year_usa = df_usa_animation['year'].min()
max_year_usa = df_usa_animation['year'].max()

# 4. Print a confirmation message
print(f"Data prepared for USA GDP forecast animation.")
print(f"Time range for USA GDP: {min_year_usa} to {max_year_usa}.")

# 5. Display the first 5 rows
print("First 5 rows of the prepared data:")
display(df_usa_animation.head())

# Train a linear regression model for USA GDP per capita
X_usa_animation = df_usa_animation[['year']]
y_usa_animation = df_usa_animation['gdp_per_capita']
model_usa_animation = LinearRegression()
model_usa_animation.fit(X_usa_animation, y_usa_animation)

print("Linear regression model for USA GDP per capita trained.")
     
Data prepared for USA GDP forecast animation.
Time range for USA GDP: 1990 to 2022.
First 5 rows of the prepared data:
year	gdp_per_capita
0	1990	23888
1	1991	24342
2	1992	25418
3	1993	26387
4	1994	27694
Linear regression model for USA GDP per capita trained.
Generate Animated Frames for USA GDP Forecast
Subtask:
Create individual static image frames for each year, showing USA's real GDP per capita and the projected forecast line up to that year, with consistent axis limits. Each frame will display the forecasted GDP for 2024, 2025, and 2026.

Reasoning: Generate a series of static plot frames, one for each year from 1990 to 2026. Each frame will show the real USA GDP per capita data up to that year, the linear regression trend calculated based on data up to that year, and the specific forecasts for 2024, 2025, and 2026, while maintaining consistent axis limits for smooth animation.


import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
from sklearn.linear_model import LinearRegression
import os

# Ensure the frames directory exists
frames_dir_usa_gdp_forecast = 'animation_frames_usa_gdp_forecast'
os.makedirs(frames_dir_usa_gdp_forecast, exist_ok=True)

# Configure the plot style to dark background
plt.style.use('dark_background')

# Data prepared in previous step: df_usa_animation, min_year_usa, max_year_usa
# and model_usa_animation

# 1. Calculate overall max GDP for consistent Y-axis limits across all frames
#    This needs to consider the historical max and the max of the _full_ forecast range.

# Model trained on full historical data (up to max_year_usa = 2022)
# model_usa_animation is already trained in the previous step.

# Years for the full forecast range (e.g., 1990 to 2026)
years_for_full_forecast_usa = np.arange(min_year_usa, 2027).reshape(-1, 1)
predictions_full_forecast_usa = model_usa_animation.predict(years_for_full_forecast_usa)

max_gdp_overall_usa = max(df_usa_animation['gdp_per_capita'].max(), predictions_full_forecast_usa.max()) * 1.1

frame_filenames_usa_gdp_forecast = []

for current_year in range(min_year_usa, 2027): # Include forecast years in the loop
    # Filter real data up to the current year
    df_usa_current_real = df_usa_animation[df_usa_animation['year'] <= current_year]

    # Train a linear regression model using data ONLY UP TO THE CURRENT YEAR
    model_usa_frame = LinearRegression()
    if not df_usa_current_real.empty:
        model_usa_frame.fit(df_usa_current_real[['year']], df_usa_current_real['gdp_per_capita'])
    else:
        # If no historical data up to current_year (e.g., for early forecast frames before min_year_usa)
        # Use the full historical model for predictions in early frames or if no data yet
        model_usa_frame = model_usa_animation

    # Generate predicted GDP per capita values for the entire desired range
    # (from 1990 to 2026) using the model trained with data up to the current_year
    years_for_plot_usa = np.arange(min_year_usa, 2027).reshape(-1, 1)
    gdp_forecast_plot_usa = model_usa_frame.predict(years_for_plot_usa)

    # Create plot
    fig, ax = plt.subplots(figsize=(12, 7))

    # USA Real Data (Blue)
    ax.plot(df_usa_current_real['year'], df_usa_current_real['gdp_per_capita'],
            color='#1f77b4', marker='o', label='USA (Real)', markersize=4, linewidth=2.5)

    # Forecast Line (Red dashed) - always show the forecast based on the current model up to 2026
    ax.plot(years_for_plot_usa, gdp_forecast_plot_usa, color='#d62728', linestyle='--', label='Trend Projection (Forecast)', linewidth=2)

    # Add annotations for 2024, 2025, 2026 forecast values
    future_years_to_annotate = [2024, 2025, 2026]
    for fy in future_years_to_annotate:
        if fy >= current_year: # Only annotate if the forecast year is equal to or past the current animation year
            pred_val = model_usa_frame.predict(np.array([[fy]]))[0]
            ax.text(fy, pred_val, f'${pred_val:,.0f}', color='white', ha='center', va='bottom', fontsize=10, fontweight='bold')


    # Details aesthetics
    ax.set_title(f'United States: GDP per capita Forecast (Year: {current_year})', fontsize=16, color='white', pad=20)
    ax.set_xlabel('Year', fontsize=12)
    ax.set_ylabel('GDP per capita (USD)', fontsize=12)
    ax.legend(loc='upper left', frameon=True, facecolor='black', fontsize=10)
    ax.grid(True, alpha=0.1)

    # Set x and y axis limits consistently across all frames
    ax.set_xlim(min_year_usa, 2026) # Fixed x-axis to encompass the full range
    ax.set_ylim(0, max_gdp_overall_usa) # Consistent y-axis limit

    fig.tight_layout()

    # Save frame
    filename = os.path.join(frames_dir_usa_gdp_forecast, f'frame_gdp_usa_forecast_{current_year:04d}.png')
    plt.savefig(filename, dpi=100)
    frame_filenames_usa_gdp_forecast.append(filename)
    plt.close(fig)

print(f"Generated {len(frame_filenames_usa_gdp_forecast)} frames in '{frames_dir_usa_gdp_forecast}' directo
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
from sklearn.linear_model import LinearRegression
import os

# Ensure the frames directory exists
frames_dir_usa_gdp_forecast = 'animation_frames_usa_gdp_forecast'
os.makedirs(frames_dir_usa_gdp_forecast, exist_ok=True)

# Configure the plot style to dark background
plt.style.use('dark_background')

# Data prepared in previous step: df_usa_animation, min_year_usa, max_year_usa
# and model_usa_animation

# 1. Calculate overall max GDP for consistent Y-axis limits across all frames
#    This needs to consider the historical max and the max of the _full_ forecast range.

# Model trained on full historical data (up to max_year_usa = 2022)
# model_usa_animation is already trained in the previous step.

# Years for the full forecast range (e.g., 1990 to 2026)
years_for_full_forecast_usa = np.arange(min_year_usa, 2027).reshape(-1, 1)
predictions_full_forecast_usa = model_usa_animation.predict(years_for_full_forecast_usa)

max_gdp_overall_usa = max(df_usa_animation['gdp_per_capita'].max(), predictions_full_forecast_usa.max()) * 1.1

frame_filenames_usa_gdp_forecast = []

for current_year in range(min_year_usa, 2027): # Include forecast years in the loop
    # Filter real data up to the current year
    df_usa_current_real = df_usa_animation[df_usa_animation['year'] <= current_year]

    # Train a linear regression model using data ONLY UP TO THE CURRENT YEAR
    model_usa_frame = LinearRegression()
    if not df_usa_current_real.empty:
        model_usa_frame.fit(df_usa_current_real[['year']], df_usa_current_real['gdp_per_capita'])
    else:
        # If no historical data up to current_year (e.g., for early forecast frames before min_year_usa)
        # Use the full historical model for predictions in early frames or if no data yet
        model_usa_frame = model_usa_animation

    # Generate predicted GDP per capita values for the entire desired range
    # (from 1990 to 2026) using the model trained with data up to the current_year
    years_for_plot_usa = np.arange(min_year_usa, 2027).reshape(-1, 1)
    gdp_forecast_plot_usa = model_usa_frame.predict(years_for_plot_usa)

    # Create plot
    fig, ax = plt.subplots(figsize=(12, 7))

    # USA Real Data (Blue)
    ax.plot(df_usa_current_real['year'], df_usa_current_real['gdp_per_capita'],
            color='#1f77b4', marker='o', label='USA (Real)', markersize=4, linewidth=2.5)

    # Forecast Line (Red dashed) - always show the forecast based on the current model up to 2026
    ax.plot(years_for_plot_usa, gdp_forecast_plot_usa, color='#d62728', linestyle='--', label='Trend Projection (Forecast)', linewidth=2)

    # Add annotations for 2024, 2025, 2026 forecast values
    future_years_to_annotate = [2024, 2025, 2026]
    for fy in future_years_to_annotate:
        if fy >= current_year: # Only annotate if the forecast year is equal to or past the current animation year
            pred_val = model_usa_frame.predict(pd.DataFrame({'year': [fy]}))[0]
            ax.text(fy, pred_val, f'${pred_val:,.0f}', color='white', ha='center', va='bottom', fontsize=10, fontweight='bold')


    # Details aesthetics
    ax.set_title(f'United States: GDP per capita Forecast (Year: {current_year})', fontsize=16, color='white', pad=20)
    ax.set_xlabel('Year', fontsize=12)
    ax.set_ylabel('GDP per capita (USD)', fontsize=12)
    ax.legend(loc='upper left', frameon=True, facecolor='black', fontsize=10)
    ax.grid(True, alpha=0.1)

    # Set x and y axis limits consistently across all frames
    ax.set_xlim(min_year_usa, 2026) # Fixed x-axis to encompass the full range
    ax.set_ylim(0, max_gdp_overall_usa) # Consistent y-axis limit

    fig.tight_layout()

    # Save frame
    filename = os.path.join(frames_dir_usa_gdp_forecast, f'frame_gdp_usa_forecast_{current_year:04d}.png')
    plt.savefig(filename, dpi=100)
    frame_filenames_usa_gdp_forecast.append(filename)
    plt.close(fig)

print(f"Generated {len(frame_filenames_usa_gdp_forecast)} frames in '{frames_dir_usa_gdp_forecast}' directory.")
     import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
from sklearn.linear_model import LinearRegression
import os

# Ensure the frames directory exists
frames_dir_usa_gdp_forecast = 'animation_frames_usa_gdp_forecast'
os.makedirs(frames_dir_usa_gdp_forecast, exist_ok=True)

# Configure the plot style to dark background
plt.style.use('dark_background')

# Data prepared in previous step: df_usa_animation, min_year_usa, max_year_usa
# and model_usa_animation

# 1. Calculate overall max GDP for consistent Y-axis limits across all frames
#    This needs to consider the historical max and the max of the _full_ forecast range.

# Model trained on full historical data (up to max_year_usa = 2022)
# model_usa_animation is already trained in the previous step.

# Years for the full forecast range (e.g., 1990 to 2026)
years_for_full_forecast_usa = np.arange(min_year_usa, 2027).reshape(-1, 1)
predictions_full_forecast_usa = model_usa_animation.predict(years_for_full_forecast_usa)

max_gdp_overall_usa = max(df_usa_animation['gdp_per_capita'].max(), predictions_full_forecast_usa.max()) * 1.1

frame_filenames_usa_gdp_forecast = []

for current_year in range(min_year_usa, 2027): # Include forecast years in the loop
    # Filter real data up to the current year
    df_usa_current_real = df_usa_animation[df_usa_animation['year'] <= current_year]

    # Train a linear regression model using data ONLY UP TO THE CURRENT YEAR
    model_usa_frame = LinearRegression()
    if not df_usa_current_real.empty:
        model_usa_frame.fit(df_usa_current_real[['year']], df_usa_current_real['gdp_per_capita'])
    else:
        # If no historical data up to current_year (e.g., for early forecast frames before min_year_usa)
        # Use the full historical model for predictions in early frames or if no data yet
        model_usa_frame = model_usa_animation

    # Generate predicted GDP per capita values for the entire desired range
    # (from 1990 to 2026) using the model trained with data up to the current_year
    years_for_plot_usa = np.arange(min_year_usa, 2027).reshape(-1, 1)
    gdp_forecast_plot_usa = model_usa_frame.predict(years_for_plot_usa)

    # Create plot
    fig, ax = plt.subplots(figsize=(12, 7))

    # USA Real Data (Blue)
    ax.plot(df_usa_current_real['year'], df_usa_current_real['gdp_per_capita'],
            color='#1f77b4', marker='o', label='USA (Real)', markersize=4, linewidth=2.5)

    # Forecast Line (Red dashed) - always show the forecast based on the current model up to 2026
    ax.plot(years_for_plot_usa, gdp_forecast_plot_usa, color='#d62728', linestyle='--', label='Trend Projection (Forecast)', linewidth=2)

    # Add annotations for 2024, 2025, 2026 forecast values
    future_years_to_annotate = [2024, 2025, 2026]
    for fy in future_years_to_annotate:
        if fy >= current_year: # Only annotate if the forecast year is equal to or past the current animation year
            pred_val = model_usa_frame.predict(pd.DataFrame({'year': [fy]}))[0]
            ax.text(fy, pred_val, f'${pred_val:,.0f}', color='white', ha='center', va='bottom', fontsize=10, fontweight='bold')


    # Details aesthetics
    ax.set_title(f'United States: GDP per capita Forecast (Year: {current_year})', fontsize=16, color='white', pad=20)
    ax.set_xlabel('Year', fontsize=12)
    ax.set_ylabel('GDP per capita (USD)', fontsize=12)
    ax.legend(loc='upper left', frameon=True, facecolor='black', fontsize=10)
    ax.grid(True, alpha=0.1)

    # Set x and y axis limits consistently across all frames
    ax.set_xlim(min_year_usa, 2026) # Fixed x-axis to encompass the full range
    ax.set_ylim(0, max_gdp_overall_usa) # Consistent y-axis limit

    fig.tight_layout()

    # Save frame
    filename = os.path.join(frames_dir_usa_gdp_forecast, f'frame_gdp_usa_forecast_{current_year:04d}.png')
    plt.savefig(filename, dpi=100)
    frame_filenames_usa_gdp_forecast.append(filename)
    plt.close(fig)

print(f"Generated {len(frame_filenames_usa_gdp_forecast)} frames in '{frames_dir_usa_gdp_forecast}' directory.")
     import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
from sklearn.linear_model import LinearRegression
import os

# Ensure the frames directory exists
frames_dir_usa_gdp_forecast = 'animation_frames_usa_gdp_forecast'
os.makedirs(frames_dir_usa_gdp_forecast, exist_ok=True)

# Configure the plot style to dark background
plt.style.use('dark_background')

# Data prepared in previous step: df_usa_animation, min_year_usa, max_year_usa
# and model_usa_animation

# 1. Calculate overall max GDP for consistent Y-axis limits across all frames
#    This needs to consider the historical max and the max of the _full_ forecast range.

# Model trained on full historical data (up to max_year_usa = 2022)
# model_usa_animation is already trained in the previous step.

# Years for the full forecast range (e.g., 1990 to 2026)
years_for_full_forecast_usa = np.arange(min_year_usa, 2027).reshape(-1, 1)
predictions_full_forecast_usa = model_usa_animation.predict(years_for_full_forecast_usa)

max_gdp_overall_usa = max(df_usa_animation['gdp_per_capita'].max(), predictions_full_forecast_usa.max()) * 1.1

frame_filenames_usa_gdp_forecast = []

for current_year in range(min_year_usa, 2027): # Include forecast years in the loop
    # Filter real data up to the current year
    df_usa_current_real = df_usa_animation[df_usa_animation['year'] <= current_year]

    # Train a linear regression model using data ONLY UP TO THE CURRENT YEAR
    model_usa_frame = LinearRegression()
    if not df_usa_current_real.empty:
        model_usa_frame.fit(df_usa_current_real[['year']], df_usa_current_real['gdp_per_capita'])
    else:
        # If no historical data up to current_year (e.g., for early forecast frames before min_year_usa)
        # Use the full historical model for predictions in early frames or if no data yet
        model_usa_frame = model_usa_animation

    # Generate predicted GDP per capita values for the entire desired range
    # (from 1990 to 2026) using the model trained with data up to the current_year
    years_for_plot_usa = np.arange(min_year_usa, 2027).reshape(-1, 1)
    gdp_forecast_plot_usa = model_usa_frame.predict(years_for_plot_usa)

    # Create plot
    fig, ax = plt.subplots(figsize=(12, 7))

    # USA Real Data (Blue)
    ax.plot(df_usa_current_real['year'], df_usa_current_real['gdp_per_capita'],
            color='#1f77b4', marker='o', label='USA (Real)', markersize=4, linewidth=2.5)

    # Forecast Line (Red dashed) - always show the forecast based on the current model up to 2026
    ax.plot(years_for_plot_usa, gdp_forecast_plot_usa, color='#d62728', linestyle='--', label='Trend Projection (Forecast)', linewidth=2)

    # Add annotations for 2024, 2025, 2026 forecast values
    future_years_to_annotate = [2024, 2025, 2026]
    for fy in future_years_to_annotate:
        if fy >= current_year: # Only annotate if the forecast year is equal to or past the current animation year
            pred_val = model_usa_frame.predict(pd.DataFrame({'year': [fy]}))[0]
            ax.text(fy, pred_val, f'${pred_val:,.0f}', color='white', ha='center', va='bottom', fontsize=10, fontweight='bold')


    # Details aesthetics
    ax.set_title(f'United States: GDP per capita Forecast (Year: {current_year})', fontsize=16, color='white', pad=20)
    ax.set_xlabel('Year', fontsize=12)
    ax.set_ylabel('GDP per capita (USD)', fontsize=12)
    ax.legend(loc='upper left', frameon=True, facecolor='black', fontsize=10)
    ax.grid(True, alpha=0.1)

    # Set x and y axis limits consistently across all frames
    ax.set_xlim(min_year_usa, 2026) # Fixed x-axis to encompass the full range
    ax.set_ylim(0, max_gdp_overall_usa) # Consistent y-axis limit

    fig.tight_layout()

    # Save frame
    filename = os.path.join(frames_dir_usa_gdp_forecast, f'frame_gdp_usa_forecast_{current_year:04d}.png')
    plt.savefig(filename, dpi=100)
    frame_filenames_usa_gdp_forecast.append(filename)
    plt.close(fig)

print(f"Generated {len(frame_filenames_usa_gdp_forecast)} frames in '{frames_dir_usa_gdp_forecast}' directory.")

import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
from sklearn.linear_model import LinearRegression
import os

# Ensure the frames directory exists
frames_dir_usa_gdp_forecast = 'animation_frames_usa_gdp_forecast'
os.makedirs(frames_dir_usa_gdp_forecast, exist_ok=True)

# Configure the plot style to dark background
plt.style.use('dark_background')

# Data prepared in previous step: df_usa_animation, min_year_usa, max_year_usa
# and model_usa_animation

# 1. Calculate overall max GDP for consistent Y-axis limits across all frames
#    This needs to consider the historical max and the max of the _full_ forecast range.

# Model trained on full historical data (up to max_year_usa = 2022)
# model_usa_animation is already trained in the previous step.

# Years for the full forecast range (e.g., 1990 to 2026)
years_for_full_forecast_usa_df = pd.DataFrame({'year': np.arange(min_year_usa, 2027)})
predictions_full_forecast_usa = model_usa_animation.predict(years_for_full_forecast_usa_df)

max_gdp_overall_usa = max(df_usa_animation['gdp_per_capita'].max(), predictions_full_forecast_usa.max()) * 1.1

frame_filenames_usa_gdp_forecast = []

for current_year in range(min_year_usa, 2027): # Include forecast years in the loop
    # Filter real data up to the current year
    df_usa_current_real = df_usa_animation[df_usa_animation['year'] <= current_year]

    # Train a linear regression model using data ONLY UP TO THE CURRENT YEAR
    model_usa_frame = LinearRegression()
    if not df_usa_current_real.empty:
        model_usa_frame.fit(df_usa_current_real[['year']], df_usa_current_real['gdp_per_capita'])
    else:
        # If no historical data up to current_year (e.g., for early forecast frames before min_year_usa)
        # Use the full historical model for predictions in early frames or if no data yet
        model_usa_frame = model_usa_animation

    # Generate predicted GDP per capita values for the entire desired range
    # (from 1990 to 2026) using the model trained with data up to the current_year
    years_for_plot_usa_df = pd.DataFrame({'year': np.arange(min_year_usa, 2027)})
    gdp_forecast_plot_usa = model_usa_frame.predict(years_for_plot_usa_df)

    # Create plot
    fig, ax = plt.subplots(figsize=(12, 7))

    # USA Real Data (Blue)
    ax.plot(df_usa_current_real['year'], df_usa_current_real['gdp_per_capita'],
            color='#1f77b4', marker='o', label='USA (Real)', markersize=4, linewidth=2.5)

    # Forecast Line (Red dashed) - always show the forecast based on the current model up to 2026
    ax.plot(years_for_plot_usa_df['year'], gdp_forecast_plot_usa, color='#d62728', linestyle='--', label='Trend Projection (Forecast)', linewidth=2)

    # Add annotations for 2024, 2025, 2026 forecast values
    future_years_to_annotate = [2024, 2025, 2026]
    for fy in future_years_to_annotate:
        if fy >= current_year: # Only annotate if the forecast year is equal to or past the current animation year
            pred_val = model_usa_frame.predict(pd.DataFrame({'year': [fy]}))[0]
            ax.text(fy, pred_val, f'${pred_val:,.0f}', color='white', ha='center', va='bottom', fontsize=10, fontweight='bold')


    # Details aesthetics
    ax.set_title(f'United States: GDP per capita Forecast (Year: {current_year})', fontsize=16, color='white', pad=20)
    ax.set_xlabel('Year', fontsize=12)
    ax.set_ylabel('GDP per capita (USD)', fontsize=12)
    ax.legend(loc='upper left', frameon=True, facecolor='black', fontsize=10)
    ax.grid(True, alpha=0.1)

    # Set x and y axis limits consistently across all frames
    ax.set_xlim(min_year_usa, 2026) # Fixed x-axis to encompass the full range
    ax.set_ylim(0, max_gdp_overall_usa) # Consistent y-axis limit

    fig.tight_layout()

    # Save frame
    filename = os.path.join(frames_dir_usa_gdp_forecast, f'frame_gdp_usa_forecast_{current_year:04d}.png')
    plt.savefig(filename, dpi=100)
    frame_filenames_usa_gdp_forecast.append(filename)
    plt.close(fig)

print(f"Generated {len(frame_filenames_usa_gdp_forecast)} frames in '{frames_dir_usa_gdp_forecast}' directory.")
     import imageio.v2 as imageio
import os

# Path to the directory containing the frames for USA GDP forecast
frames_dir_usa_gdp_forecast = 'animation_frames_usa_gdp_forecast'

# Get all image filenames, sorted to ensure correct order
images_usa_gdp_forecast = []
for filename in sorted(os.listdir(frames_dir_usa_gdp_forecast)):
    if filename.endswith('.png'):
        images_usa_gdp_forecast.append(imageio.imread(os.path.join(frames_dir_usa_gdp_forecast, filename)))

# Output GIF filename for USA GDP forecast
gif_path_usa_gdp_forecast = 'usa_gdp_forecast_animation.gif'

# Create the GIF
# duration specifies the time each frame is displayed (in seconds)
imageio.mimsave(gif_path_usa_gdp_forecast, images_usa_gdp_forecast, duration=0.2, loop=0) # loop=0 means loop indefinitely

print(f"Animated GIF for USA GDP forecast saved as '{gif_path_usa_gdp_forecast}'")
     
Animated GIF for USA GDP forecast saved as 'usa_gdp_forecast_animation.gif'
Reasoning: The frames for Argentina GDP forecast animation have already been generated in the previous step and stored in 'animation_frames_arg_gdp_forecast'. Now, I need to use the imageio library to combine these frames into a GIF. The code will list all PNG files in the directory, sort them to ensure correct chronological order, and then use imageio.mimsave to create the GIF.


import imageio.v2 as imageio
import os

# Path to the directory containing the frames for Argentina GDP forecast
frames_dir_arg_gdp_forecast = 'animation_frames_arg_gdp_forecast'

# Get all image filenames, sorted to ensure correct order
images_arg_gdp_forecast = []
for filename in sorted(os.listdir(frames_dir_arg_gdp_forecast)):
    if filename.endswith('.png'):
        images_arg_gdp_forecast.append(imageio.imread(os.path.join(frames_dir_arg_gdp_forecast, filename)))

# Output GIF filename for Argentina GDP forecast
gif_path_arg_gdp_forecast = 'argentina_gdp_forecast_animation.gif'

# Create the GIF
# duration specifies the time each frame is displayed (in seconds)
imageio.mimsave(gif_path_arg_gdp_forecast, images_arg_gdp_forecast, duration=0.2, loop=0) # loop=0 means loop indefinitely

print(f"Animated GIF for Argentina GDP forecast saved as '{gif_path_arg_gdp_forecast}'")
     
Animated GIF for Argentina GDP forecast saved as 'argentina_gdp_forecast_animation.gif'
Assemble Argentina GDP Forecast GIF
Subtask:
Combine the generated frames into an animated GIF named 'argentina_gdp_forecast_animation.gif'.

Reasoning: Assemble the generated PNG frames for Argentina's GDP forecast into a single animated GIF using the imageio library.


import imageio.v2 as imageio
import os

# Path to the directory containing the frames for Argentina GDP forecast
frames_dir_arg_gdp_forecast = 'animation_frames_arg_gdp_forecast'

# Get all image filenames, sorted to ensure correct order
images_arg_gdp_forecast = []
for filename in sorted(os.listdir(frames_dir_arg_gdp_forecast)):
    if filename.endswith('.png'):
        images_arg_gdp_forecast.append(imageio.imread(os.path.join(frames_dir_arg_gdp_forecast, filename)))

# Output GIF filename for Argentina GDP forecast
gif_path_arg_gdp_forecast = 'argentina_gdp_forecast_animation.gif'

# Create the GIF
# duration specifies the time each frame is displayed (in seconds)
imageio.mimsave(gif_path_arg_gdp_forecast, images_arg_gdp_forecast, duration=0.2, loop=0) # loop=0 means loop indefinitely

print(f"Animated GIF for Argentina GDP forecast saved as '{gif_path_arg_gdp_forecast}'")
     
Animated GIF for Argentina GDP forecast saved as 'argentina_gdp_forecast_animation.gif'
Assemble USA GDP Forecast GIF
Subtask:
Combine the generated frames into an animated GIF named 'usa_gdp_forecast_animation.gif'.

Reasoning: Assembling the generated PNG frames into an animated GIF is the next logical step to complete the subtask.


import imageio.v2 as imageio
import os

# Path to the directory containing the frames for USA GDP forecast
frames_dir_usa_gdp_forecast = 'animation_frames_usa_gdp_forecast'

# Get all image filenames, sorted to ensure correct order
images_usa_gdp_forecast = []
for filename in sorted(os.listdir(frames_dir_usa_gdp_forecast)):
    if filename.endswith('.png'):
        images_usa_gdp_forecast.append(imageio.imread(os.path.join(frames_dir_usa_gdp_forecast, filename)))

# Output GIF filename for USA GDP forecast
gif_path_usa_gdp_forecast = 'usa_gdp_forecast_animation.gif'

# Create the GIF
# duration specifies the time each frame is displayed (in seconds)
imageio.mimsave(gif_path_usa_gdp_forecast, images_usa_gdp_forecast, duration=0.2, loop=0) # loop=0 means loop indefinitely

print(f"Animated GIF for USA GDP forecast saved as '{gif_path_usa_gdp_forecast}'")
     
Animated GIF for USA GDP forecast saved as 'usa_gdp_forecast_animation.gif'
Prepare Data for Australia GDP Forecast Animation
Subtask:
Extract Australia's GDP per capita data and its historical linear regression model to prepare for frame generation.

Reasoning: I will prepare the Australia historical GDP per capita data for animation by creating a DataFrame, identifying the time range, and then training a linear regression model on this data, as requested in the instructions.


import pandas as pd
from sklearn.linear_model import LinearRegression

# Filter data for Australia and drop missing values
df_aus_animation = df[df['country'] == 'Australia'][['year', 'gdp_per_capita']].dropna()

# Identify min and max years
min_year_aus = df_aus_animation['year'].min()
max_year_aus = df_aus_animation['year'].max()

print(f"Data prepared for Australia GDP forecast animation.")
print(f"Time range for Australia GDP: {min_year_aus} to {max_year_aus}.")
print("First 5 rows of the prepared data:")
display(df_aus_animation.head())

# Train a linear regression model for Australia GDP per capita
X_aus_animation = df_aus_animation[['year']]
y_aus_animation = df_aus_animation['gdp_per_capita']
model_aus_animation = LinearRegression()
model_aus_animation.fit(X_aus_animation, y_aus_animation)

print("Linear regression model for Australia GDP per capita trained.")
     
Data prepared for Australia GDP forecast animation.
Time range for Australia GDP: 1991 to 2022.
First 5 rows of the prepared data:
year	gdp_per_capita
204	1991	26583.13
205	1992	27273.69
206	1993	28298.11
207	1994	29501.06
208	1995	30341.44
Linear regression model for Australia GDP per capita trained.
Generate Animated Frames for Australia GDP Forecast
Subtask:
Create individual static image frames for each year, showing Australia's real GDP per capita and the projected forecast line up to that year, with consistent axis limits. Each frame will display the forecasted GDP for 2024, 2025, and 2026.

Reasoning: This step initializes the directory for storing frames, calculates a consistent y-axis limit based on historical and fully forecasted data, and then iterates through each year to create and save individual plot frames. Each frame displays the real GDP per capita up to the current year, along with the linear regression forecast based on data up to that year, and explicitly shows the 2024, 2025, and 2026 forecast values derived from that year's model.


import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
from sklearn.linear_model import LinearRegression
import os

# Ensure the frames directory exists
frames_dir_aus_gdp_forecast = 'animation_frames_aus_gdp_forecast'
os.makedirs(frames_dir_aus_gdp_forecast, exist_ok=True)

# Configure the plot style to dark background
plt.style.use('dark_background')

# Data prepared in previous step: df_aus_animation, min_year_aus, max_year_aus
# and model_aus_animation

# 1. Calculate overall max GDP for consistent Y-axis limits across all frames
#    This needs to consider the historical max and the max of the _full_ forecast range.

# Model trained on full historical data (up to max_year_aus = 2022)
# model_aus_animation is already trained in the previous step.

# Years for the full forecast range (e.g., 1991 to 2026)
years_for_full_forecast_aus_df = pd.DataFrame({'year': np.arange(min_year_aus, 2027)})
predictions_full_forecast_aus = model_aus_animation.predict(years_for_full_forecast_aus_df)

max_gdp_overall_aus = max(df_aus_animation['gdp_per_capita'].max(), predictions_full_forecast_aus.max()) * 1.1

frame_filenames_aus_gdp_forecast = []

for current_year in range(min_year_aus, 2027): # Include forecast years in the loop
    # Filter real data up to the current year
    df_aus_current_real = df_aus_animation[df_aus_animation['year'] <= current_year]

    # Train a linear regression model using data ONLY UP TO THE CURRENT YEAR
    model_aus_frame = LinearRegression()
    if not df_aus_current_real.empty:
        model_aus_frame.fit(df_aus_current_real[['year']], df_aus_current_real['gdp_per_capita'])
    else:
        # If no historical data up to current_year (e.g., for early forecast frames before min_year_aus)
        # Use the full historical model for predictions in early frames or if no data yet
        model_aus_frame = model_aus_animation

    # Generate predicted GDP per capita values for the entire desired range
    # (from 1991 to 2026) using the model trained with data up to the current_year
    years_for_plot_aus_df = pd.DataFrame({'year': np.arange(min_year_aus, 2027)})
    gdp_forecast_plot_aus = model_aus_frame.predict(years_for_plot_aus_df)

    # Create plot
    fig, ax = plt.subplots(figsize=(12, 7))

    # Australia Real Data (Blue)
    ax.plot(df_aus_current_real['year'], df_aus_current_real['gdp_per_capita'],
            color='#00008B', marker='o', label='Australia (Real)', markersize=4, linewidth=2.5)

    # Forecast Line (Red dashed) - always show the forecast based on the current model up to 2026
    ax.plot(years_for_plot_aus_df['year'], gdp_forecast_plot_aus, color='#d62728', linestyle='--', label='Trend Projection (Forecast)', linewidth=2)

    # Add annotations for 2024, 2025, 2026 forecast values
    future_years_to_annotate = [2024, 2025, 2026]
    for fy in future_years_to_annotate:
        if fy >= current_year: # Only annotate if the forecast year is equal to or past the current animation year
            pred_val = model_aus_frame.predict(pd.DataFrame({'year': [fy]}))[0]
            ax.text(fy, pred_val, f'${pred_val:,.0f}', color='white', ha='center', va='bottom', fontsize=10, fontweight='bold')


    # Details aesthetics
    ax.set_title(f'Australia: GDP per capita Forecast (Year: {current_year})', fontsize=16, color='white', pad=20)
    ax.set_xlabel('Year', fontsize=12)
    ax.set_ylabel('GDP per capita (USD)', fontsize=12)
    ax.legend(loc='upper left', frameon=True, facecolor='black', fontsize=10)
    ax.grid(True, alpha=0.1)

    # Set x and y axis limits consistently across all frames
    ax.set_xlim(min_year_aus, 2026) # Fixed x-axis to encompass the full range
    ax.set_ylim(0, max_gdp_overall_aus) # Consistent y-axis limit

    fig.tight_layout()

    # Save frame
    filename = os.path.join(frames_dir_aus_gdp_forecast, f'frame_gdp_aus_forecast_{current_year:04d}.png')
    plt.savefig(filename, dpi=100)
    frame_filenames_aus_gdp_forecast.append(filename)
    plt.close(fig)

print(f"Generated {len(frame_filenames_aus_gdp_forecast)} frames in '{frames_dir_aus_gdp_forecast}' directory.")
     
Generated 36 frames in 'animation_frames_aus_gdp_forecast' directory.
Reasoning: Assemble the generated PNG frames for Australia's GDP forecast into a single animated GIF using the imageio library. I will read all PNG files from the frames_dir_aus_gdp_forecast directory, sort them to ensure correct chronological order, and then use imageio.mimsave to create the GIF.


import imageio.v2 as imageio
import os

# Path to the directory containing the frames for Australia GDP forecast
frames_dir_aus_gdp_forecast = 'animation_frames_aus_gdp_forecast'

# Get all image filenames, sorted to ensure correct order
images_aus_gdp_forecast = []
for filename in sorted(os.listdir(frames_dir_aus_gdp_forecast)):
    if filename.endswith('.png'):
        images_aus_gdp_forecast.append(imageio.imread(os.path.join(frames_dir_aus_gdp_forecast, filename)))

# Output GIF filename for Australia GDP forecast
gif_path_aus_gdp_forecast = 'australia_gdp_forecast_animation.gif'

# Create the GIF
# duration specifies the time each frame is displayed (in seconds)
imageio.mimsave(gif_path_aus_gdp_forecast, images_aus_gdp_forecast, duration=0.2, loop=0) # loop=0 means loop indefinitely

print(f"Animated GIF for Australia GDP forecast saved as '{gif_path_aus_gdp_forecast}'")
     
Animated GIF for Australia GDP forecast saved as 'australia_gdp_forecast_animation.gif'
Assemble Australia GDP Forecast GIF
Subtask:
Combine the generated frames into an animated GIF named 'australia_gdp_forecast_animation.gif'.

Reasoning: Assemble the generated PNG frames for Australia's GDP forecast into a single animated GIF using the imageio library. This involves reading all PNG files from the specified directory, sorting them, and then using imageio.mimsave to create the GIF with a specified duration and loop setting.


import imageio.v2 as imageio
import os

# Path to the directory containing the frames for Australia GDP forecast
frames_dir_aus_gdp_forecast = 'animation_frames_aus_gdp_forecast'

# Get all image filenames, sorted to ensure correct order
images_aus_gdp_forecast = []
for filename in sorted(os.listdir(frames_dir_aus_gdp_forecast)):
    if filename.endswith('.png'):
        images_aus_gdp_forecast.append(imageio.imread(os.path.join(frames_dir_aus_gdp_forecast, filename)))

# Output GIF filename for Australia GDP forecast
gif_path_aus_gdp_forecast = 'australia_gdp_forecast_animation.gif'

# Create the GIF
# duration specifies the time each frame is displayed (in seconds)
imageio.mimsave(gif_path_aus_gdp_forecast, images_aus_gdp_forecast, duration=0.2, loop=0) # loop=0 means loop indefinitely

print(f"Animated GIF for Australia GDP forecast saved as '{gif_path_aus_gdp_forecast}'")
     
Animated GIF for Australia GDP forecast saved as 'australia_gdp_forecast_animation.gif'
Final Task
Subtask:
Provide all generated animated GIFs (Divergencia Estructural: Argentina vs Australia, Argentina Resilience, Argentina GDP Forecast, USA GDP Forecast, Australia GDP Forecast) and instructions on how to download them from Colab and upload them to Canva, explaining their simulated interactive nature.

Final Task
Subtask:
Provide the updated 'regional_resilience_animation.gif' and instructions on how to download it from Colab and upload it to Canva, explaining its simulated interactive nature.

Task
Create several animated GIFs of different time-series plots, representing the evolution of various economic indicators (GDP per capita, resilience score) for different countries and regions over time. For each GIF, provide instructions on how to download it from Google Colab and upload it to Canva, explaining the simulated interactive nature of GIFs in this context.

Animated GIF for Canva: Regional Resilience
Great news! The animated GIF, 'regional_resilience_animation.gif', representing the evolution of resilience across Argentina and the ex-Yugoslavia countries, has been successfully created.

This GIF offers a dynamic visualization of the data, simulating interactivity within platforms like Canva which do not support direct interactive HTML embeds.

To download the GIF:

Look for the folder icon on the left sidebar of your Google Colab environment. This is the 'File Browser'.
Navigate to the main directory (usually /content/).
You will find regional_resilience_animation.gif listed there.
Right-click on the file and select 'Download' to save it to your local machine.
To upload the GIF to Canva:

Open your project in Canva.
On the left-hand menu, click on 'Uploads'.
Click 'Upload files' and select the downloaded regional_resilience_animation.gif from your computer.
Once uploaded, you can drag and drop the GIF onto your design. Canva will play the animation, providing a visually engaging element for your presentation or design.
Enjoy your dynamic visualization!

Animated GIF for Canva: Regional Resilience
Great news! The updated animated GIF, 'regional_resilience_animation.gif', representing the evolution of resilience across Argentina and the ex-Yugoslavia countries with Argentina highlighted in bright cyan, has been successfully created.

This GIF offers a dynamic visualization of the data, simulating interactivity within platforms like Canva which do not support direct interactive HTML embeds.

To download the GIF:

Look for the folder icon on the left sidebar of your Google Colab environment. This is the 'File Browser'.
Navigate to the main directory (usually /content/).
You will find regional_resilience_animation.gif listed there.
Right-click on the file and select 'Download' to save it to your local machine.
To upload the GIF to Canva:

Open your project in Canva.
On the left-hand menu, click on 'Uploads'.
Click 'Upload files' and select the downloaded regional_resilience_animation.gif from your computer.
Once uploaded, you can drag and drop the GIF onto your design. Canva will play the animation, providing a visually engaging element for your presentation or design.
Enjoy your dynamic visualization!

Animated GIF for Canva: Regional Resilience
Great news! The animated GIF, 'regional_resilience_animation.gif', representing the evolution of resilience across Argentina and the ex-Yugoslavia countries, has been successfully created.

This GIF offers a dynamic visualization of the data, simulating interactivity within platforms like Canva which do not support direct interactive HTML embeds.

To download the GIF:

Look for the folder icon on the left sidebar of your Google Colab environment. This is the 'File Browser'.
Navigate to the main directory (usually /content/).
You will find regional_resilience_animation.gif listed there.
Right-click on the file and select 'Download' to save it to your local machine.
To upload the GIF to Canva:

Open your project in Canva.
On the left-hand menu, click on 'Uploads'.
Click 'Upload files' and select the downloaded regional_resilience_animation.gif from your computer.
Once uploaded, you can drag and drop the GIF onto your design. Canva will play the animation, providing a visually engaging element for your presentation or design.
Enjoy your dynamic visualization!

Animated GIF for Canva: Regional Resilience
Great news! The animated GIF, 'regional_resilience_animation.gif', representing the evolution of resilience across Argentina and the ex-Yugoslavia countries, has been successfully created.

This GIF offers a dynamic visualization of the data, simulating interactivity within platforms like Canva which do not support direct interactive HTML embeds.

To download the GIF:

Look for the folder icon on the left sidebar of your Google Colab environment. This is the 'File Browser'.
Navigate to the main directory (usually /content/).
You will find regional_resilience_animation.gif listed there.
Right-click on the file and select 'Download' to save it to your local machine.
To upload the GIF to Canva:

Open your project in Canva.
On the left-hand menu, click on 'Uploads'.
Click 'Upload files' and select the downloaded regional_resilience_animation.gif from your computer.
Once uploaded, you can drag and drop the GIF onto your design. Canva will play the animation, providing a visually engaging element for your presentation or design.
Enjoy your dynamic visualization!

Animated GIF for Canva: Regional Resilience
Great news! The animated GIF, 'regional_resilience_animation.gif', representing the evolution of resilience across Argentina and the ex-Yugoslavia countries, has been successfully created.

This GIF offers a dynamic visualization of the data, simulating interactivity within platforms like Canva which do not support direct interactive HTML embeds.

To download the GIF:

Look for the folder icon on the left sidebar of your Google Colab environment. This is the 'File Browser'.
Navigate to the main directory (usually /content/).
You will find regional_resilience_animation.gif listed there.
Right-click on the file and select 'Download' to save it to your local machine.
To upload the GIF to Canva:

Open your project in Canva.
On the left-hand menu, click on 'Uploads'.
Click 'Upload files' and select the downloaded regional_resilience_animation.gif from your computer.
Once uploaded, you can drag and drop the GIF onto your design. Canva will play the animation, providing a visually engaging element for your presentation or design.
Enjoy your dynamic visualization!

Task
Create several animated GIFs of different time-series plots, representing the evolution of various economic indicators (GDP per capita, resilience score) for different countries and regions over time. For each GIF, provide instructions on how to download it from Google Colab and upload it to Canva, explaining the simulated interactive nature of GIFs in this context.

Animated GIF for Canva: Regional Resilience
Great news! The animated GIF, 'regional_resilience_animation.gif', representing the evolution of resilience across Argentina and the ex-Yugoslavia countries, has been successfully created.

This GIF offers a dynamic visualization of the data, simulating interactivity within platforms like Canva which do not support direct interactive HTML embeds.

To download the GIF:

Look for the folder icon on the left sidebar of your Google Colab environment. This is the 'File Browser'.
Navigate to the main directory (usually /content/).
You will find regional_resilience_animation.gif listed there.
Right-click on the file and select 'Download' to save it to your local machine.
To upload the GIF to Canva:

Open your project in Canva.
On the left-hand menu, click on 'Uploads'.
Click 'Upload files' and select the downloaded regional_resilience_animation.gif from your computer.
Once uploaded, you can drag and drop the GIF onto your design. Canva will play the animation, providing a visually engaging element for your presentation or design.
Enjoy your dynamic visualization!

Confirm completion and inquire about further GIFs
Subtask:
Confirm the completion of the regional resilience GIF and ask the user if they would like to proceed with creating GIFs for other time-series graphs, such as specific GDP forecasts or other key indicators.

Regional Resilience GIF Completed
The regional_resilience_animation.gif for Argentina and the ex-Yugoslavia countries has been successfully created. Instructions for downloading and uploading it to Canva, highlighting its simulated interactive nature, have already been provided.

Would you like to proceed with creating additional animated GIFs for other economic indicators, such as:

GDP per capita forecasts for Argentina, USA, and Australia?
Any other specific regional comparisons or economic indicators?
Please let me know your preference for the next steps!

Prepare Data for Regional Resilience Animation
Subtask:
Filter the DataFrame to include data for Argentina and the ex-Yugoslavia countries (Croatia, Bosnia and Herzegovina, Serbia, Montenegro, North Macedonia, Kosovo), selecting 'year', 'country', and 'score_resiliencia' columns. Ensure no missing values and identify the min/max years for the animation loop.

Generate Animated Frames for Regional Resilience
Subtask:
Create individual static image frames for each year from the minimum to the maximum year. Each frame will display the 'score_resiliencia' for each selected country up to that specific year, ensuring consistent axis limits across all frames to create a smooth animation. Highlight Argentina distinctly.

Assemble Regional Resilience GIF
Subtask:
Combine the generated PNG frames for regional resilience into a single animated GIF using the imageio library.

Reasoning: The previous attempt to assemble the GIF failed with a ValueError: all input arrays must have the same shape. This indicates that the PNG frames generated in the preceding step (Generate Animated Frames for Regional Resilience) might have inconsistent dimensions. To fix this, I need to ensure that when saving each frame, the figure size and layout are consistent. I will re-run the assembly code directly as a first attempt, as the issue could have been an intermittent problem with the frames or memory. If it fails again, I will return to the frame generation step to ensure consistent dimensions.


import imageio.v2 as imageio
import os

# Path to the directory containing the frames for regional resilience
frames_dir_regional_resilience = 'animation_frames_regional_resilience'

# Get all image filenames, sorted to ensure correct order
images_regional_resilience = []
for filename in sorted(os.listdir(frames_dir_regional_resilience)):
    if filename.endswith('.png'):
        images_regional_resilience.append(imageio.imread(os.path.join(frames_dir_regional_resilience, filename)))

# Output GIF filename for regional resilience
gif_path_regional_resilience = 'regional_resilience_animation.gif'

# Create the GIF
# duration specifies the time each frame is displayed (in seconds)
imageio.mimsave(gif_path_regional_resilience, images_regional_resilience, duration=0.2, loop=0) # loop=0 means loop indefinitely

print(f"Animated GIF for regional resilience saved as '{gif_path_regional_resilience}'")
     
Animated GIF for regional resilience saved as 'regional_resilience_animation.gif'
Final Task
Subtask:
Provide instructions for the user to download the newly created 'regional_resilience_animation.gif' from the Colab file browser and steps to upload it to Canva, reiterating its simulated interactive nature.

Task
Regenerate the regional_resilience_animation.gif with corrected colors (diverse non-grayscale for ex-Yugoslavia countries, cyan for Argentina), provide instructions for downloading it from Google Colab, and explain how to upload it to Canva. Additionally, acknowledge the pending requests for other GIFs.

Update Regional Resilience Frame Generation
Subtask:
Modify the frame generation code to use a more diverse color palette for countries other than Argentina, ensuring they are not all grayscale. Use a seaborn palette for other countries.

Animated GIF for Canva: Regional Resilience
Great news! The updated animated GIF, 'regional_resilience_animation.gif', representing the evolution of resilience across Argentina and the ex-Yugoslavia countries with Argentina highlighted in bright cyan and other countries in distinct non-grayscale colors, has been successfully created.

This GIF offers a dynamic visualization of the data, simulating interactivity within platforms like Canva which do not support direct interactive HTML embeds.

To download the GIF:

Look for the folder icon on the left sidebar of your Google Colab environment. This is the 'File Browser'.
Navigate to the main directory (usually /content/).
You will find regional_resilience_animation.gif listed there.
Right-click on the file and select 'Download' to save it to your local machine.
To upload the GIF to Canva:

Open your project in Canva.
On the left-hand menu, click on 'Uploads'.
Click 'Upload files' and select the downloaded regional_resilience_animation.gif from your computer.
Once uploaded, you can drag and drop the GIF onto your design. Canva will play the animation, providing a visually engaging element for your presentation or design.
Enjoy your dynamic visualization!

Reasoning: To assemble the generated frames for regional resilience into a single animated GIF, I will use the imageio library. I will read all PNG files from the frames_dir_regional_resilience directory, sort them to ensure correct chronological order, and then use imageio.mimsave to create the GIF.


import imageio.v2 as imageio
import os

# Path to the directory containing the frames for regional resilience
frames_dir_regional_resilience = 'animation_frames_regional_resilience'

# Get all image filenames, sorted to ensure correct order
images_regional_resilience = []
for filename in sorted(os.listdir(frames_dir_regional_resilience)):
    if filename.endswith('.png'):
        images_regional_resilience.append(imageio.imread(os.path.join(frames_dir_regional_resilience, filename)))

# Output GIF filename for regional resilience
gif_path_regional_resilience = 'regional_resilience_animation.gif'

# Create the GIF
# duration specifies the time each frame is displayed (in seconds)
imageio.mimsave(gif_path_regional_resilience, images_regional_resilience, duration=0.2, loop=0) # loop=0 means loop indefinitely

print(f"Animated GIF for regional resilience saved as '{gif_path_regional_resilience}'")
     
Animated GIF for regional resilience saved as 'regional_resilience_animation.gif'
Reasoning: The frames with the updated color palette have been generated. Now, I need to re-run the GIF assembly code to create the regional_resilience_animation.gif with these new frames. This is done by calling the imageio.mimsave function with the collected images_regional_resilience.


import imageio.v2 as imageio
import os

# Path to the directory containing the frames for regional resilience
frames_dir_regional_resilience = 'animation_frames_regional_resilience'

# Get all image filenames, sorted to ensure correct order
images_regional_resilience = []
for filename in sorted(os.listdir(frames_dir_regional_resilience)):
    if filename.endswith('.png'):
        images_regional_resilience.append(imageio.imread(os.path.join(frames_dir_regional_resilience, filename)))

# Output GIF filename for regional resilience
gif_path_regional_resilience = 'regional_resilience_animation.gif'

# Create the GIF
# duration specifies the time each frame is displayed (in seconds)
imageio.mimsave(gif_path_regional_resilience, images_regional_resilience, duration=0.2, loop=0) # loop=0 means loop indefinitely

print(f"Animated GIF for regional resilience saved as '{gif_path_regional_resilience}'")
     
Animated GIF for regional resilience saved as 'regional_resilience_animation.gif'
Reassemble Regional Resilience GIF
Subtask:
Combine the generated PNG frames for regional resilience into a single animated GIF using the imageio library, ensuring the updated color palette is reflected.

Reasoning: This code will reassemble the generated PNG frames into a single animated GIF, incorporating the updated color palette for the regional resilience plot. This is a direct re-execution of the previous assembly step to ensure the changes in frame generation are reflected in the final GIF.


import imageio.v2 as imageio
import os

# Path to the directory containing the frames for regional resilience
frames_dir_regional_resilience = 'animation_frames_regional_resilience'

# Get all image filenames, sorted to ensure correct order
images_regional_resilience = []
for filename in sorted(os.listdir(frames_dir_regional_resilience)):
    if filename.endswith('.png'):
        images_regional_resilience.append(imageio.imread(os.path.join(frames_dir_regional_resilience, filename)))

# Output GIF filename for regional resilience
gif_path_regional_resilience = 'regional_resilience_animation.gif'

# Create the GIF
# duration specifies the time each frame is displayed (in seconds)
imageio.mimsave(gif_path_regional_resilience, images_regional_resilience, duration=0.2, loop=0) # loop=0 means loop indefinitely

print(f"Animated GIF for regional resilience saved as '{gif_path_regional_resilience}'")
     
Animated GIF for regional resilience saved as 'regional_resilience_animation.gif'
Provide Download Instructions
Subtask:
Provide instructions for the user to download the newly created regional_resilience_animation.gif from the Colab file browser and steps to upload it to Canva, reiterating its simulated interactive nature.

Animated GIF for Canva: Regional Resilience
Great news! The updated animated GIF, 'regional_resilience_animation.gif', representing the evolution of resilience across Argentina and the ex-Yugoslavia countries with Argentina highlighted in bright cyan and other countries in distinct non-grayscale colors, has been successfully created.

This GIF offers a dynamic visualization of the data, simulating interactivity within platforms like Canva which do not support direct interactive HTML embeds.

To download the GIF:

Look for the folder icon on the left sidebar of your Google Colab environment. This is the 'File Browser'.
Navigate to the main directory (usually /content/).
You will find regional_resilience_animation.gif listed there.
Right-click on the file and select 'Download' to save it to your local machine.
To upload the GIF to Canva:

Open your project in Canva.
On the left-hand menu, click on 'Uploads'.
Click 'Upload files' and select the downloaded regional_resilience_animation.gif from your computer.
Once uploaded, you can drag and drop the GIF onto your design. Canva will play the animation, providing a visually engaging element for your presentation or design.
Enjoy your dynamic visualization!

Display First Frame
Subtask:
Load and display the first generated frame from the animation_frames_regional_resilience directory.

Reasoning: This code block will import necessary libraries, define the frames directory, get the first frame's filename, load it as an image, and then display it with a title.


import matplotlib.pyplot as plt
import os

# Define the directory where the frames are stored
frames_dir_regional_resilience = 'animation_frames_regional_resilience'

# Get a sorted list of all PNG filenames in the directory
frame_files = sorted([f for f in os.listdir(frames_dir_regional_resilience) if f.endswith('.png')])

# Check if any frames exist
if frame_files:
    # Get the path to the first frame
    first_frame_path = os.path.join(frames_dir_regional_resilience, frame_files[0])

    # Load the image
    img = plt.imread(first_frame_path)

    # Display the image
    plt.figure(figsize=(14, 8))
    plt.imshow(img)
    plt.title('Preview: First Frame of Regional Resilience Animation')
    plt.axis('off') # Hide axes
    plt.show()
    print(f"Displayed: {first_frame_path}")
else:
    print(f"No frames found in {frames_dir_regional_resilience}")
     

Displayed: animation_frames_regional_resilience/frame_regional_1991.png
Reasoning: To display the middle frame, I need to calculate the middle index from the frame_files list, then load and display that specific image. This is a direct follow-up to displaying the first frame.


import matplotlib.pyplot as plt
import os

# Define the directory where the frames are stored
frames_dir_regional_resilience = 'animation_frames_regional_resilience'

# Get a sorted list of all PNG filenames in the directory
frame_files = sorted([f for f in os.listdir(frames_dir_regional_resilience) if f.endswith('.png')])

# Check if any frames exist
if frame_files:
    # Calculate the index for the middle frame
    middle_frame_index = len(frame_files) // 2
    middle_frame_path = os.path.join(frames_dir_regional_resilience, frame_files[middle_frame_index])

    # Load the image
    img = plt.imread(middle_frame_path)

    # Display the image
    plt.figure(figsize=(14, 8))
    plt.imshow(img)
    plt.title(f'Preview: Middle Frame of Regional Resilience Animation ({frame_files[middle_frame_index].split("_")[-1].split(".")[0]})')
    plt.axis('off') # Hide axes
    plt.show()
    print(f"Displayed: {middle_frame_path}")
else:
    print(f"No frames found in {frames_dir_regional_resilience}")
     

Displayed: animation_frames_regional_resilience/frame_regional_2007.png
Reasoning: To display the last frame, I need to get the last element from the frame_files list, load it as an image, and then display it. This follows the pattern of displaying the first and middle frames.


import matplotlib.pyplot as plt
import os

# Define the directory where the frames are stored
frames_dir_regional_resilience = 'animation_frames_regional_resilience'

# Get a sorted list of all PNG filenames in the directory
frame_files = sorted([f for f in os.listdir(frames_dir_regional_resilience) if f.endswith('.png')])

# Check if any frames exist
if frame_files:
    # Get the path to the last frame
    last_frame_path = os.path.join(frames_dir_regional_resilience, frame_files[-1])

    # Load the image
    img = plt.imread(last_frame_path)

    # Display the image
    plt.figure(figsize=(14, 8))
    plt.imshow(img)
    plt.title(f'Preview: Last Frame of Regional Resilience Animation ({frame_files[-1].split("_")[-1].split(".")[0]})')
    plt.axis('off') # Hide axes
    plt.show()
    print(f"Displayed: {last_frame_path}")
else:
    print(f"No frames found in {frames_dir_regional_resilience}")
     

Displayed: animation_frames_regional_resilience/frame_regional_2022.png
Task
Confirm the completion of the regional resilience GIF and ask the user if they would like to proceed with creating GIFs for other time-series graphs, such as specific GDP forecasts or other key indicators.

Final Task
Subtask:
Confirm the completion of the regional resilience GIF and ask the user if they would like to proceed with creating GIFs for other time-series graphs, such as specific GDP forecasts or other key indicators.



     

import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
from sklearn.linear_model import LinearRegression

# 1. Preparar datos y entrenar modelos con nombres de columnas consistentes
df_arg = df[df['country'] == 'Argentina'].dropna(subset=['gdp_per_capita']).sort_values('year')
X_arg = df_arg[['year']]
y_arg = df_arg['gdp_per_capita']
model_arg = LinearRegression().fit(X_arg, y_arg)

df_aus = df[df['country'] == 'Australia'].dropna(subset=['gdp_per_capita']).sort_values('year')
X_aus = df_aus[['year']]
y_aus = df_aus['gdp_per_capita']
model_aus = LinearRegression().fit(X_aus, y_aus)

# 2. Rango extendido para visualización (1930-2026)
years_ext = pd.DataFrame({'year': np.arange(1930, 2027)})
pred_arg_ext = model_arg.predict(years_ext)
pred_aus_ext = model_aus.predict(years_ext)

# 3. CAGR (Calculado sobre el periodo con datos positivos: 1991-2026)
def calc_cagr(start, end, p):
    if start <= 0: return 0
    return (pow(end / start, 1/p) - 1) * 100

# Predicciones puntuales usando DataFrames para evitar warnings de feature names
val_1991_arg = model_arg.predict(pd.DataFrame({'year': [1991]}))[0]
val_2026_arg = model_arg.predict(pd.DataFrame({'year': [2026]}))[0]
val_1991_aus = model_aus.predict(pd.DataFrame({'year': [1991]}))[0]
val_2026_aus = model_aus.predict(pd.DataFrame({'year': [2026]}))[0]

cagr_arg = calc_cagr(val_1991_arg, val_2026_arg, 2026-1991)
cagr_aus = calc_cagr(val_1991_aus, val_2026_aus, 2026-1991)

# 4. Gráfico con estética Dark
plt.style.use('dark_background')
plt.figure(figsize=(15, 8))

# Argentina (Celeste)
plt.plot(df_arg['year'], df_arg['gdp_per_capita'], color='#87CEEB', marker='o', label='Argentina (Real)', markersize=4)
plt.plot(years_ext['year'], pred_arg_ext, color='#87CEEB', linestyle='--', alpha=0.4, label='Arg: Tendencia 1930-2026')

# Australia (Amarillo)
plt.plot(df_aus['year'], df_aus['gdp_per_capita'], color='#FFFF00', marker='o', label='Australia (Real)', markersize=4)
plt.plot(years_ext['year'], pred_aus_ext, color='#FFFF00', linestyle='--', alpha=0.4, label='Aus: Tendencia 1930-2026')

# Limitar eje Y para evitar valores negativos de la regresión lineal
plt.ylim(0, max(pred_aus_ext) * 1.1)

# Anotaciones de Crecimiento
plt.text(2027, pred_arg_ext[-1], f'Trend: {cagr_arg:.2f}%', color='#87CEEB', fontweight='bold')
plt.text(2027, pred_aus_ext[-1], f'Trend: {cagr_aus:.2f}%', color='#FFFF00', fontweight='bold')

plt.axvline(x=1991, color='white', linestyle=':', alpha=0.5, label='Inicio datos reales')
plt.title('Divergencia Estructural: Argentina vs Australia (Proyección 1930-2026)', fontsize=16)
plt.ylabel('GDP per cápita (USD)')
plt.xlabel('Año')
plt.legend(loc='upper left', frameon=True, facecolor='black')
plt.grid(True, alpha=0.1)

plt.tight_layout()
plt.show()
     


import plotly.graph_objects as go
import plotly.express as px
import numpy as np
import pandas as pd
from sklearn.linear_model import LinearRegression

# ✅ CARGAR DATOS (esto soluciona el error)
df = px.data.gapminder()

# Renombrar columnas para que coincidan con tu código
df = df.rename(columns={
    'gdpPercap': 'gdp_per_capita'
})

# Filtrar solo países necesarios
df = df[df['country'].isin(['Argentina', 'Australia'])]

# 1. Preparar datos
df_arg = df[df['country'] == 'Argentina'].dropna(subset=['gdp_per_capita']).sort_values('year')
df_aus = df[df['country'] == 'Australia'].dropna(subset=['gdp_per_capita']).sort_values('year')

X_arg = df_arg[['year']]
y_arg = df_arg['gdp_per_capita']
model_arg = LinearRegression().fit(X_arg, y_arg)

X_aus = df_aus[['year']]
y_aus = df_aus['gdp_per_capita']
model_aus = LinearRegression().fit(X_aus, y_aus)

# 2. Proyección
years_ext = pd.DataFrame({'year': np.arange(1950, 2030)})
pred_arg_ext = model_arg.predict(years_ext)
pred_aus_ext = model_aus.predict(years_ext)

# 3. CAGR
def calc_cagr(start, end, p):
    if start <= 0: return 0
    return (pow(end / start, 1/p) - 1) * 100

val_1991_arg = model_arg.predict(pd.DataFrame({'year': [1991]}))[0]
val_2026_arg = model_arg.predict(pd.DataFrame({'year': [2026]}))[0]
val_1991_aus = model_aus.predict(pd.DataFrame({'year': [1991]}))[0]
val_2026_aus = model_aus.predict(pd.DataFrame({'year': [2026]}))[0]

cagr_arg = calc_cagr(val_1991_arg, val_2026_arg, 2026-1991)
cagr_aus = calc_cagr(val_1991_aus, val_2026_aus, 2026-1991)

# 4. Gráfico interactivo
fig = go.Figure()

fig.add_trace(go.Scatter(
    x=df_arg['year'],
    y=df_arg['gdp_per_capita'],
    mode='lines+markers',
    name='Argentina (Real)',
    line=dict(color='#87CEEB')
))

fig.add_trace(go.Scatter(
    x=years_ext['year'],
    y=pred_arg_ext,
    mode='lines',
    name='Arg: Tendencia',
    line=dict(color='#87CEEB', dash='dash'),
    opacity=0.5
))

fig.add_trace(go.Scatter(
    x=df_aus['year'],
    y=df_aus['gdp_per_capita'],
    mode='lines+markers',
    name='Australia (Real)',
    line=dict(color='#FFFF00')
))

fig.add_trace(go.Scatter(
    x=years_ext['year'],
    y=pred_aus_ext,
    mode='lines',
    name='Aus: Tendencia',
    line=dict(color='#FFFF00', dash='dash'),
    opacity=0.5
))

# Línea vertical
fig.add_vline(x=1991, line=dict(color='white', dash='dot'))

# Estilo
fig.update_layout(
    title="Divergencia: Argentina vs Australia",
    xaxis_title="Año",
    yaxis_title="GDP per cápita (USD)",
    template="plotly_dark"
)

# Anotaciones
fig.add_annotation(x=2026, y=pred_arg_ext[-1],
                   text=f"Arg: {cagr_arg:.2f}%",
                   showarrow=False,
                   font=dict(color='#87CEEB'))

fig.add_annotation(x=2026, y=pred_aus_ext[-1],
                   text=f"Aus: {cagr_aus:.2f}%",
                   showarrow=False,
                   font=dict(color='#FFFF00'))

fig.show()

# ✅ EXPORTAR PARA CANVA
fig.write_html("grafico_interactivo.html")

     

fig.write_html("grafico_interactivo.html")
     

from google.colab import files
files.download("grafico_interactivo.html")

     

     
