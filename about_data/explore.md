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

## user_details ##
\* ! ragu dengan bagian ini !
user_details memiliki empat kolom, yaitu user_name, customer_zip_code, customer_city, customer_state. Di database, tabel ini masih mengandung banyak baris yang duplikat (masih ragu apakah boleh langsung delete baris yang duplikat atau dibiarkan terlebih dahulu kondisi ini).

user_name: username pengguna (composite primary key)\
customer_zip_code: kode pos dari pelanggan / customer\
customer_city: kota dari pelanggan / customer\
customer_state: negara bagian dari pelanggan / customer

*saya mencoba skenario dimana baris yang duplikat dihapus, maka primary keynya composite, yaitu user_name, customer_zip_code, customer_city / customer_state (bisa salah satu). 

## order_details ##

order_id: id dari pesanan / order (primary key)\
user_name: username dari pemesan; mengandung nilai duplikat dimana satu user_name dapat memiliki banyak order_id\
order_status: status dari pesanan / order; unavailable tidak memiliki pickup_date dan delivered_date, delivered memiliki seluruh date, processing hanya memiliki order_date dan order_approved_date, canceled hanya memiliki order_date, shipped tidak memiliki delivered_date, created hanya memiliki order_date dan estimated_time_delivery, approved dan invoiced tidak memiliki pickup_date dan delivered_date\
order_date: tanggal pesan\
order_approved_date: tanggal pesanan di-approved\
pickup_date: tanggal pesanan di-pickup\
delivered_date: tanggal pesanan dikirimkan\
estimated_time_delivery: tanggal perkiraan pesanan akan sampai

Cara menentukan primary key dengan menjalankan query:\
select count(order_id) from order_details: 99441\
select count(distinct(order_id)) from order_details: 99441\


## order_item_details ##
order_id: id dari order (composite primary key)\
order_item_id: id / urutan order seperti product pertama ber-id 1, dan product kedua ber-id 2 (composite primary key)\
product_id: id dari product\
seller_id: id dari seller\
pickup_limit_time: waktu maksimal pesanan dilakukan pickup\
price: harga pesanan\
shipping_cost: biaya pengiriman

Ada order_id yang sama tetapi product_id dan seller_id yang berbeda (pertanyaan: apakah memungkinkan untuk membeli product dari dua seller yang berbeda pada satu struk yang sama?).

Cara menentukan primary key dengan menjalankan query:\
select count(\*) from order_item_details oid2 group by (order_id, order_item_id) order by count(\*) desc


## Cardinality / Relationship ##
| Tabel Pertama | Relationship | Tabel Kedua |
| ------------- | ------------ | ----------- |
|product_dataset| One to Many  | order_item_dataset|
|order_dataset| One to Many  | order_item_dataset|
|seller_dataset| One to Many  | order_item_dataset|
|order_dataset| One to Many  | payment_dataset|
|feedback_dataset| Many to One  | order_dataset|
|user_dataset| One to Many  | order_dataset |
