# Explore.md #

Halaman ini akan berisi penjelasan mengenai eksplorasi data yang telah saya lakukan mengenai tujuh dataset yang telah di load di database.


## seller_details ## 

seller_details memiliki empat kolom, yaitu seller_id, seller_zip_code, seller_city, seller_state.

seller_id: id dari seller (primary key)\
seller_zip_code: kode pos dari seller\
seller_city: kota dari seller\
seller_state: negara bagian dari seller

Cara menentukan primary key dengan menjalankan query:\
select count(seller_id) from seller_details: 3095\
select count(distinct(seller_id)) from seller_details: 3095\
Selain itu, tidak ada nilai duplikat sehingga dapat diasumsikan bahwa setiap seller/penjual memiliki satu seller_id tetapi ada kemungkinan untuk memiliki seller_zip_code, seller_city atau seller_state yang sama.

## product_details ##

product_details memiliki empat kolom, yaitu product_id, product_category, product_name_length, product_description_length, product_photos_qty, product_weight_g, product_length_cm, product_height_cm, product_width_cm.

product_id: id dari product (primary key)\
product_category: jenis kategori dari product; terdapat 623 baris kosong -> select COUNT(\*) from products_details where product_category = '' group by product_category\
product_name_length: panjang huruf/kata dari nama product; terdapat 610 baris yang tidak bernilai\
product_description_length: panjang huruf/kata dari deskripsi product; terdapat 610 baris yang tidak bernilai\
product_photos_qty: jumlah foto product yang diupload; terdapat 610 baris yang tidak bernilai\
product_weight_g: berat product dalam gram; terdapat 2 baris yang tidak bernilai\
product_length_cm: panjang product dalam centimeter; terdapat 2 baris yang tidak bernilai\
product_height_cm: tinggi product; terdapat 2 baris yang tidak bernilai\
product_width_cm: lebar product; terdapat 2 baris yang tidak bernilai

Cara menentukan primary key dengan menjalankan query:\
select count(product_id) from products_details: 32951\
select count(distinct(product_id)) from products_details: 32951\
Selain itu, tidak ada nilai duplikat sehingga dapat diasumsikan bahwa setiap product hanya memiliki satu product_id. Pada product_category, terdapat 1 kategori yang tidak memiliki kategori tetapi bukan null. 

## feedback_details ##

feedback_id: id dari feedback (composite primary key)\
order_id: id dari order (composite primary key)\
feedback_score: rentang nilai kepuasan; dari rentang 1 - 5 dan tidak ada nilai kosong\
feedback_form_sent_date: tanggal dan waktu pengiriman feedback form; tidak ada nilai nilai kosong\
feedback_answer_date: tanggal dan waktu pengguna mengirimkan feedback form; tidak ada nilai nilai kosong

feedback_id, order_id adalah composite primary key karena feedback_id dan order_id masing-masing tidak unique.\
Untuk feedback_id:\
select count(feedback_id) from feedback_details: 100000\
select count(distinct(feedback_id)) from feedback_details: 99173\
Untuk order_id:\
select count(order_id) from feedback_details: 100000\
select count(distinct(order_id)) from feedback_details: 99441\
Untuk feedback_id, order_id:\
select sum(counts) from ( select feedback_id, order_id, count(\*) as counts from feedback_details group by feedback_id , order_id) as sums where counts = 1

## payment_details ##

payment_details memiliki lima kolom, yaitu order_id, payment_sequential, payment_type, payment_installments, payment_value.

order_id: id dari order (composite primary key)\
payment_sequential: urutan pembayaran / payment (asumsinya sebuah order_id bisa memiliki beberapa kali pembayaran) (composite primary key); ada order_id yang payment_sequentialnya sampai 29\
payment_type: jenis pembayaran / payment; ada lima jenis, yaitu voucher, debit_card, blipay, credit_card, not_defined\
payment_installments: cicilan pembayaran / payment; dari 0 sampai 24, bernilai 0 hanya dimiliki oleh order yang payment_type adalah credit_card\
payment_value: harga yang dibayar; nilai maksimalnya adalah 13664080, nilai kedua maksimal adalah 7274880 - setelah dihitung sekilas, kemungkinan besar terdapat banyak outlier

order_id, payment_sequential adalah composite primary key.\
Untuk order_id, payment_sequential:\
select sum(count) from (select order_id, payment_sequential, count(\*) from payment_details group by order_id, payment_sequential) as opc


## Upcoming ##
