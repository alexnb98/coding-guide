# JavaScript Objects

- [JavaScript Objects](#javascript-objects)
    - [What is an Object](#what-is-an-object)
    - [Ways of defining objects](#ways-of-defining-objects)
        - [Using object initializers](#using-object-initializers)
        - [Using a constructor function](#using-a-constructor-function)
        - [Using the Object.create method](#using-the-objectcreate-method)
    - [Inheritance](#inheritance)
        - [How it works:](#how-it-works)

## What is an Object

> An object is a collection of properties, and a property is an association between a name (or key) and a value. A property's value can be a function, in which case the property is known as a method. In addition to objects that are predefined in the browser, you can define your own objects.
[MDN Definition](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects)

![Simple explanation of objects](/js/gfx/objects-explanation.png)

## Ways of defining objects

### Using object initializers

```js

var john = {
    property: 'value',
    name: 'John',
    yearOfBirth: 1990,
    male: true,
    favColors: ['blue', 'red'], //array
    favFoods: { // object inside other object
        breakfast: 'apple',
        lunch: 'steak',
    },
};
```

### Using a constructor function

> 1. Define the object type by writing a constructor function. There is a strong convention, with good reason, to use a capital initial letter.
> 2. Create an instance of the object with `new`.

```js

function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}
```

Now you can create an object called mycar as follows:

`var mycar = new Car('Eagle', 'Talon TSi', 1993);`

### Using the Object.create method

> Objects can also be created using the `Object.create()` method. This method can be very useful, because it allows you to choose the prototype object for the object you want to create, without having to define a constructor function.

```js

var personProto = {
    calculateAge: function() {
        console.log(2016 - this.yearOfBirth);
    }
};

var john = Object.create(personProto);
john.name = 'John';
john.yearOfBirth = 1990;
john.job = 'teacher';

var jane = Object.create(personProto, {
    name: { value: 'Jane' },
    yearOfBirth: { value: 1969 },
    job: { value: 'designer' }
});
```

## Inheritance

> All objects in JavaScript inherit from at least one other object. The object being inherited from is known as the prototype (`__proto__`), and the **inherited properties** can be found in the prototype **object of the constructor**.

### How it works:

We first create an Function Constructor

```js

var Person = function(name, yearOfBirth, job) {
    this.name = name;
    this.yearOfBirth = yearOfBirth;
    this.job = job;
}
```

If we want to inherit properties from the constructor we use the `prototype` method.

```js

Person.prototype.calculateAge  = function() {
    console.log(2016 - this.yearOfBirth);
};

Person.prototype.lastName = 'Smith';
```

Now if we create a new "Person" using the constructor function this person inherits these two properties like this.

`var john = new Person('John', 1990, 'teacher');`

![Objects Inheritance](/js/gfx/objects-inheritance.png)