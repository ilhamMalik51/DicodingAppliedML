# Laporan Proyek Machine Learning - Muhammad Ilham Malik

## Project Overview

Industri animasi Jepang berkembang dengan sangat cepat dan telah menghasilkan animasi film yang sangat banyak [1]. Animasi ini biasa disebut dengan istilah "anime" juga menarik perhatian dari berbagai kalangan. Hal ini menyebabkan pertumbuhan industri animasi Jepang yang sangat cepat, bahkan pada tahun 2018, market untuk industri ini sudah melebihi 1 triliun yen [2]. Namun, dengan tingginya variasi jenis animasi film Jepang tersebut akan menyebabkan sebuah masalah yaitu akan menyulitkan user untuk menemukan sebuah _anime_ yang menyamai referensi mereka.

Masalah tersebut dapat diselesaikan dengan memanfaatkan sistem rekomendasi menggunakan pendekatan _Collaborative Filtering_ [3]. Sistem rekomendasi ini dapat memberikan keuntungan baik kepada pengguna dan industri animasi Jepang. Pengguna akan dapat menemukan sebuah _anime_ yang cocok dengan preferensi mereka secara efisien dan akurat. Industri animasi akan mendapat keuntungan lebih karena target genre animasi yang mereka buat akan dapat lebih mudah ditemukan melalui sistem rekomendasi tersebut. Selain itu, dengan diselesaikannya masalah ini akan ditemukan model yang paling optimal pada domain ini.

## Business Understanding

### Problem Statements

Menjelaskan pernyataan masalah:
- Pengguna akan kesulitan menemukan _anime_ yang sesuai dengan preferensi mereka dengan jumlah _anime_ yang sangat banyak dan juga beragam.
- Penulis belum mengetahui model yang optimal dalam merekomendasikan top-K _anime_.

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Memudahkan pengguna menemukan _anime_ yang sesuai dengan preferensi mereka secara efisien dan akurat.
- Menemukan sebuah model yang optimal pada dataset ini.

Semua poin di atas harus diuraikan dengan jelas. Anda bebas menuliskan berapa pernyataan masalah dan juga goals yang diinginkan.

### Solution statements
- Membangun sistem rekomendasi menggunakan pendekatan _Collaborative Filtering_ dengan algoritma _Deep Learning_ dan Matriks Faktorisasi.
- Model paling optimal akan diketahui setelah dilakukan analisis dan visualisasi hasil evaluasi dari setiap model.

## Data Understanding
Paragraf awal bagian ini menjelaskan informasi mengenai jumlah data, kondisi data, dan informasi mengenai data yang digunakan. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya, uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- accepts : merupakan jenis pembayaran yang diterima pada restoran tertentu.
- cuisine : merupakan jenis masakan yang disajikan pada restoran.
- dst

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

## Referensi
[1]. Wibowo, Agung Toto. "Leveraging side information to anime recommender system using deep learning." 2020 3rd International Seminar on Research of Information Technology and Intelligent Systems (ISRITI). IEEE, 2020.
[2]. Hiromichi Masuda, Tadashi Sudo, Kazuo Rikukawa, Yuji Mori, Naofumi Ito, Yasuo Kameyama, and Megumi Onouchi. Anime industry report 2019, 2019.
[3]. Lu, Jie, et al. "Recommender system application developments: a survey." Decision Support Systems 74 (2015): 12-32.

**---Ini adalah bagian akhir laporan---**
