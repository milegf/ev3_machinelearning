# Segmentación y clasificación de viviendas en Ames, Iowa

**Evaluación Parcial N°3: PCA, K-Means y ensambles**
**Ramo:** Machine Learning 001D
**Docente:** Mauro Mercado
**Integrantes:** Milenka Guerra, Aydan González, Tomas González y Nicolas Sagua

Se utiliza el mismo dataset de la Evaluación 2 (Ames Housing, 2.930 ventas entre 2006 y 2010) para reducir la dimensión de las viviendas con PCA, agruparlas con K-Means y clasificar con dos ensambles si una vivienda se vende sobre o bajo el precio mediano. El desarrollo completo está en [`notebooks/Ev3_PCA_KMeans_Ensambles.ipynb`](notebooks/Ev3_PCA_KMeans_Ensambles.ipynb).

## Relación con la evaluación 2

* De la Evaluación 2 solo se conservan la lectura correcta del archivo y la corrección de 12 errores de digitación, que son reglas fila por fila. El alcance, las variables y la etiqueta se definen de nuevo.

## Datos preparados

| Elemento | Definición |
|---|---|
| Alcance | 2.925 viviendas, se excluyen las de más de 4.000 pies² por recomendación del autor del dataset |
| División | 60% entrenamiento, 20% validación y 20% prueba, estratificada por quintiles de precio |
| Selección de variables | Correlación de Spearman con el precio de al menos 0,5 y eliminación de redundantes (correlación mayor a 0,8), calculado en entrenamiento |
| Variables (8) | `Overall Qual`, `Gr Liv Area`, `Garage Cars`, `Year Built`, `Full Bath`, `Total Bsmt SF`, `Year Remod/Add`, `Fireplaces` |
| Etiqueta | `precio_alto`, que vale 1 si el precio supera la mediana de entrenamiento (USD 160.000) |
| Transformación | Imputación con mediana y StandardScaler, ajustados solo con entrenamiento |

## Estructura del proyecto

```
housing-ml-ev3/
├── data/
│   ├── raw/          Dataset original
│   └── processed/    Entrenamiento, validación y prueba escalados (los genera el notebook)
├── notebooks/
│   └── Ev3_PCA_KMeans_Ensambles.ipynb
├── images/           Gráficos para la presentación (los genera el notebook)
├── requirements.txt
└── README.md
```

## Cómo ejecutarlo

**En Google Colab.** Abrir el notebook, subir `Ames_Iowa_Housing_Dataset.csv` a la sesión y ejecutar todas las celdas.

**En local.** Instalar las librerías con `pip install -r requirements.txt`, abrir el notebook y ejecutar todas las celdas en orden. La semilla está fijada en 42, por lo que los resultados se reproducen sin cambios.

**Requisitos.** Python 3.11 o superior. El proyecto se verificó con Python 3.13.

## Referencias
* De Cock, D. (2011). *Ames, Iowa: Alternative to the Boston Housing Data as an End of Semester Regression Project*. Journal of Statistics Education, 19(3).
