# Laporan Proyek Machine Learning - Sulaiman
## Project Overview
Peningkatan penggunaan internet di seluruh dunia menghasilkan data dalam jumlah yang sangat besar. Berbagai perangkat cerdas dan internet membuat data menjadi berlimpah. Perusahaan dan organisasi mengumpulkan data berjumlah besar untuk berbagai kepentingan, salah satunya proses merekomendasikan film yang sesuai untuk kebutuhan user. User akan mencari film dengan memanfaatkan fitur penilaian dari orang lain terlebih dahulu sebelum memutuskan menonton film tersebut. Dengan mengitegrasikan model Machine Learning ke dalam sistem, proses tersebut akan menjadi cepat dan akurat. Hal yang perlu di lakukan adalah memilih pendekatan sistem rekomendasi yang cocok untuk model Machine Learning kita.

## Business Understanding
Bagi perusahaan maupun organisasi penyedia layanan media streaming digital, era digital saat ini membuat data menjadi berlimpah, mudah serta cepat diperoleh. Dengan menggunakan sistem rekomendasi akan berdampak pada profit perusahaan, karena semakin tepat sistem dalam merekomendasikan film untuk konsumen dapat membuat konsumen semakin nyaman pada saat memilih dan menonton film yang mereka inginkan. 
#### 1. Problem Statement
Bagaimana cara mendapatkan film berdasarkan rating untuk memprediksi film yang mungkin diminati oleh user?
#### 2. Goal
Model Machine Learning dapat merekomendasikan film berdasarkan rating yang akurat dan sesuai dengan kebutuhan user/konsumen.
#### 3. Solution Approach
Dalam proyek ini saya menggunakan metode pendekatan Collaborative Filtering sebagai solusi permasalahan sistem rekomendasi. Dimana Collaborative Filtering adalah salah satu metode pada sistem rekomendasi. Metode ini memanfaatkan penilaian pengguna lain berupa rating atau umpan balik lain untuk memprediksi item yang mungkin diminati.
## Data Understanding
Data ini (ml-latest-small) merupakan data film dengan peringkat bintang 5 dan aktivitas penandaan teks bebas dari MovieLens, layanan rekomendasi film. Data Ini berisi 100836 rating dan 3683 aplikasi tag di 9742 film. Data ini dibuat oleh 610 pengguna antara 29 Maret 1996 dan 24 September 2018. Kumpulan data ini dibuat pada 26 September 2018 [movielens.org](https://movielens.org).
Sumber Dataset Grouplens.org
[Link Download Dataset](https://files.grouplens.org/datasets/movielens/ml-latest-small.zip)

Dataset terbagi ke dalam beberapa file antara lain: links.csv, movies.csv, ratings.csv dan tags.csv. Dalam proyek ini saya memuat setiap file dataset ke beberapa variabel antara lain: link, movie, rating, dan tag.
- link: merupakan pengidentifikasi yang digunakan untuk menautkan ke sumber data film lainnya
- movie: merupakan Informasi film
- rating: merupakan penilaian pada setiap film
- tag: merupakan metadata yang dibuat pengguna tentang film.

Deskripsi variabel pada setiap file:
- **link**:
    - movieId merupakan identifier untuk film yang digunakan oleh [movielens](https://movielens.org)
    - imdbId merupakan identifier untuk film yang digunakan oleh  [imdb](http://www.imdb.com)
    - tmdbId adalah identifier untuk film yang digunakan oleh  [themovie](https://www.themoviedb.org)

- **movie**:
    - movieId merupakan identifier untuk film yang digunakan oleh [movielens](https://movielens.org)
    - titile merupakan nama film
    - genres merupakan genre pada film

- **tag**:
    - userId merupakan identifier untuk user
    - movieId merupakan identifier untuk film yang digunakan oleh [movielens](https://movielens.org)
    - timestamp merupakan detik sejak tengah malam Coordinated Universal Time(UTC)   tanggal 1 januari 1970

- **rating**:
    - userId merupakan identifier untuk user
    - movieId merupakan identifier untuk film yang digunakan oleh [movielens](https://movielens.org)
    - rating merupakan penilaian film
    - timestamp merupakan detik sejak tengah malam Coordinated Universal Time(UTC) tanggal 1 januari 1970

## Data Preparation
Data Preparation atau bisa disebut juga dengan data preprocessing adalah suatu proses/langkah yang dilakukan untuk membuat data mentah menjadi data yang berkualitas (input yang baik untuk data mining tools).
Data Preparation pada proyek ini berfungsi untuk mentransformasi pada data sehingga menjadi bentuk yang cocok untuk proses permodelan.
1. Mengahapus missing value
Salah satu alasan terjadinya missing value adalah tidak terkumpulnya beberapa informasi. Missing value menyebabkan informasi yang dikumpulkan belum clear sehingga sulit untuk dilakukan analisis. Dalam dunia data, kasus-kasus mengenai data wrangling banyak dijumpai. Hal ini membuat banyak sekali spekulasi atau alasan tertentu mengapa data tidak dapat dianalisis. Tetapi pada studi kasus kali ini data kita tidak terdapat missing value setelah melewati proses pengecekan.
2. Membuat dictionary
Dictionary adalah tipe data yang anggotanya terdiri dari pasangan kunci:nilai (key:value). Dictionary bersifat tidak berurut (unordered) sehingga anggotanya tidak memiliki indeks. Dictionary dibuat dengan menempatkan anggotanya di dalam tanda kurung kurawal { }, dipisahkan oleh tanda koma. Proses ini dilakukan setelah proses penghapusan data duplikat. Proses membuat dictionary berguna untuk mendapatkan data unik untuk memudahkan dalam proses pemodelan.

## Modelling and Result
Merekomendasikan film dengan rating paling tinggi dan rekomendasi film 10 teratas pada sampel user yang di ambil secara acak dan di definisikan variabel movie_not_visited yang merupakan daftar film yang belum pernah di putar oleh user. Pada kasus ini kita mendapatkan user dengan user_id 370, untuk memperoleh rekomendasi film menggunakan fungsi model.predict() dari library keras, dari output tersebut kita dapat membandingkan antara Movie with high ratings from user dan Top 10 movie recomendation. 

Hasil rekomendasi menunjukkan beberapa kategori film dengan kategori (genre) yang sesuai dengan rating user. Kita memperoleh rekomendasi film dengan kategori (genre) Drama terbanyak yaitu 6 film, genre Comedy sebanyak 5 film, genre Romance sebanyak 3 film, genre War sebanyak 2 film, genre Thriller sebanyak 2 film, genre Crime sebanyak 1 film, dan genre Documentary sebanyak 1 film. Pada masing-masing film  rata-rata memiliki beberapa genre yang dimiliki atau tidak hanya memiliki 1 genre.

Model yang di buat adalah model dengan metode pendekatan Collaborative Filtering dimana metode ini membutuhkan data rating dari pengguna untuk mendapatkan rekomendasi.

## Evaluation
Metrik yang digunakan pada Rekomendasi ini adalah (RMSE) Root Mean Square Error , merupakan besarnya tingkat kesalahan hasil prediksi, dimana semakin kecil (mendekati 0) nilai RMSE maka hasil prediksi akan semakin akurat. Root Mean Square Error digunakan dalam analisis perbandingan data lapangan dengan data hasil proses yang diolah untuk mengetahui tingkat kesalahan yang terjadi. RMSE merupakan nilai rata-rata dari jumlah kuadrat kesalahan atau jumlah kuadrat dari nilai prakiraan dan observasi.
Dari proses ini, memperoleh nilai error akhir sebesar sekitar 0.17 dan error pada data validasi sebesar 0.20.

Hasil plot metrik evaluasi RMSE dengan matplotlib pada [link](https://drive.google.com/file/d/1J140ZVENGclrE3foF0aIZJ2_-MIeBBDH/view?usp=sharing) 


