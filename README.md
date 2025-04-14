# 🐾 Image Classification - Animals10 Dataset
Proyek ini merupakan bagian dari submission pada pembelajaran klasifikasi gambar menggunakan TensorFlow. Dataset yang digunakan adalah **Animals10** dari Kaggle dan model yang digunakan adalah kombinasi dari **EfficientNetV2S** dan **CNN custom**.

<img src="https://img.shields.io/badge/TensorFlow-2.18-orange.svg" />
<img src="https://img.shields.io/badge/Keras-3.0-blue.svg" />
<img src="https://img.shields.io/badge/Dataset-Kaggle_Animals10-green.svg" />

---

## 📦 Dataset
Dataset diambil dari Kaggle: [Animals10 Dataset](https://www.kaggle.com/datasets/alessiocorrado99/animals10)

- Terdiri dari 10 kelas hewan: Anjing, Kucing, Kuda, Laba-laba, Kupu-kupu, Ayam, Sapi, Gajah, Domba, dan Tupai.
- Setiap kelas dibatasi hingga **1400 gambar** (balanced).
- Total: **14,000 gambar**.
- Ukuran input gambar: `(224x224)` RGB.

### 📊 Distribusi Dataset

| Hewan       | Jumlah Gambar |
|-------------|----------------|
| Anjing      | 1400           |
| Ayam        | 1400           |
| Domba       | 1400           |
| Gajah       | 1400           |
| Kucing      | 1400           |
| Kuda        | 1400           |
| Kupu-kupu   | 1400           |
| Laba-laba   | 1400           |
| Sapi        | 1400           |
| Tupai       | 1400           |

---

## 🧠 Arsitektur Model

### ✅ Model 1: EfficientNetV2S
- Pre-trained: `imagenet`
- `GlobalAveragePooling2D`
- `BatchNormalization`
- `Dense(256, relu)`
- `Dropout(0.3)`
- `Dense(10, softmax)`

### ✅ Model 2: CNN Custom (untuk klasifikasi biner)
- 3 Blok Conv2D + MaxPool + BatchNormalization
- Flatten → Dense(128) → Dropout → Dense(64) → Dropout
- Output layer: `Dense(1, sigmoid)`

---

## 📈 Hasil Training (EfficientNetV2S)

| Epoch | Acc Train | Acc Val | F1 Score | Loss Val |
|-------|-----------|---------|----------|----------|
| 1     | 0.96      | 0.96    | 0.96     | 0.55     |
| 6     | **0.98**  | **0.96**| **0.98** | **0.52** |

> Model terbaik dicapai pada epoch ke-6

---

## 📊 Evaluasi Model

- **Accuracy Test**: 97.11%
- **Classification Report**: macro avg F1-Score: 0.9711
- **Visualisasi**: Confusion matrix & misclassified images ditampilkan.
- Model disimpan dalam format `.h5` dan bisa dikonversi ke TFJS atau TFLite.

---

## 🧪 Visualisasi Training

<img src="https://raw.githubusercontent.com/yourusername/yourrepo/main/images/metrics.png" width="700">

---

## 🚀 Cara Menjalankan
1. Install library:
    ```bash
    pip install tensorflow tensorflow-hub kaggle
    ```
2. Download dataset:
    - Upload `kaggle.json`
    - Jalankan:
      ```python
      !kaggle datasets download -d alessiocorrado99/animals10 --unzip
      ```
3. Jalankan semua cell di `notebook.ipynb` (bisa di Google Colab).
4. Model otomatis tersimpan sebagai `best_model.h5`.

---

## 🎯 Highlight Fitur
- Augmentasi data dengan `ImageDataGenerator`.
- EarlyStopping + ReduceLROnPlateau + ModelCheckpoint.
- Evaluasi dengan confusion matrix dan classification report.
- Implementasi dua jenis arsitektur CNN.
- Visualisasi metrik akurasi, loss, dan f1-score.

---

## 📂 Struktur Direktori
