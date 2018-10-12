# Things I learned from the Forkify App

- [Things I learned from the Forkify App](#things-i-learned-from-the-forkify-app)
    - [Webpack](#webpack)
    - [Babel](#babel)
    - [Modular Programming](#modular-programming)
        - [How to export and import Modules in Webpack](#how-to-export-and-import-modules-in-webpack)
            - [First Method](#first-method)
            - [Second Method](#second-method)
    - [Render HTML in the page](#render-html-in-the-page)
    - [Delete HTML from the page](#delete-html-from-the-page)
    - [Clear Thing from HTML](#clear-thing-from-html)
    - [Having a state object](#having-a-state-object)
    - [How to save data in the Local Storage](#how-to-save-data-in-the-local-storage)
    - [Use Event Delegation](#use-event-delegation)

## Webpack

[Good Article About Webpack Intro](https://medium.com/@svinkle/getting-started-with-webpack-and-es6-modules-c465d053d988)

Webpack is a tool that helps you bundle all your JS Modules into one File. It also helps you parsing ES6+ to ES5. And a lot More.

This is the config I used in the project. `webpack.config.js`

```js

const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
    devtool: 'cheap-module-source-map',
    entry: ['babel-polyfill', './src/js/index.js'],
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'js/bundle.js'
    },
    devServer: {
        contentBase: './dist'
    },
    plugins: [
        new HtmlWebpackPlugin({
            filename: 'index.html',
            template: './src/index.html'
        })
    ],
    module: {
        rules: [
            {
                test: /\.js$/,
                exclude: /node_modules/,
                use: {
                    loader: 'babel-loader'
                }
            }
        ]
    }
};
```

`package.json`

```json

{
  "name": "forkify",
  "version": "1.0.0",
  "description": "forkify project",
  "main": "index.js",
  "scripts": {
    "dev": "webpack --mode development",
    "build": "webpack --mode production",
    "start": "webpack-dev-server --mode development --open"
  },
  "author": "Alexander",
  "license": "ISC",
  "devDependencies": {
    "babel-core": "^6.26.3",
    "babel-loader": "^7.1.4",
    "babel-preset-env": "^1.7.0",
    "html-webpack-plugin": "^3.2.0",
    "webpack": "^4.19.1",
    "webpack-cli": "^3.1.0",
    "webpack-dev-server": "^3.1.8"
  },
  "dependencies": {
    "axios": "^0.18.0",
    "babel-polyfill": "^6.26.0",
    "fractional": "^1.0.0",
    "uniqid": "^5.0.3"
  }
}
```

## Babel

`.babelrc`

```json

{
    "presets": [
        ["env", {
            "targets": {
                "browsers": [
                    "last 5 versions",
                    "ie >= 8"
                ]
            }
        }]
    ]
}
```

## Modular Programming

Every function is written in modules using the MVC pattern (Model-View-Controller)

![MVC Graph](/js/gfx/MVC-Process.svg?sanitize=true)

This makes every Function with a clear purpose independed and easy to reuse everywhere in the project.

The Forkify App following MVP Pattern:

![Forkify Flowchart](/js/gfx/forkify_flowchart.png)

This is an example of one Module of the Controller

```js

// SEARCH CONTROLLER
const controlSearch = async () => {
    // 1. get query from view
    const query = searchView.getInput();

    if (query) {
        // 2. new search object and add to state
        state.search = new Search(query);
        try {
            // 3. Prepare UI for results
            searchView.clearInput();
            searchView.clearResults();
            renderLoader(elements.searchRes);
    
            // 4. Search for recipes
            await state.search.getResults();
            // 5. render results un UI
            clearLoader();
            searchView.renderResults(state.search.result);
        } catch(err) {
            console.error(`something went wrong with the search ${err.stack}`);
            clearLoader();
        }
    }
}

// eventListener
elements.searchForm.addEventListener('submit', e => {
    e.preventDefault();
    controlSearch();
});
```

### How to export and import Modules in Webpack

#### First Method

Files we want to export

```js

const sum = () => { //function }

export {sum};

// or

export const product = () => { //function }
```

To use functions

```js

import {sum, product} from './modules/math-functions';

// or if just one module
import sum from './modules/math-functions';

sum();
```

#### Second Method

`searchView`

```js

const funct1 = () => { //function }
const funct2 = () => { //function }
```

To import all modules from `searchView`

```js
import * as searchView from './views/searchView';

searchView.func1();
searchView.func2();
```

## Render HTML in the page

```js
export const renderLike = like => {
    const markup = `
        <li>
            <a class="likes__link" href="#${like.id}">
                <figure class="likes__fig">
                    <img src="${like.img}" alt="${like.title}">
                </figure>
                <div class="likes__data">
                    <h4 class="likes__name">${limitRecipeTitle(like.title)}</h4>
                    <p class="likes__author">${like.author}</p>
                </div>
            </a>
        </li>
    `;
    elements.likesList.insertAdjacentHTML('beforeend', markup);
}
```

## Delete HTML from the page

```js

export const deleteLike = id => {
    const el = document.querySelector(`.likes__link[href*="${id}"]`).parentElement;
    if(el) el.parentElement.removeChild(el);
}
```

## Clear Thing from HTML

```js

export const clearRecipe = () => {
    elements.recipe.innerHTML = '';
};
```

## Having a state object

The State Object includes all the data of the app at a certain moment.

1. When loading the page you create an empty state object. `const state = {};`
2. Then you create new objects inside the state `state.search = new Search(query);`
> In forkify the state had maximum 4 objects. `Search`, `Recipe`, `List` and `Likes`
3. To save something inside this 4 objects you use `this.keyword = something` 
4. All Objects have methods you can use to do something with the data that is saved in the state object.
> `Search` has `getResults()` method. To use it: `state.search.getResults()`

## How to save data in the Local Storage

Use the `localStorage` method with `setItem()`, `getItem()` and `removeItem()` example: `localStorage.setItem('likes', JSON.stringify(this.likes));`

## Use Event Delegation

This is useful to add EventListeners to items that are not yet in the DOM.
> Add event listener to a parent where the target element will be.

```js
parentElement.addEventListener('click', e => {
    const id = e.target.closest('.target_element');
}
```

To know if an Element is in the DOM use `element.matches()`
> returns `true` if the element would be selected by the specified selector string; otherwise, returns `false`. MDN
`if (e.target.matches('selector'))` // return true or false