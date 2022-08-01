# Laporan Proyek Machine Learning - Muhammad Ilham Malik

## Domain Proyek
Traffic Volume, Predictive Analysis, Sosial 

Perhitungan lalu lintas adalah perhitungan terhadap baik lalu lintas kendaraan atau pejalan kaki, dimana pada umumnya dilaksanakan sepanjang jalan tertentu atau persimpangan. Perhitungan lalu lintas menyediakan data yang dapat digunakan untuk menghitung perhitungan lalu lintas harian rata-rata yang dimana menjadi indikator umum sebagai representasi Traffic Volume. Tingginya Traffic Volume dapat menyebabkan berbagai masalah, salah satunya adalah kesempatan dan waktu yang terbuang percuma serta peningkatan stress terhadap kehidupan manusia[1],[2]. Jika dibiarkan, tidak hanya mempengaruhi produktivitas individu, bahkan dapat mempengaruhi persaingan sebuah negara[3].

Permasalahan ini perlu diselesaikan dengan tujuan agar meningkatkan kualitas hidup manusia dan meningkatkan efisiensi waktu yang digunakan selama perjalanan. Salah satu solusi adalah dengan memprediksikan Traffic Volume pada keadaan tertentu seperti waktu, dengan begitu seseorang dapat menghindari waktu tertentu untuk melewati jalan tersebut atau mencari alternatif jalan lain.

## Business Understanding

### Problem Statements

Menjelaskan pernyataan masalah latar belakang:
- Seorang individu tidak mengetahui pada keadaan apa saja yang menyebabkan Traffic Volume tinggi
- Seorang individu tidak dapat memprediksi apakah pada saat keadaan tertentu Traffic Volume sedang tinggi 

### Goals

Menjelaskan tujuan dari pernyataan masalah:
- Seseorang dapat mengetahui keadaan-keadaan yang menyebabkan Traffic Volume tinggi
- Seseorang dapat memprediksikan keadaan Traffic Volume saat ini

### Solution statements
- Memberikan insight keadaan-keadaan yang berkorelasi terhadap Traffic Volume melalui visualisasi data
- Mengajukan algoritma Linear Regresion, Decision Tree Regressor dan Random Forest Regressor. 
- Metrik yang dijadikan evaluasi adalah Root Mean Squared Error (RMSE)

## Data Understanding
Dataset Metro Interstate Traffic Volume merupakan dataset yang mengukur volume lalu lintas jalan Westbound Interstate-94, serta mengukur
fitur-fitur cuaca dan hari libur dengan tujuan untuk menjawab pengaruh fitur-fitur tersebut terhadap traffic volume.

[Metro Interstate Traffic Volume Data Set](https://archive.ics.uci.edu/ml/datasets/Metro+Interstate+Traffic+Volume). 

### Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- holiday : merupakan data kategorikal yang menjelaskan hari libur nasional dan regional US.
- temp : Merupakan data numerik yang menunjukan suhu dalam skala kelvin.
- rain_1h : Merupakan data numerik untuk mengukur hujan yang menggunakan skala milimeter per jam.
- snow_1h : Merupakan data numerik untuk mengukur salju yang menggunakan skala milimeter per jam.
- clouds_all : Merupakan data numerik presentasi awan yang menutupi jalan tersebut.
- weather_main : Merupakan data kategorikal yang menjelaskan deskripsi singkat keadaan cuaca pada daerah tersebut.
- weather_description : Merupakan data kategorikal yang menjelaskan deskripsi panjang keadaan cuaca pada daerah tersebut.
- date_time : Merupakan data bertipe date_time yang membagi dataset setiap jam.
- traffic_volume : Merupakan data numerik yang menunjukan volume lalu lintas.

#### Exploratory Data Analysis: Deskripsi Data
Pada bagian ini saya memanfaatkan methode `head()`, `info()`, dan `describe()`. Untuk `head()` digunakan untuk melihat secara sekilas struktur data yang ada pada dataset. Metode `info()` digunakan untuk memeriksa tipe data pada setiap atribut. Terakhir, metode `describe()` digunakan untuk memeriksa anomali data atau missing value atau dapat juga untuk menemukan outlier.

#### Exploratory Data Analysis: Missing Data
Pada bagian ini saya menghilangkan beberapa data pada dataset. Alasan data ini dihapus adalah karena data yang mengandung _missing value_ masih sedikit. Data ini ditemukan melalui metode `describe()` yang dimana terdapat instansi yang memiliki temperatur suhu sebesar 0 kelvin. Hal ini tidak memungkinkan karena 0 kelvin itu sama saja dengan _absolute zero_ tidak mungkin diperoleh pada sistem yang besar. Maka dari itu saya menyelidiki nilai terendah selain 0 Kelvin, dan ditemukan nilai 243 Kelvin. Maka instansi data yang memiliki nilai temp lebih kecil dari 243 Kelvin dihapuskan.

#### Exploratory Data Analysis: Univariate Data
- Untuk **data numerik** dilakukan teknik visualisasi data menggunakan histogram. Histogram ini untuk melihat ketersebaran data ditunjukan dari bentuk graph yang diberikan
- Untuk **data kategorikal** dilakukan teknik visualisasi data menggunakan bar-chart. Bar-chart ini menunjukan jumlah instansi pada setiap kategori.
- Untuk **data date_time** dilakukan pemisahan atau _feature engineering_ terlebih dahulu agar dapat divisualisasikan. Memanfaatkan library pandas untuk mengekstrak tahun, bulan, hari, dan jam. Setelah masing-masing nilai didapat, fitur-fitur tersebut dapat divisualisasikan.

#### Exploratory Data Analysis: Multivariate Data
- Untuk **data numerik** saya menggunakan method `corr_matrix` untuk melihat hubungan korelasi antar fitur terhadap target fitur. Pada bagian ini dapat diperoleh kesimpulan bahwa yang memiliki korelasi yang tidak mendekati 0 adalah **temp** dan **date_time_hour**
- Untuk **data kategorikal** menggunakan barchart terhadap fitur target, _traffic volume_. Untuk fitur holiday, kategori hari libur mempengaruhi hasil _traffic volume_ dan weather_main sedikit mempengaruhi _traffic volume_.

## Data Preparation
Pada bagian ini saya akan menjelaskan data preparation

#### Data Preparation: One Hot Encoding
One Hot Encoding ini merubah data kategorikal menjadi menjadi data numerik. Caranya adalah dengan memberikan nilai 1 pada kategori aslinya dan membiarkan nilai 0 pada kategori lainnya. metode ini digunakan karena data kategori ini tidak memiliki hubungan ordinal dan Machine Learning umumnya tidak memproses tipe data string.

#### Data Preparation: Split Data
Pada bagian ini akan menjelaskan split data. Rasio split data yang digunakan adalah 90:10. Hal ini dikarenakan menurut saya data yang digunakan sudah cukup banyak dan ukuran test-set sudah mendekati 5000 instansi. Maka dari itu akan lebih baik jika jumlah data training jadi lebih banyak.

#### Data Preparation: Feature Scaling
Pada bagian ini saya menggunakan MinMaxScaler. MinMaxScaler ini merubah data sebagaimana hingga nilai data jatuh pada rentang 0-1. Cara bekerja MinMaxScaler ini adalah seperti yang diekspresikan berikut: <br/>
`X_hat = (X - min) / (max - min)` <br/>
MinMaxScaler digunakan karena fitur data yang akan diterapkan MinMaxScaler tidak memiliki outlier lalu rentang data yang diubah tergolong tidak terlalu besar, sehingga informasi penting tidak akan hilang.

## Modeling
Pada bagian modeling saya bereksperimen dengan tiga buah model yaitu Linear Regression, Decision Tree Regressor, dan Random Forest Regressor.

#### Linear Regression
Kelebihan dari linear regression ini merupakan model yang paling sederhana dibandingkan model lain yang digunakan dalam eksperimen ini, selain itu kelebihan lainnya adalah waktu training yang cepat.
Kekurangan dari model ini adalah karena model ini termasuk yang paling sederhana, maka model ini masih mengalami underfitting terhadap dataset.

#### Decision Tree Regressor
Kelebihan dari Decision Tree Regressor adalah model ini dapat mempelajari hubungan non-linear.
Kekurangan dari Decision Tree Regressor pada kasus ini adalah karena model ini lebih kompleks daripada linear regression, model ini lebih rentan terkena overfitting terhadap dataset.

#### Random Forest Regressor
Kelebihan dari Random Forest Regressor adalah karena model ini merupakan Ensemble Machine Learning, maka model ini merupakan yang paling kompleks.
Kekurangan dari Random Forest Regressor adalah model ini memiliki waktu training yang cukup lama dibanding model yang lain, dan masih terdapat overfitting terhadap dataset.

Berdasarkan hasil eksperimen, model terbaik yang dijadikan sebagai solusi adalah **Random Forest Regressor.**

## Evaluation
Pada proyek ini metrik evaluasi yang digunakan adalah _Root Mean Squared Error_. Alasan menggunakan RMSE adalah karena metrik ini memiliki presisi yang cukup tinggi dan dataset yang digunakan tidak memiliki _outlier_ sehingga dapat menggunakan RMSE sebagai metrik evaluasi.

| Models           | Train_rmse    | Test_rmse   |
| -------------    |:-------------:| -----------:|
| LinearRegression | 1837.979158	 | 1847.533254 |
| DTRegressor      | 225.672612    | 1307.898144 |
| RFRegressor      | 419.347272    | 1067.031678 |

Berdasarkan hasil di atas dapat diambil kesimpulan bahwa model yang terbaik untuk menjadi solusi adalah **Random Forest Regressor.**
Hal ini dikarenakan RMSE menghitung jarak prediksi terhadap nilai asli. Selain itu, Random Forest Regressor mengalami overfitting namun tidak
lebih parah dibandingkan **Decision Tree Regressor.**

### Formula RMSE dapat dilihat pada gambar berikut
![Formula RMSE](https://miro.medium.com/max/966/1*lqDsPkfXPGen32Uem1PTNg.png)
Keterangan:

- n     : jumlah banyak data
- y_hat : merupakan prediksi model
- y     : merupakan nilai target

## Kesimpulan
Untuk menjawab permasalahan pada bagian Problem Statement, dapat diurutkan sebagai berikut:
1. Penyebab Tingginya Traffic Volume dipengaruhi oleh **pukul waktu** dan **temperatur** saat itu.
2. Jika seseorang mengetahui keadaan dan temperatur saat itu, dengan memanfaatkan model Machine Learning, orang tersebut dapat memprediksikan traffic volume pada saat itu juga.

## Referensi
[1].Bharadwaj, Shashank, Sudheer Ballare, and Munish K. Chandel. "Impact of congestion on greenhouse gas emissions for road transport in Mumbai metropolitan region." Transportation Research Procedia 25 (2017): 3538-3551.
[2].Hopkins, John L., and Judith McKay. "Investigating ‘anywhere working’as a mechanism for alleviating traffic congestion in smart cities." Technological Forecasting and Social Change 142 (2019): 258-272.
[3].Kesuma, P. A., M. A. Rohman, and C. A. Prastyanto. "Risk analysis of traffic congestion due to problem in heavy vehicles: a concept." IOP Conference Series: Materials Science and Engineering. Vol. 650. No. 1. IOP Publishing, 2019.


**---Ini adalah bagian akhir laporan---**
