# Curvas de nivel COP30 para quebradas ≤ 2.000 km², con equidistancia ajustable desde 1 m

Aplicación Streamlit para descargar DEMs COP30 por partes desde OpenTopography, generar curvas de nivel por mosaicos y exportar un KMZ unificado.

## Objetivo

Trabajar con quebradas y cuencas de superficie menor o igual a 2.000 km², evitando procesar rasters demasiado grandes en Streamlit Cloud.

La aplicación puede dividir el área en varios DEM parciales, procesar cada tile de forma secuencial y escribir las curvas en un único KMZ.

## Entrada

- KMZ/KML con punto de control o polígono de cuenca.
- API Key de OpenTopography.
- DEM: COP30 por defecto. Alternativas: NASADEM, SRTMGL1, SRTMGL3, COP90, AW3D30.
- Área objetivo, radio o bbox manual.
- Número de DEM parciales.
- Equidistancia de curvas de nivel.
- Resolución interna de procesamiento.

## Salida

- `curvas_quebrada_2000km2_unificado.kmz`
- `resumen_curvas_quebrada_2000km2.json`

## Main file path para Streamlit Cloud

```text
app.py
```

## Versión de Python recomendada

Usar Python 3.11 en Streamlit Cloud.

## Parámetros recomendados

Para quebradas y cuencas ≤ 2.000 km²:

- Número de DEM parciales: 1 a 8.
- Para ≤ 300 km²: resolución interna 30 m.
- Para 300 a 1.000 km²: resolución interna 30 m o 60 m.
- Para 1.000 a 2.000 km²: resolución interna 60 m o 90 m.
- Equidistancia de curvas: 10 m, 20 m o 25 m.
- Simplificación: 10 m a 30 m.

## Recomendación práctica

Para probar una quebrada nueva, comenzar con:

- 4 DEM parciales.
- Resolución interna 60 m.
- Curvas cada 25 m.
- Simplificación 20 m.

Luego mejorar el detalle bajando la resolución interna a 30 m o usando curvas cada 10 m, siempre que la app no se ponga lenta.


## Equidistancia de curvas

La aplicación permite ajustar la equidistancia entre curvas de nivel desde 1 m hasta 200 m. Para evitar KMZ excesivamente pesados, las curvas de 1 m a 5 m se recomiendan solo para áreas pequeñas o análisis local. Para quebradas grandes, especialmente sobre 300 km², se recomienda usar 10 m, 20 m, 25 m, 50 m o más, según el objetivo técnico.
