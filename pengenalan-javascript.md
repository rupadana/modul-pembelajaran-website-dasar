# 5. Pengenalan Javascript

## 5.1 Sintaks Dasar

Bagian pertama adalah Sintaks Dasar. Anggap saja ini sebagai "tata bahasa" dari JavaScript. Ini adalah aturan tentang bagaimana kita menulis instruksi agar komputer mengerti.


### 5.1.1 Komentar

Salah satu bagian paling awal dari sintaks adalah komentar (comments).

Komentar adalah baris kode yang diabaikan oleh JavaScript.

Tujuannya adalah untuk memberi catatan bagi diri kita sendiri atau programmer lain yang membaca kode kita.

Anda menyebutkan ada dua cara untuk membuatnya:

1. `//` (Garis miring ganda) untuk komentar satu baris.
2. `/* ... */` (Garis miring bintang) untuk komentar multi-baris.
   
```javascript
// Ini adalah komentar satu baris.

/* Ini adalah
  komentar multi-baris.
*/
```

Setelah memahami cara menulis "catatan" dalam kode, langkah selanjutnya adalah tentang cara menyimpan informasi.

### Variable

Variabel adalah "wadah" di dalam kode untuk menyimpan data. Anda memberi nama pada wadah ini, sehingga Anda bisa memanggil atau mengubah isinya nanti.

Seperti dalam rencana Anda, ada tiga kata kunci (keyword) untuk membuat variabel di JavaScript:

1. `var` (Variabel): Ini adalah cara lama. Sebaiknya Anda tahu ini ada, tapi untuk kode modern, kita lebih sering pakai dua di bawah ini.

2. `let` : Ini adalah cara modern untuk membuat variabel yang nilainya bisa berubah.

3. `const` (Konstanta): Ini adalah cara modern untuk membuat variabel yang nilainya tidak akan pernah berubah (konstan) setelah pertama kali diisi.

#### Perbedaan Utama: `let` vs `const`
Ini adalah inti dari rencana Anda: "kapan harus menggunakan `let` dan `const`."

Gunakan `let` jika Anda tahu nilainya perlu diubah nanti.

Gunakan `const` jika Anda tahu nilainya akan tetap sama.

#### Contoh `let`:
```javascript
// Kita pakai let karena 'skor' akan berubah
let skor = 0;
skor = 10; // Nilainya diubah, ini boleh
skor = 20; // Diubah lagi, ini juga boleh
```
#### Contoh `const`:
```javascript
// Kita pakai const karena nama 'pemain' tidak akan berubah
const namaPemain = "Alex";

// Jika kita coba ubah, kita akan dapat error!
// namaPemain = "Budi"; // <-- Ini akan menyebabkan error
```

Aturan praktis yang bagus: Selalu coba gunakan `const` terlebih dahulu. Jika Anda sadar bahwa nilainya nanti perlu diubah, baru ganti menjadi `let`.

Jika Anda ingin menyimpan jumlah nyawa dalam sebuah game (yang bisa berkurang), Anda akan menggunakan `let` atau `const`? Bagaimana jika Anda ingin menyimpan nama game itu sendiri?

Dari study case diatas, kita akan menggunakan `let` untuk jumlah nyawa dalam sebuah game dan `const` untuk nama game.

#### Contoh
```javascript
const namaGame = "Petualangan Hebat";
let jumlahNyawa = 3;
```

Logikanya sederhana:

- `namaGame` tidak akan berubah di tengah-tengah permainan.
- `jumlahNyawa` pasti akan berubah.

Kita sudah menyelesaikan bagian Variabel (`var`, `let`, `const`)

### Tipe Data

Setiap variabel yang kita buat (`let` atau `const`) menyimpan satu jenis data. JavaScript perlu tahu apakah kita menyimpan teks, angka, atau data logika (benar/salah) agar bisa mengolahnya dengan benar.

Sesuai rencana Anda, tipe data terbagi dua:

#### Tipe Data Primitif
Ini adalah tipe data yang paling dasar dan sederhana.

- String 📝
  - Apa itu: Teks.
  - Cara menulis: Selalu diapit oleh tanda kutip ("), kutip tunggal ('), atau backtick (`).
  - Contoh: `const nama = "Alex"; atau let email = 'alex@gmail.com';`

- Number 🔢
  - Apa itu: Angka.
  - Cara menulis: Tulis saja angkanya, tanpa kutip. Bisa angka bulat (integer) atau desimal (float).
  - Contoh: `let umur = 25; atau const harga = 1500.50;`

- Boolean ✅❌

  - Apa itu: Logika. Nilainya hanya ada dua: true (benar) atau false (salah).
  - Cara menulis: Langsung tulis true atau false (tanpa kutip).
  - Contoh: `let sedangBermain = true; atau const sudahSelesai = false;`

- Null dan Undefined
  - undefined artinya variabelnya sudah dibuat (dideklarasikan) tapi belum diisi nilai.
  - null artinya variabelnya ada, tapi kita sengaja mengaturnya agar kosong (tidak punya nilai).

#### Tipe Data Kompleks
Ini adalah tipe data yang bisa menampung kumpulan data.

- Object 👤

  - Apa itu: Kumpulan data yang saling berhubungan, disimpan dalam format "nama: nilai".

  - Contoh: `const pemain = { nama: "Alex", skor: 100, level: 5 };`

- Array 🗂️

  - Apa itu: Daftar data yang berurutan.

  - Contoh: `const hobi = ["membaca", "main game", "tidur"];`

Kita tidak perlu pusing dulu dengan Object dan Array. Sesuai rencana Anda, kita akan membedah keduanya secara khusus nanti di Pertemuan 11.

Sekarang, mari kita uji pemahaman tentang String dan Number.

Lihat dua variabel ini:


```javascript
let A = 10;
let B = "10";
```
Apakah `A` dan `B` menyimpan tipe data yang sama?

Jawabannya adalah `tidak`, tipe data keduanya berbeda.

`let A = 10;` adalah tipe data `Number` (angka).

`let B = "10";` adalah tipe data `String` (teks), karena diapit oleh tanda kutip (").

Bagi JavaScript, `A` adalah nilai yang bisa digunakan untuk perhitungan matematika, sedangkan `B` adalah sepotong teks.

### Operator

Operator adalah simbol khusus yang kita gunakan untuk melakukan operasi (tindakan) pada nilai atau variabel.

#### Operator Aritmatika

Mari kita pelajari keempat operator aritmatika dasar secara lebih mendalam:

##### 1. Operator Penjumlahan (+) 🧮
Operator penjumlahan digunakan untuk menambahkan dua atau lebih angka.

```javascript
// Penjumlahan angka
let angka1 = 15;
let angka2 = 25;
let hasil = angka1 + angka2;
console.log(hasil); // Output: 40

// Penjumlahan dengan angka desimal
let harga1 = 12.50;
let harga2 = 7.30;
let totalHarga = harga1 + harga2;
console.log(totalHarga); // Output: 19.8

// Penjumlahan langsung
let skorAkhir = 100 + 50 + 25;
console.log(skorAkhir); // Output: 175
```

**Catatan Penting**: Seperti yang sudah dijelaskan sebelumnya, operator `+` juga berfungsi untuk menggabungkan string. Hati-hati dengan tipe data!

##### 2. Operator Pengurangan (-) ➖
Operator pengurangan digunakan untuk mengurangi suatu angka dengan angka lain.

```javascript
// Pengurangan dasar
let uangAwal = 100000;
let uangBelanja = 25000;
let sisaUang = uangAwal - uangBelanja;
console.log(sisaUang); // Output: 75000

// Pengurangan dengan angka negatif
let suhu = 30;
let perubahanSuhu = -5;
let suhuBaru = suhu - perubahanSuhu; // 30 - (-5) = 30 + 5 = 35
console.log(suhuBaru); // Output: 35

// Pengurangan bertingkat
let nilaiAwal = 100;
let pengurangan1 = 20;
let pengurangan2 = 15;
let hasilAkhir = nilaiAwal - pengurangan1 - pengurangan2;
console.log(hasilAkhir); // Output: 65
```

##### 3. Operator Perkalian (*) ✖️
Operator perkalian digunakan untuk mengalikan angka.

```javascript
// Perkalian dasar
let panjang = 8;
let lebar = 6;
let luas = panjang * lebar;
console.log(luas); // Output: 48

// Perkalian dengan angka desimal
let hargaSatuan = 15.50;
let jumlahBarang = 3;
let totalBayar = hargaSatuan * jumlahBarang;
console.log(totalBayar); // Output: 46.5

// Menghitung pangkat sederhana (contoh: 2³)
let angkaPokok = 2;
let hasilPangkat = angkaPokok * angkaPokok * angkaPokok; // 2 × 2 × 2
console.log(hasilPangkat); // Output: 8
```

##### 4. Operator Pembagian (/) ➗
Operator pembagian digunakan untuk membagi suatu angka dengan angka lain.

```javascript
// Pembagian dasar
let totalKue = 24;
let jumlahOrang = 6;
let kuePerOrang = totalKue / jumlahOrang;
console.log(kuePerOrang); // Output: 4

// Pembagian dengan hasil desimal
let jarak = 100;
let waktu = 3;
let kecepatan = jarak / waktu;
console.log(kecepatan); // Output: 33.333333333333336

// Pembagian dengan nol (hati-hati!)
let angka = 10;
let pembagi = 0;
let hasilBagi = angka / pembagi;
console.log(hasilBagi); // Output: Infinity
```

**Perhatian Khusus**: Pembagian dengan nol di JavaScript menghasilkan `Infinity`, bukan error. Ini perlu diperhatikan dalam logika program.

##### Contoh Praktis: Menghitung Rata-rata

```javascript
// Menghitung rata-rata nilai ujian
const nilai1 = 85;
const nilai2 = 92;
const nilai3 = 78;
const nilai4 = 90;

// Cara 1: Langsung
const rataRata1 = (nilai1 + nilai2 + nilai3 + nilai4) / 4;
console.log("Rata-rata (cara 1):", rataRata1); // Output: 86.25

// Cara 2: Bertahap
const totalNilai = nilai1 + nilai2 + nilai3 + nilai4;
const jumlahMataPelajaran = 4;
const rataRata2 = totalNilai / jumlahMataPelajaran;
console.log("Rata-rata (cara 2):", rataRata2); // Output: 86.25
```

##### Tips Penting:
1. **Urutan Operasi**: JavaScript mengikuti aturan matematika (BODMAS/PEMDAS)
   ```javascript
   let hasil = 10 + 5 * 2; // Perkalian dulu, lalu penjumlahan
   console.log(hasil); // Output: 20 (bukan 30)
   
   // Gunakan tanda kurung untuk mengubah urutan
   let hasil2 = (10 + 5) * 2;
   console.log(hasil2); // Output: 30
   ```

2. **Hati-hati dengan Tipe Data**: Pastikan kedua operand adalah Number
   ```javascript
   let benar = 5 + 3;      // Output: 8 (Number)
   let salah = "5" + 3;    // Output: "53" (String)
   let betul = Number("5") + 3; // Output: 8 (Number)
   ```

#### Operator Perbandingan

Operator perbandingan digunakan untuk membandingkan dua nilai dan menghasilkan nilai Boolean (`true` atau `false`). Operator ini sangat penting dalam pemrograman untuk membuat keputusan dan kondisi.

##### 1. Operator Sama Dengan (==) ⚖️
Memeriksa apakah dua nilai sama, **tanpa memperhatikan tipe data** (type coercion).

```javascript
let a = 5;
let b = "5";

console.log(a == b);     // Output: true (JavaScript mengubah "5" menjadi 5)
console.log(10 == 10);   // Output: true
console.log(5 == 3);     // Output: false

// Contoh dengan tipe data berbeda
console.log(true == 1);  // Output: true (true diubah menjadi 1)
console.log(false == 0); // Output: true (false diubah menjadi 0)
console.log(null == undefined); // Output: true
```

##### 2. Operator Sama Identik (===) 🎯
Memeriksa apakah dua nilai sama **dengan memperhatikan tipe data** (strict equality).

```javascript
let a = 5;
let b = "5";

console.log(a === b);    // Output: false (Number vs String)
console.log(5 === 5);    // Output: true (sama nilai dan tipe)
console.log("5" === "5"); // Output: true (sama nilai dan tipe)

// Perbandingan dengan ==
console.log(true === 1); // Output: false (Boolean vs Number)
console.log(null === undefined); // Output: false (berbeda tipe)
```

**Rekomendasi**: Selalu gunakan `===` kecuali ada alasan khusus untuk menggunakan `==`.

##### 3. Operator Tidak Sama (!=) ❌
Memeriksa apakah dua nilai **tidak sama**, tanpa memperhatikan tipe data.

```javascript
let x = 10;
let y = "10";

console.log(x != y);     // Output: false (karena 10 == "10" adalah true)
console.log(5 != 3);     // Output: true
console.log(true != 1);  // Output: false (karena true == 1 adalah true)
```

##### 4. Operator Tidak Identik (!==) 🚫
Memeriksa apakah dua nilai **tidak sama** dengan memperhatikan tipe data.

```javascript
let x = 10;
let y = "10";

console.log(x !== y);    // Output: true (Number vs String)
console.log(5 !== 5);    // Output: false
console.log(true !== 1); // Output: true (Boolean vs Number)
```

##### 5. Operator Lebih Besar (>) 📈
Memeriksa apakah nilai kiri lebih besar dari nilai kanan.

```javascript
let skor1 = 85;
let skor2 = 70;

console.log(skor1 > skor2);  // Output: true
console.log(10 > 20);        // Output: false
console.log(15 > 15);        // Output: false (sama, bukan lebih besar)

// Dengan string (perbandingan leksikografis/alfabetis)
console.log("b" > "a");      // Output: true
console.log("apple" > "banana"); // Output: false
```

##### 6. Operator Lebih Kecil (<) 📉
Memeriksa apakah nilai kiri lebih kecil dari nilai kanan.

```javascript
let umur1 = 17;
let umur2 = 25;

console.log(umur1 < umur2);  // Output: true
console.log(30 < 20);        // Output: false
console.log(15 < 15);        // Output: false
```

##### 7. Operator Lebih Besar atau Sama (>=) 📊
Memeriksa apakah nilai kiri lebih besar atau sama dengan nilai kanan.

```javascript
let nilaiMinimal = 70;
let nilaiSiswa = 85;

console.log(nilaiSiswa >= nilaiMinimal); // Output: true (lulus)
console.log(60 >= 70);                   // Output: false
console.log(70 >= 70);                   // Output: true (sama juga diterima)
```

##### 8. Operator Lebih Kecil atau Sama (<=) 📋
Memeriksa apakah nilai kiri lebih kecil atau sama dengan nilai kanan.

```javascript
let batasKecepatan = 60;
let kecepatanMobil = 55;

console.log(kecepatanMobil <= batasKecepatan); // Output: true (tidak melanggar)
console.log(80 <= 60);                         // Output: false
console.log(60 <= 60);                         // Output: true
```

##### Contoh Praktis: Sistem Penilaian

```javascript
// Sistem penilaian ujian
const nilaiUjian = 85;
const nilaiMinimalLulus = 70;
const nilaiMaksimal = 100;

// Cek apakah lulus
const lulus = nilaiUjian >= nilaiMinimalLulus;
console.log("Lulus:", lulus); // Output: Lulus: true

// Cek apakah nilai sempurna
const nilaiSempurna = nilaiUjian === nilaiMaksimal;
console.log("Nilai Sempurna:", nilaiSempurna); // Output: Nilai Sempurna: false

// Cek apakah nilai valid
const nilaiValid = nilaiUjian >= 0 && nilaiUjian <= nilaiMaksimal;
console.log("Nilai Valid:", nilaiValid); // Output: Nilai Valid: true
```

##### Tips Penting untuk Operator Perbandingan:

1. **Selalu Gunakan === dan !==**: Hindari masalah type coercion
   ```javascript
   // Hindari ini
   if (nilai == "100") { ... }
   
   // Lebih baik ini
   if (nilai === 100) { ... }
   ```

2. **Hati-hati dengan Perbandingan String**:
   ```javascript
   console.log("10" > "2");     // Output: false (perbandingan string, bukan angka)
   console.log("10" > "02");    // Output: true
   console.log(Number("10") > Number("2")); // Output: true (konversi ke number)
   ```

3. **Perbandingan dengan null dan undefined**:
   ```javascript
   console.log(null == undefined);  // Output: true
   console.log(null === undefined); // Output: false
   console.log(null > 0);           // Output: false
   console.log(null >= 0);          // Output: true (aneh tapi benar!)
   ```

4. **Operator Perbandingan Menghasilkan Boolean**:
   ```javascript
   let hasil = 5 > 3;
   console.log(typeof hasil); // Output: "boolean"
   console.log(hasil);        // Output: true
   ```

#### Operator Logika

Operator logika digunakan untuk menggabungkan atau memodifikasi nilai Boolean (`true` dan `false`). Operator ini sangat penting dalam membuat kondisi yang kompleks dan logika pengambilan keputusan.

##### 1. Operator AND (&&) 🤝
Operator AND mengembalikan `true` hanya jika **kedua** kondisi bernilai `true`. Jika salah satu atau keduanya `false`, maka hasilnya `false`.

**Tabel Kebenaran AND:**
```
true  && true  = true
true  && false = false
false && true  = false
false && false = false
```

**Contoh Penggunaan:**
```javascript
// Contoh sederhana
let kondisi1 = true;
let kondisi2 = true;
console.log(kondisi1 && kondisi2); // Output: true

let kondisi3 = true;
let kondisi4 = false;
console.log(kondisi3 && kondisi4); // Output: false

// Contoh praktis: Validasi login
let usernameBenar = true;
let passwordBenar = true;
let bisaLogin = usernameBenar && passwordBenar;
console.log("Bisa login:", bisaLogin); // Output: Bisa login: true

// Contoh dengan perbandingan
let umur = 20;
let punyaKTP = true;
let bisaDaftar = (umur >= 17) && punyaKTP;
console.log("Bisa daftar:", bisaDaftar); // Output: Bisa daftar: true
```

**Short-Circuit Evaluation:**
Operator `&&` berhenti mengevaluasi begitu menemukan nilai `false` pertama.

```javascript
let a = false;
let b = (10 / 0); // Ini tidak akan dievaluasi karena a sudah false
console.log(a && b); // Output: false

// Contoh praktis short-circuit
let user = null;
let name = user && user.name; // Tidak error meski user adalah null
console.log(name); // Output: null
```

##### 2. Operator OR (||) 🔀
Operator OR mengembalikan `true` jika **minimal satu** kondisi bernilai `true`. Hanya mengembalikan `false` jika kedua kondisi `false`.

**Tabel Kebenaran OR:**
```
true  || true  = true
true  || false = true
false || true  = true
false || false = false
```

**Contoh Penggunaan:**
```javascript
// Contoh sederhana
let kondisi1 = false;
let kondisi2 = true;
console.log(kondisi1 || kondisi2); // Output: true

let kondisi3 = false;
let kondisi4 = false;
console.log(kondisi3 || kondisi4); // Output: false

// Contoh praktis: Sistem diskon
let memberVIP = false;
let belanjaDiatas500k = true;
let dapatDiskon = memberVIP || belanjaDiatas500k;
console.log("Dapat diskon:", dapatDiskon); // Output: Dapat diskon: true

// Contoh dengan perbandingan
let hari = "Sabtu";
let libur = (hari === "Sabtu") || (hari === "Minggu");
console.log("Hari libur:", libur); // Output: Hari libur: true
```

**Short-Circuit Evaluation:**
Operator `||` berhenti mengevaluasi begitu menemukan nilai `true` pertama.

```javascript
let a = true;
let b = (10 / 0); // Ini tidak akan dievaluasi karena a sudah true
console.log(a || b); // Output: true

// Contoh praktis: Default value
let namaUser = null;
let tampilkanNama = namaUser || "Pengguna Anonim";
console.log(tampilkanNama); // Output: "Pengguna Anonim"
```

##### 3. Operator NOT (!) 🔄
Operator NOT membalik nilai Boolean. `true` menjadi `false`, dan `false` menjadi `true`.

**Tabel Kebenaran NOT:**
```
!true  = false
!false = true
```

**Contoh Penggunaan:**
```javascript
// Contoh sederhana
let kondisi = true;
console.log(!kondisi); // Output: false

let kondisi2 = false;
console.log(!kondisi2); // Output: true

// Contoh praktis: Status lampu
let lampuMenyala = true;
let lampuMati = !lampuMenyala;
console.log("Lampu mati:", lampuMati); // Output: Lampu mati: false

// Contoh dengan perbandingan
let umur = 16;
let belumDewasa = !(umur >= 18);
console.log("Belum dewasa:", belumDewasa); // Output: Belum dewasa: true

// Double NOT untuk konversi ke Boolean
let nilai = "Hello";
console.log(!!nilai); // Output: true (string non-kosong = truthy)

let nilaiKosong = "";
console.log(!!nilaiKosong); // Output: false (string kosong = falsy)
```

##### Contoh Praktis Kombinasi: Sistem Keamanan

```javascript
// Sistem keamanan gedung
const jamSekarang = 14; // 14:00 (2 siang)
const punyaKartuAkses = true;
const isEmployee = true;
const isWeekend = false;

// Aturan akses:
// 1. Harus punya kartu akses DAN karyawan
// 2. Jam kerja (8-17) ATAU bukan weekend
const jamKerja = (jamSekarang >= 8) && (jamSekarang <= 17);
const bolehMasuk = punyaKartuAkses && isEmployee && (jamKerja || !isWeekend);

console.log("jam kerja:", jamKerja);           // Output: jam kerja: true
console.log("Boleh masuk:", bolehMasuk);      // Output: Boleh masuk: true

// Scenario 2: Malam hari
const jamMalam = 20;
const jamKerjaMalam = (jamMalam >= 8) && (jamMalam <= 17);
const bolehMasukMalam = punyaKartuAkses && isEmployee && (jamKerjaMalam || !isWeekend);

console.log("Jam kerja malam:", jamKerjaMalam);        // Output: Jam kerja malam: false
console.log("Boleh masuk malam:", bolehMasukMalam);   // Output: Boleh masuk malam: true (karena !isWeekend = true)
```

##### Nilai Truthy dan Falsy

JavaScript memiliki konsep nilai yang dianggap `true` (truthy) atau `false` (falsy) dalam konteks Boolean:

**Nilai Falsy:**
```javascript
console.log(!false);      // true
console.log(!0);          // true
console.log(!"");         // true (string kosong)
console.log(!null);       // true
console.log(!undefined);  // true
console.log(!NaN);        // true
```

**Nilai Truthy (semua selain falsy):**
```javascript
console.log(!true);       // false
console.log(!1);          // false
console.log(!"hello");    // false (string tidak kosong)
console.log(!42);         // false (angka selain 0)
console.log(!{});         // false (object)
console.log(![]);         // false (array)
```

##### Tips Penting untuk Operator Logika:

1. **Gunakan Kurung untuk Kejelasan:**
   ```javascript
   // Tidak jelas
   let hasil = a && b || c && d;
   
   // Lebih jelas
   let hasil = (a && b) || (c && d);
   ```

2. **Manfaatkan Short-Circuit Evaluation:**
   ```javascript
   // Hindari error dengan &&
   let user = getUser();
   let name = user && user.name && user.name.toUpperCase();
   
   // Set default value dengan ||
   let config = getUserConfig() || getDefaultConfig();
   ```

3. **Kombinasi dengan Operator Perbandingan:**
   ```javascript
   let nilai = 85;
   let lulus = (nilai >= 70) && (nilai <= 100);
   let nilaiA = (nilai >= 90) || (nilai === 100);
   ```

4. **Hati-hati dengan Precedence (Urutan Operasi):**
   ```javascript
   // && memiliki prioritas lebih tinggi dari ||
   console.log(true || false && false); // Output: true (sama seperti true || (false && false))
   console.log((true || false) && false); // Output: false
   ```

## Logika dan Struktur Kontrol

Setelah mempelajari operator perbandingan dan logika, sekarang kita akan belajar bagaimana menggunakan operator tersebut untuk mengontrol alur program. Struktur kontrol memungkinkan program untuk membuat keputusan dan mengulangi tindakan berdasarkan kondisi tertentu.

### Conditional (Percabangan) 🌿

Conditional atau percabangan memungkinkan program untuk menjalankan kode yang berbeda berdasarkan kondisi tertentu. Seperti kehidupan sehari-hari, kita sering membuat keputusan "jika ini, maka itu".

#### 1. Statement if

Statement `if` adalah struktur percabangan paling dasar. Kode di dalam blok `if` hanya akan dijalankan jika kondisi bernilai `true`.

**Sintaks:**
```javascript
if (kondisi) {
    // Kode yang dijalankan jika kondisi true
}
```

**Contoh:**
```javascript
let umur = 18;

if (umur >= 18) {
    console.log("Anda sudah dewasa");
}
// Output: "Anda sudah dewasa"

let cuaca = "hujan";
if (cuaca === "hujan") {
    console.log("Bawa payung!");
}
// Output: "Bawa payung!"
```

#### 2. Statement if...else

Statement `if...else` memberikan pilihan alternatif jika kondisi `if` bernilai `false`.

**Sintaks:**
```javascript
if (kondisi) {
    // Kode jika kondisi true
} else {
    // Kode jika kondisi false
}
```

**Contoh:**
```javascript
let nilai = 75;

if (nilai >= 70) {
    console.log("Selamat! Anda lulus");
} else {
    console.log("Maaf, Anda belum lulus");
}
// Output: "Selamat! Anda lulus"

let jam = 20;
if (jam < 18) {
    console.log("Selamat siang!");
} else {
    console.log("Selamat malam!");
}
// Output: "Selamat malam!"
```

#### 3. Statement if...else if...else

Untuk kondisi yang lebih kompleks dengan beberapa kemungkinan, kita gunakan `else if`.

**Sintaks:**
```javascript
if (kondisi1) {
    // Kode jika kondisi1 true
} else if (kondisi2) {
    // Kode jika kondisi2 true
} else if (kondisi3) {
    // Kode jika kondisi3 true
} else {
    // Kode jika semua kondisi false
}
```

**Contoh:**
```javascript
let nilai = 85;

if (nilai >= 90) {
    console.log("Grade A - Excellent!");
} else if (nilai >= 80) {
    console.log("Grade B - Good!");
} else if (nilai >= 70) {
    console.log("Grade C - Satisfactory");
} else if (nilai >= 60) {
    console.log("Grade D - Needs Improvement");
} else {
    console.log("Grade F - Failed");
}
// Output: "Grade B - Good!"
```

#### 4. Statement switch

Statement `switch` digunakan ketika kita perlu membandingkan satu variabel dengan banyak nilai yang mungkin.

**Sintaks:**
```javascript
switch (variabel) {
    case nilai1:
        // Kode jika variabel === nilai1
        break;
    case nilai2:
        // Kode jika variabel === nilai2
        break;
    default:
        // Kode jika tidak ada case yang cocok
}
```

**Contoh:**
```javascript
let hari = "Senin";

switch (hari) {
    case "Senin":
        console.log("Awal pekan, semangat!");
        break;
    case "Selasa":
        console.log("Hari ke-2, tetap semangat!");
        break;
    case "Rabu":
        console.log("Pertengahan pekan!");
        break;
    case "Kamis":
        console.log("Hampir weekend!");
        break;
    case "Jumat":
        console.log("TGIF - Thank God It's Friday!");
        break;
    case "Sabtu":
    case "Minggu":
        console.log("Weekend! Saatnya istirahat");
        break;
    default:
        console.log("Hari tidak valid");
}
// Output: "Awal pekan, semangat!"
```

**Contoh Praktis: Kalkulator Sederhana**
```javascript
let operasi = "+";
let angka1 = 10;
let angka2 = 5;
let hasil;

switch (operasi) {
    case "+":
        hasil = angka1 + angka2;
        console.log(`${angka1} + ${angka2} = ${hasil}`);
        break;
    case "-":
        hasil = angka1 - angka2;
        console.log(`${angka1} - ${angka2} = ${hasil}`);
        break;
    case "*":
        hasil = angka1 * angka2;
        console.log(`${angka1} * ${angka2} = ${hasil}`);
        break;
    case "/":
        if (angka2 !== 0) {
            hasil = angka1 / angka2;
            console.log(`${angka1} / ${angka2} = ${hasil}`);
        } else {
            console.log("Error: Tidak bisa membagi dengan nol!");
        }
        break;
    default:
        console.log("Operasi tidak dikenal");
}
// Output: "10 + 5 = 15"
```

#### 5. Ternary Operator (Conditional Operator)

Ternary operator adalah cara singkat untuk menulis `if...else` dalam satu baris.

**Sintaks:**
```javascript
kondisi ? nilaiJikaTrue : nilaiJikaFalse
```

**Contoh:**
```javascript
let umur = 17;
let status = umur >= 18 ? "Dewasa" : "Belum Dewasa";
console.log(status); // Output: "Belum Dewasa"

// Dibandingkan dengan if...else
let umur2 = 20;
let status2;
if (umur2 >= 18) {
    status2 = "Dewasa";
} else {
    status2 = "Belum Dewasa";
}
console.log(status2); // Output: "Dewasa"

// Ternary bersarang (hati-hati, bisa membingungkan)
let nilai = 85;
let grade = nilai >= 90 ? "A" : nilai >= 80 ? "B" : nilai >= 70 ? "C" : "D";
console.log(grade); // Output: "B"
```

### Looping (Perulangan) 🔄

Looping atau perulangan memungkinkan kita menjalankan blok kode berulang kali selama kondisi tertentu terpenuhi. Ini sangat berguna untuk tugas-tugas repetitif.

#### 1. For Loop

`For loop` adalah jenis perulangan yang paling umum digunakan ketika kita tahu berapa kali perulangan akan dilakukan.

**Sintaks:**
```javascript
for (inisialisasi; kondisi; increment/decrement) {
    // Kode yang akan diulang
}
```

**Komponen for loop:**
- **Inisialisasi**: Menentukan nilai awal variabel counter
- **Kondisi**: Kondisi yang harus dipenuhi untuk melanjutkan loop
- **Increment/Decrement**: Mengubah nilai counter setiap iterasi

**Contoh Dasar:**
```javascript
// Menampilkan angka 1 sampai 5
for (let i = 1; i <= 5; i++) {
    console.log("Angka:", i);
}
// Output:
// Angka: 1
// Angka: 2
// Angka: 3
// Angka: 4
// Angka: 5

// Menampilkan angka genap 2 sampai 10
for (let i = 2; i <= 10; i += 2) {
    console.log("Angka genap:", i);
}
// Output: 2, 4, 6, 8, 10
```

**Contoh Praktis:**
```javascript
// Menghitung faktorial
let n = 5;
let faktorial = 1;

for (let i = 1; i <= n; i++) {
    faktorial *= i;
    console.log(`${i}! = ${faktorial}`);
}
console.log(`Faktorial ${n} = ${faktorial}`);

// Membuat pola bintang
for (let i = 1; i <= 5; i++) {
    let bintang = "";
    for (let j = 1; j <= i; j++) {
        bintang += "*";
    }
    console.log(bintang);
}
// Output:
// *
// **
// ***
// ****
// *****
```

#### 2. While Loop

`While loop` digunakan ketika kita tidak tahu pasti berapa kali perulangan akan dilakukan, tetapi kita tahu kondisi kapan perulangan harus berhenti.

**Sintaks:**
```javascript
while (kondisi) {
    // Kode yang akan diulang
    // Jangan lupa update kondisi agar tidak infinite loop!
}
```

**Contoh:**
```javascript
// Menampilkan angka 1 sampai 5
let i = 1;
while (i <= 5) {
    console.log("Angka:", i);
    i++; // Sangat penting! Tanpa ini = infinite loop
}

// Contoh dengan input pengguna (simulasi)
let password = "";
let attempts = 0;
const correctPassword = "secret123";

while (password !== correctPassword && attempts < 3) {
    // Simulasi input password
    password = attempts === 0 ? "wrong1" : 
               attempts === 1 ? "wrong2" : "secret123";
    
    attempts++;
    
    if (password === correctPassword) {
        console.log("Login berhasil!");
    } else {
        console.log(`Password salah. Sisa percobaan: ${3 - attempts}`);
    }
}

if (attempts >= 3 && password !== correctPassword) {
    console.log("Akun terkunci!");
}
```

**Contoh Praktis: Mencari Bilangan Prima**
```javascript
function isPrime(num) {
    if (num < 2) return false;
    
    let i = 2;
    while (i * i <= num) {
        if (num % i === 0) {
            return false;
        }
        i++;
    }
    return true;
}

let angka = 17;
if (isPrime(angka)) {
    console.log(`${angka} adalah bilangan prima`);
} else {
    console.log(`${angka} bukan bilangan prima`);
}
// Output: "17 adalah bilangan prima"
```

#### 3. Do...While Loop

`Do...while loop` mirip dengan `while loop`, tetapi kode di dalam loop akan dijalankan **minimal satu kali** sebelum kondisi diperiksa.

**Sintaks:**
```javascript
do {
    // Kode yang akan diulang
    // Dijalankan minimal satu kali
} while (kondisi);
```

**Contoh:**
```javascript
// Perbedaan while vs do-while
console.log("=== While Loop ===");
let i = 10;
while (i < 10) {
    console.log("Ini tidak akan ditampilkan");
    i++;
}

console.log("=== Do-While Loop ===");
let j = 10;
do {
    console.log("Ini akan ditampilkan sekali meski kondisi false");
    j++;
} while (j < 10);

// Contoh praktis: Menu program
let pilihan;
do {
    console.log("\n=== MENU UTAMA ===");
    console.log("1. Lihat Data");
    console.log("2. Tambah Data");
    console.log("3. Hapus Data");
    console.log("4. Keluar");
    
    // Simulasi input pengguna
    pilihan = Math.floor(Math.random() * 4) + 1; // Random 1-4
    console.log(`Pilihan Anda: ${pilihan}`);
    
    switch (pilihan) {
        case 1:
            console.log("Menampilkan data...");
            break;
        case 2:
            console.log("Menambah data...");
            break;
        case 3:
            console.log("Menghapus data...");
            break;
        case 4:
            console.log("Terima kasih!");
            break;
        default:
            console.log("Pilihan tidak valid!");
    }
} while (pilihan !== 4);
```

#### Control Statements dalam Loop

**1. Break Statement**
Menghentikan loop secara paksa.

```javascript
// Mencari angka tertentu
for (let i = 1; i <= 10; i++) {
    if (i === 6) {
        console.log("Angka 6 ditemukan! Menghentikan loop...");
        break;
    }
    console.log(i);
}
// Output: 1, 2, 3, 4, 5, "Angka 6 ditemukan! Menghentikan loop..."
```

**2. Continue Statement**
Melompati iterasi saat ini dan lanjut ke iterasi berikutnya.

```javascript
// Menampilkan hanya angka ganjil
for (let i = 1; i <= 10; i++) {
    if (i % 2 === 0) {
        continue; // Lewati angka genap
    }
    console.log("Angka ganjil:", i);
}
// Output: 1, 3, 5, 7, 9
```

#### Tips Penting untuk Looping:

1. **Hindari Infinite Loop:**
   ```javascript
   // JANGAN seperti ini!
   // while (true) {
   //     console.log("Loop tak terbatas!");
   // }
   
   // Pastikan kondisi bisa berubah
   let counter = 0;
   while (counter < 5) {
       console.log(counter);
       counter++; // Ini penting!
   }
   ```

2. **Pilih Loop yang Tepat:**
   - `for`: Ketika tahu jumlah iterasi
   - `while`: Ketika kondisi berhenti tidak pasti
   - `do-while`: Ketika perlu eksekusi minimal satu kali

3. **Performance Considerations:**
   ```javascript
   // Kurang efisien
   for (let i = 0; i < array.length; i++) {
       // array.length dihitung setiap iterasi
   }
   
   // Lebih efisien
   const len = array.length;
   for (let i = 0; i < len; i++) {
       // len sudah tersimpan
   }
   ```

4. **Nested Loops (Loop Bersarang):**
   ```javascript
   // Hati-hati dengan kompleksitas
   for (let i = 0; i < 3; i++) {
       for (let j = 0; j < 3; j++) {
           console.log(`i=${i}, j=${j}`);
       }
   }
   // Total iterasi: 3 × 3 = 9 kali
   ```

## Struktur Data Inti

Struktur data adalah cara untuk mengorganisir dan menyimpan data dalam program. JavaScript memiliki dua struktur data utama yang sangat penting: **Array** dan **Object**. Kedua struktur ini memungkinkan kita menyimpan multiple data dalam satu variabel.

### Array 

Array adalah struktur data yang menyimpan kumpulan data dalam urutan tertentu (berindeks). Bayangkan array seperti daftar atau list yang setiap itemnya memiliki nomor urut (index) mulai dari 0.

#### 1. Membuat Array

**Cara 1: Array Literal (Disarankan)**
```javascript
// Array kosong
let arrayKosong = [];

// Array dengan data
let buah = ["apel", "jeruk", "mangga", "pisang"];
let angka = [1, 2, 3, 4, 5];
let campuran = ["nama", 25, true, null];

console.log(buah);    // Output: ["apel", "jeruk", "mangga", "pisang"]
console.log(angka);   // Output: [1, 2, 3, 4, 5]
```

**Cara 2: Array Constructor**
```javascript
let arrayBaru = new Array();           // Array kosong
let arrayDenganSize = new Array(5);    // Array dengan 5 elemen kosong
let arrayDenganData = new Array(1, 2, 3); // Array dengan data [1, 2, 3]

console.log(arrayDenganSize); // Output: [empty × 5]
```

#### 2. Mengakses Elemen Array

Array menggunakan **index** (dimulai dari 0) untuk mengakses elemen.

```javascript
let warna = ["merah", "hijau", "biru", "kuning"];

console.log(warna[0]);  // Output: "merah" (elemen pertama)
console.log(warna[1]);  // Output: "hijau" (elemen kedua)
console.log(warna[3]);  // Output: "kuning" (elemen keempat)
console.log(warna[10]); // Output: undefined (index tidak ada)

// Mengakses elemen terakhir
let indexTerakhir = warna.length - 1;
console.log(warna[indexTerakhir]); // Output: "kuning"
```

#### 3. Properti dan Method Array Penting

**Length Property**
```javascript
let hobi = ["membaca", "coding", "gaming"];
console.log(hobi.length); // Output: 3

// Menggunakan length untuk loop
for (let i = 0; i < hobi.length; i++) {
    console.log(`Hobi ${i + 1}: ${hobi[i]}`);
}
```

**Method Menambah Elemen:**

```javascript
let makanan = ["nasi", "ayam"];

// push() - menambah di akhir
makanan.push("sayur");
console.log(makanan); // Output: ["nasi", "ayam", "sayur"]

// unshift() - menambah di awal
makanan.unshift("kerupuk");
console.log(makanan); // Output: ["kerupuk", "nasi", "ayam", "sayur"]

// Menambah multiple elemen
makanan.push("buah", "es krim");
console.log(makanan); // Output: ["kerupuk", "nasi", "ayam", "sayur", "buah", "es krim"]
```

**Method Menghapus Elemen:**

```javascript
let angka = [1, 2, 3, 4, 5];

// pop() - menghapus elemen terakhir
let terakhir = angka.pop();
console.log(terakhir); // Output: 5
console.log(angka);    // Output: [1, 2, 3, 4]

// shift() - menghapus elemen pertama
let pertama = angka.shift();
console.log(pertama); // Output: 1
console.log(angka);   // Output: [2, 3, 4]

// splice() - menghapus elemen di posisi tertentu
angka.splice(1, 1); // Hapus 1 elemen mulai dari index 1
console.log(angka); // Output: [2, 4]
```

**Method Pencarian:**

```javascript
let hewan = ["kucing", "anjing", "burung", "ikan", "anjing"];

// indexOf() - mencari index pertama
console.log(hewan.indexOf("burung")); // Output: 2
console.log(hewan.indexOf("gajah"));  // Output: -1 (tidak ditemukan)

// includes() - mengecek keberadaan
console.log(hewan.includes("kucing")); // Output: true
console.log(hewan.includes("gajah"));  // Output: false

// lastIndexOf() - mencari index terakhir
console.log(hewan.lastIndexOf("anjing")); // Output: 4
```

#### 4. Looping Array

**Dengan For Loop Traditional:**
```javascript
let nilai = [85, 90, 78, 92, 88];

for (let i = 0; i < nilai.length; i++) {
    console.log(`Nilai ${i + 1}: ${nilai[i]}`);
}
```

**Dengan For...of Loop (ES6):**
```javascript
let buah = ["apel", "jeruk", "mangga"];

for (let item of buah) {
    console.log(`Buah: ${item}`);
}
```

**Dengan forEach Method:**
```javascript
let kota = ["Jakarta", "Surabaya", "Bandung"];

kota.forEach(function(nama, index) {
    console.log(`${index + 1}. ${nama}`);
});

// Dengan arrow function
kota.forEach((nama, index) => {
    console.log(`${index + 1}. ${nama}`);
});
```

#### 5. Contoh Praktis Array

**Sistem Daftar Belanja:**
```javascript
let daftarBelanja = [];

// Menambah item
function tambahItem(item) {
    daftarBelanja.push(item);
    console.log(`✅ ${item} ditambahkan ke daftar belanja`);
}

// Menghapus item
function hapusItem(item) {
    let index = daftarBelanja.indexOf(item);
    if (index !== -1) {
        daftarBelanja.splice(index, 1);
        console.log(`❌ ${item} dihapus dari daftar belanja`);
    } else {
        console.log(`⚠️ ${item} tidak ditemukan dalam daftar`);
    }
}

// Menampilkan daftar
function tampilkanDaftar() {
    console.log("\n📋 DAFTAR BELANJA:");
    if (daftarBelanja.length === 0) {
        console.log("Daftar kosong");
    } else {
        daftarBelanja.forEach((item, index) => {
            console.log(`${index + 1}. ${item}`);
        });
    }
}

// Penggunaan
tambahItem("Roti");
tambahItem("Susu");
tambahItem("Telur");
tampilkanDaftar();
hapusItem("Susu");
tampilkanDaftar();
```

### Object 

Object adalah struktur data yang menyimpan data dalam format **key-value pairs** (pasangan kunci-nilai). Object sangat berguna untuk merepresentasikan entitas dengan berbagai atribut.

#### 1. Membuat Object

**Cara 1: Object Literal (Disarankan)**
```javascript
// Object kosong
let objectKosong = {};

// Object dengan data
let mahasiswa = {
    nama: "Budi Santoso",
    umur: 20,
    jurusan: "Informatika",
    aktif: true,
    hobi: ["coding", "gaming", "membaca"]
};

console.log(mahasiswa);
```

**Cara 2: Object Constructor**
```javascript
let mobil = new Object();
mobil.merek = "Toyota";
mobil.model = "Avanza";
mobil.tahun = 2023;

console.log(mobil);
```

#### 2. Mengakses Property Object

**Dot Notation (Titik):**
```javascript
let siswa = {
    nama: "Ana",
    kelas: "12A",
    nilai: 85
};

console.log(siswa.nama);  // Output: "Ana"
console.log(siswa.kelas); // Output: "12A"
console.log(siswa.nilai); // Output: 85
```

**Bracket Notation (Kurung Siku):**
```javascript
let produk = {
    "nama produk": "Laptop Gaming",
    "harga": 15000000,
    "stok": 5
};

console.log(produk["nama produk"]); // Output: "Laptop Gaming"
console.log(produk["harga"]);       // Output: 15000000

// Menggunakan variabel sebagai key
let properti = "stok";
console.log(produk[properti]);      // Output: 5
```

#### 3. Menambah, Mengubah, dan Menghapus Property

```javascript
let pengguna = {
    username: "john_doe",
    email: "john@email.com"
};

// Menambah property baru
pengguna.umur = 25;
pengguna["negara"] = "Indonesia";

console.log(pengguna);
// Output: { username: "john_doe", email: "john@email.com", umur: 25, negara: "Indonesia" }

// Mengubah property yang ada
pengguna.email = "john.doe@gmail.com";
pengguna["umur"] = 26;

console.log(pengguna);

// Menghapus property
delete pengguna.negara;
console.log(pengguna);
// Output: { username: "john_doe", email: "john.doe@gmail.com", umur: 26 }
```

#### 4. Method dalam Object

Object bisa memiliki function sebagai nilai property, yang disebut **method**.

```javascript
let kalkulator = {
    hasil: 0,
    
    tambah: function(angka) {
        this.hasil += angka;
        return this;
    },
    
    kurang: function(angka) {
        this.hasil -= angka;
        return this;
    },
    
    kali: function(angka) {
        this.hasil *= angka;
        return this;
    },
    
    bagi: function(angka) {
        if (angka !== 0) {
            this.hasil /= angka;
        } else {
            console.log("Error: Tidak bisa membagi dengan nol!");
        }
        return this;
    },
    
    reset: function() {
        this.hasil = 0;
        return this;
    },
    
    tampilkan: function() {
        console.log(`Hasil: ${this.hasil}`);
        return this;
    }
};

// Penggunaan (method chaining)
kalkulator
    .tambah(10)
    .kali(2)
    .kurang(5)
    .tampilkan(); // Output: Hasil: 15
```

#### 5. Looping Object

**For...in Loop:**
```javascript
let biodata = {
    nama: "Sarah",
    umur: 23,
    pekerjaan: "Developer",
    kota: "Jakarta"
};

for (let key in biodata) {
    console.log(`${key}: ${biodata[key]}`);
}
// Output:
// nama: Sarah
// umur: 23
// pekerjaan: Developer
// kota: Jakarta
```

**Object Methods untuk Looping:**
```javascript
let smartphone = {
    merek: "Samsung",
    model: "Galaxy S23",
    ram: "8GB",
    storage: "256GB"
};

// Object.keys() - mendapat array keys
console.log(Object.keys(smartphone));
// Output: ["merek", "model", "ram", "storage"]

// Object.values() - mendapat array values
console.log(Object.values(smartphone));
// Output: ["Samsung", "Galaxy S23", "8GB", "256GB"]

// Object.entries() - mendapat array [key, value] pairs
console.log(Object.entries(smartphone));
// Output: [["merek", "Samsung"], ["model", "Galaxy S23"], ["ram", "8GB"], ["storage", "256GB"]]

// Menggunakan forEach dengan Object.entries()
Object.entries(smartphone).forEach(([key, value]) => {
    console.log(`${key}: ${value}`);
});
```

#### 6. Nested Objects dan Arrays

**Object di dalam Object:**
```javascript
let perusahaan = {
    nama: "Tech Solutions",
    alamat: {
        jalan: "Jl. Sudirman No. 123",
        kota: "Jakarta",
        kodePos: "12190"
    },
    karyawan: [
        {
            nama: "Alice",
            posisi: "Frontend Developer",
            gaji: 8000000
        },
        {
            nama: "Bob", 
            posisi: "Backend Developer",
            gaji: 9000000
        }
    ]
};

// Mengakses nested data
console.log(perusahaan.nama); // "Tech Solutions"
console.log(perusahaan.alamat.kota); // "Jakarta"
console.log(perusahaan.karyawan[0].nama); // "Alice"
console.log(perusahaan.karyawan[1].gaji); // 9000000
```

#### 7. Contoh Praktis: Sistem Manajemen Buku

```javascript
let perpustakaan = {
    nama: "Perpustakaan Digital",
    buku: [],
    
    tambahBuku: function(judul, penulis, tahun, tersedia = true) {
        let bukuBaru = {
            id: this.buku.length + 1,
            judul: judul,
            penulis: penulis,
            tahun: tahun,
            tersedia: tersedia
        };
        
        this.buku.push(bukuBaru);
        console.log(`✅ Buku "${judul}" berhasil ditambahkan`);
    },
    
    cariBuku: function(judul) {
        return this.buku.find(buku => 
            buku.judul.toLowerCase().includes(judul.toLowerCase())
        );
    },
    
    pinjamBuku: function(judul) {
        let buku = this.cariBuku(judul);
        if (buku) {
            if (buku.tersedia) {
                buku.tersedia = false;
                console.log(`📖 Buku "${buku.judul}" berhasil dipinjam`);
            } else {
                console.log(`❌ Buku "${buku.judul}" sedang dipinjam`);
            }
        } else {
            console.log(`❌ Buku "${judul}" tidak ditemukan`);
        }
    },
    
    kembalikanBuku: function(judul) {
        let buku = this.cariBuku(judul);
        if (buku) {
            if (!buku.tersedia) {
                buku.tersedia = true;
                console.log(`📚 Buku "${buku.judul}" berhasil dikembalikan`);
            } else {
                console.log(`ℹ️ Buku "${buku.judul}" sudah tersedia`);
            }
        } else {
            console.log(`❌ Buku "${judul}" tidak ditemukan`);
        }
    },
    
    daftarBuku: function() {
        console.log(`\n📚 DAFTAR BUKU - ${this.nama}`);
        console.log("=" .repeat(40));
        
        if (this.buku.length === 0) {
            console.log("Tidak ada buku dalam perpustakaan");
        } else {
            this.buku.forEach(buku => {
                let status = buku.tersedia ? "✅ Tersedia" : "❌ Dipinjam";
                console.log(`${buku.id}. ${buku.judul}`);
                console.log(`   Penulis: ${buku.penulis} (${buku.tahun})`);
                console.log(`   Status: ${status}`);
                console.log();
            });
        }
    }
};

// Penggunaan sistem perpustakaan
perpustakaan.tambahBuku("JavaScript: The Good Parts", "Douglas Crockford", 2008);
perpustakaan.tambahBuku("Clean Code", "Robert Martin", 2008);
perpustakaan.tambahBuku("You Don't Know JS", "Kyle Simpson", 2014);

perpustakaan.daftarBuku();
perpustakaan.pinjamBuku("JavaScript");
perpustakaan.pinjamBuku("Clean Code");
perpustakaan.daftarBuku();
perpustakaan.kembalikanBuku("JavaScript");
perpustakaan.daftarBuku();
```

#### 8. Tips Penting untuk Object dan Array

**1. Checking Property Existence:**
```javascript
let user = { nama: "John", umur: 25 };

// Cara yang benar
console.log("email" in user);           // false
console.log(user.hasOwnProperty("nama")); // true
console.log(user.email !== undefined);   // false

// Hati-hati dengan ini
console.log(user.email); // undefined (bukan error)
```

**2. Shallow vs Deep Copy:**
```javascript
let original = { nama: "Alice", hobi: ["coding", "gaming"] };

// Shallow copy
let copy1 = { ...original };
copy1.nama = "Bob";
copy1.hobi.push("reading");

console.log(original.nama); // "Alice" (tidak berubah)
console.log(original.hobi); // ["coding", "gaming", "reading"] (berubah!)

// Deep copy (untuk object sederhana)
let copy2 = JSON.parse(JSON.stringify(original));
```

**3. Performance Considerations:**
```javascript
// Untuk array besar, gunakan cara yang tepat
let largeArray = new Array(1000000).fill(0);

// Lebih cepat
for (let i = 0; i < largeArray.length; i++) {
    // process largeArray[i]
}

// Lebih lambat tapi lebih mudah dibaca
largeArray.forEach(item => {
    // process item
});
```

## Fungsi (Functions) 

Fungsi adalah salah satu konsep terpenting dalam JavaScript. Fungsi adalah blok kode yang dapat digunakan kembali (reusable) untuk menjalankan tugas tertentu. Bayangkan fungsi seperti mesin atau alat yang menerima input, memproses input tersebut, dan menghasilkan output.

### Mengapa Fungsi Penting?

1. **DRY Principle**: Don't Repeat Yourself - menghindari pengulangan kode
2. **Modularitas**: Memecah program besar menjadi bagian-bagian kecil
3. **Maintainability**: Kode lebih mudah dirawat dan diperbaiki
4. **Reusability**: Kode dapat digunakan berulang kali

### Deklarasi Fungsi 📝

Ada beberapa cara untuk mendeklarasikan fungsi dalam JavaScript:

#### 1. Function Declaration (Deklarasi Fungsi)

**Sintaks:**
```javascript
function namaFungsi() {
    // Blok kode fungsi
}
```

**Contoh:**
```javascript
// Fungsi sederhana tanpa parameter
function sapa() {
    console.log("Halo! Selamat datang!");
}

// Memanggil fungsi
sapa(); // Output: "Halo! Selamat datang!"

// Fungsi dengan parameter
function sapaOrang(nama) {
    console.log(`Halo, ${nama}! Selamat datang!`);
}

sapaOrang("Budi"); // Output: "Halo, Budi! Selamat datang!"
sapaOrang("Sari"); // Output: "Halo, Sari! Selamat datang!"
```

#### 2. Function Expression (Ekspresi Fungsi)

**Sintaks:**
```javascript
const namaFungsi = function() {
    // Blok kode fungsi
};
```

**Contoh:**
```javascript
// Anonymous function expression
const hitungLuas = function(panjang, lebar) {
    return panjang * lebar;
};

console.log(hitungLuas(5, 3)); // Output: 15

// Named function expression
const faktorial = function hitungFaktorial(n) {
    if (n <= 1) return 1;
    return n * hitungFaktorial(n - 1);
};

console.log(faktorial(5)); // Output: 120
```

#### 3. Arrow Function (ES6) 🏹

**Sintaks:**
```javascript
const namaFungsi = () => {
    // Blok kode fungsi
};

// Untuk satu baris, bisa ditulis singkat
const namaFungsi = () => expression;
```

**Contoh:**
```javascript
// Arrow function sederhana
const tambah = (a, b) => {
    return a + b;
};

// Arrow function satu baris (implicit return)
const kali = (a, b) => a * b;

// Arrow function dengan satu parameter (kurung opsional)
const kuadrat = x => x * x;

// Arrow function tanpa parameter
const dapatkanWaktu = () => new Date();

// Penggunaan
console.log(tambah(5, 3));      // Output: 8
console.log(kali(4, 6));        // Output: 24
console.log(kuadrat(7));        // Output: 49
console.log(dapatkanWaktu());   // Output: current date object
```

#### Perbedaan Function Declaration vs Expression vs Arrow Function

```javascript
// 1. Hoisting
console.log(fungsiA()); // ✅ Bisa dipanggil sebelum dideklarasikan
// console.log(fungsiB()); // ❌ Error: Cannot access 'fungsiB' before initialization
// console.log(fungsiC()); // ❌ Error: Cannot access 'fungsiC' before initialization

function fungsiA() {
    return "Fungsi A (Declaration) - Hoisted";
}

const fungsiB = function() {
    return "Fungsi B (Expression)";
};

const fungsiC = () => {
    return "Fungsi C (Arrow)";
};

// 2. this binding
const objek = {
    nama: "JavaScript",
    
    // Regular function - this mengacu ke objek
    metodeBiasa: function() {
        console.log(`Ini adalah ${this.nama}`);
    },
    
    // Arrow function - this tidak bound ke objek
    metodeArrow: () => {
        console.log(`Ini adalah ${this.nama}`); // undefined atau global object
    }
};

objek.metodeBiasa(); // Output: "Ini adalah JavaScript"
objek.metodeArrow();  // Output: "Ini adalah undefined"
```

### Parameter Fungsi 📥

Parameter adalah variabel yang didefinisikan dalam fungsi untuk menerima nilai input.

#### 1. Parameter Dasar

```javascript
function perkenalan(nama, umur, pekerjaan) {
    console.log(`Halo, nama saya ${nama}`);
    console.log(`Umur saya ${umur} tahun`);
    console.log(`Saya bekerja sebagai ${pekerjaan}`);
}

perkenalan("Alice", 25, "Developer");
// Output:
// Halo, nama saya Alice
// Umur saya 25 tahun
// Saya bekerja sebagai Developer
```

#### 2. Default Parameters (ES6)

```javascript
function buatProfil(nama, umur = 20, kota = "Jakarta") {
    return {
        nama: nama,
        umur: umur,
        kota: kota
    };
}

console.log(buatProfil("Bob"));                    // { nama: "Bob", umur: 20, kota: "Jakarta" }
console.log(buatProfil("Charlie", 30));            // { nama: "Charlie", umur: 30, kota: "Jakarta" }
console.log(buatProfil("Diana", 25, "Surabaya")); // { nama: "Diana", umur: 25, kota: "Surabaya" }
```

#### 3. Rest Parameters (...args)

```javascript
function jumlahkanSemua(...angka) {
    let total = 0;
    for (let num of angka) {
        total += num;
    }
    return total;
}

console.log(jumlahkanSemua(1, 2, 3));          // Output: 6
console.log(jumlahkanSemua(1, 2, 3, 4, 5));    // Output: 15
console.log(jumlahkanSemua(10, 20));           // Output: 30

// Kombinasi parameter biasa dan rest parameter
function buatKalimat(pembuka, ...kata) {
    return pembuka + " " + kata.join(" ");
}

console.log(buatKalimat("Saya suka", "coding", "dan", "gaming"));
// Output: "Saya suka coding dan gaming"
```

#### 4. Destructuring Parameters

```javascript
// Object destructuring
function tampilkanUser({ nama, email, umur }) {
    console.log(`Nama: ${nama}`);
    console.log(`Email: ${email}`);
    console.log(`Umur: ${umur}`);
}

const user = { nama: "John", email: "john@email.com", umur: 28 };
tampilkanUser(user);

// Array destructuring
function hitungOperasi([a, b], operasi) {
    switch (operasi) {
        case "+": return a + b;
        case "-": return a - b;
        case "*": return a * b;
        case "/": return a / b;
        default: return "Operasi tidak dikenal";
    }
}

console.log(hitungOperasi([10, 5], "+")); // Output: 15
console.log(hitungOperasi([10, 5], "*")); // Output: 50
```

### Return Value 📤

Return statement digunakan untuk mengembalikan nilai dari fungsi dan menghentikan eksekusi fungsi.

#### 1. Return Dasar

```javascript
function tambah(a, b) {
    return a + b; // Mengembalikan hasil penjumlahan
}

let hasil = tambah(5, 3);
console.log(hasil); // Output: 8

// Fungsi tanpa return statement mengembalikan undefined
function cetakPesan(pesan) {
    console.log(pesan);
    // Tidak ada return statement
}

let nilai = cetakPesan("Halo Dunia!"); // Output: "Halo Dunia!"
console.log(nilai); // Output: undefined
```

#### 2. Return Multiple Values

JavaScript tidak mendukung return multiple values secara langsung, tetapi kita bisa menggunakan array atau object:

```javascript
// Return array
function hitungLingkaran(radius) {
    const luas = Math.PI * radius * radius;
    const keliling = 2 * Math.PI * radius;
    
    return [luas, keliling]; // Return array
}

const [luasLingkaran, kelilingLingkaran] = hitungLingkaran(5);
console.log(`Luas: ${luasLingkaran.toFixed(2)}`);         // Luas: 78.54
console.log(`Keliling: ${kelilingLingkaran.toFixed(2)}`); // Keliling: 31.42

// Return object
function analisisNilai(nilaiArray) {
    const total = nilaiArray.reduce((sum, nilai) => sum + nilai, 0);
    const rataRata = total / nilaiArray.length;
    const maksimal = Math.max(...nilaiArray);
    const minimal = Math.min(...nilaiArray);
    
    return {
        total,
        rataRata,
        maksimal,
        minimal,
        jumlahData: nilaiArray.length
    };
}

const nilai = [85, 90, 78, 92, 88];
const analisis = analisisNilai(nilai);
console.log(analisis);
// Output: { total: 433, rataRata: 86.6, maksimal: 92, minimal: 78, jumlahData: 5 }
```

#### 3. Early Return Pattern

```javascript
function validasiUser(user) {
    // Early return jika data tidak valid
    if (!user) {
        return { valid: false, error: "User tidak ditemukan" };
    }
    
    if (!user.nama) {
        return { valid: false, error: "Nama harus diisi" };
    }
    
    if (!user.email || !user.email.includes("@")) {
        return { valid: false, error: "Email tidak valid" };
    }
    
    if (user.umur < 13) {
        return { valid: false, error: "Umur minimal 13 tahun" };
    }
    
    // Jika semua validasi lulus
    return { valid: true, message: "User valid" };
}

// Test validasi
console.log(validasiUser(null));
console.log(validasiUser({ nama: "John" }));
console.log(validasiUser({ nama: "John", email: "john@email.com", umur: 25 }));
```

### Contoh Praktis: Sistem Kalkulator Lengkap

```javascript
const kalkulator = {
    // Operasi dasar
    tambah: (a, b) => a + b,
    kurang: (a, b) => a - b,
    kali: (a, b) => a * b,
    bagi: (a, b) => {
        if (b === 0) {
            throw new Error("Tidak bisa membagi dengan nol!");
        }
        return a / b;
    },
    
    // Operasi lanjutan
    pangkat: (base, exponent) => Math.pow(base, exponent),
    akarKuadrat: (num) => {
        if (num < 0) {
            throw new Error("Tidak bisa akar kuadrat dari angka negatif!");
        }
        return Math.sqrt(num);
    },
    
    // Operasi dengan multiple parameter
    rataRata: (...angka) => {
        if (angka.length === 0) return 0;
        return angka.reduce((sum, num) => sum + num, 0) / angka.length;
    },
    
    // Operasi dengan validasi
    faktorial: function(n) {
        if (n < 0 || !Number.isInteger(n)) {
            throw new Error("Faktorial hanya untuk bilangan bulat non-negatif!");
        }
        if (n === 0 || n === 1) return 1;
        
        let result = 1;
        for (let i = 2; i <= n; i++) {
            result *= i;
        }
        return result;
    },
    
    // Fungsi utilitas
    formatHasil: function(hasil, desimal = 2) {
        return typeof hasil === 'number' ? Number(hasil.toFixed(desimal)) : hasil;
    },
    
    // Fungsi untuk menjalankan operasi
    hitung: function(operasi, ...args) {
        try {
            let hasil;
            
            switch (operasi.toLowerCase()) {
                case 'tambah':
                case '+':
                    hasil = this.tambah(args[0], args[1]);
                    break;
                case 'kurang':
                case '-':
                    hasil = this.kurang(args[0], args[1]);
                    break;
                case 'kali':
                case '*':
                    hasil = this.kali(args[0], args[1]);
                    break;
                case 'bagi':
                case '/':
                    hasil = this.bagi(args[0], args[1]);
                    break;
                case 'pangkat':
                case '^':
                    hasil = this.pangkat(args[0], args[1]);
                    break;
                case 'akar':
                    hasil = this.akarKuadrat(args[0]);
                    break;
                case 'rata-rata':
                    hasil = this.rataRata(...args);
                    break;
                case 'faktorial':
                case '!':
                    hasil = this.faktorial(args[0]);
                    break;
                default:
                    throw new Error(`Operasi '${operasi}' tidak dikenal`);
            }
            
            return {
                sukses: true,
                hasil: this.formatHasil(hasil),
                operasi: operasi,
                input: args
            };
            
        } catch (error) {
            return {
                sukses: false,
                error: error.message,
                operasi: operasi,
                input: args
            };
        }
    }
};

// Contoh penggunaan
console.log(kalkulator.hitung('+', 10, 5));           // { sukses: true, hasil: 15, ... }
console.log(kalkulator.hitung('/', 10, 0));           // { sukses: false, error: "Tidak bisa...", ... }
console.log(kalkulator.hitung('akar', 16));           // { sukses: true, hasil: 4, ... }
console.log(kalkulator.hitung('faktorial', 5));       // { sukses: true, hasil: 120, ... }
console.log(kalkulator.hitung('rata-rata', 1,2,3,4,5)); // { sukses: true, hasil: 3, ... }
```

### Scope dan Closure 🔒

#### 1. Function Scope

```javascript
function luarFungsi() {
    let variabelLuar = "Saya ada di luar";
    
    function dalamFungsi() {
        let variabelDalam = "Saya ada di dalam";
        console.log(variabelLuar);  // ✅ Bisa akses variabel luar
        console.log(variabelDalam); // ✅ Bisa akses variabel dalam
    }
    
    dalamFungsi();
    console.log(variabelLuar);  // ✅ Bisa akses variabel luar
    // console.log(variabelDalam); // ❌ Error: variabelDalam tidak terdefinisi
}

luarFungsi();
```

#### 2. Closure

```javascript
function buatPenghitung() {
    let count = 0; // Private variable
    
    return function() {
        count++;
        return count;
    };
}

const penghitung1 = buatPenghitung();
const penghitung2 = buatPenghitung();

console.log(penghitung1()); // 1
console.log(penghitung1()); // 2
console.log(penghitung1()); // 3

console.log(penghitung2()); // 1 (instance terpisah)
console.log(penghitung2()); // 2

// Contoh praktis: Private methods
function BankAccount(saldoAwal) {
    let saldo = saldoAwal;
    
    return {
        getSaldo: function() {
            return saldo;
        },
        
        setor: function(jumlah) {
            if (jumlah > 0) {
                saldo += jumlah;
                return `Berhasil setor ${jumlah}. Saldo: ${saldo}`;
            }
            return "Jumlah setor harus lebih dari 0";
        },
        
        tarik: function(jumlah) {
            if (jumlah > 0 && jumlah <= saldo) {
                saldo -= jumlah;
                return `Berhasil tarik ${jumlah}. Saldo: ${saldo}`;
            }
            return "Saldo tidak mencukupi atau jumlah tidak valid";
        }
    };
}

const akun = BankAccount(100000);
console.log(akun.getSaldo());        // 100000
console.log(akun.setor(50000));      // Berhasil setor 50000. Saldo: 150000
console.log(akun.tarik(30000));      // Berhasil tarik 30000. Saldo: 120000
// console.log(saldo);               // ❌ Error: saldo tidak dapat diakses langsung
```

### Tips Penting untuk Functions:

#### 1. Pure Functions vs Side Effects

```javascript
// Pure function - tidak mengubah input, selalu return hasil yang sama
function tambahPure(a, b) {
    return a + b;
}

let globalVar = 0;

// Function with side effect - mengubah state di luar function
function tambahSideEffect(a) {
    globalVar += a; // Side effect: mengubah variabel global
    return globalVar;
}

// Lebih baik gunakan pure functions untuk predictability
console.log(tambahPure(5, 3)); // Selalu 8
console.log(tambahPure(5, 3)); // Selalu 8

console.log(tambahSideEffect(5)); // 5
console.log(tambahSideEffect(5)); // 10 (berbeda hasil!)
```

#### 2. Function sebagai First-Class Citizens

```javascript
// Function bisa disimpan dalam variabel
const operasi = function(a, b) { return a + b; };

// Function bisa dijadikan parameter
function aplikasikanOperasi(func, x, y) {
    return func(x, y);
}

console.log(aplikasikanOperasi(operasi, 5, 3)); // 8

// Function bisa dikembalikan dari function lain
function buatOperasi(operator) {
    switch (operator) {
        case '+': return (a, b) => a + b;
        case '-': return (a, b) => a - b;
        case '*': return (a, b) => a * b;
        default: return (a, b) => 0;
    }
}

const multiply = buatOperasi('*');
console.log(multiply(4, 5)); // 20
```

#### 3. Performance dan Best Practices

```javascript
// ✅ Good: Gunakan nama yang descriptive
function hitungPajakPenghasilan(penghasilan) {
    return penghasilan * 0.1;
}

// ❌ Bad: Nama tidak jelas
function calc(x) {
    return x * 0.1;
}

// ✅ Good: Satu fungsi, satu tanggung jawab
function validasiEmail(email) {
    return email && email.includes('@') && email.includes('.');
}

function kirimEmail(email, pesan) {
    if (!validasiEmail(email)) {
        throw new Error('Email tidak valid');
    }
    // Logic pengiriman email
}

// ✅ Good: Gunakan early return untuk readability
function prosesOrder(order) {
    if (!order) return { error: 'Order tidak ada' };
    if (!order.items) return { error: 'Items kosong' };
    if (order.total <= 0) return { error: 'Total tidak valid' };
    
    // Process order logic here
    return { success: true, orderId: order.id };
}
```

## Interaksi dengan Browser (DOM Manipulation) 

Sampai sekarang kita sudah belajar JavaScript sebagai bahasa pemrograman. Sekarang saatnya mempelajari bagaimana JavaScript berinteraksi dengan halaman web (HTML) melalui DOM (Document Object Model). Ini adalah bagian yang membuat JavaScript menjadi bahasa yang powerful untuk web development.

### Apa itu DOM (Document Object Model)? 🏗️

DOM adalah representasi struktur dokumen HTML sebagai **tree of objects** yang dapat dimanipulasi dengan JavaScript. Bayangkan HTML sebagai rumah, dan DOM adalah blueprint yang memungkinkan JavaScript "merenovasi" rumah tersebut.

#### Konsep Dasar DOM

```html
<!DOCTYPE html>
<html>
<head>
    <title>Contoh DOM</title>
</head>
<body>
    <div id="container">
        <h1 class="judul">Selamat Datang</h1>
        <p class="deskripsi">Ini adalah paragraf pertama.</p>
        <button id="tombol">Klik Saya</button>
    </div>
</body>
</html>
```

**Struktur DOM Tree:**
```
Document
└── html
    ├── head
    │   └── title
    │       └── "Contoh DOM"
    └── body
        └── div#container
            ├── h1.judul
            │   └── "Selamat Datang"
            ├── p.deskripsi
            │   └── "Ini adalah paragraf pertama."
            └── button#tombol
                └── "Klik Saya"
```

#### Akses DOM di JavaScript

```javascript
// Global object 'document' adalah pintu masuk ke DOM
console.log(document);
console.log(document.title);        // "Contoh DOM"
console.log(document.URL);          // URL halaman saat ini
console.log(document.body);         // Elemen <body>
```

### Seleksi Elemen 🎯

Sebelum bisa memanipulasi elemen HTML, kita harus "menangkap" atau menyeleksi elemen tersebut terlebih dahulu.

#### 1. getElementById()

Menyeleksi elemen berdasarkan ID unik.

```javascript
// HTML: <div id="container">Content</div>
const container = document.getElementById('container');
console.log(container); // Mengembalikan elemen div dengan id="container"

// Jika elemen tidak ditemukan, mengembalikan null
const tidakAda = document.getElementById('tidak-ada');
console.log(tidakAda); // null
```

#### 2. getElementsByClassName()

Menyeleksi elemen berdasarkan nama class. Mengembalikan **HTMLCollection** (array-like).

```javascript
// HTML: <p class="deskripsi">Paragraph 1</p>
//       <p class="deskripsi">Paragraph 2</p>
const deskripsi = document.getElementsByClassName('deskripsi');
console.log(deskripsi); // HTMLCollection[2]
console.log(deskripsi[0]); // Elemen pertama dengan class="deskripsi"
console.log(deskripsi.length); // 2

// Menggunakan loop untuk mengakses semua elemen
for (let i = 0; i < deskripsi.length; i++) {
    console.log(deskripsi[i].textContent);
}
```

#### 3. getElementsByTagName()

Menyeleksi elemen berdasarkan nama tag.

```javascript
// Menyeleksi semua elemen <p>
const paragraphs = document.getElementsByTagName('p');
console.log(paragraphs);

// Menyeleksi semua elemen <div>
const divs = document.getElementsByTagName('div');
console.log(divs);
```

#### 4. querySelector() dan querySelectorAll() (Modern & Recommended)

Menggunakan CSS selector untuk menyeleksi elemen. Lebih fleksibel dan powerful!

**querySelector() - Mengembalikan elemen pertama yang cocok:**
```javascript
// Seleksi berdasarkan ID
const container = document.querySelector('#container');

// Seleksi berdasarkan class
const judul = document.querySelector('.judul');

// Seleksi berdasarkan tag
const button = document.querySelector('button');

// Seleksi berdasarkan attribute
const input = document.querySelector('input[type="text"]');

// Seleksi yang lebih kompleks
const firstPInDiv = document.querySelector('div p:first-child');
const buttonInContainer = document.querySelector('#container button');
```

**querySelectorAll() - Mengembalikan NodeList semua elemen yang cocok:**
```javascript
// Menyeleksi semua elemen dengan class="deskripsi"
const semuaDeskripsi = document.querySelectorAll('.deskripsi');
console.log(semuaDeskripsi); // NodeList[2]

// Menggunakan forEach (NodeList mendukung forEach)
semuaDeskripsi.forEach((elemen, index) => {
    console.log(`Elemen ${index}: ${elemen.textContent}`);
});

// Seleksi multiple class
const semuaHighlight = document.querySelectorAll('.highlight, .important');

// Seleksi berdasarkan attribute
const requiredInputs = document.querySelectorAll('input[required]');
```

#### 5. Perbandingan Method Seleksi

```javascript
// Perbandingan performa dan fleksibilitas
console.time('getElementById');
document.getElementById('container');
console.timeEnd('getElementById'); // Tercepat

console.time('querySelector');
document.querySelector('#container');
console.timeEnd('querySelector'); // Sedikit lebih lambat, tapi lebih fleksibel

// querySelector vs getElementsBy*
const byClass = document.getElementsByClassName('deskripsi'); // Live HTMLCollection
const byQuery = document.querySelectorAll('.deskripsi');    // Static NodeList

// Menambah elemen baru dengan class="deskripsi"
const newP = document.createElement('p');
newP.className = 'deskripsi';
document.body.appendChild(newP);

console.log(byClass.length);  // Otomatis bertambah (Live)
console.log(byQuery.length);  // Tidak bertambah (Static)
```

### Manipulasi Elemen 🛠️

Setelah menyeleksi elemen, kita bisa mengubah konten, style, dan properti elemen tersebut.

#### 1. Mengubah Konten Elemen

**textContent - Mengubah teks (tanpa HTML):**
```javascript
const judul = document.querySelector('.judul');

// Membaca konten
console.log(judul.textContent); // "Selamat Datang"

// Mengubah konten
judul.textContent = "Halo Dunia!";
console.log(judul.textContent); // "Halo Dunia!"

// textContent menghilangkan HTML tags
judul.textContent = "<em>Teks Italic</em>"; // Akan ditampilkan literal, bukan sebagai HTML
```

**innerHTML - Mengubah HTML (dengan HTML tags):**
```javascript
const container = document.querySelector('#container');

// Membaca HTML
console.log(container.innerHTML);

// Mengubah dengan HTML
container.innerHTML = `
    <h2>Judul Baru</h2>
    <p><strong>Paragraf</strong> dengan <em>format</em>.</p>
    <button onclick="alert('Clicked!')">Tombol Baru</button>
`;

// Menambahkan HTML
container.innerHTML += '<p>Paragraf tambahan</p>';
```

**innerText vs textContent:**
```javascript
// HTML: <p>Teks <span style="display:none;">tersembunyi</span> terlihat</p>
const p = document.querySelector('p');

console.log(p.textContent); // "Teks tersembunyi terlihat" (semua teks)
console.log(p.innerText);   // "Teks terlihat" (hanya teks yang terlihat)
```

#### 2. Mengubah Atribut Elemen

```javascript
const button = document.querySelector('#tombol');

// getAttribute - Membaca atribut
console.log(button.getAttribute('id')); // "tombol"

// setAttribute - Mengubah/menambah atribut
button.setAttribute('class', 'btn btn-primary');
button.setAttribute('data-action', 'submit');

// removeAttribute - Menghapus atribut
button.removeAttribute('class');

// Properti langsung untuk atribut umum
button.id = 'new-button';
button.className = 'btn large';
button.disabled = true;

// Untuk custom attribute, gunakan dataset
button.dataset.userId = '12345';
button.dataset.action = 'delete';
console.log(button.dataset.userId); // "12345"
```

#### 3. Mengubah Style/CSS

**Inline Style:**
```javascript
const judul = document.querySelector('.judul');

// Mengubah style satu per satu
judul.style.color = 'red';
judul.style.fontSize = '2em';
judul.style.backgroundColor = 'yellow';
judul.style.padding = '10px';

// Mengubah style dengan cssText
judul.style.cssText = 'color: blue; font-size: 1.5em; margin: 20px;';

// Membaca computed style
const computedStyle = window.getComputedStyle(judul);
console.log(computedStyle.fontSize); // Actual font size
console.log(computedStyle.color);    // Actual color
```

**Manipulasi Class CSS (Recommended):**
```javascript
const elemen = document.querySelector('.box');

// classList properties dan methods
console.log(elemen.classList);         // DOMTokenList
console.log(elemen.classList.length);  // Jumlah class

// add() - Menambah class
elemen.classList.add('active');
elemen.classList.add('highlight', 'animated'); // Multiple class

// remove() - Menghapus class
elemen.classList.remove('old-class');

// toggle() - Toggle class (hapus jika ada, tambah jika tidak ada)
elemen.classList.toggle('active');     // Remove jika ada, add jika tidak ada
elemen.classList.toggle('hidden', true); // Force add

// contains() - Cek apakah class ada
if (elemen.classList.contains('active')) {
    console.log('Elemen aktif');
}

// replace() - Ganti class
elemen.classList.replace('old-class', 'new-class');
```

#### 4. Membuat dan Menghapus Elemen

**createElement dan appendChild:**
```javascript
// Membuat elemen baru
const newDiv = document.createElement('div');
newDiv.textContent = 'Div baru';
newDiv.className = 'new-element';
newDiv.id = 'dynamic-div';

// Menambahkan ke DOM
document.body.appendChild(newDiv);

// Membuat elemen yang lebih kompleks
const card = document.createElement('div');
card.className = 'card';

const cardHeader = document.createElement('h3');
cardHeader.textContent = 'Card Title';

const cardBody = document.createElement('p');
cardBody.textContent = 'Card content goes here.';

const cardButton = document.createElement('button');
cardButton.textContent = 'Action';
cardButton.className = 'btn';

// Menyusun struktur
card.appendChild(cardHeader);
card.appendChild(cardBody);
card.appendChild(cardButton);

// Menambahkan ke container
const container = document.querySelector('#container');
container.appendChild(card);
```

**insertAdjacentHTML (Modern approach):**
```javascript
const container = document.querySelector('#container');

// Insert positions: 'beforebegin', 'afterbegin', 'beforeend', 'afterend'
container.insertAdjacentHTML('beforeend', `
    <div class="notification">
        <p>This is a notification</p>
        <button class="close">×</button>
    </div>
`);

// Insert elemen (bukan string HTML)
const newElement = document.createElement('span');
newElement.textContent = 'New span';
container.insertAdjacentElement('afterbegin', newElement);
```

**Menghapus Elemen:**
```javascript
const elemen = document.querySelector('.remove-me');

// Method modern (recommended)
elemen.remove();

// Method lama (masih berfungsi)
elemen.parentNode.removeChild(elemen);

// Menghapus semua child elements
const parent = document.querySelector('.parent');
parent.innerHTML = ''; // Cara cepat
// atau
while (parent.firstChild) {
    parent.removeChild(parent.firstChild);
}
```

### Event Handling 🎪

Event adalah aksi yang terjadi di halaman web (click, hover, input, dll). Event handling memungkinkan kita merespons aksi user.

#### 1. addEventListener() (Recommended)

```javascript
const button = document.querySelector('#tombol');

// Basic event listener
button.addEventListener('click', function() {
    alert('Tombol diklik!');
});

// Dengan arrow function
button.addEventListener('click', () => {
    console.log('Button clicked with arrow function');
});

// Dengan named function (bisa di-remove)
function handleClick() {
    console.log('Named function handler');
}
button.addEventListener('click', handleClick);

// Menghapus event listener
button.removeEventListener('click', handleClick);
```

#### 2. Event Object

```javascript
const input = document.querySelector('#nama');

input.addEventListener('keydown', function(event) {
    console.log('Key pressed:', event.key);
    console.log('Key code:', event.keyCode);
    console.log('Ctrl pressed:', event.ctrlKey);
    console.log('Shift pressed:', event.shiftKey);
    
    // Mencegah default behavior
    if (event.key === 'Enter') {
        event.preventDefault();
        console.log('Enter key prevented');
    }
});

// Mouse events
const div = document.querySelector('.interactive');
div.addEventListener('click', function(event) {
    console.log('Mouse X:', event.clientX);
    console.log('Mouse Y:', event.clientY);
    console.log('Target element:', event.target);
    console.log('Current target:', event.currentTarget);
});
```

#### 3. Jenis-jenis Event Populer

```javascript
const elemen = document.querySelector('.demo');

// Mouse Events
elemen.addEventListener('click', () => console.log('Clicked'));
elemen.addEventListener('dblclick', () => console.log('Double clicked'));
elemen.addEventListener('mousedown', () => console.log('Mouse down'));
elemen.addEventListener('mouseup', () => console.log('Mouse up'));
elemen.addEventListener('mouseover', () => console.log('Mouse over'));
elemen.addEventListener('mouseout', () => console.log('Mouse out'));
elemen.addEventListener('mousemove', () => console.log('Mouse move'));

// Keyboard Events
document.addEventListener('keydown', (e) => console.log('Key down:', e.key));
document.addEventListener('keyup', (e) => console.log('Key up:', e.key));
document.addEventListener('keypress', (e) => console.log('Key press:', e.key)); // Deprecated

// Form Events
const form = document.querySelector('#myForm');
const input = document.querySelector('#myInput');

input.addEventListener('focus', () => console.log('Input focused'));
input.addEventListener('blur', () => console.log('Input blurred'));
input.addEventListener('change', () => console.log('Input changed'));
input.addEventListener('input', () => console.log('Input typing'));

form.addEventListener('submit', (e) => {
    e.preventDefault(); // Mencegah form submit
    console.log('Form submitted');
});

// Window/Document Events
window.addEventListener('load', () => console.log('Page fully loaded'));
window.addEventListener('resize', () => console.log('Window resized'));
window.addEventListener('scroll', () => console.log('Page scrolled'));

document.addEventListener('DOMContentLoaded', () => {
    console.log('DOM fully loaded');
});
```

#### 4. Event Delegation

Event delegation memungkinkan handling event pada elemen yang belum ada saat page load.

```javascript
// Tanpa delegation - hanya bekerja untuk elemen yang sudah ada
const buttons = document.querySelectorAll('.btn');
buttons.forEach(btn => {
    btn.addEventListener('click', () => {
        console.log('Button clicked');
    });
});

// Dengan delegation - bekerja untuk elemen yang dinamis
document.addEventListener('click', function(event) {
    // Cek apakah elemen yang diklik memiliki class 'btn'
    if (event.target.classList.contains('btn')) {
        console.log('Button clicked (delegated)');
        console.log('Button text:', event.target.textContent);
    }
    
    // Atau cek berdasarkan selector yang lebih spesifik
    if (event.target.matches('.delete-btn')) {
        const itemId = event.target.dataset.itemId;
        console.log('Delete button clicked for item:', itemId);
    }
});

// Sekarang tombol yang ditambahkan dinamis juga akan bekerja
const container = document.querySelector('#container');
container.insertAdjacentHTML('beforeend', `
    <button class="btn delete-btn" data-item-id="123">Delete Item 123</button>
`);
```

### Contoh Praktis: Aplikasi Todo List

```html
<!DOCTYPE html>
<html>
<head>
    <title>Todo List App</title>
    <style>
        .container { max-width: 600px; margin: 0 auto; padding: 20px; }
        .todo-input { width: 70%; padding: 10px; font-size: 16px; }
        .add-btn { padding: 10px 20px; font-size: 16px; }
        .todo-item { 
            display: flex; 
            justify-content: space-between; 
            align-items: center;
            padding: 10px; 
            border: 1px solid #ddd; 
            margin: 5px 0; 
        }
        .todo-item.completed { 
            opacity: 0.6; 
            text-decoration: line-through; 
        }
        .delete-btn { 
            background: red; 
            color: white; 
            border: none; 
            padding: 5px 10px; 
            cursor: pointer; 
        }
        .complete-btn {
            background: green;
            color: white;
            border: none;
            padding: 5px 10px;
            cursor: pointer;
            margin-right: 5px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Todo List</h1>
        <div class="input-section">
            <input type="text" class="todo-input" placeholder="Enter new todo..." maxlength="100">
            <button class="add-btn">Add Todo</button>
        </div>
        <div class="stats">
            <span class="total-count">Total: 0</span> |
            <span class="completed-count">Completed: 0</span> |
            <span class="pending-count">Pending: 0</span>
        </div>
        <div class="todo-list"></div>
    </div>

    <script>
        // Todo List Application with DOM Manipulation
        class TodoApp {
            constructor() {
                this.todos = [];
                this.todoIdCounter = 1;
                this.init();
            }
            
            init() {
                this.bindEvents();
                this.updateStats();
            }
            
            bindEvents() {
                const addBtn = document.querySelector('.add-btn');
                const todoInput = document.querySelector('.todo-input');
                const todoList = document.querySelector('.todo-list');
                
                // Add todo on button click
                addBtn.addEventListener('click', () => this.addTodo());
                
                // Add todo on Enter key press
                todoInput.addEventListener('keypress', (e) => {
                    if (e.key === 'Enter') {
                        this.addTodo();
                    }
                });
                
                // Event delegation for dynamic buttons
                todoList.addEventListener('click', (e) => {
                    const todoId = parseInt(e.target.dataset.todoId);
                    
                    if (e.target.classList.contains('complete-btn')) {
                        this.toggleComplete(todoId);
                    } else if (e.target.classList.contains('delete-btn')) {
                        this.deleteTodo(todoId);
                    }
                });
            }
            
            addTodo() {
                const input = document.querySelector('.todo-input');
                const text = input.value.trim();
                
                if (!text) {
                    alert('Please enter a todo item!');
                    return;
                }
                
                const todo = {
                    id: this.todoIdCounter++,
                    text: text,
                    completed: false,
                    createdAt: new Date()
                };
                
                this.todos.push(todo);
                input.value = '';
                input.focus();
                
                this.renderTodos();
                this.updateStats();
            }
            
            toggleComplete(todoId) {
                const todo = this.todos.find(t => t.id === todoId);
                if (todo) {
                    todo.completed = !todo.completed;
                    this.renderTodos();
                    this.updateStats();
                }
            }
            
            deleteTodo(todoId) {
                const confirmed = confirm('Are you sure you want to delete this todo?');
                if (confirmed) {
                    this.todos = this.todos.filter(t => t.id !== todoId);
                    this.renderTodos();
                    this.updateStats();
                }
            }
            
            renderTodos() {
                const todoList = document.querySelector('.todo-list');
                
                if (this.todos.length === 0) {
                    todoList.innerHTML = '<p style="text-align: center; color: #666;">No todos yet. Add one above!</p>';
                    return;
                }
                
                const todosHTML = this.todos.map(todo => {
                    const completedClass = todo.completed ? 'completed' : '';
                    const completeButtonText = todo.completed ? 'Undo' : 'Complete';
                    
                    return `
                        <div class="todo-item ${completedClass}">
                            <span class="todo-text">${this.escapeHtml(todo.text)}</span>
                            <div class="todo-actions">
                                <button class="complete-btn" data-todo-id="${todo.id}">
                                    ${completeButtonText}
                                </button>
                                <button class="delete-btn" data-todo-id="${todo.id}">
                                    Delete
                                </button>
                            </div>
                        </div>
                    `;
                }).join('');
                
                todoList.innerHTML = todosHTML;
            }
            
            updateStats() {
                const totalCount = this.todos.length;
                const completedCount = this.todos.filter(t => t.completed).length;
                const pendingCount = totalCount - completedCount;
                
                document.querySelector('.total-count').textContent = `Total: ${totalCount}`;
                document.querySelector('.completed-count').textContent = `Completed: ${completedCount}`;
                document.querySelector('.pending-count').textContent = `Pending: ${pendingCount}`;
            }
            
            escapeHtml(text) {
                const div = document.createElement('div');
                div.textContent = text;
                return div.innerHTML;
            }
        }
        
        // Initialize app when DOM is loaded
        document.addEventListener('DOMContentLoaded', () => {
            new TodoApp();
        });
    </script>
</body>
</html>
```

