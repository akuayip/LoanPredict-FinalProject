# LoanPredict-FinalProject

**LoanPredict** adalah proyek pembelajaran mesin yang dirancang untuk memprediksi risiko kredit menggunakan data pinjaman. Tujuan dari proyek ini adalah untuk memprediksi apakah pinjaman akan dibayar tepat waktu atau gagal bayar berdasarkan berbagai fitur seperti jumlah pinjaman, tingkat bunga, tenor, dan lainnya.

## Ikhtisar Proyek
Dalam proyek ini, kami bereksperimen dengan beberapa algoritma pembelajaran mesin untuk memprediksi apakah pinjaman akan dibayar tepat waktu atau gagal bayar menggunakan dataset yang berisi informasi pinjaman. Kami menguji beberapa model seperti **Logistic Regression**, **Random Forest** (baik dengan parameter default maupun dengan tuning hyperparameter menggunakan **RandomizedSearchCV**), dan **XGBoost** (dengan parameter default) untuk mengevaluasi performa mereka berdasarkan metrik seperti akurasi, presisi, recall, F1 score, dan ROC AUC.

---

## 1. Data Understanding

### Analisis Dataset:
Dataset yang digunakan berisi ribuan baris dan beberapa puluh kolom dengan data numerik dan kategorikal, mencakup informasi seperti:
- `loan_amnt` (jumlah pinjaman)
- `int_rate` (tingkat bunga)
- `loan_status` (status pinjaman)
- dan fitur-fitur lain terkait profil keuangan peminjam.

### Identifikasi Atribut Data:
- `loan_status` digunakan sebagai target variabel, dikonversi menjadi biner: 1 untuk pinjaman non-gagal bayar, 0 untuk gagal bayar.
- Variabel seperti `loan_amnt` dan `int_rate` diidentifikasi sebagai prediktor penting dalam analisis risiko kredit.

### Eksplorasi Awal:
- Distribusi awal menunjukkan dominasi status seperti “Fully Paid” dan “Current”.
- Statistik deskriptif digunakan untuk memahami penyebaran data, mengidentifikasi outlier, dan mengenali ketidakseimbangan kelas.

---

## 2. Exploratory Data Analysis (EDA)

### Visualisasi Data:
- Histogram dan boxplot digunakan untuk menggambarkan distribusi `loan_amnt`, `int_rate`, dan `loan_status`.
- Visualisasi membantu mendeteksi skewness, outlier, dan dominasi kelas tertentu.

### Analisis Korelasi:
- Korelasi antar fitur numerik dihitung untuk mengidentifikasi hubungan yang signifikan.
- Ditemukan korelasi yang relevan antara `loan_amnt`, `int_rate`, dan `loan_status`.

### Analisis Univariat dan Bivariat:
- **Univariat**: Menganalisis distribusi fitur tunggal seperti jumlah pinjaman dan tingkat bunga.
- **Bivariat**: Melihat hubungan antar fitur, misalnya hubungan antara `loan_amnt` dan `loan_status`.

---

## 3. Data Preparation

### Menangani Nilai yang Hilang:
- Kolom dengan missing values lebih dari 60% dihapus.
- Missing values pada data numerik diisi dengan **median**, sedangkan pada data kategorikal menggunakan **modus**.

### Mengatasi Outlier:
- Pengecekan dilakukan, namun tidak ada perlakuan khusus karena tidak ditemukan outlier yang berpengaruh signifikan.

### Encoding Kategorikal:
- Menggunakan **LabelEncoder** untuk mengubah fitur kategorikal (seperti `purpose`, `loan_status`) menjadi numerik.

### Scaling dan Normalisasi:
- Fitur numerik dinormalisasi menggunakan **StandardScaler** agar tidak bias terhadap skala.

### Pembagian Data:
- Data dibagi menjadi **train set** dan **test set** dengan rasio 80:20.

---

## 4. Data Modelling

### Memilih Model:
Model yang digunakan:
- **Logistic Regression**
- **Random Forest** (default dan dengan **RandomizedSearchCV**)
- **XGBoost**

### Pelatihan Model:
- Setiap model dilatih menggunakan train set.
- Evaluasi awal menggunakan default hyperparameter untuk baseline.

### Penyesuaian Parameter:
- **RandomizedSearchCV** diterapkan pada **Random Forest** untuk hyperparameter tuning.

### Evaluasi Model:
- Evaluasi dilakukan menggunakan metrik: **Accuracy**, **Precision**, **Recall**, **F1 Score**, dan **ROC AUC**.
- Analisis dilakukan terhadap potensi **overfitting** atau **underfitting**, disesuaikan dengan performa model pada train dan test set.

---

## 5. Evaluation

### Evaluasi Kinerja Model:
- Metrik dihitung pada test set untuk membandingkan performa semua model.

### Menganalisis Metrik Evaluasi:
- **XGBoost** menunjukkan performa terbaik dalam **ROC AUC** dan **F1 Score**.
- **Random Forest** unggul dalam keseimbangan antara **Precision** dan **Recall**.
- **Logistic Regression** stabil tetapi sedikit kalah dalam **Recall** dan **AUC**.

### Tabel Perbandingan Metrik Evaluasi:

| Model                                  | Accuracy | Precision | Recall  | F1 Score | ROC AUC |
|----------------------------------------|----------|-----------|---------|----------|---------|
| Logistic Regression - Default          | 96.77%   | 98.69%    | 74.74%  | 85.06%   | 95.17%  |
| Logistic Regression - Threshold = 0.2  | 96.88%   | 92.41%    | 78.27%  | 84.78%   | 95.17%  |
| Random Forest (Default)                | 97.58%   | 99.36%    | 80.87%  | 89.17%   | 98.15%  |
| Random Forest - RandomizedSearchCV     | 97.50%   | 99.42%    | 80.14%  | 88.75%   | 98.33%  |
| XGBoost                                | 98.54%   | 99.66%    | 88.39%  | 93.69%   | 99.31%  |

---

## Kesimpulan

- **Model Terbaik**: Berdasarkan **AUC** dan **F1 Score**, **XGBoost** memberikan performa terbaik.
- **Random Forest** dengan default parameter menunjukkan keseimbangan terbaik antara **Precision** dan **Recall**, menjadikannya alternatif yang andal.
- **Logistic Regression** adalah baseline yang baik dan stabil, namun performanya sedikit lebih rendah dari model-model lainnya.

## Rekomendasi
Untuk implementasi prediksi risiko kredit yang membutuhkan performa tinggi dalam membedakan pinjaman baik dan buruk, **XGBoost** direkomendasikan sebagai model utama.

**Terimakasih**