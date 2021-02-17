# Explore.md #

Halaman ini akan berisi penjelasan mengenai eksplorasi data yang telah saya lakukan mengenai tujuh dataset yang telah di load di database.


## seller_details ## 

seller_details memiliki 4 kolom, yaitu seller_id, seller_zip_code, seller_city, seller_state.

seller_id: id dari seller (primary key)\
seller_zip_code: kode pos dari seller\
seller_city: kota dari seller\
seller_state: negara bagian dari seller

Cara menentukan primary key dengan menjalankan query:\
select count(seller_id) from seller_details : 3095\
select count(distinct(seller_id)) from seller_details : 3095\
Selain itu, tidak ada nilai duplikat sehingga dapat diasumsikan bahwa setiap seller/penjual memiliki satu seller_id tetapi ada kemungkinan untuk memiliki seller_zip_code, seller_city atau seller_state yang sama.

## Upcoming ##
