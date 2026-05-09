# JavaScript ES6 Scenario-Based MCQ

> Scenario-based multiple choice questions covering JavaScript ES6 topics.

<br>

## Related Topics

* *[HTML Basics](https://github.com/learning-zone/html-basics)*
* *[CSS Basics](https://github.com/learning-zone/css-basics)*
* *[JavaScript ES6 Basics](https://github.com/learning-zone/javascript-es6-basics)*
* *[JavaScript Unit Testing](https://github.com/learning-zone/javascript-unit-testing)*
* *[JavaScript Coding Practice](https://github.com/learning-zone/javascript-coding-practice)*
* *[JavaScript Design Patterns](https://github.com/learning-zone/javascript-design-patterns)*
* *[Data Structure in JavaScript](https://github.com/learning-zone/javascript-data-structure)*

<br>

## Table of Contents

* [Variables](#-1-variables)
* [Hoisting & Scope](#-2-hoisting--scope)
* [Closures](#-3-closures)
* [Template Literals](#-4-template-literals)
* [Arrow Functions](#-5-arrow-functions)
* [Classes & Inheritance](#-6-classes--inheritance)
* [Destructuring](#-7-destructuring)
* [Spread & Rest Operators](#-8-spread--rest-operators)
* [Enhanced Object Literals](#-9-enhanced-object-literals)
* [Array Methods](#-10-array-methods)
* [Map & Set](#-11-map--set)
* [Modules](#-12-modules)
* [Iterators & Generators](#-13-iterators--generators)
* [Event Loop](#-14-event-loop)
* [Concurrency](#-15-concurrency)
* [Promises](#-16-promises)
* [Async & Await](#-17-async--await)
* [Default Parameters](#-18-default-parameters)
* [String Methods](#-19-string-methods)
* [for...of and for...in](#-20-forof-and-forin)
* [Type Coercion & Equality](#-21-type-coercion--equality)
* [Optional Chaining & Nullish Coalescing](#-22-optional-chaining--nullish-coalescing)
* [Object Methods](#-23-object-methods)
* [Prototype & this Binding](#-24-prototype--this-binding)
* [Symbol](#-25-symbol)
* [WeakMap & WeakSet](#-26-weakmap--weakset)
* [Private Class Fields](#-27-private-class-fields)
* [Proxy & Reflect](#-28-proxy--reflect)
* [Async Generators](#-29-async-generators)
* [Currying & Partial Application](#-30-currying--partial-application)
* [Logical Assignment Operators](#-31-logical-assignment-operators)
* [Custom Error Handling](#-32-custom-error-handling)
* [Number Methods](#-33-number-methods)
* [Regular Expressions (ES6+)](#-34-regular-expressions-es6)
* [Functional Programming](#-35-functional-programming)
* [Property Descriptors](#-36-property-descriptors)
* [Array Algorithm Problems](#-37-array-algorithm-problems)
* [String Algorithm Problems](#-38-string-algorithm-problems)
* [Object Patterns & Immutability](#-39-object-patterns--immutability)
* [Performance & Best Practices](#-40-performance--best-practices)

<br>

## # 1. VARIABLES

<br>

## Q. A developer declares three variables using `var`, `let`, and `const` inside a block. What will be the output of the following code?

```js
{
  var a = 1;
  let b = 2;
  const c = 3;
}
console.log(a);
console.log(b);
console.log(c);
```

- A) `1`, `2`, `3`
- B) `1`, `ReferenceError`, `ReferenceError`
- C) `undefined`, `undefined`, `undefined`
- D) `ReferenceError`, `ReferenceError`, `ReferenceError`

**Answer: B) `1`, `ReferenceError`, `ReferenceError`**

> `var` is function-scoped (not block-scoped), so `a` leaks out of the block and is accessible. `let` and `const` are block-scoped, so `b` and `c` are not accessible outside the `{}` block, causing a `ReferenceError`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer tries to reassign a `const` variable holding an object. What is the outcome?

```js
const user = { name: "Alice" };
user.name = "Bob";
user = { name: "Charlie" };
```

- A) Both statements succeed; `user.name` becomes `"Charlie"`
- B) The first statement succeeds; the second throws a `TypeError`
- C) Both statements throw a `TypeError`
- D) `const` prevents all changes, so both statements are silently ignored

**Answer: B) The first statement succeeds; the second throws a `TypeError`**

> `const` prevents reassignment of the variable binding, but the object it points to is still mutable. Mutating a property (`user.name = "Bob"`) is allowed, but reassigning the variable (`user = {...}`) throws a `TypeError: Assignment to constant variable`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What will the following code output?

```js
console.log(x);
var x = 5;
console.log(x);
```

- A) `ReferenceError`, then `5`
- B) `undefined`, then `5`
- C) `5`, then `5`
- D) `null`, then `5`

**Answer: B) `undefined`, then `5`**

> `var` declarations are hoisted to the top of their scope, but the initialisation is not. At the first `console.log`, `x` exists in memory but has not yet been assigned `5`, so its value is `undefined`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A team decides to use `let` throughout their codebase instead of `var`. Which of the following is the most accurate reason?

- A) `let` variables are faster at runtime than `var`
- B) `let` prevents all accidental mutations of a variable
- C) `let` is block-scoped and avoids unintended variable leakage into outer scopes
- D) `let` variables are automatically initialised to `null`

**Answer: C) `let` is block-scoped and avoids unintended variable leakage into outer scopes**

> The primary advantage of `let` over `var` is block scoping, which confines a variable to the `{}` block where it is declared. This prevents the common bug of loop variables or conditional variables leaking into the enclosing function scope.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 2. HOISTING & SCOPE

<br>

## Q. What is the output of the following code?

```js
console.log(foo());
console.log(bar());

function foo() { return "foo"; }
var bar = function() { return "bar"; };
```

- A) `"foo"`, `"bar"`
- B) `"foo"`, `TypeError`
- C) `TypeError`, `TypeError`
- D) `undefined`, `"bar"`

**Answer: B) `"foo"`, `TypeError`**

> Function declarations are fully hoisted (both the name and the body), so `foo()` works before its declaration. `bar` is a `var`-declared variable hoisted as `undefined`; calling `undefined()` throws a `TypeError: bar is not a function`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer runs the following code and is surprised by the output. What does it print?

```js
let x = "global";

function outer() {
  let x = "outer";
  function inner() {
    console.log(x);
  }
  inner();
}
outer();
```

- A) `"global"`
- B) `undefined`
- C) `"outer"`
- D) `ReferenceError`

**Answer: C) `"outer"`**

> JavaScript uses lexical (static) scoping. When `inner` looks up `x`, it first checks its own scope (not found), then the enclosing `outer` scope where `x = "outer"` is found. The global `x` is shadowed by the `outer` scope\'s `x`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What will the following snippet output and why?

```js
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log(i), 0);
}
```

- A) `0`, `1`, `2`
- B) `3`, `3`, `3`
- C) `undefined`, `undefined`, `undefined`
- D) `0`, `0`, `0`

**Answer: B) `3`, `3`, `3`**

> `var` is function-scoped, so all three callbacks share the same `i` variable. By the time the `setTimeout` callbacks fire, the loop has finished and `i` is `3`. Replacing `var` with `let` would fix this because `let` creates a new binding per iteration.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the Temporal Dead Zone (TDZ) in ES6?

- A) A period where `var` variables are `undefined` before assignment
- B) A period between entering a block and the declaration of a `let`/`const` variable where accessing it throws a `ReferenceError`
- C) The time it takes for a Promise to settle
- D) A garbage-collection phase that nullifies unused variables

**Answer: B) A period between entering a block and the declaration of a `let`/`const` variable where accessing it throws a `ReferenceError`**

> When a block is entered, `let` and `const` bindings are created but remain uninitialised until the declaration line is reached. Accessing them before that line results in a `ReferenceError`. This zone is called the Temporal Dead Zone.

**Example**

```js
{
    // --- Start of TDZ for 'myVar' ---
    console.log(myVar); // ❌ ReferenceError: Cannot access 'myVar' before initialization
    
    let myVar = "Hello!"; // --- End of TDZ for 'myVar' ---
    console.log(myVar); // ✅ "Hello!"
}
```

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 3. CLOSURES

<br>

## Q. What is printed by the following code?

```js
function makeCounter() {
  let count = 0;
  return {
    increment() { count++; },
    getCount() { return count; }
  };
}

const counter = makeCounter();
counter.increment();
counter.increment();
console.log(counter.getCount());
```

- A) `0`
- B) `1`
- C) `2`
- D) `NaN`

**Answer: C) `2`**

> `makeCounter` returns an object whose methods close over the local `count` variable. Each call to `increment` mutates the same `count` in the closure, so after two increments `getCount()` returns `2`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer wants to create a private variable in JavaScript without using classes. Which pattern is most appropriate?

- A) Store the variable on `window` with a unique name
- B) Use a closure to encapsulate the variable inside a function
- C) Prefix the variable name with an underscore
- D) Use `Object.freeze` on the variable

**Answer: B) Use a closure to encapsulate the variable inside a function**

> Closures are the classic ES5/ES6 way to simulate private state. A variable declared inside a factory function is inaccessible from outside but can be read or mutated through the returned functions that close over it.

**Example:**

```js
function createCounter() {
  // This variable is private; it cannot be accessed directly from outside
  let count = 0; 

  return {
    increment: function() {
      count++;
      return count;
    },
    getCount: function() {
      return count;
    }
  };
}

const counter = createCounter();

console.log(counter.increment()); // 1
console.log(counter.getCount());  // 1
console.log(counter.count);       // undefined (Privacy confirmed!)
```

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What will the following code output?

```js
function outer() {
  let x = 10;
  function inner() {
    x += 5;
    return x;
  }
  return inner;
}

const fn = outer();
console.log(fn());
console.log(fn());
```

- A) `15`, `15`
- B) `15`, `20`
- C) `10`, `15`
- D) `NaN`, `NaN`

**Answer: B) `15`, `20`**

> `inner` closes over `x` from `outer`. Each call to `fn()` increments `x` by `5` within the same closure environment. First call: `10 + 5 = 15`; second call: `15 + 5 = 20`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 4. TEMPLATE LITERALS

<br>

## Q. A developer needs to build a multi-line HTML string dynamically. Which approach is cleanest in ES6?

```js
const tag = "h1";
const content = "Hello";
```

- A) `"<" + tag + ">" + content + "</" + tag + ">"`
- B) `` `<${tag}>${content}</${tag}>` ``
- C) `String.concat("<", tag, ">", content, "</", tag, ">")`
- D) `new String("<" + tag + ">" + content + "</" + tag + ">")`

**Answer: B) `` `<${tag}>${content}</${tag}>` ``**

> Template literals (backtick strings) support embedded expressions via `${}` and preserve line breaks without escape sequences, making them ideal for building dynamic HTML or multi-line strings cleanly.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following tagged template literal?

```js
function tag(strings, ...values) {
  return strings[0] + values[0] * 2 + strings[1];
}

const a = 5;
console.log(tag`Value is ${a} done`);
```

- A) `Value is 5 done`
- B) `Value is 10 done`
- C) `Value is NaN done`
- D) `TypeError`

**Answer: B) `Value is 10 done`**

> A tagged template passes the static string parts as an array (`strings`) and the interpolated values as rest arguments (`values`). Here `strings[0]` is `"Value is "`, `values[0]` is `5`, multiplied by `2` gives `10`, and `strings[1]` is `" done"`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does the following code output?

```js
const a = 5;
const b = 10;
console.log(`Sum: ${a + b}, Product: ${a * b}`);
```

- A) `Sum: ${a + b}, Product: ${a * b}`
- B) `Sum: 15, Product: 50`
- C) `Sum: 510, Product: 50`
- D) `TypeError: invalid template expression`

**Answer: B) `Sum: 15, Product: 50`**

> Expressions inside `${}` are fully evaluated at runtime. `a + b` evaluates to `15` and `a * b` evaluates to `50`, producing `Sum: 15, Product: 50`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 5. ARROW FUNCTIONS

<br>

## Q. A developer replaces a regular function with an arrow function inside an object method. What will be the output?

```js
const obj = {
  name: "Alice",
  greet: () => {
    console.log(`Hello, ${this.name}`);
  }
};
obj.greet();
```

- A) `Hello, Alice`
- B) `Hello, undefined`
- C) `Hello, `
- D) `TypeError`

**Answer: B) `Hello, undefined`**

> Arrow functions do not have their own `this`. They capture `this` from the lexical (enclosing) scope at definition time. At the top level (outside any function), `this.name` is `undefined` (or in strict mode also `undefined`). To get `"Alice"`, a regular function expression should be used.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. Which of the following is a valid single-expression arrow function that returns the square of a number?

- A) `const sq = (n) => { n * n };`
- B) `const sq = (n) => n * n;`
- C) `const sq = n => { return };`
- D) `const sq = => n * n;`

**Answer: B) `const sq = (n) => n * n;`**

> Arrow functions with a single expression body omit both `{}` and `return` — the expression result is implicitly returned. Option A uses `{}` without `return`, so it returns `undefined`. Options C and D are syntactically invalid.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following code?

```js
function Timer() {
  this.seconds = 0;
  setInterval(() => {
    this.seconds++;
  }, 1000);
}

const t = new Timer();
```

After 3 seconds, what is the value of `t.seconds`?

- A) `0` — `this` inside the arrow function refers to the global object
- B) `3` — the arrow function captures `this` from the `Timer` constructor
- C) `undefined` — arrow functions cannot access `this`
- D) `TypeError` is thrown immediately

**Answer: B) `3` — the arrow function captures `this` from the `Timer` constructor**

> Arrow functions inherit `this` from their enclosing lexical context, which here is the `Timer` constructor. Every tick increments `this.seconds` on the `Timer` instance, so after 3 seconds `t.seconds === 3`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 6. CLASSES & INHERITANCE

<br>

## Q. What will the following code output?

```js
class Animal {
  constructor(name) {
    this.name = name;
  }
  speak() {
    return `${this.name} makes a noise.`;
  }
}

class Dog extends Animal {
  speak() {
    return `${this.name} barks.`;
  }
}

const d = new Dog("Rex");
console.log(d.speak());
```

- A) `Rex makes a noise.`
- B) `Rex barks.`
- C) `undefined barks.`
- D) `TypeError`

**Answer: B) `Rex barks.`**

> `Dog` extends `Animal` and overrides the `speak` method. When `d.speak()` is called, JavaScript finds `speak` on `Dog.prototype` first (method resolution order), returning `"Rex barks."`. The `name` property is set by `Animal`\'s constructor via `super`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer forgets to call `super()` inside a subclass constructor. What happens?

```js
class Vehicle {
  constructor(type) { this.type = type; }
}

class Car extends Vehicle {
  constructor(brand) {
    this.brand = brand; // super() not called
  }
}

new Car("Toyota");
```

- A) `this.brand` is set and `this.type` is `undefined`
- B) `ReferenceError: Must call super constructor before accessing 'this'`
- C) The `Vehicle` constructor is automatically called with `undefined`
- D) The code runs without error

**Answer: B) `ReferenceError: Must call super constructor before accessing 'this'`**

> In a derived class constructor, `this` is not initialised until `super()` is called. Accessing `this` before `super()` throws a `ReferenceError`. This is enforced by the ES6 class specification.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does the `static` keyword do in an ES6 class?

```js
class MathHelper {
  static add(a, b) { return a + b; }
}
```

- A) `add` can only be called on instances of `MathHelper`
- B) `add` is defined on `MathHelper` itself and cannot be called on instances
- C) `add` is shared between parent and child classes
- D) `add` becomes a private method

**Answer: B) `add` is defined on `MathHelper` itself and cannot be called on instances**

> Static methods belong to the class constructor, not to instances. `MathHelper.add(1, 2)` works, but `new MathHelper().add(1, 2)` throws a `TypeError`. Static methods are useful for utility or factory functions that don\'t need instance state.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 7. DESTRUCTURING

<br>

## Q. What is the value of `a` and `b` after the following destructuring?

```js
const [a, , b] = [10, 20, 30];
```

- A) `a = 10`, `b = 20`
- B) `a = 10`, `b = 30`
- C) `a = 20`, `b = 30`
- D) `SyntaxError`

**Answer: B) `a = 10`, `b = 30`**

> Array destructuring maps by position. The empty slot (`,`) skips the second element `20`. So `a` receives the first element `10` and `b` receives the third element `30`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What will be the value of `city` in the following destructuring?

```js
const { address: { city } = {} } = {};
console.log(city);
```

- A) `""`
- B) `null`
- C) `undefined`
- D) `ReferenceError`

**Answer: C) `undefined`**

> The outer object is empty, so `address` is `undefined`. The default `= {}` kicks in, giving an empty object. Destructuring `city` from an empty object yields `undefined` (not a `ReferenceError`), because object destructuring of a missing key returns `undefined`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer wants to rename a destructured property. Which syntax is correct?

```js
const { name: firstName } = { name: "Alice" };
```

- A) This is invalid — destructuring cannot rename properties
- B) `firstName` is `"Alice"` and `name` is also accessible
- C) `firstName` is `"Alice"` and `name` is not declared as a new variable
- D) `firstName` is `undefined`

**Answer: C) `firstName` is `"Alice"` and `name` is not declared as a new variable**

> The `{ name: firstName }` syntax extracts the `name` property and binds its value to a new variable called `firstName`. The identifier `name` is not introduced as a variable — only `firstName` is.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is printed by the following function that uses parameter destructuring?

```js
function display({ title, author = "Unknown" }) {
  console.log(`${title} by ${author}`);
}

display({ title: "ES6 Guide" });
```

- A) `ES6 Guide by undefined`
- B) `ES6 Guide by`
- C) `ES6 Guide by Unknown`
- D) `TypeError: Cannot destructure property 'author'`

**Answer: C) `ES6 Guide by Unknown`**

> The destructuring default `author = "Unknown"` is applied when `author` is `undefined` (i.e., not provided). Because the passed object has no `author` key, the default value `"Unknown"` is used.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 8. SPREAD & REST OPERATORS

<br>

## Q. What is the output of the following code?

```js
function sum(...numbers) {
  return numbers.reduce((acc, n) => acc + n, 0);
}
console.log(sum(1, 2, 3, 4));
```

- A) `[1, 2, 3, 4]`
- B) `10`
- C) `NaN`
- D) `TypeError`

**Answer: B) `10`**

> The rest parameter `...numbers` collects all arguments into a true array. `reduce` then sums them: `0 + 1 + 2 + 3 + 4 = 10`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer wants to merge two arrays without mutating either. Which ES6 approach is correct?

```js
const a = [1, 2];
const b = [3, 4];
```

- A) `a.push(...b)`
- B) `const c = [...a, ...b];`
- C) `const c = a.concat; b;`
- D) `const c = a + b;`

**Answer: B) `const c = [...a, ...b];`**

> The spread operator `...` expands each array into individual elements inside a new array literal, producing `[1, 2, 3, 4]` without modifying `a` or `b`. Option A mutates `a`. Options C and D are invalid or produce incorrect results.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following code?

```js
const original = { a: 1, b: { c: 2 } };
const copy = { ...original };
copy.b.c = 99;
console.log(original.b.c);
```

- A) `2`
- B) `99`
- C) `undefined`
- D) `TypeError`

**Answer: B) `99`**

> The spread operator performs a **shallow** copy. Top-level properties are copied by value, but nested objects are still shared by reference. Mutating `copy.b.c` also mutates `original.b.c` because both point to the same nested object.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 9. ENHANCED OBJECT LITERALS

<br>

## Q. What does the following ES6 shorthand property syntax produce?

```js
const x = 10;
const y = 20;
const point = { x, y };
console.log(point);
```

- A) `{ x: "x", y: "y" }`
- B) `{ x: 10, y: 20 }`
- C) `{ "x": undefined, "y": undefined }`
- D) `SyntaxError`

**Answer: B) `{ x: 10, y: 20 }`**

> ES6 shorthand property notation allows `{ x }` as an abbreviation for `{ x: x }`. The property name becomes the variable name and the value becomes the variable\'s value.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is printed by the following code using a computed property name?

```js
const key = "score";
const obj = { [key]: 100 };
console.log(obj.score);
```

- A) `undefined`
- B) `"score"`
- C) `100`
- D) `SyntaxError`

**Answer: C) `100`**

> ES6 computed property names use `[]` to evaluate an expression as the property key. `[key]` resolves to `"score"`, so `obj` becomes `{ score: 100 }`, and `obj.score` returns `100`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer refactors a function property using ES6 method shorthand. Which of the following is equivalent?

```js
// Original
const calc = {
  add: function(a, b) { return a + b; }
};
```

- A) `const calc = { add(a, b) { return a + b; } };`
- B) `const calc = { add: (a, b) => a + b };`
- C) Both A and B are equivalent
- D) Neither A nor B is equivalent

**Answer: A) `const calc = { add(a, b) { return a + b; } };`**

> ES6 method shorthand (option A) is a direct replacement for `key: function() {}` syntax. Option B uses an arrow function, which differs in `this` binding and cannot be used as a constructor — making it not fully equivalent in all contexts.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 10. ARRAY METHODS

<br>

## Q. A developer needs to filter out even numbers from an array and double the remaining odd numbers. What is the output?

```js
const result = [1, 2, 3, 4, 5]
  .filter(n => n % 2 !== 0)
  .map(n => n * 2);
console.log(result);
```

- A) `[2, 4, 6, 8, 10]`
- B) `[2, 6, 10]`
- C) `[1, 3, 5]`
- D) `[1, 2, 3, 4, 5]`

**Answer: B) `[2, 6, 10]`**

> `filter` keeps only odd numbers: `[1, 3, 5]`. `map` then doubles each: `[2, 6, 10]`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does the following code return?

```js
const found = [10, 20, 30, 40].find(n => n > 25);
console.log(found);
```

- A) `[30, 40]`
- B) `30`
- C) `true`
- D) `3` (index)

**Answer: B) `30`**

> `Array.prototype.find` returns the **first element** that satisfies the predicate, not an array of matches. The first value greater than `25` is `30`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following `reduce` call?

```js
const words = ["hello", "world", "foo"];
const result = words.reduce((acc, word) => acc + word.length, 0);
console.log(result);
```

- A) `"helloworldfoo"`
- B) `13`
- C) `3`
- D) `NaN`

**Answer: B) `13`**

> `reduce` accumulates the total character count: `5 (hello) + 5 (world) + 3 (foo) = 13`. The initial value `0` ensures the accumulator starts as a number.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does `Array.from` return in the following code?

```js
const result = Array.from("ES6");
console.log(result);
```

- A) `["ES6"]`
- B) `["E", "S", "6"]`
- C) `[69, 83, 54]` (char codes)
- D) `TypeError`

**Answer: B) `["E", "S", "6"]`**

> `Array.from` converts any iterable or array-like object into an array. A string is iterable and iterates over its Unicode characters, producing `["E", "S", "6"]`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does `Array.prototype.flat()` do with a nested array? 

```js
const nested = [1, [2, [3, [4]]]];
console.log(nested.flat());
console.log(nested.flat(2));
console.log(nested.flat(Infinity));
```

- A) `[1, 2, 3, 4]`, `[1, 2, 3, 4]`, `[1, 2, 3, 4]`
- B) `[1, 2, [3, [4]]]`, `[1, 2, 3, [4]]`, `[1, 2, 3, 4]`
- C) `[1, [2, [3, [4]]]]`, `[1, 2, [3, [4]]]`, `[1, 2, 3, 4]`
- D) `TypeError`

**Answer: B) `[1, 2, [3, [4]]]`, `[1, 2, 3, [4]]`, `[1, 2, 3, 4]`**

> `flat()` with no argument defaults to depth `1`, flattening one level. `flat(2)` flattens two levels deep. `flat(Infinity)` recursively flattens all levels regardless of nesting depth.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. How does `Array.prototype.flatMap()` differ from calling `.map().flat()`? 

```js
const sentences = ["Hello World", "ES6 Rocks"];
const words = sentences.flatMap(s => s.split(" "));
console.log(words);
```

- A) `[["Hello", "World"], ["ES6", "Rocks"]]`
- B) `["Hello World", "ES6 Rocks"]`
- C) `["Hello", "World", "ES6", "Rocks"]`
- D) `TypeError`

**Answer: C) `["Hello", "World", "ES6", "Rocks"]`**

> `flatMap` applies the mapping function and then flattens the result by **one level** in a single pass. It is equivalent to `.map(fn).flat(1)` but more efficient.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does `Array.prototype.at()` return for negative indices?

```js
const arr = [10, 20, 30, 40, 50];
console.log(arr.at(0));
console.log(arr.at(-1));
console.log(arr.at(-2));
```

- A) `10`, `undefined`, `undefined`
- B) `10`, `50`, `40`
- C) `10`, `40`, `30`
- D) `50`, `40`, `30`

**Answer: B) `10`, `50`, `40`**

> `Array.prototype.at()` accepts negative indices, where `-1` is the last element, `-2` is the second-to-last, and so on. This is the modern, readable alternative to `arr[arr.length - 1]`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 11. MAP & SET

<br>

## Q. What is the size of the Set after the following operations?

```js
const s = new Set([1, 2, 3, 2, 1]);
s.add(4);
s.add(2);
console.log(s.size);
```

- A) `6`
- B) `5`
- C) `4`
- D) `3`

**Answer: C) `4`**

> A `Set` stores only unique values. The initial array `[1, 2, 3, 2, 1]` produces `{1, 2, 3}`. Adding `4` gives `{1, 2, 3, 4}`. Adding `2` again is a no-op since `2` already exists, so the final size is `4`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer uses an object as a Map key. What will be the output?

```js
const map = new Map();
const key = { id: 1 };
map.set(key, "value1");
map.set({ id: 1 }, "value2");
console.log(map.size);
```

- A) `1`
- B) `2`
- C) `TypeError`
- D) `undefined`

**Answer: B) `2`**

> `Map` uses reference equality for object keys. `key` and `{ id: 1 }` are two distinct object references in memory, so they are treated as two different keys, giving a size of `2`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the key difference between a plain object `{}` and a `Map` for storing key-value pairs?

- A) `Map` only accepts string keys; objects accept any type
- B) `Map` maintains insertion order and accepts any value as a key, whereas object keys are coerced to strings
- C) Objects are faster than `Map` in all cases
- D) `Map` cannot be iterated

**Answer: B) `Map` maintains insertion order and accepts any value as a key, whereas object keys are coerced to strings**

> `Map` guarantees iteration in insertion order and allows keys of any type (objects, functions, primitives). Plain objects coerce keys to strings (except Symbols) and do not guarantee order for integer-like keys.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 12. MODULES

<br>

## Q. A developer has the following two files. What will `main.js` print?

```js
// math.js
export const PI = 3.14159;
export function area(r) { return PI * r * r; }
export default function circumference(r) { return 2 * PI * r; }
```

```js
// main.js
import circumference, { area, PI } from "./math.js";
console.log(PI);
console.log(area(1).toFixed(2));
console.log(circumference(1).toFixed(2));
```

- A) `3.14159`, `3.14`, `3.14`
- B) `3.14159`, `6.28`, `6.28`
- C) `undefined`, `NaN`, `NaN`
- D) `SyntaxError`

**Answer: A) `3.14159`, `3.14`, `3.14`**

> Named exports (`PI`, `area`) are imported with `{}`. The default export (`circumference`) is imported without `{}`. `area(1) = PI * 1 * 1 ≈ 3.14159`, which rounds to `"3.14"`. `circumference(1) = 2 * PI * 1 ≈ 6.28` — wait, that also rounds to `"6.28"`. Re-check: `area(1).toFixed(2)` = `"3.14"`, `circumference(1).toFixed(2)` = `"6.28"`. Option B is correct.

**Corrected Answer: B) `3.14159`, `3.14`, `6.28`**

> `PI` is `3.14159`. `area(1) = 3.14159 * 1 * 1 ≈ 3.14` (toFixed 2). `circumference(1) = 2 * 3.14159 * 1 ≈ 6.28` (toFixed 2).

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the difference between a named export and a default export?

- A) Named exports can only export functions; default exports can export anything
- B) A module can have multiple named exports but only one default export
- C) Default exports must be imported with the same name; named exports can be renamed
- D) Named exports use `module.exports`; default exports use `export default`

**Answer: B) A module can have multiple named exports but only one default export**

> ES6 modules allow any number of named exports (`export const x`, `export function y`), but only one `export default` per file. Named exports must be imported with `{}` (or renamed with `as`), while default exports are imported without `{}` using any name the importer chooses.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer writes `import * as utils from "./utils.js"`. What does `utils` contain?

- A) Only the default export
- B) A namespace object with all named exports as properties
- C) An array of all exported values
- D) `undefined` if there is no default export

**Answer: B) A namespace object with all named exports as properties**

> The `* as name` syntax creates a module namespace object. Every named export from `utils.js` becomes a property on `utils`. The default export is accessible as `utils.default`. This is useful for collecting all exports into one object.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer wants to load a module only when a button is clicked. Which syntax achieves this? 

```js
button.addEventListener("click", async () => {
  // Load the chart library only on demand
  const { renderChart } = await import("./chart.js");
  renderChart(data);
});
```

- A) This is invalid — ES6 `import` statements must be at the top of the file
- B) This is valid — dynamic `import()` returns a Promise and can be called anywhere
- C) `import()` can only be used inside `async` functions
- D) `import()` is synchronous and blocks the thread while loading

**Answer: B) This is valid — dynamic `import()` returns a Promise and can be called anywhere**

> Dynamic `import()` is a function-like expression that returns a Promise resolving to the module\'s namespace object. Unlike static `import` declarations, it can appear anywhere in code — inside conditions, event handlers, or async functions — enabling **code splitting** and **lazy loading**.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the difference between `import()` and a static `import` declaration? 

- A) Static imports are evaluated lazily; dynamic imports are evaluated eagerly at parse time
- B) Static imports are hoisted and resolved before any code runs; dynamic `import()` resolves at runtime and returns a Promise
- C) Dynamic `import()` can only import default exports
- D) Static imports can be used inside functions; dynamic `import()` cannot

**Answer: B) Static imports are hoisted and resolved before any code runs; dynamic `import()` resolves at runtime and returns a Promise**

> Static `import` declarations are hoisted — the module is fetched and evaluated before the module\'s own code runs. Dynamic `import()` is evaluated at the point it is called, returning a Promise. This enables runtime conditions to control which modules are loaded, supporting features like A/B testing, locale-based loading, and route-based code splitting.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 13. ITERATORS & GENERATORS

<br>

## Q. What will the following generator function produce?

```js
function* counter(start = 0) {
  while (true) {
    yield start++;
  }
}

const gen = counter(1);
console.log(gen.next().value);
console.log(gen.next().value);
console.log(gen.next().value);
```

- A) `1`, `1`, `1`
- B) `1`, `2`, `3`
- C) `0`, `1`, `2`
- D) `undefined`, `undefined`, `undefined`

**Answer: B) `1`, `2`, `3`**

> `counter(1)` starts `start` at `1`. Each `gen.next()` resumes execution until the next `yield`, returning the current value of `start` and then incrementing it. So the sequence is `1`, `2`, `3`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following iterator protocol usage?

```js
const range = {
  [Symbol.iterator]() {
    let n = 1;
    return {
      next() {
        return n <= 3 ? { value: n++, done: false } : { done: true };
      }
    };
  }
};

for (const val of range) {
  console.log(val);
}
```

- A) `1`, `2`, `3`, `4`
- B) `1`, `2`, `3`
- C) `undefined`, `undefined`, `undefined`
- D) `TypeError`

**Answer: B) `1`, `2`, `3`**

> The object implements the iterator protocol via `[Symbol.iterator]`. `for...of` calls `next()` repeatedly until `done: true` is returned. The values `1`, `2`, `3` are yielded before `n` exceeds `3`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the `done` value of a generator after it returns?

```js
function* gen() {
  yield 1;
  return "finished";
}

const g = gen();
console.log(g.next()); // { value: 1, done: false }
console.log(g.next()); // ?
console.log(g.next()); // ?
```

- A) `{ value: "finished", done: false }`, then `{ value: undefined, done: false }`
- B) `{ value: "finished", done: true }`, then `{ value: undefined, done: true }`
- C) `{ value: undefined, done: true }`, then `{ value: undefined, done: true }`
- D) `TypeError`

**Answer: B) `{ value: "finished", done: true }`, then `{ value: undefined, done: true }`**

> When a generator executes a `return` statement, the next `next()` call returns `{ value: returnValue, done: true }`. All subsequent calls return `{ value: undefined, done: true }` because the generator is exhausted.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 14. EVENT LOOP

<br>

## Q. What is the order of output for the following code?

```js
console.log("1");
setTimeout(() => console.log("2"), 0);
Promise.resolve().then(() => console.log("3"));
console.log("4");
```

- A) `1`, `2`, `3`, `4`
- B) `1`, `4`, `2`, `3`
- C) `1`, `4`, `3`, `2`
- D) `1`, `3`, `4`, `2`

**Answer: C) `1`, `4`, `3`, `2`**

> Synchronous code runs first: `"1"` then `"4"`. After the call stack is empty, microtasks (Promises) are drained before macrotasks (setTimeout). So the `.then` callback fires (`"3"`) before the `setTimeout` callback (`"2"`).

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer has the following code. In what order are the messages logged?

```js
console.log("start");

setTimeout(() => console.log("timeout 1"), 0);
setTimeout(() => console.log("timeout 2"), 0);

Promise.resolve()
  .then(() => console.log("promise 1"))
  .then(() => console.log("promise 2"));

console.log("end");
```

- A) `start`, `end`, `timeout 1`, `timeout 2`, `promise 1`, `promise 2`
- B) `start`, `end`, `promise 1`, `promise 2`, `timeout 1`, `timeout 2`
- C) `start`, `promise 1`, `end`, `promise 2`, `timeout 1`, `timeout 2`
- D) `start`, `end`, `promise 1`, `timeout 1`, `promise 2`, `timeout 2`

**Answer: B) `start`, `end`, `promise 1`, `promise 2`, `timeout 1`, `timeout 2`**

> Synchronous code runs first (`start`, `end`). Then the microtask queue (Promises) is fully drained (`promise 1`, `promise 2`) before any macrotask (setTimeout) runs. Both `timeout 1` and `timeout 2` fire after all microtasks complete.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the call stack and why is it relevant to the event loop?

- A) The call stack stores Promise callbacks waiting to be resolved
- B) The call stack is a LIFO data structure that tracks currently executing functions; the event loop only processes callbacks when the call stack is empty
- C) The call stack manages network request queuing
- D) The call stack and event loop are the same thing

**Answer: B) The call stack is a LIFO data structure that tracks currently executing functions; the event loop only processes callbacks when the call stack is empty**

> The call stack records function invocations. The event loop\'s job is to pick callbacks from the task queue and push them onto the call stack — but only when the call stack is empty. This is why `setTimeout(..., 0)` doesn\'t execute immediately; it waits for the stack to clear.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 15. CONCURRENCY

<br>

## Q. A developer needs to fetch data from three independent APIs and proceed only after all succeed. Which approach is most appropriate?

```js
const p1 = fetch("/api/users");
const p2 = fetch("/api/posts");
const p3 = fetch("/api/comments");
```

- A) `await p1; await p2; await p3;`
- B) `Promise.all([p1, p2, p3])`
- C) `Promise.race([p1, p2, p3])`
- D) `Promise.allSettled([p1, p2, p3])`

**Answer: B) `Promise.all([p1, p2, p3])`**

> `Promise.all` runs all three fetches concurrently and resolves when every promise resolves. Option A runs them sequentially, wasting time. `Promise.race` resolves/rejects with the first settled promise. `Promise.allSettled` waits for all but does not reject if one fails.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does `Promise.allSettled` do differently from `Promise.all`?

- A) `Promise.allSettled` rejects immediately if any promise rejects
- B) `Promise.allSettled` resolves with results of all promises regardless of whether they fulfilled or rejected
- C) `Promise.allSettled` returns only the fulfilled values
- D) There is no difference

**Answer: B) `Promise.allSettled` resolves with results of all promises regardless of whether they fulfilled or rejected**

> `Promise.all` short-circuits on the first rejection. `Promise.allSettled` always waits for every promise and returns an array of result objects, each with a `status` of `"fulfilled"` or `"rejected"` and the corresponding `value` or `reason`. This is useful when you need all results regardless of failures.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following code?

```js
const p1 = Promise.resolve(1);
const p2 = Promise.reject(new Error("fail"));
const p3 = Promise.resolve(3);

Promise.all([p1, p2, p3])
  .then(values => console.log(values))
  .catch(err => console.log(err.message));
```

- A) `[1, Error, 3]`
- B) `[1, undefined, 3]`
- C) `fail`
- D) `[1, 3]`

**Answer: C) `fail`**

> `Promise.all` rejects as soon as any promise in the array rejects. `p2` rejects with `Error("fail")`, so the `.catch` handler is invoked with that error, printing `"fail"`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does `Promise.any` return, and how does it differ from `Promise.race`? 

```js
const p1 = Promise.reject(new Error("first fails"));
const p2 = new Promise(resolve => setTimeout(() => resolve("second"), 100));
const p3 = Promise.resolve("third");

Promise.any([p1, p2, p3]).then(v => console.log(v));
```

- A) Rejects immediately because `p1` rejects first
- B) `"third"` — resolves with the first fulfilled promise
- C) `"second"` — resolves with the last promise to settle
- D) `AggregateError` because one promise rejected

**Answer: B) `"third"` — resolves with the first fulfilled promise**

> `Promise.any` resolves with the **first fulfilled** promise, ignoring rejections. Unlike `Promise.race` (which settles with the first to settle — including rejections), `Promise.any` only cares about the first success. It rejects with an `AggregateError` only if **all** promises reject.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following `queueMicrotask` code? 

```js
console.log("start");

queueMicrotask(() => console.log("microtask"));

Promise.resolve().then(() => console.log("promise"));

setTimeout(() => console.log("timeout"), 0);

console.log("end");
```

- A) `start`, `end`, `timeout`, `microtask`, `promise`
- B) `start`, `end`, `microtask`, `promise`, `timeout`
- C) `start`, `microtask`, `promise`, `end`, `timeout`
- D) `start`, `end`, `promise`, `microtask`, `timeout`

**Answer: B) `start`, `end`, `microtask`, `promise`, `timeout`**

> `queueMicrotask` schedules a microtask, just like Promise callbacks. Both microtasks are drained before any macrotask (setTimeout). `queueMicrotask` and the Promise `.then` both run after synchronous code completes, in the order they were queued, before `"timeout"`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 16. PROMISES

<br>

## Q. What is the output of the following code?

```js
Promise.resolve(1)
  .then(v => v + 1)
  .then(v => { throw new Error("oops"); })
  .then(v => console.log("then:", v))
  .catch(e => console.log("catch:", e.message))
  .then(() => console.log("finally-like"));
```

- A) `then: 2`, `finally-like`
- B) `catch: oops`, `finally-like`
- C) `catch: oops`
- D) Uncaught Error: oops

**Answer: B) `catch: oops`, `finally-like`**

> The second `.then` throws, skipping the next `.then`. The `.catch` handler catches it and logs `"catch: oops"`. A `.then` after a `.catch` runs if the `.catch` does not re-throw, so `"finally-like"` is also logged.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the difference between `.then(onFulfilled, onRejected)` and `.then(onFulfilled).catch(onRejected)`?

- A) They are identical in all cases
- B) The two-argument form does not catch errors thrown inside `onFulfilled`; `.catch` does
- C) `.catch` only handles network errors
- D) The two-argument form always runs both callbacks

**Answer: B) The two-argument form does not catch errors thrown inside `onFulfilled`; `.catch` does**

> In `.then(onFulfilled, onRejected)`, if `onFulfilled` throws, `onRejected` in the same `.then` does **not** catch it. Using `.then(onFulfilled).catch(onRejected)` chains a separate handler that does catch errors from `onFulfilled`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer creates a Promise but never resolves or rejects it. What happens?

```js
const p = new Promise(() => {});
p.then(() => console.log("done"));
```

- A) `"done"` is logged immediately
- B) `"done"` is never logged; the Promise stays pending forever
- C) A `TypeError` is thrown after a timeout
- D) The Promise auto-resolves with `undefined`

**Answer: B) `"done"` is never logged; the Promise stays pending forever**

> A Promise remains in the pending state until its `resolve` or `reject` function is explicitly called. If neither is ever called, the `.then` callback never fires. This is a common source of memory leaks — always ensure a Promise eventually settles.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 17. ASYNC & AWAIT

<br>

## Q. What is the return type of an `async` function?

```js
async function greet() {
  return "Hello";
}
console.log(greet());
```

- A) `"Hello"`
- B) `undefined`
- C) A Promise that resolves to `"Hello"`
- D) A Promise that resolves to `undefined`

**Answer: C) A Promise that resolves to `"Hello"`**

> Every `async` function implicitly wraps its return value in a resolved Promise. `greet()` returns `Promise { "Hello" }`, not the string directly. To get `"Hello"`, you must `await greet()` or use `.then()`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What will the following `async/await` code output?

```js
async function fetchData() {
  const result = await Promise.resolve(42);
  return result * 2;
}

fetchData().then(v => console.log(v));
```

- A) `42`
- B) `84`
- C) `Promise { 84 }`
- D) `undefined`

**Answer: B) `84`**

> `await Promise.resolve(42)` suspends execution until the Promise resolves, giving `result = 42`. The function returns `42 * 2 = 84`. The `.then` handler receives `84` and logs it.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer writes the following `async` function. What is wrong with it?

```js
async function loadUser(id) {
  const response = await fetch(`/api/users/${id}`);
  const data = response.json();
  return data;
}
```

- A) `fetch` cannot be used inside an async function
- B) `response.json()` returns a Promise; `await` is missing, so `data` is a pending Promise
- C) The function should not use `async` since `fetch` is already asynchronous
- D) `return data` should be `return await data`

**Answer: B) `response.json()` returns a Promise; `await` is missing, so `data` is a pending Promise**

> `Response.prototype.json()` is asynchronous and returns a Promise. Without `await`, `data` holds an unresolved Promise object rather than the parsed JSON. The fix is `const data = await response.json();`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. How should errors be handled inside an `async` function?

```js
async function getData() {
  const res = await fetch("/api/data");
  const json = await res.json();
  return json;
}
```

- A) Wrap with `Promise.catch()` inside the function body
- B) Use a `try...catch` block around the `await` expressions
- C) `async` functions auto-handle all errors silently
- D) Use `.catch()` on every individual `await`

**Answer: B) Use a `try...catch` block around the `await` expressions**

> Inside an `async` function, `await` expressions that reject (or `throw`) can be caught with a standard `try...catch` block. This is the idiomatic and readable way to handle errors in async/await code, equivalent to attaching a `.catch()` on the returned Promise.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following code that uses `async/await` with `Promise.all`?

```js
async function run() {
  const [a, b] = await Promise.all([
    Promise.resolve(10),
    Promise.resolve(20)
  ]);
  console.log(a + b);
}
run();
```

- A) `[10, 20]`
- B) `30`
- C) `Promise { 30 }`
- D) `undefined`

**Answer: B) `30`**

> `Promise.all` resolves with an array `[10, 20]`. `await` unwraps it, and array destructuring assigns `a = 10`, `b = 20`. The sum `10 + 20 = 30` is logged.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 18. DEFAULT PARAMETERS

<br>

## Q. What is the output of the following function call? 

```js
function greet(name = "World") {
  return `Hello, ${name}!`;
}
console.log(greet());
console.log(greet("Alice"));
```

- A) `Hello, undefined!`, `Hello, Alice!`
- B) `Hello, World!`, `Hello, Alice!`
- C) `Hello, null!`, `Hello, Alice!`
- D) `TypeError`

**Answer: B) `Hello, World!`, `Hello, Alice!`**

> Default parameters are used when the argument is `undefined` (or omitted). The first call omits `name`, so the default `"World"` is used. The second call passes `"Alice"`, which overrides the default.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What happens when `null` is passed to a parameter that has a default value? 

```js
function connect(host = "localhost", port = 3000) {
  return `${host}:${port}`;
}
console.log(connect(null, null));
```

- A) `localhost:3000`
- B) `null:null`
- C) `localhost:null`
- D) `TypeError`

**Answer: B) `null:null`**

> Default parameters only apply when the argument is `undefined`. `null` is a distinct value — it is not `undefined` — so it does not trigger the default. Both `null` values are passed as-is, producing `"null:null"`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following code with an expression as a default parameter? 

```js
let count = 0;
function increment(n = ++count) {
  return n;
}
console.log(increment());
console.log(increment());
console.log(increment(10));
```

- A) `1`, `2`, `10`
- B) `1`, `1`, `10`
- C) `0`, `1`, `10`
- D) `1`, `2`, `3`

**Answer: A) `1`, `2`, `10`**

> Default parameter expressions are evaluated **at call time**, not at function definition time. Each call that omits `n` evaluates `++count` afresh. First call: `count` becomes `1`, `n = 1`. Second call: `count` becomes `2`, `n = 2`. Third call: explicit `10` is passed, default is not evaluated.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. Can a default parameter reference a previously declared parameter? 

```js
function box(width = 10, height = width * 2) {
  return `${width} x ${height}`;
}
console.log(box());
console.log(box(5));
```

- A) `10 x 20`, `5 x 20`
- B) `10 x 20`, `5 x 10`
- C) `10 x undefined`, `5 x undefined`
- D) `SyntaxError`

**Answer: B) `10 x 20`, `5 x 10`**

> Default parameters are evaluated left-to-right and later defaults can reference earlier parameters. When `box()` is called: `width = 10`, `height = 10 * 2 = 20`. When `box(5)` is called: `width = 5`, `height = 5 * 2 = 10`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 19. STRING METHODS

<br>

## Q. Which ES6 string method should be used to check if a URL begins with `"https"`? 

```js
const url = "https://example.com";
```

- A) `url.indexOf("https") > -1`
- B) `url.startsWith("https")`
- C) `url.includes("https")`
- D) `url.match(/^https/)`

**Answer: B) `url.startsWith("https")`**

> `String.prototype.startsWith(searchString, position)` is the ES6 idiomatic way to check if a string begins with a specific substring. It returns a boolean and is more readable than `indexOf` or a regex.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does the following code output? 

```js
console.log("ES6".repeat(3));
console.log("5".padStart(4, "0"));
console.log("hi".padEnd(5, "!"));
```

- A) `ES6ES6ES6`, `0005`, `hi!!!`
- B) `ES6ES6ES6`, `05`, `hi!!`
- C) `ES6ES6ES6`, `00005`, `hi!`
- D) `"ES6"*3`, `SyntaxError`, `SyntaxError`

**Answer: A) `ES6ES6ES6`, `0005`, `hi!!!`**

> `repeat(3)` duplicates the string three times. `padStart(4, "0")` pads `"5"` with `"0"` on the left until length is 4, giving `"0005"`. `padEnd(5, "!")` pads `"hi"` with `"!"` on the right until length is 5, giving `"hi!!!"`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer needs to check if a comma-separated string contains the word `"admin"`. Which method is most appropriate? 

```js
const roles = "user,moderator,admin,editor";
```

- A) `roles.indexOf("admin") !== -1`
- B) `roles.includes("admin")`
- C) `roles.endsWith("admin")`
- D) Both A and B

**Answer: D) Both A and B**

> Both `indexOf` (returning a non-negative index when found) and `includes` (returning `true`) correctly detect whether the substring `"admin"` exists anywhere in the string. `includes` is the more modern and readable ES6 approach.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following `String.raw` tagged template? 

```js
console.log(String.raw`Hello\nWorld`);
```

- A) `Hello` on one line, `World` on the next
- B) `Hello\nWorld` (the escape sequence is not processed)
- C) `HellonWorld`
- D) `SyntaxError`

**Answer: B) `Hello\nWorld` (the escape sequence is not processed)**

> `String.raw` is a built-in tag function that returns the raw string content with escape sequences left unprocessed. The `\n` is treated as two characters (`\` and `n`) rather than a newline, making it useful for file paths and regex patterns.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 20. FOR...OF AND FOR...IN

<br>

## Q. What does `for...in` iterate over compared to `for...of`? 

```js
const arr = [10, 20, 30];
arr.custom = "extra";

for (const key in arr) console.log(key);
// vs
for (const val of arr) console.log(val);
```

- A) `for...in` logs `10 20 30`, `for...of` logs `0 1 2 custom`
- B) `for...in` logs `0 1 2 custom`, `for...of` logs `10 20 30`
- C) Both log `10 20 30`
- D) Both log `0 1 2`

**Answer: B) `for...in` logs `0 1 2 custom`, `for...of` logs `10 20 30`**

> `for...in` iterates over all **enumerable property keys** of an object, including non-index properties and inherited ones — making it unsuitable for arrays. `for...of` iterates over **iterable values** using the `[Symbol.iterator]` protocol, yielding array elements only.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following `for...of` loop? 

```js
const map = new Map([["a", 1], ["b", 2], ["c", 3]]);
for (const [key, value] of map) {
  console.log(`${key}=${value}`);
}
```

- A) `a=1`, `b=2`, `c=3`
- B) `["a",1]`, `["b",2]`, `["c",3]`
- C) `a`, `b`, `c`
- D) `1`, `2`, `3`

**Answer: A) `a=1`, `b=2`, `c=3`**

> `Map` is iterable and yields `[key, value]` pairs. Destructuring `[key, value]` in the `for...of` loop unpacks each pair, so the template literal produces `"a=1"`, `"b=2"`, `"c=3"`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer uses `for...of` on a plain object. What happens? 

```js
const obj = { a: 1, b: 2 };
for (const val of obj) {
  console.log(val);
}
```

- A) Logs `1`, `2`
- B) Logs `a`, `b`
- C) `TypeError: obj is not iterable`
- D) Nothing is logged; the loop is skipped silently

**Answer: C) `TypeError: obj is not iterable`**

> Plain objects do not implement the `[Symbol.iterator]` protocol by default, so they are not iterable. Using `for...of` on them throws a `TypeError`. To iterate over an object\'s entries, use `for...of` with `Object.keys()`, `Object.values()`, or `Object.entries()`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What will the following code output? 

```js
function* gen() {
  yield "x";
  yield "y";
}
for (const v of gen()) {
  console.log(v);
}
```

- A) `"x"`, `"y"`, `undefined`
- B) `"x"`, `"y"`
- C) `{ value: "x", done: false }`, `{ value: "y", done: false }`
- D) `TypeError`

**Answer: B) `"x"`, `"y"`**

> Generators are iterable. `for...of` calls `next()` under the hood and unpacks `value` from each result until `done: true`. The final `return`-value (implicit `undefined`) is not emitted by `for...of`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 21. TYPE COERCION & EQUALITY

<br>

## Q. What is the output of the following comparisons? 

```js
console.log(0 == false);
console.log(0 === false);
console.log("" == false);
console.log(null == undefined);
console.log(null === undefined);
```

- A) `true`, `true`, `true`, `true`, `true`
- B) `true`, `false`, `true`, `true`, `false`
- C) `false`, `false`, `false`, `true`, `false`
- D) `true`, `false`, `false`, `true`, `false`

**Answer: B) `true`, `false`, `true`, `true`, `false`**

> `==` performs type coercion: `0 == false` (both become `0`), `"" == false` (both become `0`), `null == undefined` (special rule). `===` requires both type and value to match, so `0 === false` and `null === undefined` are both `false`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is `typeof null` in JavaScript? 

```js
console.log(typeof null);
console.log(typeof undefined);
console.log(typeof NaN);
console.log(typeof function(){});
```

- A) `"null"`, `"undefined"`, `"NaN"`, `"function"`
- B) `"object"`, `"undefined"`, `"number"`, `"function"`
- C) `"null"`, `"undefined"`, `"number"`, `"object"`
- D) `"object"`, `"undefined"`, `"NaN"`, `"object"`

**Answer: B) `"object"`, `"undefined"`, `"number"`, `"function"`**

> `typeof null === "object"` is a long-standing JavaScript bug that cannot be fixed for backwards compatibility. `typeof NaN === "number"` because `NaN` is a numeric value. `typeof function(){} === "function"` is a special case, even though functions are objects.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer checks for `NaN` using two different methods. What are the results? 

```js
console.log(isNaN("hello"));
console.log(Number.isNaN("hello"));
```

- A) `true`, `true`
- B) `false`, `false`
- C) `true`, `false`
- D) `false`, `true`

**Answer: C) `true`, `false`**

> The global `isNaN()` first coerces its argument to a number (`Number("hello")` is `NaN`) and then checks. `Number.isNaN()` does **no** coercion — it returns `true` only if the value is literally the `NaN` value. `"hello"` is a string, not `NaN`, so `Number.isNaN` returns `false`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following addition expressions? 

```js
console.log(1 + "2");
console.log(1 - "2");
console.log(true + true);
console.log([] + []);
console.log([] + {});
```

- A) `"12"`, `-1`, `2`, `""`, `"[object Object]"`
- B) `3`, `-1`, `2`, `[]`, `{}`
- C) `"12"`, `"12"`, `2`, `0`, `0`
- D) `TypeError` for all

**Answer: A) `"12"`, `-1`, `2`, `""`, `"[object Object]"`**

> `+` with a string triggers string concatenation. `-` always coerces to numbers. `true + true` is `1 + 1 = 2`. `[] + []` converts both arrays to `""` and concatenates. `[] + {}`: `[]` becomes `""` and `{}` becomes `"[object Object]"`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 22. OPTIONAL CHAINING & NULLISH COALESCING

<br>

## Q. A developer accesses a deeply nested property. What will the output be? 

```js
const user = { profile: { address: { city: "Paris" } } };
console.log(user?.profile?.address?.city);
console.log(user?.account?.balance);
```

- A) `"Paris"`, `0`
- B) `"Paris"`, `undefined`
- C) `"Paris"`, `TypeError`
- D) `undefined`, `undefined`

**Answer: B) `"Paris"`, `undefined`**

> Optional chaining `?.` short-circuits and returns `undefined` when a property in the chain is `null` or `undefined`, instead of throwing a `TypeError`. `user.account` is `undefined`, so `user?.account?.balance` safely returns `undefined`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the difference between `||` and `??` for providing fallback values? 

```js
const a = 0 || "default";
const b = 0 ?? "default";
const c = null ?? "fallback";
const d = "" || "fallback";
```

- A) `a = "default"`, `b = "default"`, `c = "fallback"`, `d = "fallback"`
- B) `a = "default"`, `b = 0`, `c = "fallback"`, `d = "fallback"`
- C) `a = 0`, `b = 0`, `c = null`, `d = ""`
- D) `a = "default"`, `b = 0`, `c = null`, `d = ""`

**Answer: B) `a = "default"`, `b = 0`, `c = "fallback"`, `d = "fallback"`**

> `||` falls back on any **falsy** value (`0`, `""`, `null`, `undefined`, `false`). `??` (nullish coalescing) only falls back on `null` or `undefined`. So `0 ?? "default"` returns `0` because `0` is not nullish, but `0 || "default"` returns `"default"` because `0` is falsy.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does the optional chaining operator do when used with a method call? 

```js
const obj = { greet: () => "Hello" };
console.log(obj.greet?.());
console.log(obj.farewell?.());
```

- A) `"Hello"`, `TypeError`
- B) `"Hello"`, `undefined`
- C) `"Hello"`, `null`
- D) `undefined`, `undefined`

**Answer: B) `"Hello"`, `undefined`**

> `?.()` is the optional call syntax. If the method exists, it is called normally. If it is `undefined` or `null`, the call is skipped and `undefined` is returned instead of throwing `TypeError: obj.farewell is not a function`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following code using the logical assignment operators? 

```js
let a = null;
let b = 0;
let c = "hello";

a ??= "default";
b ||= 42;
c &&= c.toUpperCase();

console.log(a, b, c);
```

- A) `"default"`, `42`, `"HELLO"`
- B) `null`, `0`, `"HELLO"`
- C) `"default"`, `0`, `"HELLO"`
- D) `"default"`, `42`, `"hello"`

**Answer: A) `"default"`, `42`, `"HELLO"`**

> `??=` assigns only if the left side is `null`/`undefined` (so `null ??= "default"` → `"default"`). `||=` assigns if the left side is falsy (`0` is falsy, so `0 ||= 42` → `42`). `&&=` assigns only if the left side is truthy (`"hello"` is truthy, so it becomes `"HELLO"`).

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 23. OBJECT METHODS

<br>

## Q. What is the output of the following `Object.assign` call? 

```js
const target = { a: 1, b: 2 };
const source = { b: 4, c: 5 };
const result = Object.assign(target, source);
console.log(result);
console.log(target === result);
```

- A) `{ a: 1, b: 2, c: 5 }`, `false`
- B) `{ a: 1, b: 4, c: 5 }`, `true`
- C) `{ a: 1, b: 4, c: 5 }`, `false`
- D) `{ a: 1, b: 2 }`, `true`

**Answer: B) `{ a: 1, b: 4, c: 5 }`, `true`**

> `Object.assign` **mutates** the target object and returns it. Overlapping keys from the source overwrite those in the target (`b: 4` overwrites `b: 2`). Because `target` is mutated and returned, `target === result` is `true`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of iterating with `Object.entries()`? 

```js
const scores = { alice: 90, bob: 85, carol: 92 };
const result = Object.entries(scores).map(([name, score]) => `${name}:${score}`);
console.log(result);
```

- A) `["alice", "bob", "carol"]`
- B) `[90, 85, 92]`
- C) `["alice:90", "bob:85", "carol:92"]`
- D) `[["alice", 90], ["bob", 85], ["carol", 92]]`

**Answer: C) `["alice:90", "bob:85", "carol:92"]`**

> `Object.entries()` returns an array of `[key, value]` pairs. Destructuring each pair in `map` gives `name` and `score`, which are combined into template literal strings.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the effect of `Object.freeze()` on an object? 

```js
const config = Object.freeze({ host: "localhost", port: 3000 });
config.port = 8080;
config.debug = true;
delete config.host;
console.log(config);
```

- A) `{ host: "localhost", port: 8080, debug: true }`
- B) `{ port: 3000 }`
- C) `{ host: "localhost", port: 3000 }`
- D) `TypeError` is thrown

**Answer: C) `{ host: "localhost", port: 3000 }`**

> `Object.freeze()` prevents adding, deleting, or modifying properties of an object. In non-strict mode, these operations silently fail. In strict mode, they throw a `TypeError`. The object remains unchanged as `{ host: "localhost", port: 3000 }`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. How is `Object.create(null)` different from `{}` for creating a lookup table? 

- A) `Object.create(null)` creates an immutable object
- B) `Object.create(null)` creates an object with no prototype, so it has no inherited properties like `toString` or `hasOwnProperty`
- C) `Object.create(null)` always returns `null`
- D) There is no difference between `Object.create(null)` and `{}`

**Answer: B) `Object.create(null)` creates an object with no prototype, so it has no inherited properties like `toString` or `hasOwnProperty`**

> Plain objects `{}` inherit from `Object.prototype`, giving them methods like `toString`, `hasOwnProperty`, and `constructor`. `Object.create(null)` creates a truly empty object with no prototype chain, making it safer as a pure lookup map where key collisions with inherited properties are impossible.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. How does `Object.seal()` differ from `Object.freeze()`? 

```js
const obj = Object.seal({ name: "Alice", age: 30 });
obj.name = "Bob";      // modify existing
obj.email = "a@b.com"; // add new property
delete obj.age;        // delete property
console.log(obj);
```

- A) `{ name: "Bob", email: "a@b.com" }`
- B) `{ name: "Bob", age: 30 }`
- C) `{ name: "Alice", age: 30 }`
- D) `TypeError` is thrown immediately

**Answer: B) `{ name: "Bob", age: 30 }`**

> `Object.seal()` **prevents adding or deleting** properties but **allows modifying existing** property values. `Object.freeze()` goes further — it also prevents modification of existing values.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does `Object.fromEntries()` do and how does it complement `Object.entries()`? 

```js
const entries = [["name", "Alice"], ["age", 30], ["role", "admin"]];
const obj = Object.fromEntries(entries);
console.log(obj);
```

- A) `[["name", "Alice"], ["age", 30], ["role", "admin"]]`
- B) `{ name: "Alice", age: 30, role: "admin" }`
- C) `{ 0: "name", 1: "age", 2: "role" }`
- D) `TypeError`

**Answer: B) `{ name: "Alice", age: 30, role: "admin" }`**

> `Object.fromEntries()` is the inverse of `Object.entries()` — it converts an iterable of `[key, value]` pairs into a plain object. This is commonly used after filtering or transforming entries with `Map` operations: `Object.fromEntries(Object.entries(obj).filter(...))`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. Why is `Object.hasOwn()` preferred over `obj.hasOwnProperty()` in modern code? 

```js
const obj = Object.create(null); // no prototype
obj.name = "Alice";

// Old way — throws TypeError because there\'s no hasOwnProperty
// obj.hasOwnProperty("name");

// New way
console.log(Object.hasOwn(obj, "name"));
console.log(Object.hasOwn(obj, "toString"));
```

- A) `false`, `true`
- B) `true`, `false`
- C) `true`, `true`
- D) `TypeError` for both

**Answer: B) `true`, `false`**

> `Object.hasOwn(obj, key)` is a static method that safely checks own properties regardless of the object\'s prototype. On objects created with `Object.create(null)`, calling `obj.hasOwnProperty()` throws a `TypeError` because there is no `hasOwnProperty` method inherited. `Object.hasOwn` avoids this pitfall.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does `structuredClone()` do that the spread operator cannot? 

```js
const original = { a: 1, b: { c: 2 }, d: [3, 4] };

const shallow = { ...original };
shallow.b.c = 99;

const deep = structuredClone(original);
deep.b.c = 77;
deep.d.push(5);

console.log(original.b.c); // ?
console.log(original.d.length); // ?
```

- A) `99`, `3`
- B) `2`, `2`
- C) `99`, `2`
- D) `2`, `3`

**Answer: C) `99`, `2`**

> The spread operator creates a **shallow copy** — nested objects are shared by reference, so `shallow.b.c = 99` mutates `original.b.c`. `structuredClone()` creates a **true deep clone** — all nested structures are new copies, so mutations to `deep.b.c` or `deep.d` do not affect `original`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is `Object.is()` and how does it differ from `===`? 

```js
console.log(Object.is(NaN, NaN));
console.log(Object.is(0, -0));
console.log(Object.is(1, 1));
console.log(NaN === NaN);
console.log(0 === -0);
```

- A) `true`, `true`, `true`, `false`, `false`
- B) `true`, `false`, `true`, `false`, `true`
- C) `false`, `false`, `true`, `false`, `true`
- D) `true`, `true`, `true`, `true`, `true`

**Answer: B) `true`, `false`, `true`, `false`, `true`**

> `Object.is` uses the **SameValue** algorithm. It correctly identifies `NaN === NaN` as `true` (unlike `===`) and correctly distinguishes `0` from `-0` (returning `false`, unlike `===` which returns `true`).

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 24. PROTOTYPE & THIS BINDING

<br>

## Q. What is the output of the following `call` and `apply` usage? 

```js
function introduce(greeting, punctuation) {
  return `${greeting}, I am ${this.name}${punctuation}`;
}

const person = { name: "Alice" };
console.log(introduce.call(person, "Hello", "!"));
console.log(introduce.apply(person, ["Hi", "."]));
```

- A) `"Hello, I am Alice!"`, `"Hi, I am Alice."`
- B) `"Hello, I am undefined!"`, `"Hi, I am undefined."`
- C) `TypeError` for both
- D) `"Hello, I am Alice!"`, `TypeError`

**Answer: A) `"Hello, I am Alice!"`, `"Hi, I am Alice."`**

> Both `call` and `apply` invoke a function with a specified `this` value. `call` accepts arguments individually; `apply` accepts them as an array. Both bind `this` to `person`, so `this.name` is `"Alice"`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does `bind` return, and how is it different from `call`? 

```js
function multiply(factor) {
  return this.value * factor;
}

const obj = { value: 5 };
const double = multiply.bind(obj, 2);
console.log(typeof double);
console.log(double());
```

- A) `"number"`, `10`
- B) `"function"`, `10`
- C) `"function"`, `undefined`
- D) `"object"`, `10`

**Answer: B) `"function"`, `10`**

> `bind` returns a **new function** with `this` permanently bound to the specified object and optionally pre-filled arguments (partial application). Unlike `call`/`apply`, it does not invoke the function immediately. Calling `double()` later executes `5 * 2 = 10`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following prototype chain lookup? 

```js
function Person(name) {
  this.name = name;
}
Person.prototype.greet = function() {
  return `Hi, I am ${this.name}`;
};

const p = new Person("Bob");
console.log(p.greet());
console.log(p.hasOwnProperty("greet"));
console.log(p.hasOwnProperty("name"));
```

- A) `"Hi, I am Bob"`, `true`, `true`
- B) `"Hi, I am Bob"`, `false`, `true`
- C) `"Hi, I am Bob"`, `true`, `false`
- D) `TypeError`

**Answer: B) `"Hi, I am Bob"`, `false`, `true`**

> `greet` is defined on `Person.prototype`, not directly on the instance `p`, so `p.hasOwnProperty("greet")` is `false`. `name` is set directly on `p` via the constructor (`this.name = name`), so `p.hasOwnProperty("name")` is `true`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following `instanceof` check? 

```js
class A {}
class B extends A {}
class C {}

const b = new B();
console.log(b instanceof B);
console.log(b instanceof A);
console.log(b instanceof C);
```

- A) `true`, `false`, `false`
- B) `true`, `true`, `false`
- C) `true`, `true`, `true`
- D) `false`, `true`, `false`

**Answer: B) `true`, `true`, `false`**

> `instanceof` checks the prototype chain. `b` is an instance of `B`, and because `B` extends `A`, `b` is also an instance of `A`. `b` has no connection to `C`\'s prototype chain, so `b instanceof C` is `false`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 25. SYMBOL

<br>

## Q. What is unique about a `Symbol` value? 

```js
const s1 = Symbol("id");
const s2 = Symbol("id");
console.log(s1 === s2);
console.log(typeof s1);
```

- A) `true`, `"symbol"`
- B) `false`, `"symbol"`
- C) `false`, `"object"`
- D) `true`, `"string"`

**Answer: B) `false`, `"symbol"`**

> Every `Symbol()` call creates a **unique** value, even if the same description string is given. The description is only for debugging. `typeof` a Symbol returns `"symbol"`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What happens when a Symbol is used as an object property key? 

```js
const ID = Symbol("id");
const user = {
  name: "Alice",
  [ID]: 42
};
console.log(user[ID]);
console.log(Object.keys(user));
console.log(JSON.stringify(user));
```

- A) `42`, `["name", "id"]`, `{"name":"Alice","id":42}`
- B) `42`, `["name"]`, `{"name":"Alice"}`
- C) `undefined`, `["name"]`, `{"name":"Alice"}`
- D) `42`, `["name", Symbol(id)]`, `{"name":"Alice"}`

**Answer: B) `42`, `["name"]`, `{"name":"Alice"}`**

> Symbol keys are **non-enumerable** by default and are excluded from `Object.keys()`, `for...in`, and `JSON.stringify()`. They are accessible only via the original Symbol reference or `Object.getOwnPropertySymbols()`. `user[ID]` correctly retrieves `42`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does `Symbol.for` do differently from `Symbol`? 

```js
const s1 = Symbol.for("shared");
const s2 = Symbol.for("shared");
const s3 = Symbol("shared");
console.log(s1 === s2);
console.log(s1 === s3);
```

- A) `true`, `true`
- B) `false`, `false`
- C) `true`, `false`
- D) `false`, `true`

**Answer: C) `true`, `false`**

> `Symbol.for(key)` uses a **global Symbol registry** — if a Symbol with the given key already exists, it returns the same Symbol. `Symbol("shared")` always creates a new, unique Symbol regardless of the description, so `s1 === s3` is `false`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. How does `Symbol.toPrimitive` control type coercion of an object? 

```js
const money = {
  amount: 42,
  currency: "USD",
  [Symbol.toPrimitive](hint) {
    if (hint === "number") return this.amount;
    if (hint === "string") return `${this.amount} ${this.currency}`;
    return this.amount; // default
  }
};

console.log(+money);
console.log(`${money}`);
console.log(money + 10);
```

- A) `42`, `"42 USD"`, `52`
- B) `42`, `"42"`, `"4210"`
- C) `"42 USD"`, `"42 USD"`, `"42 USD10"`
- D) `TypeError` for all

**Answer: A) `42`, `"42 USD"`, `52`**

> `Symbol.toPrimitive` receives a `hint` argument — `"number"`, `"string"`, or `"default"`. Unary `+` triggers `"number"` hint → `42`. Template literal triggers `"string"` hint → `"42 USD"`. Addition with a number triggers `"default"` hint → `42`, then `42 + 10 = 52`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the purpose of `Symbol.iterator` when added to a custom object? 

```js
const range = {
  from: 1,
  to: 5,
  [Symbol.iterator]() {
    let current = this.from;
    const last = this.to;
    return {
      next() {
        return current <= last
          ? { value: current++, done: false }
          : { value: undefined, done: true };
      }
    };
  }
};

console.log([...range]);
```

- A) `[{ from: 1, to: 5 }]`
- B) `[1, 2, 3, 4, 5]`
- C) `TypeError: range is not iterable`
- D) `[1, 5]`

**Answer: B) `[1, 2, 3, 4, 5]`**

> Adding `[Symbol.iterator]` makes any object iterable by implementing the iterator protocol. The spread operator, `for...of`, destructuring, and `Array.from` all rely on this protocol.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 26. WEAKMAP & WEAKSET

<br>

## Q. What is the key difference between `Map` and `WeakMap`? 

- A) `WeakMap` accepts any type of key; `Map` only accepts strings
- B) `WeakMap` keys must be objects, and entries are garbage-collected when the key object has no other references
- C) `WeakMap` is faster than `Map` in all cases
- D) `WeakMap` can store primitive values; `Map` cannot

**Answer: B) `WeakMap` keys must be objects, and entries are garbage-collected when the key object has no other references**

> `WeakMap` holds **weak references** to its keys. If no other reference to the key object exists, the garbage collector can reclaim that entry. This makes `WeakMap` ideal for associating private data with objects without causing memory leaks. Unlike `Map`, `WeakMap` is not iterable and has no `size` property.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. Which code correctly uses a `WeakMap` to store private data for class instances? 

```js
const _data = new WeakMap();

class Token {
  constructor(secret) {
    _data.set(this, { secret });
  }
  getSecret() {
    return _data.get(this).secret;
  }
}

const t = new Token("abc123");
console.log(t.getSecret());
console.log(t.secret);
```

- A) `"abc123"`, `"abc123"`
- B) `"abc123"`, `undefined`
- C) `undefined`, `undefined`
- D) `TypeError`

**Answer: B) `"abc123"`, `undefined`**

> The secret is stored in the `WeakMap` keyed by the instance (`this`), not on the instance itself. `getSecret()` retrieves it via the `WeakMap`, returning `"abc123"`. `t.secret` is `undefined` because it was never set as a public property, achieving true data privacy.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What will happen to a `WeakSet` entry when the referenced object is no longer reachable? 

```js
let obj = { id: 1 };
const ws = new WeakSet();
ws.add(obj);
console.log(ws.has(obj)); // true
obj = null; // original object now unreachable
// After garbage collection:
// ws.has(obj) would be false
```

- A) The `WeakSet` keeps a strong reference and prevents garbage collection
- B) The entry is automatically removed from the `WeakSet` when the object is garbage-collected
- C) Setting `obj = null` immediately removes the entry from the `WeakSet`
- D) `WeakSet` throws an error when the reference is set to `null`

**Answer: B) The entry is automatically removed from the `WeakSet` when the object is garbage-collected**

> `WeakSet` holds weak references to its objects. When the only remaining reference to an object is through a `WeakSet`, the garbage collector can reclaim it and the entry disappears from the `WeakSet`. The timing of removal is non-deterministic. This is why `WeakSet` is not iterable.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 27. PRIVATE CLASS FIELDS

<br>

## Q. What is the output of the following code using private class fields? 

```js
class BankAccount {
  #balance = 0;

  deposit(amount) {
    this.#balance += amount;
  }

  get balance() {
    return this.#balance;
  }
}

const acc = new BankAccount();
acc.deposit(100);
console.log(acc.balance);
console.log(acc.#balance);
```

- A) `100`, `100`
- B) `100`, `undefined`
- C) `100`, `SyntaxError`
- D) `undefined`, `SyntaxError`

**Answer: C) `100`, `SyntaxError`**

> Private class fields declared with `#` are truly private — they cannot be accessed outside the class body. `acc.balance` uses the getter, returning `100`. Accessing `acc.#balance` outside the class throws a `SyntaxError` (or `TypeError` depending on environment) because the syntax is not permitted outside the class.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the correct way to check if a private field exists on an object from inside the class? 

```js
class Node {
  #value;
  constructor(v) { this.#value = v; }

  static isNode(obj) {
    return #value in obj;
  }
}

console.log(Node.isNode(new Node(1)));
console.log(Node.isNode({}));
```

- A) `true`, `true`
- B) `true`, `false`
- C) `false`, `false`
- D) `SyntaxError`

**Answer: B) `true`, `false`**

> The `#field in obj` ergonomic brand check (ES2022) tests whether an object has the private field without throwing. Inside the class, `#value in obj` returns `true` for `Node` instances and `false` for plain objects that were not constructed by `Node`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. How do private class fields (`#`) differ from the underscore convention (`_`)? 

- A) Both are equally private; `#` is just newer syntax
- B) `_` prefixed properties are truly private; `#` properties are only private by convention
- C) `#` fields are enforced private by the JavaScript engine; `_` is only a naming convention with no access restriction
- D) `#` fields are only for static members

**Answer: C) `#` fields are enforced private by the JavaScript engine; `_` is only a naming convention with no access restriction**

> `#` private fields are a hard language feature — the JavaScript engine prevents access outside the class body. The `_` prefix is a community convention; any code can still read `obj._value` without restriction. Private fields also avoid name collision across subclasses since each class has its own private field namespace.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output involving a class getter and setter? 

```js
class Temperature {
  #celsius;
  constructor(c) { this.#celsius = c; }

  get fahrenheit() {
    return this.#celsius * 9/5 + 32;
  }

  set fahrenheit(f) {
    this.#celsius = (f - 32) * 5/9;
  }
}

const t = new Temperature(0);
console.log(t.fahrenheit);
t.fahrenheit = 212;
console.log(t.fahrenheit);
```

- A) `32`, `212`
- B) `0`, `100`
- C) `32`, `100`
- D) `32`, `32`

**Answer: A) `32`, `212`**

> At `0°C`, `fahrenheit` returns `0 * 9/5 + 32 = 32`. Setting `t.fahrenheit = 212` invokes the setter, which stores `(212 - 32) * 5/9 = 100` as the new `#celsius`. Reading `t.fahrenheit` again converts `100°C` back: `100 * 9/5 + 32 = 212`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 28. PROXY & REFLECT

<br>

## Q. What is the output of the following Proxy with a `get` trap? 

```js
const handler = {
  get(target, prop) {
    return prop in target ? target[prop] : `Property "${prop}" not found`;
  }
};

const obj = new Proxy({ name: "Alice" }, handler);
console.log(obj.name);
console.log(obj.age);
```

- A) `"Alice"`, `undefined`
- B) `"Alice"`, `"Property "age" not found"`
- C) `"Alice"`, `TypeError`
- D) `undefined`, `undefined`

**Answer: B) `"Alice"`, `"Property "age" not found"`**

> The `get` trap intercepts every property access on the proxy. When `prop` (`"name"`) exists on the target it returns the real value. When `prop` (`"age"`) is absent, it returns the custom not-found message instead of `undefined`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer uses a Proxy `set` trap to validate data. What will the following code do? 

```js
const validator = {
  set(target, prop, value) {
    if (prop === "age" && typeof value !== "number") {
      throw new TypeError("Age must be a number");
    }
    target[prop] = value;
    return true;
  }
};

const person = new Proxy({}, validator);
person.name = "Bob";
person.age = "thirty";
```

- A) Sets both `name` and `age` silently
- B) Sets `name` successfully, then throws `TypeError: Age must be a number`
- C) Throws `TypeError` immediately on `person.name = "Bob"`
- D) Proxy `set` traps cannot throw errors

**Answer: B) Sets `name` successfully, then throws `TypeError: Age must be a number`**

> The `set` trap intercepts all property assignments. Setting `name` passes validation and is stored. Setting `age` to a string fails the type check, causing the trap to throw `TypeError: Age must be a number`. This pattern is used to build runtime type-safe objects.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the role of `Reflect` in conjunction with a Proxy? 

- A) `Reflect` creates Proxy objects
- B) `Reflect` provides default implementations of all proxy trap operations, making it easy to forward behaviour to the target inside a custom trap
- C) `Reflect` is used to inspect proxy handlers
- D) `Reflect` methods are faster than normal property access

**Answer: B) `Reflect` provides default implementations of all proxy trap operations, making it easy to forward behaviour to the target inside a custom trap**

> `Reflect` has methods that mirror each Proxy trap (`Reflect.get`, `Reflect.set`, `Reflect.has`, etc.). Inside a trap, calling `Reflect.get(target, prop, receiver)` performs the default operation while still allowing custom logic before or after, without breaking prototype-chain lookups or `this` binding.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following Proxy with a `has` trap? 

```js
const range = new Proxy({ min: 1, max: 10 }, {
  has(target, prop) {
    const num = Number(prop);
    return num >= target.min && num <= target.max;
  }
});

console.log(5 in range);
console.log(15 in range);
```

- A) `true`, `true`
- B) `false`, `false`
- C) `true`, `false`
- D) `TypeError`

**Answer: C) `true`, `false`**

> The `has` trap intercepts the `in` operator. `5 in range` calls `has` with `prop = "5"`; `Number("5") = 5`, which is between `1` and `10`, so `true`. `15 in range` → `15 > 10`, so `false`. This pattern creates a virtual range object.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 29. ASYNC GENERATORS

<br>

## Q. What is an async generator function and what does it return? 

```js
async function* asyncRange(start, end) {
  for (let i = start; i <= end; i++) {
    await new Promise(res => setTimeout(res, 10));
    yield i;
  }
}
```

- A) It returns a regular array of Promises
- B) It returns an async iterator that yields Promises resolved from each `yield`
- C) It returns a single Promise that resolves with an array of all yielded values
- D) `SyntaxError` — `async` and `*` cannot be combined

**Answer: B) It returns an async iterator that yields Promises resolved from each `yield`**

> An `async function*` combines async/await with generators. It returns an **async iterator** whose `next()` method returns a Promise that resolves to `{ value, done }`. Each `yield` suspends execution and the `await` inside can pause for async operations between yields.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. How do you consume an async generator using `for await...of`? 

```js
async function* generate() {
  yield Promise.resolve(1);
  yield Promise.resolve(2);
  yield Promise.resolve(3);
}

async function run() {
  const results = [];
  for await (const val of generate()) {
    results.push(val);
  }
  console.log(results);
}
run();
```

- A) `[Promise, Promise, Promise]`
- B) `[1, 2, 3]`
- C) `[[1], [2], [3]]`
- D) `TypeError: generate() is not async iterable`

**Answer: B) `[1, 2, 3]`**

> `for await...of` automatically awaits each value produced by an async iterable. Although each `yield` produces a Promise, `for await` resolves it before assigning to `val`, so `results` contains the resolved values `[1, 2, 3]`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer needs to paginate through API results lazily without loading all pages upfront. Which ES6+ pattern is most suitable? 

- A) Fetch all pages with `Promise.all` and cache them
- B) Use an async generator that fetches the next page only when the iterator is advanced
- C) Use a regular generator with synchronous `fetch` calls
- D) Use `setTimeout` to delay each page request

**Answer: B) Use an async generator that fetches the next page only when the iterator is advanced**

> Async generators are ideal for lazy, on-demand asynchronous data streams. Each `yield` suspends the generator; the next value is only fetched when the consumer calls `next()` (or the `for await...of` loop advances). This avoids loading all pages into memory at once and gives the consumer control over pacing.

**Example:**

```js
// Simulated API call — returns one page of results
async function fetchPage(page) {
  // Replace with a real fetch, e.g. fetch(`/api/items?page=${page}`)
  const data = {
    1: { items: ["Alice", "Bob"], hasNext: true },
    2: { items: ["Charlie", "Diana"], hasNext: true },
    3: { items: ["Eve"], hasNext: false },
  };
  return data[page] ?? { items: [], hasNext: false };
}

// Async generator: fetches the next page only when the consumer asks for it
async function* paginate() {
  let page = 1;
  while (true) {
    const { items, hasNext } = await fetchPage(page);
    yield items; // pause here; next page is NOT fetched until consumer advances
    if (!hasNext) break;
    page++;
  }
}

// Consumer — stops early after finding a target, saving unnecessary API calls
async function findUser(target) {
  for await (const items of paginate()) {
    console.log("Fetched page with:", items);
    if (items.includes(target)) {
      console.log(`Found "${target}"!`);
      return; // generator is abandoned here — no further pages are fetched
    }
  }
  console.log(`"${target}" not found.`);
}

findUser("Charlie");

// Output:
// Fetched page with: ["Alice", "Bob"]
// Fetched page with: ["Charlie", "Diana"]
// Found "Charlie"!
```

**Why not the other options?**

| Option | Problem |
|--------|---------|
| `Promise.all` (A) | Fetches **all** pages upfront — wastes bandwidth and memory |
| Regular generator (C) | `fetch` is async; a synchronous generator can\'t `await` — yields `Promise` objects instead of resolved data |
| `setTimeout` (D) | Adds arbitrary delays with no control over when data is actually ready |

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following code mixing `yield*` with an async generator? 

```js
async function* inner() {
  yield 10;
  yield 20;
}

async function* outer() {
  yield 1;
  yield* inner();
  yield 2;
}

async function run() {
  const vals = [];
  for await (const v of outer()) vals.push(v);
  console.log(vals);
}
run();
```

- A) `[1, 2]`
- B) `[1, 10, 20, 2]`
- C) `[10, 20, 1, 2]`
- D) `[1, [10, 20], 2]`

**Answer: B) `[1, 10, 20, 2]`**

> `yield*` delegates to another iterable or async iterable inline. `outer` first yields `1`, then delegates to `inner` which yields `10` and `20`, then yields `2`. The consumer sees all values in order: `[1, 10, 20, 2]`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 30. CURRYING & PARTIAL APPLICATION

<br>

## Q. What is the output of the following curried function? 

```js
function curry(fn) {
  return function curried(...args) {
    if (args.length >= fn.length) {
      return fn(...args);
    }
    return function(...moreArgs) {
      return curried(...args, ...moreArgs);
    };
  };
}

const add = curry((a, b, c) => a + b + c);
console.log(add(1)(2)(3));
console.log(add(1, 2)(3));
console.log(add(1)(2, 3));
```

- A) `6`, `TypeError`, `TypeError`
- B) `6`, `6`, `6`
- C) `6`, `5`, `6`
- D) `TypeError` for all

**Answer: B) `6`, `6`, `6`**

> The `curry` helper checks whether the accumulated argument count meets the original function\'s arity (`fn.length`). If not, it returns another function collecting more arguments. All three call styles eventually pass three arguments to `(a, b, c) => a + b + c`, producing `6`. 

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is partial application and how does it differ from currying? 

```js
function multiply(a, b) { return a * b; }

// Partial application using bind
const double = multiply.bind(null, 2);
console.log(double(5));
console.log(double(10));
```

- A) `10`, `12`
- B) `10`, `20`
- C) `NaN`, `NaN`
- D) `TypeError`

**Answer: B) `10`, `20`**

> **Partial application** pre-fills one or more arguments of a function, returning a new function that accepts the remaining ones. `multiply.bind(null, 2)` creates `double`, which always multiplies by `2`. **Currying** transforms a function into a chain of unary functions; partial application applies some arguments immediately.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does the following memoization implementation output? 

```js
function memoize(fn) {
  const cache = new Map();
  return function(...args) {
    const key = JSON.stringify(args);
    if (cache.has(key)) {
      return cache.get(key);
    }
    const result = fn(...args);
    cache.set(key, result);
    return result;
  };
}

let callCount = 0;
const expensiveAdd = memoize((a, b) => {
  callCount++;
  return a + b;
});

console.log(expensiveAdd(2, 3));
console.log(expensiveAdd(2, 3));
console.log(expensiveAdd(4, 5));
console.log(callCount);
```

- A) `5`, `5`, `9`, `3`
- B) `5`, `5`, `9`, `2`
- C) `5`, `undefined`, `9`, `2`
- D) `TypeError`

**Answer: B) `5`, `5`, `9`, `2`**

> The memoized function caches results by a serialised argument key. The first `expensiveAdd(2, 3)` computes and caches the result. The second call with the same arguments returns the cached value without calling the original function. `expensiveAdd(4, 5)` is a new key so it computes again. The original function was called only **twice** (`callCount === 2`).

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is function composition and what does the following `compose` utility output? 

```js
const compose = (...fns) => x => fns.reduceRight((acc, fn) => fn(acc), x);

const double = x => x * 2;
const addOne = x => x + 1;
const square = x => x * x;

const transform = compose(double, addOne, square);
console.log(transform(3));
```

- A) `19`
- B) `20`
- C) `22`
- D) `18`

**Answer: B) `20`**

> `compose` applies functions **right-to-left** using `reduceRight`. Starting with `x = 3`: `square(3) = 9`, then `addOne(9) = 10`, then `double(10) = 20`. Note: `pipe` is the same concept but applies functions left-to-right.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 31. LOGICAL ASSIGNMENT OPERATORS

<br>

## Q. What is the output of the following logical assignment operators? 

```js
let a = null;
let b = 0;
let c = "hello";
let d = 1;

a ??= "default";
b ||= "fallback";
c &&= "world";
d &&= 0;

console.log(a, b, c, d);
```

- A) `"default"`, `"fallback"`, `"world"`, `0`
- B) `"default"`, `0`, `"world"`, `0`
- C) `null`, `0`, `"hello"`, `1`
- D) `"default"`, `"fallback"`, `"hello"`, `0`

**Answer: A) `"default"`, `"fallback"`, `"world"`, `0`**

> ES2021 logical assignment operators combine logic with assignment:
> - `??=` assigns only if the left side is `null` or `undefined` (`a = null` → assigned `"default"`)
> - `||=` assigns only if the left side is falsy (`b = 0` → assigned `"fallback"`)
> - `&&=` assigns only if the left side is truthy (`c = "hello"` → assigned `"world"`; `d = 1` → assigned `0`)
>

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What will the following `||=` operator do in a caching pattern? 

```js
const cache = {};

function getUser(id) {
  cache[id] ||= fetchUserFromDB(id);
  return cache[id];
}

function fetchUserFromDB(id) {
  console.log(`Fetching user ${id}`);
  return { id, name: `User${id}` };
}

getUser(1);
getUser(1);
getUser(2);
```

- A) Logs `Fetching user 1`, `Fetching user 1`, `Fetching user 2`
- B) Logs `Fetching user 1`, `Fetching user 2`
- C) Logs nothing — `||=` never triggers the right-hand side
- D) `TypeError` because object properties cannot use `||=`

**Answer: B) Logs `Fetching user 1`, `Fetching user 2`**

> `cache[id] ||= value` only evaluates and assigns the right-hand side if `cache[id]` is falsy (i.e., `undefined` the first time). On the second call for user `1`, `cache[1]` is already a truthy object, so `fetchUserFromDB` is not called.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. How does `??=` differ from `||=` when the existing value is `0` or `false`? 

```js
let score1 = 0;
let score2 = 0;

score1 ||= 100;
score2 ??= 100;

console.log(score1);
console.log(score2);
```

- A) `100`, `100`
- B) `0`, `0`
- C) `100`, `0`
- D) `0`, `100`

**Answer: C) `100`, `0`**

> `||=` assigns when the left side is **falsy** — `0` is falsy, so `score1` becomes `100`. `??=` assigns only when the left side is **nullish** (`null` or `undefined`) — `0` is not nullish, so `score2` stays `0`. This distinction prevents unintentional overwriting of valid `0` or `false` values.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 32. CUSTOM ERROR HANDLING

<br>

## Q. How do you create a custom error class in ES6? 

```js
class ValidationError extends Error {
  constructor(message, field) {
    super(message);
    this.name = "ValidationError";
    this.field = field;
  }
}

try {
  throw new ValidationError("Invalid email", "email");
} catch (e) {
  console.log(e instanceof ValidationError);
  console.log(e instanceof Error);
  console.log(e.name);
  console.log(e.field);
}
```

- A) `false`, `false`, `"Error"`, `undefined`
- B) `true`, `true`, `"ValidationError"`, `"email"`
- C) `true`, `false`, `"ValidationError"`, `"email"`
- D) `TypeError` — custom error classes are not allowed

**Answer: B) `true`, `true`, `"ValidationError"`, `"email"`**

> ES6 classes can extend `Error` to create custom error types. `super(message)` calls the `Error` constructor, setting `message` and `stack`. Overriding `this.name` ensures the error type shows correctly in stack traces. Because `ValidationError` extends `Error`, `instanceof Error` is also `true`. 

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the difference between re-throwing and swallowing an error in a `catch` block? 

```js
async function fetchData(url) {
  try {
    const res = await fetch(url);
    if (!res.ok) throw new Error(`HTTP ${res.status}`);
    return await res.json();
  } catch (e) {
    if (e instanceof TypeError) {
      // Network error — rethrow for caller to handle
      throw e;
    }
    // HTTP error — log and return null
    console.error("Request failed:", e.message);
    return null;
  }
}
```

- A) The `catch` block always swallows the error
- B) `TypeError` (network errors) are re-thrown; HTTP errors are handled locally and return `null`
- C) The function always returns `null` when an error occurs
- D) Re-throwing inside `async` functions converts the error to a resolved Promise

**Answer: B) `TypeError` (network errors) are re-thrown; HTTP errors are handled locally and return `null`**

> Selectively re-throwing errors is a best practice: handle only the errors you can recover from and propagate the rest. A `TypeError` from `fetch` (e.g., no network) is re-thrown so the caller can decide how to handle it. HTTP errors (`!res.ok`) are recoverable, logged, and result in `null`. Re-throwing inside an `async` function produces a rejected Promise, correctly propagating to the caller. 

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following error hierarchy? 

```js
class AppError extends Error {
  constructor(message, code) {
    super(message);
    this.name = "AppError";
    this.code = code;
  }
}

class NetworkError extends AppError {
  constructor(message) {
    super(message, "NETWORK_ERR");
    this.name = "NetworkError";
  }
}

const e = new NetworkError("Connection refused");
console.log(e instanceof NetworkError);
console.log(e instanceof AppError);
console.log(e instanceof Error);
console.log(e.code);
console.log(e.name);
```

- A) `true`, `false`, `false`, `undefined`, `"Error"`
- B) `true`, `true`, `true`, `"NETWORK_ERR"`, `"NetworkError"`
- C) `true`, `true`, `false`, `"NETWORK_ERR"`, `"AppError"`
- D) `false`, `true`, `true`, `"NETWORK_ERR"`, `"NetworkError"`

**Answer: B) `true`, `true`, `true`, `"NETWORK_ERR"`, `"NetworkError"`**

> The prototype chain is `NetworkError → AppError → Error`. So `instanceof` returns `true` for all three. `code` is set in `AppError`\'s constructor via `super(message, "NETWORK_ERR")`. `name` is set last in `NetworkError`\'s constructor, overriding the `"AppError"` name. 

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. How should `finally` behave when both `catch` and `finally` are present? 

```js
function riskyOperation() {
  try {
    throw new Error("oops");
  } catch (e) {
    console.log("caught:", e.message);
    return "from catch";
  } finally {
    console.log("finally runs");
  }
}

console.log(riskyOperation());
```

- A) `caught: oops`, then `"from catch"` (finally is skipped because catch returns)
- B) `caught: oops`, `finally runs`, then `"from catch"`
- C) `finally runs`, `caught: oops`, then `"from catch"`
- D) `caught: oops`, `finally runs`, then `undefined`

**Answer: B) `caught: oops`, `finally runs`, then `"from catch"`**

> `finally` always executes regardless of whether the `try` or `catch` block returns or throws. It runs **after** `catch` completes but **before** the return value is propagated to the caller. The `return "from catch"` value is still returned correctly unless `finally` itself contains a `return`, which would override it.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 33. NUMBER METHODS

<br>

## Q. What does `Number.isFinite()` return for the following values, and how does it differ from the global `isFinite()`? 

```js
console.log(Number.isFinite(42));
console.log(Number.isFinite(Infinity));
console.log(Number.isFinite("42"));
console.log(isFinite("42"));
```

- A) `true`, `false`, `false`, `false`
- B) `true`, `false`, `false`, `true`
- C) `true`, `false`, `true`, `true`
- D) `true`, `true`, `false`, `true`

**Answer: B) `true`, `false`, `false`, `true`**

> `Number.isFinite()` does **not** coerce its argument — it returns `false` for any non-number type, including the string `"42"`. The global `isFinite()` first coerces its argument (`Number("42")` → `42`), so it returns `true`. Prefer `Number.isFinite` for strict type-safe checks.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does `Number.parseInt` return, and is it identical to the global `parseInt`? 

```js
console.log(Number.parseInt === parseInt);
console.log(Number.parseInt("42px"));
console.log(Number.parseInt("0xFF", 16));
```

- A) `false`, `42`, `255`
- B) `true`, `42`, `255`
- C) `true`, `NaN`, `255`
- D) `false`, `NaN`, `NaN`

**Answer: B) `true`, `42`, `255`**

> `Number.parseInt` is the **same function** as the global `parseInt` (strict reference equality). It parses leading numeric characters and stops at the first non-numeric character. `"42px"` → `42`. `"0xFF"` in base 16 → `255`. The ES6 `Number.*` variants were added to consolidate global utilities onto the `Number` namespace.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the purpose of `Number.EPSILON`, and when should it be used? 

```js
console.log(0.1 + 0.2 === 0.3);
console.log(Math.abs((0.1 + 0.2) - 0.3) < Number.EPSILON);
```

- A) `true`, `true`
- B) `false`, `false`
- C) `false`, `true`
- D) `true`, `false`

**Answer: C) `false`, `true`**

> Floating-point arithmetic (IEEE 754) produces small rounding errors — `0.1 + 0.2` evaluates to `0.30000000000000004`. `Number.EPSILON` (≈ `2.22e-16`) represents the smallest representable difference between two numbers. Comparing the absolute difference to `Number.EPSILON` is the correct way to test floating-point equality.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does `Number.isInteger` return for the following values? 

```js
console.log(Number.isInteger(42));
console.log(Number.isInteger(42.0));
console.log(Number.isInteger(42.5));
console.log(Number.isInteger("42"));
```

- A) `true`, `false`, `false`, `true`
- B) `true`, `true`, `false`, `false`
- C) `true`, `true`, `false`, `true`
- D) `true`, `false`, `false`, `false`

**Answer: B) `true`, `true`, `false`, `false`**

> `Number.isInteger` returns `true` if the value is a finite number with no fractional part. In JavaScript, `42.0` is represented identically to `42` (both are the integer 42), so it returns `true`. `"42"` is a string — `Number.isInteger` does **not** coerce, so it returns `false`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following `BigInt` operations, and why does the regular number lose precision? 

```js
const big = 9007199254740993n;
const normal = 9007199254740993;

console.log(big === 9007199254740993n);
console.log(normal === 9007199254740993);
console.log(typeof big);
```

- A) `true`, `true`, `"number"`
- B) `true`, `false`, `"bigint"`
- C) `false`, `true`, `"bigint"`
- D) `true`, `true`, `"bigint"`

**Answer: B) `true`, `false`, `"bigint"`**

> `9007199254740993` exceeds `Number.MAX_SAFE_INTEGER` (`2^53 - 1 = 9007199254740991`), so JavaScript cannot represent it exactly as a float64 — it gets rounded to `9007199254740992`, making the `===` comparison `false`. `BigInt` literals (suffix `n`) preserve arbitrary precision. `typeof` a BigInt is `"bigint"`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does `Number.isSafeInteger` check, and what is the output? 

```js
console.log(Number.isSafeInteger(Number.MAX_SAFE_INTEGER));
console.log(Number.isSafeInteger(Number.MAX_SAFE_INTEGER + 1));
console.log(Number.isSafeInteger(3.14));
console.log(Number.MAX_SAFE_INTEGER);
```

- A) `true`, `true`, `false`, `9007199254740992`
- B) `true`, `false`, `false`, `9007199254740991`
- C) `true`, `true`, `true`, `9007199254740991`
- D) `false`, `false`, `false`, `9007199254740991`

**Answer: B) `true`, `false`, `false`, `9007199254740991`**

> `Number.isSafeInteger` returns `true` for integers in the range `[-(2^53 - 1), 2^53 - 1]` where they can be represented exactly without precision loss. `MAX_SAFE_INTEGER + 1` equals `2^53`, which exceeds the safe range — two different integers may produce the same float64 value. `3.14` is not an integer.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 34. REGULAR EXPRESSIONS (ES6+)

<br>

## Q. What does the `u` (Unicode) flag enable in ES6 RegExp? 

```js
const r1 = /\u{1F600}/;
const r2 = /\u{1F600}/u;
console.log(r1.test("😀"));
console.log(r2.test("😀"));
```

- A) `true`, `true`
- B) `false`, `true`
- C) `true`, `false`
- D) `false`, `false`

**Answer: B) `false`, `true`**

> Without the `u` flag, `\u{1F600}` is not interpreted as a Unicode code-point escape — the `{}` is treated as a quantifier, making the regex invalid or matching literally. With the `u` flag, `\u{HHHH}` syntax is enabled for code points beyond the Basic Multilingual Plane (> `U+FFFF`), correctly matching the emoji 😀 (U+1F600).

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does `String.prototype.matchAll` return compared to `match` with a global flag? 

```js
const text = "cat bat sat";
const regex = /[a-z]at/g;
const matches = [...text.matchAll(regex)];
console.log(matches.length);
console.log(matches[0][0]);
console.log(matches[0].index);
```

- A) `3`, `"cat"`, `0`
- B) `1`, `"cat"`, `0`
- C) `3`, `["cat", "bat", "sat"]`, `0`
- D) `TypeError — matchAll requires a sticky flag`

**Answer: A) `3`, `"cat"`, `0`**

> `matchAll` returns an iterator of all match result objects. Unlike `string.match(/regex/g)` which returns only the matched strings (losing capture group info), each `matchAll` result includes `index`, `input`, and named/unnamed capture groups. Here, three matches are found; the first is `"cat"` at index `0`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following code using ES2018 named capture groups?

```js
const dateStr = "2024-12-25";
const regex = /(?<year>\d{4})-(?<month>\d{2})-(?<day>\d{2})/;
const { groups } = dateStr.match(regex);
console.log(groups.year);
console.log(groups.month);
console.log(groups.day);
```

- A) `undefined`, `undefined`, `undefined`
- B) `"2024"`, `"12"`, `"25"`
- C) `2024`, `12`, `25` (as numbers)
- D) `TypeError`

**Answer: B) `"2024"`, `"12"`, `"25"`**

> ES2018 named capture groups (`(?<name>...)`) let you reference matched groups by name via the `groups` property of a match result. Captured values are always strings (not numbers), regardless of how they look. This is far more readable than referencing positional groups like `match[1]`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does the `s` (dotAll) flag enable, and what is the output? 

```js
const multiline = "Hello\nWorld";
console.log(/Hello.World/.test(multiline));
console.log(/Hello.World/s.test(multiline));
```

- A) `true`, `true`
- B) `false`, `true`
- C) `true`, `false`
- D) `false`, `false`

**Answer: B) `false`, `true`**

> By default, `.` in a regex does not match line terminators (`\n`, `\r`, `\u2028`, `\u2029`). The `s` (dotAll) flag makes `.` match **any** character including newlines. Without `s`, `Hello.World` does not match `"Hello\nWorld"`. With `s`, it does.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does the following regex with a lookbehind assertion match? 

```js
const prices = "€100 $200 £300";
const regex = /(?<=\$)\d+/g;
const matches = prices.match(regex);
console.log(matches);
```

- A) `["100", "200", "300"]`
- B) `["200"]`
- C) `["$200"]`
- D) `null`

**Answer: B) `["200"]`**

> ES2018 lookbehind assertions `(?<=...)` match a position preceded by a specific pattern without including that pattern in the match. `(?<=\$)\d+` matches digits that are immediately preceded by `$`. Only `200` qualifies. The `€` and `£` prefixed numbers are not matched.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. How does the `y` (sticky) flag differ from the `g` (global) flag? 

```js
const str = "aababc";
const globalRegex = /a/g;
const stickyRegex = /a/y;

globalRegex.exec(str);  // finds 'a' at index 0
stickyRegex.exec(str);  // finds 'a' at index 0

globalRegex.exec(str);  // next exec
stickyRegex.exec(str);  // next exec — lastIndex is now 1

console.log(globalRegex.lastIndex);
console.log(stickyRegex.lastIndex);
```

- A) `1`, `1`
- B) `2`, `0`
- C) `2`, `2`
- D) `1`, `0`

**Answer: C) `2`, `2`**

> Both `g` and `y` flags maintain `lastIndex` between `exec` calls. The difference is that `y` (sticky) only matches at exactly `lastIndex` (not later in the string), whereas `g` searches forward from `lastIndex`. After two `exec` calls that both match `a`, `lastIndex` advances to `2` for both.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 35. FUNCTIONAL PROGRAMMING

<br>

## Q. What is the output of the following function pipeline using `pipe`? 

```js
const pipe = (...fns) => x => fns.reduce((acc, fn) => fn(acc), x);

const process = pipe(
  x => x * 2,
  x => x + 3,
  x => x ** 2
);

console.log(process(4));
```

- A) `25`
- B) `121`
- C) `169`
- D) `38`

**Answer: B) `121`**

> `pipe` applies functions **left-to-right** using `reduce`. Starting with `x = 4`: `4 * 2 = 8`, then `8 + 3 = 11`, then `11 ** 2 = 121`. This contrasts with `compose` which applies functions right-to-left.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. Which approach most efficiently converts an array of user objects to a `Map` keyed by `id`? 

```js
const users = [
  { id: 1, name: "Alice" },
  { id: 2, name: "Bob" },
  { id: 3, name: "Carol" }
];
```

- A) `users.reduce((map, u) => ({ ...map, [u.id]: u }), {})`
- B) `new Map(users.map(u => [u.id, u]))`
- C) `Object.fromEntries(users)`
- D) `users.forEach(u => new Map().set(u.id, u))`

**Answer: B) `new Map(users.map(u => [u.id, u]))`**

> `Map` constructor accepts an iterable of `[key, value]` pairs. `users.map(u => [u.id, u])` produces the required pairs in O(n). Option A creates a plain object (not a `Map`) and rebuilds the accumulator each iteration — O(n²) due to object spread. Option D creates a new discarded `Map` per iteration. `Object.fromEntries` creates a plain object, not a `Map`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does the following `reduce`-based `groupBy` implementation output? 

```js
const items = [
  { type: "fruit", name: "apple" },
  { type: "veggie", name: "carrot" },
  { type: "fruit", name: "banana" },
  { type: "veggie", name: "broccoli" }
];

const grouped = items.reduce((acc, item) => {
  acc[item.type] = acc[item.type] || [];
  acc[item.type].push(item.name);
  return acc;
}, {});

console.log(grouped.fruit);
console.log(grouped.veggie.length);
```

- A) `["apple", "banana"]`, `3`
- B) `["apple", "banana"]`, `2`
- C) `["apple"]`, `1`
- D) `undefined`, `0`

**Answer: B) `["apple", "banana"]`, `2`**

> `reduce` accumulates items into groups using their `type` as the key. `fruit` gets `"apple"` and `"banana"`. `veggie` gets `"carrot"` and `"broccoli"` — length `2`. This is the classic groupBy pattern, equivalent to `Object.groupBy` (ES2024) for environments that support it.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does the following point-free curried transformation output? 

```js
const multiply = a => b => a * b;
const add = a => b => a + b;

const result = [1, 2, 3, 4, 5]
  .map(multiply(3))
  .map(add(1));

console.log(result);
```

- A) `[4, 7, 10, 13, 16]`
- B) `[3, 6, 9, 12, 15]`
- C) `[2, 3, 4, 5, 6]`
- D) `TypeError`

**Answer: A) `[4, 7, 10, 13, 16]`**

> `multiply(3)` returns `b => 3 * b`. Mapping `[1,2,3,4,5]` produces `[3, 6, 9, 12, 15]`. Then `add(1)` returns `b => 1 + b`, giving `[4, 7, 10, 13, 16]`. This point-free style passes partially-applied functions directly to higher-order array methods.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following filter-map-reduce chain? 

```js
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const result = numbers
  .filter(n => n % 2 === 0)
  .map(n => n * n)
  .reduce((sum, n) => sum + n, 0);
console.log(result);
```

- A) `110`
- B) `220`
- C) `55`
- D) `130`

**Answer: B) `220`**

> `filter` keeps even numbers: `[2, 4, 6, 8, 10]`. `map` squares each: `[4, 16, 36, 64, 100]`. `reduce` sums them: `4 + 16 + 36 + 64 + 100 = 220`. This chain is a common functional programming pattern for data transformation pipelines.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does the following `once` higher-order function output?

```js
function once(fn) {
  let called = false;
  let result;
  return function(...args) {
    if (!called) {
      called = true;
      result = fn(...args);
    }
    return result;
  };
}

const initDB = once(config => `DB connected to ${config.host}`);
console.log(initDB({ host: "localhost" }));
console.log(initDB({ host: "production" }));
console.log(initDB({ host: "staging" }));
```

- A) Three different connection strings
- B) `"DB connected to localhost"` three times
- C) `"DB connected to localhost"`, then `undefined` twice
- D) `TypeError`

**Answer: B) `"DB connected to localhost"` three times**

> `once` wraps a function so it executes **only on the first call**. Subsequent calls return the cached `result` without invoking `fn` again. All three calls return `"DB connected to localhost"`. This is a common utility in functional programming to prevent side effects from repeating.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 36. PROPERTY DESCRIPTORS

<br>

## Q. What is the output of the following `Object.defineProperty` call? 

```js
const obj = {};
Object.defineProperty(obj, "PI", {
  value: 3.14159,
  writable: false,
  enumerable: true,
  configurable: false
});

obj.PI = 99;
console.log(obj.PI);
console.log(Object.keys(obj));
```

- A) `99`, `["PI"]`
- B) `3.14159`, `[]`
- C) `3.14159`, `["PI"]`
- D) `TypeError` is thrown on `obj.PI = 99`

**Answer: C) `3.14159`, `["PI"]`**

> `writable: false` prevents the value from being changed — the assignment `obj.PI = 99` silently fails in sloppy mode (throws `TypeError` in strict mode). `enumerable: true` means the property appears in `Object.keys()` and `for...in`. The original value `3.14159` is preserved.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does `Object.getOwnPropertyDescriptor` reveal about an array\'s `length` property? 

```js
const arr = [1, 2, 3];
const desc = Object.getOwnPropertyDescriptor(arr, "length");
console.log(desc);
```

- A) `{ value: 3, writable: true, enumerable: true, configurable: true }`
- B) `{ value: 3, writable: true, enumerable: false, configurable: false }`
- C) `{ value: 3, writable: false, enumerable: false, configurable: false }`
- D) `undefined`

**Answer: B) `{ value: 3, writable: true, enumerable: false, configurable: false }`**

> The `length` property of an array is `writable: true` (you can set it to truncate/extend the array), `enumerable: false` (it doesn\'t appear in `for...in` or `Object.keys`), and `configurable: false` (it cannot be deleted or have its descriptor changed). This is a built-in engine-level property definition.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer wants to create a read-only property that still appears in `for...in`. Which descriptor combination is correct? 

- A) `{ writable: false, enumerable: true, configurable: false }`
- B) `{ writable: false, enumerable: false, configurable: true }`
- C) `{ writable: true, enumerable: true, configurable: false }`
- D) `{ writable: true, enumerable: false, configurable: false }`

**Answer: A) `{ writable: false, enumerable: true, configurable: false }`**

> `writable: false` prevents value changes. `enumerable: true` makes the property visible in `for...in` and `Object.keys()`. `configurable: false` prevents the property from being deleted or having its descriptor changed. This combination creates a read-only but enumerable property.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What happens when a property descriptor specifies both `value` and `get`? 

```js
const obj = {};
Object.defineProperty(obj, "name", {
  value: "Alice",
  get() { return "Bob"; }
});
```

- A) `get` overrides `value` — `obj.name` returns `"Bob"`
- B) `TypeError: Invalid property descriptor. Cannot both specify accessors and a value or writable attribute`
- C) Both are set; `get` takes precedence when reading
- D) `value` is set and `get` is silently ignored

**Answer: B) `TypeError: Invalid property descriptor. Cannot both specify accessors and a value or writable attribute`**

> A property descriptor is either a **data descriptor** (`value`, `writable`) or an **accessor descriptor** (`get`, `set`). Specifying both types in the same call is invalid and throws a `TypeError`. You must choose one form.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following code using `Object.defineProperties`? 

```js
const circle = { radius: 5 };

Object.defineProperties(circle, {
  area: {
    get() { return Math.PI * this.radius ** 2; },
    enumerable: true
  },
  diameter: {
    get() { return this.radius * 2; },
    enumerable: true
  }
});

console.log(circle.diameter);
console.log(circle.area.toFixed(2));
console.log(Object.keys(circle));
```

- A) `10`, `"78.54"`, `["radius"]`
- B) `10`, `"78.54"`, `["radius", "area", "diameter"]`
- C) `undefined`, `NaN`, `["radius"]`
- D) `10`, `"78.54"`, `["area", "diameter"]`

**Answer: B) `10`, `"78.54"`, `["radius", "area", "diameter"]`**

> `Object.defineProperties` adds computed getter properties in bulk. Both `area` and `diameter` are `enumerable: true`, so they appear in `Object.keys()`. The `area` getter uses `Math.PI * 5^2 ≈ 78.5398`, formatted to `"78.54"`. `diameter` returns `5 * 2 = 10`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. How does `configurable: false` affect the ability to later change a property descriptor? 

```js
const obj = {};
Object.defineProperty(obj, "x", { value: 1, configurable: false, writable: true });

// Attempt to reconfigure
try {
  Object.defineProperty(obj, "x", { enumerable: true });
} catch (e) {
  console.log(e instanceof TypeError);
}

// However, changing writable from true to false IS allowed
Object.defineProperty(obj, "x", { writable: false });
console.log(Object.getOwnPropertyDescriptor(obj, "x").writable);
```

- A) `false`, `true`
- B) `true`, `false`
- C) `true`, `true`
- D) `false`, `false`

**Answer: B) `true`, `false`**

> When `configurable: false`, most descriptor changes throw a `TypeError`. However, there is one allowed change: `writable` can be changed from `true` to `false` (a one-way tightening of restrictions) but not from `false` to `true`. Changing `enumerable` on a non-configurable property always throws.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 37. ARRAY ALGORITHM PROBLEMS

<br>

## Q. Which is the most concise ES6 way to remove duplicates from an array?

```js
const nums = [1, 2, 2, 3, 4, 4, 5];
```

- A) `nums.filter((v, i) => nums.indexOf(v) === i)`
- B) `[...new Set(nums)]`
- C) `Array.from(new Set(nums))`
- D) Both B and C are correct

**Answer: D) Both B and C are correct**

> A `Set` automatically discards duplicate values. Passing `nums` to `new Set()` gives `Set {1,2,3,4,5}`. Both `[...new Set(nums)]` (spread) and `Array.from(new Set(nums))` convert it back to an array. Option A also works but is O(n²). Options B and C are semantically equivalent and idiomatic ES6.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does the following code output when finding the range of an array? 

```js
const arr = [3, 1, 4, 1, 5, 9, 2, 6];
const max = Math.max(...arr);
const min = Math.min(...arr);
console.log(max - min);
```

- A) `6`
- B) `8`
- C) `3`
- D) `9`

**Answer: B) `8`**

> `Math.max(...arr)` spreads the array as individual arguments, returning `9`. `Math.min(...arr)` returns `1`. `9 - 1 = 8`. This spread-into-Math pattern is cleaner than `arr.reduce((a,b) => Math.max(a,b))` for small arrays.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer wants to chunk an array into groups of size `n`. What is the output? 

```js
function chunk(arr, size) {
  return Array.from(
    { length: Math.ceil(arr.length / size) },
    (_, i) => arr.slice(i * size, i * size + size)
  );
}

console.log(chunk([1, 2, 3, 4, 5], 2));
```

- A) `[[1, 2], [3, 4], [5]]`
- B) `[[1, 2, 3], [4, 5]]`
- C) `[[1], [2], [3], [4], [5]]`
- D) `[[1, 2], [3, 4]]`

**Answer: A) `[[1, 2], [3, 4], [5]]`**

> `Array.from({ length: 3 }, mapFn)` creates a 3-element array. Each element is sliced from the source: indices `[0,2]` → `[1,2]`, `[2,4]` → `[3,4]`, `[4,6]` → `[5]`. The last chunk may be shorter than `size` when the array length is not evenly divisible.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does the following frequency counter using `Map` output? 

```js
function frequencyCounter(arr) {
  return arr.reduce((map, val) => {
    map.set(val, (map.get(val) ?? 0) + 1);
    return map;
  }, new Map());
}

const freq = frequencyCounter([1, 2, 2, 3, 3, 3]);
console.log(freq.get(1));
console.log(freq.get(3));
console.log(freq.size);
```

- A) `1`, `3`, `6`
- B) `1`, `3`, `3`
- C) `1`, `2`, `3`
- D) `undefined`, `3`, `3`

**Answer: B) `1`, `3`, `3`**

> `reduce` builds a `Map` where each key is an array value and each map-value is its count. `??` ensures a missing key defaults to `0`. `1` appears once, `3` appears three times. The `Map` has 3 unique keys (`1`, `2`, `3`), so `size` is `3`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does the following matrix flatten and sort produce?

```js
const matrix = [[3, 1], [4, 1], [5, 9, 2]];
const flat = matrix.flat().sort((a, b) => a - b);
console.log(flat);
```

- A) `[[1, 3], [1, 4], [2, 5, 9]]`
- B) `[1, 1, 2, 3, 4, 5, 9]`
- C) `[3, 1, 4, 1, 5, 9, 2]`
- D) `[1, 2, 3, 4, 5, 9, 1]`

**Answer: B) `[1, 1, 2, 3, 4, 5, 9]`**

> `flat()` with default depth `1` flattens the nested arrays into `[3, 1, 4, 1, 5, 9, 2]`. The numeric comparator `(a, b) => a - b` in `.sort()` ensures ascending numeric order (without it, sort would compare as strings), producing `[1, 1, 2, 3, 4, 5, 9]`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does the following sliding-window maximum subarray sum return?

```js
function maxSumSubarray(arr, k) {
  let maxSum = arr.slice(0, k).reduce((a, b) => a + b, 0);
  let windowSum = maxSum;
  for (let i = k; i < arr.length; i++) {
    windowSum = windowSum - arr[i - k] + arr[i];
    maxSum = Math.max(maxSum, windowSum);
  }
  return maxSum;
}

console.log(maxSumSubarray([2, 1, 5, 1, 3, 2], 3));
```

- A) `7`
- B) `8`
- C) `9`
- D) `6`

**Answer: C) `9`**

> Initial window `[2,1,5]` = `8`. Slide: `[1,5,1]` = `7`, `[5,1,3]` = `9`, `[1,3,2]` = `6`. Maximum is `9`. The sliding window technique avoids O(n×k) recomputation by subtracting the outgoing element and adding the incoming one — O(n) overall.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does the following two-sum solution using a `Map` return? 

```js
function twoSum(nums, target) {
  const seen = new Map();
  for (let i = 0; i < nums.length; i++) {
    const complement = target - nums[i];
    if (seen.has(complement)) {
      return [seen.get(complement), i];
    }
    seen.set(nums[i], i);
  }
  return null;
}

console.log(twoSum([2, 7, 11, 15], 9));
console.log(twoSum([3, 2, 4], 6));
```

- A) `[0, 1]`, `[1, 2]`
- B) `[1, 0]`, `[2, 1]`
- C) `[2, 7]`, `[2, 4]`
- D) `null`, `null`

**Answer: A) `[0, 1]`, `[1, 2]`**

> For `[2,7,11,15]` target `9`: at `i=0`, `complement = 7`, not in `seen`; at `i=1`, `complement = 2`, found at index `0` → returns `[0, 1]`. For `[3,2,4]` target `6`: at `i=2`, `complement = 2`, found at index `1` → returns `[1, 2]`. The `Map` lookup makes this O(n) instead of O(n²).

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 38. STRING ALGORITHM PROBLEMS

<br>

## Q. What is the output of the following palindrome checker? 

```js
const isPalindrome = str => str === [...str].reverse().join("");
console.log(isPalindrome("racecar"));
console.log(isPalindrome("hello"));
```

- A) `false`, `false`
- B) `true`, `false`
- C) `true`, `true`
- D) `TypeError`

**Answer: B) `true`, `false`**

> Spreading a string `[...str]` splits it by Unicode character (safely handling emoji and multi-byte characters, unlike `str.split("")`). `.reverse()` reverses in place and `.join("")` re-joins. Comparing with the original detects palindromes. `"racecar"` reversed is `"racecar"` — `true`. `"hello"` reversed is `"olleh"` — `false`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following anagram checker? 

```js
function isAnagram(a, b) {
  const normalize = str => str.toLowerCase().split("").sort().join("");
  return normalize(a) === normalize(b);
}

console.log(isAnagram("listen", "silent"));
console.log(isAnagram("hello", "world"));
```

- A) `false`, `false`
- B) `true`, `true`
- C) `true`, `false`
- D) `false`, `true`

**Answer: C) `true`, `false`**

> Normalizing by lowercasing, sorting characters, and rejoining produces a canonical form. Two strings are anagrams if and only if their normalized forms are identical. `"listen"` sorted → `"eilnst"`, `"silent"` sorted → `"eilnst"` — equal. `"hello"` and `"world"` have different character sets — not equal.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does the following title-case function output? 

```js
const titleCase = str => str.replace(/\b\w/g, c => c.toUpperCase());
console.log(titleCase("the quick brown fox"));
```

- A) `"THE QUICK BROWN FOX"`
- B) `"The Quick Brown Fox"`
- C) `"the Quick Brown Fox"`
- D) `"the quick brown fox"`

**Answer: B) `"The Quick Brown Fox"`**

> The regex `/\b\w/g` matches the first word character (`\w`) after a word boundary (`\b`). The replacement callback converts each matched character to uppercase, capitalizing only the first letter of each word while leaving the rest unchanged.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following vowel counter? 

```js
const countVowels = str => (str.match(/[aeiou]/gi) || []).length;
console.log(countVowels("Hello World"));
console.log(countVowels("rhythm"));
```

- A) `3`, `1`
- B) `3`, `0`
- C) `2`, `0`
- D) `5`, `1`

**Answer: B) `3`, `0`**

> The regex `/[aeiou]/gi` matches all vowels case-insensitively. `"Hello World"` contains `e`, `o`, `o` — 3 vowels. `"rhythm"` has no vowels; `match` returns `null` which is handled by the `|| []` fallback, preventing a `TypeError` on `.length`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does the following Caesar cipher return?

```js
function caesarCipher(str, shift) {
  return str.replace(/[a-z]/gi, ch => {
    const base = ch >= "a" ? 97 : 65;
    return String.fromCharCode(((ch.charCodeAt(0) - base + shift) % 26) + base);
  });
}

console.log(caesarCipher("Hello", 3));
```

- A) `"Khoor"`
- B) `"Ifmmp"`
- C) `"Hello"`
- D) `"Ebiil"`

**Answer: A) `"Khoor"`**

> Each letter is shifted forward by 3 with modular wrapping. `H`(72) → `K`(75), `e`(101) → `h`(104), `l`(108) → `o`(111), `l` → `o`, `o`(111) → `r`(114). Result: `"Khoor"`. The `% 26` wraps the shift so `z + 1 = a`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following run-length encoding function? 

```js
function runLengthEncode(str) {
  return str.replace(/(.)\1*/g, (match, char) =>
    (match.length > 1 ? match.length : "") + char
  );
}

console.log(runLengthEncode("aaabbbccddddee"));
console.log(runLengthEncode("abcd"));
```

- A) `"3a3b2c4d2e"`, `"abcd"`
- B) `"3a3b2c4d2e"`, `"1a1b1c1d"`
- C) `"aaabbbccddddee"`, `"abcd"`
- D) `TypeError`

**Answer: A) `"3a3b2c4d2e"`, `"abcd"`**

> The regex `(.)\1*` matches a character followed by zero or more of the same character. For counts > 1, the count is prepended. For single characters, no count prefix is added. `"aaabbbccddddee"` → `"3a3b2c4d2e"`. For `"abcd"`, every character appears once, so the result remains `"abcd"`.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What does the following function that finds the most frequent character return? 

```js
function mostFrequent(str) {
  const freq = [...str].reduce((map, ch) => {
    map.set(ch, (map.get(ch) ?? 0) + 1);
    return map;
  }, new Map());
  return [...freq.entries()].reduce((max, [ch, count]) =>
    count > max[1] ? [ch, count] : max
  )[0];
}

console.log(mostFrequent("aabbbcc"));
```

- A) `"a"`
- B) `"b"`
- C) `"c"`
- D) `undefined`

**Answer: B) `"b"`**

> The function builds a frequency `Map`, then reduces over its entries to find the character with the highest count. `"a"` → 2, `"b"` → 3, `"c"` → 2. `"b"` has the highest frequency and is returned.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 39. OBJECT PATTERNS & IMMUTABILITY

<br>

## Q. Which technique creates a **deep** immutable object in ES6? 

```js
const config = {
  db: { host: "localhost", port: 5432 },
  server: { port: 3000 }
};
```

- A) `Object.freeze(config)`
- B) `Object.seal(config)`
- C) `const frozen = JSON.parse(JSON.stringify(config)); Object.freeze(frozen);`
- D) Recursively call `Object.freeze` on all nested objects

**Answer: D) Recursively call `Object.freeze` on all nested objects**

> `Object.freeze` is **shallow** — it freezes only own, direct properties. Nested objects (`config.db`, `config.server`) remain mutable. Option C creates a deep copy but then only shallow-freezes it. True deep immutability requires a recursive freeze traversal over all nested objects.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following Redux-style immutable state update? 

```js
const state = {
  user: { name: "Alice", age: 30 },
  settings: { theme: "dark" }
};

const newState = {
  ...state,
  user: { ...state.user, age: 31 }
};

console.log(state.user.age);
console.log(newState.user.age);
console.log(state.settings === newState.settings);
```

- A) `30`, `31`, `false`
- B) `30`, `31`, `true`
- C) `31`, `31`, `true`
- D) `30`, `30`, `false`

**Answer: B) `30`, `31`, `true`**

> `...state` shallow-copies top-level references. `user` is replaced with a new spread object `{ ...state.user, age: 31 }`, leaving `state.user` untouched. `settings` is not overridden — both `state.settings` and `newState.settings` reference the **same** object (`=== true`). This is the structural sharing pattern used in immutable state management.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following frozen object mutation in strict mode? 

```js
"use strict";
const point = Object.freeze({ x: 1, y: 2 });
try {
  point.x = 10;
} catch (e) {
  console.log(e instanceof TypeError);
}
console.log(point.x);
```

- A) `false`, `10`
- B) `true`, `1`
- C) `false`, `1`
- D) `true`, `10`

**Answer: B) `true`, `1`**

> In strict mode, mutating a frozen object throws a `TypeError`. The `catch` block logs `true`. The original value `1` is preserved because the write was rejected. In sloppy (non-strict) mode, the write would silently fail, also preserving `1`, but without throwing.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. How does `Object.seal()` differ from `Object.freeze()` regarding existing property values? 

```js
const obj = Object.seal({ name: "Alice", score: 100 });
obj.name = "Bob";     // modify existing
obj.email = "a@b.com"; // add new
delete obj.score;      // delete
console.log(obj);
```

- A) `{ name: "Bob", score: 100, email: "a@b.com" }`
- B) `{ name: "Bob", score: 100 }`
- C) `{ name: "Alice", score: 100 }`
- D) `TypeError` is thrown

**Answer: B) `{ name: "Bob", score: 100 }`**

> `Object.seal` marks all existing properties as `configurable: false`, preventing property addition and deletion, but **existing property values remain writable**. `obj.name = "Bob"` succeeds. `obj.email = ...` and `delete obj.score` silently fail (or throw in strict mode). `Object.freeze` additionally makes values non-writable.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following builder pattern using ES6?

```js
class QueryBuilder {
  #table = "";
  #conditions = [];
  #limit = null;

  from(table) { this.#table = table; return this; }
  where(condition) { this.#conditions.push(condition); return this; }
  limitTo(n) { this.#limit = n; return this; }

  build() {
    let query = `SELECT * FROM ${this.#table}`;
    if (this.#conditions.length) query += ` WHERE ${this.#conditions.join(" AND ")}`;
    if (this.#limit !== null) query += ` LIMIT ${this.#limit}`;
    return query;
  }
}

const query = new QueryBuilder()
  .from("users")
  .where("age > 18")
  .where("active = true")
  .limitTo(10)
  .build();

console.log(query);
```

- A) `"SELECT * FROM users"`
- B) `"SELECT * FROM users WHERE age > 18 AND active = true LIMIT 10"`
- C) `TypeError — chaining is not valid`
- D) `"SELECT * FROM users LIMIT 10"`

**Answer: B) `"SELECT * FROM users WHERE age > 18 AND active = true LIMIT 10"`**

> Each method returns `this`, enabling **method chaining** (the fluent interface / builder pattern). Private fields (`#`) encapsulate internal state. The `build()` method assembles all parts into a final SQL string. This pattern is common in query builders, configuration objects, and test builders.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following observable-like pattern using a `Proxy`? 

```js
function makeReactive(obj, onChange) {
  return new Proxy(obj, {
    set(target, prop, value) {
      const old = target[prop];
      target[prop] = value;
      if (old !== value) onChange(prop, old, value);
      return true;
    }
  });
}

const state = makeReactive({ count: 0 }, (key, oldVal, newVal) => {
  console.log(`${key}: ${oldVal} → ${newVal}`);
});

state.count = 1;
state.count = 1;
state.count = 2;
```

- A) Three logs: `count: 0 → 1`, `count: 1 → 1`, `count: 1 → 2`
- B) Two logs: `count: 0 → 1`, `count: 1 → 2`
- C) One log: `count: 0 → 2`
- D) `TypeError`

**Answer: B) Two logs: `count: 0 → 1`, `count: 1 → 2`**

> The `set` trap only calls `onChange` when `old !== value`. Setting `count` to `1` when it is already `1` is a no-op — no log. This mirrors how Vue 3\'s reactivity system avoids unnecessary re-renders when a value is set to the same value it already holds.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## # 40. PERFORMANCE & BEST PRACTICES

<br>

## Q. Which approach is more memory-efficient for processing a large dataset without loading everything into memory at once? 

- A) `const all = data.map(transform).filter(pred); all.forEach(process);`
- B) Use a generator that yields one item at a time
- C) `data.reduce(...)` with accumulation in a large array
- D) `Promise.all(data.map(async item => heavyProcess(item)))`

**Answer: B) Use a generator that yields one item at a time**

> Generators are **lazy** — they produce one value per `next()` call without materialising the entire collection in memory. Option A creates multiple intermediate arrays (O(n) memory per step). Option D fires all async tasks simultaneously which may exhaust resources. Generators are ideal for large datasets, infinite sequences, or when only a partial result is consumed.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. `Array.prototype.forEach` cannot be stopped early. Which method should be used to find the first match and stop iterating? 

```js
const numbers = [1, 2, 3, 4, 5, 100, 6, 7];
// Find first number > 10
```

- A) `numbers.forEach(n => { if (n > 10) return n; })`
- B) `numbers.find(n => n > 10)`
- C) `numbers.filter(n => n > 10)[0]`
- D) `numbers.reduce((found, n) => found || (n > 10 ? n : null), null)`

**Answer: B) `numbers.find(n => n > 10)`**

> `Array.prototype.find` returns the first element matching the predicate and **stops iterating** immediately. `forEach` cannot be short-circuited by returning. `filter` iterates the entire array. `find` is both semantically correct and more efficient for finding the first match in O(n) worst case with early termination.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following code that demonstrates lazy generator evaluation? 

```js
function* lazyRange(start, end) {
  for (let i = start; i <= end; i++) {
    console.log(`generating ${i}`);
    yield i;
  }
}

const gen = lazyRange(1, 5);
console.log("before first next");
const first = gen.next().value;
console.log("first value:", first);
```

- A) Generates all 5 values first, then `"before first next"`, then `"first value: 1"`
- B) `"before first next"`, then `"generating 1"`, then `"first value: 1"`
- C) `"before first next"`, then all 5 `"generating"` logs, then `"first value: 1"`
- D) `"generating 1"`, then `"before first next"`, then `"first value: 1"`

**Answer: B) `"before first next"`, then `"generating 1"`, then `"first value: 1"`**

> Generators are **lazy** — calling `lazyRange(1, 5)` does not execute the function body at all. Execution only begins when `gen.next()` is called, running until the first `yield`. Values 2–5 are not generated until subsequent `next()` calls. This contrasts with eager evaluation (e.g., `Array.from({length:5},...)`), which generates all values upfront.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the issue with the following sequential `await` pattern for independent operations? 

```js
async function loadDashboard() {
  const user = await fetchUser();       // 300ms
  const posts = await fetchPosts();     // 400ms
  const stats = await fetchStats();     // 200ms
  return { user, posts, stats };
}
```

- A) `async/await` cannot be used with multiple `await` expressions
- B) The three fetches run sequentially (total ≈ 900ms) even though they are independent — they should run concurrently
- C) The function will throw if any fetch rejects
- D) `async` functions cannot return objects

**Answer: B) The three fetches run sequentially (total ≈ 900ms) even though they are independent — they should run concurrently**

> Each `await` suspends execution until the previous Promise settles, making independent operations needlessly sequential. The fix is `const [user, posts, stats] = await Promise.all([fetchUser(), fetchPosts(), fetchStats()])`, which runs all three concurrently and completes in ≈ 400ms (the slowest).

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output of the following code demonstrating `WeakRef` for cache management? 

```js
let obj = { data: "important" };
const ref = new WeakRef(obj);

console.log(ref.deref()?.data);  // Before GC
obj = null;
// After GC (assuming GC has run):
// ref.deref() may return undefined
console.log(typeof ref.deref());
```

- A) `"important"`, `"undefined"` (always)
- B) `"important"`, `"object"` (always, GC hasn\'t run)
- C) `"important"`, either `"object"` or `"undefined"` (non-deterministic, depends on GC)
- D) `TypeError` — `WeakRef` is not valid ES6

**Answer: C) `"important"`, either `"object"` or `"undefined"` (non-deterministic, depends on GC)**

> `WeakRef` holds a weak reference to an object, allowing GC to reclaim it when no strong references remain. After `obj = null`, the object *may* be collected. `deref()` returns the object if it is still alive, or `undefined` if it was collected. GC timing is non-deterministic — never rely on `WeakRef` for critical logic, only for caches and registries.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. A developer profiles two approaches for building a large string. Which is more efficient and why? 

```js
// Approach A
let strA = "";
for (let i = 0; i < 10000; i++) strA += "x";

// Approach B
const parts = [];
for (let i = 0; i < 10000; i++) parts.push("x");
const strB = parts.join("");
```

- A) Approach A is faster because string concatenation is O(1)
- B) Approach B is faster because it avoids creating thousands of intermediate string objects
- C) Both approaches have identical performance
- D) Approach A is faster because `push` has overhead

**Answer: B) Approach B is faster because it avoids creating thousands of intermediate string objects**

> Strings in JavaScript are immutable. `strA += "x"` creates a new string object on every iteration — O(n²) memory allocations in worst-case implementations. Collecting parts in an array and calling `.join("")` once creates only one final string, making Approach B O(n). Modern V8 engines may optimize approach A, but Approach B is the reliable best practice.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>

## Q. What is the output and what pattern does the following `debounce` implementation demonstrate?

```js
function debounce(fn, delay) {
  let timer;
  return function(...args) {
    clearTimeout(timer);
    timer = setTimeout(() => fn.apply(this, args), delay);
  };
}

const log = debounce(msg => console.log(msg), 100);

log("first");
log("second");
log("third");
// After 100ms:
```

- A) `"first"`, `"second"`, `"third"` are all logged after 100ms each
- B) Only `"third"` is logged after 100ms
- C) Only `"first"` is logged, immediately
- D) Nothing is logged — debounce suppresses all calls

**Answer: B) Only `"third"` is logged after 100ms**

> `debounce` resets the timer on every call. Rapid successive calls (`"first"`, `"second"`, `"third"`) each cancel the previous pending timer. Only the **last** call\'s timer survives the delay and executes. This pattern is essential for performance-sensitive event handlers like search inputs, window resize, and scroll events.

<div align="right">
    <b><a href="#table-of-contents">↥ back to top</a></b>
</div>
