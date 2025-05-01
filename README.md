# 🛫 MacBrides-Aerospace: Análisis y Predicción de Tiempo hasta Despegue

Este repositorio contiene el proyecto, cuyo objetivo es la predicción del **tiempo hasta despegue** de aeronaves en el aeropuerto Adolfo Suárez Madrid-Barajas, mediante el análisis de datos ADS-B y el uso de modelos de machine learning.

## 🚀 Objetivo

Predecir con precisión el tiempo que una aeronave tarda en despegar desde que llega al punto de espera, considerando factores como el tráfico aéreo, condiciones meteorológicas y dinámicas operativas del aeropuerto.

---

## 📂 Estructura del Proyecto
📦 MacBrides-Aerospace 

├── data/ # Datos procesados y en crudo (.parquet) 

├── notebooks/ # Notebooks de análisis exploratorio 

├── scripts/ # Scripts de procesamiento, entrenamiento y evaluación 

├── models/ # Modelos entrenados y resultados


---

## 🧩 Etapas del Proyecto

### 1. Reprocesamiento de Datos
- Decodificación y filtrado de mensajes ADS-B.
- Extracción de variables clave (velocidad, altitud, identificador, etc.).
- Filtrado geográfico para centrarse en Madrid-Barajas.
- Identificación y construcción de trayectorias de despegue.

### 2. Enriquecimiento y Filtrado
- Selección de vuelos que se detienen en puntos de espera.
- Decodificación de variables meteorológicas desde mensajes BDS 4,4 y 4,5.
- Compresión y optimización de datos.

### 3. Análisis Exploratorio
- Distribución de pistas y puntos de espera.
- Análisis de tráfico aéreo y horas punta.
- Exploración de tiempos en espera y dinámica operativa.

### 4. Transformación Previa al Modelado
- Codificación cíclica de variables temporales.
- Clipping de outliers, normalización y escalado.
- Pipeline de transformación con `ColumnTransformer`.

### 5. Entrenamiento de Modelos
- Modelos usados: Random Forest, Gradient Boosting, SVR, KNN.
- Métrica principal: MAE.
- Mejor modelo: **Gradient Boosting** con MAE ≈ 67.6 segundos.

---

## 📊 Resultados

- **Tamaño del dataset final**: 160.000 registros (5895 vuelos)
- **Modelo seleccionado**: Gradient Boosting
- **Métricas**:
  - MAE: 67.6 s
  - RMSE: 104.1 s
  - R²: 0.166

### Observaciones:
- Sesgo hacia ciertas pistas y tipos de aeronaves.
- Subestimación de tiempos altos por escasez de datos.
- El modelo es eficaz en condiciones normales, pero falla en casos extremos.

---

## 👥 Equipo y Reparto de Tareas

| Nombre              | Rol                             |
|---------------------|----------------------------------|
| Carlos Mantilla     | Preprocesamiento                |
| Héctor García       | Preprocesamiento                |
| Diego Alonso        | Entrenamiento                   |
| Telmo Aracama       | Limpieza y Entrenamiento        |
| Mario López         | Entrenamiento y Evaluación      |
| Ignacio Gutiérrez   | Preprocesamiento                |
| Pablo Rodríguez     | Entrenamiento y Evaluación      |

---

## 🛠 Tecnologías y Herramientas

- `pandas`, `numpy`
- `scikit-learn`
- `matplotlib`, `seaborn`
- `joblib`, `multiprocessing`
- Archivos de datos en `.parquet`

---

## 📈 Reproducibilidad

1. Clona este repositorio:
   ```bash
   git clone https://github.com/tu_usuario/macbrides-aerospace.git
   cd macbrides-aerospace

2. Instala las dependencias:
    ```bash
   pip install -r requirements.txt

3. Ejecuta los scripts:
     ```bash
    python scripts/preprocess.py
    python scripts/train_model.py
