# Perulangan(loop) dengan "for"
Looping dalam PHP menggunakan `for` digunakan untuk mengulangi sebuah blok kode sejumlah iterasi tertentu. Struktur umum dari loop `for` adalah sebagai berikut:

```php
for (inisialisasi; kondisi; iterasi) {
    // blok kode yang akan diulang
}
```

- `inisialisasi`: Dieksekusi sekali saat loop dimulai. Biasanya digunakan untuk menginisialisasi variabel kontrol loop.
- `kondisi`: Menentukan kapan loop harus dijalankan. Jika kondisi ini bernilai `true`, loop akan terus berjalan; jika `false`, loop akan berhenti.
- `iterasi`: Dieksekusi setiap kali setelah blok kode dijalankan. Biasanya digunakan untuk memperbarui variabel kontrol loop.

Contoh sederhana looping `for` dalam PHP:

```php
<?php
for ($i = 1; $i <= 5; $i++) {
    echo "Iterasi ke-$i<br>";
}
?>
```

Pada contoh di atas:
- `$i = 1`: Inisialisasi variabel `$i` dengan nilai 1.
- `$i <= 5`: Kondisi loop. Loop akan terus berjalan selama nilai `$i` kurang dari atau sama dengan 5.
- `$i++`: Iterasi. Setiap kali blok kode dijalankan, nilai `$i` akan bertambah satu.

Hasilnya akan mencetak:

```
Iterasi ke-1
Iterasi ke-2
Iterasi ke-3
Iterasi ke-4
Iterasi ke-5
```

Ini adalah contoh loop `for` yang sederhana. Anda dapat menggantinya sesuai dengan kebutuhan spesifik Anda.

## Kontrol alur eksekusi loop
Dalam loop `for` di PHP, terdapat dua kata kunci yang sering digunakan untuk mengontrol alur eksekusi loop: `continue` dan `break`.

1. **Continue:**
   - Kata kunci `continue` digunakan untuk melanjutkan eksekusi ke iterasi berikutnya dalam loop, mengabaikan sisa kode di dalam blok loop.
   - Ketika `continue` dieksekusi, program akan meloncat langsung ke langkah iterasi berikutnya, melewatkan sisa blok kode di dalam loop.
   - Contoh penggunaan `continue`:

     ```php
     <?php
     for ($i = 1; $i <= 5; $i++) {
         if ($i == 3) {
             continue; // Melanjutkan ke iterasi berikutnya jika $i sama dengan 3
         }
         echo "Iterasi ke-$i<br>";
     }
     ?>
     ```

     Output yang dihasilkan:

     ```
     Iterasi ke-1
     Iterasi ke-2
     Iterasi ke-4
     Iterasi ke-5
     ```

2. **Break:**
   - Kata kunci `break` digunakan untuk menghentikan eksekusi loop dan keluar dari loop, bahkan jika iterasi belum selesai.
   - Ketika `break` dieksekusi, program keluar dari loop dan melanjutkan eksekusi kode berikutnya setelah loop.
   - Contoh penggunaan `break`:

     ```php
     <?php
     for ($i = 1; $i <= 5; $i++) {
         if ($i == 3) {
             break; // Keluar dari loop jika $i sama dengan 3
         }
         echo "Iterasi ke-$i<br>";
     }
     ?>
     ```

     Output yang dihasilkan:

     ```
     Iterasi ke-1
     Iterasi ke-2
     ```

Dengan menggunakan `continue` dan `break`, Anda dapat mengontrol alur eksekusi loop sesuai dengan kebutuhan logika program Anda.

## Praktikum

### 1. loop angka 1 sampai 10
Berikut adalah contoh penggunaan perulangan `for` dalam PHP untuk mencetak angka dari 1 hingga 10:

```php
<?php
for ($i = 1; $i <= 10; $i++) {
    echo $i . " ";
}
?>
```

Output dari kode di atas akan menjadi:

```
1 2 3 4 5 6 7 8 9 10
```

Pada contoh ini, perulangan dimulai dari `$i = 1` dan terus berlanjut selama `$i` kurang dari atau sama dengan 10. Setiap iterasi, nilai `$i` ditampilkan dan kemudian diikuti dengan spasi. Anda dapat mengubah inisialisasi, kondisi, atau iterasi sesuai kebutuhan spesifik Anda.

### 2. Menentukan jumlah perulangan dengan menggunakan form
Berikut adalah contoh penggunaan perulangan `for` dalam PHP dengan tambahan sebuah formulir (form) yang memungkinkan pengguna untuk menentukan berapa kali pengulangan akan dilakukan:

Pada pertemuan sebelumnya, kita membuat aplikasi dengan memisah file antara form dengan kode PHP untuk memproses inputan. Sekarang kita akan mulai menggunakan 1 file saja yg memuat form beserta kode proses nya. Namun kita perlu memanfaatkan logika `if` karena ketika awal file diakses, data POST belum ada dan akan menyebabkan error ketika kita mencoba mengakses nya pertama kali. 

Kita bisa menyiasatinya dengan menggunakan:

```php
if (isset($_POST["jumlah_pengulangan"])) {
    // Kode di dalam blok ini akan dijalankan jika POST sudah memuat data "jumlah_pengulangan"
}
```
Kode ini menggunakan fungsi `isset()` untuk memeriksa apakah elemen dengan nama "jumlah_pengulangan" telah diset (ada) dalam array `$_POST`. Ini umumnya digunakan untuk memeriksa apakah suatu formulir telah dikirimkan dan apakah data tertentu dari formulir tersebut sudah diterima.

Penjelasan lebih lanjut:

- `$_POST`: Variabel super global di PHP yang digunakan untuk mengumpulkan data formulir yang dikirimkan menggunakan metode "POST".
- `["jumlah_pengulangan"]`: Ini adalah nama elemen formulir yang akan diperiksa keberadaannya dalam array `$_POST`.
- `isset($_POST["jumlah_pengulangan"])`: Fungsi `isset()` digunakan untuk memeriksa apakah suatu variabel atau elemen array sudah di-set (ada). Jika elemen "jumlah_pengulangan" sudah ada dalam array `$_POST`, maka kondisi ini akan bernilai `true`.

Jadi, blok kode di dalam `if` tersebut akan dijalankan jika formulir telah dikirimkan (menggunakan metode "POST") dan data dengan nama "jumlah_pengulangan" ada dalam data formulir yang dikirimkan. Ini berguna untuk memastikan bahwa sebelum menjalankan kode yang memproses formulir, kita memiliki data yang diperlukan dari formulir tersebut.

OK, kalau sdh paham kita lanjut praktikum nya. Buat sebuah file yg bernama `formloop.php`. lalu masukkan kode berikut.

```php
<form method="post" action="formloop.php">
    <label for="jumlah_pengulangan">Masukkan jumlah pengulangan:</label>
    <input type="number" name="jumlah_pengulangan" id="jumlah_pengulangan" required>
    <button type="submit">Submit</button>
</form>

<?php
//kalau sudah ada $_POST["jumlah_pengulangan"], maka lakukan proses perulangan.
if (isset($_POST["jumlah_pengulangan"])) {
    // Ambil nilai jumlah_pengulangan dari form
    $jumlah_pengulangan = $_POST["jumlah_pengulangan"];

    // Perulangan for
    for ($i = 1; $i <= $jumlah_pengulangan; $i++) {
        echo $i . " ";
    }
}else{
    //kalau $_POST["jumlah_pengulangan"] belum ada, tampilkan pesan ini
    echo "Masukkan jumlah pengulangan";
}
?>
```

Dalam contoh ini, sebuah formulir sederhana dibuat dengan input number yang meminta pengguna untuk memasukkan jumlah pengulangan yang diinginkan. Setelah pengguna mengirim formulir, PHP akan mengambil nilai tersebut menggunakan `$_POST` dan menjalankan perulangan `for` sesuai dengan jumlah pengulangan yang dimasukkan. Hasilnya kemudian ditampilkan di halaman yg sama.

Perhatikan pada form diatas, atribut `action` kita arahkan ke file ini sendiri.

### 3. Contoh for loop bersarang
Seperti while, For loop juga dapat dibuat bersarang, artinya Anda dapat menempatkan satu atau lebih for loop di dalam for loop lainnya. Hal ini memungkinkan Anda untuk melakukan iterasi dalam pola yang lebih kompleks atau untuk memproses data dalam bentuk matriks atau struktur bersarang lainnya. 

Berikut adalah contoh sederhana for loop bersarang yang mencetak angka:

```php
<?php
for ($i = 1; $i <= 5; $i++) {
    for ($j = 1; $j <= $i; $j++) {
        echo $i;
    }
    echo "<br>";
}
?>
```

Penjelasan singkat:

- Loop pertama (`$i`): Digunakan untuk mengatur jumlah baris.
- Loop kedua (`$j`): Digunakan untuk mencetak angka sebanyak `$i` kali pada setiap baris.
- `echo $i;`: Mencetak nilai `$i` pada setiap iterasi loop kedua.
- `echo "<br>";`: Menambahkan tag `<br>` untuk pindah ke baris baru setelah mencetak angka pada setiap baris.

Output dari kode di atas akan menjadi:

```
1
22
333
4444
55555
```

Setiap baris mencetak angka yang sesuai dengan jumlah baris tersebut. Anda dapat memodifikasi nilai batas perulangan pertama (5 pada contoh di atas) sesuai dengan pola yang diinginkan.

For loop bersarang ini memberikan fleksibilitas dalam menangani struktur data yang bersarang atau ketika Anda perlu melakukan iterasi dalam pola yang lebih kompleks.
