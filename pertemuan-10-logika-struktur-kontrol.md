# Pertemuan 10: Logika dan Struktur Kontrol JavaScript

## Tujuan Pembelajaran
Setelah mengikuti pertemuan ini, mahasiswa diharapkan dapat:
- Memahami dan menggunakan struktur conditional (if, else if, else, switch)
- Menggunakan operator ternary untuk conditional singkat
- Memahami dan menggunakan berbagai jenis looping (for, while, do-while)
- Menggunakan break dan continue dalam loop
- Menerapkan nested loops untuk kasus yang kompleks

## 1. Conditional (Percabangan)

### 1.1 Struktur If-Else

#### If Statement Dasar:
```javascript
let umur = 18;

if (umur >= 18) {
    console.log("Anda sudah dewasa");
}
```

#### If-Else Statement:
```javascript
let nilai = 75;

if (nilai >= 70) {
    console.log("Lulus");
} else {
    console.log("Tidak Lulus");
}
```

#### If-Else If-Else:
```javascript
let score = 85;
let grade;

if (score >= 90) {
    grade = "A";
} else if (score >= 80) {
    grade = "B";
} else if (score >= 70) {
    grade = "C";
} else if (score >= 60) {
    grade = "D";
} else {
    grade = "E";
}

console.log(`Grade Anda: ${grade}`);
```

#### Nested If (If Bersarang):
```javascript
let cuaca = "cerah";
let suhu = 25;

if (cuaca === "cerah") {
    if (suhu > 30) {
        console.log("Cuaca cerah dan panas, gunakan sunscreen!");
    } else if (suhu > 20) {
        console.log("Cuaca cerah dan hangat, cocok untuk jalan-jalan!");
    } else {
        console.log("Cuaca cerah tapi dingin, pakai jaket!");
    }
} else if (cuaca === "hujan") {
    console.log("Bawa payung!");
}
```

### 1.2 Switch Statement

#### Switch Dasar:
```javascript
let hari = 3;
let namaHari;

switch (hari) {
    case 1:
        namaHari = "Senin";
        break;
    case 2:
        namaHari = "Selasa";
        break;
    case 3:
        namaHari = "Rabu";
        break;
    case 4:
        namaHari = "Kamis";
        break;
    case 5:
        namaHari = "Jumat";
        break;
    case 6:
        namaHari = "Sabtu";
        break;
    case 7:
        namaHari = "Minggu";
        break;
    default:
        namaHari = "Hari tidak valid";
}

console.log(namaHari); // Output: Rabu
```

#### Switch dengan Multiple Cases:
```javascript
let bulan = "Februari";
let jumlahHari;

switch (bulan) {
    case "Januari":
    case "Maret":
    case "Mei":
    case "Juli":
    case "Agustus":
    case "Oktober":
    case "Desember":
        jumlahHari = 31;
        break;
    case "April":
    case "Juni":
    case "September":
    case "November":
        jumlahHari = 30;
        break;
    case "Februari":
        jumlahHari = 28; // atau 29 untuk tahun kabisat
        break;
    default:
        jumlahHari = "Bulan tidak valid";
}

console.log(`${bulan} memiliki ${jumlahHari} hari`);
```

### 1.3 Operator Ternary (Conditional Operator)

#### Sintaks Dasar:
```javascript
// kondisi ? nilaiJikaTrue : nilaiJikaFalse
let umur = 20;
let status = umur >= 18 ? "Dewasa" : "Belum Dewasa";
console.log(status); // Output: Dewasa
```

#### Ternary Bersarang:
```javascript
let nilai = 85;
let grade = nilai >= 90 ? "A" : 
           nilai >= 80 ? "B" : 
           nilai >= 70 ? "C" : 
           nilai >= 60 ? "D" : "E";
console.log(grade); // Output: B
```

#### Penggunaan dalam Function Call:
```javascript
let isLoggedIn = true;
console.log(isLoggedIn ? "Selamat datang!" : "Silakan login terlebih dahulu");
```

### 1.4 Truthy dan Falsy Values

#### Falsy Values:
```javascript
// Nilai-nilai yang dianggap false
console.log(Boolean(false));     // false
console.log(Boolean(0));         // false
console.log(Boolean(-0));        // false
console.log(Boolean(0n));        // false (BigInt)
console.log(Boolean(""));        // false
console.log(Boolean(null));      // false
console.log(Boolean(undefined)); // false
console.log(Boolean(NaN));       // false
```

#### Truthy Values:
```javascript
// Semua nilai selain falsy values adalah truthy
console.log(Boolean("hello"));   // true
console.log(Boolean(1));         // true
console.log(Boolean([]));        // true (array kosong)
console.log(Boolean({}));        // true (object kosong)
console.log(Boolean("0"));       // true (string "0")
console.log(Boolean("false"));   // true (string "false")
```

#### Penggunaan Praktis:
```javascript
let username = "";
if (username) {
    console.log(`Hello, ${username}!`);
} else {
    console.log("Please enter your username");
}

// Atau dengan ternary
let greeting = username ? `Hello, ${username}!` : "Please enter your username";
```

## 2. Looping (Perulangan)

### 2.1 For Loop

#### For Loop Dasar:
```javascript
// Sintaks: for (inisialisasi; kondisi; increment/decrement)
for (let i = 1; i <= 5; i++) {
    console.log(`Iterasi ke-${i}`);
}
```

#### For Loop dengan Array:
```javascript
let buah = ["apel", "jeruk", "mangga", "pisang"];

// Menggunakan index
for (let i = 0; i < buah.length; i++) {
    console.log(`${i + 1}. ${buah[i]}`);
}

// For...of (ES6) - untuk iterasi nilai
for (let item of buah) {
    console.log(item);
}

// For...in - untuk iterasi key/index
for (let index in buah) {
    console.log(`Index ${index}: ${buah[index]}`);
}
```

#### For Loop dengan Object:
```javascript
let mahasiswa = {
    nama: "John",
    umur: 20,
    jurusan: "Informatika",
    semester: 4
};

// For...in untuk object
for (let key in mahasiswa) {
    console.log(`${key}: ${mahasiswa[key]}`);
}

// Menggunakan Object methods
for (let key of Object.keys(mahasiswa)) {
    console.log(`${key}: ${mahasiswa[key]}`);
}
```

#### Nested For Loop:
```javascript
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

// Tabel perkalian
for (let i = 1; i <= 3; i++) {
    for (let j = 1; j <= 3; j++) {
        console.log(`${i} x ${j} = ${i * j}`);
    }
    console.log("---");
}
```

### 2.2 While Loop

#### While Loop Dasar:
```javascript
let i = 1;
while (i <= 5) {
    console.log(`Iterasi ke-${i}`);
    i++; // Jangan lupa increment!
}
```

#### While dengan Kondisi Kompleks:
```javascript
let angka = 1;
let jumlah = 0;

while (jumlah < 100) {
    jumlah += angka;
    angka++;
}

console.log(`Jumlah: ${jumlah}, Angka terakhir: ${angka - 1}`);
```

#### While untuk Input Validation:
```javascript
function inputValidation() {
    let input;
    let isValid = false;
    
    while (!isValid) {
        input = prompt("Masukkan angka antara 1-10:");
        let number = parseInt(input);
        
        if (number >= 1 && number <= 10) {
            isValid = true;
            console.log(`Angka valid: ${number}`);
        } else {
            console.log("Input tidak valid! Coba lagi.");
        }
    }
}
```

### 2.3 Do-While Loop

#### Do-While Dasar:
```javascript
let i = 1;
do {
    console.log(`Iterasi ke-${i}`);
    i++;
} while (i <= 5);
```

#### Perbedaan While vs Do-While:
```javascript
// While - mungkin tidak dieksekusi sama sekali
let kondisi1 = false;
while (kondisi1) {
    console.log("Tidak akan diprint"); // Tidak dieksekusi
}

// Do-While - minimal dieksekusi sekali
let kondisi2 = false;
do {
    console.log("Akan diprint sekali"); // Dieksekusi sekali
} while (kondisi2);
```

#### Contoh Praktis Do-While:
```javascript
function menuProgram() {
    let pilihan;
    
    do {
        console.log("\n=== MENU ===");
        console.log("1. Tambah Data");
        console.log("2. Lihat Data");
        console.log("3. Hapus Data");
        console.log("0. Keluar");
        
        pilihan = parseInt(prompt("Pilih menu (0-3):"));
        
        switch (pilihan) {
            case 1:
                console.log("Menambah data...");
                break;
            case 2:
                console.log("Menampilkan data...");
                break;
            case 3:
                console.log("Menghapus data...");
                break;
            case 0:
                console.log("Terima kasih!");
                break;
            default:
                console.log("Pilihan tidak valid!");
        }
    } while (pilihan !== 0);
}
```

### 2.4 Break dan Continue

#### Break Statement:
```javascript
// Break dalam for loop
for (let i = 1; i <= 10; i++) {
    if (i === 6) {
        break; // Keluar dari loop saat i = 6
    }
    console.log(i);
}
// Output: 1, 2, 3, 4, 5

// Break dalam while loop
let angka = 1;
while (true) {
    if (angka > 5) {
        break;
    }
    console.log(angka);
    angka++;
}
```

#### Continue Statement:
```javascript
// Continue dalam for loop
for (let i = 1; i <= 10; i++) {
    if (i % 2 === 0) {
        continue; // Skip angka genap
    }
    console.log(i);
}
// Output: 1, 3, 5, 7, 9

// Continue dengan kondisi kompleks
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
for (let num of numbers) {
    if (num < 3 || num > 7) {
        continue;
    }
    console.log(`Processed: ${num}`);
}
// Output: Processed: 3, 4, 5, 6, 7
```

#### Break dan Continue dalam Nested Loop:
```javascript
// Label untuk nested loop
outer: for (let i = 1; i <= 3; i++) {
    for (let j = 1; j <= 3; j++) {
        if (i === 2 && j === 2) {
            break outer; // Break dari outer loop
        }
        console.log(`i: ${i}, j: ${j}`);
    }
}
```

## 3. Contoh Implementasi Praktis

### 3.1 Validasi Form
```javascript
function validateForm(data) {
    let errors = [];
    
    // Validasi nama
    if (!data.nama || data.nama.trim() === "") {
        errors.push("Nama harus diisi");
    } else if (data.nama.length < 2) {
        errors.push("Nama minimal 2 karakter");
    }
    
    // Validasi email
    if (!data.email) {
        errors.push("Email harus diisi");
    } else if (!data.email.includes("@")) {
        errors.push("Format email tidak valid");
    }
    
    // Validasi umur
    if (!data.umur) {
        errors.push("Umur harus diisi");
    } else if (data.umur < 17 || data.umur > 65) {
        errors.push("Umur harus antara 17-65 tahun");
    }
    
    return {
        isValid: errors.length === 0,
        errors: errors
    };
}

// Contoh penggunaan
let userData = {
    nama: "John Doe",
    email: "john@example.com",
    umur: 25
};

let validation = validateForm(userData);
if (validation.isValid) {
    console.log("Data valid!");
} else {
    console.log("Errors:");
    for (let error of validation.errors) {
        console.log("- " + error);
    }
}
```

### 3.2 Pencarian dalam Array
```javascript
function cariMahasiswa(daftarMahasiswa, kriteria) {
    let hasil = [];
    
    for (let mahasiswa of daftarMahasiswa) {
        let cocok = true;
        
        // Cek setiap kriteria
        for (let key in kriteria) {
            if (mahasiswa[key] !== kriteria[key]) {
                cocok = false;
                break;
            }
        }
        
        if (cocok) {
            hasil.push(mahasiswa);
        }
    }
    
    return hasil;
}

// Data mahasiswa
let mahasiswaList = [
    { nama: "Alice", jurusan: "Informatika", semester: 3 },
    { nama: "Bob", jurusan: "Sistem Informasi", semester: 3 },
    { nama: "Charlie", jurusan: "Informatika", semester: 5 },
    { nama: "Diana", jurusan: "Informatika", semester: 3 }
];

// Cari mahasiswa Informatika semester 3
let hasil = cariMahasiswa(mahasiswaList, { 
    jurusan: "Informatika", 
    semester: 3 
});

console.log("Mahasiswa yang ditemukan:");
for (let mahasiswa of hasil) {
    console.log(`- ${mahasiswa.nama}`);
}
```

### 3.3 Game Sederhana - Tebak Angka
```javascript
function gameTebakAngka() {
    let angkaRahasia = Math.floor(Math.random() * 100) + 1;
    let percobaan = 0;
    let maxPercobaan = 7;
    let menang = false;
    
    console.log("=== GAME TEBAK ANGKA ===");
    console.log("Tebak angka antara 1-100!");
    console.log(`Anda memiliki ${maxPercobaan} percobaan.`);
    
    while (percobaan < maxPercobaan && !menang) {
        let tebakan = parseInt(prompt(`Percobaan ${percobaan + 1}: Masukkan tebakan Anda:`));
        percobaan++;
        
        if (isNaN(tebakan) || tebakan < 1 || tebakan > 100) {
            console.log("Masukkan angka yang valid (1-100)!");
            percobaan--; // Tidak mengurangi percobaan jika input invalid
            continue;
        }
        
        if (tebakan === angkaRahasia) {
            console.log(`🎉 Selamat! Anda berhasil menebak angka ${angkaRahasia} dalam ${percobaan} percobaan!`);
            menang = true;
        } else if (tebakan < angkaRahasia) {
            console.log("Terlalu kecil! Coba angka yang lebih besar.");
        } else {
            console.log("Terlalu besar! Coba angka yang lebih kecil.");
        }
        
        if (!menang && percobaan < maxPercobaan) {
            console.log(`Sisa percobaan: ${maxPercobaan - percobaan}`);
        }
    }
    
    if (!menang) {
        console.log(`😞 Game Over! Angka yang benar adalah ${angkaRahasia}`);
    }
}
```

## 4. Latihan Praktik

### Latihan 1: Grade Calculator
```javascript
function hitungGrade(nilai) {
    let grade, keterangan;
    
    if (nilai >= 90) {
        grade = "A";
        keterangan = "Excellent";
    } else if (nilai >= 80) {
        grade = "B";
        keterangan = "Good";
    } else if (nilai >= 70) {
        grade = "C";
        keterangan = "Average";
    } else if (nilai >= 60) {
        grade = "D";
        keterangan = "Below Average";
    } else {
        grade = "E";
        keterangan = "Fail";
    }
    
    return { grade, keterangan };
}

// Test function
let nilaiMahasiswa = [95, 87, 76, 65, 45];
for (let i = 0; i < nilaiMahasiswa.length; i++) {
    let hasil = hitungGrade(nilaiMahasiswa[i]);
    console.log(`Nilai ${nilaiMahasiswa[i]}: Grade ${hasil.grade} (${hasil.keterangan})`);
}
```

### Latihan 2: Pattern Printing
```javascript
// Pattern 1: Segitiga angka
function cetakSegitigaAngka(tinggi) {
    for (let i = 1; i <= tinggi; i++) {
        let baris = "";
        for (let j = 1; j <= i; j++) {
            baris += j + " ";
        }
        console.log(baris);
    }
}

cetakSegitigaAngka(5);
// Output:
// 1 
// 1 2 
// 1 2 3 
// 1 2 3 4 
// 1 2 3 4 5 

// Pattern 2: Piramida bintang
function cetakPiramida(tinggi) {
    for (let i = 1; i <= tinggi; i++) {
        let spasi = " ".repeat(tinggi - i);
        let bintang = "*".repeat(2 * i - 1);
        console.log(spasi + bintang);
    }
}

cetakPiramida(5);
// Output:
//     *
//    ***
//   *****
//  *******
// *********
```

### Latihan 3: Array Processing
```javascript
function prosesDataPenjualan(data) {
    let totalPenjualan = 0;
    let penjualanTertinggi = 0;
    let bulanTerbaik = "";
    let bulanDiAtasTarget = [];
    let target = 50000000; // 50 juta
    
    for (let item of data) {
        totalPenjualan += item.penjualan;
        
        if (item.penjualan > penjualanTertinggi) {
            penjualanTertinggi = item.penjualan;
            bulanTerbaik = item.bulan;
        }
        
        if (item.penjualan >= target) {
            bulanDiAtasTarget.push(item.bulan);
        }
    }
    
    let rataRata = totalPenjualan / data.length;
    
    return {
        total: totalPenjualan,
        rataRata: rataRata,
        tertinggi: penjualanTertinggi,
        bulanTerbaik: bulanTerbaik,
        bulanDiAtasTarget: bulanDiAtasTarget
    };
}

// Data contoh
let dataPenjualan = [
    { bulan: "Januari", penjualan: 45000000 },
    { bulan: "Februari", penjualan: 52000000 },
    { bulan: "Maret", penjualan: 48000000 },
    { bulan: "April", penjualan: 55000000 },
    { bulan: "Mei", penjualan: 60000000 }
];

let hasil = prosesDataPenjualan(dataPenjualan);
console.log("=== LAPORAN PENJUALAN ===");
console.log(`Total Penjualan: Rp ${hasil.total.toLocaleString()}`);
console.log(`Rata-rata: Rp ${hasil.rataRata.toLocaleString()}`);
console.log(`Penjualan Tertinggi: Rp ${hasil.tertinggi.toLocaleString()} (${hasil.bulanTerbaik})`);
console.log(`Bulan di atas target: ${hasil.bulanDiAtasTarget.join(", ")}`);
```

## 5. Best Practices

### 5.1 Conditional Best Practices
```javascript
// ✅ Good - Explicit comparison
if (user.age >= 18) { }

// ❌ Avoid - Implicit comparison
if (user.age) { } // Bisa false jika age = 0

// ✅ Good - Early return
function processUser(user) {
    if (!user) {
        return "User not found";
    }
    if (!user.isActive) {
        return "User inactive";
    }
    // Process active user...
}

// ❌ Avoid - Deep nesting
function processUser(user) {
    if (user) {
        if (user.isActive) {
            // Process active user...
        }
    }
}
```

### 5.2 Loop Best Practices
```javascript
// ✅ Good - Cache array length
let items = ["a", "b", "c", "d", "e"];
for (let i = 0, len = items.length; i < len; i++) {
    console.log(items[i]);
}

// ✅ Good - Use appropriate loop type
// For arrays - use for...of
for (let item of items) {
    console.log(item);
}

// For objects - use for...in
for (let key in object) {
    console.log(key, object[key]);
}

// ✅ Good - Break early when possible
function findUser(users, id) {
    for (let user of users) {
        if (user.id === id) {
            return user; // Break early
        }
    }
    return null;
}
```

## 6. Tugas

1. **Kalkulator Sederhana**: Buat program kalkulator yang menerima input dua angka dan operator (+, -, *, /), lalu menampilkan hasil. Gunakan switch statement.

2. **Validasi Password**: Buat function untuk memvalidasi password dengan kriteria:
   - Minimal 8 karakter
   - Mengandung huruf besar dan kecil
   - Mengandung minimal satu angka
   - Mengandung karakter khusus (@, #, $, %, &)

3. **Analisis Data**: Buat program untuk menganalisis array berisi nilai ujian mahasiswa. Program harus menghitung:
   - Nilai tertinggi dan terendah
   - Rata-rata
   - Jumlah mahasiswa yang lulus (>= 70)
   - Distribusi grade (A, B, C, D, E)

4. **Pattern Generator**: Buat program yang dapat mencetak berbagai pattern berdasarkan input user (diamond, hollow square, number pyramid).

## Ringkasan

Dalam pertemuan ini kita telah mempelajari:

**Conditional (Percabangan):**
- If-else statements untuk kontrol alur program
- Switch statements untuk multiple conditions
- Operator ternary untuk conditional singkat
- Konsep truthy dan falsy values

**Looping (Perulangan):**
- For loop untuk iterasi dengan counter
- While loop untuk iterasi dengan kondisi
- Do-while loop yang minimal dieksekusi sekali
- For...of dan for...in untuk iterasi collections
- Break dan continue untuk kontrol loop

**Best Practices:**
- Gunakan early return untuk mengurangi nesting
- Cache array length dalam loop
- Pilih tipe loop yang sesuai dengan kebutuhan
- Gunakan break untuk optimasi performa