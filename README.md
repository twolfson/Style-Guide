UI Style Guide
==============
This style guide was written as a reference for Ensighten's Manage-Interface.

Contents
--------
### [Basics](#basics)
- Indentation
- Semicolons
- Variable instantiation
- Commas
- Equality
- Conditionals
- Quotes
- Braces
- CSS braces
- Functions
- Object/array literals
- Trailing whitespace
- Line length
- Constants

### [Day to day](#day-to-day)
- Localizing variables
- Variable naming
- Constructor naming
- Prototypal definition
- Condition complexity
- Parameter count
- Naming closures
- Nesting closures
- Console debugging
- Loop lookups
- TODO's and FIXME's
- Function documentation

### [Less frequents](#less-frequents)
- Prototypal inheritance
- Extending prototypes
- node_modules
- Subtle anti-patterns

### [Attribution](#attribution)

Indentation
-----------
2 spaces per level of indentation. Sorry, no tabs allowed here.

### Good
```js
setTimeout(function () {
  var hello = "world";
}, 100);
```

### Bad
```js
setTimeout(function () {
    var hello = "world";
}, 100);
```

Semicolons
----------
Semicolon every line where a semicolon would be appropriate.

### Good
```js
var hello = "world";
```

### Bad
```js
var hello = "world"
```

Variable instantiation
----------------------
Adjacent `var`s are frowned upon, use commas. Additionally, the following variables should have the same 4 space indentation (as caused by the `var `)
`var`s at different code chunks okay and occasionally suggested to improve readability.

### Good
```js
function myFunc() {
  var one = "fish",
      two = "fish";

  // Logic between one and two

  var red = "fish",
      blue = "fish";
}
```

### Bad
```js
function myFunc() {
  var one = "fish";
  var two = "fish";
  var red;
  var blue;

  // Logic between one and two

  red = "fish";
  blue = "fish";
}
```

Commas
------
Commas should be on the same line as the statement. Sorry, no comma-first allowed.

### Good
```js
var a = 1,
    b = 2;
```

### Bad
```js
var a = 1
  , b = 2;
```

Equality
--------
Always use strict equals (`===` or '!==`), never truthy/falsy equality (`!=` or `==`).

Even if you are using the type coercion of JavaScript, other developers will not know explicitly all of your cases.

It is okay to use a conditional with a truthy conversion if the variable has been coerced as a boolean earlier.

```js
var isEven = i % 2 === 0;
if (isEven) {
  // Do even things
}
```

### Good
```js
var items = [1, 2, 3],
    i = 0,
    len = items.length;
for (; i < len; i++) {
  // Do stuff with item
}
```

### Bad
```js
var items = [1, 2, 3],
    i = 0;
for (; i < items.length; i++) {
  // Do stuff with item
}
```

Conditionals
------------
Provide a space between the `if` and the opening parenthesis and a space between the closing parenthesis and opening brace.

`else if`s and `else`s should be on the same line as the closing brace.

If you would like to provide comments, make it read like a sentence and place the `if` comment before the opening `if` and the `else/else if` comment after the `else/else if` statement.

Comments should be at the same indentation as the `if` statement. `else/else if` statements should read as "Otherwise," or "Otherwise if,".

### Good
```js
// If my number is 42, answer the question
if (myNum === 42) {
  question.answer(myNum);
} else if (myNum === 88) {
// Otherwise, if my number is 88, go through time
  delorean.timeTravel();
} else {
// Otherwise, walk 500 more miles
  me.walk(500);
}
```

Quotes
------
Single quotes in any normal logic set (including object literal keys). In views, all strings and attributes should use double quotes.

Exceptions to this:

- `topic` key in vows.js tests will have no quotes.
- In grunt.js, as is the tendency for grunt, no keys should have quotes.

### Good
```js
var user = {
  'username': 'ensighten.admin',
  'clientId': 1,
  'password': '12345'
};
```

### Bad
```js
var user = {
  username: 'ensighten.admin',
  clientId: 1,
  password: '12345'
};
```

Braces
------
A conditional/function should always have the first brace on the first line. The last brace will be standalone on its own last line.

If you have a one line conditional, you are allowed to put it in one line but you must still use braces.

```js
if (myNumber === 2) { /* do stuff */ }
```

### Good
```js
var user = {
  'username': 'ensighten.admin',
  'clientId': 1,
  'password': '12345'
};
```

### Bad
```js
var user = {
  username: 'ensighten.admin',
  clientId: 1,
  password: '12345'
};
```

CSS braces
----------
We might be using stylus, but we want to stay akin to our CSS brethren. Braces are used in a similar fashion to the JS side.

If it is one CSS property, it can be one line but it must still use braces.

If it is multiple properties, same line for opening brace and own line for closing brace.

```css
.gadget { background: blue; }
```

### Good
```js
.gadget {
  background: blue;
  border: 1px solid white;
}
```

### Bad
```js
.gadget
  background blue
  border 1px solid white
```

Functions
---------
There will always be a space after the closing parenthesis and opening brace for a function. Use spaces after commas to delimit variables.

If the function is named and not being invoked, do not provide a space between the function name and the opening parenthesis.

```js
function myFunc() {
  // Do myFunc tasks
}
```

If the function is named and being invoked ([only do this when on server](#naming-closures)), *do* provide a space between the function name and the opening parenthesis.

```js
setTimeout(function paintWall () {
  // Paint the wall
}, 1000);
```

If the function is anonymous, space between `function` and opening parenthesis.

```js
var util = {
  'email': function () {
    // Email items
  }
};
```

Object/array literals
----------------------
Use indentation within the open and close of the literal. If the literal is short enough, you can make it a single line item.

Additionally, we accept both indenation formats for objects inside of arrays but the first one shown is preferred as it is leaner.

```js
var arr = ['a', 'b', 'c'];
var obj = {'a': 'b', 'c': 'd'};
```

```js
var arrayOfObject = [{
      'a': 'b'
    }, {
      'c': 'd'
    }];
```

```js
var arrayOfObject = [
      {
        'a': 'b'
      }, {
        'c': 'd'
      }
    ];
```

Trailing whitespace
-------------------
Every time you leave trailing white space in your document, God kills a kitten.

### Good
```js
var hello = "world";
```

### Bad
```js
var hello = "world";
```

Line length
-----------
Long lines are okay but frowned upon.
If you are running into long logic statements, please localize your variables (see [Localizing variables](#localizing-variables)).

Constants
---------
Constants must be defined at the head of a file. If this is a client side file, it should be placed within the `define` statement to prevent public namespace pollution/collisions.

Use `var` and ALL_CAPS with underscores for spaces.

### Good
```js
var CREATE_ERROR = {
  'code': 100,
  'name': 'Creation error',
  'description': 'Could not successfully create item',
  'severity': 'Fatal'
};
```

### Bad
```js
var createerror = {
  'code': 100,
  'name': 'Creation error',
  'description': 'Could not successfully create item',
  'severity': 'Fatal'
};
```

Day to day
==========

Localizing variables
--------------------
If you ever lookup the same item twice (methods excluded) OR reference a property of a property inline, localize the property into a variable.

### Good
```js
var items = ['a', 'b', 'c'],
    secondItem = items[1];
if (secondItem === 'a' || secondItem === 'b') {
  // Do some stuff with a or b
}
```

### Bad
```js
var items = ['a', 'b', 'c'];
if (items[1] === 'a' || items[1] === 'b') {
  // Do some stuff with a or b
}
```

Variable naming
---------------
All variables should be semantically named for the context they are being used and in a camelCase format. Additionally, if the variable is a boolean for a conditional, it is preferred to use an `is` or `has` prefix.

For jQuery collections, it is preferred that you prefix them with `$`s.

***Single letter variables are reserved for loop counters.***

```js
var $divs = $html.find('div');
```

### Good
```js
var myNumber = 2,
    isOdd = myNumber % 2 === 1;
if (isOdd) {
  // Do some stuff with my odd number
}
```

### Bad
```js
var mightbeanumber = 2,
    o = n % 2 === 1;
if (o) {
  // Do some stuff with my mightbeanumber?
}
```

Constructor naming
------------------
Constructor functions should be named in a ProperCase format. The name itself should be semantic to its purpose.

### Good
```js
function DeploymentCategory() {
  // Logic for building a new deployment category (not actually done in UI)
}
```

### Bad
```js
function deploycat() {
  // Do I look like a cat to you boy?
}
```

Prototypal definition
---------------------
When defining a prototype, it is preferred to do it all inside of a single object literal. It allows for less repetition and cleaner code.

If you want to alias a prototypal method, you can either bind it afterwards or create a funciton which proxies to the proper method.

### Good
```js
function Cat() {
}
Cat.prototype = {
  'meow': function () {
    // Alert a meow
  },
  'purr': function () {
    // Attempt to use the Audio API
  }
};
```

### Bad
```js
function Cat() {
}
Cat.prototype.meow = function () {
  // Alert a meow
};
Cat.prototype.purr = function () {
  // Alert a meow
};
```

Condition complexity
--------------------
If there is more than one condition being checked in a statement, save the condition as a var (e.g. isANumber) and check on that.

If the one condition you are checking could be unclear, name it as a variable anyway.

### Good
```js
var isNotUpperCase = str.toUpperCase() !== str,
    isNotLowerCase = str.toLowerCase() !== str,
    isMixedCase = isNotUpperCase && isNotLowerCase;
if (isMixedCase) {
  // Do mixed case things
}
```

### Bad
```js
if ((str.toUpperCase() !== str) && str.toLowerCase() === str)) {
  // Do mixed case things
}
```

Parameter count
---------------
In synchronous functions (constructor functions included), you are limited to a maximum of 2 parameters. The first one is for one required parameter (if you have more than one, use an object and combine optional parameters into that) and optional parameters (always an object) for the second.

In asynchronous functions, you are limited to a maximum of 4 parameters. The first is for errors, the middle 2 are the same as those used for synchronous functions, and the last is for your callback.

Side note: This will make you consider whether some parameters are really required or just currently required. Additionally, this alleviates the frustration of keeping track of which parameter comes first.

### Good
```js
function createUser(params) {
  // Use params.username, params.clientId, params.password and the rest are optional
}
```

### Bad
```js
function createUser(username, clientId, password, timezone, permissions, firstName, lastName, title) {
  // Use username, clientId, and password normally but have complicated fallback logic around the last 6 parameters
}
```

Naming closures
---------------
We like to name our functions but we hate to break older browsers. If you are on the server, feel free to name your function inline.

```js
function outerFn() {
  return function innerFn () {
    // Do closure-y things
  };
}
```

Otherwise, you can create a function via
```js
function outerFn() {
  function innerFn() {
    // Do closure-y things
  }
  return innerFn;
}
```

Nesting closures
----------------
You are allowed to nest closures for up to 3 levels within the body of a function (excluding `define` and other forms of template nesting).

If you go beyond that, move to using [`async.waterfall`](https://github.com/caolan/async#waterfall).

Additionally, you are allowed to create a function and refer to it later.

However, if you must expose a variable outside of its scope to refer to it in the second function, you should be using `async.waterfall`. This habit is an anti-pattern which prevents code chunks from being re-usable and functions from being self-contained.

### Good
```js
async.waterfall([
  function firstNumber (cb) {
    cb(null, 1);
  },
  function secondNumber (one, cb) {
    var two = one + one;
    cb(null, two);
  }
], function (err, two) {
  // Do stuff with two
});
```

### Bad
```js
var one,
    two;

return firstNumber();

function firstNumber() {
  one = 1;
  return secondNumber(null);
}

function secondNumber(err) {
  two = one + one;
  cb(null, two);
}
```

Console debugging
-----------------
If you debug normally using the console, align your `console.log` to the left for easy identification and removal.

### Good
```js
function myFunc() {
  if (true) {
    if (true) {
console.log(cat, isACat);
      if (isACat) {
        // Do things with cat
      }
    }
  }
}
```

### Bad
```js
function myFunc() {
  if (true) {
    if (true) {
      console.log(cat, isACat);
      if (isACat) {
        // Do things with cat
      }
    }
  }
}
```

Loop lookups
------------
If you constantly lookup a variable within a loop definition, [localize the variable](#localizing-variables).

### Good
```js
var items = [1, 2, 3],
    i = 0,
    len = items.length;
for (; i < len; i++) {
  // Do stuff with item
}
```

### Bad
```js
var items = [1, 2, 3],
    i = 0;
for (; i < items.length; i++) {
  // Do stuff with item
}
```

TODO's and FIXME's
------------------
Use `// TODO:` all of the time. If it needs to be fixed immediately, write a TODO as well as create an issue.

Additionally, you can add additional information via hash tags (e.g. `#enhancement`)

```js
function createUser() {
  // TODO: Call API method #api
}
```

Function documentation
----------------------
If you are writing a utility that deserves documentation, write a [DocumentJS flavored DocBlock](http://javascriptmvc.com/docs.html#!DocumentJS).


Less frequents
==============

Prototypal inheritance
----------------------
Instead of doing the prototype chain, we prefer to [monkey patch](http://en.wikipedia.org/wiki/Monkey_patch)/[duck punch](http://paulirish.com/2010/duck-punching-with-jquery/) properties from one prototype to another.

You can either loop over the properties, copy over explicit methods by hand, or use a helper method like `_.extend`.

### Good
```js
// slide.js
function Slide() {
}
Slide.prototype = {
  'use': function () {
    // Do some sliding
  }
};

// waterslide.js
function Waterslide() {
  Slide.call(this);
}
var SlideProto = Slide.prototype;
Waterslide.prototype = {
  'flow': function () {
    // Flow some water
  },
  'use': SlideProto.use
};
```

### Bad
```js
// slide.js
function Slide() {
}
Slide.prototype = {
  'use': function () {
    // Do some sliding
  }
};

// waterslide.js
function Waterslide() {
  Slide.call(this);
}
Waterslide.prototype = new Slide();
Waterslide.prototype.constructor = Waterslide;
Waterslide.prototype.flow = function () {
  // Flow some water
};
```

Extending prototypes
--------------------
If you want to improve a prototype, do this in the original file or don't do it at all. This means you ***DO NOT*** do it for native constructors (`Array`, `Function`, `Number`).

### NEVER
```js
Array.prototype.indexOf = function () {
  // DON'T DO THIS!!
};
```

node_modules
------------
Always keep track of any new packages via `package.json`. An extremely helpful command for this is `npm install PACKAGE --save`.


Subtle anti-patterns
--------------------
Consult my blog post on [Subtle anti patterns][antipatterns].

[antipatterns]: http://twolfson.com/2012-11-17-subtle-anti-patterns

Attribution
===========
- [Felix's Node.js Style Guide](http://nodeguide.com/style.html) - A lot of topics pulled from there
- [idiomatic.js](https://github.com/rwldrn/idiomatic.js) - Never used but browsed over
- [Nicolas Zakas](http://www.nczonline.net/) - Drove a good amount of some [Day to day](#day-to-day) topics
- [Douglas Crockford](http://www.crockford.com/) - Angry old man who loves his semicolons

License
=======
Copyright (c) 2013 Todd Wolfson
Licensed under the MIT license.