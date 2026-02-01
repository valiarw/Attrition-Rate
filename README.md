# 📄 HR Employee Attrition Analysis & Dashboard
## 📌 Project Overview
Proyek ini bertujuan untuk membantu departemen HR dalam memahami, memonitor, dan memprediksi tingkat attrition (karyawan keluar) di perusahaan. Dengan menganalisis data historis karyawan, kita dapat mengidentifikasi faktor-faktor utama penyebab resign dan membangun model prediksi untuk langkah preventif.
Proyek ini mencakup:
1) Data Analysis & Visualization: Mencari faktor penyebab attrition (Deskriptif).
2) Machine Learning Modeling: Memprediksi karyawan yang berpotensi resign (Prediktif).
3) Business Dashboard: Visualisasi interaktif menggunakan Looker Studio untuk monitoring HR.

## Business Understanding
### Problem Statements
Meningkatnya Attrition Rate bukanlah suatu hal normal, terlebih perusahaan Jaya Jaya Maju merupakan perusahaan yang cukup besar. Sehingga perlu diketahui alasan karyawan memilih resign. Karena proses recruitment, training karyawan membutuhkan biaya yang tidak sedikit, tentunya perusahaan perlu mencari tahu penyebabnya agar dapat meminimalkan karyawan yang resign. Hal yang perlu dilakukan:
1. Mengidentifikasi faktor penyebab utama karyawan resign.
2. Membuat Dashboard untuk memonitoring karyawan yang kemungkinan akan resign.
3. Membangun model klasifikasi yang mampu memberikan prediksi yang akurat dan stabil.

### Goals
Tujuan utama dari proyek ini adalah menyelesaikan masalah Human Resources:
1. Mengetahui penyebab tingginya karyawan yang resign
2. Mampu meminimalkan angka resign dengan melakukan evaluasi setelah diketahui penyebab utama
3. Mampu memprediksi karyawan yang berpotensi resign.

### Solution Statements
Untuk mencapai tujuan tersebut, pendekatan solusi menggunakan eksplorasi data karyawan dan membuat model machine learning
    a. Mengimplementasikan dan membandingkan performa beberapa algoritma klasifikasi, seperti:
    - Random Forest Classifier
    - Logistic Resresion
    - Naive Bayes
    b. Metrik evaluasi yang digunakan untuk membandingkan model:
    - Accuracy – proporsi prediksi yang benar.
    - Precision – proporsi prediksi positif yang benar.
    - Recall – proporsi data positif yang berhasil ditemukan oleh model.
    - F1-score – harmonisasi precision dan recall.

## Data Understanding 
Pada proyek ini, dataset yang digunakan adalah [Employee_Data.csv](https://github.com/dicodingacademy/dicoding_dataset/blob/main/employee/employee_data.csv).

### Kondisi dan karakteristik Dataset:
- Jumlah data: 1.470 baris (record)
- Jumlah fitur: 34 fitur + 1 target (Attrition)
- Tipe data: kombinasi antara numerik, kategorikal, dan biner
- Kondisi: Data bersih, namun memerlukan encoding untuk fitur kategorikal sebelum digunakan dalam model machine learning.
- Target variabel: Attrition (0 = Stay, 1 = Resign)

### 📂 Data Dictionary
Berikut adalah penjelasan mengenai kolom-kolom yang terdapat dalam dataset:

| Feature | Description | Values / Scale |
| :--- | :--- | :--- |
| **EmployeeId** | Identitas unik karyawan | - |
| **Attrition** | Target Variabel: Apakah karyawan resign? | `0` = No (Stay)<br>`1` = Yes (Resign) |
| **Age** | Usia karyawan | Tahun |
| **BusinessTravel** | Seberapa sering karyawan bepergian untuk kerja | Non-Travel, Travel_Rarely, Travel_Frequently |
| **DailyRate** | Upah harian | Numerical |
| **Department** | Departemen tempat bekerja | Sales, R&D, HR, etc. |
| **DistanceFromHome** | Jarak dari rumah ke kantor | Kilometer (km) |
| **Education** | Tingkat pendidikan terakhir | `1` = Below College<br>`2` = College<br>`3` = Bachelor<br>`4` = Master<br>`5` = Doctor |
| **EducationField** | Bidang studi pendidikan | Life Sciences, Medical, etc. |
| **EnvironmentSatisfaction** | Tingkat kepuasan lingkungan kerja | `1` = Low<br>`2` = Medium<br>`3` = High<br>`4` = Very High |
| **Gender** | Jenis kelamin karyawan | Male / Female |
| **HourlyRate** | Upah per jam | Numerical |
| **JobInvolvement** | Tingkat keterlibatan dalam pekerjaan | `1` = Low<br>`2` = Medium<br>`3` = High<br>`4` = Very High |
| **JobLevel** | Tingkat jabatan | 1 (Junior) - 5 (Senior) |
| **JobRole** | Posisi pekerjaan | Sales Exec, Manager, etc. |
| **JobSatisfaction** | Tingkat kepuasan kerja | `1` = Low<br>`2` = Medium<br>`3` = High<br>`4` = Very High |
| **MaritalStatus** | Status pernikahan | Single, Married, Divorced |
| **MonthlyIncome** | Gaji bulanan | Numerical (USD/IDR) |
| **MonthlyRate** | Tarif bulanan | Numerical |
| **NumCompaniesWorked** | Jumlah perusahaan tempat bekerja sebelumnya | Numerical |
| **Over18** | Apakah usia di atas 18 tahun? | Y / N |
| **OverTime** | Apakah karyawan bekerja lembur? | Yes / No |
| **PercentSalaryHike** | Persentase kenaikan gaji tahun lalu | Percentage (%) |
| **PerformanceRating** | Penilaian kinerja karyawan | `1` = Low<br>`2` = Good<br>`3` = Excellent<br>`4` = Outstanding |
| **RelationshipSatisfaction** | Tingkat kepuasan hubungan kerja | `1` = Low<br>`2` = Medium<br>`3` = High<br>`4` = Very High |
| **StandardHours** | Jam kerja standar | Numerical (e.g., 80) |
| **StockOptionLevel** | Tingkat opsi saham yang dimiliki | 0 - 3 |
| **TotalWorkingYears** | Total pengalaman kerja | Tahun |
| **TrainingTimesLastYear** | Jumlah pelatihan yang diikuti tahun lalu | Kali |
| **WorkLifeBalance** | Keseimbangan kehidupan kerja | `1` = Low<br>`2` = Good<br>`3` = Excellent<br>`4` = Outstanding |
| **YearsAtCompany** | Lama bekerja di perusahaan saat ini | Tahun |
| **YearsInCurrentRole** | Lama berada di posisi saat ini | Tahun |
| **YearsSinceLastPromotion** | Lama tahun sejak promosi terakhir | Tahun |
| **YearsWithCurrManager** | Lama bekerja dengan manajer saat ini | Tahun |

## Data Preparation
Proses data preparation sangat penting dilakukan sebelum membangun model machine learning karena data mentah biasanya mengandung ketidaksempurnaan seperti nilai kosong (missing values), data outlier, data tidak terstandarisasi, serta kategori yang belum diubah menjadi format numerik. Jika tidak ditangani, hal ini dapat menyebabkan penurunan akurasi model dan interpretasi hasil yang keliru. Berikut adalah beberapa teknik atau metode yang digunakan dalam persiapan data pada proyek ini:
1. **Undersampling:** teknik yang digunakan untuk menyeimbangkan distribusi kelas dalam dataset, khususnya ketika terjadi class imbalance (jumlah sampel di suatu kelas lebih banyak dari kelas lainnya).
Tujuannya adalah untuk mengurangi jumlah data yang diproses sehingga dapat mempercepat waktu pelatihan model dan mencegah crash yang bisa terjadi kedepannya.
2. **Feature Selection:** suatu proses memilih subset kolom (atau fitur) yang relevan dari dataset untuk digunakan dalam analisis atau pelatihan model. Langkah ini bertujuan untuk menghapus fitur yang tidak relevan atau tidak diperlukan agar model lebih efisien dan akurat.
3. **Categorical Encoding:** teknik dalam data preparation yang digunakan untuk mengubah data kategorikal (teks/label non-numerik) menjadi format numerik agar bisa digunakan oleh algoritma machine learning.
4. **Train-test split:** teknik membagi dataset menjadi dua (atau lebih) bagian, yaitu: train, validation, test. Tujuannya untuk mengevaluasi generalisasi model secara adil, agar tidak hanya bagus pada data yang dilatih, tapi juga pada data nyata yang belum pernah dilihat.
5. **Feature Scaling:** teknik dalam data preprocessing untuk menstandarkan atau menormalkan skala fitur numerik agar model machine learning dapat mempelajari data secara efektif.

## Modeling
Pada proyek ini algoritma machine learning yang digunakan ada, 3 yaitu:
1. **Random Forest**
- Kelebihan:
    - Mengatasi overfitting dengan baik berkat teknik ensembling (bagging).
    - Dapat menangani data numerik maupun kategorikal tanpa perlu banyak preprocessing.
    - Memiliki fitur penting (feature importance) yang membantu dalam seleksi fitur.
- Kekurangan:
    - Bisa memakan memori besar karena banyaknya pohon.
    - Interpretasi model lebih kompleks dibanding decision tree tunggal.
    - Kurang optimal untuk data yang highly imbalanced, kecuali disesuaikan.
2. **Logistic Regression**
- Kelebihan:
    - Komputasinya sangat ringan. Melatih data ribuan baris cuma butuh sepersekian detik.
    - Jarang mengalami overfitting pada dataset kecil hingga menengah, asalkan fiturnya tidak terlalu banyak.
- Kekurangan:
    - Sensitif terhadap Outlier (Data Pencilan)
    - Masalah Multikolinearitas, fitur yang mirip harus dibuang salah satu.
3. **Neural Network**
- Kelebihan:
    - Mampu menangkap pola kompleks dan relasi non-linear dalam data.
    - Bisa bekerja dengan baik jika diberi data yang besar dan beragam.
    - Fleksibel dalam arsitektur (jumlah layer, neuron, aktivasi).
- Kekurangan:
    - Rentan overfitting jika data terlalu sedikit.
    - Memerlukan proses training yang lama, terutama dengan banyak layer.
    - Sulit diinterpretasi dibanding model lainnya.

Berikut adalah perbandingan performa model Machine Learning yang telah dilatih:
| Model | Accuracy | Precision | Recall | F1-Score |
| :--- | :--- | :--- | :--- | :--- |
| **RandomForestClassifier** | **0.9508** | **0.9554** | **0.9508** | **0.9508** |
| **NeuralNetwork** | 0.8826 | 0.9003 | 0.8826 | 0.8820 |
| **LogisticRegression** | 0.7311 | 0.7368 | 0.7311 | 0.7309 |
- Model Terbaik: __Random Forest Classifier__
Alasan pemilihan:
    - Random Forest adalah model terbaik mutlak dengan akurasi dan F1-Score mencapai 95%. Ini menunjukkan bahwa algoritma berbasis decision trees ini sangat cocok dengan pola data karyawanmu.
    - Terlihat perbedaan yang jauh (sekitar 22%) antara Random Forest dan Logistic Regression (73%). Ini mengindikasikan bahwa hubungan antar variabel dalam datamu cenderung Non-Linear (kompleks), sehingga Logistic Regression kesulitan menangkap polanya sebaik Random Forest.
      
## Evaluation
Untuk mengevaluasi performa model dalam memprediksi persetujuan pinjaman (LoanApproved), digunakan empat metrik utama berikut:
1. Accuracy
Mengukur proporsi prediksi yang benar dari keseluruhan prediksi.

$$\text{Accuracy} = \frac{TP + TN}{TP + TN + FP + FN}$$

3. Precision
Mengukur seberapa akurat prediksi positif yang dibuat oleh model. Penting jika kesalahan positif berdampak besar (contoh: menyetujui pinjaman untuk peminjam yang seharusnya tidak lolos).

$$\text{Precision} = \frac{TP}{TP + FP}$$

4. Recall
Mengukur seberapa banyak kasus positif yang berhasil ditangkap oleh model. Sangat penting dalam kasus di mana mengidentifikasi semua peminjam yang layak adalah prioritas utama.

$$\text{Recall} = \frac{TP}{TP + FN}$$

5. F1-Score
Merupakan harmonic mean antara precision dan recall. Berguna ketika ada ketidakseimbangan kelas dan kita ingin keseimbangan antara keduanya.

$$\text{F1-Score} = 2 \cdot \frac{\text{Precision} \cdot \text{Recall}}{\text{Precision} + \text{Recall}}$$

## Conclusion & Recommendations
Berdasarkan analisis data (EDA) dan pengembangan model Machine Learning yang telah dilakukan, berikut adalah kesimpulan utama dari proyek ini:
### 1. Key Business Insights (Faktor Penyebab)
Analisis menunjukkan bahwa keputusan karyawan untuk *resign* tidak terjadi secara acak, melainkan didorong oleh faktor-faktor spesifik:
* **Overtime (Lembur):** Karyawan yang bekerja lembur memiliki tingkat *attrition* yang jauh lebih tinggi dibandingkan yang tidak. Ini adalah faktor risiko terbesar.
* **Monthly Income:** Terdapat korelasi negatif yang kuat antara gaji dan *attrition*. Karyawan dengan gaji di bawah rata-rata (terutama di level Junior) lebih rentan untuk keluar.
* **Age & Job Role:** Karyawan muda (<30 tahun) dan posisi *entry-level* (seperti Sales Representative & Lab Technician) memiliki turnover rate tertinggi.

### 2. Model Performance (Solusi Prediktif)
Dari tiga algoritma yang diuji, **Random Forest Classifier** terpilih sebagai model terbaik dengan performa yang sangat memuaskan:
* **Akurasi: 95.08%** (Sangat tinggi).
* **Precision & Recall: ~95%**.
* Hal ini menunjukkan bahwa model mampu memprediksi karyawan yang berpotensi *resign* dengan tingkat kesalahan yang sangat minim (kurang dari 5%). Model ini jauh mengungguli Logistic Regression (73%) karena kemampuannya menangkap pola hubungan non-linear yang kompleks dalam data karyawan.

### 3. Actionable Recommendations for HR
Untuk menurunkan tingkat *attrition*, disarankan agar perusahaan melakukan:
* **Evaluasi Struktur Gaji (Salary Adjustment)**: melakukan review gaji khusus untuk posisi Sales Representative dan Lab Technician. Gap pendapatan mereka terlalu jauh dibandingkan level di atasnya.
* **Program Retensi Junior**: Buat program pengembangan karir (career path) yang jelas untuk karyawan usia 20-30 tahun agar mereka melihat masa depan di perusahaan dan tidak buru-buru pindah.
* **Fokus Penanganan**: Daripada fokus ke departemen HR atau Manager (yang jumlah resign-nya sedikit), fokuskan tenaga HR untuk membenahi departemen Sales & R&D (Research) yang memiliki bar resign paling panjang.
  
# 🛠️ Requirements & Installation
Jika ingin menjalankan kode analisis ini di lokal atau Google Colab:
- Clone repository ini:
  
`git clone https://github.com/valiarw/Attrition-Rate.git`

- Install library yang dibutuhkan:
  
`pip install -r requirements.txt`
