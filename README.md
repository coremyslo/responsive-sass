# responsive-sass

[![npm version][npm-version-src]][npm-version-href]
[![npm downloads][npm-downloads-src]][npm-downloads-href]
[![License][license-src]][license-href]

A library of mixins for creating responsive styles in SASS.

## Features
* 👨‍🎨 **Multiple grids** - You can create multiple grids and use them in the same project.
* 👩‍🔬 **Smart rendering** - breakpoints are parsed smart under the hood, (1,1,1,1,1) will just insert value as is without any media query.
* ♾️ **Unlimited breakpoints** - You can create your own mixin from constructor `responsive` with any number of breakpoints.

## Setup

```bash
npm install responsive-sass

# or

yarn add responsive-sass
```
## Usage

```scss
@import "~responsive-sass/index";

@mixin mediaAll ($values...) {
    $rules: "all";
    $breakpoints: 30rem, 45rem, 75rem, 100rem; // 480px, 768px, 1024px, 1200px, 1600px;
    @include responsive ($rules, $breakpoints, $values...) {
        @content;
    }
}

// optional
@mixin mediaScreen ($values...) {
    $rules: "screen";
    $breakpoints: 30rem, 45rem, 75rem, 100rem; // 480px, 768px, 1024px, 1200px, 1600px;
    @include responsive ($rules, $breakpoints, $values...) {
        @content;
    }
}
@mixin mediaPrint ($values...) {
    $rules: "print";
    $breakpoints: 30rem, 45rem, 75rem, 100rem; // 480px, 768px, 1024px, 1200px, 1600px;
    @include responsive ($rules, $breakpoints, $values...) {
        @content;
    }
}
```
```scss
div {
    @include mediaAll (1,0,0,0,0) {
        background-color: blue;
    }
    @include mediaAll (0,0,1,0,1) {
        background-color: yellow;
    }
}
```
## Output

```css
div {
    @media all and (max-width: 30rem) {
        background-color: blue;
    }
    @media all and (min-width: 45rem) and (max-width: 75rem), all and (min-width: 100rem) {
        background-color: yellow;
    }
}
```

<!-- Badges -->
[npm-version-src]: https://img.shields.io/npm/v/responsive-sass/latest.svg?style=flat
[npm-version-href]: https://npmjs.com/package/responsive-sass

[npm-downloads-src]: https://img.shields.io/npm/dm/responsive-sass.svg?style=flat
[npm-downloads-href]: https://npmjs.com/package/responsive-sass

[license-src]: https://img.shields.io/npm/l/responsive-sass.svg?style=flat
[license-href]: https://npmjs.com/package/responsive-sass
