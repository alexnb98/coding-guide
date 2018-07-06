# Useful CSS Tips and Tricks

## Browser Reset

```scss
*,
*::after,
*::before {
    margin: 0;
    padding: 0;
    box-sizing: inherit;
}
```

## Defining 1rem = 10px

```scss

html {
    // This defines what 1rem is
    font-size: 62.5%; //1 rem = 10px; 10px/16px = 62.5%
}
```

## Change selection color

```scss
::selection{
    background-color: $primary-color;
    color: $color-white;
}
```

## Using Variables in CSS

```css
/* Declaration */
:root{
    --variable-1: #ccc;
    --variable-2: #fff;
}

/* Use */
body{
    background-color: var(--variable-1);
}
```

## Working with SVG in HTML

For Icons it is now better to use SVGs instead of Icon-Fonts

Good Resource to Download SVG Icons: [icomoon](https://icomoon.io/) you can even upload icons and convert them to svg.

You can select a Library and choose the number of icons you like from there.

Download the ones you need. Then search for the SVG folder and more importantly `symbol-defs.svg`. This is a file with all the SVGs inside of it. So the browser will only need one server-round-trip for all the SVGs. 

Change the color of the SVG with `fill: red`

Use:

```html

<svg>
    <!-- This will only work on an server -->
    <use xlink:href="source/symbol-defs.svg#icon-name"></use>
</svg>
```

## CurrentColor CSS Property

Use `currentColor` so that a child can inherit the color of his parent dynamically.

```scss

.parent{
    color: red;
    &:hover{
        color: blue;
    }
}

.child{
    color: currentColor;
}
```

## Apply different transitions to the properties

```scss

.element{
    width: 50%;
    background-color: red;
    margin: 3rem;
    // different transitions
    transition: width .2s .4s, //transition 1
                background-color .2s, //transition 2
                margin .2s ease-in; //transition 3

    &:hover{
        // other properties
    }
}
```