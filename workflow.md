# Workflow, Tools and Extras for Programing

## Introduction to SASS and NPM

### NPM
is a simple command line interface. Helps you install and manage packages, like tools, libraries, frameworks and more.

*Depends on Node.js, so install it first. Check:* `node -v`

Then install NPM

In a proyect, when using NPM, the first step is create a `package.json` file. Command `npm init` and follow the steps

To install sass for example `npm install node-sass --save-dev` 
* `--save-prod` --> "dependencies": These packages are **required** by your application in production.
* `--save-dev` --> "devDependencies": These packages are only needed for **development and testing**.

To uninstall a package 
* `npm unintall <package name> [install flag]`

[More info about NPM and package.json](https://docs.npmjs.com/getting-started/using-a-package.json)

### Write NPM Scrits
on `package.json` under "scripts" you can write you're npm scripts. 

* **Sass npm script:** `"node-sass <sass dir>/main.scss <css dir>/style.css"`
* **To use the script:** `npm run <script name>`

### Advanced NPM commands

With NPM you can use more commands to make your code better, lighter and more accesible.

1. Install Node Sass: `npm install node-sass --save-dev`
2. Install Concat: `npm install concat --save-dev` (*concat is used to concatenate or paste together different css style sheets*)
3. Install Autoprefixer: 
    1. First `npm install autoprefixer --save-dev`
    2. Second `npm install postcss-cli --save-dev` (*is a dependency of autoprefixer*)
4. Compress all of it: `node-sass <input> <output> --output-style compressed` 

To install all the packages in `package.json` use `npm install` 

#### final file 

```json

{
  "scripts": {
    // Develop Script
    "watch:sass": "node-sass sass/main.scss css/style.css -w", //watches the scss files and compiles them to css
    "devserver": "live-server", // live server lets you see the changes in real time
    // This is the one you use when developing
    "start": "npm-run-all --parallel devserver watch:sass", // uses node-sass and live-server at the same time
    // Build script
    "compile:sass": "node-sass sass/main.scss css/style.comp.css", // compiles scss to css without watching
    "concat:css": "concat -o css/style.concat.css css/icon-font.css css/style.comp.css", // concats style.css with icon-font.css
    "prefix:css": "postcss --use autoprefixer -b \"last 10 versions\" css/style.concat.css -o css/style.prefix.css", // puts prefixes 
    "compress:css": "node-sass css/style.prefix.css css/style.css --output-style compressed", // compresses the css
    // This is the one you use to build the page
    "build:css": "npm-run-all compile:sass concat:css prefix:css compress:css" // those all 4 above in one command
  },
//   These are the dev-dependencies
  "devDependencies": {
    "autoprefixer": "^7.1.4",
    "concat": "^1.0.3",
    "node-sass": "^4.5.3",
    "npm-run-all": "^4.1.1",
    "postcss-cli": "^4.1.1"
  }
}
```