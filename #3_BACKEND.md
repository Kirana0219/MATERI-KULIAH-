# FUNCTION

Function merupakan blok kode yang dibuat untuk melakukan tugas spesifik dan bisa dipanggil berulang kali. Berfungsi utuk mengurangi dan mencegah menulis kode yang sama.

## Struktur Function
1. Nama function
2. Parameter: data yang diolah pada fungsi 
3. Return Value: hasil akhir yang dikembalikan oleh fungsi (opsional)

**contoh:**
```php
<?php
    // Function untuk menghitung luas persegi panjang
    function luasPersegiPanjang($p, $l) { // Jika parameter lebih dari satu, gunakan tanda koma
        $luas = $p * $l;
        echo "Luas persegi panjang dengan panjang = $p dan lebar = $l adalah $luas";
    }

    luasPersegiPanjang(5, 6); // return value
?>
```

### Modularisasi
Modularisasi adalah teknik dalam pemrograman untuk membagi program besar menjadi bagian-bagian kecil yang disebut modul (misalnya function, class, atau file terpisah). Setiap modul memiliki tugas spesifik sehingga program menjadi lebih terstruktur dan sistematis.

Tujuannya:
1. Membagi program menjadi bagian kecil (modul) yang idependen
2. Kode lebih mudah untuk diperbaiki
3. Dapat digunakan berulang kali
4. Tim dapat bekerja di file yang berbeda secara bersamaan

## OOP (Object Oriented Programming)
adalah kerangka pemograman yang berorientasi pada objek. Aplikasi yang akan dibuat dibagi menjadi bagian kecil yang disebut sebagai objek yang saling berkaitan

Contoh:
1. Website Pendaftaran Calon Mahasiswa
* objek: Mahasiswa dan program studi

### Class dan Object
Class: apa yang harus dimiliki dan apa saja yang dapat dilakuka.
* Contoh: Class Mahasiswa berisi Nama dan Nim

Object
Bentuk nyata dari Class yang sudah diisi datanya
* Contoh: Object pendaftar Bernama “Andi” dengan NIM “110001011”'

**Note:**
* ```return``` digunakan untuk mengembalikan nilai dari suatu function, sehingga nilai tersebut dapat digunakan kembali di luar function.
Sedangkan ```echo``` digunakan untuk menampilkan output secara langsung pada baris tersebut.

