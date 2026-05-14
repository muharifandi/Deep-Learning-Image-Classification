# README.md

## Proyek Klasifikasi Gambar

# Intel Image Classification dengan Deep Learning CNN

---

## Identitas

* **Nama:** Muh. Arifandi
* **Email:** [arif76440@gmail.com](mailto:arif76440@gmail.com)
* **ID Dicoding:** arif76440

---

# Deskripsi Proyek

Perkembangan teknologi Deep Learning memungkinkan komputer melakukan pengenalan objek visual dengan tingkat akurasi yang tinggi. Salah satu implementasi paling populer pada bidang Computer Vision adalah klasifikasi gambar menggunakan Convolutional Neural Network (CNN).

Pada proyek ini dikembangkan model klasifikasi gambar berbasis Deep Learning menggunakan pendekatan Transfer Learning dengan arsitektur MobileNetV2. Model digunakan untuk mengklasifikasikan gambar pemandangan alam berdasarkan Intel Image Classification Dataset.

Model yang dibangun mampu mengidentifikasi lima kategori gambar, yaitu:

* forest
* glacier
* mountain
* sea
* street

Selain melakukan proses training model, proyek ini juga mencakup proses preprocessing data, augmentasi gambar, evaluasi model, visualisasi hasil training, inference gambar baru, serta konversi model ke beberapa format deployment seperti:

* SavedModel
* TensorFlow Lite
* TensorFlow.js

---

# Latar Belakang

Klasifikasi gambar merupakan salah satu permasalahan penting dalam bidang Artificial Intelligence dan Computer Vision. Kemampuan komputer dalam mengenali objek visual dapat diterapkan pada berbagai bidang seperti:

* sistem keamanan,
* kendaraan otonom,
* smart city,
* monitoring lingkungan,
* dan aplikasi mobile berbasis AI.

Dataset Intel Image Classification dipilih karena memiliki:

* jumlah gambar yang besar,
* variasi visual yang beragam,
* serta ukuran gambar asli yang tidak seragam.

Kondisi tersebut membuat dataset cocok digunakan sebagai studi kasus klasifikasi gambar pada kondisi nyata.

---

# Business Understanding

## Problem Statement

Permasalahan yang ingin diselesaikan pada proyek ini adalah:

1. Bagaimana membangun model CNN untuk melakukan klasifikasi gambar pemandangan alam?

2. Bagaimana meningkatkan kemampuan generalisasi model terhadap gambar baru?

3. Bagaimana mengonversi model agar dapat digunakan pada berbagai platform deployment?

---

## Goals

Tujuan proyek ini adalah:

* Membangun model klasifikasi gambar berbasis CNN.
* Mencapai akurasi model di atas 85%.
* Mengimplementasikan preprocessing dan data augmentation.
* Menghasilkan model yang dapat digunakan pada berbagai platform deployment.
* Melakukan inference terhadap gambar baru menggunakan model yang telah dibuat.

---

## Solution Statement

Solusi yang diterapkan pada proyek ini meliputi:

* Menggunakan Transfer Learning MobileNetV2.
* Menggunakan arsitektur Sequential.
* Mengimplementasikan data augmentation.
* Menggunakan callback untuk meningkatkan stabilitas training.
* Menggunakan GlobalAveragePooling2D agar model lebih ringan.
* Mengonversi model ke format SavedModel, TensorFlow Lite, dan TensorFlow.js.

---

# Dataset

Dataset yang digunakan:

## Intel Image Classification Dataset

Dataset diperoleh dari Kaggle:

Dataset URL:
[https://www.kaggle.com/datasets/puneet6060/intel-image-classification](https://www.kaggle.com/datasets/puneet6060/intel-image-classification)

---

# Jumlah Kelas yang Digunakan

Pada proyek ini digunakan 5 kelas:

| Kelas    | Jumlah Gambar |
| -------- | ------------- |
| forest   | 2271          |
| glacier  | 2404          |
| mountain | 2512          |
| sea      | 2274          |
| street   | 2382          |

Total dataset yang digunakan sekitar 11.843 gambar.

---

# Tahapan Proyek

## 1. Import Library

Library utama yang digunakan:

* TensorFlow
* NumPy
* Matplotlib
* Seaborn
* TensorFlowJS
* Scikit-Learn

---

## 2. Data Preparation

Tahapan data preparation meliputi:

* Upload Kaggle API
* Download dataset
* Extract dataset
* Memilih 5 kelas dataset
* Menentukan direktori dataset

---

## 3. Data Understanding

Dilakukan analisis dataset untuk memahami:

* jumlah gambar,
* distribusi kelas,
* dan karakteristik visual dataset.

---

# Visualisasi Distribusi Dataset

Visualisasi distribusi dataset menunjukkan bahwa jumlah gambar pada setiap kelas relatif seimbang.

Kondisi ini membantu model melakukan proses pembelajaran secara lebih stabil karena tidak terdapat perbedaan jumlah data yang terlalu signifikan antar kelas.

Kelas mountain memiliki jumlah gambar terbanyak, sedangkan kelas forest dan sea memiliki jumlah gambar yang hampir sama.

---

# Visualisasi Sample Gambar

Visualisasi sample gambar menunjukkan bahwa setiap kelas memiliki karakteristik visual yang berbeda.

* Kelas forest didominasi pepohonan dan warna hijau.
* Kelas glacier memiliki area bersalju.
* Kelas mountain memiliki kontur pegunungan.
* Kelas sea memiliki dominasi area air.
* Kelas street menampilkan lingkungan perkotaan.

Perbedaan pola visual ini membantu model mempelajari fitur unik dari masing-masing kategori.

---

# Data Preprocessing

Tahapan preprocessing meliputi:

* Resize gambar menjadi 128x128 pixel.
* Split dataset menjadi training, validation, dan testing.
* Data augmentation.
* Prefetch dataset untuk optimasi training.

---

# Data Augmentation

Teknik augmentasi yang digunakan:

* RandomFlip
* RandomRotation
* RandomZoom

Augmentasi diterapkan hanya pada training set agar model memiliki kemampuan generalisasi yang lebih baik.

---

# Arsitektur Model

Model dibangun menggunakan pendekatan Transfer Learning dengan MobileNetV2 sebagai feature extractor.

Arsitektur model:

* Input Layer
* Preprocessing Layer
* MobileNetV2
* GlobalAveragePooling2D
* Dense Layer
* Dropout
* Output Layer Softmax

---

# Penjelasan Arsitektur

## MobileNetV2

MobileNetV2 digunakan karena:

* ringan,
* cepat,
* efisien,
* dan cocok untuk deployment mobile.

Model ini telah dilatih sebelumnya menggunakan ImageNet sehingga mampu mengekstraksi fitur visual dengan baik.

---

## GlobalAveragePooling2D

Layer ini digunakan untuk:

* mengurangi jumlah parameter,
* mempercepat training,
* serta membuat model lebih ringan.

---

## Dense Layer

Dense layer digunakan untuk mempelajari pola fitur yang lebih kompleks sebelum proses klasifikasi akhir dilakukan.

---

# Callback

Callback yang digunakan:

## EarlyStopping

Menghentikan training secara otomatis ketika model tidak mengalami peningkatan performa.

---

## ReduceLROnPlateau

Mengurangi learning rate ketika performa model stagnan.

---

## ModelCheckpoint

Menyimpan model terbaik selama proses training.

---

# Hasil Training

Model berhasil mencapai performa yang baik selama proses training.

## Hasil Evaluasi

| Metric         | Hasil  |
| -------------- | ------ |
| Train Accuracy | 95.40% |
| Test Accuracy  | 91.55% |

---

# Analisis Hasil Training

Hasil training menunjukkan bahwa akurasi training dan validation mengalami peningkatan secara konsisten pada setiap epoch.

Validation accuracy berhasil mencapai lebih dari 92%, menunjukkan bahwa model mampu melakukan generalisasi dengan cukup baik terhadap data baru.

Nilai loss juga mengalami penurunan yang stabil sehingga proses pembelajaran model berjalan optimal.

---

# Visualisasi Accuracy

Grafik accuracy menunjukkan bahwa performa model meningkat secara bertahap selama proses training.

Kurva training dan validation accuracy memiliki pola yang relatif berdekatan sehingga model tidak mengalami overfitting yang signifikan.

Hal ini menunjukkan bahwa data augmentation dan callback berhasil membantu model melakukan generalisasi dengan baik.

---

# Visualisasi Loss

Grafik loss menunjukkan penurunan nilai loss pada data training maupun validation.

Penurunan loss yang stabil menunjukkan bahwa model berhasil mempelajari pola data dengan baik.

Tidak terdapat lonjakan validation loss yang ekstrem sehingga model masih tergolong stabil selama proses training.

---

# Confusion Matrix

Confusion matrix menunjukkan bahwa sebagian besar gambar berhasil diklasifikasikan dengan benar.

Kelas forest dan street memiliki tingkat prediksi yang sangat baik dengan jumlah kesalahan yang sangat kecil.

Beberapa kesalahan prediksi masih terjadi antara kelas glacier dan mountain karena kedua kelas memiliki karakteristik visual yang cukup mirip pada beberapa gambar.

---

# Classification Report

Model memperoleh precision, recall, dan f1-score yang tinggi pada sebagian besar kelas.

Kelas street memiliki performa terbaik dengan nilai hampir sempurna, sedangkan kelas glacier dan mountain memiliki performa sedikit lebih rendah karena kemiripan fitur visual antar kelas.

Weighted average sebesar 92% menunjukkan bahwa model memiliki performa klasifikasi yang baik secara keseluruhan.

---

# Inference Model

Model berhasil melakukan prediksi terhadap gambar baru dengan confidence yang tinggi.

Hasil inference menunjukkan bahwa model mampu mengenali objek gambar sesuai kategori yang benar.

---

# Deployment Model

Model berhasil dikonversi ke beberapa format deployment:

## SavedModel

Digunakan untuk deployment TensorFlow production.

---

## TensorFlow Lite

Digunakan untuk deployment pada perangkat mobile dan edge device.

---

## TensorFlow.js

Digunakan untuk deployment pada browser berbasis JavaScript.

---

# Struktur Submission

```text
submission/
│
├── saved_model/
│
├── tfjs_model/
│
├── tflite/
│   ├── model.tflite
│   └── label.txt
│
├── notebook.ipynb
├── notebook.py
├── README.md
└── requirements.txt
```

---

# Cara Menjalankan Proyek

## 1. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 2. Jalankan Notebook

Buka notebook:

```text
notebook.ipynb
```

Lalu jalankan seluruh cell secara berurutan.

---

# Requirements

Library utama:

* tensorflow
* tensorflowjs
* numpy
* matplotlib
* seaborn
* scikit-learn

---

# Kesimpulan

Pada proyek ini berhasil dibangun model klasifikasi gambar menggunakan pendekatan Deep Learning berbasis Convolutional Neural Network (CNN) dengan metode Transfer Learning menggunakan arsitektur MobileNetV2.

Dataset yang digunakan terdiri dari lima kategori:

* forest
* glacier
* mountain
* sea
* street

Tahapan preprocessing dilakukan menggunakan resize gambar, split dataset, serta data augmentation untuk meningkatkan kemampuan generalisasi model.

Model berhasil mencapai:

* training accuracy sebesar 95.40%
* testing accuracy sebesar 91.55%

Hasil evaluasi menunjukkan bahwa model mampu melakukan klasifikasi gambar dengan performa yang baik dan stabil.

Selain itu, model berhasil dikonversi ke:

* SavedModel
* TensorFlow Lite
* TensorFlow.js

sehingga dapat digunakan pada berbagai platform deployment seperti cloud, mobile, maupun browser.

Berdasarkan seluruh hasil evaluasi, model yang dibangun telah memenuhi seluruh kriteria submission dan mampu melakukan klasifikasi gambar secara akurat dan efisien.
