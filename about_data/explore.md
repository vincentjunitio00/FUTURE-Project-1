# Explore.md #

Halaman ini akan berisi penjelasan mengenai eksplorasi data yang telah saya lakukan mengenai tujuh dataset yang telah di load di database.


## seller_details ## 

seller_details memiliki 4 kolom, yaitu seller_id, seller_zip_code, seller_city, seller_state.

seller_id: id dari seller (primary key)\
seller_zip_code: kode pos dari seller\
seller_city: kota dari seller\
seller_state: negara bagian dari seller

Cara menentukan primary key dengan menjalankan query:\
select count(seller_id) from seller_details: 3095\
select count(distinct(seller_id)) from seller_details: 3095\
Selain itu, tidak ada nilai duplikat sehingga dapat diasumsikan bahwa setiap seller/penjual memiliki satu seller_id tetapi ada kemungkinan untuk memiliki seller_zip_code, seller_city atau seller_state yang sama.

## product_details ##

product_details memiliki 4 kolom, yaitu product_id, product_category, product_name_length, product_description_length, product_photos_qty, product_weight_g, product_length_cm, product_height_cm, product_width_cm.

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
select count(distinct(product_id)) from products_details: 32951
Selain itu, tidak ada nilai duplikat sehingga dapat diasumsikan bahwa setiap product hanya memiliki satu product_id. Pada product_category, terdapat 1 kategori yang tidak memiliki kategori tetapi bukan null. 

## feedback_details ##

feedback_id: id dari feedback (composite primary key)\
order_id: id dari oder (composite primary key)\

feedback_id, order_id adalah composite primary key karena feedback_id dan order_id masing-masing tidak unique.
## Upcoming ##
