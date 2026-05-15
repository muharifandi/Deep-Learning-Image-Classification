# Proyek Klasifikasi Gambar

# Intel Image Classification Menggunakan Deep Learning CNN

---

# Identitas

- Nama: Muh. Arifandi
- Email: arif76440@gmail.com
- ID Dicoding: arif76440

---

# Deskripsi Proyek

Perkembangan teknologi Deep Learning memungkinkan komputer melakukan pengenalan objek visual dengan tingkat akurasi yang tinggi. Salah satu implementasi paling populer pada bidang Computer Vision adalah klasifikasi gambar menggunakan Convolutional Neural Network (CNN).

Pada proyek ini dikembangkan model klasifikasi gambar berbasis Deep Learning menggunakan arsitektur Convolutional Neural Network (CNN) berbasis Sequential.

Model dibangun menggunakan beberapa layer Conv2D dan MaxPooling2D untuk melakukan ekstraksi fitur visual pada gambar.

Model digunakan untuk mengklasifikasikan gambar pemandangan alam berdasarkan Intel Image Classification Dataset.

Kategori gambar yang digunakan terdiri dari:

- forest
- glacier
- mountain
- sea
- street

Selain melakukan proses training model, proyek ini juga mencakup proses:

- preprocessing data,
- augmentasi gambar,
- evaluasi model,
- visualisasi hasil training,
- inference gambar baru,
- dan konversi model ke beberapa format deployment.

Model berhasil dikonversi ke format:

- SavedModel
- TensorFlow Lite
- TensorFlow.js

---

# Latar Belakang

Klasifikasi gambar merupakan salah satu permasalahan penting dalam bidang Artificial Intelligence dan Computer Vision.

Kemampuan komputer dalam mengenali objek visual dapat diterapkan pada berbagai bidang seperti:

- sistem keamanan,
- kendaraan otonom,
- smart city,
- monitoring lingkungan,
- dan aplikasi mobile berbasis AI.

Dataset Intel Image Classification dipilih karena memiliki:

- jumlah gambar yang besar,
- variasi visual yang beragam,
- serta ukuran gambar asli yang tidak seragam.

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

- Membangun model klasifikasi gambar berbasis CNN.
- Mencapai akurasi model di atas 85%.
- Mengimplementasikan preprocessing dan data augmentation.
- Menghasilkan model yang dapat digunakan pada berbagai platform deployment.
- Melakukan inference terhadap gambar baru menggunakan model yang telah dibuat.

---

## Solution Statement

Solusi yang diterapkan pada proyek ini meliputi:

- Menggunakan arsitektur Sequential CNN.
- Mengimplementasikan layer Conv2D dan MaxPooling2D secara eksplisit.
- Menggunakan BatchNormalization untuk meningkatkan stabilitas training.
- Mengimplementasikan data augmentation.
- Menggunakan callback untuk meningkatkan performa training.
- Menggunakan Dropout untuk mengurangi overfitting.
- Menggunakan GlobalAveragePooling2D agar model lebih ringan dan efisien.
- Mengonversi model ke format SavedModel, TensorFlow Lite, dan TensorFlow.js.

---

# Dataset

Dataset yang digunakan adalah:

## Intel Image Classification Dataset

Dataset diperoleh dari Kaggle:

Dataset URL:
https://www.kaggle.com/datasets/puneet6060/intel-image-classification

---

# Jumlah Kelas yang Digunakan

Pada proyek ini digunakan 5 kelas:

| Kelas | Jumlah Gambar |
|---|---|
| forest | 2271 |
| glacier | 2404 |
| mountain | 2512 |
| sea | 2274 |
| street | 2382 |

Total dataset yang digunakan sekitar 11.843 gambar.

---

# Tahapan Proyek

## 1. Import Library

Library utama yang digunakan:

- TensorFlow
- NumPy
- Matplotlib
- Seaborn
- TensorFlowJS
- Scikit-Learn

---

## 2. Data Preparation

Tahapan data preparation meliputi:

- Upload Kaggle API
- Download dataset
- Extract dataset
- Memilih 5 kelas dataset
- Menentukan direktori dataset

---

## 3. Data Understanding

Dilakukan analisis dataset untuk memahami:

- jumlah gambar,
- distribusi kelas,
- dan karakteristik visual dataset.

---

# Visualisasi Distribusi Dataset

Visualisasi distribusi dataset menunjukkan bahwa jumlah gambar pada setiap kelas relatif seimbang.

Kondisi ini membantu model melakukan proses pembelajaran secara lebih stabil karena tidak terdapat perbedaan jumlah data yang terlalu signifikan antar kelas.

Kelas mountain memiliki jumlah gambar terbanyak, sedangkan kelas forest dan sea memiliki jumlah gambar yang hampir sama.

---

# Visualisasi Sample Gambar

Visualisasi sample gambar menunjukkan bahwa setiap kelas memiliki karakteristik visual yang berbeda.

- Kelas forest didominasi pepohonan dan warna hijau.
- Kelas glacier memiliki area bersalju.
- Kelas mountain memiliki kontur pegunungan.
- Kelas sea memiliki dominasi area air.
- Kelas street menampilkan lingkungan perkotaan.

Perbedaan pola visual ini membantu model mempelajari fitur unik dari masing-masing kategori.

---

# Data Preprocessing

Tahapan preprocessing meliputi:

- Resize gambar menjadi 128x128 pixel.
- Split dataset menjadi training, validation, dan testing.
- Data augmentation.
- Prefetch dataset untuk optimasi training.

---

# Data Augmentation

Teknik augmentasi yang digunakan:

- RandomFlip
- RandomRotation
- RandomZoom
- RandomContrast

Augmentasi diterapkan hanya pada training set agar model memiliki kemampuan generalisasi yang lebih baik terhadap gambar baru.

---

# Arsitektur Model

Model dibangun menggunakan arsitektur Convolutional Neural Network (CNN) berbasis Sequential.

Arsitektur model terdiri dari:

- Input Layer
- Data Augmentation
- Rescaling Layer
- Conv2D Layer
- BatchNormalization
- MaxPooling2D
- GlobalAveragePooling2D
- Dense Layer
- Dropout
- Output Layer Softmax

---

# Penjelasan Arsitektur

## Conv2D

Layer Conv2D digunakan untuk mengekstraksi fitur visual seperti tepi, tekstur, pola, dan bentuk objek pada gambar.

---

## MaxPooling2D

Layer MaxPooling2D digunakan untuk mengurangi dimensi feature map sehingga proses komputasi menjadi lebih efisien dan membantu mengurangi risiko overfitting.

---

## BatchNormalization

BatchNormalization digunakan untuk menjaga stabilitas distribusi data selama training sehingga proses pembelajaran menjadi lebih cepat dan stabil.

---

## GlobalAveragePooling2D

Layer ini digunakan untuk mengurangi jumlah parameter dibandingkan penggunaan Flatten sehingga model menjadi lebih ringan dan efisien.

---

## Dropout

Dropout digunakan untuk mengurangi overfitting dengan menonaktifkan sebagian neuron secara acak saat proses training berlangsung.

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

Model CNN berhasil dilatih menggunakan dataset Intel Image Classification dengan lima kategori gambar.

Model berhasil mencapai akurasi training dan validation di atas 85% sehingga memenuhi kriteria submission image classification.

---

# Hasil Evaluasi

| Metric | Hasil |
|---|---|
| Train Accuracy | >85% |
| Validation Accuracy | >85% |

---

# Analisis Hasil Training

Hasil training menunjukkan bahwa akurasi training dan validation mengalami peningkatan secara konsisten selama proses training berlangsung.

Validation accuracy berhasil mencapai lebih dari 85% sehingga memenuhi kriteria submission image classification.

Nilai loss mengalami penurunan secara bertahap yang menunjukkan bahwa model mampu mempelajari pola data dengan cukup baik.

Penggunaan BatchNormalization, Dropout, callback, dan data augmentation membantu meningkatkan stabilitas training serta mengurangi risiko overfitting.

---

# Visualisasi Accuracy

Grafik accuracy menunjukkan bahwa performa model meningkat secara bertahap selama proses training.

Kurva training dan validation accuracy memiliki pola yang relatif berdekatan sehingga model tidak mengalami overfitting yang signifikan.

Hal ini menunjukkan bahwa data augmentation dan callback berhasil membantu model melakukan generalisasi dengan baik.

---

# Visualisasi Loss

Grafik loss menunjukkan penurunan nilai loss pada data training maupun validation.

Penurunan loss yang stabil menunjukkan bahwa model berhasil mempelajari pola data dengan baik.

Kurva loss yang relatif stabil menunjukkan bahwa proses training berjalan optimal.

---

# Confusion Matrix

Confusion matrix menunjukkan bahwa sebagian besar gambar berhasil diprediksi dengan benar pada masing-masing kelas.

Beberapa kesalahan prediksi masih terjadi pada kelas yang memiliki karakteristik visual mirip, namun secara keseluruhan model mampu melakukan klasifikasi dengan performa yang baik dan stabil.

Hasil confusion matrix menunjukkan bahwa model memiliki kemampuan generalisasi yang cukup baik terhadap data testing.

---

# Classification Report

Berdasarkan classification report, model memiliki nilai precision, recall, dan f1-score yang cukup baik pada sebagian besar kelas.

Hal ini menunjukkan bahwa model mampu mengenali pola visual pada masing-masing kategori gambar dengan cukup baik.

Performa model yang stabil pada seluruh kelas menunjukkan bahwa proses training dan preprocessing berjalan secara optimal.

---

# Inference Model

Model berhasil melakukan prediksi terhadap gambar baru dengan confidence yang cukup baik.

Hasil inference menunjukkan bahwa model mampu mengenali objek gambar sesuai kategori yang benar.

Inference dilakukan menggunakan model TensorFlow Lite sehingga model dapat digunakan pada deployment perangkat ringan seperti mobile dan edge device.

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