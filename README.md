# Análisis de Sentimiento en Reseñas de Películas IMDB para Film Junky Union

Este proyecto fue desarrollado para **Film Junky Union**, una comunidad dedicada a los amantes del cine clásico, con el objetivo de construir un sistema automático capaz de **clasificar reseñas de películas como positivas o negativas**. Utilizando técnicas de procesamiento de lenguaje natural (NLP), se entrenaron varios modelos de machine learning sobre un conjunto de reseñas con polaridad etiquetada, buscando alcanzar un **F1-score mínimo de 0.85**.

---

## Objetivo del Proyecto

Desarrollar un modelo de clasificación de texto para identificar **críticas negativas** en reseñas de películas. Esto permitirá filtrar contenido en plataformas y generar alertas sobre posibles tendencias de opinión negativa en lanzamientos cinematográficos.

---

## Tecnologías y Modelos Utilizados

- **Preprocesamiento de texto**:  
  - `NLTK` (stopwords, tokenización)
  - `spaCy` (lematización, parsing)

- **Vectorización**:
  - `TF-IDF Vectorizer`

- **Modelos de clasificación**:
  - Regresión Logística (`LogisticRegression`)
  - Clasificador LGBM (`LGBMClassifier`)
  - Dummy Classifier como modelo base

- **Evaluación**:
  - `F1-score`, `ROC-AUC`, `Precision`, `Recall`, `Confusion Matrix`

---

## Exploración de Datos (EDA)

- Crecimiento constante de películas y reseñas entre 1987 y 2008.
- Distribución casi equilibrada entre reseñas positivas (≈23,600) y negativas (≈23,700).
- Alta presencia de calificaciones extremas (1 y 10), lo cual influye en la polaridad.
- El comportamiento de los datos permite un entrenamiento fiable sin aplicar técnicas de rebalanceo.

---

## Modelos Evaluados

| Modelo | Herramientas | Descripción | F1-score (Test) | ROC-AUC |
|--------|--------------|-------------|------------------|----------|
| **Modelo 0** | Dummy | Clasificador constante | Bajo | Bajo |
| **Modelo 1** | NLTK + TF-IDF + LR | Preciso para detectar críticas negativas | **0.88** | 0.95 |
| **Modelo 2** | spaCy + TF-IDF + LR | Balanceado, pero más conservador con lo positivo | 0.87 | 0.94 |
| **Modelo 3** | spaCy + TF-IDF + LGBM | Optimista con reseñas positivas, menos preciso en lo negativo | 0.84 | 0.93 |

---

## Recomendación Final

Para detectar **críticas negativas con alta precisión**, el modelo más recomendable es el **Modelo 1 (NLTK + TF-IDF + Regresión Logística)**.  
Si se busca un enfoque más balanceado para reseñas ambiguas, el Modelo 2 (spaCy + TF-IDF + LR) también es viable.

---


##  Estructura del Proyecto

- `notebook_sentiment_analysis.ipynb` - Notebook principal del análisis
- `requirements.txt` – Dependencias del proyecto 
- `README.md` – Descripción general del proyecto
- `imdb_reviews.tsv` - Datos fuente

Los datos fueron proporcionados por Andrew L. Maas, Raymond E. Daly, Peter T. Pham, Dan Huang, Andrew Y. Ng, y Christopher Potts. (2011). Learning Word Vectors for Sentiment Analysis. La Reunión Anual 49 de la Asociación de Lingüística Computacional (ACL 2011).

---

