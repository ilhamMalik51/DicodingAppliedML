# Laporan Proyek Machine Learning - Muhammad Ilham Malik

## Domain Proyek

Traffic Volume, Predictive Analysis, Sosial 

Perhitungan lalu lintas adalah perhitungan terhadap baik lalu lintas kendaraan atau pejalan kaki, dimana pada umumnya dilaksanakan sepanjang jalan tertentu atau persimpangan. Perhitungan lalu lintas menyediakan data yang dapat digunakan untuk menghitung perhitungan lalu lintas harian rata-rata yang dimana menjadi indikator umum sebagai representasi Traffic Volume. Tingginya Traffic Volume dapat menyebabkan berbagai masalah, salah satunya adalah kesempatan dan waktu yang terbuang percuma serta peningkatan stress terhadap kehidupan manusia[[Risk analysis of traffic congestion due to problem in heavy 
vehicles: a concept](https://iopscience.iop.org/article/10.1088/1757-899X/650/1/012011/meta)].

Permasalahan ini perlu diselesaikan dengna tujuan agar meningkatkan kualitas hidup manusia dan meningkatkan efisiensi waktu yang digunakan selama perjalanan. Salah satu solusi adalah dengan memprediksikan Traffic Volume pada keadaan tertentu seperti waktu, dengan begitu seseorang dapat menghindari waktu tertentu untuk melewati jalan tersebut atau mencari alternatif jalan lain.

## Business Understanding

### Problem Statements

Menjelaskan pernyataan masalah latar belakang:
- Seseorang tidak mengetahui pada keadaan apa saja yang menyebabkan Traffic Volume tinggi
- Seseorang tidak dapat memprediksi apakah pada saat keadaan tertentu Traffic Volume sedang tinggi 

### Goals

Menjelaskan tujuan dari pernyataan masalah:
- Seseorang dapat mengetahui keadaan-keadaan yang menyebabkan Traffic Volume tinggi
- Seseorang dapat memprediksikan keadaan Traffic Volume saat ini

### Solution statements
- Memberikan insight keadaan-keadaan yang berkorelasi terhadap Traffic Volume melalui visualisasi data
- Mengajukan algoritma Linear Regresion dan Random Forest Regressor. 
- Metrik yang dijadikan evaluasi adalah Root Mean Squarred Error (RMSE)

## Data Understanding
Paragraf awal bagian ini menjelaskan informasi mengenai data yang Anda gunakan dalam proyek. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

### Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- accepts : merupakan jenis pembayaran yang diterima pada restoran tertentu.
- cuisine : merupakan jenis masakan yang disajikan pada restoran.
- dst

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
