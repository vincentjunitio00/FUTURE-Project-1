# FUTURE-Project-1

Repository yang memuat semua file dalam pengerjaan Project #1 Blibli FUTURE Program Batch 5.

Oleh: Vincent Junitio Ungu - Data Track


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
- [ ] Memfinalisasikan semua file sebelum mentoring (23 Februari)

Progress:
*semua akhiran dataset (csv) diubah jadi details di database.*
- user_details tidak jadi didrop nilainya di database; artinya user_details_cleaned.csv belum rencana dipakai.
- seller_details sementara langsung digunakan seperti raw karena seller_id sudah unique (kalau di database sudah dibuat primary keynya).
- products_details memiliki product_id yang unique (kalau di database belum dibuat primary keynya).
- payment_details memiliki order_id yang duplikat (kemungkinan membeli barang lebih dari satu jenis pada sebuah transaksi), dan tidak memiliki baris yang duplikat.
- order_item_details tidak memiliki nilai duplikat, namun primary key tidak bisa ditentukan hanya oleh satu kolom/fitur saja.
- order_details memiliki order_id yang unique dan tidak ada baris yang duplikat.
- feedback_details seharusnya memiliki primary key (feedback_id, order_id)
