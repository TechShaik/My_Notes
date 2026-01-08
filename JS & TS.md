
JavaScript : JavaScript (often abbreviated as JS) is a high-level, interpreted programming language that is primarily used to make web pages interactive, dynamic, and functional.

Primitive Types (single values)

string → "hello", 'abc'

number → 42, 3.14

boolean → true, false

null → intentional empty value

undefined → variable declared but not assigned

symbol → unique identifiers

bigint → very large integers

let name = "Shaik";   // string
let age = 25;         // number
let active = true;    // boolean
let score = null;     // null
let x;                // undefined

Objects & Arrays
Objects
const user = {
  id: 1,
  name: "Shaik",
  active: true
};

console.log(user.name); 

Arrays
const nums = [1, 2, 3];
const names = ["Ali", "Zara", "Shaik"];

Let vs Const :

let
1.It is mutable. We can change after assigning a value.
2.It is block scoped. We cannot access it outside the block.
3.It can be used without initialization. Ex : let a; 

const
1.It is immutable. We cannot change after assigning.
2.It is also block scoped.
3.It can't be used without initialization.
4.We can push and pop operations in arrays in const but cannot reassign.

What is a Function?

A function in JavaScript is a block of code designed to perform a task.
It can take inputs (parameters), process them, and return an output (return value).

function greet(name) {
  return "Hello, " + name;
}

console.log(greet("Shaik")); // Hello, Shaik

What is a Class?

A class in JavaScript is a blueprint for creating objects with properties and methods.
It was introduced in ES6 (2015) as a cleaner way to work with objects & prototypes.

class Person {
  constructor(name, age) {
    this.name = name; // property
    this.age = age;
  }

  // method
  greet() {
    return `Hello, my name is ${this.name} and I am ${this.age} years old.`;
  }
}

const p1 = new Person("Shaik", 25);
console.log(p1.greet());
// Hello, my name is Shaik and I am 25 years old.

Destructuring is a JavaScript feature that allows you to unpack values from arrays or properties from objects into separate variables in a concise and readable way.

👉 In simple words:
Destructuring lets you take data out of arrays or objects and store it directly into variables.

What is a Promise?

Promises are a very important concept in JavaScript, especially for handling asynchronous code (like API calls, file reading, timers, etc.).

A Promise in JavaScript is an object that represents the eventual completion (or failure) of an asynchronous operation.

Think of it like:
👉 “I promise to give you a value in the future (success or failure).”

🔹 Promise States

A promise can be in one of 3 states:

Pending → Initial state, neither fulfilled nor rejected.

Fulfilled → Operation completed successfully (resolve).

Rejected → Operation failed (reject).

const myPromise = new Promise((resolve, reject) => {
  let success = true;

  if (success) {
    resolve("✅ Operation successful!");
  } else {
    reject("❌ Operation failed!");
  }
});


Consuming a Promise

We use .then() (for success) and .catch() (for error).

myPromise
  .then(result => {
    console.log(result); // ✅ Operation successful!
  })
  .catch(error => {
    console.log(error); // ❌ Operation failed!
  })
  .finally(() => {
    console.log("Promise finished (success or failure).");
  });

Solution: async & await

async/await makes asynchronous code look like synchronous code.

async → makes a function return a Promise.

await → pauses execution until a Promise resolves or rejects.

async function getData() {
  console.log("Fetching...");        // 1️⃣ Prints immediately

  const result = await fetchData();  // 2️⃣ Pauses here until fetchData() finishes

  console.log(result);               // 3️⃣ Prints only AFTER fetchData resolves
  console.log("Done!");              // 4️⃣ Prints right after result
}

What is a Module?

A module is just a separate file that contains some code (variables, functions, classes, etc.) which you can export and then import into other files.

👉 This helps:

Split code into smaller files.
Avoid global variable pollution.
Reuse code across projects.
 


Typescript
 
TypeScript is a superset(means every valid JS code is also valid TS code) of JavaScript developed by Microsoft that adds static typing, interfaces, enums, and advanced tooling to JavaScript. It compiles (or "transpiles") down to plain JavaScript, so it can run anywhere JS runs (browser, Node.js, etc.).

1.allows to use JavaScript.
2.allows to use strict types
3.support modern features

Types:

1.once a variable is assigned your cant change it with another type data.
2. you can only reassign with same data.
3. we can pass input and its type to avoid errors.

1. String
let firstName: string = "Shaik";
let greeting: string = `Hello, ${firstName}`;
console.log(greeting);  // Hello, Shaik

🟦 2. Number
let age: number = 25;
let price: number = 99.99;

🟦 3. Boolean
let isActive: boolean = true;
let isCompleted: boolean = false;

🟦 4. Any (❌ avoid if possible)

Can hold any type (removes safety).

let random: any = "Hello";
random = 10;    // valid, but unsafe

🟦 5. Array
let numbers: number[] = [1, 2, 3, 4];
let names: string[] = ["Ali", "Ravi", "John"];

🟦 6. Tuple

Fixed-length array with specific types.

let person: [string, number] = ["Shaik", 25];

🟦 7. Enum

For fixed set of values.

enum Direction {
  Up,
  Down,
  Left,
  Right
}

let move: Direction = Direction.Up;
console.log(move); // 0 (by default starts from 0)

🟦 8. Union

Variable can have multiple types.

let value: string | number;
value = "Hello";
value = 123;   // ✅ both valid

🟦 9. Void

Used in functions that don’t return anything.

function logMessage(msg: string): void {
  console.log(msg);
}

🟦 10. Never

For functions that never return (e.g., errors, infinite loop).

function throwError(message: string): never {
  throw new Error(message);
}

used to throw error

Functions in TypeScript

Functions in TS are similar to JS, but here we can add types to parameters and return values.

1️⃣ Function with parameter & return type
function add(a: number, b: number): number {
  return a + b;
}

console.log(add(5, 10)); // ✅ 15

2️⃣ Function with void return
function greet(name: string): void {
  console.log(`Hello, ${name}`);
}
greet("Shaik"); // ✅ Hello, Shaik

Interfaces & Type Aliases

1️⃣ Interfaces
interface Person {
  name: string;
  age: number;
  isStudent?: boolean; // optional property
}

const user: Person = {
  name: "Shaik",
  age: 25,
};

2️⃣ Type Aliases
type Employee = {
  id: number;
  role: string;
};

const emp: Employee = {
  id: 101,
  role: "Developer",
};

⚡ Difference:

interface is mainly for objects/classes

type can be used for objects, primitives, unions, tuples, etc.

3️⃣ Extending Interfaces
interface Person {
  name: string;
  age: number;
}

interface Employee extends Person {
  employeeId: number;
}

const emp1: Employee = {
  name: "Shaik",
  age: 25,
  employeeId: 1001,
};

4️⃣ Interfaces in Functions
interface Product {
  id: number;
  name: string;
  price: number;
}

function printProduct(p: Product): void {
  console.log(`${p.name} costs $${p.price}`);
}

printProduct({ id: 1, name: "Laptop", price: 50000 });

Generics

Generics allow us to write reusable and type-safe code.
Instead of fixing a type, we make it dynamic but still maintain type safety.

1️⃣ Without Generics
function identity(arg: any): any {
  return arg;
}

console.log(identity(5));       // number but TS treats as 'any'
console.log(identity("Hello")); // string but TS treats as 'any'

2️⃣With Generics
function identity<T>(arg: T): T {
  return arg;
}

console.log(identity<number>(10));  // number
console.log(identity<string>("Hi")); // string