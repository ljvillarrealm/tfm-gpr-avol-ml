
# Riesgo geopolítico y volatilidad en los mercados financieros

**Un enfoque basado en *machine learning* e inteligencia artificial**

*Geopolitical Risk and Volatility in Financial Markets: A Machine Learning and Artificial Intelligence Approach*

Repositorio del Trabajo Fin de Máster. Contiene el código completo del análisis, que reproduce todas las cifras, tablas y figuras de la memoria a partir de los datos originales.

| | |
|---|---|
| **Autor** | Leonardo Jesus Villarreal Marcano |
| **Titulación** | Máster Universitario en Big Data y Ciencia de Datos |
| **Universidad** | Universidad Internacional de Valencia (VIU) |
| **Directora** | Edith Cecilia Macedo Ruiz |
| **Curso académico** | 2025–2026 |
| | |


---

## Resumen

Este trabajo evalúa si el riesgo geopolítico mejora la predicción de la volatilidad de cinco familias de activos financieros, representadas por seis series, y qué tipos de evento geopolítico concentran su contribución. Las familias son la renta variable (S&P 500), la energía (petróleo Brent y WTI), los metales preciosos (oro), la deuda soberana (bono del Tesoro estadounidense a diez años) y los criptoactivos (Bitcoin). El riesgo geopolítico se mide con el índice AI-GPR, construido con modelos de lenguaje, que permite separar su intensidad de su composición por siete tipos de evento: conflicto militar, tensión diplomática, terrorismo, guerra civil, amenaza nuclear, golpe de Estado y sanciones. La volatilidad se mide como volatilidad realizada a partir de rendimientos diarios, en horizontes semanal y mensual.

Se compara el modelo econométrico HAR con tres modelos de aprendizaje automático (Elastic Net, SVR y XGBoost). Cada modelo se estima con tres conjuntos de variables, el primero con la volatilidad pasada, el segundo con la intensidad del riesgo geopolítico y el tercero, solo en el horizonte mensual, con su composición por tipos de evento. Con la volatilidad pasada, el HAR es el modelo de referencia (HAR-RV), y con información geopolítica se convierte en su extensión lineal (HAR-X). Los modelos se entrenan con datos hasta 2021 y se evalúan fuera de muestra entre enero de 2022 y agosto de 2026, con reestimación mensual y la QLIKE como pérdida principal. La mejora predictiva se contrasta con los tests de Clark-West y Diebold-Mariano y con el conjunto de confianza de modelos, y la contribución de cada variable se mide con valores SHAP y con la importancia por permutación. Se incluyen seis pruebas de robustez y la validación de la reproducibilidad del flujo.

La intensidad del riesgo geopolítico mejora la predicción del modelo principal en un único caso, Bitcoin en el horizonte mensual, donde reduce la pérdida un 7,8 % frente al HAR-RV. Esta mejora resiste el ajuste por comparaciones múltiples, aunque la mayor ganancia del modelo no lineal frente al HAR-X no es significativa. En la energía solo aparecen mejoras en modelos secundarios del horizonte semanal, concentradas en episodios de tensión. En el resto de familias la intensidad no mejora la predicción, y en el oro la deteriora. La composición por tipos de evento no mejora a la intensidad en ningún modelo principal, aunque los modelos le asignan una contribución considerable, lo que distingue lo que un modelo usa de lo que efectivamente le ayuda a predecir. Los resultados son compatibles con un cambio en la relación entre riesgo geopolítico y volatilidad del entrenamiento a la prueba, periodo en el que el peso del conflicto militar se duplica.

**Palabras clave:** riesgo geopolítico, índice AI-GPR, predicción de la volatilidad, HAR-RV, aprendizaje automático, SHAP.

**Objetivos de Desarrollo Sostenible:** 8. Trabajo decente y crecimiento económico, 9. Industria, innovación e infraestructura, 16. Paz, justicia e instituciones sólidas.

---

## Abstract

This study assesses whether geopolitical risk improves volatility forecasts for five asset classes, represented by six series, and which types of geopolitical event account for its contribution. The asset classes are equities (S&P 500), energy (Brent and WTI crude oil), precious metals (gold), sovereign debt (10-year US Treasury bond) and crypto-assets (Bitcoin). Geopolitical risk is measured with the AI-GPR index, built with language models, which separates its intensity from its composition across seven event types: military conflict, diplomatic tension, terrorism, civil war, nuclear threat, coup d'état and sanctions. Volatility is measured as realized volatility from daily returns, at weekly and monthly horizons.

The econometric HAR model is compared with three machine learning models (Elastic Net, SVR and XGBoost). Each model is estimated with three sets of variables, the first with past volatility, the second with the intensity of geopolitical risk and the third, at the monthly horizon only, with its composition by event type. With past volatility, the HAR is the benchmark model (HAR-RV), and with geopolitical information it becomes its linear extension (HAR-X). The models are trained on data up to 2021 and evaluated out of sample between January 2022 and August 2026, with monthly re-estimation and QLIKE as the main loss function. Forecast improvements are assessed with the Clark-West and Diebold-Mariano tests and the model confidence set, and the contribution of each variable is measured with SHAP values and permutation importance. The study includes six robustness checks and a validation of the reproducibility of the workflow.

Geopolitical risk intensity improves the forecast of the main model in a single case, Bitcoin at the monthly horizon, where it reduces the loss by 7.8% relative to the HAR-RV. This improvement survives the adjustment for multiple comparisons, although the larger gain of the nonlinear model over the HAR-X is not significant. In energy, improvements appear only in secondary models at the weekly horizon and are concentrated in episodes of tension. In the remaining asset classes, intensity does not improve forecasts, and for gold it worsens them. The composition by event type does not improve on intensity in any main model, although the models assign it a considerable contribution, which distinguishes what a model uses from what actually helps it forecast. The results are consistent with a change in the relationship between geopolitical risk and volatility from the training to the test period, during which the weight of military conflict doubles.

**Keywords:** geopolitical risk, AI-GPR index, volatility forecasting, HAR-RV, machine learning, SHAP.

---

## Resolución de las hipótesis

| Hipótesis | Enunciado | Resolución |
|---|---|---|
| H1a | La intensidad del riesgo geopolítico (F1) mejora la predicción del modelo principal frente a la volatilidad pasada (F0) | Se cumple en uno de los doce casos: Bitcoin mensual (Clark-West *p* < 0,001; Holm *p* < 0,001) |
| H1b | En los casos que cumplen la H1a, la mejora es mayor en los modelos de aprendizaje automático que en el HAR-X | No se cumple (Diebold-Mariano unilateral, *p* = 0,068) |
| H2 | La composición por tipos de evento (F2) mejora la predicción respecto a la intensidad (F1) en el horizonte mensual | Se rechaza en los seis modelos principales |
| Exploratorio | Los tipos de evento persistentes concentran más contribución que los transitorios | No concluyente: depende del estimador y de la medida |

Los criterios de resolución se fijaron antes de la estimación y se describen en la sección 2.6.3 de la memoria.

---

## Estructura del repositorio

El notebook se organiza en bloques numerados que siguen el orden de la memoria: carga y control de calidad de los datos, construcción de variables, ajuste de hiperparámetros, predicción con ventana expansiva, evaluación, interpretabilidad, pruebas de robustez, tablas y figuras, y validación de la reproducibilidad.

``` shell

├── README.md
├── LICENSE.md
├── datos/
    └── raw/               # Datos del índice AI-GPR y las series financieras
├── notebooks/
│   ├── 00_tfm.ipynb       # flujo completo del análisis
│   └── figuras/           # figuras de la memoria, generadas por el notebook
│   └── resultados/        # predicciones y parámetros de los modelos entrenados, con un identificador por ejecución
└── docs/                  # Documentos

```

---

## Datos

**Índice AI-GPR.** Se emplean el índice consolidado diario y las series mensuales por tipo de evento de Iacoviello y Tong (2026), de libre acceso en la web de los autores. <!-- VERIFICAR: añadir el enlace de descarga y la fecha de la versión utilizada. -->

**Precios de las series financieras.** Proceden de un proveedor comercial de datos financieros cuyas condiciones de uso no permiten su difusión pública, por lo que no se incluyen en el repositorio. Están disponibles bajo petición al autor. Para reproducir el análisis, cada serie debe colocarse en `datos/precios/` con el formato que espera la celda de carga del notebook.

| Familia | Serie | Inicio | Fin |
|---|---|---|---|
| Renta variable | S&P 500 | Enero de 1999 | Septiembre de 2026 |
| Energía | Futuro de petróleo Brent | Enero de 1999 | Septiembre de 2026 |
| Energía | Futuro de petróleo WTI | Enero de 1999 | Septiembre de 2026 |
| Metales preciosos | Oro | Enero de 1999 | Septiembre de 2026 |
| Deuda soberana | Bono del Tesoro estadounidense a diez años | Enero de 1999 | Septiembre de 2026 |
| Criptoactivos | Bitcoin | Marzo de 2014 | Septiembre de 2026 |

---

## Ejecución

1. Crear o seleccionar un entorno con instalacción de Python y paquetes de gestion de notebooks.
2. Clonar este repositorio.
3. Abrir `notebooks/00_tfm.ipynb`, reiniciar el kernel y ejecutar todas las celdas en orden. El flujo no requiere intervención manual.

Los resultados se guardan en `figuras/` y `resultados/` con un identificador de ejecución, que permite asociar cada cifra de la memoria con la ejecución que la produjo.

### Validación de la reproducibilidad

El bloque final del notebook calcula la huella SHA-256 de los datos de entrada y compara todos los resultados con los de una ejecución anterior. El flujo principal se ejecutó completo dos veces, con un reinicio previo, y los resultados fueron idénticos con una tolerancia relativa de 10⁻⁹.

Las celdas añadidas al final del trabajo para las comprobaciones de cierre (ajuste de Holm, contraste de la H1b, verificación de Bitcoin, persistencia normalizada, componentes de la intensidad y vencimientos de la energía) son cálculos de consulta. No modifican ningún resultado anterior y no forman parte de la huella.

### Tiempo de cómputo

Medido en un equipo con 20 núcleos lógicos.

| Etapa | Tiempo |
|---|---|
| Ajuste de hiperparámetros (90 modelos) | 17 min |
| Predicción con ventana expansiva (6.720 reestimaciones) | 30 min |
| Valores SHAP con F2 (24 modelos) | 43 min |
| Valores SHAP con F1 (17 modelos) | 26 min |
| Pruebas de robustez | 19 min |
| Importancia por permutación (24 modelos) | 11 min |
| **Total** | **~2.4 hrs** |

---

## Publicación

### Cómo citar

```bibtex
@mastersthesis{villarreal_riesgo_2026,
  author = {Villarreal Marcano, Leonardo Jesus},
  title  = {Riesgo Geopolítico y Volatilidad en los Mercados Financieros: Un Enfoque Basado en Machine Learning e Inteligencia Artificial},
  school = {Universidad Internacional de Valencia},
  type   = {Trabajo Fin de Máster},
  year   = {2026}
}
```

---

### Licencia

El código se distribuye bajo la licencia indicada en el archivo `LICENSE`. Los datos de precios no se incluyen y están sujetos a las condiciones de su proveedor.

---

### Derechos de autor y publicación en curso

© 2026 Leonardo Jesus Villarreal Marcano. Todos los derechos reservados.

Este repositorio acompaña al Trabajo Fin de Máster y se publica para permitir su evaluación y la reproducción de sus resultados. A partir de este trabajo se está preparando un artículo científico, por lo que los métodos, los resultados y los textos aquí contenidos forman parte de una investigación en curso.

<!-- VERIFICAR: si el artículo se prepara en coautoría (por ejemplo, con la directora del TFM), indicarlo en el párrafo anterior. -->

Se permite consultar el código y ejecutarlo con el único fin de verificar los resultados del trabajo. No se autoriza, sin permiso expreso y por escrito del autor, la reutilización total o parcial del código, de los resultados o de los textos en otras publicaciones, trabajos académicos o productos derivados. Para cualquier uso distinto de la verificación, o para proponer una colaboración, puede contactarse con el autor.

Cualquier referencia a este trabajo debe citarlo como se indica en la sección Cómo citar. Cuando se publique el artículo, esta sección se actualizará con su referencia.

Los datos de precios no se incluyen en el repositorio y están sujetos a las condiciones de su proveedor. El índice AI-GPR está sujeto a las condiciones de uso de sus autores.

Copyright and work in progress

© 2026 Leonardo Jesus Villarreal Marcano. All rights reserved.

This repository accompanies a master's thesis and is made public for assessment and reproducibility purposes. A research article based on this work is currently in preparation. The code may be viewed and run solely to verify the results of the thesis. Any other use, including reuse of the code, results or text in other publications, academic works or derivative products, requires the author's prior written permission.