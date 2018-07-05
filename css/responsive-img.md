# Responsive Images

## HTML

## CSS

The way you apply responsive images to css is using media queries

```scss
div{
background-image: url(example-small.jpg);

@media (min-resolution: 192dpi) and (min-width: 600px),
       (min-width: 2000px){
    // 192dpi = 2x resolution screen and 2nd condition
    // the "," represents an "or"
    background-image: url(example-big.jpg);
    }
}
```