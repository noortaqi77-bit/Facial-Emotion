# Facial Emotion Recognition (FER2013)

## 1. Overview
Classifies a face image into one of 7 emotions:
(angry, disgust, fear, happy, neutral, sad, surprise) class


## 2. Dataset
- Source: FER2013 (Kaggle: msambare/fer2013)
- Images: 48x48, grayscale
- train (24,403) , validation (4,306), test (7,178)
- The dataset is imbalanced: like : disgust = 436 images and happy = 7,215 images




## 4. Architecture Choices
Rescaling(1/255) → Flatten → BatchNormalization → Dense(100) → Dense(100) → Dense(73) → Dense(7, softmax)



### Observations:
- Best classes: happy and surprise (distinct expressions).
- Weakest classes: angry, fear, sad (similar expressions, often confused).
- Training accuracy rose while validation accuracy stayed flat and
  validation loss increased, which indicates overfitting.
- Dense layers flatten the image and lose spatial structure, so accuracy
  is limited to about 40-45%.
