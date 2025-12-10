# 📘 Proyecto Final – IA / Machine Learning  

## 📄 Descripción del Proyecto

Este proyecto implementa **tres arquitecturas de Deep Learning** —MLP, CNN y RNN aplicadas a problemas reales utilizando datasets de Kaggle.

Los tipos de datos utilizados para las 3 arquitecturas fueron:

1. **Datos tabulares** (calidad de vino)  
2. **Imágenes** (enfermedades en plantas)  
3. **Secuencias musicales** (predicción y generación de notas MIDI)

Cada notebook incluye:

- Exploración de datos
- Preprocesamiento  
- Entrenamiento en TensorFlow/Keras (PyTorch para la primer arquitectura) 
- Visualización de curvas de aprendizaje  
- Métricas de evaluación  
- Análisis de resultados  
- Generación de ejemplos

---

## 📊 Datasets Utilizados

### 🟥 1. Wine Reviews – Clasificación de calidad del vino  
**Dataset:** https://www.kaggle.com/datasets/zynicide/wine-reviews  

Dataset con más de 100k reseñas de vinos, incluyendo atributos como país, variedad, precio y el puntaje `points`.  

Para este proyecto se transforma el puntaje en **3 clases de calidad**:

- **0** → 80–86 puntos  
- **1** → 87–90 puntos  
- **2** → 91+ puntos  

Usado para entrenar un **MLP**.

---

### 🌿 2. Plant Disease Dataset – Clasificación de enfermedades en plantas  
**Dataset:** https://www.kaggle.com/datasets/dittakavinikhita/plant-disease-prediction-disease-and-healthy  

Dataset con imágenes de hojas sanas y con enfermedades, organizadas en subdirectorios.  
Se utiliza para entrenar una **CNN** con técnicas de Data Augmentation.

---

### 🎵 3. MIDI Melodies – Secuencias de notas musicales  
**Dataset:** https://www.kaggle.com/datasets/zakarii/lofi-hip-hop-midi

El dataset incluye melodías en formato MIDI, desde las cuales se extraen secuencias de **pitches**.  
La tarea consiste en predecir la **siguiente nota** y generar melodías nuevas.  

Usado para entrenar una **RNN**.

---

# 🤖 Modelos Implementados

## 🧠 Modelo 1: MLP – Clasificación de Vino  
Framework: PyTorch

### Arquitectura:
- Dense(128, ReLU) + Dropout 0.3  
- Dense(64, ReLU) + Dropout 0.3  
- Dense(3, Softmax)  

### Objetivo:
Clasificar la calidad del vino usando atributos tabulares.

---

## 🌱 Modelo 2: CNN – Enfermedades en Hojas de Plantas  
Framework: TensorFlow/Keras  

### Arquitectura:
- Data Augmentation  
- Conv2D(32) + MaxPool  
- Conv2D(64) + MaxPool  
- Conv2D(128) + MaxPool  
- Conv2D(256) + MaxPool  
- Dense(256, ReLU) + Dropout 0.5  
- Dense(num_classes, Softmax)

### Objetivo:
Clasificar imágenes de hojas como **sanas** o **enfermas**.

---

## 🎼 Modelo 3: RNN – Generación Musical  
Framework: TensorFlow/Keras  

### Flujo:
1. Visitar archivos MIDI  
2. Extraer secuencias de notas (pitches)  
3. Crear pares `(secuencia → siguiente nota)`  
4. Entrenar un modelo RNN

### Arquitectura:
- Embedding(vocab_size, 128)  
- RNN(256, return_sequences=True)  
- RNN(256)  
- Dense(vocab_size, Softmax)

### Objetivo:
Predecir la siguiente nota y generar melodías desde semillas iniciales.

---

# 📈 Resultados Principales  

## 🧠 MLP – Calidad del vino
| Métrica | Resultado |
|--------|-----------|
| Test Accuracy | **0.6153** |
| Observaciones | Mejores resultados en clases 1 y 2 |

---

## 🌿 CNN – Enfermedades en plantas
| Métrica | Resultado |
|--------|-----------|
| Test Accuracy | **0.9712** |
| Observaciones | Data augmentation mejora la generalización |

---

## 🎵 RNN – Generación musical
| Métrica | Resultado |
|--------|-----------|
| Test Accuracy | **0.0833** |
| Observaciones | La red aprende intervalos locales y estructuras repetitivas |

---

# 🧠 Conclusiones y Aprendizajes
- Cada arquitectura de Deep Learning tiene un dominio donde destaca:
    - MLP → datos tabulares
    - CNN → imágenes
    - RNN → secuencias
- El proyecto permitió:
    - Aplicar preprocesamiento especializado para cada tipo de dato
    - Construir modelos completos usando TensorFlow/Keras y PyTorch
    - Evaluar con métricas cuantitativas (accuracy, loss, F1-score)
    - Explorar resultados cualitativos (imágenes, melodías MIDI)
    - Comprender cómo la arquitectura influye directamente en el desempeño
- Se observó que:
    - Las CNN logran los mejores resultados en generalización.
    - Las RNN requieren un dataset grande para generar melodías coherentes.
    - Los MLP funcionan bien con datos correctamente normalizados y codificados.