# **Domain Proyek: Prediksi Suhu Air Sungai OYO Gunungkidul Menggunakan LSTM**

#### **Latar Belakang**

Perubahan suhu air di berbagai badan air, seperti sungai atau kolam, sangat dipengaruhi oleh faktor lingkungan seperti suhu udara dan kelembapan. Suhu air yang tidak terpantau dengan baik dapat berdampak negatif pada ekosistem perairan dan bahkan bisa mengganggu sistem irigasi atau pengolahan air.

Prediksi suhu air secara akurat sangat penting untuk membantu pengelolaan sumber daya air yang lebih efisien. Dengan berkembangnya teknologi IoT dan analisis data berbasis machine learning, model prediksi berbasis data historis dapat memberikan solusi untuk memantau dan memprediksi suhu air dengan lebih efektif.

#### **Masalah yang Dihadapi**

Masalah utama yang dihadapi adalah kurangnya sistem pemantauan suhu air yang otomatis dan akurat, terutama dalam situasi di mana data suhu air hanya tersedia pada interval waktu tertentu. Solusi berbasis model deep learning, seperti Long Short-Term Memory (LSTM), bisa menawarkan pendekatan yang lebih efisien untuk memprediksi suhu air berdasarkan data historis.

#### **Referensi**

Beberapa studi sebelumnya menunjukkan bahwa model LSTM efektif dalam memprediksi deret waktu di berbagai aplikasi, termasuk prediksi suhu air. Misalnya, dalam penelitian oleh [Zhang et al. (2020)](https://www.researchgate.net/publication/343827541) yang mengaplikasikan LSTM untuk prediksi suhu air di badan air.

--------------------------------------------------

# **Business Understanding**

#### **Problem Statements**

Masalah utama yang dihadapi adalah ketidakmampuan untuk memprediksi suhu air secara akurat berdasarkan faktor-faktor yang mempengaruhinya, seperti suhu udara dan kelembapan. Hal ini dapat menghambat pengelolaan sumber daya air dan berisiko terhadap kesehatan ekosistem perairan. Solusi untuk masalah ini dibutuhkan untuk menyediakan informasi prediksi suhu air yang lebih tepat, memungkinkan pengambilan keputusan yang lebih baik dalam pengelolaan dan pemantauan suhu air di berbagai badan air.

#### **Goals**

Tujuan dari proyek ini adalah untuk membangun sistem prediksi suhu air yang akurat berdasarkan data suhu udara, kelembapan, dan waktu. Sistem ini akan menggunakan model berbasis deep learning, seperti LSTM, untuk memprediksi suhu air di masa depan dengan menggunakan data historis. Tujuan utama adalah mencapai model yang memiliki kinerja prediksi yang baik dengan metrik evaluasi yang terukur.

#### **Solution Statements**

1. **Menggunakan Model LSTM untuk Prediksi Suhu Air**
   LSTM dipilih karena kemampuannya dalam menangani data deret waktu dan mempelajari ketergantungan jangka panjang antara variabel-variabel yang mempengaruhi suhu air, seperti suhu udara dan kelembapan. Model LSTM akan dilatih dengan data historis untuk memprediksi suhu air yang akan datang.

   **Metrik Evaluasi:** MAE (Mean Absolute Error), RMSE (Root Mean Squared Error), R² (R-squared).
   Target: Mencapai R² di atas 0.8 pada data testing.

2. **Hyperparameter Tuning untuk Meningkatkan Kinerja Model LSTM**
   Untuk meningkatkan akurasi model, hyperparameter tuning akan dilakukan pada model LSTM, seperti jumlah lapisan, jumlah unit pada setiap lapisan, learning rate, dan batch size. Dengan melakukan optimasi terhadap hyperparameter, diharapkan dapat diperoleh model yang lebih baik dan lebih optimal.

   **Metrik Evaluasi:** MAE, MSE (Mean Squared Error), RMSE.
   Target: Mengurangi RMSE dan MSE, serta meningkatkan R² dibandingkan baseline model.

--------------------------------------------------

# **Data Understanding**

#### **Jumlah dan Kondisi Data**

Data yang digunakan dalam proyek ini terdiri dari sejumlah sampel yang berfokus pada variabel yang mempengaruhi suhu air. Dataset ini mencakup beberapa kolom yang mewakili kondisi lingkungan, yaitu suhu udara, kelembapan, dan waktu numerik. Dataset ini terdiri dari 1000 sampel data, yang meliputi informasi suhu udara, kelembapan, dan suhu air pada waktu tertentu. Setiap sampel menggambarkan satu titik pengamatan dalam periode waktu yang berkelanjutan.

#### **Tautan Sumber Data**

Data yang digunakan dalam proyek ini berasal dari data pribadi dimana saya melakukan pengambilan data dengan sensor dulu waktu tugas kuliah.

#### **Variabel atau Fitur pada Data**

Berikut adalah deskripsi mengenai setiap variabel yang terdapat dalam dataset:

1. **Suhu Udara**

   * Tipe: Numerik (dalam derajat Celcius)
   * Deskripsi: Mengukur suhu udara pada waktu tertentu. Suhu udara yang lebih tinggi cenderung meningkatkan suhu air, sedangkan suhu yang lebih rendah cenderung menurunkannya.

2. **Kelembapan (Humidity)**

   * Tipe: Numerik (dalam persentase)
   * Deskripsi: Menunjukkan tingkat kelembapan di udara yang berpotensi mempengaruhi suhu air. Kelembapan yang tinggi dapat memperlambat proses penguapan, yang berhubungan dengan suhu air.

3. **Waktu Numerik**

   * Tipe: Numerik (dalam satuan waktu)
   * Deskripsi: Representasi numerik dari waktu yang digunakan untuk mengurutkan data berdasarkan urutan waktu pengamatan. Variabel ini penting untuk mendeteksi pola jangka panjang atau musiman dalam suhu air.

4. **Suhu Air (Target)**

   * Tipe: Numerik (dalam derajat Celcius)
   * Deskripsi: Variabel yang diprediksi dalam proyek ini. Suhu air dipengaruhi oleh suhu udara dan kelembapan, dan merupakan target utama dalam model prediksi.

#### **Eksplorasi Data (Exploratory Data Analysis - EDA)**

Untuk memahami lebih lanjut mengenai data yang digunakan, beberapa tahapan eksplorasi data dilakukan sebagai berikut:

1. **Distribusi Data**
   Melihat distribusi setiap fitur yang ada, terutama suhu udara, kelembapan, dan suhu air, sangat penting untuk memeriksa apakah data terdistribusi secara merata atau ada pencilan yang bisa memengaruhi hasil prediksi.

2. **Korelasi Antar Fitur**
   Melakukan analisis korelasi untuk memahami hubungan antar fitur yang ada dalam dataset. Misalnya, apakah suhu udara memiliki korelasi yang kuat dengan suhu air. Korelasi ini sangat penting dalam membangun model prediksi yang efektif.

3. **Pemeriksaan Nilai yang Hilang (Missing Values)**
   Memeriksa apakah ada nilai yang hilang dalam dataset, karena nilai yang hilang dapat mengganggu performa model jika tidak ditangani dengan baik.

4. **Tren Data**
   Melihat tren waktu dari suhu udara, kelembapan, dan suhu air untuk memahami bagaimana pola data berubah seiring waktu. Ini membantu dalam mengetahui apakah ada perubahan musiman atau tren jangka panjang yang dapat dipertimbangkan dalam model prediksi.

#### **Kesimpulan Awal dari EDA**

Dari hasil eksplorasi data, dapat disimpulkan bahwa suhu udara dan kelembapan memiliki hubungan yang signifikan dengan suhu air. Visualisasi korelasi menunjukkan adanya hubungan linear yang kuat antara suhu udara dan suhu air, yang dapat dimanfaatkan untuk membuat prediksi yang akurat. Selain itu, tren waktu menunjukkan adanya pola musiman yang perlu diperhatikan dalam analisis lebih lanjut. Tahap eksplorasi ini memberikan gambaran awal yang berguna untuk membangun model prediksi yang lebih akurat.

--------------------------------------------------

# **Data Preparation**

Pada tahapan ini, beberapa teknik data preparation diterapkan untuk memastikan data siap digunakan dalam model prediksi. Berikut adalah langkah-langkah yang dilakukan:

1. **Scaling atau Standariasi Data**

   * Teknik: standarisasi data
   * Proses: Data pada fitur seperti suhu udara, kelembapan, dan waktu numerik dinormalisasi menggunakan teknik standarisasi untuk mengubah nilai-nilai menjadi rentang antara 0 dan 1. Hal ini penting untuk algoritma LSTM yang sensitif terhadap skala data.
   * Alasan: standarisasi memastikan bahwa setiap fitur berada pada skala yang sama, yang mempercepat konvergensi model dan meningkatkan akurasi prediksi.

2. **Membuat Sequence untuk LSTM**

   * Teknik: Create Sequences
   * Proses: Data diubah menjadi format yang cocok untuk model LSTM dengan membuat sequence berukuran waktu tertentu (time steps). Setiap sequence mewakili nilai-nilai fitur dalam jangka waktu tertentu untuk memprediksi suhu air pada waktu berikutnya.
   * Alasan: LSTM memerlukan input dalam bentuk urutan waktu (sequences) untuk belajar pola temporal dalam data, sehingga format ini diperlukan untuk memberi konteks pada model.

3. **Pembagian Data (Train-Test Split)**

   * Teknik: Train-Test Split (80%-20%)
   * Proses: Data dibagi menjadi data pelatihan (training) dan data pengujian (testing) dengan proporsi 80%-20%. Data pelatihan digunakan untuk melatih model, sementara data pengujian digunakan untuk mengevaluasi performa model.
   * Alasan: Pembagian data ini penting untuk menghindari overfitting dan memastikan bahwa model dapat diuji pada data yang belum pernah dilihat sebelumnya.

#### **Kesimpulan**

Data preparation ini memastikan bahwa data siap untuk digunakan dalam model LSTM dengan skala yang konsisten dan dalam format yang sesuai untuk prediksi berbasis urutan waktu. Teknik-teknik tersebut penting untuk meningkatkan kualitas model dan mempercepat proses pelatihan.

--------------------------------------------------

# **Modeling**

Pada tahapan ini, kami membangun model menggunakan algoritma Long Short-Term Memory (LSTM) untuk memprediksi suhu air berdasarkan fitur suhu udara, kelembapan, dan waktu numerik. Berikut adalah proses dan parameter yang digunakan dalam pembuatan model:

#### **Proses Pemodelan:**

1. **Membangun Model LSTM**

   * **Input Layer**: Model menerima input berupa data urutan waktu (sequences) dengan bentuk `(samples, time_steps, features)`.
   * **Lapisan LSTM**:

     * Lapisan pertama LSTM dengan 128 unit dan aktivasi 'relu'. `return_sequences=True` digunakan karena kita akan menambahkan lapisan LSTM berikutnya.
     * Lapisan kedua LSTM dengan 64 unit dan aktivasi 'relu'.
     * Lapisan ketiga LSTM dengan 32 unit dan aktivasi 'relu'.
   * **Dropout**: Ditambahkan setelah setiap lapisan LSTM untuk menghindari overfitting dengan tingkat dropout 0.3.
   * **Output Layer**: Lapisan Dense untuk memprediksi suhu air.
   * **Kompilasi**: Menggunakan optimizer 'adam' dan loss function 'mse' (Mean Squared Error), karena model ini berfokus pada regresi.

2. **Hyperparameter Tuning**
   Untuk meningkatkan performa model, kami melakukan tuning pada beberapa parameter:

   * **Jumlah unit LSTM**: Menambahkan lebih banyak unit LSTM dapat meningkatkan kemampuan model dalam menangkap pola yang lebih kompleks, tetapi juga berisiko menyebabkan overfitting.
   * **Dropout Rate**: Tingkat dropout diatur untuk mencegah overfitting dengan mengurangi kompleksitas model.
   * **Batch Size**: Mengatur ukuran batch untuk melatih model dengan efisiensi memori yang lebih baik.
   * **Epochs**: Jumlah epoch diatur agar model dapat belajar cukup lama tanpa mengalami overfitting (dengan menggunakan EarlyStopping).

#### **Kelebihan dan Kekurangan LSTM:**

* **Kelebihan:**

  * LSTM sangat efektif untuk data urutan waktu (time series), sehingga cocok untuk memprediksi suhu air berdasarkan suhu udara, kelembapan, dan waktu.
  * Mampu mengingat pola jangka panjang dalam data, sehingga ideal untuk masalah prediksi yang bergantung pada data historis.
* **Kekurangan:**

  * LSTM lebih lambat untuk pelatihan dibandingkan model yang lebih sederhana seperti regresi linier atau model pohon keputusan, terutama untuk dataset besar.
  * Memerlukan banyak data untuk mempelajari pola yang benar, dan terlalu sedikit data dapat menyebabkan model overfitting.

#### **Improvement dengan Hyperparameter Tuning:**

Setelah model dasar dibangun, beberapa langkah perbaikan dilakukan untuk meningkatkan performa model, di antaranya:

1. **Meningkatkan Jumlah Unit LSTM**: Menggunakan lebih banyak unit LSTM (misalnya, 128 unit) untuk menangkap hubungan yang lebih kompleks dalam data.
2. **Mengubah Tingkat Dropout**: Meningkatkan atau menurunkan tingkat dropout untuk mengontrol overfitting.
3. **Menyesuaikan Batch Size dan Epochs**: Mencari batch size yang optimal dan menentukan jumlah epoch yang cukup untuk mencegah model berhenti terlalu awal atau melanjutkan terlalu lama.

#### **Evaluasi Model:**

Setelah melatih model, evaluasi dilakukan dengan menggunakan metrik seperti MAE (Mean Absolute Error), MSE (Mean Squared Error), RMSE (Root Mean Squared Error), dan R² untuk mengukur seberapa baik model dalam memprediksi suhu air pada data pengujian.

#### **Kesimpulan:**

LSTM dipilih sebagai algoritma utama karena kemampuannya dalam menangani data sekuensial dan memprediksi suhu berdasarkan data historis. Proses improvement dengan hyperparameter tuning bertujuan untuk mengoptimalkan model dan meningkatkan akurasi prediksi, sementara evaluasi menggunakan metrik regresi memastikan bahwa model memberikan hasil yang memadai.

--------------------------------------------------

### **Evaluation**

Pada tahap evaluasi, kami menggunakan beberapa metrik untuk mengukur kinerja model dalam memprediksi suhu air berdasarkan data yang diberikan. Metrik yang dipilih relevan dengan tugas regresi yang kami lakukan, dimana tujuannya adalah untuk memprediksi nilai kontinu, dalam hal ini suhu air.

#### **Metrik Evaluasi yang Digunakan:**

1. **Mean Absolute Error (MAE)**
   MAE mengukur rata-rata dari selisih absolut antara nilai prediksi dan nilai aktual. Metrik ini sangat berguna untuk memahami seberapa besar rata-rata kesalahan prediksi model dalam unit yang sama dengan data asli (suhu air dalam derajat). Formula MAE adalah:

   <img width="349" alt="image" src="https://github.com/user-attachments/assets/b0c26a3c-7bbb-4938-bfc9-3efcb8f161a9" />

   Dimana:

   * $n$ adalah jumlah sampel.
   * $y_{\text{prediksi}}$ adalah nilai yang diprediksi oleh model.
   * $y_{\text{aktual}}$ adalah nilai yang sebenarnya (ground truth).

   **Interpretasi**: MAE yang lebih rendah menunjukkan bahwa model menghasilkan prediksi yang lebih akurat, dengan selisih kesalahan yang lebih kecil.

2. **Mean Squared Error (MSE)**
   MSE mengukur rata-rata dari kuadrat selisih antara nilai prediksi dan nilai aktual. Metrik ini memberikan penalti yang lebih besar untuk kesalahan yang lebih besar, sehingga lebih sensitif terhadap outlier. Formula MSE adalah:

   <img width="304" alt="image" src="https://github.com/user-attachments/assets/a0a8fb22-2670-4463-8ff5-92ebc20fd44c" />

   **Interpretasi**: MSE yang lebih rendah menunjukkan bahwa model lebih akurat dan memiliki kesalahan prediksi yang lebih kecil.

3. **Root Mean Squared Error (RMSE)**
   RMSE adalah akar kuadrat dari MSE. RMSE memberikan gambaran yang lebih jelas tentang seberapa besar kesalahan prediksi model dalam unit yang sama dengan data asli (suhu air dalam derajat). Formula RMSE adalah:

   <img width="212" alt="image" src="https://github.com/user-attachments/assets/22ba4a4d-26c7-49cf-92e6-4fb9f3be52a6" />

   **Interpretasi**: RMSE yang lebih rendah menunjukkan model yang lebih baik, karena RMSE memperhitungkan kesalahan besar dengan cara yang lebih kuat daripada MAE.

4. **R-squared (R²)**
   R² adalah ukuran yang menunjukkan seberapa baik model menjelaskan variasi dalam data. R² dihitung dengan membandingkan varians dari prediksi model dengan varians dari data asli. Formula R² adalah:

   <img width="335" alt="image" src="https://github.com/user-attachments/assets/09d29e0d-75f5-4f50-a985-6e793f32f770" />

   Dimana $\bar{y}$ adalah nilai rata-rata dari data aktual.

   **Interpretasi**: R² berkisar antara 0 dan 1, dengan nilai yang lebih tinggi menunjukkan model yang lebih baik dalam menjelaskan variasi data. Nilai R² yang mendekati 1 menunjukkan bahwa model mampu menjelaskan sebagian besar variasi dalam data.

#### **Hasil Proyek Berdasarkan Metrik Evaluasi:**

Pada hasil model yang telah dilatih, berikut adalah metrik evaluasi yang diperoleh:

* **Training MAE**: 0.0899

* **Training MSE**: 0.0220

* **Training RMSE**: 0.1483

* **Training R²**: 0.8296

* **Testing MAE**: 0.0969

* **Testing MSE**: 0.0236

* **Testing RMSE**: 0.1537

* **Testing R²**: 0.8025

**Interpretasi Hasil:**

* MAE dan RMSE yang relatif kecil menunjukkan bahwa model menghasilkan prediksi yang cukup akurat, dengan kesalahan rata-rata dan kesalahan kuadrat yang kecil.
* Nilai R² yang lebih besar dari 0.8 pada data pelatihan dan pengujian menunjukkan bahwa model mampu menjelaskan sebagian besar variabilitas dalam suhu air yang diprediksi, meskipun masih ada ruang untuk perbaikan.
* Nilai MSE dan RMSE yang rendah menunjukkan bahwa model ini bekerja dengan baik dan menghasilkan prediksi yang sangat dekat dengan nilai aktual, terutama di data pelatihan.

#### **Kesimpulan:**

Berdasarkan hasil evaluasi, model LSTM yang dibangun dapat memberikan prediksi yang cukup akurat terhadap suhu air. Metrik evaluasi menunjukkan kinerja model yang baik dengan kesalahan yang relatif kecil pada data pelatihan dan pengujian. Metrik seperti MAE, MSE, RMSE, dan R² memberikan gambaran yang jelas mengenai sejauh mana model dapat menangani permasalahan prediksi suhu air berdasarkan data sekuensial.
