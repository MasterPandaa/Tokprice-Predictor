# 🏷️ Tokprice-Predictor — E-Commerce Intelligence & Sales Estimation System

[![Python](https://img.shields.io/badge/Python-3.9+-3776AB.svg?logo=python&logoColor=white)](#)
[![Flask](https://img.shields.io/badge/Flask-2.x-000000.svg?logo=flask&logoColor=white)](#)
[![Scikit-Learn](https://img.shields.io/badge/scikit--learn-ML%20Pipeline-F7931E.svg?logo=scikit-learn&logoColor=white)](#)
[![Tailwind CSS](https://img.shields.io/badge/TailwindCSS-3.x-38B2AC.svg?logo=tailwind-css&logoColor=white)](#)
[![Explainable AI](https://img.shields.io/badge/XAI-Feature%20Impact%20Analysis-8B5CF6.svg)](#)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](#)

**Tokprice-Predictor** adalah sistem pendukung keputusan (*Decision Support System*) dan estimasi potensi performa produk e-commerce berbasis Machine Learning dan Natural Language Processing (NLP). Dirancang untuk membantu seller, data analyst, dan pelaku bisnis menganalisis potensi volume penjualan produk Tokopedia secara akurat sebelum merilis atau mengoptimasi listing produk.

Aplikasi ini menggabungkan model regresi prediktif (**Ridge Regression**), normalisasi numerik (**StandardScaler**), ekstraksi representasi semantik teks judul produk (**TF-IDF Vectorizer**), serta visualisasi interaktif **Explainable AI (XAI)** untuk transparansi analisis faktor penentu penjualan.

---

## 🌟 Mengapa Menggunakan Tokprice-Predictor?

- 🚫 **Menghilangkan Spekulasi Penetapan Harga (Zero Guesswork)**: Menghindari penetapan harga dan persentase diskon yang tidak efektif melalui data acuan pasar yang telah dilatih dari puluhan ribu data produk nyata.
- ⚡ **Prediksi Instan & Menyeluruh**: Menghasilkan estimasi jumlah unit terjual (*predicted sales*), rentang estimasi (*confidence interval*), dan *confidence score* dalam hitungan milidetik.
- 🎯 **Explainable AI (XAI) Transparan**: Tidak hanya memberikan angka hasil prediksi, sistem juga menguraikan kontribusi tiap faktor (Nama Produk, Lokasi Toko, Harga, Diskon, Rating, Ulasan) menjadi faktor pendorong vs penghambat.
- 🛡️ **Validasi Data & Deteksi Anomali Cerdas**: Dilengkapi filter peringatan otomatis jika mendeteksi anomali input (nama produk terlalu pendek, harga tidak wajar, atau kombinasi rating & ulasan yang mencurigakan).

---

## 🚀 Fitur Utama

1. **Estimasi Potensi Penjualan Realistis (`Ridge Regression + Scaler`)**:
   - Memproses data harga asli, diskon, harga final, rating, ulasan, serta panjang nama produk melalui `StandardScaler` untuk menghasilkan proyeksi penjualan yang stabil dengan metrik RMSE terkalibrasi.
2. **Ekstraksi Semantik Teks Bahasa Indonesia (`TF-IDF Vectorizer`)**:
   - Pembersihan teks otomatis (`clean_text` regex sanitization) dan pemetaan bobot kata kunci dari judul produk untuk menangkap pengaruh daya tarik penamaan barang terhadap konversi pasar.
3. **Analisis Faktor Penentu / Explainability Plot (`Matplotlib In-Memory Rendering`)**:
   - Grafik batang visualisasi kontribusi faktor (*SHAP-inspired breakdown*) yang di-generate langsung di backend dan dikirim dalam format Base64 secara aman tanpa dependensi file eksternal.
4. **Indikator Keyakinan Adaptif (`Confidence Level Meter`)**:
   - Algoritma penilaian tingkat keyakinan prediksi dinamis yang menyesuaikan skor berdasarkan kelengkapan parameter input dan kesesuaian lokasi distribusi toko.
5. **Modern Responsive Web Dashboard (`Tailwind CSS + Lucide Icons`)**:
   - Antarmuka interaktif yang elegan, mendukung form input lengkap, status feedback animasi loading, serta kartu metrik informatif.
6. **Production-Ready Deployment Setup (`Procfile + Gunicorn`)**:
   - Terkonfigurasi untuk deployment langsung ke platform cloud (Heroku, Render, Railway, VPS) dengan WSGI server standar industri.

---

## 🛠️ Tata Cara Instalasi

### 1. Prasyarat Sistem
Pastikan perangkat Anda telah terinstal:
- **Python 3.9+** ([Unduh Python](https://www.python.org/downloads/))
- **Git** ([Unduh Git](https://git-scm.com/))
- **pip** (Python Package Installer)

---

### 2. Clone Repository
```bash
git clone https://github.com/MasterPandaa/Tokprice-Predictor.git
cd Tokprice-Predictor
```

---

### 3. Setup Virtual Environment (Disarankan)

#### 🪟 Windows (PowerShell / Command Prompt)
```powershell
python -m venv venv
.\venv\Scripts\activate
```

#### 🐧 Linux / 🍎 macOS (Bash / Zsh)
```bash
python3 -m venv venv
source venv/bin/activate
```

---

### 4. Instalasi Dependensi
```bash
pip install -r requirements.txt
```

---

### 5. Menjalankan Aplikasi
```bash
python app.py
```
Setelah server aktif, buka browser Anda dan akses:
👉 **[http://127.0.0.1:5000](http://127.0.0.1:5000)**

---

## 📖 Panduan Penggunaan

1. **Buka Dashboard**: Akses [http://127.0.0.1:5000](http://127.0.0.1:5000) pada browser pilihan Anda.
2. **Isi Parameter Produk**:
   - **Nama Produk**: Masukkan nama lengkap produk (misal: `Kopi Robusta Asli 1kg`).
   - **Lokasi Toko**: Pilih kota asal toko dari dropdown list yang tersedia.
   - **Harga (Rp)**: Masukkan harga dasar produk sebelum diskon.
   - **Diskon (%)**: Masukkan persentase promo diskon (contoh: `10` atau `25.5`).
   - **Rating (0-5)**: Masukkan rata-rata rating kepuasan pelanggan.
   - **Jml Ulasan**: Masukkan estimasi atau target akumulasi jumlah ulasan.
3. **Eksekusi Prediksi**: Klik tombol **"Jalankan Prediksi"**.
4. **Analisis Hasil**:
   - Periksa **Estimasi Penjualan (Unit)** dan **Rentang Estimasi (Range)**.
   - Pantau **Confidence Level** dan periksa box peringatan (*Warning Alert*) jika ada anomali.
   - Evaluasi grafik **Analisis Faktor Penentu** untuk melihat elemen mana yang paling mendongkrak penjualan (warna hijau) atau berpotensi menurunkan konversi (warna merah).
5. **Simulasi & Optimasi**: Ubah parameter harga atau diskon secara iteratif untuk menemukan skenario harga terbaik (*optimal pricing sweet spot*).

---

## 📦 Struktur Project

```text
Tokprice-Predictor/
├── models/
│   ├── feature_columns.pkl    # Daftar nama dan urutan kolom fitur input model
│   ├── model_linreg.pkl       # Model regresi terlatih (Ridge/Linear Regression)
│   ├── scaler.pkl             # StandardScaler terlatih untuk normalisasi variabel numerik
│   └── tfidf.pkl              # Model TF-IDF Vectorizer untuk representasi teks judul produk
├── templates/
│   └── index.html             # UI Dashboard modern (Tailwind CSS, Lucide Icons, Jinja2 template)
├── .gitattributes             # Konfigurasi atribut Git & format line ending
├── Procfile                   # Konfigurasi runner web server (Gunicorn) untuk cloud deployment
├── README.md                  # Dokumentasi resmi & petunjuk instalasi lengkap
├── app.py                     # Entry point Flask backend, preprocessing, inferensi ML & visualisasi XAI
└── requirements.txt           # Daftar dependensi library Python proyek
```

---

## 🔒 Privasi & Keamanan

- **100% On-Premise / Local Inference**: Seluruh pemrosesan model inferensi ML dan NLP dijalankan secara lokal di environment server Anda tanpa mengirimkan data transaksi bisnis ke server pihak ketiga.
- **Input Sanitization**: Data teks judul produk disaring secara ketat untuk mencegah karakter anomali.
- **In-Memory Chart Generation**: Grafik visualisasi dihasilkan langsung di memori RAM dan di-encode ke Base64 tanpa meninggalkan temporary file di storage server.

---

## 📄 Lisensi

Didistribusikan di bawah lisensi [MIT](LICENSE). Bebas digunakan, dikembangkan, dan dimodifikasi untuk kebutuhan riset, pengujian, maupun penerapan komersial.
