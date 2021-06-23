# FUTURE-Project-1

Repository yang memuat semua file dalam pengerjaan Project #1 Blibli FUTURE Program Batch 5.

Oleh: Vincent Junitio Ungu - Data Track

Google drive: https://drive.google.com/drive/folders/15m9gJwCkSskd4R_irVgVe175hNZWkn-C?usp=sharing


# Pengenalan Proyek
Proyek ini akan menggunakan dataset dalam bidang *E-commerce* untuk menelusuri dataset, menjawab pertanyaan terkait perilaku bisnis, serta memberikan solusi dari permasalahan yang diidentifikasi. 

# Pembaharuan Progres
Pembaharuan progres proyek akan dilakukan setiap dua minggu.

* 26 Januari - 8 Februari

- [X] Mencari dataset

* 9 Februari - 22 Februari

- [X] Membuat repository github
- [X] Melakukan eksplorasi mengenai star schema: terdiri dari fact table dan dimension table
- [X] Membuat relationship diagram (ERD) antar tabel, kecuali user_details / user_dataset
- [X] Menentukan primary key dan foreign key, kecuali user_details / user_dataset
- [X] Export backup file .bak (tapi ragu apakah caranya benar)
- [X] Memfinalisasikan semua file sebelum mentoring (23 Februari): explore.md, .bak, erd.png

* yang binggung:
1. Apakah 7 csv tersebut kalau import ke dbeaver dan jadi satu database sudah dinamakan Data warehouse? [Solved] => 7 csv ini kalau di satu database jadi OLTP dan untuk ke DWH butuh ETL karena struktur DWH berbeda dengan database OLTP.
2. Apakah cara export .bak file sudah benar?

* 23 Februari - 8 Maret

- [X] Eksplor ulang cara pembuatan data warehouse

* 9 Maret - 23 Maret

- [X] Belajar Talend dan review ulang project
* database di postgre harus ulang karena sudah dilakukan pengubahan dari data asli yang dikirim mentor

* 24 Maret - 7 April

- [X] Ujian Tengah Semester di Universitas Gadjah Mada

* 8 April - 21 April

- [ ] Mencari business question

* 22 April - 5 Mei

- [X] Membuat dimension table Date.\
Caranya insert excel file ke talend baru import ke schema staging.
- [X] Melakukan update pada erd
- [X] Merubah tipe data kolom
- [X] Selesai membuat Fact Sales

* 5 Mei - 26 Mei

- [X] Mencari business question

* 27 Mei - 9 Juni

- [X] Mencari business question

* 10 Juni - 23 Juni

- [X] Mengfinalisasikan datawarehouse
- [X] Membuat datamart untuk business question pertama

