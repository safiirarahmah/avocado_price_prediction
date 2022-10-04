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
![MSE](https://www.google.com/imgres?imgurl=https%3A%2F%2F1.bp.blogspot.com%2F-BhCZ4B8uQqI%2FX-HjGU2kcsI%2FAAAAAAAACkQ%2FEdNE0ynOwDIR9RYD_uxRMhps2DFFs5jgQCNcBGAsYHQ%2Fs364%2Frumus%252BMSE.jpg&imgrefurl=https%3A%2F%2Fwww.khoiri.com%2F2020%2F12%2Fpengertian-dan-cara-menghitung-mean-squared-error-mse.html&tbnid=lhIbFHv6_H0LgM&vet=12ahUKEwil6e6g9Mb6AhXzjtgFHaqEDZMQMygAegUIARC7AQ..i&docid=cdHZsE6oro5JRM&w=364&h=87&q=rumus%20mse&ved=2ahUKEwil6e6g9Mb6AhXzjtgFHaqEDZMQMygAegUIARC7AQ)

- dimana:
  - At = Nilai Aktual permintaan
  - Ft = Nilai hasil prediksi
  - n = banyaknya data

Penerapan dalam metode pengembangan model, yaitu melakukan evaluasi menggunakan metrik _mean squared error_ pada model diperoleh hasil sebagai berikut:

Hasil visualisasi Root Mean Square Error (MSE)
![Visualisasi MSE](data:image/png;base64,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)

Berdasarkan visulalisasi di atas dapat dilihat MSE pada aloritma KNN menunjukkan nilai paling kecil yang artinya memiliki kesalahan paling kecil. Dan menunjukkan prediksi paling sesuai.
