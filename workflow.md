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
