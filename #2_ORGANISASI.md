

### Komponen Komputer

Desain komputer saat ini didasarkan pada konsep yang dikembangkan oleh John von Neumann (Institute for Advanced Studies, Princeton).  
Arsitektur von Neumann didasarkan pada tiga konsep kunci:

- Data dan instruksi disimpan dalam satu *read-write memory*.
- Isi dari memori dapat dialamatkan berdasarkan lokasi, tanpa memperhatikan jenis data yang ada.
- Eksekusi terjadi dengan cara sekuensial (kecuali secara eksplisit dimodifikasi) dari satu instruksi ke instruksi berikutnya.

**Hardwired Program**  
Satu set kecil komponen logika dasar yang digabungkan dengan cara tertentu untuk menyimpan data biner dan melakukan operasi aritmatika dan logika pada data.  
Jika ada perhitungan tertentu yang harus dilakukan, konfigurasi komponen logika yang dirancang khusus untuk perhitungan tersebut dapat dibangun.  
Kita dapat membayangkan proses menghubungkan berbagai komponen dalam konfigurasi yang diinginkan sebagai bentuk pemrograman.  
"Program" yang dihasilkan dalam bentuk perangkat keras/*hardware* diistilahkan dengan *Hardwired Program*.

---

### Pendekatan Hardware dan Software

Misalkan kita membangun sebuah konstruksi fungsi aritmatika dan logika tujuan umum (*general-purpose*). Perangkat keras ini akan melakukan berbagai fungsi pemrosesan data tergantung pada sinyal kontrol yang diterapkan ke perangkat keras tersebut.

- Kasus yang terjadi pada perangkat keras yang dikustomisasi, sistem menerima data dan menghasilkan hasil (Gambar a).
- Dengan perangkat keras tujuan umum (*general-purpose*), sistem menerima data dan sinyal kontrol dan menghasilkan hasil. Jadi, tidak diperlukan *rewiring* program perangkat keras untuk masing-masing program baru, *programmer* hanya menyediakan satu set sinyal kontrol baru.

**Bagaimana sinyal kontrol harus disediakan?**  
Seluruh program merupakan urutan langkah. Pada setiap langkah, beberapa operasi aritmatika atau operasi logika dilakukan pada beberapa data. Untuk setiap langkah, diperlukan satu set sinyal kontrol baru.  
Bayangkan bahwa setiap sinyal kontrol memungkinkan memiliki kode unik, kemudian tambahkan ke dalam perangkat keras tujuan umum (*general-purpose*) sebuah segmen yang dapat menerima kode tersebut dan menghasilkan sinyal kontrol (Gambar b).

**Software**  
- Sebuah urutan kode atau instruksi.
- Bagian dari perangkat keras menafsirkan setiap instruksi dan menghasilkan sinyal kontrol.
- Memberikan urutan kode yang baru untuk setiap program baru, bukannya *rewiring* perangkat keras.

**Komponen utama:**  
- **CPU**  
  - *Interpreter instruksi*  
  - Modul yang menyediakan fungsi aritmatika dan logika  
- **I/O Components**  
  - *Modul input*: Komponen dasar untuk menerima data dan instruksi dan mengubahnya menjadi bentuk sinyal yang digunakan oleh sistem.  
  - *Modul Output*: Menampilkan hasil.

Sebuah program tidak selalu dijalankan secara berurutan; mungkin melompat-lompat (misalnya, instruksi IAS *jump*).  
Demikian pula, operasi pada data mungkin membutuhkan akses ke lebih dari satu elemen pada suatu waktu dalam urutan yang telah ditentukan. Jadi, harus ada tempat untuk menyimpan sementara baik instruksi dan data.

CPU melakukan pertukaran data dengan memori utama umumnya menggunakan dua register internal (dalam CPU): **MAR** dan **MBR**.  
Sedangkan untuk pertukaran data dengan modul I/O menggunakan register: **I/OAR**, **I/OBR**.

- **Memory Address Register (MAR)** : Menentukan alamat pada memori untuk dibaca atau ditulis selanjutnya.
- **I/O Address Register (I/OAR)** : Menentukan perangkat I/O tertentu.
- **Memory Buffer Register (MBR)** : Berisi data yang akan ditulis ke dalam memori atau menerima data yang dibaca dari memori.
- **I/O Buffer Register (I/OBR)** : Digunakan untuk pertukaran data antara modul I/O dan CPU.

Modul memori terdiri dari sekumpulan lokasi, yang ditentukan dengan nomor alamat secara berurutan.  
Setiap lokasi berisi bilangan biner yang dapat diinterpretasikan baik sebagai instruksi atau data.

Modul I/O mentransfer data dari perangkat eksternal ke CPU dan memori, dan sebaliknya. Modul I/O berisi *buffer* internal yang berfungsi untuk menyimpan data sementara sampai data tersebut siap dikirim.

---

### Fetch Cycle

- Pada awal setiap siklus instruksi, prosesor mengambil instruksi dari memori.
- **Program Counter (PC)** menyimpan alamat instruksi yang akan diambil berikutnya.
- Prosesor akan menaikkan nilai PC setelah setiap instruksi diambil sehingga akan mengambil instruksi berikutnya secara berurutan.
- Instruksi yang diambil dimuat ke dalam **Instruction Register (IR)** .
- Prosesor menginterpretasikan instruksi dan melakukan tindakan yang diperlukan.

---

### Interupsi

Hampir semua komputer menyediakan mekanisme bahwa modul lain (I/O, memori) dapat melakukan interupsi proses normal prosesor.

**Beberapa Kelas Interupsi:**  
- **Program**: Dihasilkan oleh beberapa kondisi yang terjadi sebagai akibat dari eksekusi instruksi, seperti aritmatika *overflow*, pembagian dengan nol, upaya untuk mengeksekusi instruksi mesin ilegal, atau referensi di luar pengguna memungkinkan ruang memori.  
- **Timer**: Dihasilkan oleh *timer* dalam prosesor. Yang memungkinkan sistem operasi untuk menjalankan fungsi tertentu secara teratur.  
- **I/O**: Dihasilkan oleh I/O *controller*, untuk memberikan sinyal penyelesaian normal dari operasi, layanan permintaan dari prosesor, atau untuk sinyal berbagai kondisi kesalahan.  
- **Hardware Failure**: Dihasilkan oleh kegagalan seperti kegagalan daya atau kesalahan paritas memori.

**Mengapa Interupsi?**  
Interupsi disediakan terutama sebagai cara untuk meningkatkan efisiensi pemrosesan.  
Misalnya, sebagian besar perangkat eksternal jauh lebih lambat daripada prosesor. Seharusnya bahwa prosesor mentransfer data ke *printer* menggunakan skema siklus instruksi dari Gambar 3.3.  
Setelah setiap operasi tulis, prosesor harus berhenti dan tetap diam sampai *printer* mengejar ketinggalan. Panjang jeda ini mungkin pada urutan ratusan atau bahkan ribuan siklus instruksi yang tidak melibatkan memori.  
Jelas, ini adalah penggunaan prosesor yang sangat boros.

---

### Fungsi I/O

- Modul I/O dapat bertukar data secara langsung dengan prosesor.
- Prosesor dapat membaca data dari atau menulis data ke modul I/O.
- Prosesor mengidentifikasi perangkat tertentu yang dikendalikan oleh modul I/O tertentu.
- Dalam beberapa kasus memungkinkan I/O bertukar secara langsung dengan memori.
- Prosesor memberikan modul I/O otoritas untuk baca dari atau tulis ke memori, sehingga transfer I/O-memori tanpa ada ikatan dengan prosesor. Operasi ini disebut dengan **Direct Memory Access (DMA)** .

---

### Modul Komputer

Komputer memiliki 3 komponen atau modul utama: prosesor, memori, dan I/O yang saling berkomunikasi. Sehingga diperlukan jalur untuk berkomunikasi antar modul tersebut.  
Kumpulan jalur yang menghubungkan berbagai modul disebut **struktur interkoneksi**. Rancangan struktur tersebut akan bergantung pada pertukaran yang terjadi antar modul.

- **Memori**: Biasanya, sebuah modul memori akan terdiri dari N *word* dengan panjang yang sama. Setiap *word* diberi alamat numerik yang unik (0, 1, ..., N-1). Sebuah *word* data dapat dibaca atau ditulis dari/ke dalam memori. Operasi baca tulis tergantung dari sinyal kontrol. Lokasi untuk operasi ditentukan oleh alamat.
- **Modul I/O**: Dari sudut pandang internal (ke sistem komputer), I/O secara fungsional mirip dengan memori. Ada dua operasi, baca dan tulis. Modul I/O dapat mengontrol lebih dari satu perangkat eksternal. Memiliki sejumlah *port* yang berfungsi sebagai antarmuka dengan perangkat eksternal dan masing-masing memiliki alamat yang unik (misalnya, 0, 1, ..., M-1). Modul I/O dapat mengirim sinyal *interrupt* ke prosesor.
- **Prosesor**: Prosesor membaca instruksi dan data, menulis data yang sudah diproses. Menggunakan sinyal kontrol untuk mengontrol operasi keseluruhan dari sistem. Menerima sinyal interupsi.

---

### Bus

Jalur komunikasi yang menghubungkan dua atau lebih perangkat.  
Karakteristik utamanya adalah media transmisi bersama.  
Sejumlah perangkat terhubung ke bus, dan sinyal yang dikirimkan oleh suatu perangkat akan diterima oleh semua perangkat lain yang terhubung dengan bus.  
Jika dua perangkat mengirimkan selama periode waktu yang sama, sinyal tersebut akan saling tumpang tindih dan menjadi kacau.  
Jadi hanya ada satu perangkat yang dapat mengirim sinyal dengan sukses dalam satu waktu.

Biasanya, bus terdiri dari beberapa jalur komunikasi atau *line*.  
Setiap jalur mampu mentransmisikan sinyal yang mewakili biner 1 dan biner 0.  
Seiring perkembangan komputer, urutan digit biner dapat ditransmisikan melalui satu jalur/*line*.  
Beberapa jalur/*line* bus dapat digunakan untuk mengirimkan digit biner secara bersamaan (secara paralel). Sebagai contoh, unit data 8-bit dapat ditransmisikan melalui delapan jalur/*line* bus.

Sistem komputer mengandung sejumlah bus berbeda yang menyediakan jalur antara komponen pada berbagai tingkat hirarki sistem komputer.  
Sebuah bus yang menghubungkan komponen komputer utama (prosesor, memori, I/O) disebut **system bus**.  
Struktur interkoneksi komputer yang paling umum didasarkan pada penggunaan satu atau lebih bus sistem.

---

### Struktur Bus

Sebuah bus sistem biasanya terdiri dari sekitar lima puluh hingga ratusan jalur/*line* terpisah.  
Setiap jalur/*line* memiliki fungsi tertentu.  
Ada banyak desain bus yang berbeda, secara umum setiap jalur/*line* bus dapat diklasifikasikan menjadi tiga kelompok fungsional (Gambar 3.16):  
- **Bus Data**  
- **Bus Alamat**  
- **Bus Kontrol**

**Bus Data**  
Jalur data yang memberikan jalan untuk memindahkan data antara sistem modul.  
Dapat terdiri dari 32, 64, 128, atau lebih jalur yang terpisah.  
Jumlah jalur disebut sebagai **lebar bus data**.  
Jumlah jalur menentukan berapa banyak bit dapat ditransfer pada suatu waktu.  
Lebar bus data merupakan faktor kunci dalam menentukan keseluruhan kinerja sistem.

**Bus Alamat**  
Digunakan untuk menunjukkan sumber atau tujuan data pada bus data.  
Jika prosesor ingin membaca data dari memori, maka alamat dari data yang diinginkan ditempatkan pada saluran alamat.  
Lebar menentukan kemungkinan kapasitas memori maksimum dari sistem.  
Juga digunakan untuk mengatasi pengalamatan *port* I/O.  
Urutan bit lebih tinggi digunakan untuk memilih modul tertentu di bus dan urutan bit yang lebih rendah untuk memilih lokasi memori atau I/O *port* dalam modul.

**Bus Kontrol**  
Digunakan untuk mengontrol akses dan penggunaan data dan saluran alamat.  
Karena saluran data dan alamat digunakan oleh semua komponen, harus ada sarana untuk mengontrol penggunaannya.  
Sinyal kontrol mengirimkan baik perintah dan informasi *timing* antara modul sistem.  
- *Timing signal* menunjukkan validitas data dan informasi alamat.  
- Sinyal perintah menentukan operasi yang akan dilakukan.

**Jalur kontrol yang umum:**  
- *Memory Write*: memerintahkan data pada bus akan dituliskan ke dalam lokasi alamat.  
- *Memory Read*: memerintahkan data dari lokasi alamat ditempatkan pada bus data.  
- *I/O Write*: memerintahkan data pada bus dikirim ke lokasi *port* I/O.  
- *I/O Read*: memerintahkan data dari *port* I/O ditempatkan pada bus data.  
- *Transfer ACK*: menunjukkan data telah diterima dari bus atau data telah ditempatkan pada bus.  
- *Bus Request*: menunjukkan bahwa modul memerlukan kontrol/akses bus.  
- *Bus Grant*: menunjukkan modul yang melakukan *request* telah diberi hak mengontrol bus.  
- *Interrupt Request*: menandakan adanya penangguhan interupsi dari modul.  
- *Interrupt ACK*: menunjukkan penangguhan interupsi telah diketahui CPU.  
- *Clock*: kontrol untuk sinkronisasi operasi antar modul.  
- *Reset*: digunakan untuk menginisialisasi seluruh modul.

**Operasi pada Bus**  
Jika satu modul ingin mengirim data ke modul lain, ada dua hal yang dilakukan:  
1) Mendapatkan akses penggunaan bus, dan  
2) Mentransfer data melalui bus.

Jika satu modul ingin meminta data dari modul lain, hal yang dilakukan adalah:  
1) Mendapatkan akses penggunaan bus, dan  
2) Mentransfer permintaan ke modul lain melalui bus kontrol dan bus alamat. Kemudian harus menunggu modul yang diminta itu mengirimkan datanya.

---

### Hierarki Multiple Bus

Jika sejumlah besar perangkat terhubung ke bus, kinerja akan terganggu. Ada dua penyebab utama:

1. Secara umum, semakin banyak perangkat yang terhubung dengan bus, semakin besar panjang bus dan semakin besar *delay propagasi*. *Delay* ini menentukan waktu yang dibutuhkan perangkat untuk mengoordinasikan penggunaan bus. *Delay propagasi* dapat mempengaruhi kinerja.
2. Bus menjadi terganggu/*bottleneck* sebagai akibat permintaan sejumlah transfer data mendekati kapasitas bus. Hal ini dapat diatasi dengan memperlebar bus (misalnya; meningkatkan bus data dari 32 menjadi 64 bit).

Kecepatan data yang dihasilkan oleh perangkat yang terpasang (misalnya, VGA, LAN *Card*) berkembang pesat, sehingga bus tunggal tidak dapat mengimbangi kecepatan perangkat tersebut. Oleh karena itu, komputer saat ini dikembangkan dengan *Multiple Bus* yang disusun secara hierarki.

---

### Elemen Perancangan Bus

Ada beberapa parameter dasar atau elemen perancangan yang berfungsi untuk mengklasifikasikan dan membedakan bus.

- **Berdasarkan Tipe**  
  - *Dedicated*: Setiap bus (saluran) secara permanen diberi fungsi atau subset fisik komponen komputer.  
  - *Multiplexed bus*: Dilakukan informasi yang berbeda baik data, alamat maupun sinyal kontrol dengan metode multipleks data. Keuntungan adalah hanya memerlukan saluran sedikit sehingga dapat menghemat tempat. Kerugiannya adalah kecepatan transfer data menurun dan diperlukan mekanisme yang kompleks untuk mengurai data yang telah dimultipleks.

- **Metode Arbitrasi**  
  - *Centralized*: Perangkat keras tunggal, yang disebut sebagai pengendali bus atau *arbiter*, bertanggung jawab untuk mengalokasikan waktu di bus. Perangkat/*arbiter* dapat berupa modul terpisah atau bagian dari prosesor.  
  - *Distributed*: Tidak ada pengontrol pusat. Sebaliknya, setiap modul memiliki logika kontrol akses dan modul bertindak bersama untuk berbagi bus.

- **Timing**  
  *Timing* mengacu pada cara di mana kejadian/*event* dikoordinasikan di bus. Bus menggunakan *synchronous timing* atau *timing asinkron*.  
  - *Synchronous timing*: *Event* terjadi ditentukan oleh pewaktu/*clock*. Sebuah transmisi 1-0 disebut siklus waktu atau siklus bus dan menentukan besarnya *slot* waktu. Semua perangkat modul pada bus dapat membaca atau mengetahui siklus *clock*. Biasanya satu siklus untuk satu *event*. Pendekatan ini mudah diimplementasikan, namun kurang fleksibel untuk perangkat yang memiliki kecepatan operasi berbeda-beda. Biasanya digunakan untuk modul tertentu yang sudah jelas karakteristiknya.  
  - *Asynchronous timing*: Kerja modul yang tidak serempak kecepatannya. *Event* yang terjadi pada bus tergantung dari *event* sebelumnya sehingga diperlukan sinyal-sinyal validasi untuk mengidentifikasi data yang ditransfer. Sistem ini mampu menggabungkan kerja modul-modul yang berbeda kecepatan maupun teknologinya, asalkan aturan transfernya sama.

- **Lebar Bus**  
  - Semakin lebar bus maka semakin besar data yang dapat ditransfer sekali waktu.  
  - Semakin besar bus alamat, akan semakin banyak *range* lokasi yang dapat direferensikan.

- **Tipe Transfer Data**  
  - *Read*  
  - *Write*  
  - *Read-modify-write*  
  - *Read-after-write*  
  - *Block*
