# Pertemuan 12: Fungsi JavaScript

## Tujuan Pembelajaran
Setelah mengikuti pertemuan ini, mahasiswa diharapkan dapat:
- Memahami konsep dan kegunaan fungsi dalam JavaScript
- Membuat fungsi dengan berbagai cara (declaration, expression, arrow function)
- Menggunakan parameter dan return value dengan efektif
- Memahami scope dan closure dalam fungsi
- Menerapkan higher-order functions dan callback
- Menggunakan fungsi untuk modular programming

## 1. Pengenalan Fungsi

### 1.1 Apa itu Fungsi?

Fungsi adalah blok kode yang dapat digunakan kembali untuk melakukan tugas tertentu. Fungsi membantu menghindari pengulangan kode dan membuat program lebih terorganisir.

#### Mengapa Menggunakan Fungsi?
```javascript
// Tanpa fungsi - kode berulang
let radius1 = 5;
let area1 = 3.14159 * radius1 * radius1;
console.log(`Area circle 1: ${area1}`);

let radius2 = 10;
let area2 = 3.14159 * radius2 * radius2;
console.log(`Area circle 2: ${area2}`);

let radius3 = 7;
let area3 = 3.14159 * radius3 * radius3;
console.log(`Area circle 3: ${area3}`);

// Dengan fungsi - kode reusable
function calculateCircleArea(radius) {
    return 3.14159 * radius * radius;
}

console.log(`Area circle 1: ${calculateCircleArea(5)}`);
console.log(`Area circle 2: ${calculateCircleArea(10)}`);
console.log(`Area circle 3: ${calculateCircleArea(7)}`);
```

### 1.2 Anatomi Fungsi

```javascript
function functionName(parameter1, parameter2) {
    // Function body
    let result = parameter1 + parameter2;
    return result; // Return value (optional)
}

// Function call
let sum = functionName(5, 3);
```

## 2. Deklarasi Fungsi

### 2.1 Function Declaration

```javascript
// Function declaration
function greet(name) {
    return `Hello, ${name}!`;
}

// Characteristics of function declaration:
// 1. Hoisted - dapat dipanggil sebelum dideklarasikan
console.log(sayHello("World")); // "Hello, World!" - works!

function sayHello(name) {
    return `Hello, ${name}!`;
}

// 2. Function name is mandatory
// 3. Creates a function in the current scope
```

### 2.2 Function Expression

```javascript
// Function expression
const greet = function(name) {
    return `Hello, ${name}!`;
};

// Named function expression
const greet2 = function greetUser(name) {
    return `Hello, ${name}!`;
};

// Characteristics:
// 1. Not hoisted - cannot be called before declaration
// console.log(sayGoodbye("World")); // Error!
const sayGoodbye = function(name) {
    return `Goodbye, ${name}!`;
};

// 2. Function name is optional
// 3. Often assigned to variables
// 4. Can be used as values (passed to other functions, returned from functions)
```

### 2.3 Arrow Functions (ES6)

```javascript
// Basic arrow function syntax
const add = (a, b) => {
    return a + b;
};

// Shorthand for single expression (implicit return)
const multiply = (a, b) => a * b;

// Single parameter (parentheses optional)
const square = x => x * x;
const square2 = (x) => x * x; // Same as above

// No parameters
const getRandomNumber = () => Math.random();

// Multiple lines
const processData = (data) => {
    let processed = data.map(item => item * 2);
    let filtered = processed.filter(item => item > 10);
    return filtered;
};

// Arrow functions in array methods
let numbers = [1, 2, 3, 4, 5];
let doubled = numbers.map(n => n * 2);
let evens = numbers.filter(n => n % 2 === 0);
let sum = numbers.reduce((acc, n) => acc + n, 0);

console.log(doubled); // [2, 4, 6, 8, 10]
console.log(evens);   // [2, 4]
console.log(sum);     // 15
```

#### Perbedaan Arrow Functions vs Regular Functions:

```javascript
// 1. 'this' binding berbeda
let obj = {
    name: "John",
    
    // Regular function - 'this' refers to obj
    sayHello: function() {
        console.log(`Hello, I'm ${this.name}`);
    },
    
    // Arrow function - 'this' refers to outer scope
    sayGoodbye: () => {
        console.log(`Goodbye, I'm ${this.name}`); // undefined
    },
    
    // Method shorthand (recommended for object methods)
    introduce() {
        console.log(`Hi, I'm ${this.name}`);
    }
};

obj.sayHello();    // "Hello, I'm John"
obj.sayGoodbye();  // "Goodbye, I'm undefined"
obj.introduce();   // "Hi, I'm John"

// 2. Arrow functions cannot be constructors
const Person = (name) => {
    this.name = name;
};
// const john = new Person("John"); // TypeError!

// 3. No arguments object in arrow functions
function regularFunc() {
    console.log(arguments); // Works - has arguments object
}

const arrowFunc = () => {
    // console.log(arguments); // ReferenceError!
    console.log(...arguments); // Use rest parameters instead
};

// Better with rest parameters
const betterArrowFunc = (...args) => {
    console.log(args);
};
```

## 3. Parameter dan Arguments

### 3.1 Basic Parameters

```javascript
// Function with parameters
function createUser(name, age, email) {
    return {
        name: name,
        age: age,
        email: email,
        createdAt: new Date()
    };
}

// Calling with arguments
let user1 = createUser("Alice", 25, "alice@email.com");
let user2 = createUser("Bob", 30); // email will be undefined

console.log(user1);
console.log(user2);
```

### 3.2 Default Parameters (ES6)

```javascript
// Default parameters
function greet(name = "Guest", greeting = "Hello") {
    return `${greeting}, ${name}!`;
}

console.log(greet());                    // "Hello, Guest!"
console.log(greet("Alice"));             // "Hello, Alice!"
console.log(greet("Bob", "Hi"));         // "Hi, Bob!"

// Default with expressions
function createArray(length = 5, fillValue = Math.random()) {
    return new Array(length).fill(fillValue);
}

// Default parameters can reference previous parameters
function calculatePrice(price, tax = price * 0.1) {
    return price + tax;
}

console.log(calculatePrice(100)); // 110 (100 + 10)

// Complex default values
function processOptions(options = {}) {
    let defaults = {
        method: 'GET',
        timeout: 5000,
        headers: {}
    };
    
    return { ...defaults, ...options };
}

console.log(processOptions()); // Uses all defaults
console.log(processOptions({ method: 'POST', timeout: 3000 }));
```

### 3.3 Rest Parameters

```javascript
// Rest parameters - collect remaining arguments
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3));       // 6
console.log(sum(1, 2, 3, 4, 5)); // 15
console.log(sum());              // 0

// Rest parameters with other parameters
function introduce(firstName, lastName, ...hobbies) {
    console.log(`Name: ${firstName} ${lastName}`);
    console.log(`Hobbies: ${hobbies.join(", ")}`);
}

introduce("John", "Doe", "reading", "gaming", "cooking");
// Name: John Doe
// Hobbies: reading, gaming, cooking

// Rest parameters in destructuring
function processData({ name, age, ...otherInfo }) {
    console.log(`Processing ${name}, age ${age}`);
    console.log('Other info:', otherInfo);
}

processData({
    name: "Alice",
    age: 25,
    city: "Jakarta",
    job: "Developer"
});
```

### 3.4 Spread Operator dengan Functions

```javascript
// Spread operator untuk function arguments
function add(a, b, c) {
    return a + b + c;
}

let numbers = [1, 2, 3];
console.log(add(...numbers)); // Same as add(1, 2, 3)

// Combining arrays
function combineArrays(arr1, arr2, ...otherArrays) {
    return [...arr1, ...arr2, ...otherArrays.flat()];
}

let result = combineArrays([1, 2], [3, 4], [5, 6], [7, 8]);
console.log(result); // [1, 2, 3, 4, 5, 6, 7, 8]

// Finding max/min in arrays
let scores = [85, 92, 78, 96, 88];
console.log(Math.max(...scores)); // 96
console.log(Math.min(...scores)); // 78
```

### 3.5 Destructuring Parameters

```javascript
// Object destructuring in parameters
function createProfile({ name, age, email, city = "Unknown" }) {
    return `${name} (${age}) from ${city} - ${email}`;
}

let user = {
    name: "Alice",
    age: 25,
    email: "alice@email.com",
    city: "Jakarta"
};

console.log(createProfile(user));

// Array destructuring in parameters
function calculateDistance([x1, y1], [x2, y2]) {
    return Math.sqrt((x2 - x1) ** 2 + (y2 - y1) ** 2);
}

let point1 = [0, 0];
let point2 = [3, 4];
console.log(calculateDistance(point1, point2)); // 5

// Complex destructuring
function processOrder({
    id,
    customer: { name, email },
    items = [],
    shipping: { address, cost = 0 } = {}
}) {
    console.log(`Order #${id} for ${name} (${email})`);
    console.log(`Items: ${items.length}`);
    console.log(`Shipping to: ${address}, Cost: ${cost}`);
}

let order = {
    id: 12345,
    customer: { name: "John Doe", email: "john@email.com" },
    items: ["laptop", "mouse"],
    shipping: { address: "123 Main St", cost: 10 }
};

processOrder(order);
```

## 4. Return Value

### 4.1 Basic Return

```javascript
// Function with return value
function add(a, b) {
    return a + b;
}

let result = add(5, 3);
console.log(result); // 8

// Function without return (returns undefined)
function logMessage(message) {
    console.log(message);
    // implicit return undefined
}

let noReturn = logMessage("Hello");
console.log(noReturn); // undefined

// Early return
function processAge(age) {
    if (age < 0) {
        return "Invalid age";
    }
    
    if (age < 18) {
        return "Minor";
    }
    
    if (age < 60) {
        return "Adult";
    }
    
    return "Senior";
}

console.log(processAge(-5)); // "Invalid age"
console.log(processAge(16)); // "Minor"
console.log(processAge(30)); // "Adult"
console.log(processAge(65)); // "Senior"
```

### 4.2 Multiple Return Values

```javascript
// Returning objects
function getPersonInfo(person) {
    return {
        fullName: `${person.firstName} ${person.lastName}`,
        age: person.age,
        isAdult: person.age >= 18,
        initials: `${person.firstName[0]}${person.lastName[0]}`
    };
}

let info = getPersonInfo({ firstName: "John", lastName: "Doe", age: 25 });
console.log(info);

// Returning arrays
function getMinMax(numbers) {
    return [Math.min(...numbers), Math.max(...numbers)];
}

let [min, max] = getMinMax([3, 1, 4, 1, 5, 9, 2, 6]);
console.log(min, max); // 1 9

// Returning functions (higher-order functions)
function createMultiplier(factor) {
    return function(number) {
        return number * factor;
    };
}

let double = createMultiplier(2);
let triple = createMultiplier(3);

console.log(double(5)); // 10
console.log(triple(5)); // 15
```

### 4.3 Conditional Returns

```javascript
// Function with multiple return paths
function calculateDiscount(price, customerType) {
    if (customerType === "premium") {
        return price * 0.8; // 20% discount
    }
    
    if (customerType === "regular" && price > 100) {
        return price * 0.9; // 10% discount for orders > 100
    }
    
    return price; // No discount
}

console.log(calculateDiscount(150, "premium"));  // 120
console.log(calculateDiscount(150, "regular"));  // 135
console.log(calculateDiscount(50, "regular"));   // 50

// Using ternary for simple conditions
function getAbsoluteValue(number) {
    return number < 0 ? -number : number;
}

// Function returning different types based on input
function processInput(input) {
    if (typeof input === "number") {
        return input * 2;
    }
    
    if (typeof input === "string") {
        return input.toUpperCase();
    }
    
    if (Array.isArray(input)) {
        return input.length;
    }
    
    return null;
}

console.log(processInput(5));        // 10
console.log(processInput("hello"));  // "HELLO"
console.log(processInput([1,2,3]));  // 3
console.log(processInput({}));       // null
```

## 5. Scope dan Closure

### 5.1 Function Scope

```javascript
// Global scope
let globalVar = "I'm global";

function outerFunction() {
    // Function scope
    let outerVar = "I'm in outer function";
    
    function innerFunction() {
        // Inner function scope
        let innerVar = "I'm in inner function";
        
        console.log(globalVar); // Accessible
        console.log(outerVar);  // Accessible
        console.log(innerVar);  // Accessible
    }
    
    innerFunction();
    // console.log(innerVar); // Error! Not accessible here
}

outerFunction();

// Block scope (let/const)
function scopeExample() {
    let x = 1;
    
    if (true) {
        let y = 2;
        const z = 3;
        var w = 4;
        
        console.log(x); // 1 - accessible
        console.log(y); // 2 - accessible
    }
    
    console.log(x); // 1 - accessible
    // console.log(y); // Error! Block scoped
    // console.log(z); // Error! Block scoped
    console.log(w); // 4 - var is function scoped
}

scopeExample();
```

### 5.2 Closure

Closure adalah kemampuan fungsi untuk mengakses variabel dari scope luar bahkan setelah fungsi luar selesai dieksekusi.

```javascript
// Basic closure example
function createCounter() {
    let count = 0;
    
    return function() {
        count++;
        return count;
    };
}

let counter1 = createCounter();
let counter2 = createCounter();

console.log(counter1()); // 1
console.log(counter1()); // 2
console.log(counter2()); // 1 (independent counter)
console.log(counter1()); // 3

// Closure with parameters
function createGreeter(greeting) {
    return function(name) {
        return `${greeting}, ${name}!`;
    };
}

let sayHello = createGreeter("Hello");
let sayHi = createGreeter("Hi");

console.log(sayHello("Alice")); // "Hello, Alice!"
console.log(sayHi("Bob"));      // "Hi, Bob!"

// Practical closure example - Private variables
function createBankAccount(initialBalance = 0) {
    let balance = initialBalance;
    
    return {
        deposit(amount) {
            if (amount > 0) {
                balance += amount;
                return `Deposited ${amount}. New balance: ${balance}`;
            }
            return "Invalid amount";
        },
        
        withdraw(amount) {
            if (amount > 0 && amount <= balance) {
                balance -= amount;
                return `Withdrawn ${amount}. New balance: ${balance}`;
            }
            return "Invalid amount or insufficient funds";
        },
        
        getBalance() {
            return balance;
        }
    };
}

let account = createBankAccount(100);
console.log(account.deposit(50));   // "Deposited 50. New balance: 150"
console.log(account.withdraw(30));  // "Withdrawn 30. New balance: 120"
console.log(account.getBalance());  // 120
// console.log(account.balance);    // undefined - balance is private
```

### 5.3 IIFE (Immediately Invoked Function Expression)

```javascript
// Basic IIFE
(function() {
    console.log("IIFE executed!");
})();

// IIFE with parameters
(function(name) {
    console.log(`Hello, ${name}!`);
})("World");

// IIFE with return value
let result = (function(x, y) {
    return x * y;
})(5, 3);
console.log(result); // 15

// IIFE for module pattern
let calculator = (function() {
    let history = [];
    
    function add(a, b) {
        let result = a + b;
        history.push(`${a} + ${b} = ${result}`);
        return result;
    }
    
    function subtract(a, b) {
        let result = a - b;
        history.push(`${a} - ${b} = ${result}`);
        return result;
    }
    
    function getHistory() {
        return [...history];
    }
    
    // Public API
    return {
        add,
        subtract,
        getHistory
    };
})();

console.log(calculator.add(5, 3));      // 8
console.log(calculator.subtract(10, 4)); // 6
console.log(calculator.getHistory());   // ["5 + 3 = 8", "10 - 4 = 6"]
```

## 6. Higher-Order Functions dan Callbacks

### 6.1 Callback Functions

```javascript
// Function yang menerima function lain sebagai parameter
function processData(data, callback) {
    console.log("Processing data...");
    let result = data.map(item => item * 2);
    callback(result);
}

function displayResult(result) {
    console.log("Result:", result);
}

function logResult(result) {
    console.log("Logged:", result.join(", "));
}

let numbers = [1, 2, 3, 4, 5];
processData(numbers, displayResult); // Result: [2, 4, 6, 8, 10]
processData(numbers, logResult);     // Logged: 2, 4, 6, 8, 10

// Anonymous callback
processData(numbers, function(result) {
    console.log("Anonymous callback:", result.length);
});

// Arrow function callback
processData(numbers, (result) => {
    console.log("Arrow callback:", Math.max(...result));
});
```

### 6.2 Array Methods sebagai Higher-Order Functions

```javascript
let students = [
    { name: "Alice", grade: 85 },
    { name: "Bob", grade: 92 },
    { name: "Charlie", grade: 78 },
    { name: "Diana", grade: 96 }
];

// map - transform data
let names = students.map(student => student.name);
let grades = students.map(student => student.grade);

// filter - filter data
let highAchievers = students.filter(student => student.grade >= 90);
let passingStudents = students.filter(student => student.grade >= 75);

// sort - sort data
let sortedByGrade = [...students].sort((a, b) => b.grade - a.grade);
let sortedByName = [...students].sort((a, b) => a.name.localeCompare(b.name));

// forEach - iterate without return
students.forEach((student, index) => {
    console.log(`${index + 1}. ${student.name}: ${student.grade}`);
});

// find - find first match
let topStudent = students.find(student => student.grade >= 95);
let averageStudent = students.find(student => student.grade >= 80 && student.grade < 90);

// reduce - aggregate data
let totalGrades = students.reduce((sum, student) => sum + student.grade, 0);
let averageGrade = totalGrades / students.length;

console.log("Names:", names);
console.log("High achievers:", highAchievers);
console.log("Top student:", topStudent);
console.log("Average grade:", averageGrade);
```

### 6.3 Creating Custom Higher-Order Functions

```javascript
// Function yang mengembalikan function
function createValidator(type) {
    switch(type) {
        case "email":
            return (email) => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
        case "phone":
            return (phone) => /^\d{10,12}$/.test(phone.replace(/\D/g, ""));
        case "password":
            return (password) => password.length >= 8 && /[A-Z]/.test(password) && /[0-9]/.test(password);
        default:
            return () => false;
    }
}

let emailValidator = createValidator("email");
let phoneValidator = createValidator("phone");
let passwordValidator = createValidator("password");

console.log(emailValidator("test@email.com")); // true
console.log(phoneValidator("081234567890"));   // true
console.log(passwordValidator("Password123"));  // true

// Function composition
function compose(...functions) {
    return function(value) {
        return functions.reduceRight((acc, fn) => fn(acc), value);
    };
}

let addOne = x => x + 1;
let double = x => x * 2;
let square = x => x * x;

let composedFunction = compose(square, double, addOne);
console.log(composedFunction(3)); // ((3 + 1) * 2) ^ 2 = 64

// Currying
function curry(fn) {
    return function curried(...args) {
        if (args.length >= fn.length) {
            return fn.apply(this, args);
        } else {
            return function(...args2) {
                return curried.apply(this, args.concat(args2));
            };
        }
    };
}

function add(a, b, c) {
    return a + b + c;
}

let curriedAdd = curry(add);
console.log(curriedAdd(1)(2)(3)); // 6
console.log(curriedAdd(1, 2)(3)); // 6
console.log(curriedAdd(1)(2, 3)); // 6
```

## 7. Recursive Functions

### 7.1 Basic Recursion

```javascript
// Factorial function
function factorial(n) {
    // Base case
    if (n <= 1) {
        return 1;
    }
    
    // Recursive case
    return n * factorial(n - 1);
}

console.log(factorial(5)); // 120 (5 * 4 * 3 * 2 * 1)

// Fibonacci sequence
function fibonacci(n) {
    if (n <= 1) {
        return n;
    }
    
    return fibonacci(n - 1) + fibonacci(n - 2);
}

console.log(fibonacci(10)); // 55

// Sum of array
function sumArray(arr, index = 0) {
    if (index >= arr.length) {
        return 0;
    }
    
    return arr[index] + sumArray(arr, index + 1);
}

console.log(sumArray([1, 2, 3, 4, 5])); // 15
```

### 7.2 Tree Traversal with Recursion

```javascript
// Tree structure example
let familyTree = {
    name: "Grandpa",
    children: [
        {
            name: "Father",
            children: [
                { name: "Child 1", children: [] },
                { name: "Child 2", children: [] }
            ]
        },
        {
            name: "Uncle",
            children: [
                { name: "Cousin", children: [] }
            ]
        }
    ]
};

// Recursive tree traversal
function printFamily(person, level = 0) {
    let indent = "  ".repeat(level);
    console.log(indent + person.name);
    
    person.children.forEach(child => {
        printFamily(child, level + 1);
    });
}

printFamily(familyTree);

// Count total family members
function countMembers(person) {
    let count = 1; // Count current person
    
    person.children.forEach(child => {
        count += countMembers(child);
    });
    
    return count;
}

console.log("Total family members:", countMembers(familyTree)); // 6

// Find person in tree
function findPerson(tree, targetName) {
    if (tree.name === targetName) {
        return tree;
    }
    
    for (let child of tree.children) {
        let found = findPerson(child, targetName);
        if (found) {
            return found;
        }
    }
    
    return null;
}

let found = findPerson(familyTree, "Cousin");
console.log("Found:", found);
```

## 8. Function Best Practices

### 8.1 Naming dan Structure

```javascript
// ✅ Good - Descriptive function names
function calculateTotalPrice(items, taxRate) {
    let subtotal = items.reduce((sum, item) => sum + item.price, 0);
    return subtotal * (1 + taxRate);
}

// ❌ Avoid - Unclear function name
function calc(x, y) {
    return x.reduce((a, b) => a + b.p, 0) * (1 + y);
}

// ✅ Good - Single responsibility
function validateEmail(email) {
    return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
}

function validatePassword(password) {
    return password.length >= 8 && 
           /[A-Z]/.test(password) && 
           /[0-9]/.test(password);
}

// ❌ Avoid - Multiple responsibilities
function validateUser(email, password) {
    let emailValid = /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
    let passwordValid = password.length >= 8 && 
                       /[A-Z]/.test(password) && 
                       /[0-9]/.test(password);
    return { emailValid, passwordValid };
}

// ✅ Good - Pure functions (no side effects)
function addNumbers(a, b) {
    return a + b;
}

// ❌ Avoid - Functions with side effects
let total = 0;
function addToTotal(value) {
    total += value; // Side effect - modifies external state
    return total;
}
```

### 8.2 Error Handling

```javascript
// Function dengan error handling
function divide(a, b) {
    if (typeof a !== "number" || typeof b !== "number") {
        throw new Error("Both arguments must be numbers");
    }
    
    if (b === 0) {
        throw new Error("Cannot divide by zero");
    }
    
    return a / b;
}

// Safe wrapper function
function safeDivide(a, b) {
    try {
        return { success: true, result: divide(a, b) };
    } catch (error) {
        return { success: false, error: error.message };
    }
}

console.log(safeDivide(10, 2));  // { success: true, result: 5 }
console.log(safeDivide(10, 0));  // { success: false, error: "Cannot divide by zero" }

// Validation dengan return values
function createUser(userData) {
    let errors = [];
    
    if (!userData.name || userData.name.trim() === "") {
        errors.push("Name is required");
    }
    
    if (!userData.email || !validateEmail(userData.email)) {
        errors.push("Valid email is required");
    }
    
    if (!userData.age || userData.age < 18) {
        errors.push("Age must be 18 or older");
    }
    
    if (errors.length > 0) {
        return { success: false, errors };
    }
    
    return {
        success: true,
        user: {
            id: Date.now(),
            name: userData.name.trim(),
            email: userData.email.toLowerCase(),
            age: userData.age,
            createdAt: new Date()
        }
    };
}
```

## 9. Latihan Praktik

### Latihan 1: Calculator Functions
```javascript
// Membuat kalkulator dengan berbagai fungsi
const Calculator = {
    // Basic operations
    add: (a, b) => a + b,
    subtract: (a, b) => a - b,
    multiply: (a, b) => a * b,
    divide: (a, b) => b !== 0 ? a / b : "Cannot divide by zero",
    
    // Advanced operations
    power: (base, exponent) => Math.pow(base, exponent),
    squareRoot: (n) => n >= 0 ? Math.sqrt(n) : "Cannot calculate square root of negative number",
    
    // Array operations
    sum: (numbers) => numbers.reduce((acc, num) => acc + num, 0),
    average: (numbers) => numbers.length > 0 ? Calculator.sum(numbers) / numbers.length : 0,
    max: (numbers) => Math.max(...numbers),
    min: (numbers) => Math.min(...numbers),
    
    // Complex calculations
    compound: (principal, rate, time, frequency = 1) => {
        return principal * Math.pow((1 + rate / frequency), frequency * time);
    },
    
    // Chain operations
    chain: (initialValue) => {
        let value = initialValue;
        
        return {
            add: (n) => { value = Calculator.add(value, n); return this; },
            subtract: (n) => { value = Calculator.subtract(value, n); return this; },
            multiply: (n) => { value = Calculator.multiply(value, n); return this; },
            divide: (n) => { value = Calculator.divide(value, n); return this; },
            result: () => value
        };
    }
};

// Test calculator
console.log(Calculator.add(5, 3));           // 8
console.log(Calculator.average([1,2,3,4,5])); // 3
console.log(Calculator.compound(1000, 0.05, 10)); // Compound interest

// Chain operations
let result = Calculator.chain(10)
    .add(5)
    .multiply(2)
    .subtract(5)
    .result();
console.log(result); // 25
```

### Latihan 2: Data Processing Functions
```javascript
// Fungsi untuk memproses data mahasiswa
function createStudentProcessor() {
    let students = [];
    
    return {
        // Add student
        addStudent: (student) => {
            let newStudent = {
                id: students.length + 1,
                ...student,
                courses: student.courses || [],
                createdAt: new Date()
            };
            students.push(newStudent);
            return newStudent.id;
        },
        
        // Get students with filters
        getStudents: (filter = {}) => {
            return students.filter(student => {
                for (let key in filter) {
                    if (student[key] !== filter[key]) {
                        return false;
                    }
                }
                return true;
            });
        },
        
        // Calculate GPA
        calculateGPA: (studentId) => {
            let student = students.find(s => s.id === studentId);
            if (!student || student.courses.length === 0) return 0;
            
            let totalPoints = student.courses.reduce((sum, course) => {
                let points = gradeToPoints(course.grade);
                return sum + (points * course.credits);
            }, 0);
            
            let totalCredits = student.courses.reduce((sum, course) => sum + course.credits, 0);
            return totalCredits > 0 ? (totalPoints / totalCredits).toFixed(2) : 0;
        },
        
        // Statistics
        getStatistics: () => {
            let totalStudents = students.length;
            let gpas = students.map(s => parseFloat(processor.calculateGPA(s.id))).filter(gpa => gpa > 0);
            
            return {
                totalStudents,
                averageGPA: gpas.length > 0 ? (gpas.reduce((a, b) => a + b, 0) / gpas.length).toFixed(2) : 0,
                highestGPA: Math.max(...gpas),
                lowestGPA: Math.min(...gpas),
                studentsWithGPA: gpas.length
            };
        },
        
        // Sort functions
        sortBy: (criteria) => {
            return [...students].sort((a, b) => {
                if (criteria === "name") {
                    return a.name.localeCompare(b.name);
                }
                if (criteria === "gpa") {
                    return parseFloat(processor.calculateGPA(b.id)) - parseFloat(processor.calculateGPA(a.id));
                }
                return 0;
            });
        }
    };
}

function gradeToPoints(grade) {
    const gradeMap = { 'A': 4, 'B': 3, 'C': 2, 'D': 1, 'E': 0 };
    return gradeMap[grade] || 0;
}

// Test student processor
let processor = createStudentProcessor();

processor.addStudent({
    name: "Alice Johnson",
    major: "Computer Science",
    courses: [
        { name: "Data Structures", credits: 3, grade: "A" },
        { name: "Database", credits: 3, grade: "B" }
    ]
});

processor.addStudent({
    name: "Bob Smith",
    major: "Information Systems",
    courses: [
        { name: "Web Programming", credits: 2, grade: "A" },
        { name: "Software Engineering", credits: 3, grade: "A" }
    ]
});

console.log("Alice's GPA:", processor.calculateGPA(1));
console.log("Statistics:", processor.getStatistics());
console.log("CS Students:", processor.getStudents({ major: "Computer Science" }));
```

### Latihan 3: Utility Functions Library
```javascript
// Library fungsi utility yang sering digunakan
const Utils = {
    // String utilities
    string: {
        capitalize: (str) => str.charAt(0).toUpperCase() + str.slice(1).toLowerCase(),
        
        camelCase: (str) => {
            return str.toLowerCase()
                     .split(/[\s-_]+/)
                     .map((word, index) => index === 0 ? word : Utils.string.capitalize(word))
                     .join('');
        },
        
        truncate: (str, length = 50, suffix = "...") => {
            return str.length > length ? str.substring(0, length) + suffix : str;
        },
        
        slugify: (str) => {
            return str.toLowerCase()
                     .replace(/[^a-z0-9\s-]/g, '')
                     .replace(/[\s-]+/g, '-')
                     .trim('-');
        }
    },
    
    // Array utilities
    array: {
        unique: (arr) => [...new Set(arr)],
        
        chunk: (arr, size) => {
            let chunks = [];
            for (let i = 0; i < arr.length; i += size) {
                chunks.push(arr.slice(i, i + size));
            }
            return chunks;
        },
        
        groupBy: (arr, key) => {
            return arr.reduce((groups, item) => {
                let group = typeof key === 'function' ? key(item) : item[key];
                if (!groups[group]) groups[group] = [];
                groups[group].push(item);
                return groups;
            }, {});
        },
        
        shuffle: (arr) => {
            let shuffled = [...arr];
            for (let i = shuffled.length - 1; i > 0; i--) {
                let j = Math.floor(Math.random() * (i + 1));
                [shuffled[i], shuffled[j]] = [shuffled[j], shuffled[i]];
            }
            return shuffled;
        }
    },
    
    // Date utilities
    date: {
        formatDate: (date, format = "YYYY-MM-DD") => {
            let d = new Date(date);
            let year = d.getFullYear();
            let month = String(d.getMonth() + 1).padStart(2, '0');
            let day = String(d.getDate()).padStart(2, '0');
            
            return format.replace('YYYY', year)
                        .replace('MM', month)
                        .replace('DD', day);
        },
        
        addDays: (date, days) => {
            let result = new Date(date);
            result.setDate(result.getDate() + days);
            return result;
        },
        
        daysBetween: (date1, date2) => {
            let d1 = new Date(date1);
            let d2 = new Date(date2);
            return Math.abs((d2 - d1) / (1000 * 60 * 60 * 24));
        }
    },
    
    // Validation utilities
    validate: {
        email: (email) => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email),
        phone: (phone) => /^\+?[\d\s-()]{10,}$/.test(phone),
        url: (url) => {
            try {
                new URL(url);
                return true;
            } catch {
                return false;
            }
        },
        creditCard: (number) => {
            // Simple Luhn algorithm
            let digits = number.replace(/\D/g, '');
            let sum = 0;
            let isEven = false;
            
            for (let i = digits.length - 1; i >= 0; i--) {
                let digit = parseInt(digits[i]);
                
                if (isEven) {
                    digit *= 2;
                    if (digit > 9) digit -= 9;
                }
                
                sum += digit;
                isEven = !isEven;
            }
            
            return sum % 10 === 0;
        }
    }
};

// Test utility functions
console.log(Utils.string.camelCase("hello world test"));  // "helloWorldTest"
console.log(Utils.array.chunk([1,2,3,4,5,6,7], 3));     // [[1,2,3], [4,5,6], [7]]
console.log(Utils.date.formatDate(new Date()));          // "2023-12-07"
console.log(Utils.validate.email("test@email.com"));     // true
```

## 10. Tugas

1. **Personal Finance Calculator**: Buat fungsi-fungsi untuk:
   - Menghitung compound interest
   - Simulasi kredit dengan cicilan bulanan
   - Perhitungan investasi dengan inflasi
   - Budget tracker dengan kategori pengeluaran

2. **Text Processing Library**: Buat library untuk:
   - Word count dan reading time estimation
   - Text similarity checker
   - Auto-correct sederhana
   - Markdown to HTML converter

3. **Game Logic Functions**: Buat fungsi untuk game sederhana:
   - Tic-tac-toe game logic
   - Number guessing game dengan difficulty levels
   - Simple card game (blackjack atau poker)
   - Maze solver dengan recursion

4. **Data Analysis Functions**: Buat fungsi untuk menganalisis data:
   - Statistical calculations (mean, median, mode, standard deviation)
   - Data visualization helpers
   - CSV parser dan exporter
   - Trend analysis dan prediction

## Ringkasan

Dalam pertemuan ini kita telah mempelajari:

**Deklarasi Fungsi:**
- Function declaration vs expression vs arrow functions
- Kapan menggunakan masing-masing jenis fungsi
- Hoisting dan behavior differences

**Parameter dan Arguments:**
- Default parameters untuk nilai fallback
- Rest parameters untuk mengumpulkan arguments
- Spread operator untuk passing arrays sebagai arguments
- Destructuring parameters untuk cleaner code

**Return Values:**
- Single dan multiple return values
- Early return untuk cleaner logic flow
- Returning functions (higher-order functions)

**Scope dan Closure:**
- Function scope vs block scope
- Closure untuk data privacy dan factory functions
- IIFE untuk module pattern

**Advanced Concepts:**
- Higher-order functions dan callbacks
- Recursive functions untuk tree-like data
- Function composition dan currying
- Best practices untuk maintainable code

**Best Practices:**
- Single responsibility principle
- Pure functions tanpa side effects
- Proper error handling
- Descriptive naming dan clear structure