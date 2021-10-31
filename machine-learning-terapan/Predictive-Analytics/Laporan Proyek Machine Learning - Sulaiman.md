# Laporan Proyek Machine Learning - Sulaiman
## Domain Proyek
Peningkatan penggunaan internet di seluruh dunia menghasilkan data dalam jumlah yang sangat besar. Berbagai perangkat cerdas dan internet membuat data menjadi berlimpah. Perusahaan dan organisasi mengumpulkan data berjumlah besar untuk berbagai kepentingan, salah satunya proses pengambilan keputusan.
Metode pengambilan keputusan pada bisnis distributor dan retail pada saat ini masih menggunakan cara lama yaitu dengan menggunakan tenaga manusia, sedangkan Human Error adalah masalah umum yang dijumpai jika menggunakan cara tersebut. Mengingat pada saat ini data sangat berlimpah, ada baiknya jika menggunakan motode pengambilan keputusan dengan mengintegrasikan model Machine Learning ke dalam sistem.
Sebelum mengintegrasikan model ke dalam sistem hal yang perlu dilakukan adalah proses membuat model dengan menggunakan beberapa algortima Machine Learning, kemudian memilih algoritma mana yang menghasilkan error yang dengan nilai minimal/terkecil pada model Machine Learning.
## Business Understanding
Adapun model bisnis yang dijalankan adalah distributor dan retail, yakni perusahaan membeli mobil bekas dari produsen kemudian menjualnya kepada konsumen. Perusahaan juga menerima penjualan kembali mobil bekas dari konsumen. Penting bagi perusahaan untuk mengetahui dan dapat memprediksi harga mobil bekas di pasar. Prediksi akan digunakan untuk menentukan berapa harga beli yang pantas untuk mobil bekas dengan spesifikasi tertentu sehingga perusahaan bisa mendapatkan profit sebesar mungkin.

## Problem Statements
* Berapa harga pasar mobil bekas dengan spesifikasi tertentu?

## Goals
* Model Machine Learning dapat memprediksi harga mobil bekas dengan akurat berdasarkan spesifikasi yang ada.

## Solution statements
Dalam proyek ini saya menggunakan algoritma Machine Learning sebagai solusi permasalahan, yaitu Random Forest, KNN, dan Boosting Algorithm.
1. Random Forest
 Algoritma random forest adalah salah satu algoritma supervised learning. Ia dapat digunakan untuk menyelesaikan masalah klasifikasi dan regresi. Random forest juga merupakan algoritma yang sering digunakan karena cukup sederhana tetapi memiliki stabilitas yang mumpuni. Algoritma ini disusun dari banyak algoritma pohon (decision tree) yang pembagian data dan fiturnya dipilih secara acak.
2. KNN(K-Nearest Neighbor)
KNN adalah algoritma yang relatif sederhana dibandingkan dengan algoritma lain. Algoritma KNN menggunakan ‘kesamaan fitur’ untuk memprediksi nilai dari setiap data yang baru. Dengan kata lain, setiap data baru diberi nilai berdasarkan seberapa mirip titik tersebut dalam set pelatihan.
3. Boosting Algorithm
Algoritma boosting bekerja dengan membangun model dari data latih. Kemudian ia membuat model kedua yang bertugas memperbaiki kesalahan dari model pertama. Model ditambahkan sampai data latih terprediksi dengan baik atau telah mencapai jumlah maksimum model untuk ditambahkan. Algoritma ini sangat powerful dalam meningkatkan akurasi prediksi.  Caranya adalah dengan menggabungkan beberapa model sederhana dan dianggap lemah (weak learners) sehingga membentuk suatu model yang kuat (strong ensemble learner).
## Data Understanding
Dataset ini merupakan kumpulan data tentang mobil bekas dan berbagai fitur yang dimiliki, Dataset ini berisi informasi tentang mobil bekas yang tercantum pada www.cardekho.com. Dataset ini dapat digunakan untuk berbagai keperluan, contohnya  seperti prediksi harga.
Sumber dataset Kaggle.com
[link dataset](https://www.kaggle.com/abhikol/price-estimation-of-used-car-car-dekho/data?select=Car+details+v3.csv)

Deskripsi Variabel
1. name: nama mobil
2. year: tahun pembelian mobil
3. selling_price: harga yang diinginkan pemilik untuk menjual mobil
4. km_driven: jumlah kilometer yang ditempuh mobil tersebut
5. fuel: jenis bahan bakar mobil(Diesel/Petrol)
6. seller_type: mobil yang dijual oleh (individu/dealer)
7. transmission: transmisi gigi mobil (Automatic/Manual)
8. owner: pemilik
9. mileage: jarak tempuh mobil
10. engine: kapasitas mesin mobil
11. max_power: tenaga maksimal mobil
12. torque: torsi mobil
13. seats: jumlah penumpang

## Data Preparation
Data Preparation atau bisa disebut juga dengan data preprocessing adalah suatu proses/langkah yang dilakukan untuk membuat data mentah menjadi data yang berkualitas (input yang baik untuk data mining tools).
Data Preparation pada proyek ini berfungsi untuk mentransformasi pada data sehingga menjadi bentuk yang cocok untuk proses permodelan
1. Encoding fitur kategori
One-Hot Encoding adalah teknik yang merubah setiap nilai di dalam kolom menjadi kolom baru dan mengisinya dengan nilai biner dari variabel kategori ke variabel numerik menjadi 0 dan 1. One-hot-encoding berfungsi untuk mendapatkan fitur baru yang sesuai sehingga dapat mewakili variabel kategori.
2. Pembagian dataset dengan fungsi train_test_split
Membagi dataset menjadi data latih (train) dan data uji (test)
    - Data Train: Sebagai data yang digunakan model untuk belajar pola yang dimiliki data
    - Data Test: Berguna untuk memahami model bekerja di kondisi sesungguhnya (real-life situation)
    
    Pentingnya proses ini karena dalam Machine Learning, hal yang diharapkan adalah seberapa baik kinerja model ketika dihadapkan pada data yang belum pernah dilihat sebelumnya. Oleh karena itulah, harus selalu melatih dan menguji model menggunakan dua data yang berbeda.
3. Standarisasi.
Standarisasi membantu untuk membuat fitur data menjadi bentuk yang lebih mudah diolah oleh algoritma. Melakukan proses standarisasi setelah proses pembagian data train dan data test berguna untuk menghindari kebocoran informasi pada data uji, dengan menerapkan fitur standarisasi pada data latih.
Menggunakan teknik StandarScaler dari library Scikitlearn, StandardScaler melakukan proses standarisasi fitur dengan mengurangkan mean (nilai rata-rata) kemudian membaginya dengan standar deviasi untuk menggeser distribusi. 

## Modeling
Di tahap ini saya menggunakan 3 Algoritma Machine Learning antara lain Random Forest, KNN(K-Nearest Neighhbor), Boosting Algorithm, kemudian membandingkan performanya.
1. Random Forest
Random Forest berawal dari memecah data sampel yang ada kedalam decision tree secara acak. Setelah pohon terbentuk,maka akan dilakukan voting pada setiap kelas dari data sampel. Kemudian, mengkombinasikan vote dari setiap kelas kemudian diambil vote yang paling banyak.
2. KNN(K-Nearest Neighhbor)
KNN bekerja dengan membandingkan jarak satu sampel ke sampel pelatihan lain dengan memilih sejumlah k-tetangga terdekat
3. Boosting Algorithm
Boosting Algorithm bekerja dengan membangun model dari data latih. Kemudian ia membuat model kedua yang bertugas memperbaiki kesalahan dari model pertama. Model ditambahkan sampai data latih terprediksi dengan baik atau telah mencapai jumlah maksimum model untuk ditambahkan. 

Hasil evaluasi model dengan metrix MSE
Algoritma      |  	train |  	test 
------------ | ------------- | -------------
KNN | 1.09579e+08 | 1.39771e+08 |
RF | 3.75096e+07 | 2.03903e+08 |
Boosting | 2.69155e+08 | 3.52695e+08 |

Bar chart hasil evaluasi pada data latih dan data test bisa di lihat pada [link](https://drive.google.com/file/d/17MhgozLAmMyfYIW8qD6gbaZkfpGCHnSB/view?usp=sharing) 

Dari  tabel dan bar chart di atas, terlihat bahwa algoritma KNN pada model  memberikan nilai eror yang paling kecil dibandingkan algoritma Random Forest dan Boosting Algorthm pada proses train dan test yang dilakukan. Model inilah yang akan di pilih sebagai model terbaik untuk melakukan prediksi harga mobil.


## Evaluation
Metrik yang digunakan pada prediksi ini adalah MSE atau Mean Squared Error yang menghitung selisih rata-rata nilai sebenarnya dengan nilai prediksi.  Sebelum menghitung nilai MSE dalam model, perlu melakukan proses scaling fitur numerik pada data uji untuk menghindari kebocoran data.
MSE pada dasarnya mengukur kesalahan kuadrat rata-rata dari prediksi. Untuk setiap poin, ia menghitung selisih kuadrat antara prediksi dan target kemudian merata-rata nilai-nilai itu. Semakin tinggi nilai ini, semakin buruk modelnya. Nilai MSE tidak pernah negatif, karena menguadratkan kesalahan prediksi individu sebelum menjumlahkannya, tetapi akan menjadi nol untuk model yang sempurna. Kekurangan Metrik MSE adalah Jika membuat satu prediksi yang sangat buruk, kuadrat akan membuat kesalahan lebih buruk dan itu mungkin membuat metrik cenderung melebih-lebihkan keburukan model.
```
mse = pd.DataFrame(columns=['train', 'test'], index=['KNN','RF','Boosting'])
model_dict = {'KNN': knn, 'RF': RF, 'Boosting': boosting}
for name, model in model_dict.items():
    mse.loc[name, 'train'] = mean_squared_error(y_true=y_train, y_pred=model.predict(X_train))/1e3 
    mse.loc[name, 'test'] = mean_squared_error(y_true=y_test, y_pred=model.predict(X_test))/1e3
 
mse
```



