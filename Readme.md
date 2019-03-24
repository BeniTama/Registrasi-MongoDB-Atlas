# Registrasi dan Impor Data ke MongoDB Atlas

## Daftar Isi
1. [Registrasi ke MongoDB](#1-registrasi-ke-mongodb)
2. [Impor data](#2-impor-data)
3. [Mengakses data menggunakan MongoDB Compass](#3-mengakses-data-menggunakan-mongodb-compass)

## 1. Registrasi ke MongoDB

Langkah pertama adalah mendaftarkan diri ke website [MongoDB](https://www.mongodb.com/cloud/atlas). Klik tombol untuk mencoba gratis ('Try Free')
dan lakukan registrasi seperti biasa. Setelah melakukan registrasi, akan diberikan pilihan yang terbatas untuk membuat cluster pertama.
Pilihlah sesuai kebutuhan, cloud provider dan regionnya. Setelah itu, cluster server akan dibuat. Proses ini mungkin akan memakan waktu agak lama.

## 2. Impor data

Setelah cluster berhasil dibuat, komputer dengan MongoDB Atlas harus bisa terhubung agar dapat mengimpor data. Maka dari itu, pertama klik bagian
security pada cluster, kemudian pada tab IP Whitelist, tambahkan IP komputer.

Setelah itu, untuk dapat menghubungkan MongoDB Atlas dengan PC, dibutuhkan shell MongoDB pada PC. Untuk itu, diperlukan mendownload shell MongoDB pada PC.
Gunakan [link](https://fastdl.mongodb.org/win32/mongodb-win32-x86_64-2008plus-ssl-4.0.6.zip) ini untuk OS Windows. Setelah download, ekstrak filenya
ke folder yang ingin digunakan untuk mengoperasikan MongoDB.

Langkah selanjutnya adalah melakukan import data json dari PC ke MongoDB. Disini akan digunakan dataset [Starwars DataSets](https://public.tableau.com/s/sites/default/files/media/starwarscharacterdata.json).
Simpan file json kedalam folder bin tempat instalasi shell MongoDB. Setelah itu, buka cmd, lakukan cd ke folder shell, kemudian lakukan perintah
untuk melakukan impor file kedalam MongoDB.
~~~
mongoimport --host [nama host] --db starwars --type json --file starwarscharacterdata.json --jsonArray --authenticationDatabase admin --ssl --username [username] --password [password]

--host adalah host yang digunakan untuk melakukan import
--db adalah database yang digunakan
--type type yang digunakan, pada kasus ini saya menggunakan json
--file lokasi file dari json
--authenticationDatabase autotentikasi yang digunakan adalah admin
~~~

Jika impor berhasil akan keluar dialog seperti ini:
![](/pictures/impor-db.PNG)

Setelah impor berhasil dilakukan, coba lakukan akses ke MongoDB menggunakan shell. Caranya klik `Connect` di halaman MongoDB, klik `Connect with the Mongo Shell`,
kemudian copy connection string yang ada disana. Kemudian paste string ke cmd, dan jalankan. Setelah koneksi berhasil, buka dan lihat hasil
impor data seperti gambar dibawah:
![](/pictures/show-console-1.PNG)
<br>
![](/pictures/show-console-2.PNG)

## 3. Mengakses Data Menggunakan MongoDB Compass

Untuk mengakses MongoDB Compass, ikuti langkah yang disediakan MongoDB Atlas saat memilih tombol `Connect` dan `Connect With MongoDB Compass`.
Download MongoDB Compass terlebih dahulu, kemudian copy connection string yang disediakan. Setelah itu, buka MongoDB Compass, dan MongoDB Compass
akan secara otomatis mendeteksi connection string yang ada pada clipboard, dan melakukan konfigurasi secara otomatis. Setelah koneksi dijalankan,
MongoDB Compass akan tersambung dengan MongoDB.

Berikut adalah hasil tampilan data yang berhasil diimpor menggunakan MongoDB Compass:
![](/pictures/compass-view-1.PNG)
![](/pictures/compass-view-2.PNG)
