## *Trabajo Práctico 4: Ajuste de Hiperparámetros*
***Autora:*** *Sara Peña Alvarez*

#### *Objetivo*
*Este trabajo práctico tiene como objetivo aplicar técnicas de ajuste de hiperparámetros sobre un modelo de Random Forest Regressor para predecir el valor medio de las viviendas en California.
El análisis se centra en comparar tres enfoques:*
   - *Modelo Baseline (sin ajuste)*
   - *Búsqueda Aleatoria (Random Search)*
   - *Optimización Bayesiana (Optuna)*

#### *Data*
*El conjunto de datos utilizado proviene del California Housing Dataset, el cual contiene información sobre características geográficas, demográficas y estructurales de distintas zonas residenciales.*
*Variable	Descripción*
   - *longitude, latitude	Coordenadas geográficas de la zona*
   - *housing_median_age	Antigüedad promedio de las viviendas*
   - *total_rooms, total_bedrooms, population, households	Tamaño y composición del vecindario*
   - *median_income	Ingreso medio de los hogares (en decenas de miles de USD)*
   - *median_house_value	Valor medio de las viviendas (variable objetivo)*
   - *ocean_proximity	Proximidad al océano (variable categórica)*

#### *Metodología*
*Carga y exploración inicial de los datos*
   - *Se revisó la estructura del dataset (df.info()), se identificaron valores nulos y se analizaron estadísticas descriptivas.*
   - *Se detectaron 207 valores faltantes en total_bedrooms, que fueron tratados.*
   - *Se eliminaron variables categóricas para mantener solo numéricas en el modelo.*
*Análisis exploratorio (EDA)*
   - *La variable median_house_value presenta una distribución asimétrica hacia la derecha, con un límite superior en 500 000 USD.*
   - *median_income es la variable más correlacionada con el valor de las viviendas (r = 0.69).*
   - *Los gráficos boxplot mostraron que el precio medio aumenta con el ingreso y la antigüedad del barrio.*
*Preparación y partición del dataset*
   - *Se dividieron los datos en conjuntos de entrenamiento (80%) y prueba (20%).*
   - *Se implementó un pipeline con escalado (StandardScaler) y el modelo (RandomForestRegressor).*
*Modelos implementados*
   - *Baseline: parámetros por defecto del modelo.*
   - *Random Search: exploración aleatoria sobre un espacio de hiperparámetros definidos.*
   - *Optuna: optimización bayesiana enfocada en minimizar el RMSE mediante validación cruzada.*

#### *Resultados*
| Modelo         | RMSE       | R²       |
|----------------|------------|----------|
| **Baseline**   | 49 867.80  | 0.8102   |
| **Random Search** | 49 376.35  | 0.8139   |
| **Optuna**     | 49 318.33  | 0.8144   |

*El modelo Optuna logró el mejor rendimiento, reduciendo el RMSE y alcanzando un R² de 0.8144, lo que indica que explica más del 81 % de la variabilidad en los precios de vivienda.*
*Las mejoras respecto al modelo base fueron modestas pero consistentes, mostrando estabilidad del modelo tras la optimización.*
