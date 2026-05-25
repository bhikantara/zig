Bahasa pemrograman **Zig** (termasuk hingga versi terbarunya, yaitu versi 0.16.0) Saat ini, Zig memiliki tepat **49 kata kunci (keywords)**.

---

### 1. Deklarasi & Variabel

Bagian ini berisi kata kunci yang digunakan untuk mendefinisikan variabel, konstanta, serta bagaimana nilai tersebut disimpan di dalam memori atau diproses pada saat waktu kompilasi (*compile-time*).

| Keyword | Arti | Penjelasan Lengkap |
| --- | --- | --- |
| `const` | Konstanta | Mendefinisikan nilai yang **tidak bisa diubah** (*immutable*) setelah diinisialisasi. Sangat disarankan dipakai jika nilai tidak akan berubah. |
| `var` | Variabel | Mendefinisikan variabel biasa yang nilainya **bisa diubah** (*mutable*) selama program berjalan. |
| `comptime` | Waktu Kompilasi | Memaksa agar variabel, blok kode, atau evaluasi fungsi diproses **saat kode sedang dikompilasi**, bukan saat program berjalan (*run-time*). Ini adalah inti dari fitur *metaprogramming* di Zig. |
| `threadlocal` | Variabel Thread | Menyatakan bahwa setiap *thread* di dalam program akan memiliki salinan memori tersendiri untuk variabel tersebut, tidak saling berbagi. |

---

### 2. Tipe Data & Struktur

Bagian ini berisikan kata kunci untuk merancang cetak biru data, mulai dari pengelompokan variabel, pendefinisian memori, hingga pembuatan tipe error khusus.

| Keyword | Arti | Penjelasan Lengkap |
| --- | --- | --- |
| `struct` | Struktur | Membuat tipe data kompleks yang mengelompokkan berbagai variabel (field) dan fungsi di dalam satu wadah. |
| `enum` | Enumerasi | Mendefinisikan sebuah tipe data yang hanya boleh memiliki salah satu dari sekumpulan nama/nilai pasti yang telah ditentukan. |
| `union` | Kesatuan Data | Tipe data di mana semua *field* di dalamnya berbagi lokasi memori yang sama. Hanya satu *field* yang bisa aktif dalam satu waktu. |
| `opaque` | Tipe Buram | Digunakan untuk mendefinisikan tipe data yang ukuran atau letak memorinya tidak diketahui. Sangat berguna saat berinteraksi dengan API bahasa C (*C Pointers*). |
| `error` | Set Error | Mendefinisikan kumpulan tipe *error* bawaan. Zig tidak menggunakan *Exceptions* (seperti `try/catch` di Java), melainkan menjadikan error sebagai nilai data (*Error Set*). |
| `anytype` | Tipe Dinamis | Digunakan pada parameter fungsi untuk menerima argumen dengan tipe data bebas. Tipe aslinya akan disimpulkan secara otomatis saat *compile-time* (*Duck typing*). |

---

### 3. Kendali Alur (Control Flow)

Bagian ini merupakan kata kunci yang bertugas mengatur arah berjalannya program, seperti percabangan logika, perulangan, hingga penghentian paksa.

| Keyword | Arti | Penjelasan Lengkap |
| --- | --- | --- |
| `if` | Jika | Mengevaluasi logika bersyarat. Jika kondisi benar (*true*), maka blok kodenya dieksekusi. |
| `else` | Jika Tidak | Pasangan dari `if`, `switch`, `while`, atau `for`. Akan dieksekusi jika kondisi utama bernilai salah (*false*), bernilai *null*, atau jika terjadi error. |
| `switch` | Pemilihan / Kasus | Alternatif rapi untuk `if-else` yang berantai. Mengevaluasi satu nilai terhadap banyak kemungkinan kecocokan kasus (seperti *switch-case*). |
| `while` | Perulangan Syarat | Menjalankan blok kode secara berulang-ulang selama syarat kondisinya masih bernilai benar (*true*). |
| `for` | Perulangan Iterasi | Menjalankan perulangan di atas sebuah struktur data secara langsung, seperti *array*, *slice*, atau *tuple*. |
| `break` | Hentikan | Digunakan untuk melompat keluar dan menghentikan perulangan (`while` atau `for`) secara paksa. |
| `continue` | Lanjutkan | Menghentikan sisa eksekusi pada putaran loop saat ini, lalu langsung melompat ke putaran / iterasi berikutnya. |
| `return` | Kembalikan Nilai | Menghentikan fungsi yang sedang berjalan dan memberikan (mengembalikan) suatu nilai ke tempat fungsi tersebut dipanggil. |
| `unreachable` | Tak Tercapai | Memberi tahu kompiler bahwa baris kode ini **mustahil** untuk dieksekusi. Jika tanpa sengaja tereksekusi saat *runtime*, program akan *panic* (crash dengan aman). |
| `defer` | Tunda Eksekusi | Menjadwalkan sebuah baris kode agar dieksekusi tepat **sebelum** keluar dari blok saat ini. Sering dipakai untuk membersihkan memori (bebas alokasi). |
| `errdefer` | Tunda jika Error | Sama seperti `defer`, tetapi blok kode ini **hanya akan dijalankan jika** blok fungsi tersebut keluar dalam keadaan gagal atau mengembalikan *error*. |

---

### 4. Logika, Opsional & Penanganan Error

Zig sangat ketat dengan error dan nilai kosong (`null`). Bagian ini berisi kata kunci operator logika dan alat bantu untuk membuka paket data opsional atau error.

| Keyword | Arti | Penjelasan Lengkap |
| --- | --- | --- |
| `and` | Logika DAN | Operator logika AND. Menghasilkan *true* hanya jika kedua sisi bernilai benar. Memiliki sifat *short-circuit* (berhenti mengevaluasi jika sisi kiri sudah *false*). |
| `or` | Logika ATAU | Operator logika OR. Menghasilkan *true* jika salah satu sisi bernilai benar. Juga bersifat *short-circuit*. |
| `orelse` | Atau Jika Null | Mengekstrak nilai opsional (`?T`). Jika nilainya `null`, maka ia akan mengembalikan nilai alternatif (default) yang ada di sebelah kanannya. |
| `catch` | Tangkap Error | Mengekstrak nilai yang berpotensi error (`!T`). Jika berisi error, maka ia akan memberikan nilai alternatif yang ada di kanannya, atau melempar logika ke blok lain. |
| `try` | Coba & Kembalikan | Jalan pintas untuk eksekusi. Jika fungsi melempar error, `try` akan langsung mengembalikan (*return*) error tersebut ke luar fungsi utama; jika sukses, nilainya diekstrak. |

---

### 5. Fungsi, Lingkup & Pengujian

Kelompok kata kunci ini berkaitan dengan pembuatan komponen utama dari blok pemograman: membuat fungsi, mengatur siapa yang bisa melihatnya, dan pengujian program.

| Keyword | Arti | Penjelasan Lengkap |
| --- | --- | --- |
| `fn` | Fungsi | Digunakan untuk mendeklarasikan sebuah fungsi (*function*). |
| `pub` | Publik | Membuat deklarasi variabel, fungsi, atau struktur bisa diakses (bisa di-import) dari file atau *module* luar. |
| `usingnamespace` | Impor Ruang Nama | Mengambil semua deklarasi publik dari sebuah tipe/file dan meleburnya ke dalam ruang lingkup (*scope*) saat ini seolah-olah ditulis di sana. |
| `test` | Blok Uji | Membuat fungsi khusus untuk unit pengujian (*Unit Testing*). Blok ini tidak akan dimasukkan ke aplikasi akhir, hanya berjalan saat dipanggil via `zig test`. |
| `anyframe` | Frame Asinkron | Mewakili alokasi bingkai memori (*stack frame*) untuk fungsi asinkron (biasanya digunakan pada coroutine tingkat lanjut). |

---

### 6. Pemrograman Konkuren & Asinkron

Zig memiliki fitur bawaan untuk *asynchronous programming* atau fungsi yang bisa dijeda tanpa memblokir sistem. Berikut kata kuncinya (Catatan: Fitur ini sedang dirombak ulang perlahan oleh tim Zig sejak versi 0.11 ke atas).

| Keyword | Arti | Penjelasan Lengkap |
| --- | --- | --- |
| `async` | Asinkronisasi | Memanggil sebuah fungsi secara asinkron. Fungsi akan mulai berjalan, tapi program tidak akan menunggu hingga fungsi tersebut selesai. |
| `await` | Tunggu Asinkron | Menunggu hasil (nilai kembali) dari fungsi `async` yang sedang berjalan. Eksekusi lokal akan terjeda sampai hasilnya siap. |
| `suspend` | Tunda | Menghentikan sementara fungsi yang sedang berjalan dan mengembalikan kontrol ke pemanggilnya, tanpa mematikan fungsi tersebut. |
| `resume` | Lanjutkan | Melanjutkan (membangunkan) kembali fungsi asinkron yang sebelumnya tertidur akibat `suspend`. |
| `nosuspend` | Tanpa Tunda | Memaksa fungsi atau blok kode untuk berjalan sinkron penuh dan menjamin bahwa tidak ada `suspend` tersembunyi yang akan terjadi di dalamnya. |

---

### 7. Pengaturan Memori & Atribut Modifikasi

Bagian ini sangat diandalkan untuk "Sistem Programming", di mana programmer perlu mengatur langsung ukuran bit, padding, dan optimasi level rendah.

| Keyword | Arti | Penjelasan Lengkap |
| --- | --- | --- |
| `align` | Penyelarasan | Menentukan kelipatan *byte* atau posisi khusus di memori (*alignment*) untuk menyimpan sebuah variabel atau tipe data tertentu. |
| `allowzero` | Izinkan Nol | Atribut yang mengizinkan *pointer* menunjuk secara legal ke alamat memori `0`. (Normalnya, Zig melarang *pointer* menunjuk ke alamat nol/Null secara aman). |
| `packed` | Padatkan Memori | Memaksa komponen `struct` atau `union` untuk saling berhimpitan tanpa *padding* (ruang kosong) di memori, menjadikannya sekecil mungkin pada tingkat bit. |
| `volatile` | Memori Rentan | Memberi tahu kompiler untuk **tidak melakukan optimasi** (seperti caching) pada akses variabel ini, karena nilainya bisa berubah sewaktu-waktu oleh *hardware*. |
| `inline` | Sisipkan Barisan | Memaksa kompiler untuk "membongkar" isi fungsi atau perulangan (`for`/`while`) ke tempat ia dipanggil, alih-alih melakukan lompatan memori pemanggilan rutin. |
| `noinline` | Larang Sisipan | Kebalikan dari `inline`. Melarang kompiler secara ketat untuk menyisipkan fungsi ini. Berguna untuk menekan ukuran file aplikasi (*binary size*). |
| `noalias` | Tanpa Tumpang Tindih | Menandai parameter *pointer* pada fungsi untuk menjamin bahwa memori pointer ini tidak bentrok/bersinggungan (*overlap*) dengan parameter pointer lainnya. |

---

### 8. Interoperabilitas C & Sistem Tingkat Rendah (FFI)

Zig adalah pengganti modern bagi C. Karena itu, Zig dilengkapi kata kunci khusus untuk "berbicara" langsung dengan arsitektur CPU dan perpustakaan dari bahasa C.

| Keyword | Arti | Penjelasan Lengkap |
| --- | --- | --- |
| `extern` | Eksternal | Mendeklarasikan fungsi atau variabel yang ditulis dan berada di luar kode Zig (misalnya, fungsi milik C library yang di-link ke program). |
| `export` | Ekspor (Ke Luar) | Membuka fungsi atau variabel Zig agar bisa dibaca dan dipanggil oleh bahasa lain atau OS menggunakan kesepakatan format standar (C ABI). |
| `asm` | Instruksi Mesin | Mengizinkan penulisan instruksi tingkat CPU (*Inline Assembly*) langsung di dalam blok kode Zig. |
| `callconv` | Konvensi Panggil | Mengatur bagaimana argumen disalurkan di level memori saat memanggil fungsi (Contoh: `callconv(.C)` memastikan fungsinya dipanggil sesuai aturan C). |
| `linksection` | Lokasi Linker | Menaruh variabel atau fungsi pada "seksi / bagian" (section) biner spesifik di dalam program yang sudah dikompilasi. Umum digunakan dalam pemograman *Kernel/OS*. |
| `addrspace` | Ruang Alamat | Digunakan untuk menyatakan bahwa suatu *pointer* berada di *address space* khusus (sangat penting untuk pemrograman GPU / mikrokontroler spesifik). |
