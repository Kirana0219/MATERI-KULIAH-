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

# II. LINGKUNGAN SERVER

## 1. Pengertian dan Definisi Server

### Definisi Formal
**Server** adalah suatu sistem komputer, baik dalam bentuk perangkat keras (hardware) khusus maupun perangkat lunak (software) layanan, yang dirancang untuk menyediakan layanan (services), sumber daya (resources), atau data kepada satu atau lebih komputer klien (client) melalui suatu jaringan (network).

Karakteristik fundamental server adalah kemampuannya untuk beroperasi secara **terus-menerus (always-on)** dan melayani **permintaan simultan (concurrent requests)** dari banyak klien.

### Klasifikasi Server Berdasarkan Implementasi

| Jenis Server | Definisi Formal | Contoh Implementasi |
| :--- | :--- | :--- |
| **Dedicated Server (Fisik)** | Server yang diimplementasikan pada satu unit komputer fisik yang sepenuhnya didedikasikan untuk menjalankan layanan tertentu. | Dell PowerEdge, HPE ProLiant. |
| **Virtual Machine (VM)** | Server yang dijalankan sebagai mesin virtual di atas sebuah perangkat lunak hipervisor (hypervisor) yang memvirtualisasi sumber daya perangkat keras fisik. | VMware vSphere, Microsoft Hyper-V, Proxmox. |
| **Container** | Bentuk virtualisasi pada tingkat sistem operasi yang lebih ringan, di mana beberapa container berbagi kernel OS yang sama namun beroperasi dalam ruang pengguna (user space) yang terisolasi. | Docker, LXC, Podman. |
| **Cloud Server** | Server virtual yang disediakan dan dikelola oleh penyedia layanan cloud (cloud service provider) dan diakses oleh pengguna melalui internet dengan model pembayaran sesuai pemakaian (pay-as-you-go). | Amazon EC2, Google Compute Engine, Azure VM. |

### Contoh Jenis Server Berdasarkan Layanan (Fungsional)

| Jenis Server | Layanan yang Disediakan | Perangkat Lunak Umum |
| :--- | :--- | :--- |
| **Web Server** | Menyimpan, memproses, dan mengirimkan halaman web kepada klien (browser). | Apache HTTP Server, Nginx, IIS. |
| **Database Server** | Menyediakan layanan pengelolaan basis data dan menangani query dari klien. | MySQL, MariaDB, PostgreSQL, Oracle Database. |
| **File Server** | Menyediakan ruang penyimpanan terpusat untuk file dan mengatur akses pengguna terhadap file tersebut. | Samba (untuk integrasi Windows), NFS. |
| **Mail Server** | Menangani pengiriman dan penerimaan email. | Postfix, Sendmail, Microsoft Exchange. |

---

# III. PERBEDAAN SISTEM OPERASI DESKTOP DAN SERVER

## 1. Definisi Sistem Operasi

**Sistem Operasi (Operating System/OS)** adalah perangkat lunak sistem (system software) yang bertindak sebagai perantara (intermediary) antara pengguna dan perangkat keras komputer. Fungsi utamanya adalah mengelola dan mengkoordinasikan seluruh sumber daya perangkat keras serta menyediakan lingkungan yang memungkinkan perangkat lunak aplikasi (application software) dapat dijalankan.

## 2. Sistem Operasi Desktop

### Definisi Formal
**Sistem Operasi Desktop** adalah kelas sistem operasi yang dirancang khusus untuk digunakan pada komputer pribadi (personal computer) atau workstation, dengan fokus utama pada **interaktivitas pengguna (user interactivity)** dan **kemudahan penggunaan (ease of use)** .

### Karakteristik Formal

| Karakteristik | Deskripsi |
| :--- | :--- |
| **Antarmuka Pengguna Grafis (GUI)** | Dilengkapi dengan Graphical User Interface yang kaya dan intuitif untuk memfasilitasi interaksi langsung dengan pengguna. |
| **Pengguna Tunggal (Single-User)** | Dioptimalkan untuk digunakan oleh satu pengguna dalam satu waktu. Manajemen sumber daya difokuskan pada sesi pengguna aktif. |
| **Multitasking Terbatas** | Mampu menjalankan beberapa aplikasi secara bersamaan, namun tidak dirancang untuk menangani ribuan koneksi simultan dari jaringan. |
| **Manajemen Daya (Power Management)** | Memiliki fitur manajemen daya canggih untuk memperpanjang masa pakai baterai pada perangkat portabel (laptop). |
| **Ketersediaan (Uptime)** | Tidak diharuskan untuk beroperasi terus-menerus (24/7). Proses reboot (restart) berkala adalah hal yang umum, terutama setelah instalasi pembaruan. |

### Contoh Implementasi
- Microsoft Windows 11
- Apple macOS Sonoma
- Ubuntu Desktop (berbasis Linux)

## 3. Sistem Operasi Server

### Definisi Formal
**Sistem Operasi Server** adalah kelas sistem operasi yang dirancang khusus untuk dijalankan pada perangkat keras server, dengan fokus utama pada **penyediaan layanan jaringan (network service delivery)** , **stabilitas (stability)** , **keamanan (security)** , dan **kemampuan menangani beban kerja tinggi (high-throughput workload)** .

### Karakteristik Formal

| Karakteristik | Deskripsi |
| :--- | :--- |
| **Berorientasi Layanan (Service-Oriented)** | Fungsi utamanya adalah menjalankan dan mengelola layanan-layanan jaringan seperti web server, database server, dan file server. |
| **Dukungan Multi-User** | Dirancang secara arsitektural untuk melayani permintaan dari ratusan hingga ribuan pengguna (klien) secara simultan. |
| **Antarmuka Berbasis Teks (CLI)** | Seringkali dioperasikan tanpa antarmuka grafis (headless) untuk menghemat sumber daya sistem (CPU, RAM, dan ruang disk) yang dapat dialokasikan untuk layanan. Administrasi dilakukan melalui **Command Line Interface (CLI)** . |
| **Ketersediaan Tinggi (High Availability)** | Dirancang untuk beroperasi secara terus-menerus (24 jam sehari, 7 hari seminggu) dengan waktu henti (downtime) yang minimal. |
| **Keamanan yang Lebih Kompleks** | Dilengkapi dengan mekanisme keamanan yang lebih canggih dan ketat, termasuk firewall terintegrasi, kontrol akses wajib (Mandatory Access Control/MAC), dan dukungan enkripsi yang kuat. |

### Contoh Implementasi
- Microsoft Windows Server 2022
- Red Hat Enterprise Linux (RHEL)
- Ubuntu Server (edisi LTS/Long Term Support)
- CentOS Stream
- SUSE Linux Enterprise Server (SLES)

## 4. Perbandingan Komprehensif Desktop vs Server

| Aspek Perbandingan | Sistem Operasi Desktop | Sistem Operasi Server |
| :--- | :--- | :--- |
| **Tujuan Perancangan** | Produktivitas pribadi, komputasi interaktif. | Penyediaan layanan jaringan, komputasi latar belakang. |
| **Pengguna Sasaran** | Pengguna individu (end-user). | Banyak klien (client) melalui jaringan. |
| **Beban Kerja (Workload)** | Aplikasi perkantoran, multimedia, browsing web. | Layanan web, database, email, otentikasi pengguna. |
| **Ketersediaan (Uptime)** | Tidak diwajibkan 24/7. | Diwajibkan 24/7, seringkali dengan target 99.9% atau lebih. |
| **Manajemen Sumber Daya** | Diutamakan untuk responsivitas aplikasi pengguna. | Diutamakan untuk throughput jaringan dan efisiensi layanan. |
| **Kompleksitas Keamanan** | Standar, berfokus pada keamanan pengguna lokal. | Tinggi, berfokus pada keamanan perimeter jaringan dan data. |
| **Contoh Produk** | Windows 11, macOS, Ubuntu Desktop. | Windows Server 2022, RHEL, Ubuntu Server. |

---

# IV. KONSEP DASAR ARSITEKTUR KLIEN–SERVER

## 1. Definisi Formal

**Arsitektur Klien–Server (Client–Server Architecture)** adalah suatu model komputasi terdistribusi (distributed computing model) yang membagi tugas atau beban kerja (workload) antara penyedia layanan (provider of a service), yang disebut **server**, dan peminta layanan (requestor of a service), yang disebut **klien (client)** . Keduanya berkomunikasi melalui jaringan komputer dengan menggunakan protokol komunikasi yang telah ditentukan.

Dalam model ini, server bertindak sebagai penyedia sumber daya pasif yang menunggu permintaan, sementara klien bertindak sebagai pemrakarsa komunikasi (initiator) yang aktif mengirimkan permintaan.

## 2. Cara Kerja (Mekanisme Request-Response)

Arsitektur klien-server bekerja berdasarkan siklus **permintaan dan tanggapan (request-response cycle)** :

1.  **Inisiasi (Initiation):** Aplikasi klien memulai komunikasi dengan mengirimkan pesan permintaan (request message) melalui jaringan ke alamat server yang dituju. Permintaan ini biasanya berisi spesifikasi layanan atau data yang diinginkan.
2.  **Penerimaan dan Pemrosesan (Reception and Processing):** Server yang secara terus-menerus "mendengarkan" (listening) pada port tertentu menerima permintaan tersebut. Server kemudian memproses permintaan tersebut. Proses ini dapat melibatkan eksekusi logika aplikasi, pengambilan data dari basis data (database query), atau interaksi dengan sistem lain.
3.  **Tanggapan (Response):** Setelah selesai memproses, server mengirimkan pesan tanggapan (response message) kembali ke klien. Tanggapan ini dapat berupa data yang diminta, konfirmasi keberhasilan, atau pesan kesalahan (error message).

### Ilustrasi Formal: Akses Halaman Web

1.  **Klien:** Browser web (misal: Google Chrome) pada laptop pengguna mengirimkan **permintaan HTTP (HTTP Request)** ke server yang menghosting situs web `www.contoh.com`.
2.  **Server:** Server web (misal: Nginx) yang mendengarkan di **port 80 (HTTP)** atau **port 443 (HTTPS)** menerima permintaan tersebut. Server web memproses permintaan, mungkin dengan menjalankan script PHP atau mengambil konten statis dari hard disk.
3.  **Respons:** Server web mengirimkan **tanggapan HTTP (HTTP Response)** , yang berisi kode status (misal: 200 OK) dan halaman web dalam format HTML, kembali ke browser.
4.  **Render:** Browser menerima respons dan merender (menampilkan) halaman web tersebut kepada pengguna.

## 3. Peran dan Karakteristik Klien dan Server

| Atribut | Klien (Client) | Server |
| :--- | :--- | :--- |
| **Peran Arsitektural** | Pemrakarsa permintaan (Request Initiator). | Penyedia layanan (Service Provider), penanggap permintaan (Request Responder). |
| **Inisiasi Komunikasi** | Aktif memulai komunikasi. | Pasif, menunggu permintaan dari klien. |
| **Koneksi** | Membangun koneksi ke server saat dibutuhkan. | Secara konstan "mendengarkan" (listening) pada port tertentu untuk koneksi masuk. |
| **Kompleksitas** | Relatif lebih sederhana, fokus pada interaksi pengguna. | Lebih kompleks, menangani logika bisnis, keamanan, dan konkurensi. |
| **Contoh** | Browser web, aplikasi mobile, email client (Outlook). | Web server (Apache), database server (MySQL), file server (Samba). |

## 4. Kelebihan dan Keterbatasan Arsitektur Klien-Server

### Kelebihan (Advantages)
- **Sentralisasi Kontrol (Centralized Control):** Data dan logika bisnis (business logic) disimpan dan dikelola secara terpusat di server. Hal ini memudahkan pemeliharaan, pembaruan, dan penegakan kebijakan keamanan.
- **Skalabilitas (Scalability):** Kapasitas server (misal: CPU, RAM, storage) dapat ditingkatkan (scaling up/vertikal) atau jumlah server dapat ditambah (scaling out/horizontal) untuk mengakomodasi pertumbuhan jumlah klien.
- **Keamanan Terkelola (Managed Security):** Keamanan data dapat difokuskan dan dikelola di tingkat server, mengurangi risiko kebocoran data dari sisi klien.
- **Aksesibilitas (Accessibility):** Klien dapat mengakses layanan dari berbagai lokasi selama terhubung ke jaringan (termasuk internet).

### Keterbatasan (Disadvantages)
- **Titik Kegagalan Tunggal (Single Point of Failure - SPoF):** Jika server mengalami kegagalan (failure), seluruh klien tidak dapat mengakses layanan yang disediakan oleh server tersebut. Untuk mengatasi hal ini, diperlukan mekanisme redundansi seperti clustering.
- **Kemacetan Jaringan (Network Congestion):** Komunikasi yang intensif antara klien dan server dapat menyebabkan kemacetan pada jaringan, terutama jika jumlah klien sangat besar.
- **Biaya Infrastruktur (Infrastructure Cost):** Membutuhkan investasi yang signifikan untuk pengadaan, pemeliharaan, dan pengoperasian server yang handal, termasuk sistem pendingin dan catu daya cadangan.
- **Ketergantungan pada Jaringan (Network Dependency):** Kinerja dan ketersediaan layanan sangat bergantung pada ketersediaan dan kualitas jaringan. Gangguan jaringan akan melumpuhkan akses klien ke server.

## 5. Contoh Penerapan dalam Kehidupan Sehari-hari

Arsitektur ini merupakan fondasi dari hampir semua layanan digital modern:

1.  **Perbankan Digital (Mobile Banking):** Aplikasi mobile banking (klien) mengirimkan permintaan saldo ke server bank. Server bank memproses permintaan dengan mengambil data dari database nasabah, lalu mengirimkan informasi saldo kembali ke aplikasi.
2.  **E-commerce (Belanja Online):** Browser pengguna (klien) mengirimkan permintaan untuk menampilkan katalog produk ke server e-commerce. Server memproses permintaan, berinteraksi dengan database produk, dan mengirimkan halaman katalog yang telah dibuat (render) kembali ke browser.
3.  **Layanan Email (Email Service):** Aplikasi email (klien) terhubung ke server email untuk mengunduh daftar email baru menggunakan protokol IMAP atau POP3.
4.  **Game Online (Online Gaming):** Perangkat game (konsol/PC) sebagai klien terhubung ke server game pusat yang bertanggung jawab untuk menjaga konsistensi dunia game, memproses interaksi antar pemain, dan mencegah kecurangan (cheating).

Berikut adalah kelanjutan materi dengan struktur formal, bahasa akademis, dan pengertian yang mendalam sesuai permintaan Anda, melanjutkan dari bagian V yang sebelumnya (Manajemen Sistem File) ke bagian VI dan VII.

---

# V. MANAJEMEN SISTEM FILE (Sambungan)

*(Catatan: Bagian ini merupakan kelanjutan dari materi Manajemen Sistem File yang telah disampaikan sebelumnya, difokuskan pada pemahaman hak akses sebagai jembatan menuju Manajemen Pengguna.)*

## 4. Hak Akses File (File Permissions) dalam Sistem Operasi Multi-User

### Definisi Formal
**Hak Akses File (File Permissions)** adalah suatu mekanisme keamanan dalam sistem operasi yang digunakan untuk mengatur operasi apa saja yang dapat dilakukan oleh subjek (pengguna atau proses) terhadap suatu objek (file atau direktori). Mekanisme ini merupakan implementasi dari kebijakan **kontrol akses mandatori (Mandatory Access Control/MAC)** atau **kontrol akses diskresioner (Discretionary Access Control/DAC)** , yang bertujuan untuk melindungi integritas dan kerahasiaan data dalam lingkungan multi-pengguna.

Pada sistem operasi berbasis Unix/Linux, hak akses direpresentasikan dalam tiga kelas identitas:
1.  **Owner (Pemilik):** Pengguna yang menciptakan atau memiliki file/direktori tersebut.
2.  **Group (Grup):** Sekumpulan pengguna yang memiliki kebutuhan akses bersama terhadap file/direktori.
3.  **Others (Lainnya):** Semua pengguna lain yang terdaftar dalam sistem, di luar pemilik dan anggota grup.

### Representasi Simbolik dan Numerik

Hak akses untuk setiap kelas identitas ditentukan oleh tiga jenis izin dasar:

| Izin | Simbol | Pengaruh pada File | Pengaruh pada Direktori |
| :--- | :--- | :--- | :--- |
| **Read (Baca)** | `r` | Mengizinkan pembacaan isi file. | Mengizinkan penampilan daftar file di dalam direktori (misal: perintah `ls`). |
| **Write (Tulis)** | `w` | Mengizinkan modifikasi atau penghapusan isi file. | Mengizinkan pembuatan, penghapusan, atau penggantian nama file di dalam direktori. |
| **eXecute (Jalankan)** | `x` | Mengizinkan eksekusi file sebagai program/script. | Mengizinkan akses masuk ke dalam direktori (misal: perintah `cd`). |

**Format Notasi:**
`[Owner] [Group] [Others]`
` rwx     rwx     rwx `

**Contoh Notasi:** `rwx r-x r--`

Interpretasi formal dari notasi di atas adalah:
- **Owner:** Memiliki hak penuh untuk membaca (`r`), menulis (`w`), dan menjalankan (`x`) file.
- **Group:** Memiliki hak untuk membaca (`r`) dan menjalankan (`x`) file, tetapi **tidak** memiliki hak untuk menulis (`w`) atau memodifikasi file.
- **Others:** Hanya memiliki hak untuk membaca (`r`) file, tanpa hak menulis maupun menjalankan.

### Representasi Numerik (Oktal)

Untuk efisiensi konfigurasi, hak akses juga dapat direpresentasikan dalam bilangan oktal (basis 8), di mana setiap izin diberi nilai numerik:
- `r` (read) = 4
- `w` (write) = 2
- `x` (execute) = 1
- `-` (tidak ada izin) = 0

Nilai untuk suatu kelas identitas dihitung dengan menjumlahkan nilai izin yang diberikan.

**Tabel Nilai Oktal:**

| Nilai | Izin (Simbolik) | Arti |
| :--- | :--- | :--- |
| **7** | `rwx` | Baca, Tulis, dan Eksekusi |
| **6** | `rw-` | Baca dan Tulis (tanpa Eksekusi) |
| **5** | `r-x` | Baca dan Eksekusi (tanpa Tulis) |
| **4** | `r--` | Hanya Baca |
| **3** | `-wx` | Tulis dan Eksekusi (jarang digunakan) |
| **2** | `-w-` | Hanya Tulis |
| **1** | `--x` | Hanya Eksekusi |
| **0** | `---` | Tanpa Izin |

**Contoh Konversi:**
Notasi `rwx r-x r--` setara dengan nilai oktal **754**.
- Owner: `rwx` = 4+2+1 = 7
- Group: `r-x` = 4+0+1 = 5
- Others: `r--` = 4+0+0 = 4

---

# VI. MANAJEMEN PENGGUNA (USER MANAGEMENT)

## 1. Konsep Dasar Pengguna dan Grup

### Definisi Formal
Dalam konteks sistem operasi multi-pengguna (multi-user operating system), **manajemen pengguna (user management)** adalah proses administrasi yang mengatur siklus hidup akun pengguna, mulai dari kreasi, modifikasi, hingga penghapusan, serta pengelompokannya ke dalam grup-grup tertentu. Tujuan utamanya adalah untuk mengimplementasikan kebijakan **autentikasi (authentication)** dan **otorisasi (authorization)** .

Setiap entitas yang dapat berinteraksi dengan sistem (baik manusia maupun proses) direpresentasikan sebagai **pengguna (user)** . Setiap pengguna memiliki atribut identitas unik sebagai berikut:

| Atribut | Deskripsi Formal |
| :--- | :--- |
| **Username** | Identitas tekstual yang mudah diingat oleh manusia (human-readable identifier) untuk merujuk kepada suatu akun pengguna. |
| **Password** | Suatu rahasia bersama (shared secret) yang digunakan untuk memverifikasi identitas pengguna melalui proses autentikasi. Password disimpan dalam bentuk terenkripsi (hash) di dalam sistem. |
| **UID (User ID)** | **User Identifier**, suatu angka unik (unique numerical identifier) yang secara internal digunakan oleh kernel sistem operasi untuk mengidentifikasi pengguna. Sistem mengenali pengguna berdasarkan UID, bukan berdasarkan username. |
| **GID (Group ID)** | **Group Identifier**, suatu angka unik yang mengidentifikasi grup utama (primary group) dari pengguna tersebut. |
| **Group (Grup)** | Kumpulan dari beberapa pengguna yang berbagi kebutuhan akses yang sama terhadap sumber daya sistem. Grup memudahkan pemberian hak akses secara kolektif, daripada memberikannya satu per satu kepada setiap individu. |

### Tujuan Manajemen Pengguna
Secara formal, manajemen pengguna memiliki tiga tujuan fundamental dalam keamanan sistem:

1.  **Akuntabilitas (Accountability) & Pembatasan Akses (Access Restriction):** Setiap tindakan dalam sistem dapat dilacak kembali ke pengguna tertentu (audit trail). Pengguna hanya diberikan akses ke sumber daya yang diperlukan untuk menjalankan tugasnya (berdasarkan prinsip **Least Privilege**).
2.  **Penjagaan Kerahasiaan dan Integritas Data (Data Confidentiality & Integrity):** Dengan memisahkan akses antar pengguna, data milik seorang pengguna atau suatu grup terlindungi dari akses, modifikasi, atau penghapusan oleh pengguna lain yang tidak berwenang.
3.  **Pembedaan Hak Administratif (Administrative Privilege Separation):** Membedakan antara pengguna biasa dengan administrator (root) untuk mencegah perubahan konfigurasi sistem yang tidak sengaja atau berbahaya.

## 2. Jenis-Jenis Pengguna dalam Sistem Operasi Linux

Dalam sistem operasi berbasis Linux/Unix, pengguna diklasifikasikan ke dalam tiga kategori berdasarkan UID dan perannya:

| Jenis Pengguna | Rentang UID (Umum) | Deskripsi Formal |
| :--- | :--- | :--- |
| **Root (Superuser)** | **UID 0** | Pengguna dengan hak istimewa tertinggi (privileged user) dalam sistem. Root memiliki akses tak terbatas terhadap seluruh sumber daya, file, dan proses. Akun ini digunakan untuk tugas-tugas administrasi sistem tingkat rendah, seperti menginstal perangkat lunak, mengkonfigurasi perangkat keras, dan membuat akun pengguna lain. Karena haknya yang absolut, penggunaan akun root untuk kegiatan sehari-hari sangat tidak disarankan (security best practice). |
| **System User (Pengguna Sistem)** | **UID 1–999** (bervariasi antar distribusi) | Pengguna yang dibuat secara otomatis oleh sistem atau saat instalasi paket perangkat lunak. Pengguna ini **bukan** untuk login oleh manusia, melainkan digunakan oleh proses-proses latar belakang (daemon/services) untuk menjalankan layanan tertentu. Tujuannya adalah untuk mengisolasi hak akses layanan. Contoh: `www-data` (untuk web server), `mysql` (untuk database server), `sshd` (untuk SSH server). |
| **Regular User (Pengguna Biasa)** | **UID >= 1000** (umumnya) | Akun yang dibuat untuk digunakan oleh pengguna manusia. Pengguna biasa memiliki akses terbatas pada direktori home-nya sendiri (`/home/nama_pengguna`) dan tidak memiliki izin untuk mengubah file sistem atau konfigurasi global. |

## 3. Perintah Dasar Manajemen Pengguna (Linux CLI)

Manajemen pengguna dalam lingkungan Linux sebagian besar dilakukan melalui antarmuka baris perintah (Command Line Interface - CLI). Berikut adalah perintah-perintah fundamental beserta definisi formalnya:

| Perintah | Fungsi Formal |
| :--- | :--- |
| **`adduser`** | Perintah tingkat tinggi (high-level) untuk menambahkan akun pengguna baru ke dalam sistem. Perintah ini secara otomatis membuat entri di file `/etc/passwd`, membuat direktori home (`/home/username`), menyalin file konfigurasi default (skel), dan meminta pengaturan password. |
| **`useradd`** | Perintah tingkat rendah (low-level) untuk menambahkan pengguna. Lebih fleksibel tetapi memerlukan parameter tambahan (seperti `-m` untuk membuat home direktori). |
| **`passwd`** | Digunakan untuk mengatur atau mengubah password pengguna. Password akan di-hash dan disimpan di file `/etc/shadow`. |
| **`usermod`** | Perintah untuk memodifikasi atribut akun pengguna yang sudah ada, seperti mengubah grup utama (`-g`), menambahkan ke grup tambahan (`-aG`), mengubah direktori home (`-d`), atau mengunci (`-L`) / membuka kunci (`-U`) akun. |
| **`deluser`** atau **`userdel`** | Perintah untuk menghapus akun pengguna dari sistem. Opsi `--remove-home` atau `-r` dapat ditambahkan untuk menghapus direktori home dan mail spool pengguna tersebut. |

**Contoh Implementasi Formal:**

Untuk menambahkan seorang pengguna baru bernama `mahasiswa1` ke dalam sistem:

```bash
sudo adduser mahasiswa1
```

Proses ini akan memicu serangkaian tindakan sistem:
1.  Membuat UID baru (misal: 1001) dan GID baru (1001) untuk grup `mahasiswa1`.
2.  Membuat entri di `/etc/passwd`: `mahasiswa1:x:1001:1001:,,,:/home/mahasiswa1:/bin/bash`
3.  Membuat direktori `/home/mahasiswa1`.
4.  Menyalin file dari `/etc/skel` ke `/home/mahasiswa1`.
5.  Meminta administrator untuk memasukkan password bagi user `mahasiswa1` (yang kemudian di-hash dan disimpan di `/etc/shadow`).

---

# VII. KEAMANAN DALAM ADMINISTRASI SERVER

## Definisi Formal

**Keamanan Server (Server Security)** adalah suatu cabang dari keamanan siber (cybersecurity) yang berfokus pada perlindungan aset data dan sumber daya komputasi yang berada pada server dari ancaman yang bersifat internal maupun eksternal. Tujuannya adalah untuk menjaga **kerahasiaan (confidentiality)** , **integritas (integrity)** , dan **ketersediaan (availability)** layanan dan data, yang dikenal sebagai **Triad CIA (CIA Triad)** .

Dalam administrasi sistem, keamanan bukanlah suatu produk akhir, melainkan suatu **proses berkelanjutan (ongoing process)** yang terdiri dari serangkaian kebijakan, mekanisme, dan praktik terbaik (best practices).

## 1. Komponen dan Praktik Keamanan Fundamental

### a. Firewall (Pertahanan Perimeter Jaringan)
**Definisi:** **Firewall** adalah suatu sistem keamanan jaringan yang memonitor dan mengontrol lalu lintas jaringan masuk (inbound) dan keluar (outbound) berdasarkan aturan keamanan (security rules) yang telah ditentukan. Firewall bertindak sebagai penghalang (barrier) antara jaringan internal yang terpercaya dan jaringan eksternal yang tidak terpercaya (seperti internet).

**Implementasi di Linux:**
- **`iptables`** : Antarmuka baris perintah tradisional untuk mengkonfigurasi tabel firewall di kernel Linux. Memberikan kontrol yang sangat granular namun memiliki kurva pembelajaran yang curam.
- **`UFW (Uncomplicated Firewall)`** : Sebuah *front-end* yang lebih sederhana untuk `iptables`, dirancang untuk memudahkan pengguna dalam mengelola firewall. UFW menyediakan sintaks yang lebih intuitif.

**Contoh Konfigurasi UFW:**
Mengizinkan lalu lintas untuk layanan web (HTTP dan HTTPS) dan SSH, kemudian mengaktifkan firewall.
```bash
sudo ufw allow 22/tcp     # Mengizinkan SSH
sudo ufw allow 80/tcp     # Mengizinkan HTTP
sudo ufw allow 443/tcp    # Mengizinkan HTTPS
sudo ufw enable           # Mengaktifkan firewall
```

### b. Konfigurasi SSH yang Aman (Secure Shell Hardening)
**Definisi:** **SSH (Secure Shell)** adalah protokol jaringan kriptografis untuk mengoperasikan layanan jaringan dengan aman melalui jaringan yang tidak aman. Karena SSH adalah gerbang utama untuk akses administratif jarak jauh, mengamankan konfigurasinya adalah hal yang krusial.

**Praktik Terbaik (Best Practices) untuk Hardening SSH:**
1.  **Nonaktifkan Login Root:** Melarang login langsung sebagai user `root` melalui SSH. Administrator harus login sebagai user biasa, kemudian menggunakan `sudo` untuk menjalankan perintah administratif.
    - Konfigurasi di `/etc/ssh/sshd_config`: `PermitRootLogin no`
2.  **Gunakan Autentikasi Berbasis Kunci (Key-Based Authentication):** Mengganti autentikasi password dengan pasangan kunci publik-privat (public-private key pair). Ini jauh lebih aman karena tahan terhadap serangan brute-force.
    - Konfigurasi: `PasswordAuthentication no`
3.  **Ubah Port Default:** Mengubah port SSH dari default (22) ke port non-standar untuk mengurangi jumlah serangan bot otomatis.
    - Konfigurasi: `Port 2222` (contoh)
4.  **Batasi Pengguna yang Dapat Login:** Menentukan secara eksplisit pengguna mana yang diizinkan mengakses melalui SSH.
    - Konfigurasi: `AllowUsers adminuser deployuser`

### c. Enkripsi (Encryption)
**Definisi:** **Enkripsi** adalah proses mengubah data (plaintext) menjadi bentuk yang tidak dapat dibaca (ciphertext) menggunakan suatu algoritma dan kunci (key). Enkripsi melindungi kerahasiaan data, baik saat disimpan (data at rest) maupun saat dikirim melalui jaringan (data in transit).

**Implementasi:**
- **Data in Transit:** Menggunakan protokol **TLS/SSL** untuk HTTPS, atau **SSH** untuk remote access.
- **Data at Rest:** Menggunakan tools seperti **LUKS (Linux Unified Key Setup)** untuk enkripsi disk penuh (full disk encryption) atau **GnuPG (GPG)** untuk enkripsi file individual.

### d. Backup Berkala (Periodic Backup)
**Definisi:** **Backup** adalah proses membuat salinan (copy) data dari media penyimpanan primer ke media penyimpanan sekunder atau lokasi yang aman (off-site). Tujuannya adalah untuk **pemulihan data (data recovery)** jika terjadi kegagalan sistem, kerusakan data, serangan siber (seperti ransomware), atau bencana alam.

**Strategi Backup (3-2-1 Rule):**
- **3** salinan data (1 data asli + 2 cadangan).
- Disimpan di **2** media yang berbeda (misal: hard disk lokal + cloud storage).
- **1** salinan disimpan di luar lokasi (off-site).

### e. Pemantauan Log Sistem (System Log Monitoring)
**Definisi:** **Log sistem (system log)** adalah catatan kronologis (time-stamped records) dari peristiwa (events) yang terjadi dalam sistem operasi, aplikasi, dan layanan. Memantau log secara proaktif memungkinkan administrator untuk mendeteksi anomali, memecahkan masalah, dan mengidentifikasi potensi pelanggaran keamanan.

**Lokasi Log di Linux:**
Semua log sistem utama disimpan di direktori **`/var/log/`** . File-file log penting meliputi:
- **`/var/log/syslog` atau `/var/log/messages`** : Log sistem umum.
- **`/var/log/auth.log`** : Log terkait autentikasi (login sukses/gagal, penggunaan sudo).
- **`/var/log/dmesg`** : Log dari kernel dan driver perangkat.
- **`/var/log/nginx/access.log` dan `error.log`** : Log khusus untuk web server Nginx.

## 2. Model Keamanan Berlapis (Defense in Depth)

Semua komponen keamanan di atas harus diimplementasikan sebagai bagian dari strategi **Pertahanan Berlapis (Defense in Depth)** . Konsep ini mengakui bahwa tidak ada satu pun lapisan keamanan yang sempurna. Dengan memiliki banyak lapisan (firewall, konfigurasi SSH yang aman, enkripsi, backup), jika satu lapisan berhasil ditembus oleh penyerang, masih ada lapisan lain yang melindungi aset inti.




