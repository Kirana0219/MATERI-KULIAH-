
# MATERI KOMPREHENSIF KOMPUTASI AWAN (CLOUD COMPUTING)


## BAB 1: PENGENALAN KOMPUTASI AWAN (CLOUD COMPUTING)

### 1.1 Definisi dan Konsep Dasar Komputasi Awan

Secara etimologis, istilah "awan" dalam komputasi awan merupakan metafora dari internet yang dalam diagram jaringan sering digambarkan sebagai bentuk awan untuk menyembunyikan kompleksitas infrastruktur di baliknya.

**Definisi Formal NIST:**
Menurut *National Institute of Standards and Technology* (NIST), komputasi awan didefinisikan sebagai:

> *"Suatu model yang memungkinkan adanya akses jaringan yang ubiquitous (di mana-mana), nyaman, dan on-demand ke sekumpulan sumber daya komputasi yang dapat dikonfigurasi (misalnya jaringan, server, penyimpanan, aplikasi, dan layanan) yang dapat dengan cepat disediakan dan dirilis dengan upaya manajemen minimal atau interaksi dengan penyedia layanan."*

**Definisi Konseptual:**
Komputasi awan adalah paradigma di mana informasi secara permanen tersimpan di server di internet dan disimpan secara sementara di komputer pengguna (klien), termasuk di dalamnya adalah desktop, komputer tablet, notebook, hingga perangkat genggam.

**Analogi Pemahaman:**
Untuk memahami komputasi awan secara intuitif, dapat digunakan analogi **layanan listrik**. Sebelum era listrik, setiap pabrik harus memiliki generator sendiri. Setelah jaringan listrik hadir, pabrik cukup "menyambung" dan membayar berdasarkan pemakaian. Demikian pula dengan komputasi awan: organisasi tidak perlu memiliki pusat data sendiri, cukup "menyambung" ke penyedia cloud dan membayar sesuai sumber daya yang dikonsumsi.

### 1.2 Karakteristik Esensial Komputasi Awan (Lengkap dengan Penjelasan)

Berdasarkan standar NIST SP 800-145, terdapat lima karakteristik esensial yang harus dimiliki oleh sebuah sistem komputasi awan:

**1. On-Demand Self-Service (Layanan Mandiri Sesuai Permintaan)**
- **Pengertian:** Pengguna dapat secara sepihak menyediakan kemampuan komputasi, seperti waktu server dan penyimpanan jaringan, secara otomatis tanpa memerlukan interaksi manusia dengan penyedia layanan.
- **Contoh:** Seorang pengembang dapat menambah kapasitas penyimpanan dari 50GB menjadi 200GB melalui dashboard AWS tanpa perlu menghubungi customer service Amazon.

**2. Broad Network Access (Akses Jaringan Luas)**
- **Pengertian:** Sumber daya tersedia melalui jaringan dan dapat diakses melalui mekanisme standar yang mempromosikan penggunaan oleh platform klien yang heterogen.
- **Implikasi:** Dapat diakses dari berbagai perangkat seperti smartphone, tablet, laptop, dan workstation.
- **Contoh:** Seorang dosen dapat mengakses materi kuliah dari Google Drive menggunakan laptop di kantor, kemudian melanjutkannya dari tablet di rumah.

**3. Resource Pooling (Penggabungan Sumber Daya)**
- **Pengertian:** Sumber daya komputasi penyedia dikumpulkan untuk melayani banyak pengguna menggunakan model *multi-tenant*, dengan sumber daya fisik dan virtual yang berbeda dialokasikan dan dialokasikan ulang secara dinamis sesuai permintaan pengguna.
- **Konsep Penting:** Pengguna umumnya tidak memiliki kendali atau pengetahuan atas lokasi pasti dari sumber daya yang disediakan, tetapi mungkin dapat menentukan lokasi pada tingkat abstraksi yang lebih tinggi (misalnya, negara bagian, provinsi, atau pusat data).
- **Contoh:** Server fisik Amazon Web Services di Singapura melayani ribuan pelanggan secara bersamaan, namun setiap pelanggan merasa memiliki sumber daya virtualnya sendiri.

**4. Rapid Elasticity (Elastisitas Cepat)**
- **Pengertian:** Kemampuan komputasi dapat dialokasikan dan dirilis secara elastis, dalam beberapa kasus secara otomatis, untuk skala masuk dan keluar dengan cepat sesuai permintaan.
- **Implikasi:** Bagi pengguna, kapasitas yang tersedia sering tampak tidak terbatas dan dapat digunakan dalam jumlah berapa pun kapan saja.
- **Contoh:** Platform streaming video seperti Netflix secara otomatis menambah ribuan server virtual pada malam hari ketika jumlah penonton meningkat, dan menguranginya kembali saat dini hari.

**5. Measured Service (Layanan Terukur)**
- **Pengertian:** Sistem cloud secara otomatis mengontrol dan mengoptimalkan penggunaan sumber daya dengan memanfaatkan kemampuan pengukuran pada tingkat abstraksi yang sesuai dengan jenis layanan.
- **Mekanisme:** Penggunaan sumber daya dapat dipantau, dikendalikan, dan dilaporkan, memberikan transparansi baik bagi penyedia maupun pengguna layanan.
- **Contoh:** Pengguna AWS dapat melihat dashboard yang menunjukkan secara detail berapa jam EC2 yang telah digunakan, berapa GB penyimpanan S3 yang terpakai, dan berapa biaya yang harus dibayarkan bulan ini.

### 1.3 Model Layanan Komputasi Awan (Service Models)

Dalam arsitektur komputasi awan, dikenal tiga model layanan utama yang membagi tanggung jawab antara penyedia dan pengguna.

**A. Infrastructure as a Service (IaaS)**
- **Pengertian:** Model layanan yang menyediakan infrastruktur komputasi dasar seperti kemampuan pemrosesan, penyimpanan, dan jaringan. Pengguna dapat menyebarkan dan menjalankan perangkat lunak apa pun, termasuk sistem operasi dan aplikasi.
- **Tanggung Jawab Pengguna:** Mengelola sistem operasi, penyimpanan, aplikasi yang digunakan, dan mungkin juga komponen jaringan tertentu.
- **Tanggung Jawab Penyedia:** Mengelola infrastruktur virtualisasi, server fisik, jaringan, dan penyimpanan.
- **Contoh:** Amazon EC2, Google Compute Engine, Microsoft Azure Virtual Machines.
- **Skenario Penggunaan:** Perusahaan yang ingin memiliki kendali penuh atas konfigurasi servernya tetapi tidak ingin membeli hardware fisik.

**B. Platform as a Service (PaaS)**
- **Pengertian:** Model layanan di mana pengguna dapat menyebarkan aplikasi yang dibuat menggunakan bahasa pemrograman, library, dan tools yang didukung oleh penyedia. Pengguna tidak mengelola infrastruktur dasar, tetapi memiliki kendali atas aplikasi yang disebarkan.
- **Tanggung Jawab Pengguna:** Hanya pada kode aplikasi dan konfigurasi data.
- **Tanggung Jawab Penyedia:** Semua infrastruktur, sistem operasi, middleware, dan runtime.
- **Contoh:** Google App Engine, Heroku, AWS Elastic Beanstalk.
- **Skenario Penggunaan:** Tim pengembang yang ingin fokus pada penulisan kode tanpa memusingkan provisioning server, patching sistem operasi, atau manajemen skala.

**C. Software as a Service (SaaS)**
- **Pengertian:** Model layanan di mana pengguna dapat menggunakan aplikasi penyedia yang berjalan di infrastruktur cloud. Aplikasi dapat diakses dari berbagai perangkat klien melalui antarmuka klien seperti web browser.
- **Tanggung Jawab Pengguna:** Hanya pada konfigurasi spesifik aplikasi dan data pengguna.
- **Tanggung Jawab Penyedia:** Seluruh tumpukan teknologi, termasuk infrastruktur, sistem operasi, aplikasi, dan keamanan.
- **Contoh:** Google Workspace (Gmail, Google Docs), Microsoft 365, Salesforce, Dropbox.
- **Skenario Penggunaan:** Perusahaan yang ingin menggunakan perangkat lunak siap pakai tanpa instalasi dan pemeliharaan.

### 1.4 Model Deployment (Model Penempatan)

Model deployment menjelaskan bagaimana infrastruktur cloud diorganisasikan berdasarkan kepemilikan, ukuran, dan akses.

**1. Public Cloud (Cloud Publik)**
- **Pengertian:** Infrastruktur cloud disediakan untuk penggunaan umum oleh publik. Cloud ini dimiliki, dikelola, dan dioperasikan oleh organisasi penyedia cloud (vendor).
- **Karakteristik:** Model *multi-tenant*, biaya lebih rendah, skalabilitas tak terbatas, dan tidak memerlukan investasi awal.
- **Contoh:** Amazon Web Services, Microsoft Azure, Google Cloud Platform.
- **Kelebihan:** Ekonomis, tidak perlu memelihara infrastruktur.
- **Kekurangan:** Kontrol terbatas, potensi masalah kepatuhan untuk industri tertentu.

**2. Private Cloud (Cloud Privat)**
- **Pengertian:** Infrastruktur cloud diprovisikan untuk penggunaan eksklusif oleh satu organisasi yang terdiri dari banyak pengguna. Cloud ini mungkin dimiliki, dikelola, dan dioperasikan oleh organisasi itu sendiri, pihak ketiga, atau kombinasi keduanya.
- **Karakteristik:** Infrastruktur *dedicated*, keamanan lebih tinggi, kontrol penuh, dapat berlokasi *on-premise* atau di fasilitas penyedia.
- **Contoh:** OpenStack yang diimplementasikan di pusat data perusahaan, VMware vSphere untuk enterprise.
- **Kelebihan:** Kontrol penuh, keamanan tinggi, cocok untuk data sensitif.
- **Kekurangan:** Biaya tinggi, tanggung jawab pemeliharaan penuh.

**3. Hybrid Cloud (Cloud Hibrida)**
- **Pengertian:** Komposisi dari dua atau lebih infrastruktur cloud yang berbeda (privat dan publik) yang tetap menjadi entitas unik tetapi terikat oleh teknologi terstandarisasi yang memungkinkan portabilitas data dan aplikasi.
- **Mekanisme:** Memungkinkan *cloud bursting*, di mana aplikasi berjalan di cloud privat tetapi "meledak" ke cloud publik saat permintaan memuncak.
- **Contoh:** Bank yang menyimpan data nasabah di cloud privat tetapi menggunakan cloud publik untuk aplikasi mobile banking saat traffic tinggi.
- **Kelebihan:** Fleksibilitas tinggi, optimalisasi biaya, keamanan untuk data sensitif.
- **Kekurangan:** Kompleksitas manajemen tinggi, integrasi memerlukan keahlian khusus.

**4. Community Cloud (Cloud Komunitas)**
- **Pengertian:** Infrastruktur cloud diprovisikan untuk penggunaan eksklusif oleh komunitas spesifik dari organisasi yang memiliki kepentingan bersama (misalnya, misi, persyaratan keamanan, kebijakan, atau pertimbangan kepatuhan).
- **Contoh:** Cloud untuk institusi pemerintahan, cloud untuk lembaga kesehatan yang harus mematuhi HIPAA, cloud untuk institusi pendidikan.
- **Kelebihan:** Berbagi biaya antar anggota komunitas, memenuhi kebutuhan kepatuhan spesifik industri.
- **Kekurangan:** Terbatas pada anggota komunitas, kompleksitas tata kelola.

---

## BAB 2: KEUNTUNGGAN MENGGUNAKAN KOMPUTASI AWAN

### 2.1 Keuntungan Strategis dan Operasional

**1. Transformasi Biaya (CAPEX ke OPEX)**
- **Pengertian:** Perubahan model pengeluaran dari *Capital Expenditure* (investasi modal di muka untuk perangkat keras) menjadi *Operational Expenditure* (biaya operasional berkelanjutan).
- **Implikasi:** Organisasi tidak perlu mengeluarkan jutaan rupiah untuk membeli server yang mungkin menganggur, cukup membayar bulanan sesuai pemakaian.
- **Contoh:** Startup tidak perlu membeli server fisik senilai Rp 200 juta, cukup berlangganan AWS dengan biaya Rp 5 juta per bulan sesuai traffic.

**2. Skalabilitas dan Elastisitas**
- **Pengertian:** Kemampuan untuk menambah atau mengurangi sumber daya secara otomatis sesuai fluktuasi beban kerja.
- **Skalabilitas Vertikal:** Menambah kapasitas server yang sama (misal: upgrade RAM).
- **Skalabilitas Horizontal:** Menambah jumlah server.
- **Contoh:** E-commerce seperti Tokopedia saat Harbolnas (Hari Belanja Online Nasional) dapat meningkatkan kapasitas server secara otomatis untuk menampung lonjakan traffic 10x lipat, kemudian menurunkannya kembali setelah periode promo berakhir.

**3. Akses Global dan Mobilitas**
- **Pengertian:** Data dan aplikasi dapat diakses dari mana saja di dunia selama terhubung internet.
- **Implikasi:** Mendukung kerja jarak jauh (*remote work*) dan kolaborasi global.
- **Contoh:** Tim pengembang yang tersebar di Jakarta, Bandung, dan Bali dapat bekerja pada repositori kode yang sama di GitHub atau AWS CodeCommit.

**4. Keandalan dan Ketersediaan Tinggi (High Availability)**
- **Pengertian:** Penyedia cloud menjamin tingkat ketersediaan layanan melalui *Service Level Agreement* (SLA) yang biasanya mencapai 99.9% hingga 99.99%.
- **Mekanisme:** Data direplikasi ke beberapa *Availability Zone* (pusat data terpisah) untuk menghindari titik kegagalan tunggal.
- **Contoh:** Amazon S3 dirancang untuk memberikan durability 99.999999999% (11 sembilan), artinya jika Anda menyimpan 10.000 file, kemungkinan kehilangan satu file dalam 10 juta tahun.

**5. Keamanan dan Kepatuhan**
- **Pengertian:** Penyedia cloud berinvestasi besar dalam keamanan fisik dan siber yang sulit ditandingi organisasi individual.
- **Aspek Keamanan:** Enkripsi data (saat transit dan saat istirahat), manajemen identitas dan akses (IAM), firewall, deteksi intrusi.
- **Sertifikasi:** Penyedia besar memiliki sertifikasi keamanan seperti ISO 27001, SOC, PCI DSS, HIPAA.
- **Catatan Penting:** Berlaku *Shared Responsibility Model* — penyedia mengamankan *infrastruktur cloud*, pengguna bertanggung jawab mengamankan *data di cloud*.

**6. Pemulihan Bencana (Disaster Recovery)**
- **Pengertian:** Kemampuan untuk memulihkan sistem dan data setelah terjadinya bencana (alam, kegagalan sistem, serangan siber).
- **Kelebihan Cloud:** Replikasi data antar wilayah geografis memungkinkan pemulihan cepat tanpa membangun pusat data cadangan yang mahal.
- **Contoh:** Ketika server lokal perusahaan di Jakarta terkena banjir, aplikasi dapat segera dialihkan ke server di Singapura dengan downtime minimal.

**7. Fokus pada Kompetensi Inti**
- **Pengertian:** Organisasi dapat mengalihkan sumber daya TI dari tugas "menjaga server tetap hidup" ke inovasi yang memberikan nilai bisnis langsung.
- **Implikasi:** Tim IT dapat fokus mengembangkan aplikasi yang membedakan perusahaan dari kompetitor, bukan menghabiskan waktu untuk patch keamanan server.

---

## BAB 3: PENGENALAN PLATFORM KOMPUTASI AWAN

### 3.1 Platform Cloud Utama (Hyperscale Cloud Providers)

**A. Amazon Web Services (AWS)**
- **Sejarah:** Diluncurkan tahun 2006, AWS adalah pelopor komersialisasi cloud dan saat ini pemimpin pasar dengan pangsa terbesar.
- **Infrastruktur:** Memiliki 30+ wilayah (*region*) dan 90+ zona ketersediaan (*availability zones*) secara global.
- **Layanan Unggulan:**
  - EC2 (Elastic Compute Cloud): Virtual server
  - S3 (Simple Storage Service): Object storage
  - RDS (Relational Database Service): Database terkelola
  - Lambda: Serverless computing
- **Cocok untuk:** Perusahaan rintisan hingga enterprise yang menginginkan layanan terlengkap.

**B. Microsoft Azure**
- **Sejarah:** Diluncurkan tahun 2010, Azure memanfaatkan dominasi Microsoft di pasar perangkat lunak enterprise.
- **Keunggulan Integrasi:** Integrasi sempurna dengan ekosistem Microsoft (Windows Server, Active Directory, SQL Server, .NET).
- **Layanan Unggulan:**
  - Azure Virtual Machines
  - Azure SQL Database
  - Azure Active Directory
  - Hybrid Cloud dengan Azure Arc
- **Cocok untuk:** Perusahaan yang sudah menggunakan infrastruktur Microsoft secara intensif.

**C. Google Cloud Platform (GCP)**
- **Sejarah:** Diluncurkan tahun 2008, memanfaatkan keahlian Google dalam infrastruktur berskala besar.
- **Keunggulan:** Keahlian dalam data analytics, machine learning, dan container.
- **Layanan Unggulan:**
  - Compute Engine
  - BigQuery (data warehouse)
  - Kubernetes Engine (GKE)
  - TensorFlow dan AI Platform
- **Cocok untuk:** Perusahaan dengan kebutuhan analitik data besar dan machine learning intensif.

**D. Platform Lainnya**
- **Alibaba Cloud:** Dominan di pasar China dan Asia.
- **IBM Cloud:** Fokus pada hybrid cloud dan enterprise.
- **Oracle Cloud:** Spesialisasi pada database dan aplikasi enterprise.

### 3.2 Perbandingan Komprehensif Platform Cloud

| Aspek | AWS | Azure | GCP |
|-------|-----|-------|-----|
| **Pangsa Pasar (Q1 2024)** | 31% | 25% | 11% |
| **Jumlah Region** | 30+ | 60+ (termasuk announced) | 35+ |
| **Kekuatan Utama** | Layanan terlengkap, maturitas tinggi | Integrasi Microsoft, hybrid | Data analytics, AI/ML, container |
| **Kemudahan Penggunaan** | Kompleks, kurva belajar curam | Mudah bagi pengguna Microsoft | Antarmuka sederhana, dokumentasi baik |
| **Harga** | Kompetitif, berbagai opsi | Kompetitif, diskon untuk pengguna existing | Sering lebih murah untuk workload spesifik |

### 3.3 Konsep Region dan Availability Zone

**Pengertian Region:**
Region adalah lokasi geografis yang terdiri dari satu atau lebih *Availability Zones*. Setiap region independen secara fisik dan hukum.

**Pengertian Availability Zone (AZ):**
AZ adalah satu atau lebih pusat data yang terpisah secara fisik dalam satu region, masing-masing memiliki daya, pendingin, dan keamanan independen.

**Tujuan:**
- **Redundansi:** Jika satu AZ mengalami bencana, aplikasi tetap berjalan di AZ lain.
- **Latensi Rendah:** Pengguna mengakses region terdekat untuk mengurangi waktu respons.
- **Kepatuhan:** Data dapat disimpan di region tertentu untuk memenuhi regulasi lokal.

**Contoh:**
- Region Asia Pasifik (Singapura) memiliki 3 Availability Zones (AZ-a, AZ-b, AZ-c).
- Aplikasi dapat di-deploy di ketiga AZ untuk menjamin ketersediaan meskipun satu pusat data terbakar.

---

## BAB 4: PENGENALAN PROSES PERPINDAHAN KE TEKNOLOGI KOMPUTASI AWAN (CLOUD MIGRATION)

### 4.1 Definisi dan Ruang Lingkup Cloud Migration

**Pengertian Formal:**
Cloud migration adalah proses memindahkan sebagian atau seluruh aset digital organisasi—termasuk data, aplikasi, beban kerja, dan proses TI—dari infrastruktur on-premise (lokal) ke infrastruktur berbasis cloud, atau dari satu cloud ke cloud lainnya.

**Ruang Lingkup:**
Migrasi bukan sekadar "memindahkan file", tetapi meliputi transformasi arsitektur aplikasi, perubahan proses operasional, adaptasi budaya kerja, dan optimalisasi biaya.

### 4.2 Tahapan Komprehensif Cloud Migration

**Fase 1: Assessment dan Discovery (Penilaian dan Penemuan)**
- **Tujuan:** Memahami landscape TI saat ini secara menyeluruh.
- **Aktivitas:**
  - Inventarisasi semua aset: server, aplikasi, database, dependensi.
  - Identifikasi ketergantungan antar aplikasi.
  - Analisis biaya TCO (Total Cost of Ownership) saat ini.
  - Penilaian kesiapan organisasi (skill, budaya, proses).
- **Tools:** AWS Application Discovery Service, Azure Migrate.
- **Output:** Daftar inventaris lengkap dan rekomendasi awal.

**Fase 2: Planning dan Strategi (Perencanaan)**
- **Tujuan:** Menentukan pendekatan migrasi untuk setiap aplikasi.
- **Aktivitas:**
  - Memilih model deployment (publik, privat, hibrida).
  - Memilih penyedia cloud berdasarkan kebutuhan.
  - Menentukan timeline dan prioritas migrasi.
  - Merancang arsitektur target di cloud.
- **Output:** Cloud Adoption Framework, roadmap migrasi, RACI matrix.

**Fase 3: Proof of Concept (POC) dan Pilot**
- **Tujuan:** Memvalidasi asumsi dan menguji proses dengan aplikasi non-kritis.
- **Aktivitas:**
  - Memilih 1-2 aplikasi sederhana untuk migrasi uji coba.
  - Mengukur kinerja setelah migrasi.
  - Mengidentifikasi hambatan teknis dan operasional.
  - Mendokumentasikan pelajaran untuk migrasi skala penuh.
- **Output:** Laporan hasil POC, SOP migrasi yang telah direvisi.

**Fase 4: Migration Execution (Eksekusi Migrasi)**
- **Tujuan:** Melakukan migrasi aktual sesuai prioritas dan strategi.
- **Aktivitas:**
  - Migrasi data (dengan metode offline atau online).
  - Migrasi aplikasi sesuai strategi yang dipilih.
  - Pengujian fungsional dan non-fungsional.
  - Cutover (pengalihan traffic dari sistem lama ke baru).
- **Pendekatan:** Dilakukan dalam gelombang (wave) untuk mengurangi risiko.

**Fase 5: Optimization dan Operasi Berkelanjutan**
- **Tujuan:** Memastikan lingkungan cloud berjalan optimal pasca-migrasi.
- **Aktivitas:**
  - Monitoring performa dan biaya secara real-time.
  - Right-sizing: menyesuaikan kapasitas dengan kebutuhan aktual.
  - Implementasi auto-scaling untuk efisiensi.
  - Penerapan FinOps (manajemen biaya cloud).
  - Continuous improvement arsitektur.
- **Tools:** AWS CloudWatch, Azure Monitor, Google Cloud Operations.

### 4.3 Strategi Migrasi: Model 6R

**1. Rehost (Lift and Shift)**
- **Pengertian:** Memindahkan aplikasi ke cloud tanpa perubahan apa pun.
- **Keuntungan:** Cepat, risiko rendah, biaya migrasi minimal.
- **Kekurangan:** Tidak mengoptimalkan manfaat cloud.
- **Contoh:** Aplikasi ASP.NET berjalan di Windows Server dipindahkan ke AWS EC2 dengan konfigurasi identik.

**2. Replatform (Lift, Tinker, and Shift)**
- **Pengertian:** Melakukan beberapa optimasi cloud tanpa mengubah arsitektur inti aplikasi.
- **Keuntungan:** Mulai mendapat manfaat cloud tanpa perubahan besar.
- **Contoh:** Memindahkan database dari SQL Server on-premise ke Amazon RDS (managed service) tanpa mengubah kode aplikasi.

**3. Refactor / Re-architect**
- **Pengertian:** Menulis ulang atau memodifikasi aplikasi secara signifikan untuk memanfaatkan fitur cloud-native.
- **Keuntungan:** Manfaat maksimal dari cloud (skalabilitas, resiliency, efisiensi biaya).
- **Kekurangan:** Mahal, memakan waktu, risiko tinggi.
- **Contoh:** Memecah monolitik aplikasi menjadi microservices yang berjalan di container dengan Kubernetes.

**4. Repurchase**
- **Pengertian:** Mengganti aplikasi lama dengan produk baru yang berbeda, biasanya SaaS.
- **Keuntungan:** Mengurangi biaya pemeliharaan, fitur lebih modern.
- **Contoh:** Mengganti sistem CRM internal dengan Salesforce.

**5. Retire**
- **Pengertian:** Mematikan aplikasi yang tidak lagi memberikan nilai bisnis.
- **Keuntungan:** Menghemat biaya lisensi dan pemeliharaan.
- **Catatan:** Bukan migrasi dalam arti sempit, tetapi bagian dari portofolio rationalization.

**6. Retain**
- **Pengertian:** Mempertahankan aplikasi di lingkungan on-premise untuk sementara waktu.
- **Alasan:** Aplikasi terlalu kompleks untuk migrasi, regulasi melarang, atau akan diganti dalam waktu dekat.
- **Strategi:** Revisit di fase berikutnya.

### 4.4 Tantangan dan Risiko dalam Cloud Migration

**1. Keamanan dan Kepatuhan**
- **Tantangan:** Memastikan data sensitif tetap aman selama transfer dan setelah di cloud.
- **Mitigasi:** Enkripsi end-to-end, due diligence pada kepatuhan penyedia.

**2. Vendor Lock-in**
- **Tantangan:** Ketergantungan pada layanan spesifik penyebab sulitnya berpindah penyedia.
- **Mitigasi:** Menggunakan arsitektur terbuka, container, dan menghindari layanan proprietary jika memungkinkan.

**3. Manajemen Biaya**
- **Tantangan:** Biaya cloud tak terduga akibat provisioning berlebih atau kurang monitoring.
- **Mitigasi:** Implementasi FinOps, tag resources, monitoring biaya real-time.

**4. Kesenjangan Keterampilan**
- **Tantangan:** Tim TI mungkin tidak memiliki keterampilan cloud yang diperlukan.
- **Mitigasi:** Pelatihan, hiring, atau menggunakan konsultan/managed service provider.

**5. Downtime dan Gangguan Layanan**
- **Tantangan:** Proses migrasi dapat menyebabkan downtime jika tidak direncanakan.
- **Mitigasi:** Strategi cutover bertahap, migrasi blue-green deployment.

### 4.5 Studi Kasus: Migrasi E-commerce ke Cloud

**Latar Belakang:**
PT. Toko Online Indonesia, perusahaan e-commerce menengah, memiliki infrastruktur on-premise: 20 server fisik, 5 database server, dan storage 50TB.

**Tantangan:**
- Server sering overload saat flash sale.
- Biaya pemeliharaan tinggi (listrik, pendingin, teknisi).
- Waktu recovery lambat saat server mati.
- Ekspansi bisnis ke luar negeri terhambat latensi.

**Proses Migrasi:**
1. **Assessment:** Mengidentifikasi 25 aplikasi dengan dependensi.
2. **Strategi:**
   - Aplikasi web → Rehost ke EC2
   - Database → Replatform ke RDS
   - Gambar produk → S3 + CloudFront
   - Aplikasi legacy → Retain sementara
3. **Pilot:** Migrasi 2 aplikasi non-kritis dalam 2 minggu.
4. **Eksekusi:** Migrasi 4 gelombang selama 3 bulan.
5. **Optimasi:** Setelah migrasi, implementasi auto-scaling untuk flash sale.

**Hasil:**
- Biaya turun 35% dalam 1 tahun.
- Waktu loading halaman turun dari 5 detik menjadi 1,2 detik.
- Dapat menangani traffic 10x lipat tanpa masalah.
- Tim IT fokus pada pengembangan fitur baru, bukan memelihara server.



## DAFTAR PUSTAKA

1. Mell, P., & Grance, T. (2011). The NIST Definition of Cloud Computing. National Institute of Standards and Technology, Special Publication 800-145.

2. Amazon Web Services. (2024). AWS Well-Architected Framework. AWS Documentation.

3. Microsoft Azure. (2024). Microsoft Cloud Adoption Framework for Azure. Microsoft Docs.

4. Google Cloud. (2024). Google Cloud Architecture Framework. Google Cloud Documentation.

5. Gartner. (2023). Magic Quadrant for Cloud Infrastructure and Platform Services. Gartner Research.
