# Proyek Machine Learning - Safiira Rahmah Linisa

## Project Overview

Indonesia merupakan negara agraris yang mengamdalkan pertanian sebagai salah satu sektor matapencaharian terbesar bagi warga negaranya. Tanahnya yang luas dan Letaknya yang berada di wilayah tropis membuat berbagai tanaman tubuh subur di negara kita. Kondisi ini merupakan peluang besar bagi indonesia untuk menjadi negara produsen.

Alpukat merupakan salah satu buah yang banyak digemari masyarakat, tidak hanya di indonesia namun juga seluruh dunia. Berdasarkan data dari _Food and Agriculture Organization (FAO)_ tahun 2019, Indonesia menempati peringkat ke 5 negara penghasil alpukat terbesar didunia. Ini menujukkan bahwa sektor pertanian alpukat di Indonesia sudah cukup besar. Namun terkadang terdapat harga dipasaran tidak selalu stabil. Oleh karenanya dibutuhkan sistem untuk yang dapat memprediksi harga alpukat.

Untuk itu sistem prediksi harga alpukat ini dibuat dengan tujuan agar dapat menjadi acuan dan pertimbangan petani Indonesia dalam menetapkan harga ataupun dalam merancang strategi produksi. Dengan perkiraan harga tersebut petani dapat merancang stategi agar tidak mengalami kerugian dan serta meningkatkan keuntungan yang didapat.

## Business Understanding

### Problem Statement

- Dengan dataset yang dimiliki bagaimana cara mengembangkan model machine learning untuk memprediksi harga alpukat?

### Goals

- Membuat model machine learning yang mampu mempredikasi harga alpukat dengan baik.

### Solution approach

- Solusi yang diterapkan untuk dalam proyek ini adalah dengan membuat model regresi untuk memprediksi bilangan kontinue yang sesuai dengan permasalahan agar menghasilkan prediksi harga alpukat yang akurat.
- Algoritma yang digunakan untuk menyelesaikan kasus ini adalah sebagai berikut :
  - K-Nearest Neighbours
  - Random Forest
  - Boosting

## Data Understanding

**Informasi Dataset**
| Informasi | Keterangan |
| --------- | --------------------------------------------------------------------- |
| Link | https://www.kaggle.com/datasets/smokingkrils/avacado-price-prediction |

Dataset yang saya gunakan merupakan dataset mengenai Avocado atau buah alpukat.
Berikut ini variabel-variable yang terdapat dalam dataset

- Date: Tanggal Observasi
- AveragePrice: Harga Rata-rata satu buah Alpukat
- Total Volume: Jumalah Alpukat yang terjual
- 4046: Total jumlah alpukat terjual dengan PLU 4046
- 4225: Total jumlah alpukat terjual dengan PLU 4046
- 4770: Total jumlah alpukat terjual dengan PLU 4046
- Total Bags: Total jumlah sekantung alpukat
- Small Bags: Kantung/wadah kecil
- Large Bags: Kantung/wadah besar
- XLarge Bags: Kantung/wadah ekstra besar
- type: Jenis alpukat konvesional atau organik
- year: Tahun
- region: Kota atau wilayah obeservasi

- Mengecek informasi pada data
  - avocado.info()
  ![image](https://user-images.githubusercontent.com/83525234/193876299-477cc7bf-c365-428e-a24c-dfa83cb702c0.png)


- Mengecek informasi statistik pada data
  - diamonds.describe()
  ![image](https://user-images.githubusercontent.com/83525234/193876753-5092bc24-7715-4a5c-8e8c-e58acbdcf194.png)

- Menangani outlier dengan IQR Methode 

- Univariate Analysis
  - untuk menunjukan hubungan pada suatu fitur.

- Multivariate Analysis
  - untuk menunjukkan hubungan antara dua atau lebih variabel pada data

Visualisasi berikut menunjukkan korelasi atau hubungan antara tiap fitur.
![image](https://user-images.githubusercontent.com/83525234/193878390-97f5133d-54af-4753-b254-86cd0ec8683f.png)


## Data Preparation

**Mengatasi Missing Value**
Tujuannya dari proses proses missing value yaitu agar dataset menjadi bersih dari fitur yang tidak dibutuhkan, maupun yang valuenya kosong karena dapat menimbulkan hasil akurasi yang kurang baik.

**Split Dataset**
Split dataset yaitu membagi dataset menjadi data _training_ dan data _testing_. Data _training_ digunakan untuk pelatihan model, sedangakan data _testing_ digunakan untuk memvalidasi performa dan akurasi model setelah pelatihan. Untuk pembagian dataset pada proyek ini, saya membaginya menjadi 80% data _training_ dan 20% data _training_.

## Modeling

Dalam tahap Development model pada studi kasus prediksi harga alpukat ini, Algoritma machine learning yang saya gunakan sebagai solusi untuk memprediksi harga alpukat diantaranya sebagai berikut:

**K-Nearest Neighbour**
Algortma K-NN merupakan algoritma yang cara kerjanya yaitu membandingkan jarak satu sampel ke sampel pelatihan lain dengan memilih sejumlah k tetangga terdekat. Algoritma KNN menggunakan kmiripan data baru dengan data tetangga terdekat untuk memprediksi nilai dari setiap data yang baru. Dengan kata lain, setiap data baru diberi nilai berdasarkan seberapa mirip titik tersebut dalam set pelatihan. KNN ini dapat digunakan untuk kasus regresi dan klasifikasi. Pada model ini digunakan satu paramenter yaitu _n-neighbours_ atau jumlah tetangga. Untuk kasus ini saya menggunakan 5 neighbours.
Keuntungan menggunakan Algoritma ini adalah mudah dipahami dan digunakan. Sedangkan kelemahannya adalah pada jumlah fitur dan dimensi yang besar jumlah sample akan meningkat secara eksponensial.

**Random Forest**
Algoritma random forest merupakan salah satu algoritma supervised learning. Random forest termasuk ke dalam model ensamble group learning. Model ini terdiri dari sekelompok model yang bekerja secara bersama sama untuk menyelesaikan masalah. Pada model ansemble setiap model harus membuat prediksi secara independent, kemudian prediksi dari tiap model ini digabungkan untuk membuat prediksi akhir. Sehingga tingkat keberhasilan akan lebih tinggi dibanding model bekerja sendiri. Algoritma ini digunakan untuk menyelesaikan masalah klasifikasi dan regresi.
Random forest merupakan salah satu algoritma yang sering digunakan karena cukup sederhana tetapi memilikistabilitas yang mumpuni. Parameter yang digunakan pada kasus ini sebagai berikut:

- n_estimator: jumlah trees (pohon) di forest. Di sini kita set n_estimator=50.
- max_depth: kedalaman atau panjang pohon. Ia merupakan ukuran seberapa banyak pohon dapat membelah (splitting) untuk membagi setiap node ke dalam jumlah pengamatan yang diinginkan.
- random_state: digunakan untuk mengontrol random number generator yang digunakan.
- n_jobs: jumlah job (pekerjaan) yang digunakan secara paralel. Ia merupakan komponen untuk mengontrol thread atau proses yang berjalan secara paralel. n_jobs=-1 artinya semua proses berjalan secara paralel.

**Boosting**
Algoritma Boosting bekerja dengan membangun model dari data latih. Kemudian algoritma ini akan membuat model kedua untuk memperbaiki kesalahan dari model pertama. Model akan ditambahkan sampai data latih terprediksi dengan baik atau telah mencapai jumlah maksimum model untuk ditambahkan. Algortima ini bertujuan untuk meningkatkan performa atau akurasi prediksi. Caranya dengan menggabungkan beberapa model yang sederhana dan dianggap lemah (weak learners) untuk membentuk suatu model yang kuat (strong ensemble learner).
Berikut parameter yang digunakan dalam model ini.

- learning_rate: bobot yang diterapkan pada setiap regressor di masing-masing proses iterasi boosting.
- random_state: digunakan untuk mengontrol random number generator yang digunakan.

## Evaluation

Dalam model machine learning ini, metrik yang akan digunakan adalah MSE atau _Mean Squared Error_ yaitu metriks yang enghitung jumlah selisih kuadrat rata-rata nilai sebenarnya dengan nilai prediksi untuk melihat seberapa dekat hasil prediksi dengan titik data.

![image](https://user-images.githubusercontent.com/83525234/193869594-7c27fdd3-ad08-41f9-a3dc-7da940223a87.png)

- dimana:
  - At = Nilai Aktual permintaan
  - Ft = Nilai hasil prediksi
  - n = banyaknya data

Penerapan dalam metode pengembangan model, yaitu melakukan evaluasi menggunakan metrik _mean squared error_ pada model diperoleh hasil sebagai berikut:

Hasil visualisasi Root Mean Square Error (MSE)

![image](https://user-images.githubusercontent.com/83525234/193869468-7acda4e2-0138-4154-9ca7-bb332a2b0e56.png)

Berdasarkan visulalisasi di atas dapat dilihat MSE pada aloritma KNN menunjukkan nilai paling kecil yang artinya memiliki kesalahan paling kecil. Dan menunjukkan prediksi paling sesuai.