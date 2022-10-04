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
![MSE](data:image/jpeg;base64,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)

- dimana:
  - At = Nilai Aktual permintaan
  - Ft = Nilai hasil prediksi
  - n = banyaknya data

Penerapan dalam metode pengembangan model, yaitu melakukan evaluasi menggunakan metrik _mean squared error_ pada model diperoleh hasil sebagai berikut:

Hasil visualisasi Root Mean Square Error (MSE)
![Visualisasi MSE](![image](https://user-images.githubusercontent.com/83525234/193869081-1f27152b-e628-4b15-9923-967092a939b4.png))

Berdasarkan visulalisasi di atas dapat dilihat MSE pada aloritma KNN menunjukkan nilai paling kecil yang artinya memiliki kesalahan paling kecil. Dan menunjukkan prediksi paling sesuai.
