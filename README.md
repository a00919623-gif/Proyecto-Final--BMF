[README.md](https://github.com/user-attachments/files/34600277/README.md)
# Proyecto Final - Modelos - Capital Analyst

**Econometría Financiera (FZ4038) · EGADE Business School**
**Autora:** Bárbara Martínez Flores (A00919623)
**Fecha:** noviembre de 2026

Aplicación de modelos econométricos al portafolio de 11 acciones que administro en el simulador **HowTheMarketWorks** (concurso *Econometría Financiera EGADE Oct 26*): NVDA, AMZN, CAT, WMT, COST, SYNA, PENG, FCX, AAPL, XOM y una posición en corto de GS.

## Enlaces de la entrega

| Entregable | Enlace |
|---|---|
| Notebook en Google Colab (Drive) | (https://colab.research.google.com/drive/1xy_QFmXGBtpDOQNFuRzpFUS9XImiRgQc?usp=sharing) |
| Reporte en HTML | [`ProyectoFinal_BMF.html`](ProyectoFinal_BMF.html) |

## Contenido del proyecto

| Sección | Modelo | Datos |
|---|---|---|
| 2 | Regresión lineal simple: beta de cada acción contra el S&P 500 y beta del portafolio | LSEG, diario, 2 ene 2025 – 6 nov 2026 |
| 3 | Matriz de correlación | LSEG, diario |
| 4 | Regresión lineal múltiple: modelo de AAPL comparado con Bloomberg y modelo intradía de 30 minutos de WMT | LSEG diario y de 30 minutos; Bloomberg |
| 5 | Datos de panel: pooled, efectos fijos, efectos aleatorios, Hausman, Wooldridge, Pesaran y Driscoll-Kraay | LSEG, reportes trimestrales de 10 empresas, 2019T3 – 2026T2 |
| 6 | Series de tiempo: Dickey-Fuller, ARIMA y pronóstico diario (10 días) e intradía (13 barras de 30 minutos) | WMT y NVDA |
| 7 | GARCH(1,1): pronóstico de volatilidad y VaR (puntos extra) | WMT y NVDA, diario 2016 – 2026 |
| 8 | Estrategia y operaciones en HowTheMarketWorks | Resultados de las secciones anteriores |

## Principales resultados

- **Beta del portafolio:** 1.04 antes de la estrategia y **0.94** después de vender PENG (beta 2.51) y comprar XOM (beta 0.15).
- **Correlación:** WMT, COST y XOM son las acciones que más diversifican el portafolio.
- **Regresión múltiple:** los coeficientes de RStudio con datos de LSEG coinciden con los de Bloomberg; con datos de 30 minutos, WMT se explica sobre todo por COST (R² de 46%).
- **Datos de panel:** el modelo de efectos fijos es el adecuado (prueba de Hausman); más ventas aumentan el flujo de efectivo de operación y más inventarios lo reducen.
- **Series de tiempo:** los precios de WMT y NVDA tienen raíz unitaria y sus rendimientos son estacionarios; los pronósticos ARIMA son casi planos con intervalos amplios.
- **GARCH:** NVDA es alrededor de 2.1 veces más volátil que WMT y su volatilidad es persistente.

## Estructura del repositorio

```
├── README.md
├── ProyectoFinal_BMF.Rmd          # código y texto (R Markdown)
├── ProyectoFinal_BMF.html         # reporte final
├── ProyectoFinal_BMF.ipynb        # mismo código para Google Colab (R)
├── prompt_copilot.md              # prompt usado en GitHub Copilot
├── datos/                         # 24 archivos de Excel de LSEG
│   ├── *_Price_History_*.xlsx     # precios diarios (12) e intradía de 30 min (5)
│   └── *_CF-Export-*.xlsx         # reportes trimestrales (10)
├── bbg_mra_aapl_2025.png          # capturas de Bloomberg
├── bbg_mra_aapl_2018.png
└── hmw_final_*.png                # capturas de HowTheMarketWorks
```

## Cómo reproducirlo

**En RStudio:**
1. Descarga o clona el repositorio y abre `ProyectoFinal_BMF.Rmd`.
2. Instala una sola vez los paquetes: `readxl`, `xts`, `plm`, `lmtest`, `sandwich`, `car`, `forecast`, `urca`, `fGarch` y `corrplot`.
3. Da clic en **Knit**.

**En Google Colab:**
1. Abre `ProyectoFinal_BMF.ipynb` y cambia el entorno de ejecución a **R**.
2. Sube la carpeta `datos/` y las imágenes `.png` al panel de archivos.
3. Corre la celda de instalación y después *Ejecutar todas*.

## Fuentes de datos

- **LSEG Workspace:** precios de cierre diarios e intradía (*Price History*) y estados financieros trimestrales (*Financial Summary*, vista estandarizada).
- **Bloomberg:** *Multi-Security Regression Analysis* del modelo de AAPL.
- **HowTheMarketWorks:** posiciones, órdenes y balances del portafolio.
- Gujarati, D. y Porter, D. *Econometría*, 5a. edición, capítulos 16 y 21.
