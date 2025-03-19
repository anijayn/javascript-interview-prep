# Javascript Q&As

### Explain call(), apply() and bind()
call() and apply() are used to modify the this variable in the function's scope. The only diffrence is the way you pass in other arguments to the function.

Example:
```
const car = {
    make: "Toyota",
    model: "Innova",
    printInfo: function(location, year){
        console.log("I drove a " +this.make + " " + this.model + " in " + location + " during " + year)
    },
}

const newCar = {
    make: "Mahindra",
    model: "Thar",
}

car.printInfo.call(newCar, "Chennai", 2025)

OUTPUT:
I drove a Mahindra Thar in Chennai during 2025
```

The only difference between call() and apply() is that for the other arguments you pass it through an array instead.

```
car.printInfo.apply(newCar, ["Chennai", 2025])
```

If you have a predefined number of paramenters in the calling function, use call() and use apply() in the other scenario where the spread operator can be leveraged.

bind() is used when you want to clone the same function but with a different object.
Example:
```
const car = {
    make: "Toyota",
    model: "Innova",
    printInfo: function(location, year){
        console.log("I drove a " +this.make + " " + this.model + " in " + location + " during " + year)
    },
}

const newCar = {
    make: "Mahindra",
    model: "Thar",
}

const printTharInfo = car.printInfo.bind(newCar, "Chennai", 2025)
printTharInfo()

OUTPUT:
I drove a Mahindra Thar in Chennai during 2025
```

### What is an event loop?
Event loop is a component in the JS engine that:
1. Monitors the call stack, microtasks queue and callback queue continuosly
2. If call stack is empty, pushes the functions in the microtasks queue one by one, into the callstack until it is exhausted.
3. And then pushes the functions in the callback queue one by one, into the call stack until it is exhausted.

### Explain primitive types in JS other than Number, Boolean and String
1. Symbol:

It is created using the Symbol() method which returns a unique and immutable value everytime it is called.
Example:
```
const symbol1 = Symbol("Apple");
const symbol2 = Symbol("Apple");
console.log(symbol1===symbol2);

OUTPUT:
false
```
The false output indicates that symbols are unique in nature. So they can be used as unique property keys to objects to avoid collision.

2. BigInt:

The Number type can only represent only 53 bits with precision. So BigInt can be used in that scenario where accuracy is required for too large or too small numbers. To use this datatype, you suffix the number with n.
```
const largestNumberEver = 12345678900987654321n;
console.log(typeof largestNumberEver);

OUTPUT:
BigInt
```

3. undefined:

Represents the absence of a value. When a variable is declared but not assigned with a value, it is assigned with undefined.

```
let x;
console.log(typeof x);

OUTPUT:
undefined
```

4. null:

Signifying that the variable holds nothing.

```
let y = null;
console.log(typeof y);

OUTPUT:
Object //Technically a null object
```

### Explain the concepts of Sets, WeakSets, Maps and WeakMaps

**Sets**: Sets store a collection of unique values where duplicates are not allowed. Sets can hold primitive values.

```
const nums = [1,1,2,2,4,4,3,3];
const uniqueNums = new Set(nums);
console.log(uniqueNums);

OUTPUT:
{1,2,4,3}
```

**WeakSets** : WeakSets hold weak references to the objects that they hold which will be garbage collected while Sets hold strong references. Also WeakSets only hold object values.

**Maps**: Maps store key-value pairs where both can be of any type. 

```
const users = new Map();
users.set(1, {name: "Ani", age: 24});
users.set("Ks", {name: "Ks", age: 25});
console.log(users.get(1));

OUTPUT:
{name: "Ani", age: 24}
```

**WeakMaps** : WeakMaps hold weak references to the values that they hold which will be garbage collected while Maps hold strong references. Also Maps allow only object and function keys.

### Return only the unique elements of an array using filter()

```
const nums = [1,2,3,3,2,1];
const uniqueNums = nums.filter((val, index, arr)=>arr.indexOf(val)===index);
console.log(uniqueNums);

OUTPUT:
[1,2,3]
```

### Explain for...of and for...in statements
* for...of is used in iterable objects like Arrays, Strings, Maps, Sets, NodeLists

```
const arr = [1, 2, 3];

for (const value of arr) {
  console.log(value); // Prints 1, 2, 3
}
```

* for...in used in iterating over key-value pairs(keys) and arrays(indices)

```
const obj = {"a":1, "b": 2};
for (const key in obj){
    console.log(key); // Prints a,b
    console.log(obj[key]); // Prints 1, 2
}
```

### Iterating a map

1. Using for...of
```
const maps = new Map([["a", 1], ["b",2]]);

for (const [k,v] of maps) {
  console.log(k); //Prints a,b
  console.log(v); //Prints 1,2
}
```

2. Using entries():

```
const maps = new Map([["a", 1], ["b",2]]);

Array.from(maps.entries()).forEach(([k,v])=>{
    console.log(k); //Prints a,b
    console.log(v); //Prints 1,2
})
```

### ES6 features
1. Arrow functions
2. Template literals
3. Destructuring
4. Classes
5. Modules

### What are Promises?
Promises represent the eventual completion of an asynchronous operation. The benefits of using Promises include:
1. Improved code readability and maintainabilty 
2. Chaining of async operations improves the program flow
3. Better error handling

Example:
fetch("https://api.com")
    .then(res=>res.json())
    .then(data=>{console.log(data)})
    .catch(err=>{console.log(err)})

### What is the JavaScript Engine?
The JavaScript Engine is a program that executes JavaScript code. It translates JavaScript (a high-level language) into machine code that computers can understand and run. JavaScript engines include components like:
1. Parser: Converts code to Abstract Syntax Tree
2. Interpreter: Executes code line-by-line 
3. Compiler: Converts frequently-used code to optimized machine code (JIT compilation)
4. Garbage collector: Manages memory allocation/deallocation

- V8 is Google's JavaScript engine used in Chrome and Node.js
- SpiderMonkey is Mozilla's engine used in Firefox
- JavaScriptCore/Nitro powers Safari
- Chakra is Microsoft's engine (previously used in Edge)

### Best practices for addressing security issues in JavaScript
1. Ensure User Input is Sanitized and Validated: Prevents XSS attacks
2. Implement a Content Security Policy (CSP): To implement a CSP in your web application, add the policy to your server’s HTTP headers. You can configure CSP by specifying which types of resources (such as scripts, styles, or images) and which domains are allowed to load content from.
3. Ensure Data in Transit is Always Encrypted with HTTPS
4. Use Strict Mode: With strict mode, JavaScript flags an error when certain actions are taken, such as accessing global objects, using undeclared variables, and making other coding mistakes.
5. Avoid Using the eval() Function: By passing user input to eval(), you're essentially permitting them to run any code, which can lead to serious security vulnerabilities.

### Explain how Promises work
Promises can be created using the `new Promise()` constructor, which takes a callback function with two parameters: `resolve` and `reject`. Inside the callback, you perform the async operation and call `resolve` when it's successful or `reject` when it fails.
Example:
```
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    const success = true;
    if (success) {
      resolve("Operation succeeded");
    } else {
      reject("Operation failed");
    }
  }, 2000);
});

promise
  .then((message) => {
    console.log(message); // Operation succeeded
  })
  .catch((error) => {
    console.error(error); // Operation failed
  });
```

### What are thenables and how do they relate to Promises?
Thenables are objects that have a `then()` method. Promises are a type of thenable, but not all thenables are Promises. Promises have additional features like `catch()` and `finally()` methods, which are not available in plain thenables. Many promise patterns, like chaining and async/await, work with any thenable.

### Key differences between Promises and async/await. Provide examples of when you would prefer one approach over the other.
1. Syntax: Promises use `.then()` and `.catch()` to handle async operations, while async/await uses `async` and `await` keywords.
2. Error handling: Promises use `.catch()` for error handling, while async/await uses `try/catch` blocks.
3. Readability: async/await is more readable and easier to understand than Promises.
4. Chaining: async/await allows you to write synchronous-looking code, while Promises require chaining `.then()` calls.
 
Use Promises when:
- You need to support older browsers that don't support async/await
- You prefer a more functional programming style
- You need to handle multiple async operations concurrently
Example:
```
fetch("https://api.com")
    .then(res=>res.json())
    .then(data=>{console.log(data)})
    .catch(err=>{console.log(err)})
```

Use async/await when:
- You want to write cleaner, more readable code
- You need to wait for a single async operation to complete
Example:
```
async function fetchData() {
  try {
    const res = await fetch("https://api.com");
    const data = await res.json();
    console.log(data);
  } catch (err) {
    console.error(err);
  }
}
```

### How do you differentiate an array, object and null in JavaScript?

```javascript
const arr = [1,2,3];
const obj ={a: 1, b:2, c:3}
const empty = null;
const map = new Map()
const testSet = new Set()
console.log(typeof(arr) === 'object' && typeof(obj) === 'object' && typeof(empty)=== 'object' && typeof(map) === 'object' && typeof(testSet) === 'object'  ) // true since [], {}, null, Map, WeakMap, Set, WeakSet are of the type object
function findType(value) {
  if (value === null) {
    return 'null';
  }
  if (Array.isArray(value)) {
    return 'array';
  }
  const type = Object.prototype.toString.call(value);
  switch (type) {
    case '[object Object]':
      return 'object';
    case '[object Map]':
      return 'map';
    case '[object Set]':
      return 'set';
    default:
      return typeof value;
  }
}
const res = findType(testSet)
console.log("This variable is a ",res)
```

### How do you handle error management in async functions ?
To handle errors in async functions, you can use try/catch blocks.

Example:
```
async function fetchData() {
  try {
    const res = await fetch("https://api.com");
    const data = await res.json();
    console.log(data);
  } catch (err) {
    console.error(err);
  }
}
```

You can also use .catch() to handle errors.

Example:
```
fetch("https://api.com")
    .then(res=>res.json())
    .then(data=>{console.log(data)})
    .catch(err=>{console.log(err)})
```

### List out some ES6 features
1. Arrow functions
2. Template literals
3. Destructuring
4. Classes
5. Modules
6. Promises
7. Async/await
8. Map and Set
9. Rest and spread operators
10. Destructuring
