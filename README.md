# LoanPredict-FinalProject

**LoanPredict** adalah proyek pembelajaran mesin yang dirancang untuk memprediksi risiko kredit menggunakan data pinjaman. Tujuan dari proyek ini adalah untuk memprediksi apakah pinjaman akan dibayar tepat waktu atau gagal bayar berdasarkan berbagai fitur seperti jumlah pinjaman, tingkat bunga, tenor, dan lainnya.

## Ikhtisar Proyek

Dalam proyek ini, Saya bereksperimen dengan beberapa algoritma pembelajaran mesin untuk memprediksi apakah pinjaman akan dibayar tepat waktu atau gagal bayar menggunakan dataset yang berisi informasi pinjaman. Saya menguji beberapa model seperti **Logistic Regression**, **Random Forest** (baik dengan parameter default maupun dengan tuning hyperparameter menggunakan RandomizedSearchCV), dan **XGBoost** (dengan parameter default) untuk mengevaluasi performa mereka berdasarkan metrik seperti akurasi, presisi, recall, F1 score, dan ROC AUC.

## Pemahaman Data

Dataset ini berisi informasi pinjaman termasuk:
- **loan_amnt**: Jumlah pinjaman# LoanPredict-FinalProject

**LoanPredict** adalah proyek pembelajaran mesin yang dirancang untuk memprediksi risiko kredit menggunakan data pinjaman. Tujuan dari proyek ini adalah untuk memprediksi apakah pinjaman akan dibayar tepat waktu atau gagal bayar berdasarkan berbagai fitur seperti jumlah pinjaman, tingkat bunga, tenor, dan lainnya.

## Ikhtisar Proyek

Dalam proyek ini, Saya bereksperimen dengan beberapa algoritma pembelajaran mesin untuk memprediksi apakah pinjaman akan dibayar tepat waktu atau gagal bayar menggunakan dataset yang berisi informasi pinjaman. Saya menguji beberapa model seperti **Logistic Regression**, **Random Forest** (baik dengan parameter default maupun dengan tuning hyperparameter menggunakan RandomizedSearchCV), dan **XGBoost** (dengan parameter default) untuk mengevaluasi performa mereka berdasarkan metrik seperti akurasi, presisi, recall, F1 score, dan ROC AUC.

## Pemahaman Data

Dataset ini berisi informasi pinjaman termasuk:
- **loan_amnt**: Jumlah pinjaman
- **int_rate**: Tingkat bunga
- **loan_status**: Status pinjaman (Current, Fully Paid, Charged Off, Late, Default, dll.)
- Fitur keuangan lainnya terkait dengan histori pembayaran dan profil peminjam.

### Wawasan Kunci:
- Dataset tidak seimbang, dengan lebih banyak pinjaman yang berstatus "Current" atau "Fully Paid" dibandingkan dengan "Charged Off" atau "Late."
- Fitur seperti **loan_amnt** dan **int_rate** adalah prediktor yang penting untuk menentukan risiko pinjaman.

## Langkah-Langkah yang Dilakukan

### 1. Persiapan Data:
- Menghapus kolom dengan kardinalitas tinggi dan missing values lebih dari 60%.
- Menangani missing values dengan imputasi menggunakan median untuk fitur numerik dan modus untuk fitur kategorikal.
- Mengubah **loan_status** menjadi target biner: 1 untuk pinjaman non-gagal bayar dan 0 untuk pinjaman gagal bayar.
- Menstandarkan fitur numerik menggunakan **StandardScaler** dan mengubah fitur kategorikal menggunakan **LabelEncoder**.

### 2. Analisis Data Eksploratif (EDA):
- Menganalisis distribusi jumlah pinjaman, tingkat bunga, dan status pinjaman.
- Melakukan analisis bivariat untuk memahami hubungan antara fitur-fitur seperti **loan_amnt** dan **loan_status**.
- Memeriksa korelasi antar fitur numerik dan mengidentifikasi fitur yang redundan atau sangat berkorelasi.

### 3. Pemodelan:
- Menerapkan **Logistic Regression** sebagai model dasar.
- Bereksperimen dengan **Random Forest** (default dan dengan RandomizedSearchCV untuk tuning hyperparameter).
- Menggunakan **XGBoost** untuk pelatihan dan evaluasi model.
- Mengevaluasi setiap model menggunakan akurasi, presisi, recall, F1 score, dan ROC AUC.

## Evaluasi Model

### Tabel Perbandingan Metrik Evaluasi untuk Setiap Model:

| Model                               | Accuracy | Precision | Recall  | F1 Score | ROC AUC |
|-------------------------------------|----------|-----------|---------|----------|---------|
| **Logistic Regression - Default**   | 96.77%   | 98.69%    | 74.75%  | 85.06%   | 95.17%  |
| **Logistic Regression - Thresholds = 0.2** | 96.88%   | 92.41%    | 78.27%  | 84.78%   | 95.17%  |
| **Random Forest (Default)**         | 97.58%   | 99.36%    | 80.87%  | 89.17%   | 98.15%  |
| **Random Forest (RandomizedSearchCV)** | 97.50%   | 99.42%    | 80.14%  | 88.75%   | 98.33%  |
| **XGBoost (Default)**               | 98.54%   | 99.66%    | 88.39%  | 93.69%   | 99.31%  |

## Kesimpulan

- **Model Terbaik**: Berdasarkan AUC dan F1 Score, **XGBoost** dengan parameter default menunjukkan performa terbaik.
- **Random Forest (Default)** memberikan keseimbangan yang sangat baik antara Precision dan Recall, menjadikannya model yang sangat baik jika lebih mengutamakan deteksi risiko kredit.
- **Logistic Regression** memberikan hasil yang stabil, tetapi sedikit kurang baik dibandingkan dengan **Random Forest** dan **XGBoost** dalam hal recall dan AUC.

## Rekomendasi

**XGBoost** sangat direkomendasikan untuk aplikasi prediksi risiko kredit jika fokus pada kemampuan membedakan kelas dengan AUC yang tinggi dan recall yang baik.

---

Silakan gunakan format ini untuk membuat `README.md` yang dapat Anda unggah ke GitHub.

- **int_rate**: Tingkat bunga
- **loan_status**: Status pinjaman (Current, Fully Paid, Charged Off, Late, Default, dll.)
- Fitur keuangan lainnya terkait dengan histori pembayaran dan profil peminjam.

### Wawasan Kunci:
- Dataset tidak seimbang, dengan lebih banyak pinjaman yang berstatus "Current" atau "Fully Paid" dibandingkan dengan "Charged Off" atau "Late."
- Fitur seperti **loan_amnt** dan **int_rate** adalah prediktor yang penting untuk menentukan risiko pinjaman.

## Langkah-Langkah yang Dilakukan

### 1. Persiapan Data:
- Menghapus kolom dengan kardinalitas tinggi dan missing values lebih dari 60%.
- Menangani missing values dengan imputasi menggunakan median untuk fitur numerik dan modus untuk fitur kategorikal.
- Mengubah **loan_status** menjadi target biner: 1 untuk pinjaman non-gagal bayar dan 0 untuk pinjaman gagal bayar.
- Menstandarkan fitur numerik menggunakan **StandardScaler** dan mengubah fitur kategorikal menggunakan **LabelEncoder**.

### 2. Analisis Data Eksploratif (EDA):
- Menganalisis distribusi jumlah pinjaman, tingkat bunga, dan status pinjaman.
- Melakukan analisis bivariat untuk memahami hubungan antara fitur-fitur seperti **loan_amnt** dan **loan_status**.
- Memeriksa korelasi antar fitur numerik dan mengidentifikasi fitur yang redundan atau sangat berkorelasi.

### 3. Pemodelan:
- Menerapkan **Logistic Regression** sebagai model dasar.
- Bereksperimen dengan **Random Forest** (default dan dengan RandomizedSearchCV untuk tuning hyperparameter).
- Menggunakan **XGBoost** untuk pelatihan dan evaluasi model.
- Mengevaluasi setiap model menggunakan akurasi, presisi, recall, F1 score, dan ROC AUC.

## Evaluasi Model

### Tabel Perbandingan Metrik Evaluasi untuk Setiap Model:

| Model                               | Accuracy | Precision | Recall  | F1 Score | ROC AUC |
|-------------------------------------|----------|-----------|---------|----------|---------|
| **Logistic Regression - Default**   | 96.77%   | 98.69%    | 74.75%  | 85.06%   | 95.17%  |
| **Logistic Regression - Thresholds = 0.2** | 96.88%   | 92.41%    | 78.27%  | 84.78%   | 95.17%  |
| **Random Forest (Default)**         | 97.58%   | 99.36%    | 80.87%  | 89.17%   | 98.15%  |
| **Random Forest (RandomizedSearchCV)** | 97.50%   | 99.42%    | 80.14%  | 88.75%   | 98.33%  |
| **XGBoost (Default)**               | 98.54%   | 99.66%    | 88.39%  | 93.69%   | 99.31%  |

## Kesimpulan

- **Model Terbaik**: Berdasarkan AUC dan F1 Score, **XGBoost** dengan parameter default menunjukkan performa terbaik.
- **Random Forest (Default)** memberikan keseimbangan yang sangat baik antara Precision dan Recall, menjadikannya model yang sangat baik jika lebih mengutamakan deteksi risiko kredit.
- **Logistic Regression** memberikan hasil yang stabil, tetapi sedikit kurang baik dibandingkan dengan **Random Forest** dan **XGBoost** dalam hal recall dan AUC.

## Rekomendasi

**XGBoost** sangat direkomendasikan untuk aplikasi prediksi risiko kredit jika fokus pada kemampuan membedakan kelas dengan AUC yang tinggi dan recall yang baik.

---

Silakan gunakan format ini untuk membuat `README.md` yang dapat Anda unggah ke GitHub.
