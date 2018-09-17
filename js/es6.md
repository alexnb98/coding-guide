# ES6 New Stuff

## Variables

new variables `const` and `let`. They are block scoped. Witch means they can't be used outside of their block.

## IIFE

```js

{
    // Data Privacy
    const a = 1;
    let b = 2;
}
```

## Template literals

```js

let string = `This is ${firstName} ${lastName}.`
// output --> This is John Smith.
```

## Arrow Functions

```js

    let ages6 = years.map(el => 2016 - el);
    console.log(ages6);
```

## Destructuring

```js

// arrays
const [name, age] = ['John', 26];
console.log(name); // John
console.log(age); // 26

// objects
const obj = {
    firstName: 'John',
    lastName: 'Smith'
};

const {firstName, lastName} = obj;
console.log(firstName);
console.log(lastName);

const {firstName: a, lastName: b} = obj;
console.log(a);
console.log(b);
```

## Loop through NodeLists (querySelectorAll)

```js

const boxes = document.querySelectorAll('.box');
Array.from(boxes).forEach(cur => cur.style.backgroundColor = 'dodgerblue');
```

## Looping trough Arrays

```js

for (const cur of boxesArr6) {
    if (cur.className.includes('blue')) {
        continue;
    }
    cur.textContent = 'I changed to blue!';
}
```

## Finding information from Arrays

```js

const ages = [12, 17, 8, 21, 14, 11];
console.log(ages.findIndex(cur => cur >= 18)); // 3
console.log(ages.find(cur => cur >= 18)); // 21
```

## Spread Operator

> Spread syntax allows an iterable such as an array expression or string to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected. MDN

```js

function sum(x, y, z) {
  return x + y + z;
}

const numbers = [1, 2, 3];

console.log(sum(...numbers));
// expected output: 6
```

## Rest Parameters

>The rest parameter syntax allows us to represent an indefinite number of arguments as an array.

```js

function sum(...theArgs) {
  return theArgs.reduce((previous, current) => {
    return previous + current;
  });
}

console.log(sum(1, 2, 3));
// expected output: 6
```

## Default parameters

`function SmithPerson(firstName, yearOfBirth, lastName = 'Smith'){ ... }`
If `lastName` is not passed as an argument, it will take the value of `Smith`, else it will take the specified value.

## Maps

> The Map object holds key-value pairs. Any value (both objects and primitive values) may be used as either a key or a value. MDN

new Map([[ 1, 'one' ],[ 2, 'two' ]])

[See MPN Specification](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map)

```js

var myMap = new Map();

var keyString = 'a string',
    keyObj = {},
    keyFunc = function() {};

// setting the values
myMap.set(keyString, "value associated with 'a string'");
myMap.set(keyObj, 'value associated with keyObj');
myMap.set(keyFunc, 'value associated with keyFunc');

myMap.size; // 3

// getting the values
myMap.get(keyString);    // "value associated with 'a string'"
myMap.get(keyObj);       // "value associated with keyObj"
myMap.get(keyFunc);      // "value associated with keyFunc"

myMap.get('a string');   // "value associated with 'a string'"
                         // because keyString === 'a string'
myMap.get({});           // undefined, because keyObj !== {}
myMap.get(function() {}) // undefined, because keyFunc !== function () {}
```

## Classes

> Classes are in fact "special functions", and just as you can define function expressions and function declarations, the class syntax has two components: class expressions and class declarations.

**Class declarations**: 

```js

class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}
```

> Class declarations are not Hoisted! You have to declare it first to access it.

**Class expression**

```js

let Rectangle = class {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};
```