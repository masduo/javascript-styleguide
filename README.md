# JustPark Javascript styleguide

- Line length
- Commas
- Semicolons
- Whitespace
- Blocs
- Comments
- Strings
- Operators
- Dynamic
- Hoising
- Type conversion
- Numbers
- Undefined, null
- Arrays
- Conditionals
- Properties
- Functions
- Hoisting
- First class citizern
- Objects
- Classes
- Constructors
- Accessors
- Inheritance
- Modules
- Encapsulation
- Events
- Garbage collection
- Promisses
- Callbacks
- Browser
- Naming conventions

## Line length

- Max line length should be 80 characters

## Commas

- Do not use leading commas.
- Don't leave additional trailing commas.
- Commas must be at the end of the last line.

```JavaScript
// Bad
var cars = [
  'Volkswagen'
, 'Renault'
, 'Mercedes'
, 'Porsche'
];

// Bad
var cars = [
  'Volkswagen',
  'Renault',
  'Mercedes',
  'Porsche',
];

// Bad
var cars = [
  'Volkswagen',
  'Renault',
  'Mercedes'
  ,
  'Porsche'
];

// Good
var cars = [
  'Volkswagen',
  'Renault',
  'Mercedes',
  'Porsche'
];
```

## Semicolons

- Each statement must end with a semicolon.
- Write only one statement per line.
- It's a good practice to put semicolon before parenthesis when using anonymous functions

```JavaScript
// Bad
var car = 'Volkswagen'
console.log(car)

// Bad
var car = 'Volkswagen'; console.log(car);

// Good
var car = 'Volkswagen';
console.log(car);

// Good
;(function() {
  var car = 'Volkswagen';
  console.log(car);
});

```

## Whitespaces

- Use 2 space indent, not tabs.

```JavaScript
// Bad
function() {
	var car = 'Volkswagen';
}

// Good
function() {
  var car 'Volkswagen';
}
```

- No linebreak at the begining of files.
- Single linebrear at the end of files.

```JavaScript
// Bad
function(global) {
  // ...
}(this);
```

```JavaScript
// Bad
function(global) {
  // ...
}(this);↵
↵
```

```JavaScript
// Good
function(global) {
  // ...
}(this);↵
```

- One space before leading bracket.
- No space after function name, or function keyword (when anonymous function).
- One space after keywords (`if`, `else`).

```JavaScript
// Bad
function(){
  // ...
}

// Bad
function () {
  // ...
}

// Good
function() {
  // ...
}

// Bad
if(car) {
  // ...
}

// Good
if (car) {
  // ...
}

```

- Space between operators and operands but not inside parenthesis.

```JavaScript
// Bad
var result=(value+number)*2;

// Bad
var result = (  value + number ) * 2;

// Good
var result = (value + number) * 2;
```

- Leave a blank between blocks and statements.
- Don't leave a space between object properties (if they are not functions)
- Don't insert meaningless line breaks

```JavaScript
// Bad
function(car) {
  var color = car.color;
  if (color === 'red') {
    return 'Car is red';
  }
  return 'Car is not red';
}

// Bad
function(car) {
  var color = car.color;
  
  if (color === 'red') {
    
    return 'Car is red';
    
  }
  
  return 'Car is not red';
}

// Bad
function(car) {
  var color = car.color;
  
  if (color === 'red') {
    return 'Car is red';    
  }
  
  
  return 'Car is not red';
}

// Good
function(car) {
  var color = car.color;
  
  if (color === 'red') {
    return 'Car is red';
  }
  
  return 'Car is not red';
}

// Bad
var object = {
  foo: function() {
    // ...
  },
  bar: function() {
    // ...
  }
};
return object;

// Good
var object = {
  foo: function() {
    // ...
  },
  
  bar: function() {
    // ...
  }
};

return object;

// Bad
var object = {
  foo: 'some property',

  bar: 'other property',

  other: 'yes another property'
}

// Good
var object = {
  foo: 'some property',
  bar: 'other property',
  other: 'yes another property'
}
```

- Don't leave white spaces at the end of lines. (`~` for whitespace)
- Empty lines should not have white spaces.

```JavaScript
// Empty spaces are represented by ~

// Bad
function(car) {
  var color = car.color;
~~
  if (color === 'red') {
    return 'Car is red';
  }
~~
  return 'Car is not red';
}

// Bad
function() {~
  var color = car.color;~~

  if (color === 'red') {
    return 'Car is red';~
  }

  return 'Car is not red';
}

// Good
function() {
  var color = car.color;

  if (color === 'red') {
    return 'Car is red';
  }

  return 'Car is not red';
}
```

- Use leading dots for long methods chains.

```JavaScript
// Bad
$('#car').find('.details').append('4 seats').highlight().show();

// Good
$('#car').find('.details')
  .append('4 seats')
  .highlight()
  .show();
```

## Blocks

- Don't write single line blocks.
- Always use brackets.

```JavaScript
// Bad
if (car.color === 'red') return 'Car is red';

// Bad
if (car.color === 'red') { return 'Car is red'; }

// Bad
if (car.color === 'red')
  return 'Car is red';

// Good
if (car.color === 'red') {
  return 'Car is red';
}
```

- Put `else` statement on the same line as the closing bracket of the `if` statement.

```JavaScript
// Bad
if (car.color === 'red') {
  // ...
}
else {
  // ...
}

// Good
if (car.color === 'red') {
  // ...
} else {
  // ...
}
```

## Comments

- Follow [JSDoc](http://usejsdoc.org) style for documentation.
- Use `/** ... */` for multiline comments.
- The code should be clear enough not to need comments.
- Put an empty line before comments.

```JavaScript
// Bad
var car = new Car();
// Do some complex operation with car
car.someComplexOperation(...);

// Good
var car = new Car();

// Do some complicated operation with car
car.someComplexOperation(...);
```

- Use `// FIXME:` to annotate problems

```JavaScript
function Calculator() {

  // FIXME: shouldn't use a global here
  total = 0;

  return this;
}
```

- Use `// TODO:` to annotate solutions to problems

```JavaScript
function Calculator() {

  // TODO: total should be configurable by an options param
  this.total = 0;

  return this;
}
```

## Strings

- Use single quotes for strings

```JavaScript
// Bad
var color = "red";

// Good
var color = 'red';
```

- Use concatenation when the line is more than 80 characters
- If the string length is too long, use Array#join instead of concatenation.

```JavaScript
// Bad
var message = 'This is a very long message which should not be written in a single line';

// Bad
var message = 'This is a very long message which should not be \
written in a single line';

// Good
var message = 'This is a very long message which should not be ' +
  'written in a single line';
```

## Operators

- Use identity instead of equality. If needed, use explicit type conversion.

```JavaScript
var a = 20;
var b = '20';

// Bad
console.log(a == b);

// Good
console.log(a === b);

// Good
console.log(a === parseInt(b, 10));
```

- No Yoda conditions.

```JavaScript
// Bad
if ('red' === color) {
  //...
}

// Good
if (color === 'red') {
  //...
}
```
## Dynamic



## Hoisting

- Hoist variables at the top of functions.

```JavaScript
// Bad
function(color) {
  
  if (color === 'red') {
    var message = 'Car is red';
  }
  
  // ...
}

// Good
function(color) {
  var message;
  
  if (color === 'red') {
    message = 'Car is red';
  }
  
  // ...
}
```

## Type conversion

- Use explicit type conversion when converting to integer.
- Always provide the second argument when using `parseInt`.

```JavaScript
// Bad
var count = '20';
var total = count + 1;

// Bad
var count = '20';
var total = parseInt(count) + 1;

// Good
var count = '20';
var total = parseInt(count, 10) + 1;
```

## Undefined, null

## Arrays

- Instantiate new arrays using the literal notation. The constructor's signature is ambiguous as `new Array(2)` will make an array of size 2, and `new Array('2')` will make an array with the string `'2'` as value.
- JavaScript arrays are objects. Their lenght is always dynamic, thus size doesn't need to be specified.

```JavaScript
// Bad
var colors = new Array();

// Bad
var colors = [];
colors.length = 3;

// Good
var colors = [];
```

- Use standard object methods when more appropriate ([developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array))

```JavaScript

// Bad
function getCountPerBrand(cars) {
  var brands = {};
  
  for (var index = 0; index < cars.length; index++) {
    if (typeof brands[cars[index].brand] === 'undefined') {
      brands[cars[index].brand] = 0;
    }
    
    brands[cars[index].brand] = brands[cars[index].brand] + 1;
  }
  
  return brands;
}

// Good
function getCountPerBrand(cars) {
  return cars.reduce(function(brands, car) {
    if (typeof brands[car.brand] === 'undefined') {
      brands[car.brand] = 0;
    }
    
    brands[car.brand] = brands[car.brand] + 1;
    return brands;
  }, {});
}
```

## Conditionals

- Use switch statement when there are too many conditions

```JavaScript
// Bad
function getColorCoolness(color) {
  if (color === 'blue') {
    return 10;
  } else if (color === 'red') {
    return 20;
  } else if (color === 'green') {
    return 100;
  } else {
    return 5;
  }
}

// Good
function getColorCoolness(color) {
  switch(color) {
    case 'blue': return 10;
    case 'red': return 20;
    case 'green': return 100;
    default: return 5;
  }
}

// Also good
var COLORS_COOLNESS = {
  blue: 10,
  red: 20,
  green: 100
};

function getColorCoolness(color) {
  if (COLORS_COOLNESS.indexOf(color) === -1) {
    return 5;
  }
  
  return COLORS_COOLNESS[color];
}
```

- When a function can only execute with certain arguments, use a conditional at the top to immediately return.

```JavaScript
// Bad
function registerCar(car) {

  if (car) {
    // code to register the car ...
  } else {
    return;
  }
}

// Good
function registerCar(car) {
  if (!car) {
    return;
  }
  
  // code to register the car ...
}
```

## Properties

- Use dot notation for accessing properties

```JavaScript
// Bad
car['color'] = 'red';

// Good
car.color = 'red';
```

- Use brackets when accessing properties via a variable

```JavaScript
// Good
var property = 'color';
car[property] = 'red';
```

## Functions

- Functions are first class citizerns
- 

## Hoisting

## Naming conventions

- Use American English (when sensible).

```JavaScript
// Bad
function initialise(){...}

// Good
function initialize(){...}
```
