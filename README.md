# Trash-Scan ♻️📸

**Trash-Scan** is a computer vision application built in Python and Google Colab that classifies common recyclable waste items using a deep learning model. By leveraging transfer learning, the application identifies waste types from uploaded images or live webcam streams and provides actionable disposal instructions to encourage proper segregation.

---

## 🚀 Features

* **4-Class Waste Classification**: Accurately classifies:
  * 🥤 Soda Cans
  * 📦 Cardboard
  * 🍾 Glass Bottles
  * 🧴 Plastic Bottles
* **Transfer Learning**: Built on top of **MobileNetV2** pre-trained on ImageNet for high accuracy and fast inference.
* **Dual Input Modes**:
  * **Image Upload**: Upload `.jpg` or `.png` files directly.
  * **Live Webcam Capture**: Integrated JavaScript camera control within Google Colab for real-time scanning.
* **Actionable Disposal Guidance**: Outputs specific waste management instructions alongside prediction confidence scores to encourage proper recycling habits.

---

## 🛠️ Built With

* **Python 3**
* **TensorFlow / Keras**: Neural network design, data augmentation, and training.
* **MobileNetV2**: Base backbone for transfer learning.
* **ipywidgets**: Interactive GUI setup in Google Colab.
* **Pillow (PIL) & Matplotlib**: Image processing and result visualization.
* **JavaScript**: Browser API camera integration for webcam functionality.

---

## 📂 Project Structure

```text
├── models/
│   └── waste_classifier_model.h5   # Trained Keras model
├── Trash_Scan.ipynb                 # Google Colab notebook containing training & UI logic
└── README.md                        # Project documentation
```

---

## ⚙️ Model Architecture & Training

1. **Base Model**: `MobileNetV2` with frozen weights (`include_top=False`, input shape `180x180x3`).
2. **Top Layers**:
   * `GlobalAveragePooling2D`
   * `Dropout(0.2)`
   * `Dense(128, activation='relu')`
   * `Dense(4, activation='softmax')`
3. **Data Augmentation**: Applied rotation, horizontal flipping, and spatial shifts via `ImageDataGenerator` to improve model generalization on small datasets.
4. **Loss & Optimizer**: `Adam` optimizer with `sparse_categorical_crossentropy`.

---

## 🖥️ How to Run in Google Colab

1. **Clone or Download**: Upload `Trash_Scan.ipynb` to your Google Drive or open it directly in Google Colab.
2. **Setup Dataset Directory**:
   Organize your dataset in Google Drive under the following directory structure:
   ```text
   cs124p project/
   ├── Soda Can/
   ├── Cardboard/
   ├── Plastic Bottle/
   └── Glass Bottle/
   ```
3. **Mount Google Drive & Run Notebook**:
   * Run the initial cell to mount Drive.
   * Run the training code cell to generate `waste_classifier_model.h5` (or use a pre-existing trained model file).
   * Execute the interactive UI cell to launch the `ipywidgets` interface.

---

## 💡 Usage

Once the UI cell is running:

1. **To Upload an Image**: Click **Upload**, pick a photo of a waste item, and view the predicted class along with recycling instructions.
2. **To Use the Webcam**:
   * Click **Scan with Webcam**.
   * Grant browser camera permissions.
   * Point your item at the screen and click **Scan Trash**.
3. **Review Output**: Check the classification name, confidence percentage, and the printed disposal instructions.

---

## 📋 Sample Disposal Instructions Output

| Class | Output Instruction |
| :--- | :--- |
| **Soda Can** | *"Empty any remaining liquid, crush the can to save space, and place it in the Recyclables bin."* |
| **Cardboard** | *"Flatten completely and ensure it is dry and free of food waste. Place in the Recyclables bin."* |
| **Plastic Bottle** | *"Empty all liquid, remove the cap, crush the bottle, and dispose of it in the Recyclables bin."* |
| **Glass Bottle** | *"Empty the contents and handle with care. Do not crush or break. Place gently in the Recyclables or designated Glass bin."* |

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](../../issues).
