thoughtpad-plugin-compiler-coffeekup
=================================

[![build status][travis-image]][travis-url]
[![Test coverage][coveralls-image]][coveralls-url]

A thoughtpad plugin that responds to HTML compile events. Coffeekup will be compiled to HTML for use in the browser.

## Usage

The plugin should be loaded using the [thoughtpad-plugin-manager](https://github.com/thoughtpad/thoughtpad-plugin-manager). Once this has been done then the plugin will respond to events. To use standalone:

```JavaScript
var man = require('thoughtpad-plugin-manager'),
    coffeekup = require('thoughtpad-plugin-compiler-coffeekup');

var thoughtpad = man.registerPlugins([coffeekup]);
thoughtpad.subscribe("html-compile-complete", function (data) {
    console.log("HTML is returned here"); 
});
yield thoughtpad.notify("html-compile-request", { 
    ext: "coffee", 
    contents: "your coffeekup code here", 
    data: {foo:'bar'},
    name: "name of the file"
});
```

## Variables

Additional data can be used in the Coffeekup code that allows you to dynamically generate code and create simple logical constructs. This extra data can be passed into the `html-compile-request` notification using the `data` object. In addition, anything in the `thoughtpad.config` object will be passed too.

## Tests

Ensure you have globally installed mocha - `npm -g install mocha`. Then you can run:

`mocha`

Alternatively if you are in a *NIX environment `npm test` will run the tests plus coverage data.

## License

The code is available under the [MIT license](http://deif.mit-license.org/).

[travis-image]: https://img.shields.io/travis/thoughtpad/thoughtpad-plugin-compiler-coffeekup/master.svg?style=flat-square
[travis-url]: https://travis-ci.org/thoughtpad/thoughtpad-plugin-compiler-coffeekup
[coveralls-image]: https://img.shields.io/coveralls/thoughtpad/thoughtpad-plugin-compiler-coffeekup/master.svg?style=flat-square
[coveralls-url]: https://coveralls.io/r/thoughtpad/thoughtpad-plugin-compiler-coffeekup?branch=master
