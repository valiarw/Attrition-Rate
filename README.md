# Proyek Akhir: Menyelesaikan Permasalahan Attrition Rate di Perusahaan Jaya Jaya Maju

## Business Understanding
Jaya Jaya Maju merupakan perusahaan yang cukup besar. Namun, saat ini perusahaan menghadapi tantangan serius berupa meningkatnya *attrition rate* (tingkat karyawan keluar/resign) yang mencapai lebih dari 10%. Hal ini bukan kondisi normal dan berpotensi merugikan perusahaan karena biaya rekrutmen dan pelatihan karyawan baru (*training*) sangatlah mahal.
Untuk menjaga stabilitas operasional dan efisiensi biaya, departemen HR perlu memahami pola di balik fenomena ini. Saat ini, perusahaan belum memiliki alat yang efektif untuk memonitor faktor penyebab utama *resign* maupun sistem untuk memprediksi karyawan mana yang berpotensi keluar di masa depan.

### Permasalahan Bisnis
Berdasarkan latar belakang tersebut, berikut adalah permasalahan bisnis utama yang akan diselesaikan:
1.  **Ketidaktahuan Faktor Penyebab:** Perusahaan belum mengetahui secara pasti faktor dominan (apakah gaji, jam kerja, atau lingkungan) yang memicu tingginya angka *resign*.
2.  **Risiko Biaya & Produktivitas:** Tingginya *turnover* karyawan meningkatkan biaya operasional rekrutmen dan menurunkan produktivitas tim.
3.  **Absennya Sistem Deteksi Dini:** Belum ada sistem monitoring maupun model prediktif yang dapat memberikan peringatan dini kepada HR mengenai karyawan yang berisiko tinggi untuk keluar.

### Cakupan Proyek
Proyek ini mencakup serangkaian langkah analisis data dan pengembangan sistem untuk menjawab permasalahan di atas:
1.  **Exploratory Data Analysis (EDA):** Menganalisis data historis untuk mengidentifikasi pola dan korelasi antara variabel (seperti *OverTime*, *Income*, *Age*) dengan keputusan *resign*.
2.  **Data Preparation:** Melakukan pembersihan data, *undersampling* untuk menangani ketidakseimbangan kelas, serta *feature engineering*.
3.  **Machine Learning Modeling:** Membangun dan membandingkan performa tiga algoritma klasifikasi (Random Forest, Logistic Regression, dan Neural Network) untuk memprediksi karyawan yang berpotensi *resign*.
4.  **Business Dashboard:** Membuat dashboard interaktif berbasis Looker Studio untuk memantau metrik HR secara *real-time*.

### Persiapan
**Sumber data:**
Dataset yang digunakan dalam proyek ini adalah data karyawan yang dapat diakses melalui tautan berikut:
[Employee_Data.csv](https://github.com/dicodingacademy/dicoding_dataset/blob/main/employee/employee_data.csv).
Dataset ini terdiri dari 1.470 baris dan 35 fitur, mencakup informasi demografis, kepuasan kerja, dan status *attrition*. Variabel target adalah `Attrition` (0 = Stay, 1 = Resign).

**Setup environment:**
Jika Anda ingin menjalankan kode analisis ini di lokal atau Google Colab, ikuti langkah berikut:
1. Clone repository ini:
   ```bash
   git clone https://github.com/valiarw/Attrition-Rate.git
   
2. Install library yang dibutuhkan:
   ```bash
   pip install -r requirements.txt

## Business Dashboard
Untuk memudahkan tim HR dalam memonitor kondisi karyawan dan mengambil keputusan berbasis data, telah dibuat sebuah Business Dashboard interaktif.
Dashboard dapat diakses melalui link berikut: 👉 [Lihat Dashboard HR Attrition di Looker Studio](https://lookerstudio.google.com/reporting/230f22f5-7948-426b-8429-e0382d2ac5c4).

Fitur Utama Dashboard:
- Overview: Menampilkan total karyawan, tingkat attrition saat ini, dan jumlah karyawan aktif.
- Risk Analysis: Visualisasi faktor-faktor risiko utama seperti pengaruh Lembur (OverTime) dan Gaji (Monthly Income) terhadap keputusan resign.
- Demographics: Sebaran karyawan yang keluar berdasarkan Usia, Gender, dan Departemen.

## Conclusion
Berdasarkan hasil analisis data dan evaluasi model Machine Learning, berikut adalah kesimpulan dari proyek ini:
1. Faktor Utama Penyebab Resign: Analisis menunjukkan bahwa keputusan karyawan untuk keluar didorong oleh faktor spesifik, yaitu:
  - Overtime (Lembur): Karyawan yang sering lembur memiliki tingkat attrition jauh lebih tinggi.
  - Monthly Income: Terdapat korelasi negatif kuat antara gaji dan attrition. Karyawan dengan gaji di bawah rata-rata (terutama level Junior) lebih rentan keluar.
  - Age & Job Role: Karyawan muda (<30 tahun) dan posisi entry-level (seperti Sales Representative & Lab Technician) memiliki turnover rate tertinggi.
2. Performa Model Prediksi: Dari tiga model yang diuji, Random Forest Classifier terpilih sebagai model terbaik (Champion Model).
3. Akurasi & F1-Score: Mencapai 95%, jauh mengungguli Logistic Regression (73%) dan Neural Network (88%).
Keunggulan: Random Forest mampu menangkap pola hubungan non-linear yang kompleks dalam data karyawan Jaya Jaya Maju, menjadikannya alat prediksi yang sangat andal untuk mendeteksi potensi resign.

### Rekomendasi Action Items (Optional)
Berdasarkan temuan di atas, berikut adalah rekomendasi tindakan strategis bagi perusahaan untuk menekan angka attrition:
1. Evaluasi Struktur Gaji (Salary Adjustment): Lakukan peninjauan ulang standar gaji khusus untuk posisi Sales Representative dan Laboratory Technician, karena gap pendapatan mereka terlalu jauh dibandingkan level di atasnya.
2. Program Retensi Junior: Buat jalur karir (career path) yang jelas dan program pengembangan diri untuk karyawan usia 20-30 tahun agar mereka melihat masa depan jangka panjang di perusahaan.
3. Manajemen Beban Kerja: Tinjau kembali kebijakan lembur (OverTime). Pastikan beban kerja terdistribusi merata atau berikan kompensasi yang sepadan untuk mencegah kelelahan (burnout).
4. Fokus Penanganan: Alokasikan sumber daya retensi HR untuk membenahi departemen Sales & R&D, karena departemen ini memiliki jumlah kasus resign tertinggi dibandingkan departemen lain.
