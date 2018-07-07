# Basic responsive design principles

## Using rem instead of pixel

Using `rem` makes you site more responsive and accesible for people. If the users changes the default `font-size` in his browser, it still will work perfectly.

```scss

html {
    // This defines what 1rem is
    font-size: 62.5%; //1 rem = 10px; 10px/16px = 62.5%

    // then you can use media querias and change the value

    body {
        box-sizing: border-box;
        padding: 3rem; //represents 30 pixel
    }
}
```

Note that when using `media queries` it is best to use `em` instead.

## Mobile first vs Desktop first

![Media Queries](gfx/media-queries.png)

### Desktop First

* Is optimized for large screens
* `max-width(...)`

### Mobile First 

![Mobile First cons and pros](gfx/mobile-first.png)
* Optimized for mobiles
* `min-width(...)`

## Breakpoints

![How to choose breakpoints](gfx/breakpoints.png)
**Good:** you see which are the most used device width and make your decision from there

**Perfect:** you start from your mobile or desktop page and start decreasing your browser and every time your design brakes, you add a Media Query. 

## How to use Media Queries

### Use Mixins

#### For Desktop First

`only screen` makes shure the media querias only get applied to screens

```scss
@mixin md-down($breakpoint) {
    @if $breakpoint == phone {
        @media only screen and (max-width: 37.5em) { @content };    //600px
    }
    @if $breakpoint == tab-port {
        @media only screen and (max-width: 56.25em) { @content };     //900px
    }
    @if $breakpoint == tab-land {
        @media only screen and (max-width: 75em) { @content };    //1200px
    }
}
```

#### For Mobile First

```scss

@mixin mq-up($breakpoint) {
    @if $breakpoint == phone {
        @media only screen and (min-width: 37.5em) { @content };    //600px
    }
    @if $breakpoint == tab-port {
        @media only screen and (min-width: 56.25em) { @content };     //900px
    }
    @if $breakpoint == tab-land {
        @media only screen and (min-width: 75em) { @content };    //1200px
    }
}
```

#### Touch Devices

This makes shure the styles only get applied in touch devices or devices where there is no hover possible.

```scss

@media screen only and (hover: none){
    // styles
}
```

And add the mixins at the end of your styles. Examples:

```scss

.row {
    // styles
    &:not(:last-child) {
        // styles

        @include respond(tab-port) {
            // media queries styles
        }
    }
    @include respond(tab-port) {
        // media queries styles
    }
    [class^="col-"] {    
        &:not(:last-child) {
            // styles

            @include respond(tab-port) {
                // media queries styles
            }
        }
    }
```

## Custom Media Queries

```scss

@mixin mq-down($bp) {
    @media only screen and (max-width: $bp) { @content };
}

@mixin mq-up($bp) {
    @media only screen and (min-width: $bp) { @content };
}

@mixin mq-only($bp-min, $bp-max) {
    @media (min-width: $bp-min) and (max-width: $bp-max) { @content };
}
```

### My Custom VS Code Snippets for using the mixins

```json

{
    "Media Query Down": {
        "prefix": "mq-down",
        "body": [
            "@include mq-down(${bp}) {",
                "",
            "}"
        ],
        "description": "Media Query Desktop First"
    },
    "Media Query Up": {
        "prefix": "mq-up",
        "body": [
            "@include mq-up(${bp}) {",
                "",
            "}"
        ],
        "description": "Media Query Mobile First"
    },
    "Media Query Up": {
        "prefix": "mq-only",
        "body": [
            "@include mq-only(${bp-min}, ${bp-max}) {",
                "",
            "}"
        ],
        "description": "Media Query Between Ranges"
    },
}
```

File Name: `scss.json`

Save in: `...\Code\User\snippets`

## Browser support

Test always for browser support with [caniuse.com](https://caniuse.com/)

To apply certain styles if the browser supports the property use this method: `@supports (property: value){...}`

example

```scss
div {
    @supports (display: grid) {
        display: grid;
  }
}
```

More information on [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/@supports)