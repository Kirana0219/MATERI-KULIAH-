# ADMINISTRASI SISTEM
* Pengenalan administrasi sistem dan peranannya dalam infrastruktur IT. 
* Perbedaan antara sistem operasi desktop dan server. 
* Konsep dasar arsitektur klien-server.

# I. PENGANTAR ADMINISTRASI SISTEM DAN LINGKUNGAN SERVER

## 1. Pengertian Administrasi Sistem

### **Definisi**
**Administrasi Sistem** (System Administration) adalah suatu disiplin ilmu dan praktik dalam bidang teknologi informasi yang mencakup proses perancangan (designing), implementasi (implementing), pemeliharaan (maintaining), konfigurasi (configuring), dan pengamanan (securing) sistem komputer beserta infrastruktur pendukungnya, dengan tujuan untuk memastikan sistem tersebut beroperasi secara efektif, efisien, andal (reliable), dan aman (secure) dalam mendukung kebutuhan organisasi atau perusahaan.
Dalam terminologi manajemen layanan TI (IT Service Management), administrasi sistem berfokus pada **penjaminan ketersediaan layanan (service availability assurance)** dan **pengelolaan perubahan sistem (system change management)** .

### **Definisi Peran Administrator Sistem**
**Administrator Sistem** (System Administrator/Sysadmin) adalah seorang profesional TI yang bertanggung jawab atas operasional harian (day-to-day operations) sistem komputer multi-pengguna (multi-user system). Tanggung jawab ini meliputi:

| Aspek Tanggung Jawab | Deskripsi Formal |
| :--- | :--- |
| **Ketersediaan Sistem** | Memastikan sistem dan layanan memiliki waktu aktif (uptime) yang tinggi sesuai dengan perjanjian tingkat layanan (SLA - Service Level Agreement). |
| **Integritas Data** | Menjamin keutuhan dan konsistensi data melalui mekanisme backup dan prosedur pemulihan bencana (disaster recovery). |
| **Keamanan Sistem** | Mengimplementasikan kebijakan keamanan (security policy), manajemen firewall, deteksi intrusi, dan penambalan kerentanan (vulnerability patching). |
| **Manajemen Konfigurasi** | Mengelola perubahan konfigurasi perangkat lunak dan perangkat keras secara terkendali dan terdokumentasi. |
| **Administrasi Pengguna** | Mengelola siklus hidup akun pengguna (user account lifecycle) dan hak aksesnya (access rights). |

### Contoh Kasus Formal (Implementasi di Institusi Pendidikan)
Sebuah universitas memiliki Sistem Informasi Akademik (SIA) yang berjalan di atas server terpusat. Administrator sistem bertanggung jawab untuk:
1.  Memastikan server SIA memiliki **ketersediaan 99,9%** (downtime tidak lebih dari 8 jam per tahun), terutama saat periode pengisian Kartu Rencana Studi (KRS).
2.  Melakukan **backup harian** database akademik ke media penyimpanan terpisah (off-site backup).
3.  Mengkonfigurasi **firewall** agar hanya mengizinkan akses ke port yang diperlukan (misal: port 80/443 untuk web) dan memblokir akses dari alamat IP mencurigakan.
4.  Membuat dan menghapus akun mahasiswa dan dosen setiap awal dan akhir tahun ajaran.

Kegagalan dalam menjalankan peran ini (misal: server down saat KRS) akan mengakibatkan gangguan operasional akademik dan kerugian reputasi institusi.

---

## 2. **Peran Administrasi Sistem dalam Infrastruktur TI**

### a. Definisi Infrastruktur TI
**Infrastruktur Teknologi Informasi (IT Infrastructure)** adalah fondasi atau landasan berupa gabungan dari komponen perangkat keras (hardware), perangkat lunak (software), sumber daya jaringan (network resources), dan layanan (services) yang diperlukan untuk mendukung keberlangsungan operasional, pengelolaan data, dan penyampaian layanan digital dalam suatu organisasi.

**Komponen Utama Infrastruktur TI:**

| Komponen | Contoh Spesifik |
| :--- | :--- |
| **Hardware** | Server fisik, perangkat penyimpanan (storage), komputer klien, perangkat jaringan (router, switch). |
| **Software** | Sistem operasi, aplikasi basis data (database), aplikasi bisnis. |
| **Jaringan** | Kabel, serat optik, perangkat nirkabel (Wi-Fi), protokol TCP/IP. |
| **Layanan Cloud** | Infrastruktur sebagai Layanan (IaaS), Platform sebagai Layanan (PaaS). |
| **Fasilitas Data Center** | Ruang server, sistem pendingin (HVAC), catu daya tak terputus (UPS). |

### b. Peran Strategis Administrasi Sistem dalam Infrastruktur
Administrasi sistem berperan sebagai **fungsi kontrol dan pemeliharaan (control and maintenance function)** yang menjamin seluruh komponen infrastruktur TI bekerja secara sinergis dan optimal. Secara lebih spesifik, peran tersebut mencakup:

| Bidang Fungsional | Peran Formal Administrator |
| :--- | :--- |
| **Ketersediaan Layanan** | Merancang dan mengimplementasikan sistem redundan (failover clustering) untuk mencegah titik kegagalan tunggal (single point of failure). |
| **Keamanan Siber** | Menegakkan kebijakan keamanan (firewall, enkripsi, autentikasi multi-faktor) dan melakukan audit keamanan berkala. |
| **Manajemen Akses** | Menerapkan prinsip hak akses minimal (Principle of Least Privilege) dalam pemberian izin kepada pengguna. |
| **Pemulihan Bencana** | Menyusun dan menguji prosedur pemulihan bencana (Disaster Recovery Plan) untuk mengembalikan sistem setelah terjadi kegagalan besar. |
| **Pemantauan Proaktif** | Menggunakan alat pemantau (monitoring tools) untuk menganalisis metrik kinerja sistem (CPU, RAM, I/O disk) dan mendeteksi anomali dini. |

### Contoh Implementasi
Sebuah perusahaan fintech menggunakan **Ubuntu Server** sebagai sistem operasi untuk menjalankan aplikasi backend. Administrator sistem bertanggung jawab terhadap:
- Pembaruan sistem berkala (security patching).
- Konfigurasi **Secure Shell (SSH)** untuk akses jarak jauh yang aman (nonaktifkan login root, gunakan autentikasi berbasis kunci).
- Implementasi firewall menggunakan **Uncomplicated Firewall (UFW)** atau **iptables**.
- Manajemen akun pengguna server (developer, tim operasional) dengan hak akses terbatas.

---




