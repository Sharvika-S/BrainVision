

# 🧠 Brain Tumor Classification using CNN and Grad-CAM

This project focuses on classifying brain MRI images into tumor types using a **custom Convolutional Neural Network (CNN)** and visualizing model interpretability using **Grad-CAM (Gradient-weighted Class Activation Mapping)**.

---

## 🔍 Overview

* **Objective**: Automatically classify brain MRI images into four categories: `glioma`, `meningioma`, `pituitary`, and `notumor`.
* **Model Architecture**: A custom CNN built from scratch using Keras with Conv2D, MaxPooling, Dense, and Dropout layers.
* **Explainability**: The Grad-CAM technique is used to highlight regions in the MRI scans that influenced the model’s prediction.

---

## 📂 Dataset

The dataset is organized into four classes:

* `glioma`
* `meningioma`
* `pituitary`
* `notumor`

Each class is split into:

* `Training/`
* `Testing/`

> The dataset is provided as a ZIP file and extracted at runtime from Google Drive.

---

## 🧠 CNN Model Architecture

```python
model = Sequential([
    Conv2D(32, (3,3), activation='relu', input_shape=(224, 224, 3)),
    MaxPooling2D(pool_size=(2,2)),
    Conv2D(64, (3,3), activation='relu'),
    MaxPooling2D(pool_size=(2,2)),
    Flatten(),
    Dense(128, activation='relu'),
    Dropout(0.5),
    Dense(4, activation='softmax')  # 4 output classes
])
```

* **Optimizer**: Adam
* **Loss Function**: Categorical Crossentropy
* **Metrics**: Accuracy

---

## 📊 Evaluation Metrics

Model performance is assessed using:

* Accuracy
* Precision
* Recall
* F1 Score
* AUC (Area Under Curve)

These are summarized and compared in a results table at the end of training.

---

## 🔍 Grad-CAM Visualizations

Grad-CAM is used to visualize which parts of the input image influenced the CNN's classification decision.

### Example Output:

```python
# Heatmap for interpretability
heatmap = make_gradcam_heatmap(img_array, model, last_conv_layer_name="conv2d_1")

# Display the Grad-CAM heatmap
plt.matshow(heatmap)
plt.title("Grad-CAM Heatmap")
```

This helps in understanding **why** the model predicted a certain tumor type by highlighting important regions in the MRI image.

---

## 📁 Folder Structure

```
├── brain_tumor_cnn_gradcam.ipynb
├── README.md
├── gradcam_outputs/
│   └── heatmap_examples/
└── models/
    └── cnn_model.h5
```

---

## ✅ Conclusion

* A lightweight **custom CNN** can perform well on brain MRI classification tasks with proper training.
* **Grad-CAM** adds a layer of interpretability, which is crucial in medical applications.
* The system provides accurate predictions along with **visual reasoning**, making it a reliable tool for clinical support.

