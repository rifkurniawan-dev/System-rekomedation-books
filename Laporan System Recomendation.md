# **Laporan Proyek Machine Learning Terapan 2**


---

# **Detail Laporan : System Recommendation Books**

---

## Project Overview

Pengetahuan memegang peran krusial dalam kehidupan manusia. Melalui pengetahuan, individu dapat memahami berbagai aspek dalam hidup dan meningkatkan kualitas hidup mereka. Oleh karena itu, memahami dan mempelajari ilmu pengetahuan menjadi hal yang sangat penting. Salah satu cara yang paling mudah dan efektif untuk mengakses pengetahuan adalah melalui buku. Buku menyimpan berbagai pemikiran dan informasi dari penulis yang dikemas dalam bentuk narasi, ilustrasi, maupun bentuk lainnya. Aktivitas membaca memungkinkan seseorang memahami hal-hal yang sebelumnya belum diketahui.

Terdapat ungkapan bahwa buku adalah jendela dunia. Namun kenyataannya, tingkat minat baca masyarakat Indonesia tergolong sangat rendah. Berdasarkan data, indeks literasi Indonesia hanya mencapai 0,001 — artinya dari seribu orang, hanya satu yang memiliki ketertarikan tinggi terhadap aktivitas membaca. Angka ini sangat jauh jika dibandingkan dengan negara-negara maju seperti Amerika Serikat (0,45) dan Singapura (0,55), yang menunjukkan tingginya budaya membaca di negara tersebut. Hal ini menjadi alarm penting bagi Indonesia untuk mendorong peningkatan minat baca.

Salah satu hambatan utama yang dihadapi masyarakat dalam memulai kebiasaan membaca adalah kesulitan dalam menemukan buku yang sesuai dengan minat. Meski banyak pilihan buku tersedia, tanpa panduan atau rekomendasi, calon pembaca sering kali bingung menentukan pilihan. Akibatnya, motivasi membaca pun bisa cepat menghilang. Oleh karena itu, dibutuhkan sebuah sistem yang mampu membantu individu menemukan buku yang relevan dengan preferensi mereka, guna mendorong semangat membaca di kalangan masyarakat. 

Salah satu solusi yang dapat dimanfaatkan untuk membantu seseorang dalam menemukan buku yang sesuai adalah dengan membangun sistem rekomendasi buku. Sistem ini bertujuan untuk menyarankan buku-buku kepada pengguna berdasarkan preferensi atau riwayat bacaan, sehingga proses pencarian buku menjadi lebih efisien dan terarah. Sistem rekomendasi tersebut memanfaatkan data dari ulasan atau penilaian pengguna lain untuk menyajikan daftar buku yang kemungkinan besar akan disukai oleh pengguna baru. Dengan adanya sistem ini, diharapkan pembaca pemula dapat lebih mudah menemukan bacaan yang sesuai dengan ketertarikannya. Dalam pengembangannya, pendekatan yang digunakan adalah collaborative filtering, yaitu metode yang memanfaatkan interaksi dan perilaku pembaca lain sebagai dasar rekomendasi.

## Business Understanding

### Problem Statements

Berdasarkan uraian permasalahan sebelumnya, maka dapat dirumuskan beberapa pertanyaan sebagai berikut:

* Bagaimana merancang dan membangun sistem rekomendasi buku yang mampu mendorong peningkatan minat baca pengguna?

* Teknik apa yang paling sesuai dan memberikan hasil akurasi terbaik dalam penerapan metode collaborative filtering untuk sistem rekomendasi buku ini?
### Goals

Tujuan dari proyek ini adalah sebagai berikut:

* Membangun sebuah sistem rekomendasi buku yang mampu mendorong peningkatan minat membaca dengan memanfaatkan ulasan dari pembaca lain.

* Menentukan dan menerapkan metode collaborative filtering yang paling sesuai dan akurat untuk mendukung pengembangan sistem rekomendasi ini.
### Solution statements

Untuk mencapai tujuan pengembangan sistem rekomendasi buku, digunakan pendekatan collaborative filtering dengan menerapkan dua teknik, yaitu Singular Value Decomposition (SVD) dan Neural Network. Kedua pendekatan ini akan dibandingkan untuk menentukan metode yang paling efektif.

* **Collaborative Filtering dengan teknik Singular Value Decomposition (SVD)**

SVD merupakan metode faktorisasi matriks yang digunakan untuk mereduksi ukuran dimensi matriks menjadi bentuk yang lebih ringkas. Dalam konteks sistem rekomendasi, SVD mengelompokkan pengguna berdasarkan atribut mereka, lalu melakukan dekomposisi terhadap matriks penilaian (rating). Proses ini menghasilkan matriks representasi baru dari pengguna dan item, yang kemudian dianalisis untuk menghitung tingkat kemiripan antar pengguna dalam memberikan rekomendasi.

* **Collaborative Filtering dengan teknikNeural Network**

  Neural Network merupakan algoritma machine learning yang meniru cara kerja jaringan saraf manusia. Dalam sistem rekomendasi, algoritma ini dapat diintegrasikan dengan metode collaborative filtering untuk memperoleh kemampuan progressive learning, yakni pembelajaran yang terus berkembang seiring bertambahnya data. Dengan pendekatan ini, Neural Network mampu mengidentifikasi pola tersembunyi antara karakteristik pengguna dan item yang direkomendasikan.
  
## Data Understanding

Dataset yang digunakan dalam pengembangan sistem rekomendasi buku diperoleh dari Kaggle [**Book Recommendation Dataset**](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset). Dataset ini terdiri dari dua file berformat comma-separated values (CSV), yaitu Books.csv dan Ratings.csv. File Users.csv tidak digunakan dalam pengembangan sistem ini karena tidak diperlukan dalam proses pemodelan rekomendasi. Secara keseluruhan, terdapat 1.149.780 penilaian dan terhadap 271.360 buku. Dataset ini terdiri dari dua file berformat comma-separated values (CSV), yaitu ```Books.csv```dan ```Ratings.csv```.

Penjelasan masing-masing file dalam dataset ini adalah sebagai berikut:

* ```Books.csv```: Berisi data mengenai buku-buku yang diperoleh dari Amazon Web Services, mencakup informasi detail seperti ISBN, Judul Buku, Penulis Buku, Tahun Terbit, Penerbit dan URL Gambar S
* ```Ratings.csv```: Menyajikan data penilaian yang diberikan oleh pengguna terhadap buku dengan skala 0 hingga 10, di mana nilai yang lebih tinggi menunjukkan tingkat apresiasi yang lebih besar terhadap buku tersebut.

Fitur pada masing-masing data:
Fitur pada Data Books:

* ```ISBN```: Nomor identifikasi unik untuk setiap buku (International Standard Book Number).

* ```Book-Title```: Judul buku.

* ```Book-Author```: Nama penulis buku.

* ```Year-Of-Publication```: Tahun buku diterbitkan.

* ```Publisher```: Nama penerbit buku.

* ```Image-URL-S```: URL gambar sampul buku ukuran kecil (dari Amazon).

* ```Image-URL-M```: URL gambar sampul buku ukuran sedang (dari Amazon).

* ```Image-URL-L```: URL gambar sampul buku ukuran besar (dari Amazon).


**Fitur pada Data Ratings:**

* ```User-ID```: ID pengguna yang memberikan penilaian.

* ```ISBN```: Kode unik dari buku yang dinilai.

* ```Book-Rating```: Skor penilaian terhadap buku, dengan rentang 0 hingga 10. Nilai 0 menunjukkan bahwa pengguna belum memberikan rating.

Berdasarkan eksplorasi awal menggunakan .info() sebagai berikut: 
* **```Books.csv```**
  
<class 'pandas.core.frame.DataFrame'>

RangeIndex: 271360 entries, 0 to 271359

Data columns (total 8 columns):

|  #  |     Column              |  Non-Null Count  |  Dtype  |
|-----|-------------------------|------------------|---------|  
|  0  |    ISBN                 |  271360 non-null |  object |
|  1  |    Book-Title           |  271360 non-null |  object |
|  2  |    Book-Author          |  271358 non-null |  object |
|  3  |    Year-Of-Publication  |  271360 non-null |  object |
|  4  |    Publisher            |  271358 non-null |  object |
|  5  |    Image-URL-S          |  271360 non-null |  object |
|  6  |    Image-URL-M          |  271360 non-null |  object |
|  7  |    Image-URL-L          |  271357 non-null |  object |
--------------------------------------------------------------

dtypes: object(8)

memory usage: 16.6+ MB

Setelah mengeksekusi kode di atas, dapat dilihat bahwa seluruh kolom pada dataset Books.csv memiliki tipe yang berupa data object. Ada hal unik yang didapati ketika menjalankan kode di atas, dapat dilihat bahwa kolom Year-Of-Publication bertipe data object sedangkan tahun publikasi umumnya bertipe data integer, oleh karena itu perlu adanya perbaikan pada tipe data.
Hasil Perbaikan tipe data

| ISBN                  |  object |
|-----------------------|---------|
| Book-Title            |  object |
| Book-Author           |  object |
| Year-Of-Publication   |   int64 |
| Publisher             |  object |
| Image-URL-S           |  object |
| Image-URL-M           |  object |
| Image-URL-L           |  object |
| dtype: object         |         |
-----------------------------------


* **```Ratings```**
  
  <class 'pandas.core.frame.DataFrame'>
  
RangeIndex: 1149780 entries, 0 to 1149779

Data columns (total 3 columns):

|  #  |  Column       |   Non-Null Count   |    Dtype    | 
|-----|---------------|--------------------|-------------|  
|  0  |  User-ID      |  1149780 non-null  |   int64     | 
|  1  |  ISBN         |  1149780 non-null  |   object    | 
|  2  |  Book-Rating  |  1149780 non-null  |   int64     |
----------------------------------------------------------

dtypes: int64(2), object(1)

memory usage: 26.3+ MB

Setelah menjalankan kode di atas, dapat dilihat bahwa kolom User-ID dan Book-Rating pada dataset Ratings.csv memiliki tipe data integer sedangkan kolom ISBN bertipe object.


Berdasarkan .isnull().sum() dari masing-masing DataFrame, ditemukan kondisi missing value sebagai berikut:
```**Books.csv:**```

* ```Book-Author```: 2 nilai kosong

* ```Year-Of-Publication```: 0 nilai kosong

* ```Publisher```: 2 nilai kosong

* Kolom gambar (```Image-URL-S```, ```Image-URL-M```, ```Image-URL-L```) tidak memiliki nilai kosong.

```**Ratings.csv:**```

Tidak terdapat missing value pada kolom manapun.



### Univariate Analysis

Dilakukan analisa dengan teknik *univarate* EDA untuk mengetahui informasi yang ada pada variabel di dataset. Analisa hanya dilakukan di beberapa variabel sesuai dengan kebutuhan sistem rekomendasi.

**Jumlah Buku Berdasarkan Penulis**

![image](https://github.com/user-attachments/assets/d7c91c11-051d-4ed9-8926-199d618094f6)

Gambar 1. Grafik Jumlah Buku Berdasarkan Penulis

Pada Gambar 1 terlihat data Analisis terhadap kolom Book-Author menunjukkan bahwa penulis Agatha Christie merupakan penulis paling produktif dalam dataset, dengan jumlah buku lebih dari 600 judul. Diikuti oleh William Shakespeare dan Stephen King, yang juga memiliki lebih dari 500 judul buku masing-masing.

Visualisasi dalam bentuk diagram batang memperlihatkan 20 penulis teratas berdasarkan jumlah buku yang mereka tulis. Hal ini menunjukkan adanya dominasi oleh beberapa penulis terkenal yang sangat produktif dalam industri penerbitan buku.

**Penerbit teratas berdasarkan jumlah buku**

Gambar 2. Nama Penerbit teratas berdasarkan jumlah buku

![image](https://github.com/user-attachments/assets/4aa03660-a518-4819-99b6-958e9327edcf)

Dilihat dari Gambar 2 didapatkan informasi sebagai berikut :

-Selanjutnya, dilakukan analisis terhadap kolom Publisher. Ditemukan bahwa penerbit Harlequin menjadi penerbit dengan jumlah buku terbanyak dalam dataset, yaitu lebih dari 7000 judul buku. Hal ini mengindikasikan bahwa Harlequin merupakan salah satu penerbit paling aktif.
Visualisasi bar chart menunjukkan 20 penerbit teratas, yang sebagian besar terdiri dari penerbit komersial besar dan mapan dalam industri penerbitan.

**Tahun Terbit Buku**

Gambar 3. Tahunn terbit buku teratas

![image](https://github.com/user-attachments/assets/a4a6b8a0-d99c-4a31-bcc0-c0bef764bab9)

Dilihat dari Gambar 3 didapatkan informasi sebagai berikut :

Distribusi terhadap Year-Of-Publication menunjukkan bahwa tahun 2002 merupakan tahun dengan jumlah penerbitan buku terbanyak, yaitu lebih dari 17.500 buku. Grafik yang dihasilkan menampilkan 20 tahun teratas berdasarkan frekuensi penerbitan buku.
Hal ini dapat disebabkan oleh meningkatnya digitalisasi dan distribusi data buku yang lebih masif pada awal 2000-an.

**Rating Buku**

Gambar 4. Visualisasi Frekuensi Jumlah Rating 

![image](https://github.com/user-attachments/assets/e1a6789a-47cc-438a-b856-9c196baaf3c9)


Dilihat dari Gambar 4 didapatkan informasi sebagai berikut :

Distribusi dari Book-Rating menunjukkan bahwa sebagian besar buku mendapatkan rating 0, yang kemungkinan besar menunjukkan tidak adanya rating dari pengguna, bukan berarti buku tersebut tidak disukai. Histogram yang ditampilkan menunjukkan frekuensi rating dari skala 0 hingga 10.
Distribusi ini memberikan gambaran bahwa terdapat sejumlah besar data yang belum mendapatkan evaluasi atau penilaian dari pembaca.

**Buku dengan Rata-Rata Rating Tertinggi**

Setelah dilakukan penggabungan data antara buku dan rating, dihitung rata-rata rating untuk setiap judul buku. Ditemukan bahwa beberapa buku mendapatkan rata-rata rating tertinggi yaitu 10.0, contohnya:

* Dark Justice
* California Historical Landmarks
* Isms: a dictionary of words ending in -ism, -ology, and -phobia
* 1,001 Things Everyone Should Know About American History
* 10 Real SATs, Third Edition

Buku-buku tersebut mendapatkan penilaian sempurna dari seluruh pengguna yang memberikan rating.

**Buku dengan Rata-Rata Rating Terendah**
Sebaliknya, ditemukan juga beberapa buku dengan rata-rata rating terendah yaitu 0.0, seperti:

* Always Have Popsicles
* Apple Magic (The Collector's series
* Harry Potter and the Bible: The Menace Behind the Magick
* Pokemon: The Official Collector's Sticker Book
* Til the Fat Lady Sings
  
## Data Preparation.

Sebelum melakukan tahap *data preparation*, dataset perlu melalui proses pengolahan awal. Hal ini disebabkan karena data masih tersebar dalam dua file berbeda berformat **comma separated values (CSV)**. Adapun langkah-langkah yang dilakukan dalam tahap ini meliputi:

* **Penggabungan Dataset.** Kedua sumber data, yaitu `Books.csv` dan `Ratings.csv`, masih terpisah. Oleh karena itu, dilakukan penggabungan antara keduanya menggunakan variabel `ISBN` sebagai kunci unik untuk setiap buku.

* **Penghapusan Kolom Tidak Relevan.** Setelah penggabungan, masih terdapat beberapa kolom yang tidak diperlukan dalam proses pembuatan model. Untuk menyederhanakan dan mengurangi dimensi data, hanya kolom `User-ID`, `ISBN`, dan `Book-Rating` yang dipertahankan, sementara kolom lainnya dihapus seperti `Book-Title`, `Book-Author`, `Year-Of-Publication`, `Publisher`, dan URL gambar.

  Sebelum kolom `Year-Of-Publication` dihapus, telah dilakukan proses pembersihan terhadap nilai-nilai tidak valid yang muncul pada kolom tersebut, seperti `'DK Publishing Inc'` dan `'Gallimard'`. Nilai-nilai tersebut dihapus, lalu tipe data kolom diubah menjadi bilangan bulat (`integer`) agar data menjadi konsisten. Proses ini dilakukan pada tahap *Data Understanding* sebelum data diproses lebih lanjut.

Langkah-langkah yang dilakukan untuk menyiapkan data (*Data Preparation*) selanjutnya adalah sebagai berikut:


* **Penanganan Data Kosong (Missing Value)**.

Pada dataset `ratings`, tidak ditemukan adanya nilai yang hilang, sehingga tidak diperlukan penanganan khusus pada tahap ini.

Sementara itu, pada dataset `books`, terdapat masing-masing 2 nilai kosong pada kolom `Book-Author` dan `Publisher`. Namun, kolom-kolom ini tidak digunakan dalam proses pembangunan model rekomendasi, sehingga dihapus pada tahap pembersihan data bersama dengan atribut lain yang dianggap tidak relevan. Dengan demikian, missing value tersebut tidak memengaruhi proses pemodelan dan tidak perlu ditangani secara eksplisit.

* **Proses Encoding**.

Dilakukan proses encoding, yaitu mengubah format data menjadi bentuk lain yang lebih mudah diproses oleh sistem. Pada tahap ini, variabel ```ISBN``` dan ```User-ID``` diubah ke dalam format indeks bilangan bulat ```integer``` untuk memudahkan proses pelatihan model di tahap berikutnya.

* **Normalisasi Variabel.**

Dilakukan normalisasi atau skala ulang terhadap variabel Book-Rating ke dalam rentang nilai antara ```0``` hingga ```1```. Tujuan dari normalisasi ini adalah untuk mempercepat dan mempermudah proses pelatihan model serta agar data lebih mudah dipahami oleh algoritma.

* **Pembagian Data Latih dan Data Uji**.

 Dataset dibagi menjadi dua bagian, yaitu ```80%``` sebagai data **latih** dan ```20%``` sebagai data **uji**. Dalam proyek ini, digunakan dua metode pembagian data, yakni: 
 a. pembagian menggunakan fungsi ```train_test_split``` dari pustaka **Surprise** untuk model dengan metode **SVD**, 
 b. pembagian berdasarkan persentase untuk model yang menggunakan pendekatan **Neural Network**.
## Modeling

Proyek ini berfokus pada metode collaborative filtering, yaitu pendekatan yang merekomendasikan item (dalam hal ini buku) kepada pengguna berdasarkan preferensi atau perilaku pengguna lain yang serupa. Informasi utama yang digunakan sebagai dasar rekomendasi adalah penilaian pengguna terhadap buku, yang disimpan dalam **Rating Buku** .

Dalam pengembangan sistem rekomendasi ini, digunakan dua pendekatan **collaborative filtering**. Salah satu teknik yang diterapkan adalah **collaborative filtering berbasis Single Value Decomposition (SVD)**. Implementasi teknik SVD dilakukan menggunakan pustaka   ```Surprise```, yang dirancang khusus untuk membangun dan mengevaluasi sistem rekomendasi.

SVD bekerja dengan merepresentasikan interaksi antara pengguna dan item dalam bentuk matriks, di mana setiap baris mewakili pengguna dan setiap kolom mewakili buku. Matriks ini kemudian difaktorisasi menjadi tiga komponen utama:

* Matriks U, yang merepresentasikan hubungan antara pengguna dan latent factor,

* Matriks S, yakni matriks diagonal yang menunjukkan tingkat kontribusi atau variasi dari masing-masing latent factor, dan

* Matriks V, yang merepresentasikan hubungan antara buku dan latent factor.

Latent factor sendiri merupakan fitur tersembunyi yang mengungkap karakteristik atau pola tertentu dari buku dan preferensi pengguna, yang dalam proyek ini dilandaskan pada nilai Book-Rating. Melalui pendekatan ini, sistem dapat memetakan hubungan kompleks antara pembaca dan buku secara lebih efisien, sekalipun sebagian besar data penilaian bersifat spars (jarang).


## **X = USV**T

  Kelebihan dan kekurangan SVD dijelaskan dibawah ini :

  * Kelebihan
    * Mereduksi dimensi
    * Efisien dalam proses komputasi
  * Kekurangan
    * Membutuhkan resource yang lebih besar untuk komputasi dataset yang sangat besar
    * Sensitif terhadap data *outliers*

Hasil dari prediksi  dapat dilihat di Tabel 1.

  Tabel 1.Daftar 10 teratas rekomendasi buku untuk pembaca dengan User-ID 276729 dengan teknik **SVD**

|	       |  ISBN	      | Book-Title	                                    |  Book-Author	       | prediction_rate |
|--------|--------------|-------------------------------------------------|----------------------|-----------------|
| 0	     |  034545104X	| Flesh Tones: A Novel	                          |   M. J. Rose	       | 0.283867        |
| 766517 |	0671665871	| GOING HOME	                                    |   Danielle Steel	   | 0.283867        |
| 766523 |	0671690582	| WHISPER OF DEATH : WHISPER OF DEATH	            |   Christopher Pike	 | 0.283867        |
| 766522 |	0671690094	| ANNE FRANK: DIARY OF A YOUNG GIRL	              |   Anne Frank	       | 0.283867        |
| 766521 |	067167630X	| BOOMER	                                        |   Charles Taylor	   | 0.283867        |
| 766520 |	067167465X	| BEST OF ENEMIES (NANCY DREW HARDY BOY SUPERMYS..|   Carolyn Keene	     | 0.283867        |
| 766519 |	0671673513	| The SILENCE OF THE LAMBS	                      |   Thomas Harris	     | 0.283867        |
| 766518 |  0671670662	| WEB OF DREAMS (Casteel Saga (Paperback))	      |   V.C. Andrews       | 0.283867        |
| 766516 |	0671664549	| Happy Birthday, Moon (Moonbear)	                |   Frank Asch	       | 0.283867        |
| 766525 |	0671692550	| The Tale of Peter Rabbit (Sticker Book)         |	  Beatrix Potter     | 0.283867        |

  

* *Collaborative filtering* dengan teknik *Neural Network*. Pada proyek ini implementasi *collaborative filtering* dengan teknik Neural Network menggunakan bantuan Keras model yang terinspirasi dari *class* [RecommenderNet](https://keras.io/examples/structured_data/collaborative_filtering_movielens/). Model *Neural Network* yang digunakan menggunakan BinaryCrossentropy sebagai *loss function*, Adam (*Adaptive Moment Estimation*) sebagai *optimizer* dan RMSE (*Root Mean Square Error*) sebagai matriks evaluasi. Hyperparameter yang digunakan adalah epoch sebesar 4 dan batch_size sebesar 500. Nilai ini didapatkan dengan cara *trial and error.*

  Proses yang ada di model RecommenderNet adalah *match score* antara pembaca dan buku dihitung menggunakan *dot product* kemudian hasil ini ditambahkan dengan nilai bias pembaca dan bias buku. Hasil akhir akan di skala ulang dengan nilai 0 sampai 1 menggunakan *sigmoid activation* yang mana nilai rating sudah di skala ulang menjadi 0 sampai 1 di tahap persiapan data. Jumlah *embedding layer* yang digunakan adalah 4. Ilustrasi cara kerja *Neural Network* dapat dilihat di Gambar 5.

  ![Image](https://github.com/user-attachments/assets/e82e74d7-d1bb-4e0d-8824-ef199ac7ed3d)

  Gambar 5. Ilustrasi Cara Kerja Neural Network di Sistem Rekomendasi

  * Kelebihan
    * Bagus untuk model dengan input dengan banyak dimensi
    * Didesain untuk melakukan pembelajaran yang berkelanjutan (**continuous learning*)
  * Kekurangan
    * Memakan banyak waktu dalam proses pelatihan data
    * Bergantung kepada data latih sehingga rentan terhadap *overfitting*

  
  Hasil dari prediksi  dapat dilihat di Tabel 2.

  Tabel 2.Daftar 10 teratas rekomendasi buku untuk pembaca dengan User-ID 276729 dengan teknik **Neural Network**

|   	    |    ISBN       |  Book-Title                                             | 	 Book-Author       | 
|---------|---------------|---------------------------------------------------------|----------------------| 
|  47213	|  0373764359	  |  His Majesty, M.D. (Man Of The Month/The Royal ...	    |   Leanne Banks       | 
|  57191	|  0373246005	  |  Where You Least Expect It (Silhouette Special ...	    |   Tori Carrington    | 
|  57639	|  0140048103	  |  A Square of Sky and a Touch of Earth                 	|   Janina David       | 
|  105002	|  0789459698	  |  Essential Managers: Managing Budgets                   |   Stephen Brookson   | 
|  189894	|  0586061657	  |  The Panther Book of Scottish Short Stories	            |   James Campbell     | 
|  196622 |  1558749527	  |  Perfect Daughters (Revised Edition)	                  |   Robert J. Ackerman | 
|  207403	|  0380778491	  |  A Question of Innocence                                |   Brandilyn Collins  | 
|  218071	|  1878624393	  |  There's an Elephant in the Bathtub (Storytime ...	    |   Jo Albee           | 
|  240999	|  0465039138	  |  Code and Other Laws of Cyberspace                      |   Lawrence Lessig    | 
|  259193	|  0821730533   |  Delightful Deception (Regency)                         |  	Nancy Lawrence     | 
  	

## Evaluation

Root Mean Squared Error (RMSE) merupakan salah satu metrik evaluasi yang digunakan untuk mengukur seberapa besar perbedaan antara nilai yang diprediksi oleh model dan nilai sebenarnya. RMSE diperoleh dengan cara menghitung akar kuadrat dari rata-rata selisih kuadrat antara nilai prediksi dan nilai aktual. Semakin kecil nilai RMSE, maka semakin baik dan akurat performa model dalam melakukan prediksi.

Rumus RMSE

![Image](https://github.com/user-attachments/assets/70e12977-4477-4753-a8c2-d323dd6bd972)

**Keterangan:**

* Dengan n = jumlah dataset
* yi = nilai sebenarnya
* ŷi = nilai prediksi


Nilai dari RMSE dari tiap pendekatan model dapat dilihat di Tabel 1.

Tabel 3. Tabel Hasil RMSE (*Root Mean Squared Error*) tiap model

|                | test     |
| -------------- | -------- |
| SVD            | 0.343696 |
| Neural Network | 0.439319 |

Dari Tabel 3 diketahui bahwa nilai RMSE yang dihasilkan oleh metode SVD lebih rendah dibandingkan dengan metode Neural Network, yakni sebesar 0.343696 untuk SVD dan0.439319 untuk Neural Network. Nilai tersebut mengindikasikan bahwa SVD memiliki kinerja prediksi yang lebih akurat dalam sistem rekomendasi buku berbasis collaborative filtering. Rentang nilai RMSE antara 0.3 hingga 0.4 masih dianggap cukup baik dalam konteks sistem rekomendasi. Meskipun performa Neural Network saat ini belum melampaui SVD, metode ini tetap memiliki peluang untuk ditingkatkan melalui penyempurnaan seperti tuning hyperparameter, modifikasi arsitektur jaringan, serta perbaikan kualitas data latih. Oleh karena itu, pendekatan Neural Network tetap relevan dan dapat dipertimbangkan untuk pengembangan sistem rekomendasi di tahap berikutnya.
## Kesimpulan

Melalui serangkaian tahapan yang telah dilakukan, berhasil dikembangkan sebuah sistem rekomendasi buku berbasis collaborative filtering dengan memanfaatkan dua pendekatan, yaitu teknik SVD dan Neural Network. Sistem ini menggunakan data rating dari pengguna lain sebagai dasar dalam memberikan rekomendasi, sehingga buku-buku yang disarankan merupakan buku yang dianggap menarik oleh pembaca sebelumnya. Harapannya, dengan menyajikan rekomendasi yang relevan dan menarik, sistem ini dapat mendorong minat pembaca baru untuk mulai membaca, serta turut berkontribusi dalam meningkatkan budaya literasi di Indonesia.

Kedua teknik yang diterapkan menunjukkan hasil yang menjanjikan dengan nilai RMSE yang relatif rendah, menandakan kecocokan dalam membangun sistem rekomendasi buku. Meskipun keduanya efektif, Neural Network dipilih sebagai pendekatan yang lebih unggul karena hasil RMSE-nya lebih rendah dibandingkan dengan teknik SVD. Selain itu, Neural Network memiliki potensi besar untuk ditingkatkan performanya melalui optimasi parameter seperti jumlah epoch, batch size, serta perbaikan kualitas data pelatihan. Oleh karena itu, Neural Network dinilai lebih tepat untuk digunakan dalam pengembangan lanjutan sistem rekomendasi ini.
## Referensi

1.  (https://journal.unesa.ac.id/index.php/jpi/article/view/140)] Kasiyun, Suharmono. "Upaya meningkatkan minat baca sebagai sarana untuk mencerdaskan bangsa." (2015): 81.
2.  (https://ejournal.akprind.ac.id/index.php/technoscientia/article/view/612)] Irfan, Mohammad, and Andharini Dwi Cahyani. "Sistem Rekomendasi: Buku Online Dengan Metode Collaborative Filtering." *Jurnal Teknologi Technoscientia* (2014): 076-84
3.  (https://ieeexplore.ieee.org/abstract/document/6615466)] Ba, Qilong, Xiaoyong Li, and Zhongying Bai. "Clustering collaborative filtering recommendation system based on SVD algorithm." *2013 IEEE 4th International Conference on Software Engineering and Service Science*. IEEE, 2013.
4.  (https://dl.acm.org/doi/abs/10.5555/1983862.1983922)] Vassiliou, Charalampos, et al. "A recommender system framework combining neural networks & collaborative filtering." *Proceedings of the 5th WSEAS international conference on Instrumentation, measurement, circuits and systems*. 2006.
