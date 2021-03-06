# `<macro-carousel>` &middot; [![npm version](https://img.shields.io/npm/v/macro-carousel.svg?style=flat)](https://www.npmjs.com/package/macro-carousel) [![Build Status](https://travis-ci.org/ciampo/macro-carousel.svg?branch=master)](https://travis-ci.org/ciampo/macro-carousel) [![Coverage Status](https://coveralls.io/repos/github/ciampo/macro-carousel/badge.svg)](https://coveralls.io/github/ciampo/macro-carousel) [![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/ciampo/macro-carousel/blob/master/LICENSE)

`<macro-carousel>` is a carousel (*vanilla*) Web Component.

**[DEMOS](https://ciampo.github.io/macro-carousel/demo/)** | **[DOCS](https://github.com/ciampo/macro-carousel/blob/master/docs/macro-carousel.md)**

- Compatible with every framework
- Public APIs exposed as methods, events and properties/attributes
- Mouse and touch events
- Previous and next buttons
- Pagination indicators
- Multiple slides per view
- Customisable styles though CSS custom properties
- Focused on a11y
- no external dependencies

## Installation

**`npm install --save macro-carousel`**

It is reccommended to install the [`inert`](https://github.com/WICG/inert) and [`focus-visible`](https://github.com/WICG/focus-visible) polyfills (listed as `peerDependencies`).


### Running the project locally

Run `npm install` to install all local dependencies.

Run `npm start` and open the [`http://localhost:8080/demo/`](http://localhost:8080/demo/) page in your browser.

## Usage

Please read the [full documentation](./docs/macro-carousel.md)

```html
<macro-carousel>
  <div>First slide</div>
  <div>Second slide</div>
  <div>Third slide</div>
</macro-carousel>

<script src="macro-carousel.min.js" defer></script>
```

For more examples, look at the demos ([Live demo](https://ciampo.github.io/macro-carousel/demo/), [Demo code](./demo/))

## Browser support

### WebComponent Polyfills suite

In order for this Web Component to work on all evergreen browsers, you may need to add the [WebComponent polyfills suite](https://github.com/webcomponents/webcomponentsjs) to your page. (*Please note that this repository focuses on the `macro-carousel` Web Component, and not on the polyfills*)

All the demos in this repository already make use of the polyfills (by using [`webcomponents-loader.js`](https://github.com/webcomponents/webcomponentsjs#webcomponents-loaderjs)). The source code of the `macro-carousel` Web Component also makes optional calls to the `ShadyCSS` polyfill.

Because of the [`ShadyCSS` polyfill limitations](https://github.com/webcomponents/shadycss#limitations), certain style rules are not applied in polyfilled browsers:

- all the rules that rely on the `:host-context()` selector are not polyfilled correctly (these rules are mainly around using the `focus-visible` polyfill)
- some of the more complex selectors using `:host()` are also not supported. This mainly impact the hover/focus states on navigation buttons.
- normally, external styles have the priority over the internal Web Component styles. But sometimes, after the polyfill's transformation, some internal selectors end up having a higher specificity then the external ones. This is quite an edge case, but keep an eye for it (e.g.: the [custom navigation demo](./demo/custom-navigation.html) uses the `!important` keyword to force some styles).

For browsers not supporting ES6 classes, the tranpiled ES5 version can be used instead (`macro-carousel.es5.min.js`), together with the  [`custom-elements-es5-adapter.js`](https://github.com/webcomponents/webcomponentsjs#custom-elements-es5-adapterjs) polyfill. The [es5 demo](./demo/es5.html) shows how to do that.

As browser support grows and the polyfills improve, these limitations should become less and less frequent and problematic.

### Other known cross-browser limitations

In order to change the color of the navigation button arrow, this project makes use of the `mask-image` CSS property. Unofruntaly, when this CSS feature is not supported, the color defined through `--macro-carousel-navigation-color-focus` is not going to be applied correctly to the arrow.

## Test

Run `npm test` to run all tests.

## Whishlist

Please have a look at [the backlog](https://github.com/ciampo/macro-carousel/milestone/2) to see the plan for the next releases.

If you have a feature request, feel free to open an issue!
