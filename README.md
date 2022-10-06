# Proyek Machine Learning - Safiira Rahmah Linisa

## Project Overview

Indonesia merupakan negara agraris yang mengandalkan pertanian sebagai salah satu sektor matapencaharian terbesar bagi warga negaranya. Tanahnya yang luas dan Letaknya yang berada di wilayah tropis membuat berbagai tanaman tubuh subur di negara kita. Kondisi ini merupakan peluang besar bagi indonesia untuk menjadi negara produsen.

Alpukat merupakan salah satu buah yang banyak digemari masyarakat, tidak hanya di indonesia namun juga seluruh dunia. Berdasarkan data dari _Food and Agriculture Organization (FAO)_ tahun 2019, Indonesia menempati peringkat ke 5 negara penghasil alpukat terbesar di dunia. Ini menunjukkan bahwa sektor pertanian alpukat di Indonesia sudah cukup besar. Namun terkadang terdapat kendala dimana harga dipasaran tidak selalu stabil. Oleh karenanya dibutuhkan sistem yang dapat memprediksi harga alpukat.

Untuk itu sistem prediksi harga alpukat ini dibuat dengan tujuan agar menjadi acuan dan pertimbangan petani Indonesia dalam menetapkan harga ataupun dalam merancang strategi produksi. Dengan perkiraan harga tersebut petani dapat merancang strategi agar tidak mengalami kerugian dan serta meningkatkan keuntungan yang didapat.

## Business Understanding

### Problem Statement

- Dengan dataset yang dimiliki bagaimana cara mengembangkan model _machine learning_ untuk memprediksi harga alpukat?

### Goals

- Membuat model _machine learning_ yang mampu memprediksi harga alpukat dengan baik.

### Solution approach

- Solusi yang diterapkan untuk dalam proyek ini adalah dengan membuat model regresi untuk memprediksi bilangan kontinu yang sesuai dengan permasalahan agar menghasilkan prediksi harga alpukat yang akurat.
- Algoritma yang digunakan untuk menyelesaikan kasus ini adalah sebagai berikut :
  - _K-Nearest Neighbors_
  - _Random Forest_
  - _Boosting_

## Data Understanding

**Informasi Dataset**

Tabel 1. Informasi dataset

| Informasi    | Keterangan                                                            |
| ------------ | --------------------------------------------------------------------- |
| Link         | https://www.kaggle.com/datasets/smokingkrils/avacado-price-prediction |
| Nama Dataset | Avocado Price Prediction                                              |
| Usability    | 7.06                                                                  |
| Jumlah Data  | 18249                                                                 |
| Jumlah Kolom | 14                                                                    |
| Jumlah fitur | 13                                                                    |

Dataset yang saya gunakan merupakan dataset mengenai Avocado atau buah alpukat.
Berikut ini variabel-variable yang terdapat dalam dataset

- Date: Tanggal Observasi
- AveragePrice: Harga Rata-rata satu buah Alpukat
- Total Volume: Jumlah Alpukat yang terjual
- 4046: Total jumlah alpukat terjual dengan PLU 4046
- 4225: Total jumlah alpukat terjual dengan PLU 4046
- 4770: Total jumlah alpukat terjual dengan PLU 4046
- Total Bags: Total jumlah sekantung alpukat
- Small Bags: Kantong/wadah kecil
- Large Bags: Kantong/wadah besar
- XLarge Bags: Kantong/wadah ekstra besar
- type: Jenis alpukat konvensional atau organik
- year: Tahun
- region: Kota atau wilayah observasi

Pada tahap ini juga dilakukan analisis dan exploratory terhadap data.
Berikut ini uraiannya:

- Mengecek informasi pada data

  Tabel 2. Informasi pada Data

  | #   | Column       | Non-Null Count | Dtype   |
  | --- | ------------ | -------------- | ------- |
  | 1   | Date         | 18249 non-null | int64   |
  | 2   | AveragePrice | 18249 non-null | object  |
  | 3   | Total Volume | 18249 non-null | float64 |
  | 4   | 4046         | 18249 non-null | float64 |
  | 5   | 4225         | 18249 non-null | float64 |
  | 6   | 4770         | 18249 non-null | float64 |
  | 7   | Total Bags   | 18249 non-null | float64 |
  | 8   | Small Bags   | 18249 non-null | float64 |
  | 9   | Large Bags   | 18249 non-null | float64 |
  | 10  | XLarge Bags  | 18249 non-null | float64 |
  | 11  | type         | 18249 non-null | object  |
  | 12  | year         | 18249 non-null | object  |
  | 13  | region       | 18249 non-null | int64   |

  dtypes: float64(9), int64(2), object(3)
  memory usage: 1.9+ MB

- Mengecek informasi statistik pada data

- Menangani _outlier_ dengan _IQR Methode_

- Univariate Analysis

  - untuk menunjukan hubungan pada suatu fitur.

  ![image](https://user-images.githubusercontent.com/83525234/193973858-f51adc67-2b28-4b95-9b3e-3d9df7403633.png)

  Gambar 1. Histogram Univariate Analysis

- Multivariate Analysis

  - untuk menunjukkan hubungan antara dua atau lebih variabel pada data

  ![image](https://user-images.githubusercontent.com/83525234/193973993-3fb0aa57-11c9-479b-aacf-8a1e923a3c42.png)

  Gambar 2. Histogram Multivariate Analysis

Visualisasi berikut menunjukkan korelasi atau hubungan antara tiap fitur.

![image](https://user-images.githubusercontent.com/83525234/193878390-97f5133d-54af-4753-b254-86cd0ec8683f.png)

Gambar 3. Matrik Korelasi Untuk Fitur Numerik

## Data Preparation

**Mengatasi Missing Value**

Tujuan dari proses _missing value_ yaitu agar dataset menjadi bersih dari fitur yang tidak dibutuhkan, maupun yang valuenya kosong karena dapat menimbulkan hasil akurasi yang kurang baik.

- Mendeteksi fitur yang memiliki value 0

  ![image](https://user-images.githubusercontent.com/83525234/193991693-123e148b-376d-45b6-af34-84434a9f8dfd.png)
  Gambar 4. Fitur _Total Bags_ dengan _value_ 0

  Berdasarkan data diatas dapat dilihat bahwa terdapat fitur yang memiliki missing value. Data diatas sangat menarik karena menunjukkan hubungan antara fitur _Total Bags_, _Small Bags_ serta _Large Bags_.

- Menangani _Missing Value_ dengan menghapus fitur yang bernilai 0

Karena terdapat hubungan value yang bernilai 0 antara fitur _Total Bags_, _Small Bags_ serta _Large Bags_. Maka sampel dengan nilai 0 pada _Total Bags_, _Small Bags_ dan _Large Bags_ akan dihapus.

**Menangani _oulier_**

- Memvisualisasikan data Avocado dengan boxplot untuk mendeteksi _outliers_ pada beberapa fitur numerik.

  ![image](https://user-images.githubusercontent.com/83525234/193988867-ced2a289-4629-43ef-9717-008b591555cd.png)

  Gambar 5. Outlier pada fitur Average Price

  Dari visualisasi tersebut dapat dilihat bahwa terdapat outlier pada fitur _Average Price_. Menggunakan cara yang sama ditemukan pula outlier pada beberapa fitur numerik lain yaitu pada _Total Bags_ dan _Small Bags_.

- Mengatasi _Outlier_ dengan _IQR Method_

  Untuk mengatasi _outlier_ pada proyek ini digunakan teknik _IQR Method_. Cara kerja dari _IQR Method_ yaitu dengan menghapus data yang berada diluar _interquartile range_. Interquartile adalah range diantara kuartil pertama(25%) dan kuartil ketiga(75%).

**Drop data**

Drop data atau menghapus data yang tidak dibutuhkan. Pada proyek ini data yang terdapat beberapa fitur yang dihapus dari dataset.
Untuk fitur numerik XLarge dan year dihapus karena memiliki nilai korelasi yang sangat rendah terhadap model. Sedangkan fitur date, type dan region dihapus karena memiliki type data string sehingga tidak dapat diproses model.
Proses Drop data ini bertujuan agar model dapat dilatih dengan baik untuk memprediksi data dengan hasil prediksi yang memiliki akurasi tinggi. fungsi yang digunakan.

**Split Dataset**

Split dataset yaitu membagi dataset menjadi data _training_ dan data _testing_. Data _training_ digunakan untuk pelatihan model, sedangkan data _testing_ digunakan untuk memvalidasi performa dan akurasi model setelah pelatihan. Untuk pembagian dataset pada proyek ini, saya membaginya menjadi 80% data _training_ dan 20% data _testing_.

Split data harus dilakukan sebelum proses transformasi dan normalisasi. Karena data uji (_testing_) berperan sebagai data baru, kita perlu melakukan semua proses transformasi dalam data latih. Oleh karenanya membagi dataset adalah proses pertama sebelum melakukan transformasi apa pun. Tujuannya adalah agar kita tidak mengotori data uji dengan informasi yang kita dapat dari data latih. Jika melakukan proses normalisasi sebelum training maka berpotensi menimbulkan kebocoran data (_data leakage_).

**Normalisasi**

Normalisasi data merupakan proses membuat variabel-variabel yang ada memiliki rentang nilai yang sama.
Pada kasus ini saya mentransformasi 'x*train' menggunakan fungsi .fit_transform() dari \_library MinMaxScaler*.
MinMax merupakan metode normalisasi yang bersifat linier dengan data aslinya. _Library MinMaxScaler_ melakukan skala dan transformasi pada setiap fitur secara individual sehingga berada dalam rentang yang diberikan pada set pelatihan, _library_ ini memiliki range default antara 0 dan 1. Normalisasi bertujuan agar model dapat mengenali pola-pola pada data sehingga menghasilkan prediksi lebih baik.

## Modeling

Dalam tahap Development model pada studi kasus prediksi harga alpukat ini, Algoritma machine learning yang saya gunakan sebagai solusi untuk memprediksi harga alpukat diantaranya sebagai berikut:

**K-Nearest Neighbor**

Algoritma K-NN merupakan algoritma yang cara kerjanya yaitu membandingkan jarak satu sampel ke sampel pelatihan lain dengan memilih sejumlah k tetangga terdekat. Algoritma KNN menggunakan kemiripan data baru dengan data tetangga terdekat untuk memprediksi nilai dari setiap data yang baru. Dengan kata lain, setiap data baru diberi nilai berdasarkan seberapa mirip titik tersebut dalam set pelatihan. KNN ini dapat digunakan untuk kasus regresi dan klasifikasi. Pada model ini digunakan satu parameter yaitu _n-neighbors_ atau jumlah tetangga. Untuk kasus ini saya menggunakan 5 neighbors.

- Keuntungan

  - sederhana dan mudah dipahami
  - mudah digunakan
  - parameter sedikit

- Kelemahan
  - Jumlah fitur atau dimensi yang besar
  - Memakan waktu lama jika dataset sangat besar
  - Jumlah sampel meningkat secara eksponensial seiring dengan jumlah dimensi.

**Random Forest**

Algoritma random forest merupakan salah satu algoritma supervised learning. Random forest termasuk ke dalam model ensemble group learning. Model ini terdiri dari sekelompok model yang bekerja secara bersama sama untuk menyelesaikan masalah. Pada model ensemble setiap model harus membuat prediksi secara independent, kemudian prediksi dari tiap model ini digabungkan untuk membuat prediksi akhir. Sehingga tingkat keberhasilan akan lebih tinggi dibanding model bekerja sendiri. Algoritma ini digunakan untuk menyelesaikan masalah klasifikasi dan regresi.
Random forest merupakan salah satu algoritma yang sering digunakan karena cukup sederhana tetapi memiliki stabilitas yang mumpuni. Parameter yang digunakan pada kasus ini sebagai berikut:

- n_estimator: jumlah trees (pohon) di forest. Di sini kita set n_estimator=50.
- max_depth: kedalaman atau panjang pohon. Ia merupakan ukuran seberapa banyak pohon dapat membelah (splitting) untuk membagi setiap node ke dalam jumlah pengamatan yang diinginkan. Untuk kasus ini digunakan max_depth=16.
- random_state: digunakan untuk mengontrol random number generator yang digunakan. nilai untuk random_tate pada kasus ini random_state=55.
- n_jobs: jumlah job (pekerjaan) yang digunakan secara paralel. Ia merupakan komponen untuk mengontrol thread atau proses yang berjalan secara paralel. n_jobs=-1 artinya semua proses berjalan secara paralel.

* Keuntungan

  - cukup sederhana namun memiliki stabilitas yang baik.
  - Dapat digunakan dengan baik pada dataset berukuran besar.
  - memiliki pengklasifiksian yang akurat.

* Kelemahan
  - Overfiting untuk kumpulan data yang mengandung noise.
  - Tidak bisa memperbaiki model yang dihasilkan secara berulang.

**Boosting**

Algoritma Boosting bekerja dengan membangun model dari data latih. Kemudian algoritma ini akan membuat model kedua untuk memperbaiki kesalahan dari model pertama. Model akan ditambahkan sampai data latih terprediksi dengan baik atau telah mencapai jumlah maksimum model untuk ditambahkan. Algoritma ini bertujuan untuk meningkatkan performa atau akurasi prediksi. Caranya dengan menggabungkan beberapa model yang sederhana dan dianggap lemah (weak learners) untuk membentuk suatu model yang kuat (strong ensemble learner).
Berikut parameter yang digunakan dalam model ini.

- learning*rate: bobot yang diterapkan pada setiap regressor di masing-masing proses iterasi boosting. \_Learning rate* pada kasus ini learning_rate=0.05.
- random*state: digunakan untuk mengontrol random number generator yang digunakan. Untuk kasus ini \_random state* sebesar random_state=55.

* Keuntungan

  - sangat powerful dalam meningkatkan akurasi prediksi
  - Mudah diimplementasikan.

* Kelemahan
  - Overfiting untuk kumpulan data yang mengandung noise.
  - Waktu komputasi yang lama.

## Evaluation

Dalam model machine learning ini, metrik yang akan digunakan adalah MSE atau _Mean Squared Error_ yaitu metriks yang menghitung jumlah selisih kuadrat rata-rata nilai sebenarnya dengan nilai prediksi untuk melihat seberapa dekat hasil prediksi dengan titik data.

$$MSE = {\sum{i=1}^n \left(At - Ft\right)^2 \over N}$$

- dimana:
  - At = Nilai Aktual permintaan
  - Ft = Nilai hasil prediksi
  - n = banyaknya data

Penerapan dalam metode pengembangan model, yaitu melakukan evaluasi menggunakan metrik _mean squared error_ pada model diperoleh hasil sebagai berikut:

Hasil visualisasi _Mean Square Error_ (MSE)

![image](https://user-images.githubusercontent.com/83525234/193869468-7acda4e2-0138-4154-9ca7-bb332a2b0e56.png)

Gambar 6. visualisasi _Mean Square Error_

Dari visualisasi di atas dapat dilihat MSE pada algoritma KNN menunjukkan nilai paling kecil yang artinya memiliki kesalahan paling kecil dibandingkan dengan algoritma _random forest_ dan _boosting_.

Tabel 3. Hasil Prediksi

|      | ytrue | prediksi_KNN | prediksi_RF | prediksi_Boosting |
| ---- | ----- | ------------ | ----------- | ----------------- |
| 7295 | 1.44  | 1.4          | 1.3         | 1.1               |

Pada Tabel 3 memberikan hasil nilai prediksi dari algoritma KNN paling baik dan mendekati nilai sebenarnya.

Berdasarkan uraian pada laporan di atas, dapat disimpulkan bahwa model yang telah dibuat dapat memprediksi harga alpukat, dan hasil prediksi terbaik yaitu menggunakan algoritma KNN yang memiliki nilai paling mendekati nilai sebenarnya.

### Referensi

- Santosa, Yohanes Tri. 2022. "10 Negara Terbesar Penghasil Alpukat di Dunia" The Agriculture News. di akses melalui (https://theagrinews.com/10-negara-penghasil-alpukat-terbesar-di-dunia/)
- Production of Avocados. 2018. Food and Agriculture Organiztion di akses melalui (https://www.fao.org/faostat/en/#data/QC/visualize)
