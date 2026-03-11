# Bone Fracture Detection using Deep Learning (ResNet50 + MURA Dataset)

## Overview

This project implements a deep learning based system for detecting bone fractures from X-ray images using Convolutional Neural Networks.
The model is trained on the MURA (Musculoskeletal Radiographs) dataset and uses a ResNet50 architecture for image classification.

The goal of this project is to understand the full pipeline of a medical image classification system, including dataset processing, model training, fracture detection, and GUI-based prediction.

The system performs two-stage prediction:

1. Detect body part (Elbow / Hand / Shoulder)
2. Detect fracture using a model trained specifically for that bone

A graphical user interface (GUI) is included to allow testing predictions on X-ray images.

This repository contains my reproduction and experimentation with this fracture detection pipeline.

---

## Dataset

The project uses the MURA dataset, a large dataset of musculoskeletal radiographs.

Total images used in this project: ~20,000

| Part     | Normal | Fractured | Total |
| -------- | ------ | --------- | ----- |
| Elbow    | 3160   | 2236      | 5396  |
| Hand     | 4330   | 1673      | 6003  |
| Shoulder | 4496   | 4440      | 8936  |

Dataset structure:

Dataset/
├── train_valid/
├── test/
├── Elbow/
├── Hand/
├── Shoulder/

Each image belongs to a patient study folder.

---

## Model Architecture

The project uses ResNet50 as the backbone CNN.

Pipeline:

1. Image preprocessing and augmentation
2. Body part classification using ResNet50
3. Load fracture detection model for that body part
4. Binary classification (fracture / normal)
5. Display result in GUI

This two-stage approach improves performance by using a specialized model for each bone type.

Why ResNet50:

* Strong performance for image classification
* Supports transfer learning
* Good for medical imaging tasks
* Stable training behavior

---

## Training Pipeline

Training scripts included:

training_parts.py
training_fracture.py

Steps:

* Load images from dataset folders
* Assign labels automatically
* Apply augmentation
* Train body part classifier
* Train fracture classifier for each bone
* Save trained weights

Weights stored in:

weights/

ResNet50_BodyParts.h5
ResNet50_Elbow_frac.h5
ResNet50_Hand_frac.h5
ResNet50_Shoulder_frac.h5

---

## Results

During experiments, the model achieved around 90–92% accuracy depending on bone type.

Performance varies due to dataset size and hardware limitations.

These results demonstrate that deep learning models can successfully learn fracture patterns from X-ray images.

---

## GUI Application

GUI built using CustomTkinter.

Features:

* Upload X-ray image
* Predict body part
* Detect fracture
* Show result
* Display confidence

Run GUI:

python mainGUI.py

---

## Installation

Python 3.7  recommended, to be compatible with TensorFlow 2.6

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

## Purpose of this Project

This project was used to study and reproduce a deep learning based fracture detection system and to understand:

* Medical image classification
* Transfer learning with ResNet50
* Dataset preprocessing
* Model training
* GUI integration
* Prediction pipeline

Future work may include:

* Better training pipeline
* Higher accuracy models
* Improved GUI
* Web interface
* More bone types

---

## Author
Krapansh Dubey

This repository contains my experimentation and study of fracture detection using deep learning and the MURA dataset.
