# CSS Architecture:
The process: 
1. Think
2. Build
3. Architect

### Think
Think of your website as a colection of components (Component driven design). The components are modular building blocks, that are re-usable, independent and are held together by the layout of the page.

### Build (BEM Method)
Build your colection of components with the CSS Methodology of your choice. Examples:
* BEM
* SMACSS
* OOCSS
* DRY CSS

### Architecting with files and folders
Organize your files with a specific order system. Example

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

## BEM Method
* **Block**: standalone component that is meaningful on its own
* **Element**: part of a block that has no standalone meaning
* **Modifier**: a different version of a block or an element

```css
.block {}
.block__element {}
.block__element--modifier {}
```
[More info](http://getbem.com/introduction/)