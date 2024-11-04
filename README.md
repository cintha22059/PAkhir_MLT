# Laporan Proyek AKhir Machine Learning Terapan - Cintha Hafrida Putri

## Domain Proyek

Pertumbuhan Popularitas Anime
Anime telah berkembang menjadi bagian integral dari budaya populer global, 
dengan jutaan penggemar setia di seluruh dunia. Dari berbagai genre dan gaya visual,
anime menawarkan lebih dari 12.000 judul yang membuat penggemar terus menikmati, mengeksplorasi, 
dan menemukan konten baru. Namun, dengan banyaknya pilihan yang tersedia, banyak pengguna merasa 
kesulitan dalam menemukan judul yang sesuai dengan selera pribadi mereka [(Muhammad., 2023_)](https://publishing-widyagama.ac.id/ejournal-v2/bcti/article/view/4885). 
Untuk menjawab tantangan ini, muncul kebutuhan akan sistem rekomendasi yang 
mampu memberikan saran yang lebih tepat dan relevan, disesuaikan dengan preferensi 
unik masing-masing pengguna.

## Business Understanding

### Problem Statements
- Pengguna kesulitan menemukan judul anime yang sesuai dengan preferensi mereka di antara ribuan pilihan yang tersedia.
- Kurangnya rekomendasi yang relevan membuat pengguna membutuhkan sistem yang dapat menyarankan anime yang belum pernah ditonton dan sesuai dengan minat mereka.
- Diperlukan metode yang dapat mengukur efektivitas sistem rekomendasi dalam memberikan saran yang akurat dan relevan bagi pengguna.

### Goals
- Mengembangkan sistem rekomendasi anime yang mampu memberikan saran anime yang sesuai dengan preferensi pengguna.
- Meningkatkan kepuasan pengguna dengan merekomendasikan anime yang belum pernah ditonton dan cocok dengan minat mereka.
- Mengukur kinerja sistem rekomendasi menggunakan metrik seperti precision untuk memastikan kualitas rekomendasi yang dihasilkan.

### Solution statements
- Menggunakan pendekatan content-based filtering berbasis cosine similarity untuk merekomendasikan anime berdasarkan kesamaan genre.
- Mengimplementasikan collaborative-based filtering untuk menganalisis preferensi pengguna berdasarkan rating yang telah diberikan, sehingga bisa merekomendasikan anime yang mungkin disukai oleh pengguna.
- Mengukur performa sistem dengan menggunakan metrik precision untuk memastikan rekomendasi yang relevan dan meningkatkan akurasi sistem dalam memberikan saran yang sesuai.

## Data Understanding
Dataset yang digunakan adalah Anime Dataset 2023 [(Anime_dataset_2023_kaggle)](https://www.kaggle.com/datasets/dbdmobile/myanimelist-dataset?select=users-details-2023.csv). 
Dmana dalam proyek ini hanya menggunakan dataset anime-dataset-2023, user-score, dan user-details.

Anime-datset-2023 
- Jumlah baris : 24905
- Jumlah kolom : 24
- Berikut adalah variabel-variabel pada anime-dataset-2023
  
| Kolom         | Deskripsi                                                                                                                                                          |
|---------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| anime_id      | ID unik untuk setiap anime.                                                                                                                                        |
| Name          | Nama asli anime dalam bahasa aslinya.                                                                                                                              |
| English name  | Nama anime dalam bahasa Inggris.                                                                                                                                   |
| Other name    | Nama atau judul asli anime dalam bahasa lain (misalnya Jepang, Tiongkok, atau Korea).                                                                              |
| Score         | Skor atau penilaian yang diberikan untuk anime tersebut.                                                                                                          |
| Genres        | Genre dari anime, dipisahkan dengan koma.                                                                                                                          |
| Synopsis      | Deskripsi singkat atau ringkasan alur cerita anime.                                                                                                               |
| Type          | Tipe anime (misalnya, serial TV, film, OVA, dll.).                                                                                                                |
| Episodes      | Jumlah episode dalam anime.                                                                                                                                        |
| Aired         | Tanggal ketika anime ditayangkan.                                                                                                                                  |
| Premiered     | Musim dan tahun ketika anime pertama kali tayang.                                                                                                                 |
| Status        | Status penayangan anime (misalnya, Selesai Ditayangkan, Sedang Ditayangkan, dll.).                                                                                |
| Producers     | Perusahaan produksi atau produser dari anime.                                                                                                                     |
| Licensors     | Pemberi lisensi anime (misalnya, platform streaming).                                                                                                             |
| Studios       | Studio animasi yang mengerjakan anime tersebut.                                                                                                                   |
| Source        | Sumber asli materi dari anime (misalnya, manga, novel ringan, orisinal).                                                                                          |
| Duration      | Durasi setiap episode anime.                                                                                                                                      |
| Rating        | Rating usia untuk anime tersebut.                                                                                                                                 |
| Rank          | Peringkat anime berdasarkan popularitas atau kriteria lainnya.                                                                                                    |
| Popularity    | Peringkat popularitas dari anime tersebut.                                                                                                                        |
| Favorites     | Jumlah pengguna yang menandai anime sebagai favorit.                                                                                                              |
| Scored By     | Jumlah pengguna yang memberikan skor untuk anime tersebut.                                                                                                        |
| Members       | Jumlah anggota yang menambahkan anime ke daftar mereka di platform.                                                                                               |
| Image URL     | URL dari poster atau gambar anime.                                                                                                                                |

Dataset ini menawarkan informasi berharga untuk menganalisis dan
 memahami karakteristik, peringkat, popularitas, dan jumlah penonton dari berbagai 
 acara anime. Dengan memanfaatkan dataset ini, seseorang dapat melakukan berbagai analisis,
 termasuk mengidentifikasi anime dengan rating tertinggi, mengeksplorasi genre paling populer,
 memeriksa distribusi rating, dan mendapatkan wawasan tentang preferensi dan tren pemirsa. 
 Selain itu, dataset ini memfasilitasi pembuatan sistem rekomendasi, analisis deret waktu,
 dan pengelompokan untuk mempelajari lebih dalam tentang tren anime dan perilaku pengguna.



user-details
- Jumlah baris : 731290
- Jumlah kolom : 16
- berikut adalah variabel-variabel pada dataset user-details
  
| Kolom           | Deskripsi                                                                                                                                                 |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Mal ID          | ID unik untuk setiap pengguna.                                                                                                                            |
| Username        | Nama pengguna dari user.                                                                                                                                  |
| Gender          | Jenis kelamin pengguna.                                                                                                                                   |
| Birthday        | Tanggal lahir pengguna (dalam format ISO).                                                                                                                |
| Location        | Lokasi atau negara tempat pengguna berada.                                                                                                                |
| Joined          | Tanggal ketika pengguna bergabung dengan platform (dalam format ISO).                                                                                    |
| Days Watched    | Total jumlah hari yang dihabiskan oleh pengguna untuk menonton anime.                                                                                     |
| Mean Score      | Skor rata-rata yang diberikan oleh pengguna kepada anime yang telah mereka tonton.                                                                        |
| Watching        | Jumlah anime yang sedang ditonton oleh pengguna saat ini.                                                                                                 |
| Completed       | Jumlah anime yang telah selesai ditonton oleh pengguna.                                                                                                   |
| On Hold         | Jumlah anime yang ditunda oleh pengguna.                                                                                                                  |
| Dropped         | Jumlah anime yang telah dihentikan atau dibatalkan oleh pengguna.                                                                                         |
| Plan to Watch   | Jumlah anime yang direncanakan untuk ditonton oleh pengguna di masa mendatang.                                                                            |
| Total Entries   | Total jumlah entri anime di daftar pengguna.                                                                                                              |
| Rewatched       | Jumlah anime yang telah ditonton ulang oleh pengguna.                                                                                                     |
| Episodes Watched| Total jumlah episode yang telah ditonton oleh pengguna.                                                                                                   |


Dataset Detail Pengguna memberikan informasi berharga untuk menganalisis perilaku dan
preferensi pengguna di platform anime. Dengan memeriksa skor rata-rata dan genre anime, 
Anda dapat memperoleh wawasan tentang preferensi pengguna. Pengguna dapat disegmentasikan
ke dalam kelompok yang berbeda berdasarkan perilaku menonton mereka, seperti pengguna aktif 
dan penonton biasa. Sistem rekomendasi yang dipersonalisasi dapat dibuat menggunakan 
daftar yang telah diisi dan rencana tontonan pengguna. Analisis berbasis lokasi 
mengungkapkan popularitas anime dan keterlibatan pengguna di berbagai negara. 
Tren perilaku menonton, retensi pengguna, dan perbedaan preferensi anime berdasarkan ge
nder dapat diidentifikasi. Selain itu, Anda dapat mengeksplorasi kebiasaan menonton ulang 
dan melakukan analisis deret waktu untuk memahami pola keterlibatan pengguna dari waktu ke 
waktu.

user-score
- jumlah baris : 24325191 (pada analisis hanya digunakan sample sebanyak 10000 data)
- jumlah kolom : 5
- Berikut variabel nya
  
| Kolom       | Deskripsi                                                                                                  |
|-------------|------------------------------------------------------------------------------------------------------------|
| user_id     | ID unik untuk setiap pengguna.                                                                             |
| Username    | Nama pengguna dari user.                                                                                   |
| anime_id    | ID unik untuk setiap anime.                                                                                |
| Anime Title | Judul dari anime.                                                                                          |
| rating      | Rating yang diberikan oleh pengguna untuk anime tersebut.                                                  |


Dataset Skor Pengguna memungkinkan berbagai analisis dan wawasan tentang
interaksi pengguna dengan anime. Dengan memeriksa peringkat pengguna untuk berbagai 
judul anime, Anda dapat mengidentifikasi anime dengan peringkat tinggi dan populer
di kalangan pengguna. Selain itu, Anda dapat menjelajahi preferensi pengguna dan pola 
menonton untuk judul anime tertentu. Kumpulan data ini juga membentuk dasar untuk membangun 
sistem rekomendasi berdasarkan peringkat pengguna, membantu menyarankan anime yang sesuai 
dengan selera individu. Selain itu, Anda dapat melakukan pemfilteran kolaboratif dan 
analisis kemiripan untuk menemukan pola minat pengguna yang serupa. Secara keseluruhan,
kumpulan data ini menawarkan informasi berharga untuk memahami keterlibatan dan preferensi 
pengguna di platform anime.


## Exploratory Data Analysis

Mengecek informasi untuk dataset anime-dataset 2023

| No | Column       | Non-Null Count | Dtype  |
|----|--------------|----------------|--------|
| 1  | anime_id     | 24905 non-null | int64  |
| 2  | Name         | 24905 non-null | object |
| 3  | English name | 24905 non-null | object |
| 4  | Other name   | 24905 non-null | object |
| 5  | Score        | 24905 non-null | object |
| 6  | Genres       | 24905 non-null | object |
| 7  | Synopsis     | 24905 non-null | object |
| 8  | Type         | 24905 non-null | object |
| 9  | Episodes     | 24905 non-null | object |
| 10 | Aired        | 24905 non-null | object |
| 11 | Premiered    | 24905 non-null | object |
| 12 | Status       | 24905 non-null | object |
| 13 | Producers    | 24905 non-null | object |
| 14 | Licensors    | 24905 non-null | object |
| 15 | Studios      | 24905 non-null | object |
| 16 | Source       | 24905 non-null | object |
| 17 | Duration     | 24905 non-null | object |
| 18 | Rating       | 24905 non-null | object |
| 19 | Rank         | 24905 non-null | object |
| 20 | Popularity   | 24905 non-null | int64  |
| 21 | Favorites    | 24905 non-null | int64  |
| 22 | Scored By    | 24905 non-null | object |
| 23 | Members      | 24905 non-null | int64  |
| 24 | Image URL    | 24905 non-null | object |

Mengecek informasi untuk dataset user-details

| No | Column            | Non-Null Count   | Dtype    |
|----|-------------------|------------------|----------|
| 0  | Mal ID            | 731290 non-null   | int64    |
| 1  | Username          | 731289 non-null   | object   |
| 2  | Gender            | 224383 non-null   | object   |
| 3  | Birthday          | 168068 non-null   | object   |
| 4  | Location          | 152805 non-null   | object   |
| 5  | Joined            | 731290 non-null   | object   |
| 6  | Days Watched      | 731282 non-null   | float64  |
| 7  | Mean Score        | 731282 non-null   | float64  |
| 8  | Watching          | 731282 non-null   | float64  |
| 9  | Completed         | 731282 non-null   | float64  |
| 10 | On Hold           | 731282 non-null   | float64  |
| 11 | Dropped           | 731282 non-null   | float64  |
| 12 | Plan to Watch     | 731282 non-null   | float64  |
| 13 | Total Entries     | 731282 non-null   | float64  |
| 14 | Rewatched         | 731282 non-null   | float64  |
| 15 | Episodes Watched   | 731282 non-null   | float64  |

Mengecek informasi untuk dataset user-details

| No | Column       | Dtype  |
|----|--------------|--------|
| 0  | user_id      | int64  |
| 1  | Username     | object |
| 2  | anime_id     | int64  |
| 3  | Anime Title  | object |
| 4  | rating       | int64  |

Dari pengecekan informasi dataset maka kita dapat mengetahuo tipe data tiap kolomnya dari 
situ saya juga memilih beberapa kolom untuk diubah tipe datanya guna kebutuhan analisis yang lebih mendalam 
(akan dibahas pada preparataion)

Statistik deskriptif untuk anime-dataset 2023

| Statistik | anime_id       | Popularity     | Favorites      | Members         |
|-----------|----------------|----------------|----------------|-----------------|
| count     | 24905.000000   | 24905.000000   | 24905.000000   | 24905.000000    |
| mean      | 29776.709014   | 12265.388356   | 432.595222     | 37104.960000    |
| std       | 17976.076290   | 7187.428393    | 4353.181647    | 156825.200000   |
| min       | 1.000000       | 0.000000       | 0.000000       | 0.000000        |
| 25%       | 10507.000000   | 6040.000000    | 0.000000       | 209.000000      |
| 50%       | 34628.000000   | 12265.000000   | 1.000000       | 1056.000000     |
| 75%       | 45240.000000   | 18491.000000   | 18.000000      | 9326.000000     |
| max       | 55735.000000   | 24723.000000   | 217606.000000  | 3744541.000000  |

Statistik deksriptif untuk user-details

| Statistik | Mal ID         | Days Watched   | Mean Score     | Watching        | Completed      | On Hold        | Dropped        | Plan to Watch  | Total Entries  | Rewatched      | Episodes Watched |
|-----------|----------------|----------------|----------------|-----------------|----------------|----------------|----------------|----------------|----------------|----------------|------------------|
| count     | 731290.000000  | 731282.000000  | 731282.000000  | 731282.000000   | 731282.000000  | 731282.000000  | 731282.000000  | 731282.000000  | 731282.000000  | 731282.000000  | 731282.000000   |
| mean      | 507020.300000  | 24.180819      | 3.948018       | 4.765714        | 65.953066      | 3.391615       | 4.565480       | 17.547893      | 96.230147      | 4.443352       | 1658.828000     |
| std       | 364014.700000  | 140.105073     | 4.137606       | 20.495890       | 186.633286     | 19.296913      | 34.915341      | 90.286927      | 265.459220     | 29.693175      | 50771.680000    |
| min       | 1.000000       | 0.000000       | 0.000000       | 0.000000        | 0.000000       | 0.000000       | 0.000000       | 0.000000       | 0.000000       | 0.000000       | 0.000000        |
| 25%       | 201108.500000  | 0.000000       | 0.000000       | 0.000000        | 0.000000       | 0.000000       | 0.000000       | 0.000000       | 0.000000       | 0.000000       | 0.000000        |
| 50%       | 425170.500000  | 0.200000       | 0.000000       | 0.000000        | 0.000000       | 0.000000       | 0.000000       | 0.000000       | 1.000000       | 0.000000       | 15.000000       |
| 75%       | 775340.000000  | 24.800000      | 8.040000       | 4.000000        | 48.000000      | 1.000000       | 1.000000       | 5.000000       | 74.000000      | 0.000000       | 1489.000000     |
| max       | 1291097.000000 | 105338.600000  | 255.000000     | 4358.000000     | 13226.000000   | 5167.000000    | 14341.000000   | 21804.000000   | 24817.000000   | 13215.000000   | 3376442.000000  |

Statistik deskriptif untuk user-score

| Statistik | user_id        | anime_id       | rating         |
|-----------|----------------|----------------|----------------|
| count     | 24325190.000000| 24325190.000000| 24325190.000000|
| mean      | 440384.300000  | 9754.686000    | 7.622930       |
| std       | 366946.900000  | 12061.960000   | 1.661510       |
| min       | 1.000000       | 1.000000       | 1.000000       |
| 25%       | 97188.000000   | 873.000000     | 7.000000       |
| 50%       | 387978.000000  | 4726.000000    | 8.000000       |
| 75%       | 528043.000000  | 13161.000000   | 9.000000       |
| max       | 1291097.000000 | 56085.000000   | 10.000000      |

Pada EDA ini juga diidentifikasi missing value dimana ternyata ditemukan pada dataset user-details dan user-score
nantinya akan di handling pada data preparation

### Univariate Analysis 


## Data Preparation
Penanganan Tipe Data
- **Mengkonversi kolom harga**: Mengubah kolom harga dari string ke float dengan menghapus simbol mata uang (₹) dan tanda koma.
- **Mengubah kolom discount_percentage**: Mengubah dari string ke float dengan menghapus simbol '%'.
- **Konversi rating dan rating_count**: Mengubah tipe data kolom rating dan rating_count ke format numerik.

Penanganan Missing Value
- **Mengisi missing value pada kolom rating**: Mengisi dengan nilai median karena rating menggunakan skala 1-5.
- **Mengisi missing value pada kolom rating_count**: Mengisi dengan median karena distribusinya skewed.
- **Alasan**: Penggunaan median lebih tepat daripada mean untuk data yang tidak terdistribusi normal.

Feature Engineering
- **Fitur baru 'price_ratio'**: Membuat fitur 'price_ratio' yang dihitung dengan rumus `price_ratio = actual_price / discounted_price`.
- **Fitur 'review_length'**: Menambahkan fitur yang dihitung dari panjang kolom review_content.
- **Alasan**: Fitur ini dibuat untuk menangkap hubungan antara harga dan memberikan insight lebih detail tentang ulasan.

Standardisasi
- **Menggunakan StandardScaler**: Menormalkan fitur numerik agar skala antar fitur seragam.
- **Alasan**: Standardisasi ini penting agar tidak ada fitur yang mendominasi dalam proses clustering.

## Modeling
**Pemodelan Clustering**

Dalam pemodelan ini, terdapat tiga model yang digunakan, yaitu **KMeans dengan fitur terpilih**, **KMeans dengan fitur terpilih dan fitur tambahan**, dan **DBSCAN dengan fitur terpilih**. Berikut adalah penjelasan tahapan dan parameter yang digunakan dalam masing-masing model:

Model 1: KMeans dengan Fitur Terpilih

**Standarisasi Data:**
- **Parameter**: `StandardScaler()`
- Data numerik (`rating`, `rating_count`, `discount_percentage`) dinormalisasi untuk memastikan bahwa semua fitur berada dalam skala yang sama, menghindari bias pada fitur dengan rentang yang lebih besar.

**K-Means Clustering:**
- **Parameter**: `n_clusters` dalam rentang 2 hingga 10 (uji berbagai jumlah kluster).
- Model KMeans dilatih menggunakan data yang telah distandarisasi, dan metrik evaluasi seperti inertia dan silhouette score dihitung untuk setiap jumlah kluster yang diuji.

Model 2: KMeans dengan Fitur Terpilih dan Fitur Tambahan

**Penambahan Fitur:**
- Fitur baru (`price_ratio` dan `review_length`) ditambahkan ke dataset untuk meningkatkan informasi yang tersedia bagi model.
  - `price_ratio`: Rasio antara harga aktual dan harga diskon.
  - `review_length`: Panjang konten ulasan.

**Standarisasi Data:**
- Proses standarisasi dilakukan lagi untuk fitur baru dan yang sudah ada.

**K-Means Clustering:**
- Sama seperti model sebelumnya, KMeans digunakan dengan rentang `n_clusters` yang sama untuk menemukan kluster yang optimal dan mengevaluasi dengan metrik yang relevan.

Model 3: DBSCAN dengan Fitur Terpilih

**Penskalaan Data:**
- Data distandarisasi menggunakan `StandardScaler()`.

**DBSCAN Clustering:**
- **Parameter**: `eps=0.5`, `min_samples=5`
- DBSCAN digunakan untuk mendeteksi kluster berdasarkan densitas data, dan model menghitung label kluster. Hasil evaluasi termasuk jumlah kluster yang terbentuk dan jumlah noise.

Kelebihan dan Kekurangan dari Setiap Algoritma

**KMeans**
Dalam konteks data yang berisi fitur numerik seperti `rating`, `rating_count`, `discount_percentage`, `price_ratio`, dan `review_length`, KMeans berfungsi dengan baik jika data tersebut tidak memiliki outlier signifikan dan jika kluster berbentuk bulat. Karena data yang digunakan mencakup fitur yang terkait langsung dengan produk dan penilaian, algoritma ini memberikan hasil yang relevan. Namun, jika terdapat banyak variasi dalam data (misalnya, produk dengan diskon ekstrem atau rating yang tidak biasa), hasil klustering mungkin tidak mencerminkan struktur data dengan akurat.

**DBSCAN**
Jika dataset memiliki produk dengan pola rating yang sangat bervariasi atau diskon yang tidak teratur, DBSCAN akan lebih efektif karena kemampuannya dalam mendeteksi kluster dengan bentuk tidak beraturan dan mengidentifikasi outlier. DBSCAN akan sangat berguna untuk dataset yang mengandung noise, misalnya produk dengan rating yang ekstrem, dan memberikan keunggulan dalam menemukan struktur kluster yang lebih halus dalam data.

**Pemilihan Model Terbaik**

Berdasarkan hasil evaluasi:
- **Model 1 KMeans (Fitur Terpilih)**: Silhouette Score: 0.6349
- **Model 2 KMeans (Fitur Terpilih + Fitur Tambahan)**: Silhouette Score: 0.8997
- **Model 3 DBSCAN**: Silhouette Score: 0.3555

**Model 2** dipilih sebagai model terbaik karena memiliki silhouette score tertinggi (0.8997), yang menunjukkan bahwa kluster yang dihasilkan lebih terpisah dengan baik dibandingkan dengan model lainnya. Hal ini mengindikasikan bahwa fitur tambahan meningkatkan pemisahan antar kluster.

**Cara Kerja dan Parameter dari Setiap Model**

**KMeans**
Menggunakan centroid untuk mengelompokkan data. Setiap iterasi, pusat kluster diperbarui hingga konvergensi. Parameter `n_clusters` menentukan jumlah kluster, sedangkan `random_state` digunakan untuk memastikan hasil yang konsisten.

**DBSCAN**
Mengelompokkan titik data berdasarkan densitas. `eps` menentukan jarak maksimum antara dua titik untuk menganggap mereka dalam kluster yang sama, sedangkan `min_samples` menentukan jumlah titik minimum dalam `eps` untuk membentuk kluster.

**Proses Pencarian K Optimal**

Untuk menemukan jumlah kluster optimal `k` dalam model KMeans, metode yang digunakan adalah dengan menghitung dan membandingkan nilai inertia dan silhouette score untuk setiap `k` dalam rentang yang telah ditentukan (2-10). Metrik ini digunakan untuk menentukan trade-off antara kompakness (inertia) dan pemisahan (silhouette score) dari kluster yang terbentuk, dengan tujuan untuk memilih nilai `k` yang memberikan hasil terbaik.

Secara umum, silhouette score yang lebih tinggi menunjukkan kluster yang lebih baik, sedangkan inertia yang lebih rendah menunjukkan kluster yang lebih kompak. Mencari `k` optimal adalah bagian penting dari proses modeling, dan dapat melibatkan metode lain seperti elbow method atau silhouette analysis.


## Evaluation
Metrik Evaluasi untuk Model Clustering
![alt text](https://github.com/cintha22059/PA_MLT/blob/main/plot%20silhouette%20score.png)

Silhouette Score
- **Deskripsi**: Mengukur seberapa mirip objek dengan cluster-nya sendiri dibandingkan dengan cluster lain.
- **Range nilai**: -1 hingga 1.
- **Interpretasi**: Skor yang lebih tinggi menunjukkan cluster yang lebih baik.
- **Hasil**:
Komparasi Silhouette Score 
- Model 1 KMeans Selected features: 0.6349327834910277
- Model 2 KMeans Selected features dan Add new Features: 0.8997343627882889
- Model 3 DBSCAN selected features: 0.3554689722570361

Sehingga diputuskan model kluster terbaik adalah model 2 Kmeans dengan nilai Silhouette Score 0.89 dimana menerapkan features selection dan penambahan features.

Berikut merupakan hasil analisis Cluster dari model terbaik :

**Cluster 0:**

Review Length: Memiliki banyak outlier dengan review yang sangat panjang (hingga 17500 karakter), namun median sekitar 1000-1500 karakter

Price Ratio: Memiliki outlier hingga 16x lipat, dengan median sekitar 2x

Discount Percentage: Median diskon sekitar 50% dengan rentang 30-65%

Rating Count: Jumlah rating relatif rendah (median <50000)

Rating: Median rating sekitar 4.1 dengan beberapa outlier rendah hingga 2.0

Analisis:
Cluster 0 merepresentasikan produk dengan engagement pengguna yang lebih rendah namun memiliki review yang lebih detail. Produk-produk ini cenderung memiliki variasi harga yang ekstrem dan diskon yang moderat. Meski jumlah rating rendah, rating keseluruhan cukup baik dengan beberapa kasus ketidakpuasan.



**Cluster 1:**

Review Length: Lebih konsisten dengan sedikit outlier, median sekitar 1000-1500 karakter

Price Ratio: Lebih stabil dengan median sekitar 2x dan sedikit outlier

Discount Percentage: Distribusi diskon mirip dengan Cluster 0

Rating Count: Jumlah rating sangat tinggi (median >150000)

Rating: Rating lebih konsisten dengan median sekitar 4.2
Analisis:

Cluster 1 merepresentasikan produk populer dengan engagement tinggi. Review cenderung lebih singkat namun konsisten. Harga dan diskon lebih stabil dibanding Cluster 0. Produk-produk ini memiliki basis pengguna yang besar dengan rating yang konsisten tinggi, menunjukkan kualitas dan kepuasan pelanggan yang lebih terjamin.

**Evaluasi terhadap Business Understanding**
Hasil analisis cluster berhasil menjawab problem statement dengan memberikan wawasan mendalam mengenai perilaku konsumen dan faktor-faktor yang mempengaruhi performa produk. Cluster 0 dan Cluster 1 menunjukkan pola perilaku yang berbeda dalam hal panjang ulasan, rasio harga, diskon, jumlah rating, dan rating yang diberikan, yang mencerminkan preferensi konsumen terhadap berbagai jenis produk.

Model berhasil mencapai goals yang diharapkan. Analisis yang dilakukan pada masing-masing cluster memberikan pemahaman yang lebih baik tentang bagaimana konsumen berinteraksi dengan produk berdasarkan rating dan ulasan mereka. Selain itu, identifikasi cluster yang menunjukkan produk dengan engagement rendah dan tinggi dapat membantu dalam pengambilan keputusan strategis.

Solusi yang direncanakan berdampak signifikan. Dengan memisahkan produk ke dalam cluster berdasarkan karakteristik yang telah dianalisis, perusahaan dapat mengadopsi pendekatan yang lebih terarah dalam pemasaran dan penetapan harga. Misalnya, untuk Cluster 0, perusahaan dapat mempertimbangkan untuk meningkatkan interaksi dengan konsumen untuk produk dengan review panjang namun engagement rendah, sedangkan untuk Cluster 1, perusahaan dapat memanfaatkan popularitas dan kualitas produk untuk strategi promosi yang lebih agresif.
