---
description: >-
  JS is a lightweight, interpreted, or just-in-time compiled programming
  language
coverY: 0
---

# 🔞 JavaScript

## Links

Styleguide - [https://github.com/airbnb/javascript](https://github.com/airbnb/javascript)&#x20;

ESLint statically analyzes your code - [https://eslint.org/](https://eslint.org)&#x20;

Online IDE - [https://replit.com/](https://replit.com/)

## Comments

### One-line comments <a href="#one-line-comments" id="one-line-comments"></a>

```javascript
console.log("Nice to see you!"); // This code outputs the message to the console
```

### Multi-line comments <a href="#multi-line-comments" id="multi-line-comments"></a>

```javascript
/*  
  The following code outputs the message to the console
  The console will display a line with the text "Hello, JS!"
*/
console.log("Hello, JS!");
```

## Variables

**declaration**\
\*\*\*\*The name of a variable can contain only letters, numbers or symbols `$` and `_` and it _cannot_ begin with a number.

JavaScript uses two keywords to create variables:

* `let` defines a **mutable variable** the value of which \_\_ can be changed as many times as needed;
* `const` declares a **constant** the value of which \_\_ cannot be changed.
* `var` - is an outdated way of declaring a variable, and we do not recommend using it.

## Data types

### _typeof_ operator <a href="#em-typeof-em-operator" id="em-typeof-em-operator"></a>

```javascript
console.log(typeof(9)); // number
console.log(typeof 9); // number
```

### _null_ <a href="#em-null-em" id="em-null-em"></a>

`null` means that the variable was explicitly assigned an empty or non-existent value. If the variable is `null`, we know that it does not contain an acceptable number, string or other data type:

```
let name = null; 
console.log(name); // null
```

### _undefined_ <a href="#em-undefined-em" id="em-undefined-em"></a>

The `undefined` value is returned when a variable was declared, but its value wasn't set. Let's consider the following example:

```javascript
let count; 
console.log(count); // undefined

let person = {
  age: 27
};
 
console.log(person.name); // undefined
```

But that's not all! The `undefined` value is also returned when a function has a missing parameter:

```javascript
function getDetails(a) {
  console.log(a);
}

getDetails(); // undefined
```

### Array

```javascript
const companies = ["Apple", "Google", "Amazon"];
companies.push("Yandex"); // add new:
companies.pop(); // delete last:
const firstPlace = companies[0] // get by index
companies.length // check length
```

## Arithmetic operators

The JavaScript programming language provides operators to perform arithmetic operations. They are called **binary** because they apply to two **operands** (objects over which the operation is performed).

* addition `+`

```javascript
console.log(12 + 26); // 38
console.log("My name is " + "John"); // My name is John
```

* subtraction `-`

```
console.log(5 - 3); // 2
```

* multiplication `*`

```
console.log(10 * 4); // 40
```

* integer division `/`

```
console.log(8 / 2); // 4
```

* remainder `%`. This operator finds the residue from the division:

```
console.log(10 % 3); // 1, because 10 divided by 3 leaves a remainder of 1
console.log(12 % 4); // 0, because 12 divided by 4 leaves no remainder
```

* exponentiation `**`

```
console.log(2 ** 3); // 8, because (2 * 2 * 2) is 8
```

### Order

The list below is sorted from the highest to the lowest precedence level:

* parentheses
* unary plus/minus
* multiplication, division
* addition and subtraction

## Boolean and logical operators

### Comparison operators <a href="#step-title" id="step-title"></a>

[**https://hyperskill.org/learn/step/8580**](https://hyperskill.org/learn/step/8580)

There are only three of them in JavaScript: logical AND (`&&`), logical OR (`||`) and NOT (`!`).

```
console.log(true && true);   // true
console.log(true && false);  // false
console.log(false && true);  // false
console.log(false && false); // false
```

`||` returns _false_ if both operands are false and _true_ in all other cases:

```
console.log(true || true);   // true
console.log(true || false);  // true
console.log(false || true);  // true
console.log(false || false); // false
```

`!` returns _false_ to true and _true_ to false:

```
console.log(!false); // true
console.log(!true);  // false
```

Among the numerical values, `0` is considered `false`, and all other numbers are true. Strings are considered true.

Expression is always calculated from left to right. `&&` returns \*\*\*\* _false_ as soon as it finds the first occurring \*\*\*\* _false_, and the operator `||` returns \*\*\*\* _true_ as soon as it sees the first \*\*\*\* _true_:

```
console.log(true || 0);      // true
console.log(false && "sun"); // false
console.log(1 || 0);         // 1
```

The priority of `!` is higher than that of `&&`, and the priority of `&&` is higher than that of `||`. If you need to change the priority, use parentheses:

```
console.log(!false && !true);   // false
console.log(!(false && !true)); // true
```

## Type conversion

### String conversion

In JS, an _implicit conversion_ will be called by the binary `+` operator when one of the operands is a string:

```javascript
"3" + 4                        // "34"
4 + ""                         // "4"
true + "detective"             // "truedetective"
"You are " + 25 + " years old" // "You are 25 years old"
```

The automatic conversion will take place regardless of the location of the operand string on the right or left side of the expression.

Remember the order of arithmetic operations. If there are several numbers before the string, these numbers will be added before the conversion:

```javascript
3 + 10 + "1" // "131", not "3101"
```

### Numeric conversion <a href="#numeric-conversion" id="numeric-conversion"></a>

When converting a string to a number, spaces and characters `\n,`  at the beginning and the end of the string are cut off. If the string turns out to be empty, the result will be `0`. The boolean type behaves as expected: `false` turns into `0`, `true` turns into `1`.

If the values ​​cannot be cast to a number, the result of the conversion will be `NaN`. For example, `Number("apple")` will return a `NaN` value, which means **Not-a-Number**. Usually, this value is returned when an operation with numbers is performed incorrectly.

The _implicit_ conversion is a little more confusing. It occurs in almost all mathematical functions and expressions:

```javascript
true + 43 // 44
3 - false // 3
10 / "5"  // 2
-true     // -1
+"85"     // 85
```

### Boolean conversion <a href="#boolean-conversion" id="boolean-conversion"></a>

The rules for using this function are simple: values that imply "empty", like `0` or an empty string `""` turn into `false`. All other values turn into `true`.

An _implicit_ conversion occurs when using logical operators (`||&&` `!`):

```javascript
!!3                      // true
0 || "hello"             // "hello"
"Master" && "Margarita"  // "Margarita"
```

## Functions

### **built-in**

Console.log() - print some text

```javascript
console.log("Learning JavaScript is easy and enjoyable!");
```

`String()`

```javascript
String(123);   // "123"
String(false); // "false"
```

`Number()`

```javascript
Number("1");    // 1
Number(" 37 "); // 37
Number("");     // 0
Number("\n3");  // 3
Number("\n");   // 0
Number("\t");   // 0
Number(true);   // 1
Number(false);  // 0
```

`Boolean()`

```javascript
Boolean(1);            // true
Boolean(0);            // false
Boolean("Am I nice?"); // true
Boolean("");           // false
```

`getElementById()`

```markup
<p id="blue-text">What's your hyper skill?</p>
<script>
  let element = document.getElementById("blue-text"); // get the element by id
</script>
```

`querySelector()`

With the `querySelector()` method it is possible to return the first document element that corresponds to the specified selector:

```
<p>What's your hyper skill?</p>
 
<script>
  let element = document.querySelector("p"); // get the element by selector
</script>
```

`querySelectorAll()`\
\*\*\*\*gets all elements that match the specified selector:

```
<p>Tell me</p>
<p>What's your hyper skill?</p>
 
<script>
  let elements = document.querySelectorAll("p"); // get elements by selector
</script>
```

### **user-defined**

**default style**

```javascript
function name(a, b) {
  var result = a + b
  return result;
};
```

#### **arrow functions** style

```javascript
const name = (a, b) => {
  const result = a + b
  return result;
};
// it could be one-line function
two = (a) => b = 2 + a;
```

* Arrow functions don't have their own bindings to [`this`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this), [`arguments`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments) or [`super`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/super), and should not be used as [methods](https://developer.mozilla.org/en-US/docs/Glossary/Method).
* Arrow functions don't have access to the [`new.target`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new.target) keyword.
* Arrow functions aren't suitable for [`call`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Function/call), [`apply`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Function/apply) and [`bind`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Function/bind) methods, which generally rely on establishing a [scope](https://developer.mozilla.org/en-US/docs/Glossary/Scope).
* Arrow functions cannot be used as [constructors](https://developer.mozilla.org/en-US/docs/Glossary/Constructor).
* Arrow functions cannot use [`yield`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/yield), within its body.

**Формальными параметрами** функции называются имена переменных в _определении функции_. Например у функции `const f = (a, b) => a - b;` формальные параметры — это `a` и `b`.

**Фактические параметры** — это то, что было _передано в функцию_ в момент вызова. Например если предыдущую функцию вызвать так `f(5, z)`, где `const z = 8`, то фактическими параметрами являются `5` и `z`. Результатом этого вызова будет число `-3`, а внутри функции на момент конкретного вызова параметр `a` становится равным `5`, а `b` становится равным `8`.

#### recursion

```javascript
const factorial = (n) => {
  if (n === 0) {
    return 1;
  }
  else {
    return n * factorial(n - 1);
  }
}

const answer = factorial(3);
```

## Objects

An **object** is a _non-primitive_ data type that represents an **unordered** collection of _properties_.A **property** is a part of the object that imitates a variable. It consists of a **key** and a **value** separated by a colon. A key can only be a string, but the value may be of any data type.

```javascript
const сountry = {
  name: "Netherlands",
  population: 17.18,
  stillExist: true,
  "friendly name": "Holland" // key could be in " " we can use whitespace between words
};
```

### Properties <a href="#properties" id="properties"></a>

To access the properties, we use a record with the object name and a dot.

```javascript
console.log(country.name); // Netherlands
console.log(country.["name"]); // Netherlands - alternative 
```

Properties can be added using the dot symbol and the `=` assignment symbol.

```
сountry.capital = "Amsterdam";
```

To delete a property, we can use the `delete` operator and a dot.

```
delete country.population;
```

### Audio Object <a href="#step-title" id="step-title"></a>

`Audio Object` can be created by using the following syntax:

```javascript
let audio = document.createElement("AUDIO");
//or
let audio = new Audio("path/to/myAudio.mp3");
```

To get access to this object, we can use the method we're already familiar with: `getElementById()`. Let's assume that our HTML `<audio>` element has the id `myAudioID`. We call the method `getElementById()` to access that element by its id:

```
let audio = document.getElementById("myAudioID");
```

#### Properties

[https://www.w3schools.com/jsref/dom\_obj\_audio.asp](https://www.w3schools.com/jsref/dom\_obj\_audio.asp)

```javascript
let audio = getElementById("myObjectID");
let src = audio.src; // "path/to/myAudio.mp3"
console.log(src);
```

The `duration` property lets us know the duration of the audio file in seconds:

```
let duration = audio.duration;
console.log(duration);
```

#### Methods

[https://www.w3schools.com/jsref/dom\_obj\_audio.asp](https://www.w3schools.com/jsref/dom\_obj\_audio.asp)

The following method is responsible for reloading the `<audio>` element:

```
audio.load();
```

The following methods are probably the most basic ones:

```
audio.play();
audio.pause();
```

## Conditional operators

### if

```javascript
let condition = true; 
 
if (condition) {
    console.log(“True!”);
}
```

### ternary operator "? :" <a href="#the-ternary-operator" id="the-ternary-operator"></a>

short version of the `if...else` block

```javascript
const getColour = colour => colour === 'white' ? 'white' : 'black';
```

## Browser events

[https://developer.mozilla.org/en-US/docs/Web/Events](https://developer.mozilla.org/en-US/docs/Web/Events)

### Mouse events <a href="#mouse-events" id="mouse-events"></a>

* `click` is the event that occurs when a user clicks on an item with the left mouse button;
* `dblclick` is responsible for events occurring after double clicking with the left mouse button;
* `contextmenu` is when a user clicks on an element with the right mouse button.

### Keyboard events <a href="#keyboard-events" id="keyboard-events"></a>

* `keydown` is the event that occurs when the user presses a key;
* `keyup` is the event that happens when the any key is released;
* `keypress` is the event that occurs when any key other than Shift, Fn, CapsLock is in the pressed position

Each browser event has an **event handler**: a code block that occurs after the event operation. When the code block is executed, we can say that we register the event handler. It is thanks to these handlers that the code can react to user actions.

```javascript
document.addEventListener("click", function() {
  console.log("There's been a browser event");
});
```

```javascript
document.getElementById("myBtn").addEventListener("keypress", function() {
  // body
});
```

### Key Codes <a href="#key-codes" id="key-codes"></a>

Javascript has a property `event.code` that allows you to get the code for the specific keyboard character. Each key has its own code which depends on its location on the keyboard:

* letter codes are composed according to a `Key<letter>` scheme;
* numeric key codes are built on the principle `Digit<number>`;
* the code for special keys is their name, for instance, `Enter` for the _Enter_ key.

Use `event.code` when you do not care about case and vice versa, use `event.key` when you care about case.

### Event handling <a href="#event-handling" id="event-handling"></a>

```javascript
document.addEventListener("keydown", function(event) {
  if (event.code == "AltRight") {
    console.log(event);
  }
});
```

```javascript
document.addEventListener("keydown", function(event) {
  if (event.key == "W") {
    console.log("W Pressed");
  }
});
```
