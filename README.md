# Análisis de la Calidad del Aire en Colombia — PM2.5 (2011–2024)

Análisis estadístico completo (descriptivo, inferencial y visual) de las concentraciones de
**PM2.5** en Colombia, a partir del conjunto de datos abiertos **"Calidad del Aire en
Colombia (Promedio Anual)"** publicado por el **IDEAM** a través del subsistema **SISAIRE**
en el portal oficial de datos abiertos **datos.gov.co**.

---

## 📁 Contenido del repositorio

| Archivo | Descripción |
|---|---|
| `analisis_calidad_aire_colombia.ipynb` | Notebook Jupyter con el análisis completo (carga, limpieza, estadística, pruebas de hipótesis y visualizaciones) |
| `calidad_aire_colombia.csv` | Dataset crudo descargado de datos.gov.co (29.683 registros) |
| `README.md` | Este documento |
| `informe_calidad_aire_colombia.pdf` | Informe en formato APA 7 (con referencias) |

> **Nota:** el notebook descarga automáticamente el dataset si no encuentra el CSV local.

---

## 📊 Descripción del dataset

- **Nombre:** Calidad del Aire en Colombia (Promedio Anual)
- **Fuente:** Instituto de Hidrología, Meteorología y Estudios Ambientales (IDEAM) – SISAIRE
- **Portal:** https://www.datos.gov.co/d/kekd-7v7h
- **Licencia:** Creative Commons Attribution Share Alike 4.0 (CC BY-SA 4.0)
- **Cobertura:** Nacional — 654 estaciones, 49 departamentos, 339 municipios
- **Periodo:** 2011 – 2024
- **Variables:** 20 (contaminantes: PM10, PM2.5, PST, NO, NO2, SO2, O3, CO; y meteorología: TAire, HAire, VViento, P, PLiquida, RGlobal, RUVb, DViento)

Cada fila resume un año de medición de una variable en una estación (promedio, mediana,
máximo, mínimo, percentil 98 y conteo de excedencias respecto a la norma).

---

## ⚙️ Requisitos

- Python 3.9+
- Librerías:
  - `pandas`
  - `numpy`
  - `matplotlib`
  - `seaborn`
  - `scipy`

```bash
pip install pandas numpy matplotlib seaborn scipy
```

Para ejecutar el notebook:

```bash
jupyter notebook analisis_calidad_aire_colombia.ipynb
```

---

## 🔬 Estructura del análisis

1. **Configuración** — importación de librerías.
2. **Descarga** — obtención del CSV desde la API de Socrata.
3. **Estructura** — exploración de variables, años y cobertura.
4. **Limpieza** — normalización de nombres de departamentos/municipios (tildes y mayúsculas) y selección del PM2.5 (exposición 24 h).
5. **Análisis descriptivo** — media, mediana, dispersión, asimetría y curtosis.
6. **Visualizaciones** — histograma, evolución anual, rankings por departamento y municipio.
7. **Valores atípicos** — método IQR.
8. **Pruebas de hipótesis** (no paramétricas):
   - Shapiro–Wilk (normalidad)
   - Wilcoxon de una muestra (cumplimiento de la norma de 25 µg/m³)
   - Spearman y Mann–Whitney (tendencia temporal)
   - Mann–Whitney (diferencia regional Antioquia vs Cundinamarca)
9. **Correlación** PM2.5–PM10 (Pearson).
10. **Conclusiones**.

---

## ✅ Resultados principales

- **PM2.5 nacional:** media 17.0 µg/m³, mediana 15.8 µg/m³, máximo 68.6 µg/m³.
- **Cumplimiento:** la mediana nacional está significativamente por debajo de la norma anual (25 µg/m³), pero el **11 %** de los registros la supera.
- **Tendencia:** disminución significativa, de ~21 µg/m³ (2011–2015) a ~15.4 µg/m³ (2020–2024); `ρ = −0.30`, `p ≈ 6.6e-43`.
- **Regional:** Antioquia (Valle de Aburrá) presenta PM2.5 significativamente mayor que Cundinamarca (`p ≈ 4.7e-17`); Sabaneta, Itagüí y Medellín lideran los peores registros.
- **Correlación:** PM2.5 y PM10 correlacionan positivamente (`r = 0.57`, `p ≈ 1e-72`).

---

## 📚 Referencias (APA 7)

1. Instituto de Hidrología, Meteorología y Estudios Ambientales. (2026). *Calidad del aire en Colombia (promedio anual)* [Conjunto de datos]. Datos Abiertos Colombia. https://www.datos.gov.co/d/kekd-7v7h
2. Ministerio de Ambiente y Desarrollo Sostenible. (2017). *Resolución 2254 de 2017: Por la cual se adopta la norma de calidad del aire ambiente y se dictan otras disposiciones*. Diario Oficial No. 50.456.
3. Organización Mundial de la Salud. (2021). *Directrices mundiales de la OMS sobre la calidad del aire: Material particulado (PM2.5 y PM10), ozono, dióxido de nitrógeno, dióxido de azufre y monóxido de carbono*. Organización Mundial de la Salud.
4. Pope, C. A., III, & Dockery, D. W. (2006). Health effects of fine particulate air pollution: Lines that connect. *Journal of the Air & Waste Management Association, 56*(6), 709–742. https://doi.org/10.1080/10473289.2006.10464485
5. Área Metropolitana del Valle de Aburrá. (2020). *Plan Integral de Gestión de la Calidad del Aire del Valle de Aburrá (PIGECA 2030)*.
6. De Vito, S., Massera, E., Piga, M., Martinotto, L., & Di Francia, G. (2008). On field calibration of an electronic nose for benzene estimation in an urban pollution monitoring scenario. *Sensors and Actuators B: Chemical, 129*(2), 750–757. https://doi.org/10.1016/j.snb.2007.09.060

---
https://github.com/CAlejandroPerdomo/UDEC-DATOS-NO-ESTRUCTURADOSQ/blob/main/README.md#%EF%B8%8F-aviso
