# Bone Fracture Detection using Deep Learning (ResNet50 + MURA Dataset)

## Overview

This project implements a deep learning based system for automatic bone fracture detection from X-ray images using Convolutional Neural Networks.
The model is trained on the MURA (Musculoskeletal Radiographs) dataset and uses a ResNet50 architecture to classify body parts and detect fractures.

The goal of the project is to explore how modern computer vision techniques can assist medical diagnosis by providing fast and reliable fracture detection from radiographic images.

The system performs two-stage prediction:

1. Predict the body part (Elbow / Hand / Shoulder)
2. Detect fracture for the predicted body part using a dedicated model

A graphical user interface (GUI) is provided to allow users to upload X-ray images and view predictions.

---

## Dataset

The project uses the MURA dataset, a large collection of musculoskeletal radiographs.

Total images used in this project: ~20,000

| Part     | Normal | Fractured | Total |
| -------- | ------ | --------- | ----- |
| Elbow    | 3160   | 2236      | 5396  |
| Hand     | 4330   | 1673      | 6003  |
| Shoulder | 4496   | 4440      | 8936  |

Each image belongs to a patient study folder, and the dataset is split into training, validation, and test sets.

Dataset structure:

Dataset/
├── train_valid/
├── test/
├── Elbow/
├── Hand/
├── Shoulder/

---

## Model Architecture

The system uses ResNet50 as the backbone CNN.

Pipeline:

1. Image preprocessing and augmentation
2. Body part classification using ResNet50
3. Load specific fracture detection model
4. Binary classification (fracture / normal)
5. Display result in GUI



Why ResNet50:

* strong performance on image classification
* deep residual connections
* good transfer learning support
* widely used in medical imaging

---

## Training Process

Steps:

* Load dataset
* Label images automatically from folder names
* Apply augmentation (flip, brightness, contrast)
* Split into train / validation / test
* Train body part classifier
* Train fracture detection models for each bone
* Save trained weights

Models saved in:

weights/
ResNet50_BodyParts.h5
ResNet50_Elbow_frac.h5
ResNet50_Hand_frac.h5
ResNet50_Shoulder_frac.h5

---

## Results

Body Part Classification Accuracy: ~92%

Fracture Detection Accuracy:

* Elbow ~90%
* Hand ~91%
* Shoulder ~92%



These results show that deep learning models can successfully detect bone fractures from X-ray images with high accuracy.

---

## GUI Application

The project includes a GUI built using CustomTkinter.

Features:

* Upload X-ray image
* Predict body part
* Detect fracture
* Show result
* Show confidence



Run GUI:

python mainGUI.py

---

## Installation

Requirements:

Python 3.7+

Install dependencies:

pip install -r requirements.txt

Libraries used:

tensorflow
keras
numpy
pandas
matplotlib
scikit-learn
opencv-python
customtkinter
pillow

---

## Future Improvements

* Improve accuracy using better fine-tuning
* Use larger input resolution
* Add more augmentation
* Add more bone types
* Improve GUI design
* Add web interface

---

## Motivation

This project was built to explore how deep learning can be applied to medical image classification and to understand the full pipeline from dataset processing to model training and GUI deployment.

The project demonstrates practical knowledge of:

* Computer Vision
* Deep Learning
* TensorFlow / Keras
* Medical datasets
* GUI development
* Model deployment

---

## Author

Krapansh Dubey 