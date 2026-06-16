# 🎮 OUROBOROS PROJECT
### *Steam Analytics Advisory — Consultoría de Datos para la Industria de los Videojuegos*

> **Idea central:** el cálculo es la herramienta, la pregunta de negocio es la razón de ser. Cada KPI, cada scoring y cada forecast de este proyecto nace de una pregunta concreta que se haría una empresa antes de invertir en un videojuego.

**Equipo:** Bautista Díaz · Damián García · Joaquín Vazquez
**Materia:** Ciencia de Datos — Universidad Católica Argentina, Sede Mendoza · 2026
**Herramientas:** Python · Pandas · NumPy · Matplotlib · Seaborn · Plotly Express / Graph Objects · Scikit-learn (MinMaxScaler, LinearRegression, PolynomialFeatures) · Google Colab

---

## 📁 Datasets

| Dataset | Archivo | Filas | Columnas |
|---|---|---|---|
| Top 500 Steam (curado) | `steam_games_2026_500.csv` | 500 | 13 |
| Catálogo completo Steam | `games_dataset.csv` | 50.872 | 13 |
| Lanzamientos históricos por año | `steamdb_game_releases_per_year.csv` | 21 | 3 |

> Variable de cruce entre datasets: **`AppID` / `app_id`**

---

## 📋 Índice

**Primera parte — Steam Analytics Advisory**
1. [Introducción del proyecto](#-introducción-del-proyecto)
2. [Conceptos clave](#-conceptos-clave)
3. [Proceso de actualización del dataset](#-proceso-de-actualización-del-dataset)
4. [Bloques de código — primera parte](#-bloques-de-código--primera-parte)
5. [Conclusión de la primera presentación](#-conclusión-de-la-primera-presentación)

**Segunda parte — Ouroboros Project**
6. [Introducción segunda parte](#-introducción-segunda-parte)
7. [Explicación de los datasets](#-explicación-de-los-datasets)
8. [Contenido de los datasets](#-contenido-de-los-datasets)
9. [Bloques de código — segunda parte](#-bloques-de-código--segunda-parte)
10. [Conclusión del proyecto](#-conclusión-del-proyecto)
11. [Glosario](#-glosario)

---

## 🟢 Introducción del proyecto

**Steam Analytics Advisory** nace como una consultora de análisis de datos especializada en la industria de los videojuegos, pensada para desarrolladoras, publishers y estudios independientes que necesitan tomar decisiones estratégicas respaldadas por datos reales del mercado en lugar de intuición.

La industria del videojuego mueve más de 180.000 millones de dólares anuales a nivel global, y Steam —la plataforma de distribución digital más importante del mundo, con más de 50.000 juegos disponibles— genera una cantidad enorme de datos públicos que muy pocas empresas saben aprovechar. El objetivo del proyecto es convertir esos datos en inteligencia accionable, analizando un recorte representativo del top de juegos más relevantes (por volumen de reviews, jugadores activos y revenue estimado) para ofrecer un mapa claro del mercado.

El mercado objetivo de la consultora se divide en tres segmentos:

| Segmento | Necesidad | Ejemplo de uso |
|---|---|---|
| Estudios independientes | Validar si su idea de juego tiene mercado antes de invertir en desarrollo | ¿Mi juego de estrategia tiene demanda? ¿A qué precio lanzarlo? |
| Publishers medianos | Optimizar su catálogo y detectar géneros con alta rentabilidad | ¿Vale la pena adquirir un estudio de RPG? ¿Qué géneros tienen mejor ARPU? |
| Inversores / fondos de gaming | Due diligence antes de invertir en un estudio | ¿Es rentable el segmento de juegos de acción free-to-play? |

---

## 🟢 Conceptos clave

- **KPI (Key Performance Indicator):** mide una sola dimensión del negocio (ej. eficiencia de monetización, velocidad de adopción).
- **Scoring:** combina varias dimensiones en un único número para poder ordenar y comparar; la decisión más importante no es la fórmula, sino qué variables se incluyen y qué peso recibe cada una.
- **Forecast:** identifica patrones de comportamiento sostenidos en el pasado y los proyecta hacia adelante, sin "inventar" el futuro.
- **ARPU (Average Revenue Per User):** ingreso promedio estimado por usuario, usado para calcular revenue en juegos free-to-play donde el precio de lista es $0.
- **ADPG / ADPC (Steam cut):** porcentaje que la plataforma retiene de cada venta; permite pasar de un revenue bruto a un revenue neto más realista.
- **F2P vs Premium:** los dos grandes modelos de negocio del mercado — regalar el juego y monetizar después, o cobrar por adelantado.
- **Owner / Estimated Owners:** estimación de la cantidad de personas que poseen un juego (no necesariamente lo juegan activamente).

---

## 🟡 Proceso de actualización del dataset

El **Bloque 1** del notebook documenta de forma explícita las decisiones tomadas sobre los datos crudos:

- Se descartan los registros marcados como DLC (`Is_DLC? == 'No'`), para no mezclar contenido descargable con juegos base.
- Se construye un **ARPU base por género** (tabla fija de 11 géneros, de USD 6 a USD 22) y se asigna a cada juego según su `Primary_Genre`; los géneros no mapeados reciben el ARPU de `Unknown`.
- Se crea **ADPG** (corte plano del 30% sobre juegos de pago) y, sobre esa base, un segundo cálculo más fino llamado **ADPC**: un corte de plataforma por tramos sobre el revenue bruto total (30% hasta USD 10M, 25% entre USD 10M y 50M, 20% por encima de USD 50M), replicando cómo Steam reduce su comisión a medida que un título genera más ingresos.
- Se calcula `positive_ratio` a partir de `Positive_Reviews / Total_Reviews` para los juegos que tienen al menos una review.
- **Decisión de filtrado para el análisis de revenue:** se conservan únicamente los juegos con `Total_Reviews > 0`, ya que sin reviews no hay forma confiable de validar su presencia real en el mercado. Sobre el dataset de 500 juegos, esto deja **479 juegos** utilizables para el análisis económico.
- **Revenue final:** para juegos de pago, `Estimated_Owners × Price_USD × (1 − ADPG) × (1 − ADPC)`; para juegos gratuitos, `Estimated_Owners × ARPU × (1 − ADPC)`.

Resultado del diagnóstico de nulos y distribución: 58 juegos gratuitos, 422 de pago, y solo 1 juego sin ninguna review sobre el total de 500.

---

## 🟡 Bloques de código — primera parte

### Bloque 0 — Librerías e importación del dataset
Importa pandas, numpy, matplotlib, seaborn, plotly, PIL y los módulos de scikit-learn que se usarán más adelante (`MinMaxScaler`, `LinearRegression`, `PolynomialFeatures`). Define formateadores de moneda (`$1.2M`, `$350K`) y de cantidad de jugadores para que los ejes de los gráficos sean legibles. Verifica que los tres CSV y los tres logos de sistema operativo existan localmente antes de pedir una carga manual, y finalmente lee los tres datasets base (`df1`, `df2`, `df3`).

---

### Bloque 1 — Limpieza y preparación del dataset
Descrito en detalle en la sección [Proceso de actualización del dataset](#-proceso-de-actualización-del-dataset). Es la celda que decide cómo se manejan los juegos gratuitos, el corte de Steam y los juegos sin reviews, dejando como resultado el DataFrame `juegos_con_revenue`.

---

### Bloque 2 — Panorama general del mercado
Construye tres gráficos en una misma figura: el top 10 de géneros por cantidad de juegos, la distribución de precios entre los juegos de pago, y la proporción de juegos gratuitos vs. de pago. Es el punto de partida obligatorio antes de recomendar cualquier estrategia: entender el terreno antes de hablar de ingresos.

---

### Bloque 3 — Revenue por género
Agrupa `juegos_con_revenue` por `Primary_Genre` y calcula tanto el revenue total como el revenue promedio por juego, mostrando ambos rankings en gráficos de barras horizontales más un gráfico circular interactivo de Plotly con la participación de cada género en el revenue total.

---

### Bloque 4 — Calidad vs rentabilidad
Cruza `Review_Score_Pct_SteamDB` con `Revenue` en un scatter interactivo de Plotly (coloreado por género, con tooltip de nombre, precio y cantidad de reviews) para evaluar si los juegos mejor valorados generan más ingresos. Complementa con un gráfico de revenue promedio segmentado por rango de precio (`$0-5` a `$100+`).

---

### Bloque 5 — Jugadores activos y tendencias
Calcula el pico de jugadores en las últimas 24 horas agrupado por género, mostrando qué categorías tienen comunidades activas hoy (no solo en el pasado). Agrega además un gráfico circular sobre la distribución de juegos según su estado de compatibilidad con Steam Deck.

---

### Bloque 6 — Conclusiones y recomendaciones
Cierra la primera parte del análisis traduciendo los resultados anteriores en una recomendación ejecutiva concreta. El género con mejor revenue total y mejor cantidad de jugadores activos resultó ser **Action**, y el rango de precio con mejor revenue promedio fue **$50–100**.

---

## 🔴 Conclusión de la primera presentación

**Hallazgos principales de la primera entrega (Steam Analytics Advisory):**

- **Action** domina el mercado tanto en cantidad de juegos como en jugadores activos, consolidándose como el segmento de mayor volumen de la plataforma.
- Los juegos de **Massively Multiplayer** tienen el ARPU más alto del mercado (USD 22/usuario), lo que los convierte en el segmento más rentable bajo el modelo free-to-play, aun siendo menos numerosos.
- Incorporar el corte de plataforma (Steam cut) en el cálculo de revenue permite estimar con mayor precisión el ingreso neto real del desarrollador, diferenciándolo del ingreso bruto.
- La calidad (Review Score) tiene correlación positiva con el revenue, pero no es el único factor: juegos con reviews moderadas en géneros de alta demanda pueden superar en ingresos a juegos muy bien valorados en nichos pequeños.
- El pico de jugadores en 24 horas funciona como indicador de demanda viva, clave para proyectar el éxito de un lanzamiento.

**Recomendación ejecutiva de cierre:** una empresa que quiera entrar al mercado de Steam debería apuntar a géneros con alta demanda activa y revenue sostenido, con un precio en el rango óptimo identificado, o bien desarrollar un modelo free-to-play en géneros de alto ARPU como Massively Multiplayer o RPG.

---

## 🟢 Introducción segunda parte

A partir del feedback de la primera entrega, la consultora evoluciona hacia **Ouroboros Project**, profundizando el análisis con un marco más estratégico: cada indicador deja de responder solo "qué pasó" para responder primero **por qué le importa a una empresa**. La segunda parte incorpora:

- Cuatro **KPIs** de negocio: RPO, TTT, RRG e ILC.
- Dos **modelos de Scoring**: disponibilidad por sistema operativo, y F2P vs Premium.
- Dos **forecasts**: crecimiento del mercado en cantidad de lanzamientos, y un forecast combinado de precio original + descuento promedio.

Para esto, el dataset curado de 500 juegos se complementa con el catálogo completo de Steam (más de 50.000 títulos) y con una serie histórica de lanzamientos por año, lo que permite responder preguntas que el dataset acotado no podía responder por sí solo (por ejemplo, cobertura real de plataformas o tendencias de mercado a largo plazo).

---

## 🟢 Explicación de los datasets

El proyecto trabaja con **tres datasets** que se cargan al inicio del notebook como `df1`, `df2` y `df3`, cada uno con un propósito distinto:

- **`df1` — `steam_games_2026_500.csv`:** el dataset curado de los 500 juegos más relevantes de Steam (por reviews, jugadores activos y owners estimados). Es la base de los KPIs de negocio (RPO, TTT, RRG) y de los cálculos de revenue. Se carga con `encoding='Windows-1252'`, separador `;` y decimales con coma.
- **`df2` — `games_dataset.csv`:** el catálogo completo de Steam, con más de 50.000 títulos. Se usa para los análisis que requieren ver "todo el mercado" y no solo el top: el Scoring de disponibilidad por sistema operativo, el KPI de longevidad (ILC) y el enriquecimiento de la variable de calidad (`positive_ratio` oficial). Se carga en UTF-8 con separador `,`.
- **`df3` — `steamdb_game_releases_per_year.csv`:** serie histórica con la cantidad de juegos lanzados por año desde 2006. Es la base del forecast de crecimiento del mercado. Se carga en `UTF-8-SIG` con separador `;`.

---

## 🟢 Contenido de los datasets

### `df1` — steam_games_2026_500.csv (500 filas × 13 columnas)

| Columna | Contenido |
|---|---|
| `AppID` | Identificador único del juego en Steam |
| `Name` | Nombre del juego |
| `Release_Date` | Fecha de lanzamiento |
| `Primary_Genre` | Género principal (Action, RPG, Indie, Simulation, etc.) |
| `All_Tags` | Etiquetas/tags asociadas al juego |
| `Price_USD` | Precio de venta actual en dólares (0 para free-to-play) |
| `Review_Score_Pct_SteamDB` | Porcentaje de reviews positivas según SteamDB |
| `Total_Reviews` | Cantidad total de reviews recibidas |
| `Positive_Reviews` | Cantidad de reviews positivas |
| `Steam_Deck_Status` | Estado de compatibilidad con Steam Deck |
| `Estimated_Owners` | Estimación de propietarios del juego |
| `24h_Peak_Players` | Pico de jugadores activos en las últimas 24 horas |
| `Is_DLC?` | Indica si el registro corresponde a un contenido descargable |

Columnas derivadas creadas durante la limpieza: `ARPU`, `ADPG`, `ADPC`, `Gross_Revenue_Total`, `positive_ratio`, `Revenue`, `RRG`, `Rango_Precio`.

### `df2` — games_dataset.csv (50.872 filas × 13 columnas)

| Columna | Contenido |
|---|---|
| `app_id` | Identificador único del juego |
| `title` | Nombre del juego |
| `date_release` | Fecha de lanzamiento |
| `win` / `mac` / `linux` | Disponibilidad (booleano) en cada sistema operativo |
| `rating` | Calificación textual de Steam |
| `positive_ratio` | Porcentaje de reviews positivas (fuente oficial de Steam) |
| `user_reviews` | Cantidad total de reviews de usuarios |
| `price_final` | Precio final de venta |
| `price_original` | Precio de lista original |
| `discount` | Porcentaje de descuento aplicado |
| `steam_deck` | Compatibilidad con Steam Deck |

### `df3` — steamdb_game_releases_per_year.csv (21 filas × 3 columnas)

| Columna | Contenido |
|---|---|
| `DateTime` | Año de referencia |
| `Games` | Cantidad de juegos estándar lanzados ese año |
| `Limited Games` | Cantidad de juegos con perfil limitado en Steam lanzados ese año |

---

## 🔵 Bloques de código — segunda parte

### Scoring 1a — Disponibilidad por sistema operativo (sobre `juegos_con_revenue`)
Fusiona `juegos_con_revenue` con las columnas de plataforma de `df2` (`win`, `mac`, `linux`, `steam_deck`) usando `AppID`/`app_id`, carga los logos de Windows, Mac y Linux como imágenes y cuenta cuántos juegos del top están disponibles en cada sistema operativo.

### Scoring 1b — Disponibilidad por sistema operativo (sobre todo `df2`)
Repite el cálculo anterior pero sobre el catálogo completo de Steam (`df2`), para construir un mapa real de cobertura de mercado y no solo del top de juegos. Es la versión que aparece en el informe final: **Windows 98,4% (50.076 juegos)**, **Mac 25,6% (13.018 juegos)**, **Linux 17,8% (9.041 juegos)**.

### Scoring 2 — F2P vs Premium: impacto en comunidad
Toma dos listas curadas de referentes (10 títulos Free-to-Play y 10 títulos Premium) con su cantidad de reviews y porcentaje de reviews positivas. Aplica una transformación logarítmica (`log1p`) al volumen de reviews para evitar que los títulos gigantes aplasten al resto del ranking, normaliza ambas variables con `MinMaxScaler` y construye un score ponderado: **55% popularidad (reviews, en escala logarítmica) + 45% satisfacción (% de reviews positivas)**. El grupo Premium obtuvo un score promedio de **0,654** frente a **0,462** del grupo F2P.

### Merge 1 — Enriquecimiento de calidad
Cruza `Review_Score_Pct_SteamDB` (df1) con `positive_ratio` y `rating` (df2) por `AppID`/`app_id`, calcula la correlación entre ambas fuentes de calidad y la visualiza en un scatter con una línea de referencia de coincidencia perfecta. Sirve como validación de que la métrica de calidad usada en los KPIs es consistente entre ambas fuentes de datos.

### KPI N°1 — RPO (Revenue por Owner)
Calcula `Revenue / Estimated_Owners` para medir cuánto dinero genera cada juego por cada persona que lo posee, con un selector interactivo por tramo de precio. El RPO promedio del mercado analizado fue de **USD 16,74** (mediana USD 14,97), creciendo de forma proporcional al precio de lista: desde ~USD 5 en juegos de USD 9,99 hasta ~USD 37 en juegos de USD 69,99.

### KPI N°2 — TTT (Tasa de Tracción Temprana)
Calcula cuántas reviews acumula un juego por cada año que lleva disponible en el mercado, fusionando `user_reviews` y `positive_ratio` desde `df2` y calculando los años transcurridos desde `Release_Date`. Permite distinguir entre juegos que "explotaron" al salir y juegos de crecimiento lento y sostenido.

### KPI N°3 — RRG (Rentabilidad Relativa al Género)
Calcula `Revenue / promedio de Revenue del género` para cada juego, identificando "campeones de nicho" que superan ampliamente el estándar de su propia categoría aunque no figuren en el top de ingresos globales. El resultado se visualiza con un gráfico de barras interactivo en Plotly con escala de color RdYlGn.

### KPI N°4 — ILC (Índice de Longevidad Comercial)
Se construye sobre el catálogo completo (`df2`) en lugar del top 500, usando `user_reviews` como proxy de actividad de jugadores y calculando los años transcurridos desde el lanzamiento (con un piso de 1 año para que el índice tenga sentido). Permite distinguir entre "éxitos de temporada" y modelos de negocio durables.

### Forecast 1 — Evolución histórica y proyección de lanzamientos
Primero construye un gráfico de barras apiladas (juegos estándar + juegos de perfil limitado) con la serie histórica completa desde 2006. Luego ajusta una **regresión polinómica de grado 2** sobre los datos desde 2012 (en lugar de una línea recta) porque el crecimiento del mercado es exponencial y no lineal, y proyecta la cantidad de lanzamientos para 2026, 2027 y 2028 con una banda de error de ±15%, acercándose y potencialmente superando los 25.000–28.000 títulos nuevos por año.

### Forecast exploratorio — Porcentaje de juegos gratuitos por año
Calcula, año a año entre 2010 y 2022, qué porcentaje de los lanzamientos fueron gratuitos, y ajusta una **regresión lineal** para proyectar 2023, 2024 y 2025 (~25% a ~28%). Este análisis se mantiene en el notebook como exploración adicional, aunque no forma parte del informe final entregado al cliente.

### Forecast 2 — Forecast combinado de precio original y descuento
Calcula el promedio anual de `price_original` y `discount` entre 2010 y 2022, ajusta una regresión lineal independiente para cada variable y proyecta ambas hacia 2023–2025 en un único gráfico interactivo de Plotly con doble eje Y, pensado para explorar año por año el comportamiento conjunto de precio y descuento en una conversación con el cliente.

---

## 🏁 Conclusión del proyecto

El forecast combinado deja tres mensajes centrales para un inversor que evalúa entrar al mercado de Steam:

- **Más competencia, no menos:** el volumen de lanzamientos seguirá creciendo de forma acelerada, por lo que la diferenciación deja de ser una ventaja deseable y se convierte en una condición de supervivencia.
- **El precio de lista no es el precio real:** cualquier estrategia de pricing debe planificarse asumiendo que una porción del ciclo de vida del juego se venderá con descuento, y ese descuento tiende a profundizarse con el tiempo.
- **La ventana de oportunidad se reduce:** si cada año entran más competidores, los géneros y modelos de negocio identificados como "oportunidad" en este informe (RRG alto, baja saturación) tienen una vigencia limitada — la recomendación es actuar sobre esas oportunidades en el corto plazo, no posponer la decisión.

A nivel de indicadores, el RPO mostró que el revenue por usuario escala de forma consistente con el precio de lista; el TTT permitió separar lanzamientos de tracción inmediata de los de crecimiento sostenido; el RRG identificó campeones de nicho fuera del top de ingresos globales; el ILC distinguió modas pasajeras de modelos de negocio durables; el Scoring de sistema operativo confirmó que Windows es prácticamente universal (98,4%) mientras que Mac y Linux siguen siendo nichos desatendidos; y el Scoring F2P vs Premium mostró que, entre los referentes analizados, el modelo Premium construyó comunidades más consistentes en el tiempo que el modelo Free-to-Play.

---

## 📖 Glosario

| Término | Significado |
|---|---|
| **KPI** | Key Performance Indicator: indicador que mide una sola dimensión del negocio |
| **Scoring** | Índice que combina varias variables en un único número para ordenar/comparar |
| **Forecast** | Proyección de una variable hacia el futuro a partir de su comportamiento histórico |
| **RPO** | Revenue por Owner: ingreso estimado dividido por la cantidad de propietarios del juego |
| **TTT** | Tasa de Tracción Temprana: reviews acumuladas por cada año en el mercado |
| **RRG** | Rentabilidad Relativa al Género: revenue de un juego dividido por el promedio de revenue de su género |
| **ILC** | Índice de Longevidad Comercial: actividad de jugadores ajustada por antigüedad del juego |
| **ARPU** | Average Revenue Per User: ingreso promedio estimado por usuario, usado en juegos free-to-play |
| **ADPG** | Corte plano (30%) aplicado sobre el revenue bruto de juegos de pago |
| **ADPC** | Corte de plataforma efectivo, calculado por tramos sobre el revenue bruto total |
| **Owner / Estimated Owners** | Estimación de la cantidad de personas que poseen (no necesariamente juegan) un título |
| **F2P (Free-to-Play)** | Modelo de negocio donde el juego es gratuito y se monetiza después (microtransacciones, pases de batalla) |
| **Premium** | Modelo de negocio donde el juego se cobra por adelantado |
| **Steam Deck Status** | Indicador de compatibilidad de un juego con la consola portátil Steam Deck |
| **Revenue bruto vs. neto** | El bruto no descuenta la comisión de la plataforma; el neto sí (revenue bruto × (1 − corte de plataforma)) |
| **Regresión polinómica** | Modelo de regresión que ajusta una curva (no una recta) para capturar crecimiento acelerado |
| **MinMaxScaler** | Técnica de normalización que escala variables a un rango fijo (0 a 1) antes de combinarlas en un score |
| **log1p / transformación logarítmica** | Transformación matemática que reduce el peso de los valores extremos en un ranking |

---

_Ouroboros Project · Steam Analytics Advisory · Ciencia de Datos UCA Mendoza 2026_
