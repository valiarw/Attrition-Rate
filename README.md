# Laporan Proyek Data Science - Valia Rismawanti
**Submission Pertama: Menyelesaikan Permasalahan Human Resources**

## Project Overview
### Latar Belakang
Jaya Jaya Maju merupakan salah satu perusahaan multinasional yang telah berdiri sejak tahun 2000. Ia memiliki lebih dari 1000 karyawan yang tersebar di seluruh penjuru negeri. 

Walaupun telah menjadi menjadi perusahaan yang cukup besar, Jaya Jaya Maju masih cukup kesulitan dalam mengelola karyawan. Hal ini berimbas tingginya attrition rate (rasio jumlah karyawan yang keluar dengan total karyawan keseluruhan) hingga lebih dari 10%.

Untuk mencegah hal ini semakin parah, manajer departemen HR ingin meminta bantuan Anda mengidentifikasi berbagai faktor yang mempengaruhi tingginya attrition rate tersebut. Selain itu, ia juga meminta Anda untuk membuat business dashboard untuk membantunya memonitori berbagai faktor tersebut. Selain itu, mereka juga telah menyediakan dataset yang dapat Anda unduh melalui tautan berikut: [Jaya Jaya Maju](https://github.com/dicodingacademy/dicoding_dataset/tree/main/employee).

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

**Kondisi dan karakteristik Dataset:**
- Jumlah data: 1.470 baris (record)
- Jumlah fitur: 34 fitur + 1 target (Attrition)
- Tipe data: kombinasi antara numerik, kategorikal, dan biner
- Kondisi: Data bersih, namun memerlukan encoding untuk fitur kategorikal sebelum digunakan dalam model machine learning.
- Target variabel: Attrition (0 = Stay, 1 = Resign)

## 📂 Data Dictionary
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
2. **Gradient Boosting**
- Kelebihan:
    - Salah satu algoritma ensemble terbaik untuk menangani masalah klasifikasi dan regresi.
    - Cenderung memberikan hasil yang lebih akurat dibanding model-tree lainnya dengan mengoptimalkan prediksi secara iteratif.
    - Mampu menangani data dengan noise dan outlier lebih baik.
- Kekurangan:
    - Lebih lambat dalam training dibandingkan dengan Random Forest, terutama untuk dataset besar.
    - Rentan terhadap overfitting jika tidak dituning dengan baik.
    - Model bisa menjadi lebih kompleks dan sulit untuk diinterpretasi karena iterasi yang banyak.
3. **Neural Network**
- Kelebihan:
    - Mampu menangkap pola kompleks dan relasi non-linear dalam data.
    - Bisa bekerja dengan baik jika diberi data yang besar dan beragam.
    - Fleksibel dalam arsitektur (jumlah layer, neuron, aktivasi).
- Kekurangan:
    - Rentan overfitting jika data terlalu sedikit.
    - Memerlukan proses training yang lama, terutama dengan banyak layer.
    - Sulit diinterpretasi dibanding model lainnya.

__Perbandingan dari 3 algoritma yang dipilih:__
| Model             | Accuracy | Precision | Recall | F1-Score |
|------------------|----------|-----------|--------|----------|
| Random Forest     | 0.7999   | 0.7140    | 0.9983 | 0.8326   |
| Gradient Boosting | 0.8003   | 0.7139    | 1.0000 | 0.8331   |
| Neural Network    | 0.7927   | 0.7102    | 0.9866 | 0.8259   |

- Model Terbaik: __Gradient Boosting__
Alasan pemilihan:
    - F1-score tertinggi (0.8331) menunjukkan keseimbangan terbaik antara precision dan recall.
    - Recall sempurna (1.0) menandakan tidak ada false negative—semua risiko berhasil terdeteksi.
    - Meskipun akurasi tidak jauh berbeda dari Random Forest, hasil akhir menunjukkan Gradient Boosting sebagai yang paling konsisten dan presisi dalam konteks dataset ini.

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

## Conclusion
Berdasarkan hasil pengujian, **Model Gradient Boosting** menunjukkan performa terbaik secara keseluruhan, terutama dari sisi recall dan F1-Score. Ini berarti model tersebut sangat baik dalam menangkap semua kasus peminjam yang disetujui (true positive) dan menjaga keseimbangan antara precision dan recall.

Relevansi Metrik terhadap Konteks
Dalam konteks persetujuan pinjaman, recall menjadi metrik yang sangat penting karena:
- Kita tidak ingin melewatkan peminjam yang sebenarnya layak mendapatkan pinjaman (false negative).
- Model harus lebih toleran terhadap false positive daripada false negative, karena menyaring calon nasabah potensial lebih baik daripada kehilangan mereka sama sekali.
Namun demikian, precision juga harus dipertimbangkan agar bank tidak terlalu banyak memberikan pinjaman pada peminjam yang seharusnya ditolak.




