Selamat datang di langkah pertama Anda dalam mempelajari bahasa pemrograman Zig. Panduan ini dirancang untuk menuntun Anda sepenuhnya dari awal, mulai dari menyiapkan ruang kerja, membuat berkas pertama, hingga memahami cara kerja kode secara mendetail. Seluruh penjelasan disajikan dalam bentuk narasi yang mengalir dan sederhana agar mudah dipahami oleh pemula, namun tetap mempertahankan kejelasan teknis yang dibutuhkan oleh pemrogram berpengalaman.

---

## 1. Menyiapkan Ruang Kerja

Sebelum mulai menulis kode, langkah awal yang harus dilakukan adalah menyiapkan ruang kerja atau *workspace* secara manual agar lebih sederhana. Buka terminal komputer Anda, lalu buat sebuah folder baru dengan menjalankan perintah `mkdir hello_world` dan masuk ke dalamnya menggunakan perintah `cd hello_world`. Setelah berada di dalam folder tersebut, buatlah sebuah berkas kosong baru dan beri nama `main.zig`. Berkas tunggal inilah yang akan menjadi tempat kita menulis seluruh kode dan bertindak sebagai titik awal eksekusi program Anda.

---

## 2. Menulis Kode Pertama Anda

Untuk mulai bereksperimen, buka berkas `main.zig` yang baru saja Anda buat menggunakan editor teks pilihan Anda (seperti VS Code atau Notepad). Karena berkas tersebut masih kosong, silakan tulis atau salin baris kode sederhana di bawah ini untuk mencetak kalimat sapaan ke layar terminal:

```zig
const std = @import("std");

pub fn main() !void {
    std.debug.print("Assalamualaikum \n", .{});    
}

```

---

## 3. Memahami Baris demi Baris

Mari kita bedah struktur kode di atas secara berurutan agar Anda dapat memahami fungsinya dengan mudah. Kode diawali dengan baris `const std = @import("std");` yang berfungsi untuk memanggil pustaka standar bawaan Zig, lalu menyimpannya ke dalam sebuah variabel konstan bernama `std` agar fiturnya bisa kita gunakan.

Selanjutnya, baris `pub fn main() !void {` digunakan untuk mendefinisikan fungsi utama program yang bersifat publik atau dapat diakses oleh sistem dari luar. Simbol tanda seru dan kata `void` (`!void`) di sana menandakan bahwa fungsi ini memiliki potensi untuk menghasilkan *error*, namun jika program berjalan dengan lancar, ia tidak akan mengembalikan nilai data apa pun.

Di dalam fungsi utama tersebut, terdapat perintah `std.debug.print` yang kita gunakan untuk menampilkan teks ke layar terminal. Teks sapaan diakhiri dengan karakter `\n` yang berfungsi untuk memindahkan kursor terminal ke baris baru setelah teks dicetak. Terakhir, simbol kurung kurawal kosong `.{}` di ujung perintah merupakan parameter wajib berbentuk *anonymous struct* yang sengaja dikosongkan karena kita murni hanya mencetak kalimat biasa tanpa menyisipkan variabel tambahan di dalamnya.

---

## 4. Cara Menjalankan Program

Karena kita menggunakan struktur proyek tunggal yang sangat minimalis tanpa berkas konfigurasi tambahan yang rumit, cara menjalankan programnya pun sangat mudah. Buka kembali terminal Anda, pastikan Anda masih berada di dalam folder `hello_world`, lalu jalankan perintah `zig run main.zig`.

Perintah ini akan langsung mengompilasi dan menjalankan kode Anda di dalam memori komputer secara cepat tanpa meninggalkan bekas berkas biner (`.exe`) yang mengotori folder Anda. Setelah dieksekusi, Anda akan langsung melihat hasil akhirnya berupa teks sapaan Assalamualaikum yang muncul dengan rapi pada layar terminal Anda.
