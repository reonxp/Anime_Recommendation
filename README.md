# Laporan Proyek Machine Learning - Bagus Dzakiy Rahman Saputra

## Domain Proyek

Proyek ini bertujuan untuk membangun sistem rekomendasi anime untuk memudahkan pengguna memilih tontonan anime sesuai dengan preferensi mereka. Dengan menggunakan sistem rekomendasi, pengguna tidak akan merasa kesulitan dalam menentukan anime yang ingin mereka tonton, meningkatkan pengalaman menonton mereka.

Sistem rekomendasi sangat penting dalam konteks platform streaming dan bisnis digital, karena dapat meningkatkan engagement pengguna dan membuat mereka lebih lama berada di platform. Dengan memanfaatkan data rating dan genre dari berbagai anime, sistem ini diharapkan memberikan rekomendasi yang relevan dan menarik.

Proyek ini bertujuan untuk merancang, membangun, dan membandingkan dua jenis sistem rekomendasi anime berbeda:

- **Content-Based Filtering (CBF)**: Merekomendasikan anime berdasarkan kemiripan konten, dalam hal ini adalah genre.
- **Collaborative Filtering (CF)**: Merekomendasikan anime berdasarkan pola selera dari komunitas pengguna.

Dengan membangun kedua model ini, kita dapat memahami karakteristik, kelebihan, serta kekurangan masing-masing pendekatan dalam memberikan rekomendasi yang relevan dan personal.

**Rubrik/Kriteria Tambahan (Opsional):**  
- Penting untuk menganalisis dan membangun sistem rekomendasi dalam domain hiburan seperti anime guna mengatasi masalah choice overload, di mana pengguna dihadapkan pada puluhan ribu pilihan judul. Sistem yang efektif dapat secara signifikan meningkatkan pengalaman dan kepuasan pengguna, yang pada akhirnya mendorong retensi dan keterlibatan (engagement) pada platform digital. Dari perspektif bisnis, sistem rekomendasi adalah alat vital untuk personalisasi layanan, meningkatkan durasi tontonan, dan menyajikan konten yang relevan untuk mempertahankan basis pengguna.

- Penelitian dan praktik industri di bidang sistem rekomendasi telah lama berpusat pada dua paradigma utama. Pendekatan pertama, Content-Based Filtering, merekomendasikan item berdasarkan kemiripan atributnya, sebuah metode yang efektif untuk transparansi dan menangani item baru (Ricci et al., 2011). Namun, metode ini memiliki kelemahan yaitu kecenderungan menciptakan "gelembung filter" (filter bubble) dan kesulitan memberikan rekomendasi yang beragam atau mengejutkan. Pendekatan kedua, Collaborative Filtering, yang dipopulerkan oleh sistem seperti Amazon (Linden et al., 2003), merekomendasikan item berdasarkan pola perilaku dari pengguna dengan selera serupa. Metode ini, terutama yang berbasis faktorisasi matriks seperti SVD, terbukti sangat kuat dalam memberikan rekomendasi personal dan serendipitas, meskipun memiliki tantangan pada masalah "cold start" untuk pengguna atau item baru.

- **Linden, G., Smith, B., & York, J. (2003)**. "Amazon.com Recommendations: Item-to-Item Collaborative Filtering." *IEEE Internet Computing*, vol. 7, no. 1, pp. 76-80. [Link to Paper](https://www.cs.umd.edu/~samir/498/Amazon-Recommendations.pdf).  
- **Anime Recommendations Dataset**. [Kaggle](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database).  

## Business Understanding

Sistem rekomendasi anime ini berfokus pada memberikan rekomendasi yang relevan berdasarkan data rating yang diberikan oleh pengguna dan fitur anime (seperti genre, tipe, dan rating).

### Problem Statements  

- **Pernyataan Masalah 1**: Bagaimana membangun sistem rekomendasi yang mampu memberikan saran anime berdasarkan rating pengguna dan genre yang mereka sukai? 
  
- **Pernyataan Masalah 2**: Apa yang dapat kita pelajari dari data rating pengguna untuk mengoptimalkan rekomendasi yang diberikan oleh sistem?

### Goals  

Tujuan dari analisis ini adalah:  
- **Jawaban untuk Pernyataan Masalah 1**: Mengembangkan model sistem rekomendasi menggunakan algoritma berbasis Collaborative Filtering dan Content-Based Filtering, yang memanfaatkan data rating pengguna dan metadata anime seperti genre.
  
- **Jawaban untuk Pernyataan Masalah 2**: Mengidentifikasi pola dalam data rating untuk menemukan faktor-faktor yang mempengaruhi preferensi pengguna, serta mengeksplorasi cara mengoptimalkan algoritma rekomendasi.

### Solution Statements  

Untuk meraih tujuan pengembangan sistem rekomendasi yang efektif, beberapa solusi yang diusulkan adalah: 
- **Menggunakan Dua Algoritma**: Pada tahap ini, dua pendekatan utama yang digunakan untuk membangun sistem rekomendasi adalah Collaborative Filtering dan Content-Based Filtering. Untuk masing-masing metode ini, beberapa algoritma diterapkan untuk mengevaluasi model mana yang memberikan hasil terbaik dalam memberikan rekomendasi anime kepada pengguna.

   **Content-Based Filtering**: Menggunakan Cosine Similarity dan TF-IDF Vectorizer untuk menghitung kemiripan antara anime berdasarkan fitur seperti genre, tipe, dan rating. Metode ini berguna terutama bagi pengguna dengan preferensi yang lebih eksplisit terkait genre atau tipe anime yang mereka sukai.

   **Collaborative Filtering**: Menggunakan algoritma Singular Value Decomposition (SVD) untuk mencari pola di antara pengguna berdasarkan rating mereka terhadap anime. Dengan demikian, sistem ini dapat menyarankan anime berdasarkan kesamaan preferensi antar pengguna.

- **Hyperparameter Tuning**: Untuk meningkatkan performa model dan memastikan akurasi serta ketahanan sistem rekomendasi, hyperparameter tuning dilakukan pada algoritma SVD. Proses tuning ini menggunakan teknik Grid Search untuk menemukan kombinasi parameter yang optimal. 

- **Evaluasi dengan Metrik**: Untuk menilai kinerja sistem rekomendasi, saya menggunakan beberapa metrik evaluasi yang relevan, seperti Root Mean Squared Error (RMSE) dan Mean Squared Error (MSE). Metrik ini digunakan untuk mengukur seberapa baik model dapat memprediksi rating yang diberikan oleh pengguna terhadap anime yang belum mereka tonton.

   **RMSE**  : Metrik ini mengukur seberapa besar kesalahan antara prediksi dan nilai yang sebenarnya. Semakin kecil nilai RMSE, semakin baik model dalam memberikan rekomendasi yang akurat.
   **MSE**   : Metrik ini digunakan untuk mengukur rata-rata kesalahan kuadrat antara prediksi dan nilai sebenarnya. Nilai MSE yang rendah menunjukkan performa model yang lebih baik.

Dengan menggunakan metode evaluasi yang tepat dan pengoptimalan parameter, diharapkan model yang dikembangkan dapat memberikan rekomendasi yang lebih tepat dan relevan, meningkatkan pengalaman pengguna secara keseluruhan.

## Data Understanding

Dataset yang digunakan berasal dari Anime Dataset di Kaggle dan terdiri dari 2 dataset. Dataset anime.csv memiliki 12.294 baris dengan 7 kolom, dan dataset rating.csv memiliki 7.813.737 baris dengan 3 kolom. Sumber data dapat diunduh dari [Anime Recommendation Dataset](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database).

Selanjutnya berikut adalah variable atau fitur dalam dataset tersebut:  

### Variabel-variabel pada Anime dataset adalah sebagai berikut:

**anime.csv**
- **anime_id**: ID unik anime yang didapatkan dari MyAnimelist.
- **name**: Judul anime.
- **genre**: Genre pada anime (Adventure, Comedy, Romance, dll).
- **type**: Tipe anime (Movie, TV, OVA).
- **episodes**: Jumlah episode dari anime.
- **rating**: Rating anime menurut pengguna dari MyAnimlist (Rentang 0-10).
- **members**: Jumlah member yang memasukkan anime ke list mereka.

**rating.csv**
- **user_id**: ID unik pengguna.
- **anime_id**: Anime yang diberikan peringkat oleh pengguna.
- **rating**: Rating yang diberikan oleh user dalam skala 0-10 (-1 untuk user yang sudah menonton tetapi tidak memberikan rating).

### Missing Value pada Anime Recommendation Dataset adalah sebagai berikut:

**anime.csv**
- **Genre**: Terdapat missing value sebanyak 62 value (Menggunakan .dropna() untuk teknik imputasi).
- **type**: Terdapat missing value sebanyak 25 value (Menggunakan .dropna() untuk teknik imputasi).
- **rating**: Terdapat missing value sebanyak 230 value (Menggunakan .dropna() untuk teknik imputasi).

Sedangkan pada dataset **rating.csv** tidak ada value yang missing.

### Duplicate Value pada Anime recommendation Dataset adalah sebagai berikut

**rating.csv**
Terdapat data duplikat pada dataset rating.csv sebanyak 1 value (Menggunakan .dropna() untuk mengatasi data duplicated).

sedangkat pada dataset **anime.csv** tidak ada value yang terduplikat.

**Rubrik/Kriteria Tambahan (Opsional)**:
Dalam melakukan pemahaman data, beberapa teknik visualisasi data dan exploratory data analysis (EDA) dilakukan, antara lain:  
- **Visualisasi Distribusi Rating**: Membuat histogram untuk memahami distribusi rating pada dataset anime.  
- **Visualisasi 10 Genre Anime Terpopuler**: Menggunakan grafik batang untuk membandingkan genre apa yang paling populer diantara genre lainnya.
- **Visualisasi 10 Top anime dengan rating tertinggi**: Menggunakan grafik batang untuk membandingkan anime apa yang memiliki rating tertinggi.

## Data Preparation

Pada bagian ini, teknik data preparation yang dilakukan adalah sebagai berikut: 

**Rubrik/Kriteria Tambahan (Opsional)**: 

1. **Mengidentifikasi dan Mengisi Nilai Hilang**:  
   - Pada kolom **genre**, **type**, dan **rating** nilai yang hilang dihapus menggunakan teknik .dropna() untuk menjaga konsistensi dari dataset tersebut, dan tidak menimbulkan ambiguitas terhadap informasi sebenarnya.

2. **Menghapus Kolom yang Tidak Relevan**:  
   - Kolom-kolom seperti **type** dan **episodes**, yang tidak menyediakan informasi signifikan untuk analisis, dihapus. Ini tidak hanya menyederhanakan dataset tetapi juga mengurangi kompleksitas model dan meningkatkan performa.  

2. **Mengidentifikasi dan Menghapus Value Duplicate**:
   - Mengidentifikasi nilai pada **rating.csv** yang terdeteksi duplicate dan menghapusnya mengunakan teknik .drop_duplicates() untuk menjaga dataset supaya optimal.

Proses persiapan data sangat krusial untuk menjamin bahwa data tersebut bersih dan siap untuk digunakan dalam analisis dan pemodelan. Tahapan ini berkontribusi pada peningkatan kualitas dan ketepatan model, memungkinkan penemuan pola yang lebih jelas, serta memfasilitasi analisis lebih lanjut.

## Modeling
Pada tahap ini, saya menerapkan dua algoritma machine learning untuk membangun dan mengoptimalkan sistem rekomendasi anime. Algoritma yang digunakan terdiri dari Collaborative Filtering menggunakan Singular Value Decomposition (SVD), serta Content-Based Filtering menggunakan Cosine Similarity dan TF-IDF Vectorizer. Berikut penjelasan mengenai tahapan, parameter yang digunakan, serta kelebihan dan kekurangan dari masing-masing algoritma.

### Content-Based Filtering  

  - Tahapan: Hanya mengambil anime yang memiliki lebih dari 1000 member (Kemungkinan anime dengan member dibawah 1000 adalah anime yang jarang orang-orang lihat). Selanjutnya proses normalisasi fitur genre dengan mengahapus tanda koma(,), spasi pada awal dan akhir genre, dan menerapkan lowercase ke fitur genre, setelah dinormalisasi kemudian digabungkan menjadi satu string. Kemudian vectorisasi menggunakan TF-IDF untuk mengubah value dari genre menjadi nilai matriks. Selanjutnya mehitung menggunakan Cosine Similarity untuk mengukur kemiripan antar vector. Tahapan terakhir adalah membuat model rekomendasi Content-Based Filtering dengan menerapkan beberapa fungsi, salah satunya mengatasi sensitive-case agar user dapat meng-inputkan anime tanpa meneliti cara pengisiannya.
  - Kelebihan: Memberikan rekomendasi yang sangat personal karena langsung didasarkan pada data yang sudah diketahui pengguna (seperti genre atau judul anime yang disukai)
  - Kekurangan: Hanya dapat memberikan rekomendasi berdasarkan kesamaan fitur yang sudah ada dan tidak mempertimbangkan interaksi pengguna lainnya.

### Collaborative Filtering  

  - Tahapan: Mengambil data rating dengan mengecualikan value -1 karena dapat dianggap bahwa user pernah menonton animenya, tetapi tidak memberikan rating. Selanjutnya mengambil sample data sebanyak 500.000 dari 6.337.240 data, untuk efisiensi dalam pemrosesan. Karena kalau menggunakan data asli, Pemrosesan akan memakan waktu yang sangat lama. Setelah melalui proses pengambilan sample, selanjutnya adalah mengubah data ke format surprise agar data dapat diproses menggunakan library surprise. Tahap selanjutnya adalah splitting data dan training data dengan parameter umum. Kemudian melakukan Hyperparameter tuning untuk mendapatkan parameter yang cocok dengan struktur data, kemudian training ulang model menggunakan parameter terbaik. Pada tahap terakhir adalah membuat sistem rekomendasi berbasis Collaborative-Filtering dengan beberapa fungsi untuk memaksimalkan model memberikan rekomendasi.
  - Kelebihan: Mampu memberikan rekomendasi yang unik untuk setiap pengguna berdasarkan riwayat rating mereka, bukan hanya berdasarkan kemiripan konten.
  - Kekurangan: Sangat sulit memberikan rekomendasi untuk pengguna baru (yang belum punya riwayat rating) atau merekomendasikan anime baru (yang belum ada yang memberi rating).
  - Parameter yang digunakan: (n_factors=100, n_epochs=20, random_state=42)

### Proses Improvement dengan Hyperparameter Tuning  

Untuk meningkatkan performa model Collaborative Filtering, saya melakukan hyperparameter tuning pada model SVD menggunakan GridSearchCV dari library scikit-surprise. Proses ini melibatkan:  

1. Menentukan beberapa pilihan nilai untuk parameter-parameter kunci dari algoritma SVD.
2. Melakukan cross-validation (dalam kasus ini, 3-fold) untuk setiap kombinasi parameter dan mencatat performanya berdasarkan metrik RMSE dan MAE.  
3. Memilih kombinasi parameter yang memberikan skor error (RMSE) rata-rata terendah. 

**Parameter Yang Digunakan Pada Hyperparameter Tuning**
   ```"n_factors": [50, 100, 150],```
   ```"n_epochs": [20, 30],```
   ```"lr_all": [0.005, 0.01],```
   ```"reg_all": [0.02, 0.1]```

**Alasan Menggunakan Parameter Tersebut**
   - **n_factors**: Menentukan jumlah faktor laten yang akan dipelajari oleh model. Faktor-faktor ini adalah "sifat" tersembunyi yang ditangkap oleh model dari data rating, misalnya bisa merepresentasikan konsep abstrak seperti "anime dengan cerita kelam" atau "cocok untuk penggemar mecha". Menguji beberapa nilai membantu menemukan kompleksitas model yang pas.
   - **n_epochs**: Mengatur berapa kali algoritma akan berjalan melalui seluruh dataset training. Semakin banyak epoch memberi kesempatan model untuk belajar lebih dalam, tetapi jika terlalu banyak bisa berisiko overfitting (terlalu 'hafal' data training).
   - **lr_all (Learning Rate)**: Mengontrol seberapa besar langkah yang diambil model untuk memperbaiki dirinya sendiri di setiap iterasi. Learning rate yang tepat membantu model menemukan solusi terbaik dengan lebih efisien.
   - **reg_all (Regularization Term)**: Berfungsi sebagai "rem" untuk mencegah model menjadi terlalu kompleks dan overfitting. Parameter ini memberikan pinalti pada nilai faktor yang terlalu besar, mendorong model untuk belajar pola yang lebih general.

### Result
**Result Content-Based Filtering**
![Result Content-Based Filtering](https://github.com/reonxp/Anime_Recommendation/blob/main/documentation/Result%20Content-Based%20Filtering.png?)

Menampilkan output dari rekomendasi anime "Shingeki no Kyojin" dengan genre yang serupa. Menghasilkan output top 10 anime rekomendasi dengan genre yang sama.

**Result Collaborative Filtering**
![Result Collaborative Filtering](https://github.com/reonxp/Anime_Recommendation/blob/main/documentation/Result%20Collaborative%20Filtering.png?)

Menampilkan output 20 anime berdasarkan referensi dari user. Daftar anime ditampilkan dengan urut berdasarkan anime yang paling cocok untuk user.


## Evaluation

Pada tahap ini, dilakukan evaluasi kuantitatif terhadap model Collaborative Filtering untuk mengukur akurasi prediksinya. Metrik yang digunakan adalah RMSE (Root Mean Squared Error) dan MAE (Mean Absolute Error) untuk menilai seberapa dekat tebakan rating model dengan rating asli yang diberikan pengguna.

### Hasil Proyek Berdasarkan Metrik Evaluasi  

Evaluasi kuantitatif dilakukan pada model Collaborative Filtering (SVD) untuk mengukur seberapa akurat model dalam memprediksi rating yang akan diberikan oleh pengguna. Metrik utama yang digunakan adalah:

- **RMSE (Root Mean Squared Error)**: Mengukur rata-rata besarnya kesalahan prediksi, dengan memberikan bobot lebih besar pada kesalahan yang nilainya jauh. Semakin kecil nilainya, semakin baik.
- **MAE (Mean Absolute Error)**: Mengukur rata-rata absolut dari selisih antara rating prediksi dan rating aktual. Metrik ini lebih mudah diinterpretasikan secara langsung.

Setelah melalui proses hyperparameter tuning menggunakan GridSearchCV dengan 3-fold cross-validation, didapatkan hasil performa terbaik sebagai berikut:

| Metrik Evaluasi                  | Skor Terbaik |
| :------------------------------- | :----------- |
| RMSE (Root Mean Squared Error)   | 1.2855       |
| MAE (Mean Absolute Error)        | 1.0078       |

Hasil evaluasi ini menunjukkan bahwa model Collaborative Filtering yang telah dioptimalkan memiliki performa yang solid. Skor RMSE sebesar 1.2855 pada skala rating 1-10 menandakan bahwa secara rata-rata, prediksi rating yang dihasilkan model memiliki selisih sekitar 1.29 poin dari rating yang sebenarnya akan diberikan oleh pengguna.

### Hasil Analisis Terhadap Pernyataan Masalah

**Pernyataan Masalah 1**:
*Bagaimana membangun sistem rekomendasi yang mampu memberikan saran anime berdasarkan rating pengguna dan genre yang mereka sukai?*

Untuk menjawab pernyataan ini, proyek ini mengimplementasikan dua pendekatan model yang berbeda untuk menangani kedua aspek permintaan tersebut secara terpisah:

Untuk aspek **"genre yang mereka sukai"**, diimplementasikan model **Content-Based Filtering**. Model ini bekerja dengan cara:
- Menganalisis dan menormalisasi data genre dari setiap anime.
- Menggunakan TfidfVectorizer untuk mengubah data teks genre menjadi representasi vektor numerik.
- Menghitung Cosine Similarity untuk membangun matriks kemiripan antar semua anime berdasarkan kesamaan genre mereka.
- Hasilnya adalah sebuah sistem yang mampu merekomendasikan anime dengan tema atau konten yang serupa secara efektif.

Untuk aspek **"rating pengguna"**, diimplementasikan model **Collaborative Filtering**. Model ini bekerja dengan cara:
- Menganalisis data historis rating dari seluruh pengguna.
- Menggunakan algoritma SVD (Singular Value Decomposition) untuk mempelajari pola selera tersembunyi (latent factors) dari setiap pengguna dan anime.
- Model kemudian memprediksi rating yang mungkin diberikan seorang pengguna untuk anime yang belum ia tonton, menghasilkan rekomendasi yang sifatnya personal.

**Pernyataan Masalah 2**:
*Apa yang dapat kita pelajari dari data rating pengguna untuk mengoptimalkan rekomendasi yang diberikan oleh sistem?*

Analisis dan pembangunan model Collaborative Filtering memberikan beberapa wawasan kunci untuk proses optimasi:

**Pentingnya Data Rating yang Eksplisit**: Pembelajaran pertama adalah bahwa tidak semua data rating dapat langsung digunakan. Data dengan nilai rating = -1 (yang berarti "ditonton tanpa skor") harus dibersihkan terlebih dahulu. Algoritma seperti SVD memerlukan skor numerik yang jelas (1-10) untuk dapat belajar secara akurat. Tanpa pembersihan ini, pemahaman model terhadap preferensi pengguna akan terdistorsi.

**Kebutuhan Hyperparameter Tuning**: Model dengan parameter default memberikan hasil yang cukup baik (RMSE ~1.31), namun belum optimal. Melalui proses Hyperparameter Tuning menggunakan ```GridSearchCV```, kita belajar bahwa penyesuaian parameter seperti ```n_factors```, ```n_epochs```, dan ```lr_all``` sangat krusial. Proses ini berhasil menurunkan error prediksi model ke RMSE ~1.28, membuktikan bahwa tuning adalah langkah esensial untuk optimasi akurasi.

**Adanya Popularity Bias**: Salah satu pelajaran terpenting adalah bahwa akurasi metrik (RMSE rendah) tidak selalu menjamin pengalaman pengguna yang baik. Ditemukan bahwa model yang telah dioptimalkan sekalipun memiliki kecenderungan kuat untuk merekomendasikan anime yang sangat populer secara universal kepada banyak pengguna yang berbeda. Hal ini mengajarkan kita bahwa untuk mengoptimalkan rekomendasi lebih lanjut, teknik diversifikasi (seperti random sampling dari kandidat teratas) perlu dipertimbangkan untuk menyeimbangkan antara akurasi dan variasi hasil.


### Kesimpulan

Analisis dan pengembangan dalam proyek ini menegaskan bahwa kedua model, **Content-Based Filtering** dan **Collaborative Filtering**, berhasil diimplementasikan dan berfungsi dengan baik untuk tujuan masing-masing dalam memberikan rekomendasi anime. Proyek ini menyoroti pentingnya pemilihan pendekatan berdasarkan kebutuhan dan data yang tersedia.

**Model Content-Based Filtering** terbukti efektif dalam merekomendasikan item berdasarkan kemiripan fitur, dengan kualitas metadata genre sebagai faktor penentu utamanya. Di sisi lain, **model Collaborative Filtering**, setelah melalui proses hyperparameter tuning yang sistematis dan mencapai skor RMSE 1.2849, menunjukkan kapabilitasnya dalam menghasilkan rekomendasi yang dipersonalisasi dengan menganalisis pola interaksi pengguna. Faktor-faktor seperti kualitas data rating dan konfigurasi hyperparameter terbukti memiliki pengaruh signifikan terhadap akurasi prediksinya.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.

