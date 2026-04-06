

#  HIERARKI MEMORI DAN KARAKTERISTIKNYA

## 1. Pendahuluan

Memori komputer merupakan salah satu komponen terpenting dalam sistem komputer. Tidak ada satu teknologi memori pun yang optimal dalam memenuhi semua kebutuhan sistem komputer. Oleh karena itu, sistem komputer modern dilengkapi dengan **hierarki memori** (*memory hierarchy*), yaitu susunan beberapa tingkat (level) memori dengan karakteristik yang berbeda-beda.

---

## 2. Karakteristik Sistem Memori

Untuk memahami hierarki memori, kita perlu memahami karakteristik dasar dari setiap sistem memori. Berikut adalah karakteristik kuncinya:

### 2.1 Lokasi (*Location*)
- **Memori Internal**: Berada di dalam sistem komputer dan langsung diakses oleh prosesor. Contoh: register CPU, cache, memori utama (RAM).
- **Memori Eksternal**: Berada di luar sistem komputer, diakses melalui I/O. Contoh: hard disk, SSD, optical disk, magnetic tape.

### 2.2 Kapasitas (*Capacity*)
- Dinyatakan dalam jumlah **byte** (1 byte = 8 bit) atau **word** (ukuran word bervariasi, misal 16, 32, atau 64 bit).
- Semakin ke bawah hierarki, kapasitas semakin besar.

### 2.3 Unit Transfer (*Unit of Transfer*)
- Jumlah bit yang dibaca atau ditulis dari/ke memori dalam satu kali akses.
- Untuk memori internal, unit transfer biasanya sama dengan lebar jalur data (*data bus*).
- Untuk memori eksternal, unit transfer disebut **blok** (lebih besar dari word).

### 2.4 Metode Akses (*Access Method*)

| Metode Akses | Deskripsi | Contoh | Karakteristik |
|--------------|-----------|--------|---------------|
| **Sekuensial** | Akses harus dilakukan dalam urutan linear tertentu | Magnetic tape | Waktu akses sangat bervariasi |
| **Langsung (*Direct*)** | Memiliki mekanisme baca-tulis bersama, akses dengan mencapai area umum lalu mencari | Disk | Waktu akses bervariasi |
| **Akses Acak (*Random*)** | Setiap lokasi memiliki mekanisme pengalamatan unik | RAM, Cache | Waktu akses konstan |
| **Asosiatif** | Data ditemukan berdasarkan isinya, bukan alamatnya | Cache asosiatif | Waktu akses konstan |

### 2.5 Kinerja (*Performance*)

Tiga parameter kinerja utama:

1.  **Waktu Akses (*Access Time*)**:
    - Untuk RAM: waktu dari alamat diberikan hingga data tersedia.
    - Untuk non-RAM: waktu untuk memposisikan mekanisme baca-tulis.

2.  **Waktu Siklus Memori (*Memory Cycle Time*)**:
    - Waktu akses + waktu tambahan sebelum akses kedua dapat dimulai.
    - Berkaitan dengan bus sistem, bukan prosesor.

3.  **Laju Transfer (*Transfer Rate*)**:
    - Kecepatan data dipindahkan masuk/keluar unit memori.
    - Untuk RAM: \( \text{Laju Transfer} = \frac{1}{\text{Waktu Siklus}} \)

### 2.6 Tipe Fisik (*Physical Type*)
- **Semikonduktor**: Digunakan untuk memori utama dan cache (cepat, namun volatil).
- **Magnetik**: Digunakan untuk disk dan tape (non-volatil, kapasitas besar).
- **Optik**: CD, DVD, Blu-ray (non-volatil, tahan lama).
- **Magneto-optik**: Kombinasi teknologi magnetik dan optik.

### 2.7 Karakteristik Fisik
- **Volatil**: Data hilang jika daya listrik dimatikan. Contoh: RAM, Cache.
- **Non-volatil**: Data tetap tersimpan meskipun daya dimatikan. Contoh: ROM, hard disk, flash disk.
- **Dapat Dihapus (*Erasable*)**: Data dapat diubah. Contoh: RAM, EEPROM.
- **Tidak Dapat Dihapus (*Non-erasable*)**: Data bersifat permanen. Contoh: ROM (mask ROM).

---

## 3. Hierarki Memori (*Memory Hierarchy*)

### 3.1 Konsep Dasar

Desainer sistem dihadapkan pada tiga pertanyaan mendasar:
1.  **Berapa banyak?** (Kapasitas)
2.  **Seberapa cepat?** (Kecepatan akses)
3.  **Semahal apa?** (Biaya)

Tidak ada teknologi tunggal yang dapat memenuhi ketiganya secara optimal karena terdapat hubungan **trade-off**:
- Semakin cepat waktu akses → semakin mahal biaya per bit.
- Semakin besar kapasitas → semakin murah biaya per bit.
- Semakin besar kapasitas → semakin lambat waktu akses.

### 3.2 Struktur Hierarki Memori

Hierarki memori disusun dari tingkat teratas (paling dekat dengan prosesor) hingga terbawah (paling jauh), dengan karakteristik:

| Tingkat | Teknologi | Kapasitas | Kecepatan | Biaya/bit | Frekuensi Akses |
|---------|-----------|-----------|-----------|-----------|-----------------|
| **Register CPU** | Semikonduktor | Paling kecil | Paling cepat | Paling mahal | Paling sering |
| **Cache L1** | SRAM | Kecil | Sangat cepat | Mahal | Sangat sering |
| **Cache L2** | SRAM | Sedang | Cepat | Cukup mahal | Sering |
| **Cache L3** | SRAM | Lebih besar | Agak lambat | Lebih murah | Kurang sering |
| **Memori Utama** | DRAM | Besar | Lambat | Murah | Jarang |
| **Disk (Virtual Memory)** | Magnetik | Sangat besar | Sangat lambat | Sangat murah | Sangat jarang |
| **Tape/Backup** | Magnetik/Optik | Terbesar | Terlambat | Termurah | Paling jarang |

### 3.3 Prinsip Locality of Reference

Keberhasilan hierarki memori bergantung pada prinsip **Locality of Reference** (Dennings, 1968):

> Selama eksekusi program, referensi memori oleh prosesor cenderung mengelompok (*cluster*).

**Dua jenis locality:**

1.  **Temporal Locality**:
    - Data/instruksi yang baru saja diakses kemungkinan akan diakses lagi dalam waktu dekat.
    - Contoh: variabel counter dalam loop, instruksi dalam loop.

2.  **Spatial Locality**:
    - Ketika suatu lokasi diakses, lokasi di sekitarnya (alamat berdekatan) kemungkinan juga akan diakses.
    - Contoh: pemrosesan elemen array secara berurutan.

### 3.4 Perhitungan Kinerja Hierarki Dua Tingkat

Untuk hierarki dengan dua tingkat memori (M1 di atas, M2 di bawah):

**Parameter:**
- \( T_1 \) = waktu akses M1
- \( T_2 \) = waktu akses M2
- \( H \) = *hit ratio* (fraksi akses yang ditemukan di M1)

**Rumus waktu akses rata-rata:**
\[
T_s = T_1 + (1-H) \times T_2
\]

**Contoh perhitungan:**
- \( T_1 = 0,01 \mu s \)
- \( T_2 = 0,1 \mu s \)
- \( H = 0,95 \)

\[
T_s = 0,01 + (0,05 \times 0,1) = 0,01 + 0,005 = 0,015 \mu s
\]

Dengan hit ratio 95%, waktu akses rata-rata (0,015 μs) jauh lebih dekat ke \( T_1 \) (0,01 μs) daripada ke \( T_2 \) (0,1 μs).

---

## 4. Cache Memory

### 4.1 Prinsip Kerja Cache

Cache memory adalah memori berkecepatan tinggi berkapasitas kecil yang menyimpan salinan sebagian data dari memori utama.

**Mekanisme operasi baca (Gambar 4.5):**
1. Prosesor menghasilkan alamat baca (RA)
2. Cek apakah data di cache:
   - **Hit**: Data dikirim ke prosesor (tanpa akses memori utama)
   - **Miss**: Blok data diambil dari memori utama, disalin ke cache, lalu dikirim ke prosesor

### 4.2 Elemen Desain Cache

| Elemen Desain | Pilihan | Keterangan |
|---------------|---------|-------------|
| **Alamat Cache** | Logical (virtual) / Physical | Logical lebih cepat, Physical lebih aman |
| **Ukuran Cache** | 4 KB - 32 MB | Trade-off: kecil cepat, besar hit ratio tinggi |
| **Fungsi Pemetaan** | Direct / Associative / Set-Associative | Menentukan mapping blok ke line |
| **Algoritma Penggantian** | LRU, FIFO, LFU, Random | Mengatur line mana yang diganti |
| **Kebijakan Penulisan** | Write Through / Write Back | Mengatur update ke memori utama |
| **Ukuran Blok** | 8 - 128 byte | Trade-off: kecil vs besar |
| **Jumlah Level** | Single / Multi-level (L1, L2, L3) | Meningkatkan performa |
| **Organisasi** | Unified / Split (I & D cache) | Split untuk superskalar |

### 4.3 Fungsi Pemetaan Cache

#### a) Direct Mapping
- Setiap blok memori utama hanya dapat dipetakan ke **satu line cache** tertentu.
- \( i = j \mod m \)
- Alamat: **Tag** | **Line** | **Word**
- Kelebihan: Sederhana, murah
- Kekurangan: Tidak fleksibel, rawan thrashing

#### b) Associative Mapping
- Setiap blok dapat dipetakan ke **sembarang line** cache.
- Alamat: **Tag** | **Word**
- Kelebihan: Fleksibel, hit ratio tinggi
- Kekurangan: Rangkaian kompleks, mahal

#### c) Set-Associative Mapping
- Kompromi antara direct dan associative.
- Cache dibagi menjadi beberapa **set**, setiap set memiliki beberapa **line**.
- \( i = j \mod v \) (v = jumlah set)
- Alamat: **Tag** | **Set** | **Word**
- Paling umum digunakan (2-way, 4-way, 8-way)

### 4.4 Kebijakan Penulisan (Write Policy)

#### Write Through
- Data ditulis ke **cache DAN memori utama** secara simultan.
- Kelebihan: Memori utama selalu valid
- Kekurangan: Lalu lintas bus tinggi

#### Write Back
- Data ditulis **hanya ke cache**, *dirty bit* diset.
- Data ke memori utama ditulis saat line akan digantikan.
- Kelebihan: Lalu lintas bus rendah
- Kekurangan: Memori utama tidak selalu valid

### 4.5 Multi-level Cache

- **L1 Cache**: On-chip, kecepatan CPU, ukuran kecil (8-64 KB)
- **L2 Cache**: Bisa on/off-chip, lebih lambat dari L1, ukuran lebih besar (256 KB - 1 MB)
- **L3 Cache**: On-chip pada prosesor modern, ukuran besar (2-32 MB)

**Tujuan**: Menutup celah kecepatan antara prosesor dan memori utama.

### 4.6 Split vs Unified Cache

| Unified Cache | Split Cache |
|---------------|-------------|
| Satu cache untuk data dan instruksi | Cache terpisah untuk data (D-cache) dan instruksi (I-cache) |
| Hit ratio lebih tinggi (balancing otomatis) | Menghilangkan konflik akses |
| Desain lebih sederhana | Penting untuk superskalar dan pipelining |

---

## 5. Ringkasan

1.  **Hierarki memori** adalah solusi untuk mengatasi trade-off antara kecepatan, kapasitas, dan biaya.

2.  Karakteristik memori meliputi: lokasi, kapasitas, unit transfer, metode akses, kinerja, tipe fisik, dan karakteristik fisik.

3.  **Prinsip locality of reference** (temporal dan spatial) adalah kunci keberhasilan hierarki memori.

4.  **Cache memory** menggunakan prinsip yang sama dengan hierarki: sebagian kecil data yang paling sering diakses disimpan di memori cepat.

5.  Elemen desain cache yang penting: fungsi pemetaan, kebijakan penulisan, ukuran blok, dan jumlah level cache.

6.  Organisasi **set-associative** dengan kebijakan **write back** adalah yang paling umum digunakan pada prosesor modern.


---

## KOMPONEN HIERARKI MEMORI

### 1. REGISTER CPU

**Apa itu?**
Register adalah lokasi memori internal dengan kecepatan tertinggi yang berada langsung di dalam prosesor (CPU). Jumlahnya sangat terbatas (biasanya puluhan hingga ratusan).

**Untuk apa?**
- Menyimpan data yang sedang diproses oleh ALU (Arithmetic Logic Unit).
- Menyimpan alamat instruksi yang akan dieksekusi (Program Counter/PC).
- Menyimpan hasil sementara dari operasi aritmatika dan logika.
- Menyimpan status dan kondisi prosesor (flag/condition code).

**Karakteristik:**
| Properti | Nilai |
|----------|-------|
| Kecepatan | Paling cepat (1 siklus CPU) |
| Kapasitas | Paling kecil (biasanya 16-256 byte) |
| Biaya per bit | Paling mahal |
| Teknologi | Semikonduktor (SRAM) |
| Volatilitas | Volatil |


### 2. CACHE MEMORY (L1, L2, L3)

Cache adalah memori perantara antara prosesor yang sangat cepat dan memori utama yang relatif lambat. Tujuannya adalah untuk menyimpan salinan data yang paling sering diakses agar prosesor tidak perlu terus-menerus mengakses memori utama yang lambat.

#### 2.1 CACHE L1 (Level 1)

**Apa itu?**
Cache L1 adalah cache tingkat pertama yang paling dekat dengan inti prosesor (core). Biasanya diimplementasikan *on-chip* (berada dalam chip prosesor yang sama).

**Untuk apa?**
- Menyimpan instruksi dan data yang paling kritis dan paling sering diakses.
- Meminimalkan waktu tunggu prosesor karena akses ke L1 hanya membutuhkan 1-3 siklus clock.
- Pada prosesor modern, L1 biasanya **di-split** menjadi dua:
  - **L1 Instruction Cache (I-cache)**: Khusus menyimpan instruksi program.
  - **L1 Data Cache (D-cache)**: Khusus menyimpan data yang diolah.

**Mengapa dipisah (split)?**
- Menghilangkan konflik akses antara unit *fetch* instruksi dan unit eksekusi data.
- Sangat penting untuk prosesor **superskalar** dan **pipelining** yang melakukan banyak operasi paralel.
- Memungkinkan prosesor mengambil instruksi dan data secara bersamaan.

**Karakteristik:**
| Properti | Nilai |
|----------|-------|
| Kecepatan | 1-3 siklus CPU (paling cepat di antara cache) |
| Kapasitas | Kecil (biasanya 16-64 KB per core) |
| Teknologi | SRAM (Static RAM) |
| Lokasi | On-chip |


#### 2.2 CACHE L2 (Level 2)

**Apa itu?**
Cache L2 adalah cache tingkat kedua yang melayani cache L1. Dulu berada *off-chip* (terpisah dari prosesor), tetapi sekarang sebagian besar prosesor modern mengintegrasikannya *on-chip*.

**Untuk apa?**
- Menampung data yang tidak muat atau tidak cukup sering diakses untuk berada di L1.
- Menjadi "jaring pengaman" ketika terjadi *cache miss* di L1. Jika data tidak ada di L1, prosesor akan mencarinya di L2.
- Mengurangi kebutuhan akses ke memori utama yang sangat lambat.

**Karakteristik:**
| Properti | Nilai |
|----------|-------|
| Kecepatan | 5-15 siklus CPU (lebih lambat dari L1) |
| Kapasitas | Lebih besar (biasanya 256 KB - 8 MB per core) |
| Teknologi | SRAM |
| Lokasi | Umumnya on-chip pada prosesor modern |


#### 2.3 CACHE L3 (Level 3)

**Apa itu?**
Cache L3 adalah cache tingkat ketiga yang melayani cache L2. Ini adalah level terakhir sebelum prosesor harus mengakses memori utama (DRAM).

**Untuk apa?**
- Menyediakan kapasitas cache yang sangat besar untuk menangani *working set* aplikasi modern yang sangat besar.
- Menjadi *shared cache* yang dapat diakses oleh semua core dalam prosesor multicore, memungkinkan berbagi data antar core secara efisien.
- Mengurangi frekuensi akses ke memori utama DRAM yang berbiaya mahal dalam hal waktu (latency) dan energi.

**Karakteristik:**
| Properti | Nilai |
|----------|-------|
| Kecepatan | 20-40 siklus CPU |
| Kapasitas | Besar (biasanya 4-32 MB, shared antar core) |
| Teknologi | SRAM |
| Lokasi | On-chip |

**Contoh dari PDF (Tabel 4.3 dan 18.1):**
- IBM POWER5: L3 cache 36 MB
- Intel Core i7: L3 cache 8 MB (shared)
- IBM z10 (mainframe): L3 cache 24-48 MB


### 3. MEMORI UTAMA (MAIN MEMORY)

**Apa itu?**
Memori utama adalah tempat penyimpanan utama program dan data yang sedang dieksekusi oleh prosesor. Sering disebut sebagai RAM (Random Access Memory).

**Untuk apa?**
- Menyimpan kode program (instruksi) yang akan dieksekusi.
- Menyimpan data yang sedang diolah.
- Menjadi tempat berbagi (shared memory) antar proses dalam sistem operasi.

**Karakteristik:**
| Properti | Nilai |
|----------|-------|
| Kecepatan | 50-100 ns (ratusan siklus CPU) |
| Kapasitas | Besar (biasanya 4-256 GB) |
| Biaya per bit | Murah |
| Teknologi | DRAM (Dynamic RAM) |
| Volatilitas | Volatil (hilang jika listrik mati) |


### 4. MEMORI EKSTERNAL (EXTERNAL MEMORY)

#### 4.1 MAGNETIC DISK (HARD DISK)

**Apa itu?**
Piringan magnetik yang berputar dengan lapisan magnetik untuk menyimpan data secara permanen.

**Untuk apa?**
- Menyimpan sistem operasi, program aplikasi, dan file pengguna.
- Digunakan sebagai **virtual memory** (memori virtual) untuk memperluas ruang alamat memori utama.
- Sebagai *secondary storage* (penyimpanan sekunder).

**Karakteristik:**
| Properti | Nilai |
|----------|-------|
| Kecepatan | Sangat lambat (ms, jutaan siklus CPU) |
| Kapasitas | Sangat besar (500 GB - 20 TB) |
| Biaya per bit | Sangat murah |
| Teknologi | Magnetik |
| Volatilitas | Non-volatil |

#### 4.2 SOLID STATE DRIVE (SSD) - CATATAN TAMBAHAN

Meskipun tidak disebutkan secara eksplisit dalam bagian PDF yang diberikan (karena buku ini terbit tahun 2010, SSD belum dominan), SSD sekarang menjadi bagian penting dari hierarki memori. SSD menggunakan teknologi flash memory (semikonduktor) dan memiliki kecepatan yang jauh melampaui hard disk magnetik, meskipun masih lebih lambat dari DRAM.


## RINGKASAN FUNGSI SETIAP TINGKATAN

| Tingkatan | Fungsi Utama | Kecepatan Relatif |
|-----------|--------------|-------------------|
| **Register** | Menyimpan data yang sedang diproses ALU | 1x (paling cepat) |
| **L1 Cache** | Menyimpan instruksi & data paling kritis untuk core tertentu | ~3x lebih lambat dari register |
| **L2 Cache** | Menampung data yang tidak muat di L1, mengurangi akses ke L3/memori | ~10x lebih lambat dari L1 |
| **L3 Cache** | Cache bersama untuk semua core, kapasitas besar | ~2x lebih lambat dari L2 |
| **Main Memory (DRAM)** | Menyimpan program dan data yang sedang berjalan | ~50-100x lebih lambat dari L1 |
| **Disk (SSD/HDD)** | Penyimpanan permanen program, data, dan virtual memory | >10.000x lebih lambat dari L1 |

---

## MENGAPA TIDAK LANGSUNG PAKAI REGISTER SAJA?

**Pertanyaan yang sering muncul:** "Kalau register itu paling cepat, kenapa tidak semua memori dibuat dalam bentuk register saja?"

**Jawaban:** Karena **biaya**. Register menggunakan teknologi SRAM dengan kompleksitas sirkuit yang tinggi. Biaya per bit register bisa **ratusan kali** lebih mahal daripada DRAM, dan **jutaan kali** lebih mahal daripada hard disk.

Hierarki memori adalah solusi cerdas untuk mendapatkan **ilusi memori yang besar, murah, dan cepat**. Dengan prinsip *locality*, data yang paling sering diakses disimpan di tingkat atas yang cepat, sementara data yang jarang diakses disimpan di tingkat bawah yang murah.