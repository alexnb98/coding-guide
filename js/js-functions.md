# Functions

>Generally speaking, a function is a "subprogram" that can be called by code external (or internal in the case of recursion) to the function. Like the program itself, a function is composed of a sequence of statements called the function body. Values can be passed to a function, and the function will return a value. [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions)

## Types of functions

### The function declaration (function statement)

```js

function name([param[, param[, ... param]]]) {
   statements
}
```

### The function expression (function expression)

```js

var getRectArea = function(width, height) {
    return width * height;
}
```

### IIFE (Immediately invokable function expression)

IIFE's are used to create *data privacy*. Because of the scope chain the variables declared in an IIFE can not be accessed from the global Global Execution Context.

```js

(function() {
    statements
})();
```

### Functions returning functions

```js

function interviewQuestion(job) {
    if (job === 'designer') {
        return function(name) {
            console.log(name + ', can you please explain what UX design is?');
        }
    } else {
        return function(name) {
            console.log('Hello ' + name + ', what do you do?');
        }
    }
}

var teacherQuestion = interviewQuestion('teacher');
teacherQuestion('John');
// Hello John, what do you do?

interviewQuestion('designer')('Mark');
// Mark, can you please explain what UX design is?
```

```js

function interviewQuestion(job) {
    var designer = ', can you please explain what UX design is?';
    var teacher = 'What subject do you teach, ';
    if (job === 'designer') {
        return function(name) {
            console.log(name + designer);
        }
    } else if (job === 'teacher') {
        return function(name) {
            console.log(teacher + name + '?');
        }
    } else {
        return function(name) {
            console.log('Hello ' + name + ', what do you do?');
        }
    }
}
```