# BAGIAN 1: KONSEP DASAR WEB SERVER DAN PROTOKOL HTTP/HTTPS

## 1.1 Apa Itu Web Server?

**Web server** adalah perangkat lunak (software) yang berfungsi untuk menerima permintaan (request) dari klien (biasanya browser web seperti Chrome, Firefox, dll) melalui protokol HTTP atau HTTPS, kemudian memproses permintaan tersebut, dan mengirimkan kembali respons (response) berupa konten web (HTML, CSS, JavaScript, gambar, video, dll).

### Komponen Utama Web Server:
1. **Listener** - mendengarkan port tertentu (80 untuk HTTP, 443 untuk HTTPS)
2. **Request Parser** - membaca dan memahami permintaan HTTP
3. **Handler** - memproses permintaan (mencari file, menjalankan script)
4. **Response Generator** - membuat respons HTTP
5. **Logger** - mencatat semua aktivitas

### Contoh Web Server Populer:
- Apache HTTP Server
- Nginx
- Microsoft IIS
- LiteSpeed
- Caddy

### Cara Kerja Web Server (Lengkap):

1. Client mengetik URL (misalnya: http://example.com)
2. Browser mengirim request ke server
3. Server memproses permintaan
4. Server mengirim response (halaman web)
5. Browser menampilkan hasil

## 1.2 Protokol HTTP (HyperText Transfer Protocol)

### Karakteristik HTTP:
- **Stateless** - setiap request tidak tahu request sebelumnya (kecuali dengan cookie/session)
- **Text-based** - pesan dalam format teks (mudah dibaca manusia)
- **Client-Server model** - klien memulai request, server merespons
- **Port default:** 80


### HTTP Methods (Verbs):

| Method | Fungsi | Contoh |
|--------|--------|--------|
| **GET** | Mengambil data | `GET /produk.html` |
| **POST** | Mengirim data (form, upload) | `POST /register` |
| **PUT** | Menyimpan/update resource | `PUT /user/123` |
| **DELETE** | Menghapus resource | `DELETE /file.txt` |
| **HEAD** | Sama seperti GET tapi tanpa body | `HEAD /largefile.zip` |
| **PATCH** | Update parsial | `PATCH /profile` |


### HTTP Status Codes:

**1xx (Informational):**
- `100 Continue` - server menerima awal request
- `101 Switching Protocols` - ganti protokol (WebSocket)

**2xx (Success):**
- `200 OK` - sukses
- `201 Created` - resource berhasil dibuat (POST/PUT)
- `204 No Content` - sukses tapi tidak ada konten yang dikembalikan

**3xx (Redirection):**
- `301 Moved Permanently` - URL sudah pindah permanen
- `302 Found` - redirect sementara
- `304 Not Modified` - konten tidak berubah (gunakan cache)

**4xx (Client Error):**
- `400 Bad Request` - request tidak valid
- `401 Unauthorized` - perlu autentikasi
- `403 Forbidden` - tidak punya akses
- `404 Not Found` - resource tidak ditemukan
- `405 Method Not Allowed` - method tidak diizinkan
- `429 Too Many Requests` - rate limit

**5xx (Server Error):**
- `500 Internal Server Error` - error di server
- `502 Bad Gateway` - gateway/proxy error
- `503 Service Unavailable` - server overload/maintenance
- `504 Gateway Timeout` - timeout dari upstream

### HTTP Headers:

| Header | Fungsi | Contoh |
|--------|--------|--------|
| `Host` | Menentukan domain yang diminta | `Host: www.google.com` |
| `User-Agent` | Identitas browser/klien | `User-Agent: Mozilla/5.0` |
| `Content-Type` | Tipe data body | `Content-Type: application/json` |
| `Authorization` | Token autentikasi | `Authorization: Bearer xyz123` |
| `Cookie` | Mengirim cookie ke server | `Cookie: session=abc` |
| `Cache-Control` | Mengontrol caching | `Cache-Control: max-age=3600` |
| `Location` | URL redirect (301/302) | `Location: /new-page` |


## 1.3 Protokol HTTPS 

### Apa Itu HTTPS?
HTTPS adalah versi aman dari HTTP dengan menggunakan enkripsi **SSL/TLS** (Secure Sockets Layer / Transport Layer Security).

### Perbedaan HTTP vs HTTPS:

| Aspek | HTTP | HTTPS |
|-------|------|-------|
| **Enkripsi** | Tidak ada (plain text) | AES-256 atau ChaCha20 |
| **Port** | 80 | 443 |
| **Sertifikat** | Tidak perlu | Diperlukan (SSL/TLS certificate) |
| **Kecepatan** | Lebih cepat (tanpa overhead enkripsi) | Sedikit lebih lambat (handshake + enkripsi) |
| **SEO** | Lebih rendah | Google prioritaskan HTTPS |
| **Integritas data** | Tidak dijamin | Dijamin (tidak bisa diubah tengah jalan) |
| **Autentikasi server** | Tidak ada | Dijamin oleh CA (Certificate Authority) |
| **Penggunaan** | Development, internal | Production, e-commerce, login |


### Jenis Sertifikat SSL/TLS:

| Jenis | Validasi | Cocok untuk | Contoh harga |
|-------|----------|-------------|--------------|
| **Domain Validation (DV)** | Hanya kepemilikan domain | Blog, personal | Gratis (Let's Encrypt) |
| **Organization Validation (OV)** | Domain + organisasi | Bisnis kecil | $50-100/tahun |
| **Extended Validation (EV)** | Domain + organisasi + legal | Bank, e-commerce besar | $200-500/tahun |


# BAGIAN 2: PERBANDINGAN APACHE DAN NGINX

## 2.1 Arsitektur Apache (Process-Driven)


### Kelebihan Apache:
- **.htaccess** - konfigurasi per direktori tanpa restart
- **Modul dinamis** - load/unload module tanpa recompile
- **Kompatibilitas luas** - semua OS, semua control panel
- **Autentikasi fleksibel** - mod_auth_basic, mod_auth_digest, mod_authn_dbm
- **URL rewriting** - mod_rewrite sangat powerful

### Kekurangan Apache:
- Konsumsi memori tinggi pada koneksi concurrent besar
- Performa menurun drastis pada 1000+ koneksi simultan
- Proses fork() overhead untuk setiap koneksi

## 2.2 Arsitektur Nginx (Event-Driven)

### Kelebihan Nginx:
- **Sangat ringan** - 1 worker = 1 thread menangani ribuan koneksi
- **Konsumsi memori rendah** - ~2-5 MB per worker
- **High concurrency** - handle 10.000+ koneksi simultan
- **Static file serving** - sangat cepat (sendfile syscall)
- **Reverse proxy** - built-in load balancing
- **Event-driven** - tidak ada overhead thread/process

### Kekurangan Nginx:
- **Tidak ada .htaccess** - konfigurasi hanya di file utama
- **Dynamic module** - perlu recompile untuk modul tambahan (versi lama)
- **Konfigurasi kurang fleksibel** untuk beberapa kasus


# BAGIAN 3: PROTOKOL BERBAGI FILE

## 3.1 SMB/CIFS (Server Message Block)

### Sejarah dan Versi:
- **SMB 1.0** (1980s) - tidak aman, tidak digunakan lagi
- **SMB 2.0** (2006) - dengan Windows Vista, lebih efisien
- **SMB 2.1** (2010) - improved caching
- **SMB 3.0** (2012) - enkripsi end-to-end
- **SMB 3.1.1** (2015) - enkripsi AES-256, pre-authentication integrity

### Port yang Digunakan SMB:
- **TCP 445** - SMB over TCP (modern)
- **UDP 137** - NetBIOS name service
- **UDP 138** - NetBIOS datagram service
- **TCP 139** - NetBIOS session service

### Samba di Linux:
Samba adalah implementasi open source dari protokol SMB untuk sistem Unix/Linux.

**Komponen Samba:**
- `smbd` - daemon utama SMB
- `nmbd` - NetBIOS name server
- `winbindd` - integrasi dengan Windows domain

## 3.2 NFS (Network File System)

### NFS Export Options:

| Option | Fungsi |
|--------|--------|
| `rw` | Read-write |
| `ro` | Read-only |
| `sync` | Write langsung ke disk (lebih aman) |
| `async` | Write ke cache dulu (lebih cepat) |
| `no_subtree_check` | Percepatan untuk subtree |
| `root_squash` | Map root ke nobody |
| `no_root_squash` | Root tetap root (bahaya!) |


## 3.3 Perbandingan SMB vs NFS 

| Aspek | SMB (Samba) | NFS |
|-------|-------------|-----|
| **Primary OS** | Windows, Linux (client) | Linux/Unix |
| **Autentikasi** | User/password, Domain | Host-based, Kerberos |
| **File locking** | Full support | Terbatas (NFSv4 lebih baik) |
| **Case sensitivity** | Case preserving but not sensitive | Case sensitive |
| **Performance (LAN)** | 80-120 MB/s | 100-150 MB/s |
| **Performance (WAN)** | Buruk (chatty protocol) | Lebih baik |
| **Encryption** | SMB 3.0+ (AES-256) | NFSv4+ (Kerberos) |
| **Setup complexity** | Moderate | Simple |
| **Firewall** | Banyak port (137-139,445) | 1 port (2049) |
| **Debugging** | Sulit (banyak log) | Mudah (rpcdebug) |

### Contoh Skenario Penggunaan:

**SMB/Samba cocok untuk:**
- Lingkungan mixed OS (Windows + Linux)
- Perlu autentikasi user granular
- Print server sharing
- Domain controller (Samba AD)

**NFS cocok untuk:**
- Lingkungan pure Linux/Unix
- High-performance computing (HPC)
- Shared storage untuk cluster
- Virtualization (VMware, KVM)

---

# BAGIAN 4: MANAJEMEN SHARED FOLDER DAN HAK AKSES

## 4.1 Hak Akses Linux (POSIX)

### Format RWX (Read, Write, Execute):

```
-rwxr-xr-- 1 user group 1234 Apr 6 10:00 file.txt
|  |  |  |
|  |  |  +--- Other (4+0+0 = 4) = r--
|  |  +----- Group (4+0+1 = 5) = r-x
|  +-------- Owner (4+2+1 = 7) = rwx
+---------- Type (- = file, d = directory)
```

### Tabel Nilai Numerik (Octal):

| Permission | Symbolic | Numeric |
|------------|----------|---------|
| Tidak ada | `---` | 0 |
| Execute only | `--x` | 1 |
| Write only | `-w-` | 2 |
| Write + Execute | `-wx` | 3 |
| Read only | `r--` | 4 |
| Read + Execute | `r-x` | 5 |
| Read + Write | `rw-` | 6 |
| Read + Write + Execute | `rwx` | 7 |

### Special Permissions:

| Permission | Symbol | Numeric | Fungsi |
|------------|--------|---------|--------|
| **SUID** (Set User ID) | `rws` | 4xxx | Jalankan sebagai owner file |
| **SGID** (Set Group ID) | `rws` (group) | 2xxx | Jalankan sebagai group file |
| **Sticky Bit** | `t` | 1xxx | Hanya owner yang bisa hapus |

#  Praktikum

## Praktikum 2a: Instalasi dan Konfigurasi Web Server (Pilih Apache atau Nginx)

Contoh menggunakan **Nginx** di Ubuntu 22.04.

### Instalasi
```bash
sudo apt update
sudo apt install nginx -y
sudo systemctl enable nginx
sudo systemctl start nginx
```

### Konfigurasi Virtual Host
Buat file `/etc/nginx/sites-available/demo.conf`:
```nginx
server {
    listen 80;
    server_name demo.local;
    root /var/www/demo;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

Aktifkan:
```bash
sudo mkdir -p /var/www/demo
sudo ln -s /etc/nginx/sites-available/demo.conf /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx
```

## Praktikum 2b: Mengunggah Halaman Web Statis

Buat file `/var/www/demo/index.html`:
```html
<!DOCTYPE html>
<html>
<head>
    <title>Demo Web Server</title>
</head>
<body>
    <h1>Selamat Datang di Web Server Saya!</h1>
    <p>Halaman ini disajikan oleh Nginx.</p>
</body>
</html>
```

### Pengujian akses dari klien

**Dari server sendiri:**
```bash
curl http://localhost
# atau
curl http://demo.local  # jika sudah set hosts file
```

**Dari klien Windows/Linux lain:**
1. Edit file hosts (`C:\Windows\System32\drivers\etc\hosts` atau `/etc/hosts`)
   ```
   192.168.1.100   demo.local
   ```
2. Buka browser: `http://demo.local`

---

## Praktikum 2c: Instalasi dan Konfigurasi Samba Server

### Instalasi Samba
```bash
sudo apt update
sudo apt install samba -y
```

### Buat direktori sharing
```bash
sudo mkdir -p /srv/samba/share
sudo chown nobody:nogroup /srv/samba/share
sudo chmod 0777 /srv/samba/share
```

### Konfigurasi Samba
Edit `/etc/samba/smb.conf`, tambahkan di bagian akhir:
```ini
[public]
   path = /srv/samba/share
   browseable = yes
   read only = no
   guest ok = yes
   force user = nobody

[secured]
   path = /srv/samba/secure
   browseable = yes
   read only = no
   valid users = @sambausers
   create mask = 0660
   directory mask = 0770
```

### Buat direktori secured dan user
```bash
sudo mkdir -p /srv/samba/secure
sudo groupadd sambausers
sudo useradd -M -g sambausers user1
sudo smbpasswd -a user1   # masukkan password
sudo systemctl restart smbd
```

## Praktikum 2d: Pengujian Akses dengan Autentikasi

### Dari Windows
1. Buka File Explorer
2. Ketik `\\<IP_SAMBA>\public` (tanpa password)
3. Ketik `\\<IP_SAMBA>\secured` (login dengan user1 & password)

### Dari Linux (menggunakan smbclient)
```bash
# Akses public tanpa auth
smbclient //192.168.1.100/public -N

# Akses secured dengan auth
smbclient //192.168.1.100/secured -U user1

# Mount ke filesystem
sudo mount -t cifs //192.168.1.100/secured /mnt/samba -o username=user1,password=xxx
```

### Dari Linux (NFS - tambahan jika diperlukan)
```bash
# Di server
sudo apt install nfs-kernel-server -y
echo "/srv/nfs *(rw,sync,no_subtree_check)" | sudo tee /etc/exports
sudo exportfs -a
sudo systemctl start nfs-server

# Di client
sudo apt install nfs-common -y
sudo mount -t nfs 192.168.1.100:/srv/nfs /mnt/nfs
```

---

# Ringkasan Perintah Penting

| Tujuan | Perintah |
|--------|----------|
| Cek status Nginx | `systemctl status nginx` |
| Test konfigurasi Nginx | `nginx -t` |
| Reload Nginx | `systemctl reload nginx` |
| Cek Samba share | `smbclient -L localhost -N` |
| Test Samba config | `testparm` |
| Lihat log error | `tail -f /var/log/nginx/error.log` atau `/var/log/samba/log.smbd` |

