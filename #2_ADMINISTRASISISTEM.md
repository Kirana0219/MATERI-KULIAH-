# Pengelolaan Sistem File, Manajemen Pengguna, DHCP, DNS, dan Analisis Infrastruktur Jaringan

# 1. Pengelolaan Sistem File dan Direktori pada Linux

## 1.1 Pengertian Sistem File
**Sistem file (file system)** adalah metode atau struktur yang digunakan oleh sistem operasi untuk **menyimpan, mengatur, mengelola, dan mengambil data pada media penyimpanan** seperti hard disk, SSD, atau flash drive.

Pada sistem operasi **Linux**, semua data disimpan dalam bentuk **file** dan diorganisasikan dalam struktur **direktori (folder)** yang berbentuk **hierarki seperti pohon (tree structure)**. Ini berbeda dengan konsep drive `C:\`, `D:\` di Windows.

Struktur paling atas disebut **root directory** dengan simbol:
```
/
```
Semua direktori lain, file, dan perangkat berada di bawah root ini.

## 1.2 Struktur Direktori Penting di Linux (Filesystem Hierarchy Standard / FHS)
Linux mengadopsi standar hirarki sistem file. Berikut adalah direktori penting beserta fungsinya:

| Direktori | Fungsi |
| --------- | --------------------------------------- |
| `/` (Root) | Direktori utama, pangkal dari seluruh sistem file. |
| `/home` | Direktori penyimpanan data pribadi setiap pengguna (misal: `/home/budi`, `/home/siti`). |
| `/etc` | Berisi file-file konfigurasi sistem dan aplikasi. |
| `/bin` | Berisi program penting (binari) yang digunakan oleh semua pengguna atau program dasar. |
| `/sbin` | Berisi program penting untuk administrasi sistem (biasanya dijalankan oleh root). |
| `/usr` | Berisi aplikasi tambahan, library, dan data tambahan yang dapat dibagi (*shareable*). |
| `/var` | Menyimpan data yang sering berubah (*variable*), seperti file log (`/var/log`). |
| `/tmp` | Direktori untuk file sementara yang dapat diakses semua pengguna. |
| `/boot` | Berisi file-file yang digunakan saat proses booting, seperti kernel. |
| `/dev` | Berisi file khusus yang mewakili perangkat keras (*devices*). |
| `/proc` | Sistem file virtual yang memberikan informasi tentang proses dan kernel. |

### Contoh Struktur Direktori
```
/
 ├── home
 │    ├── Kirana 
 │    │    ├── Documents
 │    │    └── Downloads
 │    └── siti
 ├── etc
 │    ├── apache2
 │    └── network
 ├── var
 │    └── log
 └── tmp
```

## 1.3 Konsep Path (Jalur)
Path adalah alamat yang menunjukan lokasi dalam suatu file atu direktori dalam file
*   **Absolute Path (Path Absolut):** Jalur lengkap dari direktori root. Selalu diawali dengan `/`.
    *   *Contoh:* `/home/budi/Documents/laporan.txt`
*   **Relative Path (Path Relatif):** Jalur yang relatif terhadap direktori tempat pengguna berada saat ini (hanya menampilkan folder dimana file tersebut berada).
    *   *Contoh:* Jika sedang di `/home/budi`, maka `Documents/laporan.txt` adalah path relatif.
*   **Notasi Khusus:**
    *   **`.` (satu titik):** Merujuk pada direktori saat ini.
    *   **`..` (dua titik):** Merujuk pada direktori satu level di atas (*parent directory*).

## 1.4 Perintah Dasar Pengelolaan File dan Direktori
Manajemen File merupakan proses membuat, menghapus, menyalin, dan memindahkan file atau folder dalam sistem operasi 

| Perintah | Fungsi | Contoh |
| --------- | --------------------------------------- | ------- |
| `pwd` | Melihat direktori aktif saat ini. | `pwd` -> Output: `/home/budi` |
| `ls` | Melihat daftar isi direktori. | `ls -l /home` (melihat detail semua pengguna) |
| `cd` | Masuk kedalam direktori. | `cd /etc` (pindah ke `/etc`), lalu `cd ..` (kembali ke direktori sebelumnya) |
| `mkdir` | Membuat direktori baru. | `mkdir tugas_linux` atau `mkdir /home/budi/proyek_web` |
| `touch` | Membuat file. | `touch laporan.txt` |
| `rm` | Menghapus file atau direktori. | `rm laporan.txt` (hapus file), `rm -r tugas_lama` (hapus folder beserta isinya) |
| `cp` | Menyalin file atau direktori. | `cp laporan.txt backup.txt` atau `cp laporan.txt /home/budi/backup/` |
| `mv` | Memindahkan atau mengganti nama file/direktori. | `mv laporan.txt laporan_2023.txt` (rename), `mv laporan.txt /home/budi/arsip/` (pindah) |

### Navigasi Direktori
`cd..` = kembali ke direktori sebelumnya 
`cd ~`= kembali ke home direktori
 
---

# 2. Konsep Pengguna (User), Grup (Group), dan Perizinan Akses (Permission) di Linux

Linux adalah sistem operasi **multi-user**, yang memungkinkan banyak orang mengakses sistem secara bersamaan. Keamanan data diatur melalui kombinasi user, grup, dan permission.

## 2.1 Konsep Pengguna (User)
**User** adalah akun yang digunakan seseorang atau sistem untuk mengakses komputer atau server.
*   **Username** (identitas)
*   **Password** (untuk autentikasi)
*   **User ID (UID)** (identitas numerik unik)
*   **Home Directory** (tempat penyimpanan pribadi, biasanya di `/home/username`)
*   **Shell** (program antarmuka baris perintah, misal `/bin/bash`)

Dalam linux terdapat memiliki beberapa jenis user:
- root
- user biasa
- system user

### Tiga Jenis User Utama:
1.  **Root (Superuser):** UID 0. Memiliki hak akses tak terbatas.
2.  **Pengguna Sistem:** UID < 1000 (biasanya). Dibuat oleh sistem untuk menjalankan layanan tertentu (misal: `www-data`, `mysql`). Tidak memiliki password login.
3.  **Pengguna Biasa:** UID >= 1000. Dibuat untuk interaksi manusia. Akses terbatas pada direktori home-nya sendiri.

## 2.2 Konsep Grup (Group)
**Group** adalah kumpulan beberapa user yang memiliki **hak akses yang sama terhadap file atau sumber daya tertentu**. Setiap user memiliki **Group ID (GID)** utama (*primary group*) dan bisa menjadi anggota grup tambahan (*supplementary groups*).

hak akses yang diberikan kepada file tersebut 

**Tujuan Grup:**
*   Mempermudah pengelolaan hak akses untuk tim proyek.
*   Meningkatkan keamanan dengan memberikan akses berbasis peran.
*   Mengaktur akses file yang sama
*   Mempermudah manajemen user 

*   **Contoh:** Buat grup `developer`. Anggota grup ini (Budi, Siti, Ali) perlu mengakses folder proyek. Daripada memberi izin satu per satu, kita beri izin untuk grup `developer`, lalu masukkan mereka ke dalam grup tersebut.

## 2.3 Konsep Perizinan Akses (File Permission)
Setiap file dan direktori memiliki serangkaian izin yang menentukan siapa yang bisa melakukan apa, atau "apa yang boleh dilakukan oleh file tersebut". 

### Tiga Jenis Entitas:
1.  **Pemilik (User/Owner - u)**
2.  **Grup (Group - g)**
3.  **Pengguna Lain (Others - o)**

### Tiga Jenis Izin:
| Izin | Simbol | Untuk File | Untuk Direktori |
| ---- | ------ | ---------- | --------------- |
| **Read** | `r` | Bisa membaca/melihat isi file. | Bisa melihat daftar isi (misal dengan `ls`). |
| **Write** | `w` | Bisa mengubah/menulis isi file. | Bisa membuat, menghapus, atau mengganti nama file di dalamnya. |
| **Execute**| `x` | Bisa menjalankan file sebagai program/script. | Bisa masuk ke dalam direktori (misal dengan `cd`). |

## 2.4 Cara Melihat dan Mengubah Permission

### Melihat Izin (Permission)
Gunakan perintah `ls -l`. Outputnya akan seperti ini:
`-rw-r--r-- 1 budi developer 1024 Oct 10 10:30 catatan.txt`

*   **`-`** (strip pertama): Tipe file (`-`=file biasa, `d`=direktori).
*   **`rw-`** : Izin untuk pemilik (`budi`) = baca dan tulis (rw-).
*   **`r--`** : Izin untuk grup (`developer`) = hanya baca (r--).
*   **`r--`** : Izin untuk pengguna lain = hanya baca (r--).
*   **`1`** : Jumlah link.
*   **`budi`** : Pemilik file.
*   **`developer`** : Grup pemilik file.

### Mengubah Izin dengan `chmod`
Gunakan perintah `chmod` (Change Mode).

**a. Mode Simbolik:**
Gunakan huruf (`u`, `g`, `o`, `a`) dan operator (`+`, `-`, `=`).
*   *Contoh:* `chmod u+x script.sh` (tambahkan izin execute untuk pemilik).
*   *Contoh:* `chmod go-w catatan.txt` (cabut izin write untuk grup dan lainnya).

**b. Mode Numerik (Oktal):**
Setiap izin memiliki nilai angka:
*   `r` = 4
*   `w` = 2
*   `x` = 1
*   `-` = 0

Jumlahkan nilai untuk setiap set (user, group, others) menjadi satu angka.
*   *Contoh:* `chmod 755 script.sh`
    *   Pemilik (User): 7 = 4+2+1 = **rwx**
    *   Grup: 5 = 4+0+1 = **r-x**
    *   Lainnya: 5 = 4+0+1 = **r-x**
    *   Hasil: `rwxr-xr-x`

*   *Contoh:* `chmod 644 catatan.txt`
    *   Pemilik (User): 6 = 4+2+0 = **rw-**
    *   Grup: 4 = 4+0+0 = **r--**
    *   Lainnya: 4 = 4+0+0 = **r--**
    *   Hasil: `-rw-r--r--`

### Mengubah Pemilik dan Grup dengan `chown`
Gunakan perintah `chown` (Change Owner).
*   *Contoh:* `sudo chown budi:developer laporan.txt` (ubah pemilik menjadi `budi` dan grup menjadi `developer`).

---

# 3. Memahami Peran DHCP dan DNS

## 3.1 Dynamic Host Configuration Protocol (DHCP)

### 3.1.1 Pengertian DHCP
**Dynamic Host Configuration Protocol (DHCP)** adalah protokol jaringan yang memungkinkan server untuk secara otomatis memberikan konfigurasi jaringan kepada perangkat klien (komputer, laptop, smartphone, printer) saat mereka terhubung ke jaringan.

**Informasi yang Diberikan DHCP:**
*   Alamat IP dan Subnet Mask
*   Gateway Default (alamat router)
*   Alamat DNS Server
*   Durasi "Sewa" IP (*Lease Time*)

### 3.1.2 Cara Kerja DHCP (DORA Process)
Proses perolehan IP secara otomatis ini dikenal dengan singkatan **DORA**:
1.  **D**iscover: Klien menyiarkan pesan "Saya baru di jaringan, cari server DHCP".
2.  **O**ffer: Server DHCP merespon dengan menawarkan konfigurasi IP yang tersedia.
3.  **R**equest: Klien meminta untuk menggunakan konfigurasi yang ditawarkan.
4.  **A**ck: Server mengonfirmasi dan mencatat alokasi IP tersebut.

### 3.1.3 Keuntungan dan Contoh Penggunaan DHCP
**Keuntungan:**
*   **Efisiensi:** Menghemat waktu konfigurasi manual.
*   **Mengurangi Kesalahan:** Menghindari *typo* dan konflik IP.
*   **Mudah Dikelola:** Sangat cocok untuk jaringan besar dan dinamis.

**Contoh Implementasi:**
*   Di kantor, seorang karyawan membuka laptop dan langsung bisa internet tanpa setting IP manual.
*   Di rumah, ponsel Anda otomatis terhubung ke WiFi dan mendapatkan IP dari router.
*   Di jaringan kampus, perangkat seperti laptop mahasiswa, smartphone, dan printer lab mendapatkan IP otomatis:
    *   Laptop A → `192.168.1.10`
    *   Laptop B → `192.168.1.11`
    *   Printer → `192.168.1.12`

## 3.2 Domain Name System (DNS)

### 3.2.1 Pengertian DNS
**Domain Name System (DNS)** adalah sistem yang berfungsi untuk **menerjemahkan nama domain yang mudah diingat manusia** (seperti `www.google.com`) **ke alamat IP numerik** (seperti `142.250.185.46`) yang digunakan komputer untuk berkomunikasi. DNS adalah "buku telepon" internet.

### 3.2.2 Cara Kerja DNS
Prosesnya sederhana:
1.  User mengetik `www.contoh.com` di browser.
2.  Komputer menanyakan alamat IP domain tersebut ke **DNS Resolver** (misal: `8.8.8.8`).
3.  Resolver mencari jawaban secara hierarkis hingga menemukan IP yang tepat.
4.  Resolver mengembalikan IP tersebut ke komputer pengguna.
5.  Browser terhubung ke server menggunakan IP tersebut.

### 3.2.3 Peran dan Contoh DNS
**Peran Utama:**
*   **Resolusi Nama:** Fungsi utamanya (Domain ke IP).
*   **Resolusi Balik:** IP ke Nama Domain.
*   **Mempermudah Akses:** Pengguna cukup mengingat nama, bukan deretan angka.

**Contoh Implementasi:**
*   **Tanpa DNS:** User harus mengetik `142.250.190.78`.
*   **Dengan DNS:** User cukup mengetik `google.com`.
*   **Layanan Email:** Server email tujuan ditemukan melalui pencarian DNS (MX Record).
*   **Internal Perusahaan:** Karyawan mengakses server aplikasi dengan nama `hrd-app.perusahaan.local`.

---

# 4. Analisis Kebutuhan Layanan DHCP dan DNS dalam Infrastruktur

Analisis kebutuhan sangat penting untuk merancang infrastruktur jaringan yang efisien, handal, dan sesuai dengan skala serta kebutuhan organisasi.

## 4.1 Infrastruktur Jaringan
**Infrastruktur jaringan** adalah kumpulan perangkat keras (hardware) dan perangkat lunak (software) yang digunakan untuk menghubungkan komputer dan perangkat lain agar dapat berkomunikasi dan berbagi sumber daya.
*   **Perangkat Keras:** Server, Router, Switch, Access Point, Kabel.
*   **Perangkat Lunak:** Sistem Operasi Jaringan, Protokol (TCP/IP, DHCP, DNS), Aplikasi.

## 4.2 Kapan DHCP Sangat Dibutuhkan?
*   **Jaringan Besar & Dinamis:** Di kantor, kampus, atau hotel dengan banyak pengguna yang sering berganti perangkat. Konfigurasi manual tidak mungkin dilakukan.
*   **Jaringan Tamu (Guest Wi-Fi):** Memberikan akses internet sementara dan terisolasi.
*   **Perangkat Mobile:** Lingkungan dengan banyak laptop, tablet, dan ponsel yang berpindah-pindah.
*   **Efisiensi Administrasi:** Jika ada perubahan gateway atau DNS server, cukup ubah di server DHCP, semua klien akan mendapat konfigurasi baru secara otomatis saat *lease* diperbarui.

**Analisis Kebutuhan:**
*   *Jaringan kecil (5-10 perangkat statis):* DHCP mungkin opsional.
*   *Laboratorium komputer dengan 40 unit:* **DHCP sangat diperlukan.** Tanpa DHCP, administrator harus mengatur 40 IP secara manual satu per satu, yang sangat rawan kesalahan dan memakan waktu.

## 4.3 Kapan DNS Sangat Dibutuhkan?
*   **Akses ke Internet:** Mutlak diperlukan. Tanpa DNS, pengguna harus menghafal alamat IP setiap situs yang ingin dikunjungi.
*   **Layanan Internal Perusahaan:** Jika ada server internal (file server, intranet, mail server), DNS internal sangat penting agar karyawan bisa mengaksesnya dengan mudah menggunakan nama yang mudah diingat (misal: `mail.perusahaan.local`).
*   **Load Balancing dan Redundansi:** Situs besar dapat menggunakan DNS untuk mengarahkan pengguna ke server terdekat atau yang tidak sibuk, atau ke server cadangan jika server utama mati.

**Analisis Kebutuhan:**
*   *Untuk jaringan rumah yang hanya butuh akses internet:* DNS dari ISP sudah cukup.
*   *Untuk perusahaan dengan server internal:* **Membangun DNS Internal adalah keharusan** agar manajemen akses lebih mudah dan tidak bergantung pada koneksi internet eksternal untuk mengakses sumber daya internal.

## 4.4 Studi Kasus: Analisis Kebutuhan Perusahaan "XYZ"
**Skenario:**
Perusahaan XYZ akan pindah ke kantor baru dengan 150 karyawan. Mereka memiliki server internal (file server, printer server, server aplikasi HRD) dan membutuhkan akses internet untuk semua karyawan.

**Analisis dan Solusi:**

1.  **Kebutuhan DHCP:**
    *   **Analisis:** SANGAT DIBUTUHKAN. Mengelola 150 laptop karyawan secara manual tidak efisien dan rawan kesalahan. Jika ada perubahan gateway, akan sulit jika harus mengubah semua laptop satu per satu.
    *   **Solusi:** Siapkan server DHCP (bisa di router utama atau server khusus).
        *   Alokasikan *range* IP untuk karyawan (misal: `192.168.1.100` - `192.168.1.250`).
        *   **Buat Reservasi IP (Static Lease)** untuk server-server internal (file server, dll.) agar IP mereka tetap dan tidak berubah.

2.  **Kebutuhan DNS:**
    *   **Analisis (Internal):** DIBUTUHKAN. Karyawan perlu mengakses `file-server` atau `printer-1` tanpa harus menghafal IP. Ini meningkatkan produktivitas.
    *   **Analisis (Eksternal):** MUTLAK DIBUTUHKAN. Untuk akses internet ke situs eksternal seperti `google.com`.
    *   **Solusi:**
        *   Bangun **DNS Internal** (misal dengan BIND9 di Linux atau DNS Server di Windows).
        *   Buat *record* untuk server internal: `file-server.xyz.local` → `192.168.1.10`, `hrd-app.xyz.local` → `192.168.1.11`.
        *   Konfigurasikan server DNS internal ini untuk "meneruskan" (*forward*) permintaan domain internet (yang tidak ada di database internalnya) ke DNS publik (seperti `8.8.8.8`).
        *   Atur **server DHCP untuk memberikan alamat DNS Internal ini (misal: `192.168.1.5`) kepada semua klien**. Dengan demikian, klien bisa meresolusi nama internal dan eksternal.


# 5. Kesimpulan

1.  **Sistem file Linux** mengatur data dalam struktur hierarki dari root (`/`), dengan direktori standar seperti `/home`, `/etc`, dan `/var` untuk tujuan spesifik. Perintah seperti `ls`, `cd`, `mkdir` digunakan untuk navigasi dan pengelolaan.
2.  **User, group, dan permission** adalah fondasi keamanan Linux. Setiap file memiliki izin *read*, *write*, *execute* untuk pemilik, grup, dan lainnya, yang dikelola dengan perintah `chmod` dan `chown`.
3.  **DHCP** memberikan alamat IP dan konfigurasi jaringan secara otomatis kepada klien melalui proses DORA, sangat penting untuk efisiensi administrasi jaringan berskala besar.
4.  **DNS** bertindak sebagai penerjemah antara nama domain yang mudah diingat manusia dan alamat IP numerik yang digunakan komputer, sehingga memudahkan akses ke layanan internet dan internal.
5.  Dalam **infrastruktur jaringan modern**, analisis kebutuhan menunjukkan bahwa DHCP dan DNS adalah layanan krusial. DHCP menyederhanakan manajemen alamat IP, sementara DNS memudahkan akses dan penemuan layanan. Keduanya bekerja bersama untuk menciptakan jaringan yang efisien, skalabel, dan user-friendly.