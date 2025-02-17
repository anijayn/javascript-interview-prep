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
