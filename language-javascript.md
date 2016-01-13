# JavaScript

Please refer to [Idiomatic JavaScript](https://github.com/necolas/idiomatic-js)
for style–guides about JavaScript.


## Addendum

### Fix errors early.

We want to **target bugs as soon as possible**. To do so, we should always add
`'use strict';` as the first statement of any function at the root of the
document.

### Be more flexible.

In case of a function doing too much but that can‘t be easily refactored, and
if that function has more than two parameters, let’s avoid having the following:
```js
/** Defining this awesome function that does too much.
 *
 * @param {integer} parameter1 - Represent something.
 * @param {integer} parameter2 - Represent something else.
 * @param {boolean} parameter3 - Is this for real?
 * @param {string}  parameter4 - Values for that other stuff.
 */
someFunctionWithAddedParametersOverTime( parameter1, parameter2, parameter3, parameter4 ) {
    // Do something…
    […]
}

// Call the function.
someFunctionWithAddedParametersOverTime(
    undefined,
    undefined,
    false,
    'someValue'
);
```

Use an `options` parameter instead to allow more flexibility:
```js
/** Defining this awesome function that still does too much.
 *
 * @param {object}  options
 * @param {integer} options.parameter1 - Represent something.
 * @param {integer} options.parameter2 - Represent something else.
 * @param {boolean} options.parameter3 - Is this for real?
 * @param {string}  options.parameter4 - Values for that other stuff.
 */
someFunctionWithOptions( options ) {
    // Do something…
    […]
}

// Call the function.
someFunctionWithOptions({
    'parameter4' => 'someValue'
});
```

Ideally: refactor the function into smaller pieces.



## Tools

Please use the [.jscsrc](.jscsrc) and [.jshintrc](.jshintrc) files in this
repository for your projects. These files contain most of the style–guide
related issues addressed by our style–guides.

You can use them in you environment with the relevant softwares or plugins:

* JSHint: http://jshint.com/install/
* JSCS: http://jscs.info/overview#friendly-packages
