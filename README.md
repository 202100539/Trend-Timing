
# Trend Timing
Proyecto asignatura: Desarrollo de aplicaciones para la Visualización de Datos
**¿Cómo nacen, crecen y desaparecen las tendencias de moda?**

Proyecto de la asignatura *Desarrollo de Aplicaciones para la Visualización de Datos* (curso 2026-27).

## Descripción

Trend Timing es un observatorio interactivo de tendencias de moda construido con series temporales de Google Trends. Compara 15-20 tendencias (colores, estampados, prendas, calzado, accesorios y estéticas), analiza su evolución, las clasifica según su fase actual y estima su evolución a corto plazo.

Está pensado para creadores de contenido, tiendas y compradores de moda, y profesionales de marketing y comunicación.

La aplicación se despliega en una URL pública con Dash y Render.

## Objetivos

1. Responder a tres preguntas: ¿qué tendencias están creciendo ahora?, ¿cómo han evolucionado hasta llegar aquí? y ¿cómo podrían evolucionar en las próximas semanas?
2. Clasificar cada tendencia en una fase (`Rising`, `Peak`, `Stable` o `Falling`) a partir de medias móviles, pendiente y momentum.
3. Estudiar la idea *"Fashion always comes back"*: distinguir tendencias estacionales, evergreen, de un único pico y con regreso (comeback).
4. Prever la evolución de cada tendencia a unas 8 semanas (modelos de referencia, ETS y/o SARIMA) con validación temporal.
5. Construir un pipeline reproducible: al incorporar datos nuevos se recalculan los indicadores y se actualizan las visualizaciones.
6. Ofrecer tres módulos: **Trend Radar**, **Trend Explorer** y **Trend Forecast**.
7. Desplegar la aplicación en una URL accesible y mejorarla de forma continua durante el semestre.

## Plan de trabajo inicial

| Fechas | Hitos |
| --- | --- |
| 5 - 11 oct | Repositorio y README; selección de 15-20 tendencias; descarga de Google Trends (5 años, con término ancla) |
| 12 - 19 oct | Limpieza, indicadores (medias móviles, pendiente, momentum) y clasificación de fases |
| 20 - 31 oct | Estacionalidad y análisis "Fashion always comes back?"; modelos de forecasting y validación temporal |
| 1 - 15 nov | Aplicación Dash con los tres módulos y callbacks |
| 16 - 22 nov | Despliegue en Render, pruebas, diseño y documentación |
| 23 - 30 nov | Ensayo de la exposición (5 min + 2 min de preguntas) y presentaciones |

## Estructura del repositorio

```
trend-timing/
├── data/
│   ├── raw/          # CSV de Google Trends tal cual se descargan
│   └── processed/    # series limpias, indicadores y fases
├── notebooks/        # limpieza, exploración, fases, estacionalidad y modelos
├── src/              # funciones reutilizables (limpieza, indicadores, fases, modelos, gráficos)
├── app.py            # aplicación Dash
├── requirements.txt
└── README.md
```

## Datos

Series semanales de interés de búsqueda en España (5 años) de Google Trends. Como solo permite comparar 5 términos a la vez y normaliza cada consulta, cada grupo incluye un término ancla común para poder compararlos.

## Tecnologías

Python, pandas, statsmodels, Plotly, Dash, Render y GitHub.

## Limitaciones

- Google Trends devuelve un índice relativo (0-100) de interés de búsqueda, no volumen absoluto: se interpreta como evolución relativa del interés, no como popularidad, ventas o consumo.
- El modelo de predicción estima la dirección y evolución esperada del interés a corto plazo, no la popularidad exacta ni la fecha de un pico.
