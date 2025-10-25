# Pertemuan 13: Interaksi dengan Browser - DOM Manipulation

## Tujuan Pembelajaran
Setelah mengikuti pertemuan ini, mahasiswa diharapkan dapat:
- Memahami konsep DOM (Document Object Model) dan struktur HTML sebagai tree
- Menggunakan method untuk memilih elemen HTML (getElementById, querySelector, dll)
- Memanipulasi konten, atribut, dan style elemen HTML menggunakan JavaScript
- Menambah, menghapus, dan memodifikasi elemen DOM secara dinamis
- Menangani berbagai jenis event (click, submit, load, dll)
- Membuat aplikasi web interaktif dengan DOM manipulation

## 1. Pengenalan DOM (Document Object Model)

### 1.1 Apa itu DOM?

DOM adalah representasi dari dokumen HTML sebagai struktur tree yang dapat diakses dan dimanipulasi menggunakan JavaScript. Setiap elemen HTML menjadi node dalam tree tersebut.

#### Struktur HTML sebagai Tree:
```html
<!DOCTYPE html>
<html>
<head>
    <title>My Page</title>
</head>
<body>
    <div id="container">
        <h1 class="title">Welcome</h1>
        <p>This is a paragraph</p>
        <ul>
            <li>Item 1</li>
            <li>Item 2</li>
        </ul>
    </div>
</body>
</html>
```

```
document
    └── html
        ├── head
        │   └── title
        │       └── "My Page"
        └── body
            └── div#container
                ├── h1.title
                │   └── "Welcome"
                ├── p
                │   └── "This is a paragraph"
                └── ul
                    ├── li
                    │   └── "Item 1"
                    └── li
                        └── "Item 2"
```

### 1.2 Node Types dalam DOM

```javascript
// Document node
console.log(document.nodeType); // 9 (DOCUMENT_NODE)

// Element nodes
let element = document.getElementById('container');
console.log(element.nodeType); // 1 (ELEMENT_NODE)

// Text nodes
let textNode = element.firstChild;
console.log(textNode.nodeType); // 3 (TEXT_NODE)

// Attribute nodes (accessed differently)
let titleAttr = element.getAttributeNode('id');
console.log(titleAttr.nodeType); // 2 (ATTRIBUTE_NODE)

// Node type constants
console.log(Node.ELEMENT_NODE);   // 1
console.log(Node.TEXT_NODE);      // 3
console.log(Node.COMMENT_NODE);   // 8
console.log(Node.DOCUMENT_NODE);  // 9
```

### 1.3 Mengakses DOM dari JavaScript

```javascript
// Global object 'document' adalah entry point ke DOM
console.log(document);              // HTMLDocument object
console.log(document.documentElement); // <html> element
console.log(document.head);         // <head> element
console.log(document.body);         // <body> element
console.log(document.title);        // Page title
console.log(document.URL);          // Current URL

// Document information
console.log(document.doctype);      // <!DOCTYPE html>
console.log(document.characterSet); // "UTF-8"
console.log(document.readyState);   // "complete", "loading", or "interactive"
```

## 2. Seleksi Elemen

### 2.1 Method Seleksi Dasar

#### getElementById():
```javascript
// Mencari elemen berdasarkan ID (paling cepat)
let container = document.getElementById('container');
console.log(container); // <div id="container">...</div>

// Jika tidak ditemukan, return null
let notFound = document.getElementById('not-exist');
console.log(notFound); // null

// ID harus unik dalam satu dokumen
let title = document.getElementById('main-title');
if (title) {
    console.log('Title found:', title.textContent);
} else {
    console.log('Title not found');
}
```

#### getElementsByTagName():
```javascript
// Mencari elemen berdasarkan tag name (returns HTMLCollection)
let paragraphs = document.getElementsByTagName('p');
console.log(paragraphs);        // HTMLCollection[p, p, p]
console.log(paragraphs.length); // 3
console.log(paragraphs[0]);     // First <p> element

// HTMLCollection is "live" - automatically updates
let divs = document.getElementsByTagName('div');
console.log(divs.length); // Current div count

// Create new div
let newDiv = document.createElement('div');
document.body.appendChild(newDiv);
console.log(divs.length); // Count increased by 1!

// Convert to array for array methods
let divArray = Array.from(divs);
let divArray2 = [...divs];

// Iterate through HTMLCollection
for (let i = 0; i < paragraphs.length; i++) {
    console.log(paragraphs[i].textContent);
}

// Or use for...of
for (let paragraph of paragraphs) {
    console.log(paragraph.textContent);
}
```

#### getElementsByClassName():
```javascript
// Mencari elemen berdasarkan class (returns HTMLCollection)
let highlights = document.getElementsByClassName('highlight');
console.log(highlights);

// Multiple classes (semua class harus ada)
let specialItems = document.getElementsByClassName('item special');

// Scope search to specific element
let container = document.getElementById('container');
let containerHighlights = container.getElementsByClassName('highlight');

// Class names are case-sensitive
let items = document.getElementsByClassName('Item'); // Won't find 'item'
```

### 2.2 Modern Selectors (Recommended)

#### querySelector():
```javascript
// Mencari elemen pertama yang cocok dengan CSS selector
let firstParagraph = document.querySelector('p');
let mainTitle = document.querySelector('#main-title');
let firstHighlight = document.querySelector('.highlight');

// Complex selectors
let firstListItem = document.querySelector('ul li:first-child');
let submitButton = document.querySelector('button[type="submit"]');
let navLink = document.querySelector('nav a.active');

// Descendant selectors
let containerParagraph = document.querySelector('#container p');
let formInput = document.querySelector('form .input-group input');

// Pseudo-selectors
let evenRows = document.querySelector('tr:nth-child(even)');
let lastItem = document.querySelector('li:last-child');

// Attribute selectors
let requiredInputs = document.querySelector('input[required]');
let emailInput = document.querySelector('input[type="email"]');

// Returns null if not found
let notFound = document.querySelector('.does-not-exist');
console.log(notFound); // null
```

#### querySelectorAll():
```javascript
// Mencari semua elemen yang cocok (returns NodeList)
let allParagraphs = document.querySelectorAll('p');
let allHighlights = document.querySelectorAll('.highlight');
let allButtons = document.querySelectorAll('button');

console.log(allParagraphs);        // NodeList[p, p, p]
console.log(allParagraphs.length); // 3

// NodeList is "static" - doesn't update automatically
let allDivs = document.querySelectorAll('div');
console.log(allDivs.length); // Current count

// Add new div
let newDiv = document.createElement('div');
document.body.appendChild(newDiv);
console.log(allDivs.length); // Same as before (static)

// NodeList has forEach method
allParagraphs.forEach((paragraph, index) => {
    console.log(`Paragraph ${index}:`, paragraph.textContent);
});

// Convert to array for other array methods
let paragraphArray = Array.from(allParagraphs);
let texts = paragraphArray.map(p => p.textContent);

// Complex selectors
let navLinks = document.querySelectorAll('nav ul li a');
let formInputs = document.querySelectorAll('form input, form select, form textarea');
let dataElements = document.querySelectorAll('[data-category]');

// Chaining selectors
let container = document.querySelector('#main-container');
let containerButtons = container.querySelectorAll('button');
```

### 2.3 Navigasi DOM Tree

```javascript
let element = document.querySelector('#main-content');

// Parent navigation
console.log(element.parentNode);       // Direct parent
console.log(element.parentElement);    // Same as parentNode for elements
console.log(element.closest('div'));   // Nearest ancestor div
console.log(element.closest('.container')); // Nearest ancestor with class

// Child navigation
console.log(element.children);         // HTMLCollection of child elements
console.log(element.childNodes);       // NodeList including text nodes
console.log(element.firstElementChild); // First child element
console.log(element.lastElementChild);  // Last child element
console.log(element.firstChild);        // First child node (might be text)
console.log(element.lastChild);         // Last child node

// Sibling navigation
console.log(element.nextElementSibling);     // Next sibling element
console.log(element.previousElementSibling); // Previous sibling element
console.log(element.nextSibling);            // Next sibling node (might be text)
console.log(element.previousSibling);        // Previous sibling node

// Practical navigation example
function findAllSiblings(element) {
    let siblings = [];
    let parent = element.parentElement;
    
    if (parent) {
        for (let child of parent.children) {
            if (child !== element) {
                siblings.push(child);
            }
        }
    }
    
    return siblings;
}

// Get all children recursively
function getAllDescendants(element) {
    let descendants = [];
    
    for (let child of element.children) {
        descendants.push(child);
        descendants.push(...getAllDescendants(child));
    }
    
    return descendants;
}
```

## 3. Manipulasi Elemen

### 3.1 Mengubah Konten

#### textContent vs innerHTML:
```javascript
let element = document.querySelector('#content');

// textContent - plain text only
element.textContent = 'Hello World';
element.textContent = '<strong>Bold</strong>'; // Displays as literal text

console.log(element.textContent); // Gets all text content, no HTML

// innerHTML - HTML content
element.innerHTML = '<strong>Bold Text</strong>';
element.innerHTML = `
    <h2>Dynamic Content</h2>
    <p>This is generated by JavaScript</p>
    <ul>
        <li>Item 1</li>
        <li>Item 2</li>
    </ul>
`;

console.log(element.innerHTML); // Gets HTML content as string

// innerText vs textContent
let hiddenElement = document.querySelector('#hidden');
hiddenElement.style.display = 'none';
hiddenElement.innerHTML = '<span>Hidden <strong>text</strong></span>';

console.log(hiddenElement.textContent); // "Hidden text" (ignores styling)
console.log(hiddenElement.innerText);   // "" (respects styling - element is hidden)

// Safe HTML insertion (avoid XSS)
function safeHTML(strings, ...values) {
    let result = strings[0];
    for (let i = 0; i < values.length; i++) {
        let value = String(values[i])
            .replace(/&/g, '&amp;')
            .replace(/</g, '&lt;')
            .replace(/>/g, '&gt;')
            .replace(/"/g, '&quot;')
            .replace(/'/g, '&#39;');
        result += value + strings[i + 1];
    }
    return result;
}

let userInput = '<script>alert("XSS")</script>';
element.innerHTML = safeHTML`<p>User said: ${userInput}</p>`;
```

#### insertAdjacentHTML():
```javascript
let element = document.querySelector('#target');

// Insert positions
element.insertAdjacentHTML('beforebegin', '<div>Before element</div>');
element.insertAdjacentHTML('afterbegin', '<div>Start of element</div>');
element.insertAdjacentHTML('beforeend', '<div>End of element</div>');
element.insertAdjacentHTML('afterend', '<div>After element</div>');

/*
<!-- beforebegin -->
<div id="target">
    <!-- afterbegin -->
    existing content
    <!-- beforeend -->
</div>
<!-- afterend -->
*/

// Practical example - adding items to list
function addListItem(list, text) {
    list.insertAdjacentHTML('beforeend', `<li>${text}</li>`);
}

let todoList = document.querySelector('#todo-list');
addListItem(todoList, 'New task');
```

### 3.2 Manipulasi Atribut

```javascript
let element = document.querySelector('#my-element');

// getAttribute() and setAttribute()
let id = element.getAttribute('id');        // Get attribute value
element.setAttribute('class', 'new-class'); // Set attribute
element.setAttribute('data-role', 'button'); // Custom attributes

// hasAttribute() and removeAttribute()
if (element.hasAttribute('disabled')) {
    element.removeAttribute('disabled');
}

// Direct property access (for standard attributes)
element.id = 'new-id';
element.className = 'class1 class2';
element.title = 'Tooltip text';

// Input-specific properties
let input = document.querySelector('#my-input');
input.value = 'New value';
input.placeholder = 'Enter text here';
input.disabled = true;
input.required = true;
input.checked = true; // for checkboxes/radios

// Link-specific properties
let link = document.querySelector('#my-link');
link.href = 'https://example.com';
link.target = '_blank';

// Image-specific properties
let img = document.querySelector('#my-image');
img.src = 'new-image.jpg';
img.alt = 'Description';

// Data attributes
element.setAttribute('data-user-id', '123');
element.setAttribute('data-category', 'electronics');

// Accessing data attributes (modern way)
console.log(element.dataset.userId);    // "123"
console.log(element.dataset.category);  // "electronics"

element.dataset.newProperty = 'value'; // Creates data-new-property="value"

// Working with classes
element.className = 'class1 class2 class3';

// Better way - classList API
element.classList.add('new-class');
element.classList.remove('old-class');
element.classList.toggle('active');        // Add if not present, remove if present
element.classList.contains('active');      // Returns true/false
element.classList.replace('old', 'new');   // Replace class

// Multiple classes
element.classList.add('class1', 'class2', 'class3');
element.classList.remove('class1', 'class2');

// Practical example - active navigation
function setActiveNav(activeLink) {
    // Remove active from all nav links
    document.querySelectorAll('nav a').forEach(link => {
        link.classList.remove('active');
    });
    
    // Add active to clicked link
    activeLink.classList.add('active');
}
```

### 3.3 Manipulasi Style

```javascript
let element = document.querySelector('#styled-element');

// Inline styles (higher specificity)
element.style.color = 'red';
element.style.backgroundColor = 'yellow';
element.style.fontSize = '20px';
element.style.marginTop = '10px';

// CSS property names in camelCase
element.style.borderRadius = '5px';
element.style.textAlign = 'center';
element.style.fontWeight = 'bold';

// Using cssText for multiple properties
element.style.cssText = 'color: blue; background: yellow; padding: 10px;';
element.style.cssText += 'border: 1px solid black;'; // Append

// Getting computed styles (read-only)
let computedStyle = getComputedStyle(element);
console.log(computedStyle.color);           // "rgb(255, 0, 0)"
console.log(computedStyle.fontSize);        // "20px"
console.log(computedStyle.display);         // "block"

// Getting specific computed style
let fontSize = getComputedStyle(element).getPropertyValue('font-size');

// Dynamic styling example
function animateElement(element) {
    element.style.transition = 'all 0.3s ease';
    element.style.transform = 'scale(1.1)';
    element.style.boxShadow = '0 5px 15px rgba(0,0,0,0.3)';
    
    setTimeout(() => {
        element.style.transform = 'scale(1)';
        element.style.boxShadow = 'none';
    }, 300);
}

// Theme switcher example
function applyTheme(theme) {
    const root = document.documentElement;
    
    if (theme === 'dark') {
        root.style.setProperty('--bg-color', '#333');
        root.style.setProperty('--text-color', '#fff');
        root.style.setProperty('--accent-color', '#007acc');
    } else {
        root.style.setProperty('--bg-color', '#fff');
        root.style.setProperty('--text-color', '#333');
        root.style.setProperty('--accent-color', '#0066cc');
    }
}

// Responsive helper
function setResponsiveStyle(element, styles) {
    const width = window.innerWidth;
    
    if (width < 768) {
        Object.assign(element.style, styles.mobile);
    } else if (width < 1024) {
        Object.assign(element.style, styles.tablet);
    } else {
        Object.assign(element.style, styles.desktop);
    }
}

// Usage
setResponsiveStyle(element, {
    mobile: { fontSize: '14px', padding: '5px' },
    tablet: { fontSize: '16px', padding: '10px' },
    desktop: { fontSize: '18px', padding: '15px' }
});
```

## 4. Menambah, Menghapus, dan Memodifikasi Elemen

### 4.1 Membuat Elemen Baru

```javascript
// createElement() - membuat elemen baru
let newDiv = document.createElement('div');
let newParagraph = document.createElement('p');
let newButton = document.createElement('button');

// Set properties and attributes
newDiv.id = 'dynamic-div';
newDiv.className = 'container';
newDiv.textContent = 'This is a new div';

newParagraph.textContent = 'Dynamic paragraph';
newParagraph.style.color = 'blue';

newButton.textContent = 'Click me';
newButton.type = 'button';
newButton.onclick = function() {
    alert('Button clicked!');
};

// Complex element creation
function createElement(tag, attributes = {}, children = []) {
    let element = document.createElement(tag);
    
    // Set attributes
    Object.keys(attributes).forEach(key => {
        if (key === 'textContent') {
            element.textContent = attributes[key];
        } else if (key === 'innerHTML') {
            element.innerHTML = attributes[key];
        } else if (key === 'style') {
            Object.assign(element.style, attributes[key]);
        } else if (key === 'classList') {
            element.classList.add(...attributes[key]);
        } else {
            element.setAttribute(key, attributes[key]);
        }
    });
    
    // Add children
    children.forEach(child => {
        if (typeof child === 'string') {
            element.appendChild(document.createTextNode(child));
        } else {
            element.appendChild(child);
        }
    });
    
    return element;
}

// Usage example
let card = createElement('div', {
    classList: ['card', 'shadow'],
    style: { padding: '20px', margin: '10px' }
}, [
    createElement('h3', { textContent: 'Card Title' }),
    createElement('p', { textContent: 'Card description' }),
    createElement('button', { 
        textContent: 'Action',
        classList: ['btn', 'btn-primary']
    })
]);

// createTextNode() for text-only content
let textNode = document.createTextNode('Plain text content');

// cloneNode() for copying elements
let original = document.querySelector('#template');
let clone = original.cloneNode(true); // true = deep clone (includes children)
clone.id = 'template-copy';
```

### 4.2 Menambahkan Elemen ke DOM

```javascript
let parent = document.querySelector('#parent');
let newElement = document.createElement('div');

// appendChild() - adds to end
parent.appendChild(newElement);

// insertBefore() - adds before specific child
let referenceElement = document.querySelector('#reference');
parent.insertBefore(newElement, referenceElement);

// Modern methods (ES6+)
parent.prepend(newElement);           // Add to beginning
parent.append(newElement);            // Add to end
parent.before(newElement);            // Add before parent
parent.after(newElement);             // Add after parent

// Multiple elements at once
let elem1 = document.createElement('div');
let elem2 = document.createElement('p');
parent.append(elem1, elem2, 'Text node');

// insertAdjacentElement()
let target = document.querySelector('#target');
target.insertAdjacentElement('beforebegin', newElement);
target.insertAdjacentElement('afterbegin', newElement);
target.insertAdjacentElement('beforeend', newElement);
target.insertAdjacentElement('afterend', newElement);

// Practical example - dynamic list
function addTodoItem(text, completed = false) {
    let todoList = document.querySelector('#todo-list');
    
    let listItem = createElement('li', {
        classList: completed ? ['todo-item', 'completed'] : ['todo-item']
    }, [
        createElement('input', {
            type: 'checkbox',
            checked: completed,
            classList: ['todo-checkbox']
        }),
        createElement('span', {
            textContent: text,
            classList: ['todo-text']
        }),
        createElement('button', {
            textContent: 'Delete',
            classList: ['delete-btn']
        })
    ]);
    
    todoList.appendChild(listItem);
    return listItem;
}

// Dynamic table creation
function createTable(data, headers) {
    let table = createElement('table', { classList: ['data-table'] });
    
    // Create header
    let thead = createElement('thead');
    let headerRow = createElement('tr');
    headers.forEach(header => {
        headerRow.appendChild(createElement('th', { textContent: header }));
    });
    thead.appendChild(headerRow);
    table.appendChild(thead);
    
    // Create body
    let tbody = createElement('tbody');
    data.forEach(row => {
        let tr = createElement('tr');
        Object.values(row).forEach(cell => {
            tr.appendChild(createElement('td', { textContent: cell }));
        });
        tbody.appendChild(tr);
    });
    table.appendChild(tbody);
    
    return table;
}
```

### 4.3 Menghapus Elemen

```javascript
let element = document.querySelector('#to-remove');

// Modern way (ES6+)
element.remove(); // Removes the element from DOM

// Traditional way
element.parentNode.removeChild(element);

// Remove all children
let container = document.querySelector('#container');
while (container.firstChild) {
    container.removeChild(container.firstChild);
}

// Or using modern method
container.replaceChildren(); // Removes all children

// Conditional removal
function removeElementsByClass(className) {
    let elements = document.querySelectorAll(`.${className}`);
    elements.forEach(element => element.remove());
}

// Remove with confirmation
function safeRemove(element, message = 'Are you sure?') {
    if (confirm(message)) {
        element.remove();
        return true;
    }
    return false;
}

// Bulk operations
function clearList(listId) {
    let list = document.querySelector(`#${listId}`);
    if (list) {
        list.innerHTML = ''; // Quick way to remove all children
        // Or: list.replaceChildren();
    }
}

// Remove with animation
function animatedRemove(element, duration = 300) {
    element.style.transition = `opacity ${duration}ms ease`;
    element.style.opacity = '0';
    
    setTimeout(() => {
        element.remove();
    }, duration);
}
```

### 4.4 Mengganti Elemen

```javascript
let oldElement = document.querySelector('#old');
let newElement = document.createElement('div');
newElement.textContent = 'Replacement element';

// replaceWith() - modern method
oldElement.replaceWith(newElement);

// Traditional method
oldElement.parentNode.replaceChild(newElement, oldElement);

// Replace content but keep element
oldElement.innerHTML = '<h2>New Content</h2>';

// Replace multiple elements
let oldElements = document.querySelectorAll('.old-class');
oldElements.forEach(element => {
    let replacement = document.createElement('span');
    replacement.textContent = element.textContent;
    replacement.className = 'new-class';
    element.replaceWith(replacement);
});

// Smart replacement function
function replaceElement(selector, newTagName, keepContent = true, keepAttributes = true) {
    let elements = document.querySelectorAll(selector);
    
    elements.forEach(element => {
        let newElement = document.createElement(newTagName);
        
        if (keepContent) {
            newElement.innerHTML = element.innerHTML;
        }
        
        if (keepAttributes) {
            Array.from(element.attributes).forEach(attr => {
                newElement.setAttribute(attr.name, attr.value);
            });
        }
        
        element.replaceWith(newElement);
    });
}

// Usage: Replace all <b> tags with <strong> tags
replaceElement('b', 'strong');
```

## 5. Event Handling

### 5.1 Menambahkan Event Listeners

```javascript
// addEventListener() - recommended method
let button = document.querySelector('#my-button');

button.addEventListener('click', function() {
    console.log('Button clicked!');
});

// Arrow function event handler
button.addEventListener('click', () => {
    console.log('Button clicked with arrow function!');
});

// Event handler with parameters
button.addEventListener('click', function(event) {
    console.log('Event:', event);
    console.log('Target:', event.target);
    console.log('Current target:', event.currentTarget);
    
    // Prevent default behavior
    event.preventDefault();
    
    // Stop event propagation
    event.stopPropagation();
});

// Named function handler (easier to remove later)
function handleClick(event) {
    console.log('Named function handler');
}

button.addEventListener('click', handleClick);

// Multiple event types
function handleInteraction(event) {
    console.log(`${event.type} event occurred`);
}

button.addEventListener('click', handleInteraction);
button.addEventListener('mouseover', handleInteraction);
button.addEventListener('mouseout', handleInteraction);

// Event options
button.addEventListener('click', handleClick, {
    once: true,    // Execute only once
    passive: true, // Never calls preventDefault()
    capture: true  // Execute during capture phase
});

// Old-school method (not recommended)
button.onclick = function() {
    console.log('Old-school event handler');
};
```

### 5.2 Common Event Types

```javascript
// Mouse events
document.addEventListener('click', (e) => console.log('Click:', e.clientX, e.clientY));
document.addEventListener('dblclick', (e) => console.log('Double click'));
document.addEventListener('mousedown', (e) => console.log('Mouse down'));
document.addEventListener('mouseup', (e) => console.log('Mouse up'));
document.addEventListener('mousemove', (e) => console.log('Mouse move:', e.clientX, e.clientY));
document.addEventListener('mouseover', (e) => console.log('Mouse over'));
document.addEventListener('mouseout', (e) => console.log('Mouse out'));
document.addEventListener('mouseenter', (e) => console.log('Mouse enter'));
document.addEventListener('mouseleave', (e) => console.log('Mouse leave'));

// Keyboard events
document.addEventListener('keydown', (e) => {
    console.log('Key pressed:', e.key, e.code);
    console.log('Modifiers:', e.ctrlKey, e.shiftKey, e.altKey);
});

document.addEventListener('keyup', (e) => console.log('Key released:', e.key));
document.addEventListener('keypress', (e) => console.log('Key pressed (deprecated)'));

// Form events
let form = document.querySelector('#my-form');
let input = document.querySelector('#my-input');

form.addEventListener('submit', (e) => {
    e.preventDefault(); // Prevent form submission
    console.log('Form submitted');
});

input.addEventListener('focus', () => console.log('Input focused'));
input.addEventListener('blur', () => console.log('Input blurred'));
input.addEventListener('change', (e) => console.log('Input changed:', e.target.value));
input.addEventListener('input', (e) => console.log('Input typing:', e.target.value));

// Window events
window.addEventListener('load', () => console.log('Page loaded'));
window.addEventListener('resize', () => console.log('Window resized:', window.innerWidth, window.innerHeight));
window.addEventListener('scroll', () => console.log('Page scrolled:', window.scrollY));

// Document events
document.addEventListener('DOMContentLoaded', () => console.log('DOM ready'));

// Custom events
let customEvent = new CustomEvent('myCustomEvent', {
    detail: { message: 'Hello from custom event!' }
});

document.addEventListener('myCustomEvent', (e) => {
    console.log('Custom event:', e.detail.message);
});

document.dispatchEvent(customEvent);
```

### 5.3 Event Object dan Properties

```javascript
document.addEventListener('click', function(event) {
    // Event target information
    console.log('Target element:', event.target);           // Element that triggered the event
    console.log('Current target:', event.currentTarget);    // Element with event listener
    console.log('Event type:', event.type);                 // 'click'
    
    // Mouse position
    console.log('Client coordinates:', event.clientX, event.clientY); // Relative to viewport
    console.log('Page coordinates:', event.pageX, event.pageY);       // Relative to document
    console.log('Screen coordinates:', event.screenX, event.screenY); // Relative to screen
    
    // Keyboard modifiers
    console.log('Ctrl pressed:', event.ctrlKey);
    console.log('Shift pressed:', event.shiftKey);
    console.log('Alt pressed:', event.altKey);
    console.log('Meta pressed:', event.metaKey); // Cmd on Mac, Windows key on PC
    
    // Mouse button information
    console.log('Button pressed:', event.button); // 0=left, 1=middle, 2=right
    console.log('Buttons pressed:', event.buttons); // Bitmask of pressed buttons
    
    // Event timing
    console.log('Timestamp:', event.timeStamp);
    
    // Prevent default and propagation
    event.preventDefault();  // Prevent default behavior
    event.stopPropagation(); // Stop bubbling to parent elements
    event.stopImmediatePropagation(); // Stop other listeners on same element
});

// Keyboard event properties
document.addEventListener('keydown', function(event) {
    console.log('Key:', event.key);           // 'a', 'Enter', 'ArrowUp'
    console.log('Code:', event.code);         // 'KeyA', 'Enter', 'ArrowUp'
    console.log('Key code:', event.keyCode);  // Deprecated
    console.log('Char code:', event.charCode); // Deprecated
    console.log('Repeat:', event.repeat);     // True if key is held down
});

// Form event properties
document.querySelector('#my-input').addEventListener('change', function(event) {
    console.log('Value:', event.target.value);
    console.log('Form:', event.target.form);
    console.log('Name:', event.target.name);
    console.log('Type:', event.target.type);
});
```

### 5.4 Event Bubbling dan Capturing

```javascript
// HTML structure:
// <div id="outer">
//   <div id="inner">
//     <button id="button">Click me</button>
//   </div>
// </div>

let outer = document.querySelector('#outer');
let inner = document.querySelector('#inner');
let button = document.querySelector('#button');

// Event bubbling (default) - from target to root
button.addEventListener('click', () => console.log('Button clicked'));
inner.addEventListener('click', () => console.log('Inner div clicked'));
outer.addEventListener('click', () => console.log('Outer div clicked'));

// When button is clicked, output:
// "Button clicked"
// "Inner div clicked"
// "Outer div clicked"

// Event capturing - from root to target
outer.addEventListener('click', () => console.log('Outer (capture)'), true);
inner.addEventListener('click', () => console.log('Inner (capture)'), true);
button.addEventListener('click', () => console.log('Button (capture)'), true);

// With capture, output when button clicked:
// "Outer (capture)"
// "Inner (capture)"
// "Button (capture)"
// "Button clicked"
// "Inner div clicked"
// "Outer div clicked"

// Stop propagation example
button.addEventListener('click', function(event) {
    console.log('Button clicked');
    event.stopPropagation(); // Prevents bubbling to parent elements
});

// Event delegation - handle events for multiple elements
document.querySelector('#todo-list').addEventListener('click', function(event) {
    if (event.target.classList.contains('delete-btn')) {
        // Handle delete button click
        event.target.closest('li').remove();
    } else if (event.target.classList.contains('todo-checkbox')) {
        // Handle checkbox click
        event.target.closest('li').classList.toggle('completed');
    }
});

// Dynamic event delegation
function delegateEvent(parent, eventType, selector, handler) {
    parent.addEventListener(eventType, function(event) {
        if (event.target.matches(selector)) {
            handler.call(event.target, event);
        }
    });
}

// Usage
delegateEvent(document, 'click', '.dynamic-button', function(event) {
    console.log('Dynamic button clicked:', this.textContent);
});
```

### 5.5 Removing Event Listeners

```javascript
let button = document.querySelector('#my-button');

// Named function (required for removal)
function clickHandler(event) {
    console.log('Button clicked');
}

// Add event listener
button.addEventListener('click', clickHandler);

// Remove event listener
button.removeEventListener('click', clickHandler);

// Anonymous functions cannot be removed
button.addEventListener('click', function() {
    console.log('Cannot remove this');
});

// AbortController for easy cleanup (modern approach)
let controller = new AbortController();

button.addEventListener('click', clickHandler, {
    signal: controller.signal
});

input.addEventListener('input', inputHandler, {
    signal: controller.signal
});

// Remove all events with same signal
controller.abort();

// Cleanup utility
class EventManager {
    constructor() {
        this.listeners = [];
    }
    
    addEventListener(element, type, handler, options = {}) {
        element.addEventListener(type, handler, options);
        this.listeners.push({ element, type, handler, options });
    }
    
    removeAllListeners() {
        this.listeners.forEach(({ element, type, handler, options }) => {
            element.removeEventListener(type, handler, options);
        });
        this.listeners = [];
    }
}

// Usage
let eventManager = new EventManager();
eventManager.addEventListener(button, 'click', clickHandler);
eventManager.addEventListener(input, 'input', inputHandler);

// Later cleanup
eventManager.removeAllListeners();
```

## 6. Aplikasi Praktis

### 6.1 Todo List App

```html
<!DOCTYPE html>
<html>
<head>
    <title>Todo List</title>
    <style>
        .todo-item { margin: 5px 0; padding: 10px; border: 1px solid #ddd; }
        .todo-item.completed { text-decoration: line-through; opacity: 0.6; }
        .delete-btn { margin-left: 10px; background: red; color: white; border: none; padding: 5px; }
    </style>
</head>
<body>
    <div id="todo-app">
        <h1>Todo List</h1>
        <form id="todo-form">
            <input type="text" id="todo-input" placeholder="Enter new todo" required>
            <button type="submit">Add Todo</button>
        </form>
        <div id="todo-list"></div>
    </div>
</body>
</html>
```

```javascript
class TodoApp {
    constructor() {
        this.todos = [];
        this.nextId = 1;
        
        this.todoForm = document.querySelector('#todo-form');
        this.todoInput = document.querySelector('#todo-input');
        this.todoList = document.querySelector('#todo-list');
        
        this.init();
    }
    
    init() {
        this.todoForm.addEventListener('submit', (e) => {
            e.preventDefault();
            this.addTodo();
        });
        
        this.todoList.addEventListener('click', (e) => {
            if (e.target.classList.contains('delete-btn')) {
                this.deleteTodo(parseInt(e.target.dataset.id));
            } else if (e.target.classList.contains('todo-checkbox')) {
                this.toggleTodo(parseInt(e.target.dataset.id));
            }
        });
        
        this.render();
    }
    
    addTodo() {
        let text = this.todoInput.value.trim();
        if (text) {
            let todo = {
                id: this.nextId++,
                text: text,
                completed: false,
                createdAt: new Date()
            };
            
            this.todos.push(todo);
            this.todoInput.value = '';
            this.render();
        }
    }
    
    deleteTodo(id) {
        this.todos = this.todos.filter(todo => todo.id !== id);
        this.render();
    }
    
    toggleTodo(id) {
        let todo = this.todos.find(todo => todo.id === id);
        if (todo) {
            todo.completed = !todo.completed;
            this.render();
        }
    }
    
    render() {
        this.todoList.innerHTML = '';
        
        this.todos.forEach(todo => {
            let todoElement = document.createElement('div');
            todoElement.className = 'todo-item' + (todo.completed ? ' completed' : '');
            
            todoElement.innerHTML = `
                <input type="checkbox" class="todo-checkbox" data-id="${todo.id}" ${todo.completed ? 'checked' : ''}>
                <span>${todo.text}</span>
                <button class="delete-btn" data-id="${todo.id}">Delete</button>
            `;
            
            this.todoList.appendChild(todoElement);
        });
    }
}

// Initialize app when DOM is ready
document.addEventListener('DOMContentLoaded', () => {
    new TodoApp();
});
```

### 6.2 Interactive Form Validation

```html
<!DOCTYPE html>
<html>
<head>
    <title>Form Validation</title>
    <style>
        .form-group { margin: 15px 0; }
        .error { color: red; font-size: 14px; }
        .success { color: green; }
        input.invalid { border: 2px solid red; }
        input.valid { border: 2px solid green; }
    </style>
</head>
<body>
    <form id="registration-form">
        <div class="form-group">
            <label for="username">Username:</label>
            <input type="text" id="username" name="username" required>
            <div class="error" id="username-error"></div>
        </div>
        
        <div class="form-group">
            <label for="email">Email:</label>
            <input type="email" id="email" name="email" required>
            <div class="error" id="email-error"></div>
        </div>
        
        <div class="form-group">
            <label for="password">Password:</label>
            <input type="password" id="password" name="password" required>
            <div class="error" id="password-error"></div>
        </div>
        
        <div class="form-group">
            <label for="confirm-password">Confirm Password:</label>
            <input type="password" id="confirm-password" name="confirmPassword" required>
            <div class="error" id="confirm-password-error"></div>
        </div>
        
        <button type="submit">Register</button>
    </form>
</body>
</html>
```

```javascript
class FormValidator {
    constructor(formId) {
        this.form = document.querySelector(formId);
        this.validators = {};
        this.init();
    }
    
    init() {
        this.form.addEventListener('submit', (e) => {
            e.preventDefault();
            if (this.validateAll()) {
                this.onSuccess();
            }
        });
        
        // Real-time validation
        this.form.addEventListener('input', (e) => {
            this.validateField(e.target);
        });
        
        this.form.addEventListener('blur', (e) => {
            this.validateField(e.target);
        }, true);
    }
    
    addValidator(fieldName, validator) {
        this.validators[fieldName] = validator;
        return this;
    }
    
    validateField(field) {
        let fieldName = field.name;
        let validator = this.validators[fieldName];
        let errorElement = document.querySelector(`#${field.id}-error`);
        
        if (validator) {
            let result = validator(field.value, this.getFormData());
            
            if (result === true) {
                this.showFieldSuccess(field, errorElement);
            } else {
                this.showFieldError(field, errorElement, result);
            }
            
            return result === true;
        }
        
        return true;
    }
    
    validateAll() {
        let isValid = true;
        let formData = this.getFormData();
        
        Object.keys(this.validators).forEach(fieldName => {
            let field = this.form.querySelector(`[name="${fieldName}"]`);
            if (field && !this.validateField(field)) {
                isValid = false;
            }
        });
        
        return isValid;
    }
    
    getFormData() {
        let formData = {};
        let inputs = this.form.querySelectorAll('input, select, textarea');
        
        inputs.forEach(input => {
            formData[input.name] = input.value;
        });
        
        return formData;
    }
    
    showFieldError(field, errorElement, message) {
        field.classList.remove('valid');
        field.classList.add('invalid');
        errorElement.textContent = message;
        errorElement.className = 'error';
    }
    
    showFieldSuccess(field, errorElement) {
        field.classList.remove('invalid');
        field.classList.add('valid');
        errorElement.textContent = '';
        errorElement.className = 'success';
    }
    
    onSuccess() {
        alert('Form is valid! Data: ' + JSON.stringify(this.getFormData()));
    }
}

// Validation rules
let validator = new FormValidator('#registration-form')
    .addValidator('username', (value) => {
        if (value.length < 3) {
            return 'Username must be at least 3 characters';
        }
        if (!/^[a-zA-Z0-9_]+$/.test(value)) {
            return 'Username can only contain letters, numbers, and underscore';
        }
        return true;
    })
    .addValidator('email', (value) => {
        if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(value)) {
            return 'Please enter a valid email address';
        }
        return true;
    })
    .addValidator('password', (value) => {
        if (value.length < 8) {
            return 'Password must be at least 8 characters';
        }
        if (!/(?=.*[a-z])(?=.*[A-Z])(?=.*\d)/.test(value)) {
            return 'Password must contain at least one uppercase, lowercase, and number';
        }
        return true;
    })
    .addValidator('confirmPassword', (value, formData) => {
        if (value !== formData.password) {
            return 'Passwords do not match';
        }
        return true;
    });
```

### 6.3 Dynamic Content Gallery

```html
<!DOCTYPE html>
<html>
<head>
    <title>Image Gallery</title>
    <style>
        .gallery { display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 10px; }
        .gallery-item { position: relative; cursor: pointer; }
        .gallery-item img { width: 100%; height: 200px; object-fit: cover; }
        .gallery-item .overlay { position: absolute; top: 0; left: 0; right: 0; bottom: 0; background: rgba(0,0,0,0.7); color: white; display: flex; align-items: center; justify-content: center; opacity: 0; transition: opacity 0.3s; }
        .gallery-item:hover .overlay { opacity: 1; }
        .modal { position: fixed; top: 0; left: 0; right: 0; bottom: 0; background: rgba(0,0,0,0.9); display: flex; align-items: center; justify-content: center; z-index: 1000; }
        .modal img { max-width: 90%; max-height: 90%; }
        .close-btn { position: absolute; top: 20px; right: 20px; background: none; border: none; color: white; font-size: 24px; cursor: pointer; }
        .hidden { display: none; }
    </style>
</head>
<body>
    <div class="gallery" id="gallery"></div>
    
    <div class="modal hidden" id="modal">
        <button class="close-btn" id="close-modal">&times;</button>
        <img id="modal-image" src="" alt="">
    </div>
</body>
</html>
```

```javascript
class ImageGallery {
    constructor(galleryId, images = []) {
        this.gallery = document.querySelector(galleryId);
        this.modal = document.querySelector('#modal');
        this.modalImage = document.querySelector('#modal-image');
        this.closeBtn = document.querySelector('#close-modal');
        this.images = images;
        
        this.init();
    }
    
    init() {
        this.render();
        this.setupEventListeners();
    }
    
    setupEventListeners() {
        // Gallery click handling
        this.gallery.addEventListener('click', (e) => {
            let galleryItem = e.target.closest('.gallery-item');
            if (galleryItem) {
                let imageSrc = galleryItem.querySelector('img').src;
                this.openModal(imageSrc);
            }
        });
        
        // Modal close handling
        this.closeBtn.addEventListener('click', () => this.closeModal());
        this.modal.addEventListener('click', (e) => {
            if (e.target === this.modal) {
                this.closeModal();
            }
        });
        
        // Keyboard navigation
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Escape') {
                this.closeModal();
            }
        });
    }
    
    addImage(imageData) {
        this.images.push(imageData);
        this.render();
    }
    
    removeImage(index) {
        this.images.splice(index, 1);
        this.render();
    }
    
    render() {
        this.gallery.innerHTML = '';
        
        this.images.forEach((image, index) => {
            let galleryItem = document.createElement('div');
            galleryItem.className = 'gallery-item';
            galleryItem.innerHTML = `
                <img src="${image.src}" alt="${image.alt}" loading="lazy">
                <div class="overlay">
                    <span>${image.title}</span>
                </div>
            `;
            
            this.gallery.appendChild(galleryItem);
        });
    }
    
    openModal(imageSrc) {
        this.modalImage.src = imageSrc;
        this.modal.classList.remove('hidden');
        document.body.style.overflow = 'hidden';
    }
    
    closeModal() {
        this.modal.classList.add('hidden');
        document.body.style.overflow = '';
    }
}

// Sample images
let sampleImages = [
    { src: 'https://picsum.photos/400/300?random=1', alt: 'Random image 1', title: 'Beautiful Landscape' },
    { src: 'https://picsum.photos/400/300?random=2', alt: 'Random image 2', title: 'City View' },
    { src: 'https://picsum.photos/400/300?random=3', alt: 'Random image 3', title: 'Nature Scene' },
    { src: 'https://picsum.photos/400/300?random=4', alt: 'Random image 4', title: 'Architecture' },
    { src: 'https://picsum.photos/400/300?random=5', alt: 'Random image 5', title: 'Abstract Art' },
    { src: 'https://picsum.photos/400/300?random=6', alt: 'Random image 6', title: 'Street Photography' }
];

// Initialize gallery
document.addEventListener('DOMContentLoaded', () => {
    let gallery = new ImageGallery('#gallery', sampleImages);
    
    // Add more images dynamically
    setTimeout(() => {
        gallery.addImage({
            src: 'https://picsum.photos/400/300?random=7',
            alt: 'Dynamic image',
            title: 'Dynamically Added'
        });
    }, 2000);
});
```

## 7. Best Practices dan Performance

### 7.1 Performance Optimization

```javascript
// ✅ Batch DOM operations
function addMultipleElements() {
    let fragment = document.createDocumentFragment();
    
    for (let i = 0; i < 1000; i++) {
        let element = document.createElement('div');
        element.textContent = `Item ${i}`;
        fragment.appendChild(element);
    }
    
    document.body.appendChild(fragment); // Single DOM operation
}

// ❌ Individual DOM operations (slow)
function addElementsSlowly() {
    for (let i = 0; i < 1000; i++) {
        let element = document.createElement('div');
        element.textContent = `Item ${i}`;
        document.body.appendChild(element); // 1000 DOM operations
    }
}

// ✅ Cache DOM queries
let cachedElement = document.querySelector('#frequently-used');
function useElement() {
    cachedElement.textContent = 'Updated';
    cachedElement.style.color = 'red';
}

// ❌ Repeated queries
function queryRepeatedly() {
    document.querySelector('#frequently-used').textContent = 'Updated';
    document.querySelector('#frequently-used').style.color = 'red';
}

// ✅ Debounce expensive operations
function debounce(func, wait) {
    let timeout;
    return function executedFunction(...args) {
        const later = () => {
            clearTimeout(timeout);
            func(...args);
        };
        clearTimeout(timeout);
        timeout = setTimeout(later, wait);
    };
}

let expensiveOperation = debounce(() => {
    console.log('Expensive operation executed');
}, 300);

window.addEventListener('resize', expensiveOperation);

// ✅ Use event delegation for dynamic content
document.addEventListener('click', function(e) {
    if (e.target.matches('.dynamic-button')) {
        handleButtonClick(e.target);
    }
});
```

### 7.2 Memory Management

```javascript
// ✅ Clean up event listeners
class Component {
    constructor(element) {
        this.element = element;
        this.boundMethods = new Map();
        
        // Bind methods and store references for cleanup
        this.boundMethods.set('click', this.handleClick.bind(this));
        this.boundMethods.set('resize', this.handleResize.bind(this));
        
        this.element.addEventListener('click', this.boundMethods.get('click'));
        window.addEventListener('resize', this.boundMethods.get('resize'));
    }
    
    handleClick(e) {
        console.log('Clicked');
    }
    
    handleResize(e) {
        console.log('Resized');
    }
    
    destroy() {
        // Clean up event listeners
        this.element.removeEventListener('click', this.boundMethods.get('click'));
        window.removeEventListener('resize', this.boundMethods.get('resize'));
        
        // Clear references
        this.boundMethods.clear();
        this.element = null;
    }
}

// ✅ Avoid memory leaks with closures
function createHandler() {
    let largeData = new Array(1000000).fill('data'); // Large array
    
    return function handler() {
        // Don't reference largeData if not needed
        console.log('Handler called');
    };
}

// ✅ Use WeakMap for private data
let privateData = new WeakMap();

class SecureComponent {
    constructor(element) {
        privateData.set(this, {
            element: element,
            secretValue: 'private'
        });
    }
    
    getElement() {
        return privateData.get(this).element;
    }
}
```

## 8. Tugas

1. **Interactive Dashboard**: Buat dashboard dengan:
   - Multiple widgets yang dapat di-drag dan drop
   - Real-time data updates dengan timer
   - Filter dan sort functionality
   - Responsive layout dengan CSS Grid/Flexbox

2. **Mini E-commerce Product Page**: Buat halaman produk dengan:
   - Image gallery dengan zoom functionality
   - Product variants (size, color) selection
   - Add to cart dengan local storage
   - Review system dengan rating stars

3. **Task Management App**: Buat aplikasi manajemen tugas dengan:
   - Drag and drop untuk mengubah status task
   - Filter berdasarkan kategori dan priority
   - Deadline tracking dengan notifications
   - Export/import data functionality

4. **Interactive Quiz Application**: Buat aplikasi quiz dengan:
   - Multiple choice dan true/false questions
   - Timer untuk setiap pertanyaan
   - Progress indicator
   - Score calculation dan results display
   - Review answers functionality

## Ringkasan

Dalam pertemuan ini kita telah mempelajari:

**DOM Fundamentals:**
- Konsep DOM sebagai tree structure
- Node types dan cara mengakses document object
- Perbedaan antara element nodes dan text nodes

**Element Selection:**
- Method seleksi tradisional: getElementById, getElementsByTagName, getElementsByClassName
- Modern selectors: querySelector dan querySelectorAll
- Navigation dalam DOM tree: parent, children, siblings

**DOM Manipulation:**
- Mengubah content: textContent vs innerHTML
- Manipulasi attributes dan properties
- Styling elements dengan JavaScript
- Creating, adding, removing, dan replacing elements

**Event Handling:**
- addEventListener dan event types
- Event object dan properties
- Event bubbling, capturing, dan delegation
- Best practices untuk event management

**Practical Applications:**
- Building interactive web applications
- Form validation dan user feedback
- Dynamic content management
- Performance optimization techniques

**Best Practices:**
- Batch DOM operations untuk performance
- Memory management dan cleanup
- Event delegation untuk dynamic content
- Debouncing expensive operations

DOM manipulation adalah keterampilan fundamental untuk membuat aplikasi web yang interaktif dan responsif. Dengan menguasai konsep-konsep ini, Anda dapat membuat user experience yang engaging dan professional.