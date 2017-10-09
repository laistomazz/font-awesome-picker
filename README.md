# fontAwesomePicker

[![npm](https://img.shields.io/npm/v/font-awesome-picker.svg) ![npm](https://img.shields.io/npm/dm/font-awesome-picker.svg)](https://www.npmjs.com/package/fontawesomepicker)
[![vue2](https://img.shields.io/badge/vue-2.x-brightgreen.svg)](https://vuejs.org/)

A Vue.js component to easily pick a FontAwesome icon and use it as you wish.

![print screen](https://raw.githubusercontent.com/laistomazz/font-awesome-picker/master/docs/font-awesome-picker.png)

## Table of contents

- [Installation](#installation)
- [Usage](#usage)
- [Options](#options)

# Installation

```
npm install --save font-awesome-picker
```

# Usage

Install the component:

```javascript
import Vue from 'vue';
import { fontAwesomePicker } from 'font-awesome-picker';

export default {
    name: 'yourComponent',
    components: {
        'font-awesome-picker': fontAwesomePicker,
    },
}
```

Instance as a custom element:

```html
<font-awesome-picker></font-awesome-picker>
```

Import style

```sass
@import 'node_modules/font-awesome-picker/dist/font-awesome-picker';
```
# Options

## Searchbox

To change the search box placeholder:

```html
<font-awesome-picker seachbox="search here"></font-awesome-picker>
```

## Result

To get the result from the fontAwesomePicker

```html
<font-awesome-picker v-on:selectIcon="yourFunction"></font-awesome-picker>
```

It will emit an object as a result:

```javascript
{
    className: 'fa-home',
    cssValue: 'F015',
}
```

[MIT](http://opensource.org/licenses/MIT)
