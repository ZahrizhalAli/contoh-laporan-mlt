# Laporan Proyek Machine Learning - Zahrizhal Ali

## Domain Proyek

Sebuah perusahaan distribusi wine berhasil melakukan audit dari berbagai sampel data pembelian wine menggunakan pendekatan analisis kimia, hal ini dikarenakan terdapat beberapa supplier yang mencoba untuk memasukkan produk dengan kualitas rendah demi mendapatkan harga yang tinggi. Maka dari itu kita akan menggunakan data sampel yang telah dikumpulkan untuk mendeteksi wine berkualitas rendah yang akan berlabel 'Fraud'.

Referensi data source: P. Cortez, A. Cerdeira, F. Almeida, T. Matos and J. Reis. Modeling wine preferences by data mining from physicochemical properties. In Decision Support Systems, Elsevier, 47(4):547-553, 2009.

## Business Understanding


### Problem Statements

Pernyataan masalah latar belakang:
- Apakah machine learning tradisional dapat digunakan untuk mendeteksi dan mengklasifikasikan wine berkualitas rendah melalui fitur sampel.
- Evaluasi performa metriks yang akan dibutuhkan untuk menentukan kualitas performa dari machine learning model.

### Goals

Tujuan dari pernyataan masalah:
- Menggunakan machine learning tradisional yaitu model algoritma klasifikasi seperti Support Vector Machine untuk mendeteksi fraud sehingga akan mempermudah perusahaan untuk menentukan aspek seperti apa yang akan diperhatikan kedepannya untuk mengetahui dengan mudah jenis wine berkategori rendah atau Fraud.
- Meninjau analisis metriks seperti akurasi, presisi, recall dan f1-score untuk melihat hasil performa model

## Data Understanding

Berdasarkan sumber referensi artikel dari dataset resmi study dataset init adalah vinho verde, yang merupakan produk dari Portugal. Data yang digunakan ini mencakup sekitar 15% total produksi wine di Portulag dan 10% total yang di export. Secara keseluruhan, total fitur pada datasett ini adalah 13 dengan 2 diantaranya merupakan tipe data object yaitu type dan quality. Beberapa fitur numeric lainnya adalah hitungan-hitungan larutan kimia yang terkandung pada produk.

Sumber Dataset: https://www.kaggle.com/datasets/asmaabdolahpoor/wine-fraud

### Variabel-variabel yang digunakan:
- ﬁxed acidity (g(tartaric acid)/dm3
- volatile acidity (g(acetic acid)/dm3)
- citric acid (g/dm3
- residual sugar (g/dm3
- chlorides (g(sodium chloride)/dm3
- free sulfur dioxide (mg/dm3
- total sulfur dioxide (mg/dm3)
- density (g/cm3)
- pH
- alcohol (% vol.)
- sulphates (g(potassium sulphate)/dm3)

## Data Preparation
Setelah melakukan Exploratory Data Analysis untuk memahami dataset yang akan digunakan,
Langkah pertama kita memisahkan Fitur dan Label dikarenakan studi kasus ini adalah supervised learning. teknik yang digunakan menggunakan bantuan pandas library. Dalam hal ini, X adalah feature dan y adalah label (quality)

Langkah selanjutnya, untuk menguji kelayakan performa model maka model harus dilatih kedalam dataset training terlebih dahulu dan kemudian melakukan evaluasi ke dataset testing. Dataset training adalah dataset yang dipelajari secara langsung oleh mdoel sedangkan data testing adalah data yang diujikan dari hasil belajar sebelumnya. Teknik yang digunakan pada tahap ini adalaha train test split menggunakan 10% data testing dari total data.

Langkah selanjutnya adalah standarisasi data dikarenakan beberapa fitur memiliki rentang nilai yang cukup berbeda sehingga memungkingkan terjadinya pelemahan proses belajar atau mengidentifikasi prediksi.
## Modeling
Model machine learning yang akan digunakan adalah Support Vector Machine atau Support Vector Classifier yang bertugas khusus untuk classification task. Dalam dokumentasi Scikit-learn , SVC menggunakan metode pengukuran one-versus-one atau OvO untuk membandingkan hasil, hal ini sangat berguna terkhusus karena kita hanya melakukan binary classification.
Beberapa hyperparameter yang digunakan diantaranya:

class_weight : memberikan peningkatan importance pada sampel tertentu sehingga menguntungkan meskipun menggunakan dataset yang imbalance
C : Parameter untuk teknik regularisasi dan harus bernilai positif.
gamma : koefisien untuk kernel seperti rbf, poly. bernilai 'auto' atau dapat juga berupa float. jika auto maka nilai gamma = 1/n_features.

Selanjutnya untuk mengimprovisasi model, akan digunakan teknik Grid Search yang akan secara otomatis melakukan training model melalui konfigurasi inputan manual paramater grid dan akan menghasilkan model dengan parameter terbaik yang akan berpengaruh pada hasil performa.


## Evaluation
Metriks evaluasi yang diukur adalah:
* Precision : total kelas yang benar dari total prediksi 
* Recall  : total kelas yang benar dari total kelas keseluruhan
* Accuracy : total prediksi yang benar
* F1 : Harmonic mean dari precision dan recall
