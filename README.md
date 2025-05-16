# 🚖 Predicción de Pedidos de Taxi – Sweet Lift Taxi

La compañía **Sweet Lift Taxi** ha recopilado datos históricos sobre pedidos de taxis en los aeropuertos. El objetivo del proyecto es **predecir la cantidad de pedidos de taxis para la próxima hora**, especialmente durante las horas pico, a fin de atraer a más conductores de manera proactiva.

📌 La métrica **RECM** (Raíz del Error Cuadrático Medio) en el conjunto de prueba no debe ser superior a **48**.

---

## 📁 Descripción de los Datos

- Fuente: Archivo `taxi.csv`  
- Columna objetivo: `num_orders` (número de pedidos por hora)

---

## ⚙️ Estructura del Proyecto

1. ### **Preparación de Datos**
   - Importación de librerías: `pandas`, `numpy`, `matplotlib`, `sklearn`, `statsmodels`, `lightgbm`, `catboost`.
   - Lectura de los datos desde archivo CSV.

2. ### **Análisis de Serie Temporal**
   - Evaluación visual de estacionariedad.
   - Prueba de **Dickey-Fuller** para confirmar estadísticamente la estacionariedad.
   - Análisis de **autocorrelación** para identificar desfases relevantes.

3. ### **Formación de Características**
   - Generación de **media móvil** con distintas ventanas: 1, 10 y 24.
   - Extracción de atributos de **fecha**: mes, día y hora.
   - Inclusión de desfases identificados como relevantes: **1, 22, 23 y 24**.

4. ### **Preparación Datos Entrenamiento**
   - Eliminación de datos faltantes.
   - Separación del conjunto en datos de **entrenamiento y prueba**.

5. ### **Entrenamiento de Modelos de Machine Learning**
   - **Regresión Lineal**
   - **Random Forest**
   - **LightGBM**

6. ### **Conclusiones**
   - Aunque visualmente parecía no estacionaria, se confirmó que la serie sí lo era mediante la prueba Dickey-Fuller.
   - Los desfases más predictivos fueron 1, 22, 23 y 24. Usar solo el defase 1 aumentó el error.
   - La inclusión de atributos como mes, día y hora mejoró el desempeño.
   - El uso de una **ventana de 10** para la media móvil redujo el RECM respecto a usar solo 1. La ventana de 24 no aportó mejora adicional.
   - El modelo de regresión lineal podría mejorar con estandarización.
   - El mejor rendimiento fue del modelo **LightGBM** tras el ajuste de hiperparámetros.
   - Se logró cumplir con la métrica requerida: **un modelo con RECM menor a 48**.

---

## 🚀 Cómo Clonar este Repositorio

```bash
git clone https://github.com/dsc530/taxis_ordenes.git
