# Tópicos D — Machine Learning aplicado a Ciberseguridad

Curriculum educativo de aprendizaje automático supervisado con enfoque en ciberseguridad, desarrollado en Python con Jupyter Notebooks. Los notebooks progresan desde algoritmos fundamentales hasta un pipeline completo de ML sobre el dataset NSL-KDD de detección de intrusiones de red.

## Contenido

### Notebooks 4–5 — Regresión

| Notebook | Tema |
|----------|------|
| [4](notebook_4-5/4_test.ipynb) | **Regresión Lineal** — predice el coste de un incidente de seguridad a partir del número de sistemas afectados (datos sintéticos) |
| [5](notebook_4-5/5_test.ipynb) | **Regresión Logística** — detección de correo SPAM |

### Notebooks 6–10 — Pipeline ML sobre NSL-KDD

Todos operan sobre el dataset de ciberseguridad **NSL-KDD** en formato ARFF.

| Notebook | Tema |
|----------|------|
| [6](notebook_6/6_Visualización+del+conjunto+de+datos.ipynb) | **Visualización** — `scatter_matrix`, codificación de etiquetas, análisis de correlación |
| [7](notebook_7/7_División+del+conjunto+de+datos.ipynb) | **División train/test** — `train_test_split` |
| [8](notebook_8/8_Preparación+del+conjunto+de+datos.ipynb) | **Preprocesamiento** — imputación, one-hot encoding, escalado |
| [9](notebook_9/9_Creación+de+Transformadores+y+Pipelines+personalizados.ipynb) | **Pipelines** — transformadores personalizados con `BaseEstimator` + `TransformerMixin`, `ColumnTransformer` |
| [10](notebook_10/10_Evaluación+de+resultados.ipynb) | **Evaluación** — validación cruzada, precisión, recall, F1 |

Cada notebook sigue el flujo: **Datos → Preprocesamiento → Ingeniería de características → Entrenamiento → Evaluación → Predicción**

## Dataset

**NSL-KDD** es una versión mejorada del dataset KDD Cup 99 para sistemas de detección de intrusiones (IDS). Contiene tráfico de red etiquetado como `normal` o `anomaly`.

- Fuente: [Canadian Institute for Cybersecurity](https://www.unb.ca/cic/datasets/nsl.html)
- Formato: ARFF y TXT/CSV
- Train set: 125 973 instancias, 42 atributos

> Tavallaee, M., Bagheri, E., Lu, W., & Ghorbani, A. (2009). *A Detailed Analysis of the KDD CUP 99 Data Set*. IEEE CISDA.

## Instalación

Requiere Python 3.13 y [`uv`](https://github.com/astral-sh/uv).

```bash
# Instalar dependencias
uv sync

# Lanzar un notebook
jupyter notebook notebook_6/6_Visualización+del+conjunto+de+datos.ipynb
```

Los notebooks también incluyen enlaces a **Google Colab** para ejecutarlos sin instalación local.

### Dependencias principales

| Paquete | Uso |
|---------|-----|
| `scikit-learn` | Modelos, pipelines, métricas |
| `pandas` | Manipulación de datos |
| `matplotlib` | Visualización |
| `liac-arff` | Lectura de ficheros ARFF |
| `scipy` | Utilidades científicas |

## Nota sobre compatibilidad

`liac-arff 2.5.0` tiene un bug con atributos nominales que tienen un espacio antes del `}` de cierre (e.g. `{ 'S0', 'SF' }`). Los ficheros ARFF del dataset han sido corregidos eliminando ese espacio para que la librería los parsee correctamente.
