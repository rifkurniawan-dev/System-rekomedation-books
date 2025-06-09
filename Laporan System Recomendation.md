# **Laporan Proyek Machine Learning Terapan 2**


---

# **Detail Laporan : System Recommendation Books**

---

## Project Overview

Pengetahuan memegang peran krusial dalam kehidupan manusia. Melalui pengetahuan, individu dapat memahami berbagai aspek dalam hidup dan meningkatkan kualitas hidup mereka. Oleh karena itu, memahami dan mempelajari ilmu pengetahuan menjadi hal yang sangat penting. Salah satu cara yang paling mudah dan efektif untuk mengakses pengetahuan adalah melalui buku. Buku menyimpan berbagai pemikiran dan informasi dari penulis yang dikemas dalam bentuk narasi, ilustrasi, maupun bentuk lainnya. Aktivitas membaca memungkinkan seseorang memahami hal-hal yang sebelumnya belum diketahui.

Terdapat ungkapan bahwa buku adalah jendela dunia. Namun kenyataannya, tingkat minat baca masyarakat Indonesia tergolong sangat rendah. Berdasarkan data, indeks literasi Indonesia hanya mencapai 0,001 — artinya dari seribu orang, hanya satu yang memiliki ketertarikan tinggi terhadap aktivitas membaca [1]. Angka ini sangat jauh jika dibandingkan dengan negara-negara maju seperti Amerika Serikat (0,45) dan Singapura (0,55), yang menunjukkan tingginya budaya membaca di negara tersebut. Hal ini menjadi alarm penting bagi Indonesia untuk mendorong peningkatan minat baca.

Salah satu hambatan utama yang dihadapi masyarakat dalam memulai kebiasaan membaca adalah kesulitan dalam menemukan buku yang sesuai dengan minat. Meski banyak pilihan buku tersedia, tanpa panduan atau rekomendasi, calon pembaca sering kali bingung menentukan pilihan. Akibatnya, motivasi membaca pun bisa cepat menghilang. Oleh karena itu, dibutuhkan sebuah sistem yang mampu membantu individu menemukan buku yang relevan dengan preferensi mereka, guna mendorong semangat membaca di kalangan masyarakat. 

Salah satu solusi yang dapat dimanfaatkan untuk membantu seseorang dalam menemukan buku yang sesuai adalah dengan membangun sistem rekomendasi buku. Sistem ini bertujuan untuk menyarankan buku-buku kepada pengguna berdasarkan preferensi atau riwayat bacaan, sehingga proses pencarian buku menjadi lebih efisien dan terarah [2]. Sistem rekomendasi tersebut memanfaatkan data dari ulasan atau penilaian pengguna lain untuk menyajikan daftar buku yang kemungkinan besar akan disukai oleh pengguna baru. Dengan adanya sistem ini, diharapkan pembaca pemula dapat lebih mudah menemukan bacaan yang sesuai dengan ketertarikannya. Dalam pengembangannya, pendekatan yang digunakan adalah collaborative filtering, yaitu metode yang memanfaatkan interaksi dan perilaku pembaca lain sebagai dasar rekomendasi.

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

Dataset yang digunakan dalam pengembangan sistem rekomendasi buku diperoleh dari Kaggle **Book Recommendation Dataset**. Dataset ini mencakup tiga jenis data utama: data **buku (books), data pengguna (users), dan data penilaian (ratings)**. Secara keseluruhan, terdapat 278.858 entri pengguna dengan total 1.149.780 penilaian terhadap 271.360 buku. Dataset ini terdiri dari tiga file berformat comma-separated values (CSV), yaitu ```Books.csv```, ```Ratings.csv```, dan ```Users.csv```.

Penjelasan masing-masing file dalam dataset ini adalah sebagai berikut:

* ```Books.csv```: Berisi data mengenai buku-buku yang diperoleh dari Amazon Web Services, mencakup informasi detail seperti ISBN, Judul Buku, Penulis Buku, Tahun Terbit, Penerbit dan URL Gambar S
* ```Ratings.csv```: Menyajikan data penilaian yang diberikan oleh pengguna terhadap buku dengan skala 0 hingga 10, di mana nilai yang lebih tinggi menunjukkan tingkat apresiasi yang lebih besar terhadap buku tersebut.

* ```Users.csv```: Memuat informasi tentang para pembaca, termasuk ID pengguna yang telah dianonimkan serta data demografi seperti lokasi dan usia.


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

**Fitur pada Data Users:**

* ```User-ID```: Identifikasi unik pembaca dalam bentuk bilangan bulat.

* ```Location```: Lokasi tempat tinggal pengguna.

* ```Age```: Usia pengguna.

**Fitur pada Data Ratings:**

* ```User-ID```: ID pengguna yang memberikan penilaian.

* ```ISBN```: Kode unik dari buku yang dinilai.

* ```Book-Rating```: Skor penilaian terhadap buku, dengan rentang 0 hingga 10. Nilai 0 menunjukkan bahwa pengguna belum memberikan rating.


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
  
## Data Preprocessing

Sebelum melakukan tahap data preparation, dataset perlu melalui proses pengolahan awal. Hal ini disebabkan karena data masih tersebar dalam tiga file berbeda berformat **comma separated values (CSV)**. Adapun langkah-langkah yang dilakukan dalam tahap ini meliputi:

* Penggabungan Dataset. Ketiga sumber data, yaitu ```Books.csv```, ```Ratings.csv```, dan ```Users.csv```, masih terpisah. Oleh karena itu, dilakukan penggabungan antara Books.csv dan Ratings.csv menggunakan variabel ISBN sebagai kunci unik setiap buku. Sementara itu, ```Users.csv``` tidak digabungkan karena sistem rekomendasi yang dikembangkan tidak memanfaatkan data umur maupun informasi demografis pengguna.

* Penghapusan Kolom Tidak Relevan. Setelah penggabungan, masih terdapat beberapa kolom yang tidak diperlukan dalam proses pembuatan model. Untuk menyederhanakan dan mengurangi dimensi data, hanya kolom User-ID, ISBN, dan Book-Rating yang dipertahankan, sementara kolom lainnya dihapus.


## Data Preparation

Langkah-langkah yang dilakukan untuk menyiapkan data (*data preparation*) adalah sebagai berikut :


* **Penanganan Data Kosong (Missing Value)**.

Dalam dataset yang digunakan pada proyek ini, tidak ditemukan adanya nilai yang hilang, sehingga tidak diperlukan langkah khusus untuk menangani **missing value**.

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

|          ISBN    |   Book-Title                                     |	Book-Author   	|prediction_rate |
|-------|----------|--------------------------------------------------|-----------------|----------------|-
|0	    |034545104X|	Flesh Tones: A Novel	                          |M. J. Rose       |	0.284154       |
|766517	|0671665871|	GOING HOME	                                    |Danielle Steel   |	0.284154       |
|766523	|0671690582|	WHISPER OF DEATH : WHISPER OF DEATH	            |Christopher Pike	| 0.284154       |
|766522	|0671690094|	ANNE FRANK: DIARY OF A YOUNG GIRL	              |Anne Frank       | 0.284154       |
|766521	|067167630X|	BOOMER	                                        |Charles Taylor   |	0.284154       |
|766520	|067167465X|	BEST OF ENEMIES (NANCY DREW HARDY BOY SUPERMYS..|Carolyn Keene	  | 0.284154       |
|766519	|0671673513|	The SILENCE OF THE LAMBS	Thomas Harris	        |Thomas Harris    | 0.284154       |
|766518	|0671670662|	WEB OF DREAMS (Casteel Saga (Paperback))	      |V.C. Andrews	    | 0.284154       |
|766516	|0671664549|	Happy Birthday, Moon (Moonbear)	                |Frank Asch       |	0.284154       |
|766525	|0671692550|	The Tale of Peter Rabbit (Sticker Book)	        |Beatrix Potter	  | 0.284154       |
----------------------------------------------------------------------------------------------------------


* *Collaborative filtering* dengan teknik *Neural Network*. Pada proyek ini implementasi *collaborative filtering* dengan teknik Neural Network menggunakan bantuan Keras model yang terinspirasi dari *class* [RecommenderNet](https://keras.io/examples/structured_data/collaborative_filtering_movielens/). Model *Neural Network* yang digunakan menggunakan BinaryCrossentropy sebagai *loss function*, Adam (*Adaptive Moment Estimation*) sebagai *optimizer* dan RMSE (*Root Mean Square Error*) sebagai matriks evaluasi. Hyperparameter yang digunakan adalah epoch sebesar 8 dan batch_size sebesar 500. Nilai ini didapatkan dengan cara *trial and error.*

  Proses yang ada di model RecommenderNet adalah *match score* antara pembaca dan buku dihitung menggunakan *dot product* kemudian hasil ini ditambahkan dengan nilai bias pembaca dan bias buku. Hasil akhir akan di skala ulang dengan nilai 0 sampai 1 menggunakan *sigmoid activation* yang mana nilai rating sudah di skala ulang menjadi 0 sampai 1 di tahap persiapan data. Jumlah *embedding layer* yang digunakan adalah 4. Ilustrasi cara kerja *Neural Network* dapat dilihat di Gambar 9.

  ![Image](https://github.com/user-attachments/assets/e82e74d7-d1bb-4e0d-8824-ef199ac7ed3d)

  Gambar 6. Ilustrasi Cara Kerja Neural Network di Sistem Rekomendasi

  * Kelebihan
    * Bagus untuk model dengan input dengan banyak dimensi
    * Didesain untuk melakukan pembelajaran yang berkelanjutan (**continuous learning*)
  * Kekurangan
    * Memakan banyak waktu dalam proses pelatihan data
    * Bergantung kepada data latih sehingga rentan terhadap *overfitting*

  

  Hasil dari prediksi  dapat dilihat di Tabel 2.

  Tabel 2.Daftar 10 teratas rekomendasi buku untuk pembaca dengan User-ID 276729 dengan teknik **Neural Network**
  	
|       | ISBN	   |        Book-Title	                                |          Book-Author     |
|-------|--------  | ---------------------------------------------------| ------------------------ |
|27937  |0452280362|	Dreaming Southern	                                |     Linda Bruckheimer    |
|44011  |0964535203|Kombucha: How to and What It's All About            |	    Alana Pascal         |
|55318  |0805047174|Stopping for Death: Poems of Death and Loss         |	    Carol Ann Duffy      |
|78939  |1582341141|Mangoes and Quince: A Novel	                        |     Carol Field          |
|146801 |0671646877|	Scene of the Crime (The Hardy Boys Casefiles, ...	|     Franklin Dixon       |
|150467 |0843946474|	Keeper of My Heart	                              |     Penelope Neri        |
|168117 |0932592104|The Klutz Book of Knots: How to Tie the World'...   |	    John Cassidy         |
|172097 |0471527270|	Neanderthals at Work: How People and Politics ...	|     Albert J. Bernstein  |
|214910 |0451197348|	A Cat on Stage Left: An Alice Nestleton Myster... |     Lydia Adamson        |
|236975 |0020955707|	GOLDEN BOUGH	                                    |     James G, Sr. Fraser  |
----------------------------------------------------------------------------------------------------

  



## Evaluation

Metric yang digunakan untuk mengevaluasi model adalah RMSE (*Root Mean Squared Error*). RMSE menghitung akar dari rata-rata selisih kuadrat antara nilai prediksi dan nilai aktual atau bisa dikatakan akar kuadrat dari MSE (*Mean Squared Error*). Nilai RMSE yang kecil menunjukkan performa model yang lebih baik dan akurat.

Rumus RMSE

![Image](https://github.com/user-attachments/assets/70e12977-4477-4753-a8c2-d323dd6bd972)

```
Dengan n = jumlah dataset, yi = nilai sebenarnya , ŷi = nilai prediksi
```

Nilai dari RMSE dari tiap pendekatan model dapat dilihat di Tabel 1.

Tabel 3. Tabel Hasil RMSE (*Root Mean Squared Error*) tiap model

|                | test     |
| -------------- | -------- |
| SVD            | 0,343416 |
| Neural Network | 0,441751 |

Dari Tabel 3 terlihat bahwa nilai RMSE untuk teknik SVD lebih kecil dibandingkan dengan teknik Neural Network, yaitu sebesar 0.343416 untuk SVD dan 0.441751 untuk Neural Network. Hal ini menunjukkan bahwa teknik SVD memberikan performa yang lebih baik dalam hal akurasi prediksi pada sistem rekomendasi buku dengan metode collaborative filtering. Nilai RMSE sebesar 0.3 hingga 0.4 masih tergolong cukup baik dalam konteks sistem rekomendasi. Meskipun performa Neural Network saat ini belum melampaui SVD, teknik ini masih memiliki potensi untuk ditingkatkan lebih lanjut melalui optimasi hyperparameter, arsitektur jaringan, dan data pelatihan. Oleh karena itu, teknik Neural Network tetap dipertimbangkan dalam pengembangan lanjutan proyek ini.

## Kesimpulan

Dari tahapan yang sudah dilakukan sudah berhasil dibuat sistem rekomendasi buku dengan metode *collaborative filtering* dengan teknik SVD dan *Neural Network*. Sistem rekomendasi yang dibuat menggunakan data rating dari pembaca lainnya sebagai acuan sehingga akan merekomendasikan buku yang dianggap menarik oleh pembaca lainnya. Diharapkan dengan merekomendasi buku-buku yang menarik, pembaca baru dapat mulai tertarik untuk memulai membaca buku sehingga meningkatkan minat baca buku di Indonesia. 

Dari kedua teknik yang digunakan di proyek ini, keduanya memiliki kecocokan ketika diterapkan dalam membangun sistem rekomendasi buku dilihat dari nilai RMSE yang cukup kecil. Dari kedua teknik yaitu teknik SVD dan teknik Neural Network, teknik Neural Network yang dipilih sebagai teknik yang lebih akurat dan tepat. Teknik *Neural Network* dipilih karena memiliki banyak ruang untuk peningkatan performa dalam merekomendasikan buku selain itu hasil RMSE dari teknik *Neural Network* lebih kecil dari teknik SVD. Peningkatan performa ini dapat dilakukan dengan cara mengatur hyperparameter epoch, batch_size serta memperbaiki kualitas data latih. 

## Referensi

[[1](https://journal.unesa.ac.id/index.php/jpi/article/view/140)] Kasiyun, Suharmono. "Upaya meningkatkan minat baca sebagai sarana untuk mencerdaskan bangsa." (2015): 81.

[[2](https://ejournal.akprind.ac.id/index.php/technoscientia/article/view/612)] Irfan, Mohammad, and Andharini Dwi Cahyani. "Sistem Rekomendasi: Buku Online Dengan Metode Collaborative Filtering." *Jurnal Teknologi Technoscientia* (2014): 076-84.

[[3](https://ieeexplore.ieee.org/abstract/document/6615466)] Ba, Qilong, Xiaoyong Li, and Zhongying Bai. "Clustering collaborative filtering recommendation system based on SVD algorithm." *2013 IEEE 4th International Conference on Software Engineering and Service Science*. IEEE, 2013.

[[4](https://dl.acm.org/doi/abs/10.5555/1983862.1983922)] Vassiliou, Charalampos, et al. "A recommender system framework combining neural networks & collaborative filtering." *Proceedings of the 5th WSEAS international conference on Instrumentation, measurement, circuits and systems*. 2006.
