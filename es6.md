---
title: ES2015+
category: JavaScript
layout: 2017/sheet
tags: [Featured]
updated: 2017-10-21
weight: -10
intro: |
  A quick overview of new JavaScript features in ES2015, ES2016, ES2017 and beyond.
---

### Block scoping

#### Let

```js
function fn () {
  let x = 0
  if (true) {
    let x = 1 // only inside this `if`
  }
}
```
{: data-line="2,4"}

#### Const

```js
const a = 1
```

`let` is the new `var`. Constants work just like `let`, but can't be reassigned.
See: [Let and const](https://babeljs.io/learn-es2015/#let--const)

### Backtick strings

#### Interpolation

```js
const message = `Hello ${name}`
```

#### Multiline strings

```js
const str = `
hello
world
`
```

Templates and multiline strings.
See: [Template strings](https://babeljs.io/learn-es2015/#template-strings)

### Binary and octal literals

```js
let bin = 0b1010010
let oct = 0o755
```

See: [Binary and octal literals](https://babeljs.io/learn-es2015/#binary-and-octal-literals)

### New methods

#### New string methods

```js
"hello".repeat(3)
"hello".includes("ll")
"hello".startsWith("he")
"\u1E9B\u0323".normalize("NFC")
```

See: [New methods](https://babeljs.io/learn-es2015/#math--number--string--object-apis)

### Classes

```js
class Circle extends Shape {
```

#### Constructor

```js
  constructor (radius) {
    this.radius = radius
  }
```
{: data-line="1"}

#### Methods

```js
  getArea () {
    return Math.PI * 2 * this.radius
  }
```
{: data-line="1"}

#### Calling superclass methods

```js
  expand (n) {
    return super.expand(n) * Math.PI
  }
```
{: data-line="2"}

#### Static methods

```js
  static createFromDiameter(diameter) {
    return new Circle(diameter / 2)
  }
}
```
{: data-line="1"}

Syntactic sugar for prototypes.
See: [Classes](https://babeljs.io/learn-es2015/#classes)

### Exponent operator

```js
const byte = 2 ** 8
// Same as: Math.pow(2, 8)
```
{: data-line="1"}

Promises
--------
{: .-three-column}

### Making promises

```js
new Promise((resolve, reject) => {
  if (ok) { resolve(result) }
  else { reject(error) }
})
```
{: data-line="1"}

For asynchronous programming.
See: [Promises](https://babeljs.io/learn-es2015/#promises)

### Using promises

```js
promise
  .then((result) => { ··· })
  .catch((error) => { ··· })
```
{: data-line="2,3"}

### Promise functions

```js
Promise.all(···)
Promise.race(···)
Promise.reject(···)
Promise.resolve(···)
```

### Async-await

```js
async function run () {
  const user = await getUser()
  const tweets = await getTweets(user)
  return [user, tweets]
}
```
{: data-line="2,3"}

`async` functions are another way of using functions.

See: [async function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)

Destructuring
-------------
{: .-three-column}

### Destructuring assignment

#### Arrays

```js
const [first, last] = ['Nikola', 'Tesla']
```
{: data-line="1"}

#### Objects

```js
let {title, author} = {
  title: 'The Silkworm',
  author: 'R. Galbraith'
}
```
{: data-line="1"}

Supports for matching arrays and objects.
See: [Destructuring](https://babeljs.io/learn-es2015/#destructuring)

### Default values

```js
const scores = [22, 33]
const [math = 50, sci = 50, arts = 50] = scores
```

```js
// Result:
// math === 22, sci === 33, arts === 50
```

Default values can be assigned while destructuring arrays or objects.

### Function arguments

```js
function greet({ name, greeting }) {
  console.log(`${greeting}, ${name}!`)
}
```
{: data-line="1"}

```js
greet({ name: 'Larry', greeting: 'Ahoy' })
```

Destructuring of objects and arrays can be also be done in function arguments.

### Default values

```js
function greet({ name = 'Rauno' } = {}) {
  console.log(`Hi ${name}!`);
}
```
{: data-line="1"}

```js
greet() // Hi Rauno!
greet({ name: 'Larry' }) // Hi Larry!
```

### Reassigning keys

```js
function printCoordinates({ left: x, top: y }) {
  console.log(`x: ${x}, y: ${y}`)
}
```
{: data-line="1"}

```js
printCoordinates({ left: 25, top: 90 })
```

This example assigns `x` to the value of the `left` key.

### Loops

```js
for (let {title, artist} of songs) {
  ···
}
```
{: data-line="1"}

The assignment expressions work in loops, too.

Spread
------

### Object spread

#### with Object spread

```js
const options = {
  ...defaults,
  visible: true
}
```
{: data-line="2"}

#### without Object spread

```js
const options = Object.assign(
  {}, defaults,
  { visible: true })
```

The Object spread operator lets you build new objects from other objects.

See: [Object spread](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator)

### Array spread

#### with Array spread

```js
const users = [
  ...admins,
  ...editors,
  'rstacruz'
]
```
{: data-line="2,3"}

#### without Array spread

```js
const users = admins
  .concat(editors)
  .concat([ 'rstacruz' ])
```

The spread operator lets you build new arrays in the same way.

See: [Spread operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator)

Functions
---------

### Function arguments

#### Default arguments

```js
function greet (name = 'Jerry') {
  return `Hello ${name}`
}
```
{: data-line="1"}

#### Rest arguments

```js
function fn(x, ...y) {
  // y is an Array
  return x * y.length
}
```
{: data-line="1"}

#### Spread

```js
fn(...[1, 2, 3])
// same as fn(1, 2, 3)
```
{: data-line="1"}

Default, rest, spread.
See: [Function arguments](https://babeljs.io/learn-es2015/#default--rest--spread)

### Fat arrows

#### Fat arrows

```js
setTimeout(() => {
  ···
})
```
{: data-line="1"}

#### With arguments

```js
readFile('text.txt', (err, data) => {
  ...
})
```
{: data-line="1"}

#### Implicit return
```js
numbers.map(n => n * 2)
// No curly braces = implicit return
// Same as: numbers.map(function (n) { return n * 2 })
```
{: data-line="1"}

Like functions but with `this` preserved.
See: [Fat arrows](https://babeljs.io/learn-es2015/#arrows-and-lexical-this)

Objects
-------

### Shorthand syntax

```js
module.exports = { hello, bye }
// Same as: module.exports = { hello: hello, bye: bye }
```

See: [Object literal enhancements](https://babeljs.io/learn-es2015/#enhanced-object-literals)

### Methods

```js
const App = {
  start () {
    console.log('running')
  }
}
// Same as: App = { start: function () {···} }
```
{: data-line="2"}

See: [Object literal enhancements](https://babeljs.io/learn-es2015/#enhanced-object-literals)

### Getters and setters

```js
const App = {
  get closed () {
    return this.status === 'closed'
  },
  set closed (value) {
    this.status = value ? 'closed' : 'open'
  }
}
```
{: data-line="2,5"}

See: [Object literal enhancements](https://babeljs.io/learn-es2015/#enhanced-object-literals)

### Computed property names

```js
let event = 'click'
let handlers = {
  [`on${event}`]: true
}
// Same as: handlers = { 'onclick': true }
```
{: data-line="3"}

See: [Object literal enhancements](https://babeljs.io/learn-es2015/#enhanced-object-literals)

Modules
-------

### Imports

```js
import 'helpers'
// aka: require('···')
```

```js
import Express from 'express'
// aka: const Express = require('···').default || require('···')
```

```js
import { indent } from 'helpers'
// aka: const indent = require('···').indent
```

```js
import * as Helpers from 'helpers'
// aka: const Helpers = require('···')
```

```js
import { indentSpaces as indent } from 'helpers'
// aka: const indent = require('···').indentSpaces
```

`import` is the new `require()`.
See: [Module imports](https://babeljs.io/learn-es2015/#modules)

### Exports

```js
export default function () { ··· }
// aka: module.exports.default = ···
```

```js
export function mymethod () { ··· }
// aka: module.exports.mymethod = ···
```

```js
export const pi = 3.14159
// aka: module.exports.pi = ···
```

`export` is the new `module.exports`.
See: [Module exports](https://babeljs.io/learn-es2015/#modules)

Generators
----------

### Generators

```js
function* idMaker () {
  let id = 0
  while (true) { yield id++ }
}
```

```js
let gen = idMaker()
gen.next().value  // → 0
gen.next().value  // → 1
gen.next().value  // → 2
```

It's complicated.
See: [Generators](https://babeljs.io/learn-es2015/#generators)

### For..of iteration

```js
for (let i of iterable) {
  ···
}
```

For iterating through generators and arrays.
See: [For..of iteration](https://babeljs.io/learn-es2015/#iterators--forof)

### Maps

Maps is a much needed data structure in JavaScript. Prior to ES6, we created hash maps through objects:

```js
var map = new Object();
map[key1] = 'value1';
map[key2] = 'value2';
```

However, this does not protect us from accidentally overriding functions with specific property names:

> getOwnProperty({ hasOwnProperty: 'Hah, overwritten'}, 'Pwned');
> TypeError: Property 'hasOwnProperty' is not a function
Actual Maps allow us to set, get and search for values (and much more).

let map = new Map();
> map.set('name', 'david');
> map.get('name'); // david
> map.has('name'); // true

The most amazing part of Maps is that we are no longer limited to just using strings. We can now use any type as a key, and it will not be type-cast to a string.

```js
let map = new Map([
    ['name', 'david'],
    [true, 'false'],
    [1, 'one'],
    [{}, 'object'],
    [function () {}, 'function']
]);

for (let key of map.keys()) {
    console.log(typeof key);
    // > string, boolean, number, object, function
}
```

Note: Using non-primitive values such as functions or objects won't work when testing equality using methods such as map.get(). As such, stick to primitive values such as Strings, Booleans and Numbers.

We can also iterate over maps using .entries():

```js
for (let [key, value] of map.entries()) {
    console.log(key, value);
}
(back to table of contents)
```

### WeakMaps
In order to store private data versions < ES6, we had various ways of doing this. One such method was using naming conventions:

```js
class Person {
    constructor(age) {
        this._age = age;
    }

    _incrementAge() {
        this._age += 1;
    }
}
```

But naming conventions can cause confusion in a codebase and are not always going to be upheld. Instead, we can use WeakMaps to store our values:

```js
let _age = new WeakMap();
class Person {
    constructor(age) {
        _age.set(this, age);
    }

    incrementAge() {
        let age = _age.get(this) + 1;
        _age.set(this, age);
        if (age > 50) {
            console.log('Midlife crisis');
        }
    }
}
```

The cool thing about using WeakMaps to store our private data is that their keys do not give away the property names, which can be seen by using Reflect.ownKeys():

> const person = new Person(50);
> person.incrementAge(); // 'Midlife crisis'
> Reflect.ownKeys(person); // []

A more practical example of using WeakMaps is to store data which is associated to a DOM element without having to pollute the DOM itself:

```js
let map = new WeakMap();
let el  = document.getElementById('someElement');

// Store a weak reference to the element with a key
map.set(el, 'reference');

// Access the value of the element
let value = map.get(el); // 'reference'

// Remove the reference
el.parentNode.removeChild(el);
el = null;

// map is empty, since the element is destroyed
```

As shown above, once the object is destroyed by the garbage collector, the WeakMap will automatically remove the key-value pair which was identified by that object.

Note: To further illustrate the usefulness of this example, consider how jQuery stores a cache of objects corresponding to DOM elements which have references. Using WeakMaps, jQuery can automatically free up any memory that was associated with a particular DOM element once it has been removed from the document. In general, WeakMaps are very useful for any library that wraps DOM elements.
