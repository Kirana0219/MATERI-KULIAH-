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


