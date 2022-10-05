# Proyek Machine Learning - Safiira Rahmah Linisa

## Project Overview

Indonesia merupakan negara agraris yang mengandalkan pertanian sebagai salah satu sektor matapencaharian terbesar bagi warga negaranya. Tanahnya yang luas dan Letaknya yang berada di wilayah tropis membuat berbagai tanaman tubuh subur di negara kita. Kondisi ini merupakan peluang besar bagi indonesia untuk menjadi negara produsen.

Alpukat merupakan salah satu buah yang banyak digemari masyarakat, tidak hanya di indonesia namun juga seluruh dunia. Berdasarkan data dari _Food and Agriculture Organization (FAO)_ tahun 2019, Indonesia menempati peringkat ke 5 negara penghasil alpukat terbesar didunia. Ini menujukkan bahwa sektor pertanian alpukat di Indonesia sudah cukup besar. Namun terkadang terdapat kendala dimana harga dipasaran tidak selalu stabil. Oleh karenanya dibutuhkan sistem yang dapat memprediksi harga alpukat.

Untuk itu sistem prediksi harga alpukat ini dibuat dengan tujuan agar menjadi acuan dan pertimbangan petani Indonesia dalam menetapkan harga ataupun dalam merancang strategi produksi. Dengan perkiraan harga tersebut petani dapat merancang strategi agar tidak mengalami kerugian dan serta meningkatkan keuntungan yang didapat.

## Business Understanding

### Problem Statement

- Dengan dataset yang dimiliki bagaimana cara mengembangkan model _machine learning_ untuk memprediksi harga alpukat?

### Goals

- Membuat model _machine learning_ yang mampu mempredikasi harga alpukat dengan baik.

### Solution approach

- Solusi yang diterapkan untuk dalam proyek ini adalah dengan membuat model regresi untuk memprediksi bilangan kontinue yang sesuai dengan permasalahan agar menghasilkan prediksi harga alpukat yang akurat.
- Algoritma yang digunakan untuk menyelesaikan kasus ini adalah sebagai berikut :
  - _K-Nearest Neighbors_
  - _Random Forest_
  - _Boosting_

## Data Understanding

**Informasi Dataset**
| Informasi | Keterangan |
| --------- | --------------------------------------------------------------------- |
| Link | https://www.kaggle.com/datasets/smokingkrils/avacado-price-prediction |
| Nama Dataset | Avocado Price Prediction |
| Usability | 7.06 |
| Jumlah Data | 18249 |
| Jumlah Kolom | 14 |
| Jumlah fitur | 13 |

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

  - avocado.info()

  ![image](https://user-images.githubusercontent.com/83525234/193876299-477cc7bf-c365-428e-a24c-dfa83cb702c0.png)

- Mengecek informasi statistik pada data

  - diamonds.describe()

  ![image](https://user-images.githubusercontent.com/83525234/193876753-5092bc24-7715-4a5c-8e8c-e58acbdcf194.png)

- Menangani _outlier_ dengan _IQR Methode_

- Univariate Analysis

  - untuk menunjukan hubungan pada suatu fitur.

  ![image](https://user-images.githubusercontent.com/83525234/193973858-f51adc67-2b28-4b95-9b3e-3d9df7403633.png)

- Multivariate Analysis

  - untuk menunjukkan hubungan antara dua atau lebih variabel pada data

  ![image](https://user-images.githubusercontent.com/83525234/193973993-3fb0aa57-11c9-479b-aacf-8a1e923a3c42.png)

Visualisasi berikut menunjukkan korelasi atau hubungan antara tiap fitur.

![image](https://user-images.githubusercontent.com/83525234/193878390-97f5133d-54af-4753-b254-86cd0ec8683f.png)

## Data Preparation

**Mengatasi Missing Value**

Tujuannya dari proses _missing value_ yaitu agar dataset menjadi bersih dari fitur yang tidak dibutuhkan, maupun yang valuenya kosong karena dapat menimbulkan hasil akurasi yang kurang baik.

- Mendeteksi fitur yang memiliki value 0

  ![image](https://user-images.githubusercontent.com/83525234/193991693-123e148b-376d-45b6-af34-84434a9f8dfd.png)

  Berdasarkan data diatas dapat dilihat bahwa terdapat fitur yang memiliki missing value. Data diatas sangat menarik karena menunjukkan hubungan antara fitur _Total Bags_, _Small Bags_ serta _Large Bags_.

- Menangani Missing Value dengan menghapus fitur yang bernilai 0

  ![image](https://user-images.githubusercontent.com/83525234/193992198-962e3631-d8d0-48e3-8d5a-b2146ee5f0dc.png)

**Menangani _oulier_**

- Memvisualisasikan data Avocado dengan boxplot untuk mendeteksi _outliers_ pada beberapa fitur numerik.

  ![image](https://user-images.githubusercontent.com/83525234/193988867-ced2a289-4629-43ef-9717-008b591555cd.png)

  Dari visualisasi tersebut dapat dilihat bahwa terdapat outlier pada fitur _Average Price_. Menggunakan cara yang sama ditemukan pula outlier pada beberapa fitur numerik lain yaitu pada _Total Bags_ dan _Small Bags_.

- Mengatasi _Outlier_ dengan _IQR Method_
  Untuk mengatasi _outlier_ pada proyek ini digunakan teknik _IQR Method_. Cara kerja dari _IQR Method_ yaitu dengan menghapus data yang berada diluar _interquartile range_. Interquartile adalah range diantara kuartil pertama(25%) dan kuartil ketiga(75%).

  ![image](https://user-images.githubusercontent.com/83525234/193990096-0074dc2c-7b16-4b87-8ac8-67f3d2821a5e.png)

**Drop data**

Menghapus data non numerik serta menghapus data yang tidak dibutuhkan. Hal ini bertujuan agar model dapat dilatih untuk memprediksi data dengan baik dan mendapatkan hasil prediksi dengan akurasi tinggi.

![image](https://user-images.githubusercontent.com/83525234/193994042-3ed1235d-2c75-4c6d-bac9-4bc86c7aa7bc.png)

**Split Dataset**

Split dataset yaitu membagi dataset menjadi data _training_ dan data _testing_. Data _training_ digunakan untuk pelatihan model, sedangkan data _testing_ digunakan untuk memvalidasi performa dan akurasi model setelah pelatihan. Untuk pembagian dataset pada proyek ini, saya membaginya menjadi 80% data _training_ dan 20% data _training_.

## Modeling

Dalam tahap Development model pada studi kasus prediksi harga alpukat ini, Algoritma machine learning yang saya gunakan sebagai solusi untuk memprediksi harga alpukat diantaranya sebagai berikut:

**K-Nearest Neighbor**

Algoritma K-NN merupakan algoritma yang cara kerjanya yaitu membandingkan jarak satu sampel ke sampel pelatihan lain dengan memilih sejumlah k tetangga terdekat. Algoritma KNN menggunakan kemiripan data baru dengan data tetangga terdekat untuk memprediksi nilai dari setiap data yang baru. Dengan kata lain, setiap data baru diberi nilai berdasarkan seberapa mirip titik tersebut dalam set pelatihan. KNN ini dapat digunakan untuk kasus regresi dan klasifikasi. Pada model ini digunakan satu parameter yaitu _n-neighbors_ atau jumlah tetangga. Untuk kasus ini saya menggunakan 5 neighbors.
Keuntungan menggunakan Algoritma ini adalah mudah dipahami dan digunakan. Sedangkan kelemahannya adalah pada jumlah fitur dan dimensi yang besar jumlah sampel akan meningkat secara eksponensial.

**Random Forest**

Algoritma random forest merupakan salah satu algoritma supervised learning. Random forest termasuk ke dalam model ensemble group learning. Model ini terdiri dari sekelompok model yang bekerja secara bersama sama untuk menyelesaikan masalah. Pada model ensemble setiap model harus membuat prediksi secara independent, kemudian prediksi dari tiap model ini digabungkan untuk membuat prediksi akhir. Sehingga tingkat keberhasilan akan lebih tinggi dibanding model bekerja sendiri. Algoritma ini digunakan untuk menyelesaikan masalah klasifikasi dan regresi.
Random forest merupakan salah satu algoritma yang sering digunakan karena cukup sederhana tetapi memiliki stabilitas yang mumpuni. Parameter yang digunakan pada kasus ini sebagai berikut:

- n_estimator: jumlah trees (pohon) di forest. Di sini kita set n_estimator=50.
- max_depth: kedalaman atau panjang pohon. Ia merupakan ukuran seberapa banyak pohon dapat membelah (splitting) untuk membagi setiap node ke dalam jumlah pengamatan yang diinginkan.
- random_state: digunakan untuk mengontrol random number generator yang digunakan.
- n_jobs: jumlah job (pekerjaan) yang digunakan secara paralel. Ia merupakan komponen untuk mengontrol thread atau proses yang berjalan secara paralel. n_jobs=-1 artinya semua proses berjalan secara paralel.

**Boosting**

Algoritma Boosting bekerja dengan membangun model dari data latih. Kemudian algoritma ini akan membuat model kedua untuk memperbaiki kesalahan dari model pertama. Model akan ditambahkan sampai data latih terprediksi dengan baik atau telah mencapai jumlah maksimum model untuk ditambahkan. Algoritma ini bertujuan untuk meningkatkan performa atau akurasi prediksi. Caranya dengan menggabungkan beberapa model yang sederhana dan dianggap lemah (weak learners) untuk membentuk suatu model yang kuat (strong ensemble learner).
Berikut parameter yang digunakan dalam model ini.

- learning_rate: bobot yang diterapkan pada setiap regressor di masing-masing proses iterasi boosting.
- random_state: digunakan untuk mengontrol random number generator yang digunakan.

## Evaluation

Dalam model machine learning ini, metrik yang akan digunakan adalah MSE atau _Mean Squared Error_ yaitu metriks yang menghitung jumlah selisih kuadrat rata-rata nilai sebenarnya dengan nilai prediksi untuk melihat seberapa dekat hasil prediksi dengan titik data.

![image](https://user-images.githubusercontent.com/83525234/193869594-7c27fdd3-ad08-41f9-a3dc-7da940223a87.png)

- dimana:
  - At = Nilai Aktual permintaan
  - Ft = Nilai hasil prediksi
  - n = banyaknya data

Penerapan dalam metode pengembangan model, yaitu melakukan evaluasi menggunakan metrik _mean squared error_ pada model diperoleh hasil sebagai berikut:

Hasil visualisasi Root Mean Square Error (MSE)

![image](https://user-images.githubusercontent.com/83525234/193869468-7acda4e2-0138-4154-9ca7-bb332a2b0e56.png)

Tabel Hasil Prediksi
![image](https://user-images.githubusercontent.com/83525234/193977432-924a212e-3ccf-4d1a-a7b1-0a0b64378b49.png)

Berdasarkan visualisasi di atas dapat dilihat MSE pada algoritma KNN menunjukkan nilai paling kecil yang artinya memiliki kesalahan paling kecil. Dan menunjukkan prediksi paling sesuai.
