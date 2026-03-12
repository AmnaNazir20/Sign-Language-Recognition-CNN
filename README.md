# Sign Language Recognition Using CNN and OpenCV

This repository contains the implementation of a **Convolutional Neural Network (CNN)** based system for recognizing **American Sign Language (ASL) alphabet gestures**.
The project is based on our research paper **“Sign Language Recognition Using CNN and OpenCV”**.

The system performs both **offline training and real-time gesture recognition** using a webcam.

---

# Authors

Amna Nazir


National University of Computer and Emerging Sciences (FAST), Pakistan

---

# Project Overview

Sign language recognition systems help reduce communication barriers between deaf individuals and the hearing population.
This project implements a **CNN-based model** that classifies ASL hand gestures into alphabet categories and deploys the model for **real-time recognition using OpenCV**.

The proposed system improves a baseline CNN by introducing:

* Batch Normalization
* L2 Regularization
* Dropout Layers
* Data Augmentation

These improvements increase model robustness and reduce overfitting.

---

# Dataset

The model is trained using the **ASL Alphabet Dataset**, which contains **29 gesture classes** representing:

* A – Z letters
* Space
* Delete
* Nothing

Dataset statistics:

* Total images: **~87,000 RGB images**
* Training set: **69,600 images**
* Validation set: **17,400 images**
* Test set: **28 images**

All images were resized to **64×64 pixels** before training. 

Dataset source:
https://www.kaggle.com/datasets/grassknoted/asl-alphabet

---

# Preprocessing

Before training, the following preprocessing steps were applied:

* Image resizing to **64×64**
* Pixel normalization to **[0,1]**
* Data augmentation techniques including:

  * Rotation (±20°)
  * Width and height shifts
  * Zoom variations
  * Shear transformations
  * Horizontal flipping

These techniques increase dataset diversity and improve model generalization. 

---

# Model Architecture

## Baseline CNN

The baseline model consists of:

* 3 Convolutional Layers
* MaxPooling layers
* Flatten layer
* Dense layer (128 neurons)
* Softmax output layer (29 classes)

Training parameters:

* Epochs: 10
* Batch size: 32
* Optimizer: Adam
* Loss: Categorical Crossentropy

Total parameters: **686,941**

---

## Improved CNN

The improved model enhances the baseline architecture with:

* 4 Convolutional Blocks
* Batch Normalization
* L2 Regularization
* Dropout Layers
* Dense layers: **256 → 128 → 29**

Training configuration:

* Epochs: up to 20
* EarlyStopping (patience = 5)
* ReduceLROnPlateau
* ModelCheckpoint

These techniques improve generalization and reduce overfitting. 

---

# Results

The improved CNN achieved better performance compared to the baseline model.

| Metric              | Baseline | Improved  |
| ------------------- | -------- | --------- |
| Training Accuracy   | 98.77%   | 93.31%    |
| Validation Accuracy | 85.9%    | 94.7%     |
| Parameters          | 686,941  | 1,671,485 |

The improved model demonstrated stronger generalization and stability during training.

---

# Real-Time Recognition

The trained model was integrated with **OpenCV** to perform real-time gesture recognition.

Workflow:

1. Capture webcam frame
2. Extract hand region (ROI)
3. Preprocess image
4. Predict ASL letter using CNN
5. Display prediction and confidence

The system shows high accuracy for several gestures such as **A, C, and M**, while some letters like **Y** are more challenging due to similar hand shapes. 

---

# Technologies Used

* Python
* TensorFlow / Keras
* OpenCV
* NumPy
* Matplotlib
* Scikit-learn

---

# Project Structure

```
Sign-Language-Recognition
│
├── Model Implementation.ipynb
├── trained_model.h5
├── dataset
├── README.md
```

---

# How to Run

Clone the repository:

```
git clone https://github.com/username/sign-language-recognition.git
```

Install dependencies:

```
pip install tensorflow opencv-python numpy matplotlib scikit-learn
```

Run the notebook:

```
Model Implementation.ipynb
```

---

# Future Work

Future improvements may include:

* Dynamic sign recognition
* LSTM or Transformer-based gesture models
* Larger datasets
* Improved real-time tracking

---

# References

See the research paper for detailed references and methodology.
