# Facial Emotion Recognition (FER2013)

## Overview
Classifies a face image into one of 7 emotions:

(angry, disgust, fear, happy, neutral, sad, surprise) class


## Dataset
- Source: FER2013 (Kaggle: msambare/fer2013)
- Images: 48x48, grayscale
- train (24,403) , validation (4,306), test (7,178)
- The dataset is imbalanced: like : disgust = 436 images and happy = 7,215 images

## Preprocessing
- **Resize:** all images are 48x48
- **Color:** converted to grayscale , 1 channel
- **Normalize:** pixel values divided by 255 so they are between 0 and 1
 also,  (`Rescaling(1./255)` is the first layer of the model).
- **Split:** the original train folder is split into Train 85% for 24,403 images
  and Validation 15% with 4,306 images
  The original test folder is 7,178 images, is kept untouched for final evaluation to see the performance.
- **Labels:** using label_mode="categorical"
- **Class imbalance:** handled with class_weight (balanced) during training.



## Architecture Choices
- architecture : Rescaling(1/255) → Flatten → BatchNormalization → Dense(200, ReLU) → Dense(100, ReLU) → Dense(80, ReLU) → Dense(50, ReLU) → Dense(7, Softmax)
- Loss: categorical_crossentropy
- Optimizer: Adam , with learning rate= 0.001
- 

## Evaluation

The model was evaluated using test accuracy, precision, recall, F1-score, loss, and a confusion matrix.

## Results
- Baseline test accuracy is 39%.
- Improved test accuracy is 40%.
- Recall of disgust improved from 0.40 to 0.44 to class weights.
- Best classes is happy and surprise.
- Weakest classes is fear, angry and disgust because their expressions look similar.
- Accuracy is limited to about 40 to 45% because Dense layers flatten the image and lose the position of facial features.



  ### Application

A Gradio interface allows users to upload a facial image or capture one using a webcam. The application displays the predicted expression and class probabilities.
link= (https://0104397f26a9234c06.gradio.live/)


### Ethics & Limitations
- Class imbalance may affect recognition of some emotions.
- The model achieved 40% test accuracy, so predictions may be incorrect.
- Lighting, image quality, and face angles and shapes may affect predictions.
- The model may perform differently on real-world images.

