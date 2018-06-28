# Advanced CSS Course from Jonas Schedmann

Jonas has a lot of  resources on his [Internet page](http://codingheroes.io/resources/) 

## 3 Pillars to write good HTML and CSS
1. **Responsive Design:**
Fluid layouts, media queries, responsive images, correct units, dektop vs mobile first
2. **Maintainable and scalable code:**
clean, easy-to-understand, growth, reusable, how to organize files, how to name classes, how to structure html
3. **Web Performanc:**
less http request, less code, compressed code, css preprocessor, less images, compress images

## CSS Architecture:
The process: 
1. Think
2. Build
3. Architect

### Think
Think of your website as a colection of components (Component driven design). The components are modular building blocks, that are re-usable, independent and are held together by the layout of the page.

### Build (BEM Method)
* **Block**: standalone component that is meaningful on its own
* **Element**: part of a block that has no standalone meaning
* **Modifier**: a different version of a block or an element

```css
.block {}
.block__element {}
.block__element--modifier {}
```
There are a lot of other Build Methods, like OOCSS, DRY CSS, SMACSS. 

### Architecting with files and folders
**The 7-1 Pattern**: 7 folders for partial sass files, 1 main sass file to import all others

The 7 folders
* base/
* components/
* layout/
* pages/
* themes/
* abstracts/
* vendors/

*You don't have to use allways all folders, it depents on de size and scope of the proyect*

## Introduction to SASS and NPM

### NPM
is a simple command line interface. Helps you install and manage packages, like tools, libraries, frameworks and more.

*Depends on Node.js, so install it first. Check:* `node -v`

Then install NPM

In a proyect, when using NPM, the first step is create a `package.json` file. Command `npm init` and follow the steps

To install sass for example `npm install node-sass --save-dev` 
* `--save-prod` --> "dependencies": These packages are **required** by your application in production.
* `--save-dev` --> "devDependencies": These packages are only needed for **development and testing**.

[More info about NPM and package.json](https://docs.npmjs.com/getting-started/using-a-package.json)


