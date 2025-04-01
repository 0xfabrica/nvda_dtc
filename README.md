## Informe de Proyecto: Predicción del Precio de Acciones de NVIDIA

Este proyecto se centró en la predicción del precio de las acciones de NVIDIA (NVDA) utilizando tres algoritmos de aprendizaje automático: Regresión Lineal (muestra sobreajuste), DecisionTreeClassifier y XGBoost. A continuación, se presenta un resumen de las métricas obtenidas para cada algoritmo:

**1. Regresión Lineal:**

**Objetivo:** Predecir el precio de cierre ajustado ("Adj Close").

**Variables:** Precio de apertura ("Open") y Volumen ("Volume").

**Métricas:**

| Métrica | Valor | Descripción |
|---|---|---|
| MAE (Mean Absolute Error) | 0.1776 | Error promedio en las predicciones, en las mismas unidades que la variable objetivo. |
| MSE (Mean Squared Error) | 0.4434 | Error cuadrático promedio, penaliza errores grandes. |
| RMSE (Root Mean Squared Error) | 0.6659 | Raíz cuadrada del MSE, en las mismas unidades que la variable objetivo. |
| R² (R-squared) | 0.9992 | Proporción de la varianza en la variable objetivo explicada por el modelo. |
| Accuracy | 0.9992 | Precisión del modelo. |
| MAPE (Mean Absolute Percentage Error) | 4.5555% | Error porcentual absoluto promedio. |
| MedAE (Median Absolute Error) | 0.0161 | Mediana de los errores absolutos. |
| Explained Variance Score | 0.9992 | Varianza explicada por el modelo. |
| Max Error | 8.8935 | Error máximo en las predicciones. |

**Observaciones:** Aunque las métricas como R² y Accuracy son muy altas, el Max Error es considerablemente alto, lo que indica la presencia de valores atípicos que afectan al modelo. Esto sugiere un posible sobreajuste, donde el modelo se ajusta demasiado a los datos de entrenamiento y no generaliza bien a datos nuevos.

**2. DecisionTreeClassifier:**

**Objetivo:** Predecir si el precio de las acciones subirá o bajará ("Target").

**Variables:** Precio de cierre ajustado ("Adj Close"), Volumen ("Volume") y "Tomorrow".

**Métricas:**

| Métrica | Valor | Descripción |
|---|---|---|
| Accuracy | 0.94 | Precisión del modelo. |
| Precision | 0.93 | Proporción de predicciones positivas correctas. |
| Recall | 0.94 | Proporción de verdaderos positivos identificados. |
| F1-score | 0.94 | Media armónica entre precisión y recall. |

**Matriz de Confusión:**

| | Predicho 0 | Predicho 1 |
|---|---|---|
| Real 0 | 2989 (VN) | 185 (FP) |
| Real 1 | 211 (FN) | 3173 (VP) |

**Observaciones:** DecisionTreeClassifier muestra un alto rendimiento en la clasificación, con una precisión del 94%. La matriz de confusión indica un buen balance entre la identificación de verdaderos positivos y verdaderos negativos. El modelo utilizado se encuentra guardado en el archivo **model_dtc_without_target.joblib**.

**3. XGBoost:**

**Objetivo:** Predecir si el precio de las acciones subirá o bajará ("Target").

**Variables:** Precio de cierre ajustado ("Adj Close"), Volumen ("Volume") y "Tomorrow".

**Métricas:**

| Métrica | Valor | Descripción |
|---|---|---|
| Accuracy | 0.7743 | Precisión del modelo. |
| Precision | 0.77 | Proporción de predicciones positivas correctas. |
| Recall | 0.77 | Proporción de verdaderos positivos identificados. |
| F1-score | 0.77 | Media armónica entre precisión y recall. |

**Matriz de Confusión:**

| | Predicho 0 | Predicho 1 |
|---|---|---|
| Real 0 | 686 (VN) | 242 (FP) |
| Real 1 | 202 (FN) | 838 (VP) |

**Observaciones:** XGBoost, aunque con menor precisión que DecisionTreeClassifier, sigue siendo un modelo aceptable con una precisión del 77%. La matriz de confusión revela un ligero desbalance en la clasificación, con una mayor cantidad de falsos positivos.

**Conclusión:**

* La regresión lineal, aunque con métricas aparentemente altas, presenta indicios de sobreajuste y podría no ser la mejor opción para este caso.
* DecisionTreeClassifier demostró un alto rendimiento en la clasificación, con una precisión del 94%.
* XGBoost, con una precisión del 77%, también es un modelo aceptable, aunque con un ligero desbalance en la clasificación.

**Recomendaciones:**

* Se recomienda seguir explorando otros modelos, como redes neuronales o modelos de series temporales, para mejorar aún más la precisión de las predicciones.
* Considerar la inclusión de otras variables relevantes para la predicción del precio de las acciones.
* Implementar estrategias de validación cruzada para obtener una evaluación más robusta de los modelos.
* Realizar un análisis más profundo del sobreajuste en la regresión lineal y considerar técnicas de regularización para mitigarlo.

**Nota:** Este proyecto fue realizado con fines educativos y no se recomienda su uso en producción. El mercado financiero es altamente volátil y predecir su comportamiento con precisión es extremadamente difícil. Por lo tanto, cualquier implementación real debe considerar enfoques más avanzados y herramientas especializadas para el análisis financiero.

