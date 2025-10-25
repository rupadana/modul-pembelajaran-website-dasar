# Pertemuan 11: Struktur Data Inti JavaScript - Array dan Object

## Tujuan Pembelajaran
Setelah mengikuti pertemuan ini, mahasiswa diharapkan dapat:
- Memahami dan menggunakan Array untuk menyimpan multiple data
- Menguasai berbagai method Array untuk manipulasi data
- Memahami dan membuat Object sebagai struktur data kompleks
- Menggunakan berbagai cara mengakses dan memanipulasi Object
- Menggabungkan Array dan Object untuk struktur data yang kompleks
- Memahami konsep destructuring untuk Array dan Object

## 1. Array

### 1.1 Pengenalan Array

Array adalah struktur data yang digunakan untuk menyimpan multiple nilai dalam satu variabel. Array di JavaScript bersifat dinamis dan dapat menyimpan berbagai tipe data.

#### Membuat Array:
```javascript
// Cara 1: Array literal (recommended)
let buah = ["apel", "jeruk", "mangga"];
let angka = [1, 2, 3, 4, 5];
let campuran = ["text", 42, true, null, undefined];

// Cara 2: Constructor Array
let kosong = new Array();
let ukuran = new Array(5); // Array dengan 5 elemen undefined
let isi = new Array("a", "b", "c");

// Cara 3: Array.from()
let dariString = Array.from("hello"); // ["h", "e", "l", "l", "o"]
let dariRange = Array.from({length: 5}, (v, i) => i + 1); // [1, 2, 3, 4, 5]

console.log(buah);     // ["apel", "jeruk", "mangga"]
console.log(angka);    // [1, 2, 3, 4, 5]
console.log(campuran); // ["text", 42, true, null, undefined]
```

### 1.2 Mengakses dan Memanipulasi Array

#### Mengakses Elemen:
```javascript
let colors = ["red", "green", "blue", "yellow"];

// Akses menggunakan index (dimulai dari 0)
console.log(colors[0]);  // "red"
console.log(colors[2]);  // "blue"
console.log(colors[-1]); // undefined (tidak seperti Python)

// Index negatif dengan slice
console.log(colors[colors.length - 1]); // "yellow" (elemen terakhir)

// Destructuring assignment
let [first, second, ...rest] = colors;
console.log(first);  // "red"
console.log(second); // "green"
console.log(rest);   // ["blue", "yellow"]
```

#### Mengubah Elemen:
```javascript
let numbers = [1, 2, 3, 4, 5];

// Mengubah elemen
numbers[0] = 10;
numbers[2] = 30;
console.log(numbers); // [10, 2, 30, 4, 5]

// Menambah elemen di index tertentu
numbers[10] = 100; // Akan membuat index 5-9 menjadi undefined
console.log(numbers); // [10, 2, 30, 4, 5, undefined, undefined, undefined, undefined, undefined, 100]
console.log(numbers.length); // 11
```

### 1.3 Method Array untuk Menambah/Menghapus

#### Menambah Elemen:
```javascript
let fruits = ["apple", "banana"];

// push() - menambah di akhir
fruits.push("orange");
console.log(fruits); // ["apple", "banana", "orange"]

// unshift() - menambah di awal
fruits.unshift("mango");
console.log(fruits); // ["mango", "apple", "banana", "orange"]

// splice() - menambah di posisi tertentu
fruits.splice(2, 0, "grape", "kiwi"); // posisi 2, hapus 0, tambah "grape" dan "kiwi"
console.log(fruits); // ["mango", "apple", "grape", "kiwi", "banana", "orange"]
```

#### Menghapus Elemen:
```javascript
let numbers = [1, 2, 3, 4, 5];

// pop() - menghapus elemen terakhir
let last = numbers.pop();
console.log(last);    // 5
console.log(numbers); // [1, 2, 3, 4]

// shift() - menghapus elemen pertama
let first = numbers.shift();
console.log(first);   // 1
console.log(numbers); // [2, 3, 4]

// splice() - menghapus elemen di posisi tertentu
let removed = numbers.splice(1, 2); // mulai index 1, hapus 2 elemen
console.log(removed); // [3, 4]
console.log(numbers); // [2]

// delete - menghapus tapi meninggalkan undefined (tidak disarankan)
let arr = [1, 2, 3, 4, 5];
delete arr[2];
console.log(arr); // [1, 2, undefined, 4, 5]
```

### 1.4 Method Array untuk Pencarian

#### indexOf() dan lastIndexOf():
```javascript
let colors = ["red", "green", "blue", "green", "yellow"];

console.log(colors.indexOf("green"));     // 1 (index pertama)
console.log(colors.lastIndexOf("green")); // 3 (index terakhir)
console.log(colors.indexOf("purple"));    // -1 (tidak ditemukan)

// Dengan parameter start position
console.log(colors.indexOf("green", 2)); // 3 (mulai cari dari index 2)
```

#### includes():
```javascript
let numbers = [1, 2, 3, 4, 5];

console.log(numbers.includes(3));  // true
console.log(numbers.includes(10)); // false

// Case sensitive untuk string
let words = ["Hello", "world"];
console.log(words.includes("hello")); // false
console.log(words.includes("Hello")); // true
```

#### find() dan findIndex():
```javascript
let users = [
    { id: 1, name: "Alice", age: 25 },
    { id: 2, name: "Bob", age: 30 },
    { id: 3, name: "Charlie", age: 35 }
];

// find() - mengembalikan elemen pertama yang memenuhi kondisi
let user = users.find(user => user.age > 28);
console.log(user); // { id: 2, name: "Bob", age: 30 }

// findIndex() - mengembalikan index elemen pertama yang memenuhi kondisi
let index = users.findIndex(user => user.name === "Charlie");
console.log(index); // 2

// some() - mengecek apakah ada elemen yang memenuhi kondisi
let hasAdult = users.some(user => user.age >= 30);
console.log(hasAdult); // true

// every() - mengecek apakah semua elemen memenuhi kondisi
let allAdults = users.every(user => user.age >= 18);
console.log(allAdults); // true
```

### 1.5 Method Array untuk Transformasi

#### map() - Transform setiap elemen:
```javascript
let numbers = [1, 2, 3, 4, 5];

// Mengalikan setiap elemen dengan 2
let doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8, 10]

// Transform object array
let users = [
    { firstName: "John", lastName: "Doe" },
    { firstName: "Jane", lastName: "Smith" }
];

let fullNames = users.map(user => `${user.firstName} ${user.lastName}`);
console.log(fullNames); // ["John Doe", "Jane Smith"]

// Map dengan index
let indexed = numbers.map((num, index) => `${index}: ${num}`);
console.log(indexed); // ["0: 1", "1: 2", "2: 3", "3: 4", "4: 5"]
```

#### filter() - Filter elemen berdasarkan kondisi:
```javascript
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// Filter angka genap
let evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers); // [2, 4, 6, 8, 10]

// Filter berdasarkan string length
let words = ["apple", "banana", "orange", "grape", "watermelon"];
let shortWords = words.filter(word => word.length <= 5);
console.log(shortWords); // ["apple", "grape"]

// Filter object
let products = [
    { name: "Laptop", price: 15000000, category: "Electronics" },
    { name: "Book", price: 50000, category: "Education" },
    { name: "Phone", price: 8000000, category: "Electronics" }
];

let electronics = products.filter(product => product.category === "Electronics");
let affordable = products.filter(product => product.price < 10000000);
```

#### reduce() - Reduce array menjadi single value:
```javascript
let numbers = [1, 2, 3, 4, 5];

// Menghitung total
let sum = numbers.reduce((acc, curr) => acc + curr, 0);
console.log(sum); // 15

// Mencari nilai maksimum
let max = numbers.reduce((acc, curr) => curr > acc ? curr : acc);
console.log(max); // 5

// Menghitung kemunculan elemen
let fruits = ["apple", "banana", "apple", "orange", "banana", "apple"];
let count = fruits.reduce((acc, fruit) => {
    acc[fruit] = (acc[fruit] || 0) + 1;
    return acc;
}, {});
console.log(count); // { apple: 3, banana: 2, orange: 1 }

// Flatten array
let nested = [[1, 2], [3, 4], [5, 6]];
let flattened = nested.reduce((acc, curr) => acc.concat(curr), []);
console.log(flattened); // [1, 2, 3, 4, 5, 6]
```

### 1.6 Method Array Lainnya

#### sort() - Mengurutkan array:
```javascript
let numbers = [3, 1, 4, 1, 5, 9, 2, 6];

// Sort default (sebagai string)
let sortedDefault = [...numbers].sort();
console.log(sortedDefault); // [1, 1, 2, 3, 4, 5, 6, 9]

// Sort numerik
let sortedNumeric = [...numbers].sort((a, b) => a - b);
console.log(sortedNumeric); // [1, 1, 2, 3, 4, 5, 6, 9]

// Sort descending
let sortedDesc = [...numbers].sort((a, b) => b - a);
console.log(sortedDesc); // [9, 6, 5, 4, 3, 2, 1, 1]

// Sort string array
let fruits = ["banana", "apple", "orange", "grape"];
fruits.sort();
console.log(fruits); // ["apple", "banana", "grape", "orange"]

// Sort object array
let students = [
    { name: "Alice", grade: 85 },
    { name: "Bob", grade: 92 },
    { name: "Charlie", grade: 78 }
];

students.sort((a, b) => b.grade - a.grade); // Sort by grade descending
console.log(students);
```

#### slice() dan concat():
```javascript
let arr = [1, 2, 3, 4, 5];

// slice() - membuat copy sebagian array (tidak mengubah original)
let portion = arr.slice(1, 4); // dari index 1 sampai 3 (4 tidak termasuk)
console.log(portion); // [2, 3, 4]
console.log(arr);     // [1, 2, 3, 4, 5] (original tidak berubah)

// concat() - menggabungkan array
let arr1 = [1, 2, 3];
let arr2 = [4, 5, 6];
let combined = arr1.concat(arr2);
console.log(combined); // [1, 2, 3, 4, 5, 6]

// Spread operator (ES6) - alternatif concat
let combined2 = [...arr1, ...arr2];
console.log(combined2); // [1, 2, 3, 4, 5, 6]
```

#### join() dan reverse():
```javascript
let words = ["Hello", "World", "JavaScript"];

// join() - menggabungkan elemen menjadi string
console.log(words.join());     // "Hello,World,JavaScript"
console.log(words.join(" "));  // "Hello World JavaScript"
console.log(words.join("-"));  // "Hello-World-JavaScript"

// reverse() - membalik urutan array (mengubah original)
let numbers = [1, 2, 3, 4, 5];
numbers.reverse();
console.log(numbers); // [5, 4, 3, 2, 1]

// Untuk tidak mengubah original, gunakan spread
let original = [1, 2, 3, 4, 5];
let reversed = [...original].reverse();
console.log(original); // [1, 2, 3, 4, 5]
console.log(reversed); // [5, 4, 3, 2, 1]
```

## 2. Object

### 2.1 Pengenalan Object

Object adalah struktur data yang menyimpan data dalam bentuk key-value pairs. Object sangat berguna untuk merepresentasikan entitas yang memiliki properti.

#### Membuat Object:
```javascript
// Object literal (paling umum)
let person = {
    name: "John Doe",
    age: 30,
    city: "Jakarta",
    isMarried: true
};

// Object constructor
let car = new Object();
car.brand = "Toyota";
car.model = "Camry";
car.year = 2023;

// Object.create()
let animal = Object.create(null);
animal.species = "Cat";
animal.name = "Fluffy";

// Constructor function
function Student(name, major, semester) {
    this.name = name;
    this.major = major;
    this.semester = semester;
}
let student1 = new Student("Alice", "Computer Science", 4);

console.log(person);  // { name: "John Doe", age: 30, city: "Jakarta", isMarried: true }
console.log(student1); // Student { name: "Alice", major: "Computer Science", semester: 4 }
```

### 2.2 Mengakses dan Memanipulasi Object

#### Mengakses Properti:
```javascript
let user = {
    firstName: "John",
    lastName: "Doe",
    age: 25,
    "full-name": "John Doe", // key dengan spasi/karakter khusus
    address: {
        street: "Jl. Sudirman",
        city: "Jakarta",
        zipCode: 12190
    }
};

// Dot notation
console.log(user.firstName); // "John"
console.log(user.age);       // 25

// Bracket notation
console.log(user["lastName"]);   // "Doe"
console.log(user["full-name"]);  // "John Doe"

// Dynamic property access
let prop = "age";
console.log(user[prop]); // 25

// Nested object access
console.log(user.address.city);     // "Jakarta"
console.log(user.address["street"]); // "Jl. Sudirman"

// Optional chaining (ES2020)
console.log(user?.address?.country?.name); // undefined (tidak error)
```

#### Mengubah dan Menambah Properti:
```javascript
let product = {
    name: "Laptop",
    price: 15000000
};

// Mengubah properti existing
product.price = 14000000;
product["name"] = "Gaming Laptop";

// Menambah properti baru
product.brand = "ASUS";
product.specs = {
    ram: "16GB",
    storage: "512GB SSD"
};

// Computed property names (ES6)
let key = "category";
product[key] = "Electronics";

console.log(product);
// {
//   name: "Gaming Laptop",
//   price: 14000000,
//   brand: "ASUS",
//   specs: { ram: "16GB", storage: "512GB SSD" },
//   category: "Electronics"
// }
```

#### Menghapus Properti:
```javascript
let obj = {
    a: 1,
    b: 2,
    c: 3
};

// delete operator
delete obj.b;
console.log(obj); // { a: 1, c: 3 }

// Set undefined (properti masih ada tapi nilainya undefined)
obj.c = undefined;
console.log(obj); // { a: 1, c: undefined }

// Mengecek apakah properti ada
console.log("a" in obj);           // true
console.log("b" in obj);           // false
console.log(obj.hasOwnProperty("a")); // true
```

### 2.3 Method dalam Object

#### Method sebagai Function:
```javascript
let calculator = {
    // Method dengan function expression
    add: function(a, b) {
        return a + b;
    },
    
    // Method shorthand (ES6)
    subtract(a, b) {
        return a - b;
    },
    
    // Arrow function (this behaves differently)
    multiply: (a, b) => a * b,
    
    // Method yang mengakses properti object
    currentResult: 0,
    
    setResult(value) {
        this.currentResult = value;
        return this;
    },
    
    addToResult(value) {
        this.currentResult += value;
        return this;
    },
    
    getResult() {
        return this.currentResult;
    }
};

console.log(calculator.add(5, 3));      // 8
console.log(calculator.subtract(10, 4)); // 6

// Method chaining
let result = calculator.setResult(10)
                      .addToResult(5)
                      .addToResult(3)
                      .getResult();
console.log(result); // 18
```

#### Getter dan Setter:
```javascript
let person = {
    _firstName: "John",
    _lastName: "Doe",
    
    // Getter
    get fullName() {
        return `${this._firstName} ${this._lastName}`;
    },
    
    // Setter
    set fullName(name) {
        let parts = name.split(" ");
        this._firstName = parts[0] || "";
        this._lastName = parts[1] || "";
    },
    
    get firstName() {
        return this._firstName;
    },
    
    set firstName(name) {
        if (typeof name === "string" && name.length > 0) {
            this._firstName = name;
        }
    }
};

console.log(person.fullName); // "John Doe"
person.fullName = "Jane Smith";
console.log(person._firstName); // "Jane"
console.log(person._lastName);  // "Smith"

person.firstName = "Alice";
console.log(person.fullName); // "Alice Smith"
```

### 2.4 Object Method dan Utilities

#### Object.keys(), Object.values(), Object.entries():
```javascript
let student = {
    name: "Alice",
    major: "Computer Science",
    semester: 4,
    gpa: 3.75
};

// Object.keys() - mendapatkan array key
let keys = Object.keys(student);
console.log(keys); // ["name", "major", "semester", "gpa"]

// Object.values() - mendapatkan array value
let values = Object.values(student);
console.log(values); // ["Alice", "Computer Science", 4, 3.75]

// Object.entries() - mendapatkan array [key, value]
let entries = Object.entries(student);
console.log(entries);
// [["name", "Alice"], ["major", "Computer Science"], ["semester", 4], ["gpa", 3.75]]

// Iterasi menggunakan for...in
for (let key in student) {
    console.log(`${key}: ${student[key]}`);
}

// Iterasi menggunakan Object.entries()
for (let [key, value] of Object.entries(student)) {
    console.log(`${key}: ${value}`);
}
```

#### Object.assign() dan Spread Operator:
```javascript
let target = { a: 1, b: 2 };
let source1 = { b: 3, c: 4 };
let source2 = { c: 5, d: 6 };

// Object.assign() - merge objects
let merged = Object.assign({}, target, source1, source2);
console.log(merged); // { a: 1, b: 3, c: 5, d: 6 }

// Spread operator (ES6) - lebih modern
let merged2 = { ...target, ...source1, ...source2 };
console.log(merged2); // { a: 1, b: 3, c: 5, d: 6 }

// Shallow copy
let original = { a: 1, b: { c: 2 } };
let copy = { ...original };
copy.b.c = 3;
console.log(original.b.c); // 3 (affected because of shallow copy)

// Deep copy (simple approach for JSON-serializable objects)
let deepCopy = JSON.parse(JSON.stringify(original));
```

#### Destructuring Assignment:
```javascript
let user = {
    id: 1,
    name: "John Doe",
    email: "john@example.com",
    address: {
        street: "123 Main St",
        city: "New York"
    },
    hobbies: ["reading", "gaming"]
};

// Basic destructuring
let { name, email } = user;
console.log(name);  // "John Doe"
console.log(email); // "john@example.com"

// Destructuring with rename
let { name: userName, id: userId } = user;
console.log(userName); // "John Doe"

// Destructuring with default values
let { phone = "No phone", age = 0 } = user;
console.log(phone); // "No phone"

// Nested destructuring
let { address: { city, street } } = user;
console.log(city);   // "New York"
console.log(street); // "123 Main St"

// Rest in destructuring
let { name: n, ...rest } = user;
console.log(rest); // { id: 1, email: "john@example.com", address: {...}, hobbies: [...] }

// Function parameter destructuring
function displayUser({ name, email, address: { city } }) {
    console.log(`${name} (${email}) from ${city}`);
}

displayUser(user); // "John Doe (john@example.com) from New York"
```

## 3. Kombinasi Array dan Object

### 3.1 Array of Objects
```javascript
let employees = [
    { 
        id: 1, 
        name: "Alice Johnson", 
        department: "Engineering", 
        salary: 120000,
        skills: ["JavaScript", "Python", "React"]
    },
    { 
        id: 2, 
        name: "Bob Smith", 
        department: "Marketing", 
        salary: 85000,
        skills: ["SEO", "Content Writing", "Analytics"]
    },
    { 
        id: 3, 
        name: "Charlie Brown", 
        department: "Engineering", 
        salary: 110000,
        skills: ["Java", "Spring Boot", "MySQL"]
    }
];

// Filter employees by department
let engineers = employees.filter(emp => emp.department === "Engineering");

// Calculate average salary
let avgSalary = employees.reduce((sum, emp) => sum + emp.salary, 0) / employees.length;

// Find employee by name
let alice = employees.find(emp => emp.name.includes("Alice"));

// Get all unique skills
let allSkills = employees
    .flatMap(emp => emp.skills)
    .filter((skill, index, arr) => arr.indexOf(skill) === index);
console.log(allSkills);

// Sort by salary descending
let sortedBySalary = [...employees].sort((a, b) => b.salary - a.salary);

// Group by department
let groupedByDept = employees.reduce((groups, emp) => {
    let dept = emp.department;
    if (!groups[dept]) {
        groups[dept] = [];
    }
    groups[dept].push(emp);
    return groups;
}, {});
console.log(groupedByDept);
```

### 3.2 Object with Arrays
```javascript
let company = {
    name: "TechCorp",
    founded: 2015,
    employees: [
        { name: "Alice", role: "Developer" },
        { name: "Bob", role: "Designer" },
        { name: "Charlie", role: "Manager" }
    ],
    departments: {
        engineering: {
            budget: 500000,
            head: "Alice",
            projects: ["Project A", "Project B"]
        },
        design: {
            budget: 200000,
            head: "Bob",
            projects: ["UI Redesign", "Brand Identity"]
        }
    },
    
    // Methods
    addEmployee(employee) {
        this.employees.push(employee);
    },
    
    getEmployeesByRole(role) {
        return this.employees.filter(emp => emp.role === role);
    },
    
    getTotalBudget() {
        return Object.values(this.departments)
               .reduce((total, dept) => total + dept.budget, 0);
    },
    
    getProjectCount() {
        return Object.values(this.departments)
               .reduce((total, dept) => total + dept.projects.length, 0);
    }
};

// Usage
company.addEmployee({ name: "Diana", role: "Developer" });
console.log(company.getEmployeesByRole("Developer"));
console.log(`Total Budget: $${company.getTotalBudget()}`);
console.log(`Total Projects: ${company.getProjectCount()}`);
```

### 3.3 Complex Data Manipulation
```javascript
// E-commerce data structure
let store = {
    products: [
        { id: 1, name: "Laptop", category: "Electronics", price: 15000000, stock: 10 },
        { id: 2, name: "Book", category: "Education", price: 50000, stock: 100 },
        { id: 3, name: "Phone", category: "Electronics", price: 8000000, stock: 25 }
    ],
    
    customers: [
        { id: 1, name: "John", email: "john@email.com", orders: [] },
        { id: 2, name: "Jane", email: "jane@email.com", orders: [] }
    ],
    
    orders: [
        { 
            id: 1, 
            customerId: 1, 
            items: [
                { productId: 1, quantity: 1, price: 15000000 },
                { productId: 2, quantity: 2, price: 50000 }
            ],
            total: 15100000,
            date: new Date('2023-01-15')
        }
    ],
    
    // Analytics methods
    getMonthlySales(year, month) {
        return this.orders
            .filter(order => {
                let orderDate = new Date(order.date);
                return orderDate.getFullYear() === year && 
                       orderDate.getMonth() === month - 1;
            })
            .reduce((total, order) => total + order.total, 0);
    },
    
    getTopProducts(limit = 5) {
        let productSales = {};
        
        this.orders.forEach(order => {
            order.items.forEach(item => {
                if (!productSales[item.productId]) {
                    productSales[item.productId] = 0;
                }
                productSales[item.productId] += item.quantity;
            });
        });
        
        return Object.entries(productSales)
            .map(([productId, quantity]) => ({
                product: this.products.find(p => p.id == productId),
                totalSold: quantity
            }))
            .sort((a, b) => b.totalSold - a.totalSold)
            .slice(0, limit);
    },
    
    getCustomerValue(customerId) {
        return this.orders
            .filter(order => order.customerId === customerId)
            .reduce((total, order) => total + order.total, 0);
    }
};

// Usage examples
console.log("January 2023 Sales:", store.getMonthlySales(2023, 1));
console.log("Top Products:", store.getTopProducts(3));
console.log("Customer 1 Total Value:", store.getCustomerValue(1));
```

## 4. Latihan Praktik

### Latihan 1: Student Management System
```javascript
let studentSystem = {
    students: [],
    
    addStudent(student) {
        student.id = this.students.length + 1;
        student.courses = student.courses || [];
        this.students.push(student);
        return student.id;
    },
    
    addCourse(studentId, course) {
        let student = this.students.find(s => s.id === studentId);
        if (student) {
            student.courses.push({
                name: course.name,
                credits: course.credits,
                grade: course.grade || null
            });
            return true;
        }
        return false;
    },
    
    calculateGPA(studentId) {
        let student = this.students.find(s => s.id === studentId);
        if (!student || student.courses.length === 0) return 0;
        
        let totalPoints = 0;
        let totalCredits = 0;
        
        student.courses.forEach(course => {
            if (course.grade) {
                let points = this.gradeToPoints(course.grade);
                totalPoints += points * course.credits;
                totalCredits += course.credits;
            }
        });
        
        return totalCredits > 0 ? (totalPoints / totalCredits).toFixed(2) : 0;
    },
    
    gradeToPoints(grade) {
        const gradeMap = { 'A': 4, 'B': 3, 'C': 2, 'D': 1, 'E': 0 };
        return gradeMap[grade] || 0;
    },
    
    getStudentsByMajor(major) {
        return this.students.filter(student => student.major === major);
    },
    
    getTopStudents(limit = 5) {
        return this.students
            .map(student => ({
                ...student,
                gpa: parseFloat(this.calculateGPA(student.id))
            }))
            .sort((a, b) => b.gpa - a.gpa)
            .slice(0, limit);
    }
};

// Test the system
let id1 = studentSystem.addStudent({
    name: "Alice Johnson",
    major: "Computer Science",
    year: 2
});

studentSystem.addCourse(id1, { name: "Data Structures", credits: 3, grade: "A" });
studentSystem.addCourse(id1, { name: "Database", credits: 3, grade: "B" });
studentSystem.addCourse(id1, { name: "Web Programming", credits: 2, grade: "A" });

console.log("Alice's GPA:", studentSystem.calculateGPA(id1));
console.log("Top Students:", studentSystem.getTopStudents());
```

### Latihan 2: Library Management
```javascript
class Library {
    constructor() {
        this.books = [];
        this.members = [];
        this.borrowedBooks = [];
    }
    
    addBook(book) {
        this.books.push({
            id: this.books.length + 1,
            title: book.title,
            author: book.author,
            isbn: book.isbn,
            copies: book.copies || 1,
            availableCopies: book.copies || 1
        });
    }
    
    addMember(member) {
        this.members.push({
            id: this.members.length + 1,
            name: member.name,
            email: member.email,
            joinDate: new Date(),
            borrowedBooks: []
        });
    }
    
    borrowBook(memberId, bookId) {
        let member = this.members.find(m => m.id === memberId);
        let book = this.books.find(b => b.id === bookId);
        
        if (!member || !book) return { success: false, message: "Member or book not found" };
        if (book.availableCopies <= 0) return { success: false, message: "No copies available" };
        if (member.borrowedBooks.length >= 3) return { success: false, message: "Borrowing limit exceeded" };
        
        // Create borrow record
        let borrowRecord = {
            id: this.borrowedBooks.length + 1,
            memberId: memberId,
            bookId: bookId,
            borrowDate: new Date(),
            returnDate: null,
            dueDate: new Date(Date.now() + 14 * 24 * 60 * 60 * 1000) // 14 days from now
        };
        
        this.borrowedBooks.push(borrowRecord);
        member.borrowedBooks.push(borrowRecord.id);
        book.availableCopies--;
        
        return { success: true, message: "Book borrowed successfully", borrowId: borrowRecord.id };
    }
    
    returnBook(borrowId) {
        let borrowRecord = this.borrowedBooks.find(b => b.id === borrowId && !b.returnDate);
        if (!borrowRecord) return { success: false, message: "Borrow record not found" };
        
        let member = this.members.find(m => m.id === borrowRecord.memberId);
        let book = this.books.find(b => b.id === borrowRecord.bookId);
        
        borrowRecord.returnDate = new Date();
        member.borrowedBooks = member.borrowedBooks.filter(id => id !== borrowId);
        book.availableCopies++;
        
        // Calculate fine if overdue
        let fine = 0;
        if (borrowRecord.returnDate > borrowRecord.dueDate) {
            let daysOverdue = Math.ceil((borrowRecord.returnDate - borrowRecord.dueDate) / (24 * 60 * 60 * 1000));
            fine = daysOverdue * 1000; // Rp 1000 per day
        }
        
        return { 
            success: true, 
            message: "Book returned successfully", 
            fine: fine,
            daysOverdue: fine > 0 ? Math.ceil((borrowRecord.returnDate - borrowRecord.dueDate) / (24 * 60 * 60 * 1000)) : 0
        };
    }
    
    searchBooks(query) {
        return this.books.filter(book => 
            book.title.toLowerCase().includes(query.toLowerCase()) ||
            book.author.toLowerCase().includes(query.toLowerCase())
        );
    }
    
    getOverdueBooks() {
        let now = new Date();
        return this.borrowedBooks
            .filter(borrow => !borrow.returnDate && borrow.dueDate < now)
            .map(borrow => ({
                ...borrow,
                book: this.books.find(b => b.id === borrow.bookId),
                member: this.members.find(m => m.id === borrow.memberId),
                daysOverdue: Math.ceil((now - borrow.dueDate) / (24 * 60 * 60 * 1000))
            }));
    }
}

// Test the library system
let library = new Library();

// Add books
library.addBook({ title: "JavaScript: The Good Parts", author: "Douglas Crockford", isbn: "978-0596517748", copies: 3 });
library.addBook({ title: "Clean Code", author: "Robert Martin", isbn: "978-0132350884", copies: 2 });

// Add members
library.addMember({ name: "Alice Johnson", email: "alice@email.com" });
library.addMember({ name: "Bob Smith", email: "bob@email.com" });

// Borrow books
console.log(library.borrowBook(1, 1));
console.log(library.borrowBook(2, 1));

// Search books
console.log("JavaScript books:", library.searchBooks("JavaScript"));

// Check overdue books (would need to manipulate dates for testing)
console.log("Overdue books:", library.getOverdueBooks());
```

## 5. Best Practices

### 5.1 Array Best Practices
```javascript
// ✅ Use const for arrays that won't be reassigned
const fruits = ["apple", "banana"];
fruits.push("orange"); // OK - modifying content
// fruits = []; // Error - reassigning

// ✅ Use descriptive names
const userIds = [1, 2, 3, 4];
const activeUsers = users.filter(user => user.isActive);

// ✅ Use array methods instead of loops when possible
// Good
const doubled = numbers.map(n => n * 2);
const evens = numbers.filter(n => n % 2 === 0);

// Avoid
const doubled2 = [];
for (let i = 0; i < numbers.length; i++) {
    doubled2.push(numbers[i] * 2);
}

// ✅ Use spread operator for copying
const originalArray = [1, 2, 3];
const copiedArray = [...originalArray];

// ✅ Check if array before using array methods
function processItems(items) {
    if (!Array.isArray(items)) {
        return [];
    }
    return items.map(item => item.toUpperCase());
}
```

### 5.2 Object Best Practices
```javascript
// ✅ Use object shorthand when possible
const name = "John";
const age = 30;

// Good
const person = { name, age };

// Avoid
const person2 = { name: name, age: age };

// ✅ Use destructuring for cleaner code
// Good
function greetUser({ name, age }) {
    return `Hello ${name}, you are ${age} years old`;
}

// Avoid
function greetUser2(user) {
    return `Hello ${user.name}, you are ${user.age} years old`;
}

// ✅ Use optional chaining for nested properties
const cityName = user?.address?.city ?? "Unknown";

// ✅ Use meaningful property names
// Good
const user = {
    firstName: "John",
    lastName: "Doe",
    isActive: true
};

// Avoid
const user2 = {
    fName: "John",
    lName: "Doe",
    active: true
};
```

## 6. Tugas

1. **Todo List Manager**: Buat aplikasi todo list dengan fitur:
   - Menambah/menghapus todo
   - Menandai sebagai complete/incomplete
   - Filter berdasarkan status
   - Mencari todo berdasarkan teks

2. **Shopping Cart System**: Buat sistem shopping cart dengan fitur:
   - Menambah/menghapus produk
   - Update quantity
   - Hitung total harga dengan diskon
   - Validasi stok produk

3. **Grade Book**: Buat aplikasi untuk mengelola nilai mahasiswa dengan fitur:
   - Input nilai per mata kuliah
   - Hitung rata-rata per mahasiswa
   - Hitung rata-rata per mata kuliah
   - Ranking mahasiswa berdasarkan GPA

4. **Contact Manager**: Buat aplikasi manajemen kontak dengan fitur:
   - Tambah/edit/hapus kontak
   - Cari kontak berdasarkan nama/email
   - Group kontak berdasarkan kategori
   - Export data ke format JSON

## Ringkasan

Dalam pertemuan ini kita telah mempelajari:

**Array:**
- Membuat dan mengakses array
- Method untuk manipulasi: push, pop, shift, unshift, splice
- Method untuk pencarian: indexOf, find, includes
- Method untuk transformasi: map, filter, reduce
- Method lainnya: sort, slice, concat, join

**Object:**
- Membuat dan mengakses object
- Dot notation vs bracket notation
- Method dalam object dan this keyword
- Getter dan setter
- Object utilities: Object.keys(), Object.values(), Object.entries()
- Destructuring assignment

**Kombinasi Array & Object:**
- Array of objects untuk data collection
- Object with arrays untuk struktur data kompleks
- Method chaining untuk operasi yang efisien

**Best Practices:**
- Gunakan method array yang tepat untuk setiap kebutuhan
- Manfaatkan destructuring untuk kode yang lebih bersih
- Gunakan optional chaining untuk akses property yang aman
- Pilih struktur data yang tepat sesuai kebutuhan aplikasi