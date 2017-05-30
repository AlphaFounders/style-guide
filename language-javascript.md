# JavaScript

Please refer to
* as base [airbnb](https://github.com/airbnb/javascript)
* addendum [Idiomatic JavaScript](https://github.com/necolas/idiomatic-js)

Use ECMAScript (ES6) format.
You can watch useful lessons here [Laracast ES2015 Crash Course](https://laracasts.com/series/es6-cliffsnotes)

__Enable or install__ ESLint module for your IDE. Some projects have configured ESLint rules.
For example, [linter](https://github.com/roadhump/SublimeLinter-eslint) for Sublime.
## Addendum

### Line height and quotes
* Line length limit is still 120
* Use single quotes only

### Aligment

Developer has to align equal signs
```js
@section('scripts')
    <script>
        Rabbit                              = Rabbit || {};
        Rabbit.messages                     = Rabbit.messages || {};
        Rabbit.messages.invalidEmailAddress = '{!! trans('global.invalid-email') !!}';
        Rabbit.messages.invalidPhoneNumber  = '{!! trans('global.invalid-phone-number') !!}';
    </script>
@endsection
```

Use `$` in variable name only if it is some selected DOM element.

```js
// another example of variables declaration
const platform             = Rabbit.platForm;
const $body                = $('body');
const $compareButton       = $('#compare-button');
const $someSelectedElement = $('#selector');
const resultCard           = new ResultCard(platform);
const compare              = new CompareHelper(platform);
let counter                = 0;
let someVariable           = 'value';


// Don't need to align object's property
let someObject = {
    provider: 'value1',
    installmentLongProperty: 3,
};

```

### Fix errors early (not for ES6).

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
someFunctionWithOptions(options) {
    // Do something…
    […]
}

// Call the function.
someFunctionWithOptions({
    'parameter4' => 'someValue'
});
```

__Ideally__: refactor the function into smaller pieces.



## Tools
Please use the [.jscsrc](.jscsrc) and [.jshintrc](.jshintrc) files in this
repository for your projects. These files contain most of the style–guide
related issues addressed by our style–guides.

You can use them in you environment with the relevant softwares or plugins:

* JSHint: http://jshint.com/install/
* JSCS: http://jscs.info/overview#friendly-packages
