# ¿La corrupción mata? Evidencia estadística entre corrupción, economía y salud pública

> **Health-GDP-Corruption** es un análisis exploratorio y econométrico que evalúa cómo la corrupción institucional se relaciona con resultados de salud pública, mortalidad cardiovascular y esperanza de vida, usando datos internacionales para República Dominicana y países comparables.

<img width="907" height="732" alt="download" src="https://github.com/user-attachments/assets/4a481d40-5cf2-4432-b428-7f09a64396aa" />

## Resumen ejecutivo

Este proyecto nace de una pregunta inicial: **¿a mayor PIB, mejores resultados en salud?**

Al analizar República Dominicana y países comparables, el PIB por sí solo no explicaba completamente las diferencias en mortalidad cardiovascular, mortalidad infantil, mortalidad materna y esperanza de vida. El hallazgo central fue que la **corrupción institucional actúa como una fuga del sistema**: limita la capacidad real de convertir crecimiento económico y gasto público en servicios de salud efectivos.

La hipótesis del proyecto se resume así:

```text
↑ Corrupción → ↓ Inversión real en salud → ↓ Calidad de servicios → ↓ Esperanza de vida
```

## Hallazgos principales

Para República Dominicana, el modelo estima:

| Indicador | Resultado estimado |
|---|---:|
| Años de vida reducidos | **7.82 años** |
| Muertes cardiovasculares anuales asociadas | **10,069 muertes/año** |
| Efecto estimado por +0.1 en corrupción | **-0.96 años de esperanza de vida** |
| Serie histórica analizada | **2000–2019** |
| Proyección poblacional aplicada | **2025** |

> Nota metodológica: estos valores son estimaciones estadísticas derivadas de modelos OLS y correlaciones históricas. El análisis identifica asociaciones robustas y escenarios contrafactuales, pero no prueba causalidad individual directa.

## Visualizaciones

### 1. Correlación entre corrupción, economía y salud

<img width="907" height="732" alt="1_download" src="https://github.com/user-attachments/assets/c3bb1a57-f1f3-4051-8855-344b50ddc714" />

El mapa de calor muestra relaciones relevantes:

| Relación | Correlación |
|---|---:|
| Corrupción vs. mortalidad cardiovascular | **0.65** |
| Corrupción vs. mortalidad infantil | **0.87** |
| Corrupción vs. mortalidad materna | **0.89** |
| Corrupción vs. esperanza de vida | **-0.84** |
| Gasto en salud como % del PIB vs. corrupción | **-0.53** |

La lectura general es clara: los países con mayor corrupción presentan peores indicadores sanitarios y menor esperanza de vida.

### 2. Años de vida “robados” por corrupción

<img width="1600" height="960" alt="Code_Generated_Image (1)" src="https://github.com/user-attachments/assets/91cd990d-260a-42de-8ee5-89e3bf2c842a" />

República Dominicana aparece como el país con mayor reducción estimada de esperanza de vida dentro del grupo analizado.

### 3. Vidas perdidas anualmente por corrupción

<img width="1600" height="960" alt="Code_Generated_Image" src="https://github.com/user-attachments/assets/3001f705-791d-43f7-a866-12e7dfd986e7" />

La visualización estima el volumen de muertes cardiovasculares anuales asociadas al nivel de corrupción institucional, ajustado por población.

## Países analizados

El análisis compara siete países:

- República Dominicana
- Argentina
- Chile
- Estados Unidos
- España
- Corea del Sur
- México

## Fuentes de datos

Las fuentes utilizadas incluyen:

- **V-Dem Dataset** — Public Sector Corruption Index (`v2x_corr`)
- **World Bank Open Data** — PIB per cápita y gasto en salud como % del PIB
- **WHO Global Health Observatory** — Indicadores de salud y mortalidad
- **Oficina Nacional de Estadística** — Referencias poblacionales para República Dominicana

## Metodología

El análisis sigue cuatro pasos:

1. **Integración de datos**  
   Se combinaron bases de corrupción, PIB, gasto en salud, mortalidad cardiovascular, mortalidad infantil, mortalidad materna y esperanza de vida.

2. **Limpieza y transformación**  
   Se filtró la serie 2000–2019, se homologaron códigos de país y se consolidaron indicadores en una tabla analítica.

3. **Análisis de correlación**  
   Se calculó la matriz de correlaciones entre salud pública, economía y corrupción.

4. **Modelado OLS**  
   Se estimaron modelos de regresión lineal para evaluar el efecto de corrupción y gasto en salud sobre cada indicador sanitario.

Modelo conceptual simplificado:

```text
Indicador_salud = β0 + β1(Gasto_salud_%PIB) + β2(Índice_corrupción) + ε
```

## Stack técnico

| Herramienta | Uso |
|---|---|
| Python | Análisis principal |
| Pandas | Limpieza, integración y transformación de datos |
| NumPy | Operaciones numéricas |
| Statsmodels | Regresión OLS |
| Seaborn | Mapas de calor y visualización estadística |
| Matplotlib | Gráficos finales |
| Jupyter Notebook | Desarrollo reproducible |

## Estructura recomendada del repositorio

```text
health-gdp-corruption/
├── README.md
├── notebooks/
│   └── analysis_gdp_corruption_health.ipynb
├── assets/
│   ├── heatmap_correlation_rdbu.png
│   ├── heatmap_correlation_blues.png
│   ├── life_years_stolen.png
│   └── annual_deaths_cardio.png
├── data/
│   └── README.md
└── requirements.txt
```

## Instalación

Clona el repositorio:

```bash
git clone https://github.com/BraylinJR/health-gdp-corruption.git
cd health-gdp-corruption
```

Crea un entorno virtual:

```bash
python -m venv .venv
source .venv/bin/activate  # Linux / Mac
.venv\Scripts\activate     # Windows
```

Instala dependencias:

```bash
pip install -r requirements.txt
```

Ejemplo de `requirements.txt`:

```txt
pandas
numpy
matplotlib
seaborn
statsmodels
jupyter
```

Ejecuta el notebook:

```bash
jupyter notebook notebooks/analysis_gdp_corruption_health.ipynb
```

## Resultados destacados por país

| País | Muertes cardiovasculares estimadas/año | Reducción estimada en esperanza de vida |
|---|---:|---:|
| República Dominicana | 10,069 | 7.82 años |
| México | 87,598 | 5.91 años |
| Argentina | 20,654 | 3.96 años |
| Corea del Sur | 6,399 | 1.10 años |
| Estados Unidos | 36,264 | 0.94 años |
| Chile | 1,219 | 0.54 años |
| España | 1,932 | 0.36 años |

## Interpretación

El análisis sugiere que la corrupción no es solo un problema ético o administrativo. En sistemas de salud, puede convertirse en un determinante estructural de mortalidad.

Cuando los recursos se pierden en ineficiencia, captura institucional o mala asignación, el presupuesto deja de traducirse en médicos, medicamentos, infraestructura, prevención y continuidad de atención.

**La transparencia funciona como infraestructura sanitaria.** Sin integridad institucional, el crecimiento económico no necesariamente se convierte en vida.

## Limitaciones

- El análisis utiliza datos agregados por país, no microdatos individuales.
- Los resultados deben interpretarse como estimaciones estadísticas y no como causalidad clínica directa.
- El índice de corrupción es una aproximación institucional y puede contener incertidumbre de medición.
- La proyección poblacional 2025 se utiliza para traducir tasas en impacto humano actual.

## Autor

**Braylin Alexander Jiménez Reynoso**  
Economista | Data Scientist | Customer Intelligence | Health Systems Management

- LinkedIn: [www.linkedin.com/in/bajr2025](https://www.linkedin.com/in/bajr2025)
- GitHub: [BraylinJR](https://github.com/BraylinJR)

## Licencia

Este proyecto se publica con fines educativos, analíticos y de portafolio profesional.

Código bajo licencia **MIT**. Visualizaciones, texto analítico y diseño del caso © Braylin Alexander Jiménez Reynoso. Reutilización permitida con atribución.
