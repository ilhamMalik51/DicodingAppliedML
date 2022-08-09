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
- Menemukan sebuah model yang optimal pada dataset ini yang ditunjukan dengan evaluasi metrik yang digunakan.

### Solution statements
- Membangun sistem rekomendasi menggunakan pendekatan _Collaborative Filtering_ dengan algoritma _Deep Learning_ RecommenderNet dan Matriks Faktorisasi menggunakan metode _Deep Learning_ yang bernama _Probabilistic Matrix Factorization_ [4].
- Model paling optimal akan diketahui setelah dilakukan analisis dan visualisasi hasil evaluasi dari setiap model.

## Data Understanding
Dataset _anime_ yang digunakan merupakan dataset yang ditemukan pada platform _public dataset_ Kaggle. Dataset ini memiliki informasi data terkait preferensi pengguna sebanyak 73.516 penilaian pengguna terhadap 12.294 film _anime_. Dataset ini diperoleh dari laman _Website_ myanimelist.net dengan memanfaatkan API pada _website_ tersebut. Informasi lebih lanjut terkait dataset yang digunakan dapat diakses pada [Anime Recommendations Database](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database?resource=download)

Pada file Anime.csv, terdapat variabel-variabel sebagai berikut:
- anime_id : Merupakan _identifier_ unik film anime.
- name : Merupakan judul lengkap _anime._
- genre : Merupakan genre _anime_.
- type : Merupakan jenis _anime_ (OVA, TV, Movie).
- episodes : Merupakan jumlah episode _anime_ tersebut.
- rating : Merupakan rerata nilai yang didapatkan _anime_ tersebut.
- members : Jumlah anggota yang berada pada "grup" _anime_ tersebut.

Pada file Rating.csv, terdapat variabel-variabel sebagai berikut:
- user_id : Merupakan _identifier_ yang dibuat secara random sebagai user_id.
- anime_id : Merupakan _identifier_ anime yang diberikan nilai oleh pengguna.
- rating : Merupakan nilai yang diberikan oleh pengguna, memiliki skala hingga 10 serta nilai -1 jika user menonton dan tidak memberikan rating.

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
[4]. Mnih, Andriy, and Russ R. Salakhutdinov. "Probabilistic matrix factorization." Advances in neural information processing systems 20 (2007).

**---Ini adalah bagian akhir laporan---**
