# responsive-sass

[![npm version][npm-version-src]][npm-version-href]
[![npm downloads][npm-downloads-src]][npm-downloads-href]
[![License][license-src]][license-href]

A library of mixins for creating responsive styles in SASS.

## Setup
1. Add the dependency

```bash
npm install responsive-sass

# or

yarn add responsive-sass
```
2. Import the file

```scss
@import "~responsive-sass/index";
```
3. Configure your own mixin(s) from the constructor

```scss
@mixin mediaAll ($values...) {
    $rules: "all"; // all, screen, print
    $breakpoints: 30rem, 45rem, 75rem, 100rem; // 480px, 768px, 1024px, 1200px, 1600px;
    @include responsive ($rules, $breakpoints, $values...) {
        @content;
    }
}
```
4. Use it in your scss styles

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
5. Observe the result in css:

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
