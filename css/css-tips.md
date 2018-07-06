# Usefull CSS Tips and Tricks

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

You can select a Libary and choose the number of icons you like from there.

Download the ones you need. Then search for the SVG folder and more importanly `symbol-defs.svg`. This is a file with all the SVGs inside of it. So the browser will only need one server-round-trip for all the SVGs. 

Use:

```html

<svg>
    <!-- This will only work on an server -->
    <use xlink:href="source/symbol-defs.svg#icon-name"></use>
</svg>
```
