# 🚗 Car Brand Classification (ESP32-CAM)

A lightweight **Car Brand Classification** project that identifies **Mercedes-Benz, Porsche, and MINI** cars using an **Edge-optimized MobileNetV2** model deployed on an **ESP32-CAM** board.

This project demonstrates the full workflow from dataset preprocessing and model training to deployment as an **Arduino library** for embedded real-time inference.

---

## 📸 Overview

| ![ESP32-CAM](https://upload.wikimedia.org/wikipedia/commons/7/7e/ESP32-CAM.jpg) | ![Cars](https://upload.wikimedia.org/wikipedia/commons/0/03/Mercedes-Benz_C-Class_%28W205%29.jpg) |
|:--:|:--:|
| *ESP32-CAM device used for real-time classification* | *Target brands: Mercedes-Benz, Porsche, MINI* |

---

## 🧠 Dataset

- **Source:** [Ahmed ElSany – Car Brand Classification Dataset (Kaggle)](https://www.kaggle.com/datasets/ahmedelsayed268/car-brand-classification)
- **Classes:** `Mercedes-Benz`, `Porsche`, `MINI`
- **Format:** Image dataset with labeled folders
- **Usage:** Preprocessed and split for training and validation in Jupyter

---

## ⚙️ Tech Stack

| Component | Technology |
|------------|-------------|
| Dataset | Kaggle – Ahmed ElSany’s Car Brand Dataset |
| Model Architecture | MobileNetV2 |
| Framework | TensorFlow / Keras |
| Conversion | TensorFlow Lite (TFLite) |
| Edge Deployment | [Edge Impulse](https://edgeimpulse.com) |
| Hardware | ESP32-CAM (Arduino) |
| IDE | Jupyter Notebook, Arduino IDE |

---

## 🧩 Project Workflow

1. **Import Dependencies & Dataset**
   - Download Kaggle dataset and unzip to project folder.
   - Import using TensorFlow and OpenCV.

2. **Preprocessing**
   - Resize all images to `96x96`.
   - Normalize pixel values to `[0, 1]`.
   - Split dataset: 80% training, 20% validation.

3. **Model Definition**
   - Base model: `MobileNetV2` pretrained on ImageNet.
   - Custom classifier layers for 3 car brands.
   - Optimizer: `Adam`, learning rate scheduler via cosine decay.

4. **Training**
   - Fine-tuning last layers.
   - Data augmentation (rotation, flipping).
   - Evaluate and export accuracy and confusion matrix.

5. **Model Conversion**
   - Convert the trained `.h5` model → `.tflite`.
   - Apply **INT8 quantization** for microcontroller compatibility.

6. **Deployment**
   - Upload `.tflite` model to **Edge Impulse**.
   - Deploy as **Arduino Library**.
   - Download and extract `.zip` file.

7. **ESP32-CAM Inference**
   - Load library in Arduino IDE.
   - Open `CarClassification-3-Classes.ino`.
   - Flash firmware to ESP32-CAM.
   - Observe classification results over serial monitor or web stream.

---

## 🧪 Example Output

| Input Image | Predicted Label |
|--------------|----------------|
| ![Mercedes](https://upload.wikimedia.org/wikipedia/commons/f/f9/Mercedes-Benz_logo_2010.svg) | Mercedes-Benz |
| ![Porsche](https://upload.wikimedia.org/wikipedia/commons/2/2e/Porsche_logo.svg) | Porsche |
| ![MINI](https://upload.wikimedia.org/wikipedia/commons/4/4d/MINI_logo_2018.svg) | MINI |

---

## 📂 Repository Structure

