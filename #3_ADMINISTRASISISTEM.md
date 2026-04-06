## Layanan Jaringan Dasar: DHCP dan DNS


### Pendahuluan

Dalam jaringan modern, digunakan dua layanan khusus untuk membantu proses komunikasi perangkat:
- **DHCP** (Dynamic Host Configuration Protocol)
- **DNS** (Domain Name System)

Kedua layanan ini memiliki peran sangat penting dalam infrastruktur jaringan.

---

### IP Address dalam Jaringan

- Setiap perangkat dalam jaringan **harus memiliki IP Address**.
- IP Address adalah alamat unik untuk mengidentifikasi perangkat.
- Contoh: `192.168.1.10`

#### Apa yang terjadi tanpa IP Address?
- Perangkat tidak bisa saling berkomunikasi.
- Data tidak tahu harus dikirim ke mana.

#### Permasalahan dalam Pengelolaan IP (tanpa sistem otomatis)
- IP harus diatur secara manual.
- Berpotensi terjadi **konflik IP**.
- Sulit dikelola dalam jumlah besar.
- Contoh: 30 komputer di lab harus diatur satu per satu → tidak efisien dan rawan kesalahan.

---

## DHCP (Dynamic Host Configuration Protocol)

**Definisi:**  
Layanan yang digunakan untuk memberikan alamat IP secara otomatis kepada perangkat dalam jaringan.

- Tidak perlu setting manual.
- IP diberikan otomatis saat perangkat terhubung ke jaringan.

### Fungsi DHCP
- Memberikan IP secara otomatis.
- Menghindari konflik IP.
- Mempermudah pengelolaan jaringan.

### Komponen DHCP
1. **DHCP Server** → perangkat yang bertugas memberikan alamat IP otomatis ke client.
2. **DHCP Client** → perangkat yang meminta dan menerima alamat IP dari server.
3. **IP Pool** → kumpulan alamat IP yang tersedia untuk dibagikan ke client.

### Cara Kerja DHCP (4 langkah otomatis)
1. Client meminta IP.
2. Server menawarkan IP.
3. Client menerima.
4. IP diberikan ke DHCP client.

---

## DNS (Domain Name System)

**Definisi:**  
Layanan yang digunakan untuk menerjemahkan nama domain menjadi IP Address.

- IP sulit diingat manusia.  
  Contoh: `172.217.0.142` → sulit diingat  
  `google.com` → mudah diingat

### Fungsi DNS
- Menerjemahkan nama domain menjadi alamat IP.
- Mempermudah pengguna mengakses layanan jaringan.
- Menghindari penggunaan IP address yang sulit diingat.
- Mempercepat proses pencarian alamat dalam jaringan.

### Cara Kerja DNS (Resolusi Domain)
1. User mengetik nama domain (contoh: `google.com`).
2. Permintaan dikirim ke DNS server.
3. DNS server mencari alamat IP yang sesuai.
4. DNS mengirimkan IP ke user.
5. Browser menggunakan IP tersebut untuk mengakses server.

---

## Hubungan DHCP dan DNS

- DHCP dan DNS bekerja **bersama** dalam jaringan.

| Tanpa DHCP | Tanpa DNS |
|------------|------------|
| IP harus diatur manual | Harus menggunakan IP address |
| Berisiko konflik IP | Sulit mengakses layanan (tidak user-friendly) |
| Sulit mengelola banyak perangkat | |

---

## Instalasi & Konfigurasi DHCP Server

**Persiapan:**  
- Sudah login ke Ubuntu Server.
- Koneksi internet aktif (untuk install package).

### 1. Update Repository
```bash
sudo apt update
```
**Penjelasan:**  
- Memperbarui daftar package dari repository.
- Memastikan sistem mendapat versi terbaru.
- Tanpa ini, install bisa gagal atau dapat versi lama.

### 2. Install DHCP Server
```bash
sudo apt install isc-dhcp-server
```
**Penjelasan:**  
- `isc-dhcp-server` adalah nama aplikasi DHCP.
- Setelah install, server siap dikonfigurasi.
- DHCP Server akan bertugas memberikan IP ke client.

**Hasilnya:**  
Sistem sekarang punya layanan yang bisa membagikan IP otomatis.

### Cara cek sudah terinstall atau belum
```bash
dpkg -l | grep isc-dhcp-server
```
- `dpkg -l` → menampilkan semua package terinstall.
- `|` (pipe) → menyaring hasil.
- `grep isc-dhcp-server` → mencari yang berkaitan dengan DHCP.
- Jika sudah terinstall: muncul `ii isc-dhcp-server ...`
- Jika belum terinstall: tidak muncul apa-apa.

### 3. Cek File Konfigurasi DHCP
```bash
sudo nano /etc/dhcp/dhcpd.conf
```
**Penjelasan:**  
File ini adalah file utama konfigurasi DHCP, berisi pengaturan: subnet, range IP, gateway (opsional), dan DNS (opsional).

### 4. Tambahkan Konfigurasi Dasar
```bash
subnet 192.168.10.0 netmask 255.255.255.0 {
    range 192.168.10.10 192.168.10.20;
}
```
**Simpan:** `Ctrl + O` → Enter → **Keluar:** `Ctrl + X`

**Penjelasan:**
- `subnet 192.168.10.0` (sesuaikan dengan IP kamu) → menunjukkan jaringan yang digunakan.
- `netmask 255.255.255.0` → menentukan ukuran jaringan.
- `range` → daftar IP yang akan dibagikan oleh DHCP.

### 6. Restart DHCP Service
```bash
sudo systemctl restart isc-dhcp-server
```
**Penjelasan:** Menjalankan ulang service DHCP agar konfigurasi yang diubah bisa aktif.

### 7. Cek Status DHCP
```bash
sudo systemctl status isc-dhcp-server
```
**Penjelasan:** Memastikan DHCP berjalan dengan baik. Jika error, akan terlihat di sini.  
Contoh output: `Active: active (running)`

---

## Instalasi & Konfigurasi DNS Server

### 1. Install DNS Server
```bash
sudo apt install bind9
```
- `bind9` adalah DNS server di Linux.
- Digunakan untuk membuat domain sendiri.

### 2. Edit Konfigurasi Zone
Menambahkan domain yang ingin kita buat.
```bash
sudo nano /etc/bind/named.conf.local
```
Tambahkan:
```
zone "kampus.local" {
    type master;
    file "/etc/bind/db.kampus";
};
```
**Penjelasan:**
- `zone "kampus.local"` → nama domain yang dibuat.
- `type master` → server utama.
- `file` → lokasi file zone.

### 3. Buat File Zone
```bash
sudo nano /etc/bind/db.kampus
```
Isi:
```
$TTL 604800
@ IN SOA kampus.local. root.kampus.local. (
    2
    604800
    86400
    2419200
    604800
)
```
**Penjelasan:**
- `$TTL` → waktu cache DNS.
- `SOA` → informasi server DNS.
- `NS` → nameserver.
- `A` → mapping domain ke IP.

### 4. Set DNS Resolver
Sistem harus diarahkan untuk menggunakan DNS yang telah dibuat.
```bash
sudo nano /etc/resolv.conf
```
Lalu atur:
```
nameserver 127.0.0.1
```

### 5. Restart DNS
```bash
sudo systemctl restart bind9
```
**Penjelasan:** Mengaktifkan konfigurasi DNS, wajib setelah perubahan file.

### 6. Cek Status DNS
```bash
sudo systemctl status bind9
```
**Penjelasan:** Memastikan DNS berjalan. Jika error, akan muncul di sini.  
Contoh status: `"running"`

---

## Pengujian DNS

**Hasil yang Diharapkan:**  
✓ domain berhasil diterjemahkan  
✓ muncul IP: `127.0.0.1`

### 1. Uji dengan ping
```bash
ping kampus.local
```
**Penjelasan:** Menguji apakah domain bisa diakses. Jika berhasil, domain sudah terhubung.

### 2. Uji dengan nslookup
```bash
nslookup kampus.local
```
**Penjelasan:** Melihat hasil resolusi DNS, memastikan domain diterjemahkan menjadi IP.

---

## Tabel Troubleshooting DNS (dari gambar)

| Error | Arti | Apa yang Harus Dilakukan |
|-------|------|--------------------------|
| NXDOMAIN | domain tidak ada | ✓ cek nama domain di config (named.conf.local & db file)<br/>✓ pastikan domain yang di-test sama dengan yang dibuat<br/>✓ cek record (A / www) sudah ada |
| SERVFAIL | config error | ✓ cek file zone (db.kampus)<br/>✓ jalankan `named-checkzone` untuk cek error<br/>✓ perbaiki typo (titik, spasi, format SOA)<br/>✓ restart bind9 |
| Temporary failure | DNS tidak digunakan | ✓ cek `/etc/resolv.conf`<br/>✓ pastikan ada `nameserver 127.0.0.1`<br/>✓ pastikan bind9 sudah running |

