# Pertemuan 9: Sintaks Dasar JavaScript

## Tujuan Pembelajaran
Setelah mengikuti pertemuan ini, mahasiswa diharapkan dapat:
- Memahami sintaks dasar JavaScript
- Menggunakan komentar dalam kode JavaScript
- Memahami dan menggunakan variabel dengan `var`, `let`, dan `const`
- Mengenal berbagai tipe data dalam JavaScript
- Menggunakan operator aritmatika, perbandingan, dan logika

## 1. Sintaks Dasar JavaScript

### 1.1 Pengenalan JavaScript
JavaScript adalah bahasa pemrograman yang digunakan untuk membuat halaman web yang interaktif. JavaScript dapat dijalankan di browser dan juga di server (Node.js).

### 1.2 Cara Menulis Kode JavaScript

#### Di dalam file HTML:
```html
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript Dasar</title>
</head>
<body>
    <script>
        // Kode JavaScript ditulis di sini
        console.log("Hello, JavaScript!");
    </script>
</body>
</html>
```

#### File JavaScript terpisah:
```html
<!-- Di file HTML -->
<script src="script.js"></script>
```

```javascript
// Di file script.js
console.log("Hello, JavaScript!");
```

### 1.3 Komentar dalam JavaScript

#### Komentar Satu Baris:
```javascript
// Ini adalah komentar satu baris
console.log("Hello World"); // Komentar di akhir baris
```

#### Komentar Multi Baris:
```javascript
/*
Ini adalah komentar
yang terdiri dari
beberapa baris
*/
console.log("Hello World");
```

**Kapan Menggunakan Komentar:**
- Menjelaskan kode yang kompleks
- Mendokumentasikan fungsi atau algoritma
- Memberikan informasi tentang penulis atau versi
- Menonaktifkan sementara bagian kode

## 2. Variabel

### 2.1 Pengertian Variabel
Variabel adalah tempat untuk menyimpan data yang dapat digunakan dan diubah selama program berjalan.

### 2.2 Cara Mendeklarasikan Variabel

#### Menggunakan `var`:
```javascript
var nama = "John";
var umur = 25;
console.log(nama); // Output: John
```

#### Menggunakan `let`:
```javascript
let nama = "Jane";
let umur = 23;
console.log(nama); // Output: Jane
```

#### Menggunakan `const`:
```javascript
const PI = 3.14159;
const nama = "Alice";
// PI = 3.15; // Error! const tidak bisa diubah
```

### 2.3 Perbedaan var, let, dan const

| Karakteristik | var | let | const |
|--------------|-----|-----|-------|
| Scope | Function/Global | Block | Block |
| Hoisting | Ya | Ya (tapi tidak accessible) | Ya (tapi tidak accessible) |
| Re-declaration | Ya | Tidak | Tidak |
| Re-assignment | Ya | Ya | Tidak |
| Inisialisasi | Opsional | Opsional | Wajib |

#### Contoh Scope:
```javascript
function contohScope() {
    if (true) {
        var x = 1;
        let y = 2;
        const z = 3;
    }
    
    console.log(x); // 1 - var accessible
    // console.log(y); // Error - let tidak accessible
    // console.log(z); // Error - const tidak accessible
}
```

#### Kapan Menggunakan:
- **`const`**: Gunakan sebagai default untuk nilai yang tidak berubah
- **`let`**: Gunakan untuk variabel yang nilainya akan berubah
- **`var`**: Hindari penggunaan (legacy)

## 3. Tipe Data

### 3.1 Tipe Data Primitif

#### String (Teks):
```javascript
let nama = "John Doe";
let alamat = 'Jakarta';
let template = `Nama: ${nama}`; // Template literal

// Properti dan method string
console.log(nama.length); // 8
console.log(nama.toUpperCase()); // JOHN DOE
console.log(nama.toLowerCase()); // john doe
```

#### Number (Angka):
```javascript
let umur = 25;
let tinggi = 175.5;
let negatif = -10;

// Operasi matematika
console.log(umur + 5); // 30
console.log(tinggi * 2); // 351

// Method number
console.log(tinggi.toFixed(1)); // "175.5"
```

#### Boolean:
```javascript
let isActive = true;
let isComplete = false;

// Konversi ke boolean
console.log(Boolean(1)); // true
console.log(Boolean(0)); // false
console.log(Boolean("")); // false
console.log(Boolean("text")); // true
```

#### null dan undefined:
```javascript
let data = null; // Sengaja dikosongkan
let belumDiisi; // undefined secara otomatis

console.log(data); // null
console.log(belumDiisi); // undefined
console.log(typeof null); // "object" (quirk JavaScript)
console.log(typeof undefined); // "undefined"
```

### 3.2 Tipe Data Kompleks

#### Object:
```javascript
let mahasiswa = {
    nama: "Alice",
    umur: 20,
    jurusan: "Informatika",
    isActive: true
};

// Mengakses properti
console.log(mahasiswa.nama); // Alice
console.log(mahasiswa["umur"]); // 20

// Menambah/mengubah properti
mahasiswa.semester = 3;
mahasiswa.umur = 21;
```

#### Array:
```javascript
let buah = ["apel", "jeruk", "mangga"];
let angka = [1, 2, 3, 4, 5];
let campuran = ["text", 123, true, null];

// Mengakses elemen
console.log(buah[0]); // apel
console.log(angka.length); // 5

// Method array
buah.push("pisang"); // Menambah di akhir
buah.unshift("anggur"); // Menambah di awal
```

### 3.3 Mengecek Tipe Data
```javascript
console.log(typeof "Hello"); // "string"
console.log(typeof 42); // "number"
console.log(typeof true); // "boolean"
console.log(typeof undefined); // "undefined"
console.log(typeof null); // "object"
console.log(typeof {}); // "object"
console.log(typeof []); // "object"

// Untuk array, gunakan Array.isArray()
console.log(Array.isArray([])); // true
console.log(Array.isArray({})); // false
```

## 4. Operator

### 4.1 Operator Aritmatika

```javascript
let a = 10;
let b = 3;

console.log(a + b); // 13 - Penjumlahan
console.log(a - b); // 7  - Pengurangan
console.log(a * b); // 30 - Perkalian
console.log(a / b); // 3.333... - Pembagian
console.log(a % b); // 1  - Modulo (sisa bagi)
console.log(a ** b); // 1000 - Pangkat (ES2016)

// Operator assignment
a += 5; // a = a + 5
b *= 2; // b = b * 2

// Increment dan Decrement
let x = 5;
console.log(x++); // 5 (post-increment)
console.log(++x); // 7 (pre-increment)
console.log(x--); // 7 (post-decrement)
console.log(--x); // 5 (pre-decrement)
```

### 4.2 Operator Perbandingan

```javascript
let x = 5;
let y = "5";
let z = 10;

// Equality
console.log(x == y);  // true (nilai sama, tipe diabaikan)
console.log(x === y); // false (nilai dan tipe harus sama)
console.log(x != z);  // true
console.log(x !== y); // true

// Relational
console.log(x > 3);   // true
console.log(x < z);   // true
console.log(x >= 5);  // true
console.log(z <= 10); // true
```

**Penting:** Selalu gunakan `===` dan `!==` untuk menghindari konversi tipe otomatis yang tidak diinginkan.

### 4.3 Operator Logika

```javascript
let a = true;
let b = false;
let x = 5;
let y = 10;

// AND (&&) - semua harus true
console.log(a && b); // false
console.log(x > 0 && y > 0); // true

// OR (||) - salah satu true sudah cukup
console.log(a || b); // true
console.log(x > 10 || y > 5); // true

// NOT (!) - membalik nilai boolean
console.log(!a); // false
console.log(!b); // true
console.log(!(x > y)); // true
```

#### Short-circuit evaluation:
```javascript
// AND - berhenti di nilai falsy pertama
let result1 = false && console.log("Tidak dijalankan");

// OR - berhenti di nilai truthy pertama
let result2 = true || console.log("Tidak dijalankan");

// Praktik umum untuk default value
let nama = "" || "Anonymous"; // "Anonymous"
let config = userConfig || defaultConfig;
```

## 5. Latihan Praktik

### Latihan 1: Variabel dan Tipe Data
```javascript
// Buatlah variabel untuk menyimpan data mahasiswa
const nama = "John Doe";
let umur = 20;
let ipk = 3.75;
let isActive = true;
let hobi = ["membaca", "coding", "musik"];

console.log(`Nama: ${nama}`);
console.log(`Umur: ${umur} tahun`);
console.log(`IPK: ${ipk}`);
console.log(`Status: ${isActive ? "Aktif" : "Tidak Aktif"}`);
console.log(`Hobi: ${hobi.join(", ")}`);
```

### Latihan 2: Operator
```javascript
// Kalkulator sederhana
let angka1 = 15;
let angka2 = 4;

console.log(`${angka1} + ${angka2} = ${angka1 + angka2}`);
console.log(`${angka1} - ${angka2} = ${angka1 - angka2}`);
console.log(`${angka1} * ${angka2} = ${angka1 * angka2}`);
console.log(`${angka1} / ${angka2} = ${angka1 / angka2}`);
console.log(`${angka1} % ${angka2} = ${angka1 % angka2}`);

// Perbandingan
console.log(`${angka1} > ${angka2}: ${angka1 > angka2}`);
console.log(`${angka1} === ${angka2}: ${angka1 === angka2}`);
```

### Latihan 3: Kombinasi Operator
```javascript
// Validasi data user
let username = "john_doe";
let password = "password123";
let age = 18;
let isVerified = true;

let isValidUser = username.length >= 3 && 
                  password.length >= 8 && 
                  age >= 18 && 
                  isVerified;

console.log(`User valid: ${isValidUser}`);

// Menghitung diskon
let totalBelanja = 150000;
let isMember = true;
let diskon = isMember && totalBelanja > 100000 ? 0.1 : 0;
let totalBayar = totalBelanja * (1 - diskon);

console.log(`Total belanja: Rp ${totalBelanja.toLocaleString()}`);
console.log(`Diskon: ${diskon * 100}%`);
console.log(`Total bayar: Rp ${totalBayar.toLocaleString()}`);
```

## 6. Tugas

1. **Tugas Variabel**: Buatlah program untuk menghitung luas dan keliling persegi panjang menggunakan variabel `panjang` dan `lebar`.

2. **Tugas Tipe Data**: Buatlah object untuk menyimpan data buku yang berisi judul, pengarang, tahun terbit, dan status (dipinjam/tersedia).

3. **Tugas Operator**: Buatlah program kalkulator BMI (Body Mass Index) yang menghitung BMI dan memberikan kategori (underweight, normal, overweight, obesitas).

## 7. Referensi Tambahan

- [MDN JavaScript Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)
- [JavaScript.info - Variables](https://javascript.info/variables)
- [JavaScript.info - Data Types](https://javascript.info/types)
- [JavaScript.info - Operators](https://javascript.info/operators)

## Ringkasan

Dalam pertemuan ini kita telah mempelajari:
- Sintaks dasar JavaScript dan cara menulis komentar
- Perbedaan antara `var`, `let`, dan `const`
- Tipe data primitif (string, number, boolean, null, undefined) dan kompleks (object, array)
- Operator aritmatika, perbandingan, dan logika
- Best practices dalam penggunaan variabel dan operator

**Tips Penting:**
- Gunakan `const` sebagai default, `let` jika perlu mengubah nilai
- Selalu gunakan `===` untuk perbandingan
- Beri nama variabel yang deskriptif dan mudah dipahami
- Gunakan komentar untuk menjelaskan kode yang kompleks