# Usefull Javascript Functions & Methods

## Functions

Calculate random number:

```js

function randomNumber(minNum, maxNum){
    return Math.floor(Math.random() * maxNum + 1) + minNum;
}
```

## Methods

to do DOM manipulation
`document`

### Select Elements

To select an html element
`document.querySelector('css selector')` // only gets first element

Select Id
`document.getElementById('Id')`

use to define text in an html element
`.textContent = "This is text";`

use to define html inside an html element
`.innerHTML = "<em> this is html </em>";`

To change CSS property:
`style.cssProperty = 'cssValue'`

### Methods for calling functions

* `call()`
* `apply();`
* `bind()`

## Event Listener

[Event Listeners table](https://developer.mozilla.org/en-US/docs/Web/Events)
