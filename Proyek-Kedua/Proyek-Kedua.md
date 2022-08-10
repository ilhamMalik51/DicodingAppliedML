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
Dataset _anime_ yang digunakan merupakan dataset yang ditemukan pada platform _public dataset_ Kaggle. Dataset ini memiliki informasi data terkait preferensi pengguna sebanyak 73.516 penilaian pengguna terhadap 12.294 film _anime_ dengan total keseluruhan sebanya 7.813.737 baris data. Dataset ini diperoleh dari laman _Website_ myanimelist.net dengan memanfaatkan API pada _website_ tersebut. Informasi lebih lanjut terkait dataset yang digunakan dapat diakses pada [Anime Recommendations Database](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database?resource=download)

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

### Exploratory Data Analysis: Data Description
Pada bagian ini, akan digunakan method-method yang berasal dari library Pandas DataFrame untuk memahami skema data. Method-method tersebut melipui `head()` dan `info()`. Secara singkat method `head()` digunakan untuk melihat beberapa baris data. Selain itu, method `info()` digunakan untuk memeriksa tipe data dan memeriksa keberadaan _missing value_.

Untuk membaca dataset, dapat menggunakan `read_csv()` method untuk membaca file yang memiliki format CSV.

```
anime_df = pd.read_csv("dataset/anime.csv")
rating_df = pd.read_csv("dataset/rating.csv")
```

Berikut adalah merupakan kode yang digunakan untuk melihat 10 data teratas dari dataset. Kode di bawah ini menggunakan head() method yang ada pada objek DataFrame.

```
anime_df.head(10)
```

![anime_df_head](https://github.com/ilhamMalik51/DicodingAppliedML/blob/09e3b2d6195b79a2ecc378130fd2465dbd046c44/Proyek-Kedua/asset/df_head_anime_df.JPG)

Seperti yang sudah disinggung sebelumnya, dataset ini terdiri dari 7 fitur. Terdapat fitur yang perlu diperhatikan, contohnya fitur **rating**. Berdasarkan metadata fitur **rating** ini merupakan rerata rating yang diterima oleh film tersebut. Hal ini penting diketahui karena apabila terdapat sebuah data yang tidak memiliki rating, dapat dilakukan imputasi menggunakan mean yang berasal dari dataset tersebut.

```
rating_df.head(10)
```

![rating_df_head](https://github.com/ilhamMalik51/DicodingAppliedML/blob/09e3b2d6195b79a2ecc378130fd2465dbd046c44/Proyek-Kedua/asset/df_head_rating_df.JPG)

Berdasarkan gambar di atas, dapat diketahui bahwa dataset tersebut terdiri dari 3 fitur. Fitur yang perlu diperhatikan pada dataset ini adalah fitur **rating**, dikarenakan berdasar dari informasi metadata, terdapat nilai rating -1 yang berarti orang tersebut yang sudah menonton namun tidak menilai film tersebut. Hal ini sebenarnya sama saja dengan _missing value_ terhadap fitur **rating**.

#### Memeriksa Jumlah Data Total, user_id, dan anime_id

Berdasarkan hipotesis solusi yang diajukan menggunakan pendekatan *Collaborative Filtering* maka fitur-fitur yang akan diperiksa adalah sebagai berikut.
1. Jumlah seluruh data penilaian terhadap *anime*
2. Jumlah user identifier
3. Jumlah anime identifier

```
print("Jumlah seluruh data penilaian anime: {}".format(len(rating_df["user_id"])))
print("Jumlah identifier unik user: {}".format(len(rating_df["user_id"].unique())))
print("Jumlah identifier unik anime: {}".format(len(anime_df["anime_id"].unique())))
```

![len_data](https://github.com/ilhamMalik51/DicodingAppliedML/blob/09e3b2d6195b79a2ecc378130fd2465dbd046c44/Proyek-Kedua/asset/panjang_total_anime_id_user_id.JPG)

#### Memeriksa Informasi Dataset

```
anime_df.info()
```

![df_anime_info](https://github.com/ilhamMalik51/DicodingAppliedML/blob/6314c91ee8adb0323f3623e41e534277299339f9/Proyek-Kedua/asset/df_info_anime_df.JPG)

```
rating_df.info()
```

![df_rating_info](https://github.com/ilhamMalik51/DicodingAppliedML/blob/6314c91ee8adb0323f3623e41e534277299339f9/Proyek-Kedua/asset/df_info_rating_df.JPG)

Berdasarkan kedua gambar di atas, dataset _Anime_ memiliki 7 fitur yang meliputi _anime_id_, _name_, _genre_, _type_, _episodes_, _rating_, dan _members_. Sedangkan untuk dataset _Rating_ memiliki 3 fitur meliputi _user_id_, _anime_id_, dan _rating._ Jumlah data yang terdapat pada dataset _Rating_ adalah 7.813.737. Jumlah ini sangat banyak, maka dari itu rasio pembagian data sudah dapat ditentukan.

### Exploratory Data Analysis: Data Cleaning
Berdasarkan informasi yang telah didapat pada bagian sebelumnya yaitu terdapat nilai rating -1. Seluruh baris data yang memiliki nilai tersebut tidak dapat digunakan jika tidak dirubah atau dihapus. 

Berikut kode yang digunakan untuk memeriksa nilai rating -1 tersebut.

```
neg_rating = rating_df[rating_df["rating"] == -1]
pos_rating = rating_df[rating_df["rating"] != -1]

print("Jumlah data yang memiliki poitif rating: {}".format(len(pos_rating)))
print("Jumlah data yang memiliki negatif rating: {}".format(len(neg_rating)))
print("Jumlah identifier unik pada data negatif rating: {}".format(len(neg_rating["anime_id"].unique())))
```

![jumlah_pos_neg](https://github.com/ilhamMalik51/DicodingAppliedML/blob/6314c91ee8adb0323f3623e41e534277299339f9/Proyek-Kedua/asset/jumlah_pos_rating_neg_rating.JPG)

Berdasarkan gambar di atas dan setelah dipertimbangkan, maka nilai rating -1 akan diimputasikan menggunakan fitur **rating** yang berada pada dataset *Anime*. Hal ini dilakukan karena jika data tersebut dihapus memiliki kemungkinan menghapus film anime tertentu. Selain itu, jika data dihapus, dataset Rating kehilangan sekitar 1.476.496 atau hampir 19% dari keseluruhan data.

Berikut kode yang digunakan untuk mengimputasikan nilai mean terhadap film _anime_ yang memiliki rating -1.

```
merge_rating = neg_rating.merge(anime_df, on="anime_id")

merge_rating = merge_rating[["user_id", "anime_id", "rating_y"]]
print("Panjang sebelum menghilangkan missing value: {}".format(len(merge_rating["anime_id"].unique())))

merge_rating = merge_rating.dropna(subset=["rating_y"])
print("Panjang setelah menghilangkan missing value: {}".format(len(merge_rating["anime_id"].unique())))

merge_rating["rating_y"] = merge_rating["rating_y"].astype("int64")
print("Merubah tipe data rating_y dari float menjadi int!")
```

Kode mengimputasikan nilai mean ini dimulai dengan menggunakan method `merge()`. Metode ini menyatukan dataset negatif rating dengan dataset anime. Dengan ini, setiap baris data akan memiliki fitur **rating_y** yang merupakan nilai rerata rating film _anime_ tersebut. Setelah itu,  kolom yang tidak digunakan dapat dihilangkan dan apabila terdapat film _anime_ yang tidak memiliki nilai rerata rating setelah diimputasikan dapat di-_drop_. Terakhir, karena nilai rerata ini merupakan nilai float, maka dapat di-_cast_ menjadi integer dan secara otomatis nilai desimal tersebut akan dibulatkan ke bawah.

Setelah data dengan nilai negatif rating diimputasikan, maka dataset kembali digabungkan. Hal tersebut dapat dilakukan dengan kode berikut.

```
prepared_df = pd.concat([pos_rating, merge_rating], ignore_index=True)

print("Jumlah data setelah dilakukan penggabungan data {}".format(len(prepared_df)))
```

Jumlah data setelah dilakukan penggabungan data 7.813.728.

### Exploratory Data Analysis: Univariate Analysis


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
