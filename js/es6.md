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