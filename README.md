# Reset css

```css
html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed, 
figure, figcaption, footer, header, hgroup, 
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
	margin: 0;
	padding: 0;
	border: 0;
	font-size: 100%;
	font: inherit;
	vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure, 
footer, header, hgroup, menu, nav, section {
	display: block;
}
body {
	line-height: 1;
}
ol, ul {
	list-style: none;
}
blockquote, q {
	quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
	content: '';
	content: none;
}
table {
	border-collapse: collapse;
	border-spacing: 0;
}
```

# Responsive

```css

//mobile S
@media (min-width: 320px) {
	
}

//mobile M
@media (min-width: 375px) {
	
}

//mobile L
@media (min-width: 425px) {
	
}

//tablet
@media (min-width: 768px) {
	
}

//laptop
@media (min-width: 1024px) {
	
}

//laptop L
@media (min-width: 1440px) {
	
}
```

# meta

```html
<meta name="viewport" content="width=device-width,initial-scale=1">
<meta http-equiv="X-UA-Comptatible" content="ie=edge">
```

# Documentation BEM

* Block
* Element `__`
* Modifier(s) `--`

```html
<header class="header">
  <nav class="headerNav">
    <ul class="headerNav">
      <li class="headerNav__item">
        <a href="/a-propos" class="headerNav__itemLink">
          A propos
        </a>
      </li>
      <li class="headerNav__item">
        <a href="/home" class="headerNav__itemLink headerNav__itemLink--isActive">
          Accueil
        </a>
      </li>
      <li class="headerNav__item">
        <a href="/account" class="headerNav__itemLink headerNav__itemLink--isDisabled">
          Mon compte
        </a>
      </li>
    </ul>
  </nav>
</header>
```

```scss
$bptablet: 768px;
$bpdesktop: 1024px;

@mixin bp(val) {
  @media (min-width: #{val}) {
    @content;
  }
}
.headerNav {
  display: flex;
  justify-content: space-between;
  @include bp($bptablet) {
    flex-direction: column;
  }
  &--xmas {
    background: red;
  }
  &__item {
    list-style: none;
  }
  &__itemLink {
    color: #fff;
    text-decoration: none;
    &--isDisabled {
      color: grey;
    }
    &--isActive {
      color: green;
    }
  }
}
```

# Psuedo attribut ::after & ::before

Les pseudos attributs `before`et `after` sont essentiellment utilisés pour
ajouter des éléments à votre Dom pour décorer sans que cela ait un impact sur
le référencement ou votre HTML.

### **ATTENTION**

* Il est obligatoire d'avoir un `content: ''` afin que vos after / before s'affichent.
* Vous pouvez leur donnez une taille, une position (absolute par rapport à son parent)
* essentiellment utilisé pour de la décoration.  

```HTML
<section class="cover">
  <h2 class="cover__title">Présentation</h2>
</section>
```

```css
.cover {
  &__title {
    font-size: 24px;
    color: #bbb;
    text-align: center;
    position: relative;
    &::before,
    &::after {
      content: '';
      position: absolute;
      top: 0;
      display: block;
      width: 50px;
      height: 50px;
      background: green;
    }
    &::before {
      left: 0;
    }
    &::after {
      right: 0;
    }
  }
}
```
## Why SCSS is better than CSS with BEM

```CSS
.nav {

}
.nav__list {

}
.nav__list__item {

}
.nav__link {

}
.nav__link--active {

}
```

## Les unités

### REM

L'unité de mesure REM est basée sur la taille de l'élément racine du HTML.
Par défaut, la taille du `<html>` est sde 16px, ce qui veut dire que `1rem = 16px`.
Pour éviter de devoir faire des calculs afin de respecter les tailles relatives à votre
maquette, vous pouvez ré-écrire cette `font-size` afin que `1rem = 10px`

Les proportions et tailles vont se scaler en fonction du zoom de la page.

```css
  html {
    font-size: 62,5%;
  }

  .mainTitle {
    font-size: 2.4rem;
  }

  .cover {
    width: 32rem;
  }

```

### EM

Le `EM` à contrario du `REM` se base quant à lui sur la taille de son parent direct (pas son grand-parent).

```css
.cover {
  font-size: 16px
  &__title {

  }
}
```

## [Flexboxgrid Docs](http://flexboxgrid.com/)

## JavaScript
[JavaScript Docs](http://devdocs.io/javascript/)

### Array
Exemple on how to declare an array + what does the method ".length" does:
```js
var fruits = ['Apple', 'Banana'];

console.log(fruits.length);
// 2
```

Here's a list of some array's methods:

* filter() => 
```js
var words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter(word => word.length > 6);

console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]
```

* find() =>
```js
var array1 = [5, 12, 8, 130, 44];

var found = array1.find(function(element) {
  return element > 10;
});

console.log(found);
// expected output: 12
```

* indexOf() =>
```js
var beasts = ['ant', 'bison', 'camel', 'duck', 'bison'];

console.log(beasts.indexOf('bison'));
// expected output: 1

// start from index 2
console.log(beasts.indexOf('bison', 2));
// expected output: 4

console.log(beasts.indexOf('giraffe'));
// expected output: -1
```

* shift() =>
```js
var array1 = [1, 2, 3];

var firstElement = array1.shift();

console.log(array1);
// expected output: Array [2, 3]

console.log(firstElement);
// expected output: 1
```

* splice() =>
```js
var months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb');
// inserts at 1st index position
console.log(months);
// expected output: Array ['Jan', 'Feb', 'March', 'April', 'June']

months.splice(4, 1, 'May');
// replaces 1 element at 4th index
console.log(months);
// expected output: Array ['Jan', 'Feb', 'March', 'April', 'May']
```

* unshift() =>
```js
var array1 = [1, 2, 3];

console.log(array1.unshift(4, 5));
// expected output: 5

console.log(array1);
// expected output: Array [4, 5, 1, 2, 3]
```

[Array Docs](http://devdocs.io/javascript/global_objects/array)

### Boolean

Here's a list of some boolean's methods:

* toString() =>
```js
var flag1 = new Boolean(true);

console.log(flag1.toString());
// expected output: "true"

var flag2 = new Boolean(1);

console.log(flag2.toString());
// expected output: "true"
```

* valueOf() =>
```js
var x = new Boolean();

console.log(x.valueOf());
// expected output: false

var y = new Boolean("Mozilla");

console.log(y.valueOf());
// expected output: true
```

[Boolean Docs](http://devdocs.io/javascript/global_objects/boolean)
### Classes

Here's a list of some classes's methods:

* constructor() =>
```js
class Polygon {
  constructor() {
    this.name = "Polygon";
  }
}

var poly1 = new Polygon();

console.log(poly1.name);
// expected output: "Polygon"
```

* extends() =>
```js
class formatDate extends Date {
  constructor(dateStr) {
    super(dateStr);

  }

  getFormattedDate() {
    var months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun',
                  'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];

    return `${this.getDate()}-${months[this.getMonth()]}-${this.getFullYear()}`;
  }
}

console.log(new formatDate('August 19, 1975 23:15:30').getFormattedDate());
// expected output: "19-Aug-1975"
```

* static() =>
```js
class StaticMethodCall {
  constructor() {
    console.log(StaticMethodCall.staticMethod());
    // expected output: "static method has been called."
  }

  static staticMethod() {
    return 'static method has been called.';
  }
}

new StaticMethodCall();
```

[Classes Docs](http://devdocs.io/javascript/global_objects/classes)

### Date

Here's a list of some date's methods:

* getFullYear() =>
```js
var moonLanding = new Date('July 20, 69 00:20:18');

console.log(moonLanding.getFullYear());
// expected output: 1969
```

* now() =>
```js
// this example takes 2 seconds to run
var start = Date.now();

console.log("starting timer...");
// expected output: starting timer...

setTimeout(function() {
  var millis = Date.now() - start;

  console.log("seconds elapsed = " + Math.floor(millis/1000));
  // expected output : seconds elapsed = 2
}, 2000);
```

* parse() =>
```js
var unixTimeZero = Date.parse('01 Jan 1970 00:00:00 GMT');
var javaScriptRelease = Date.parse('04 Dec 1995 00:12:00 GMT');

console.log(unixTimeZero);
// expected output: 0

console.log(javaScriptRelease);
// expected output: 818035920000
```

* FullYear() =>
```js
var event = new Date('August 19, 1975 23:15:30');

event.setFullYear(1969);

console.log(event.getFullYear());
// expected output: 1969

event.setFullYear(0);

console.log(event.getFullYear());
// expected output: 0
```

* UTC() =>
```js
var utcDate1 = new Date(Date.UTC(96, 1, 2, 3, 4, 5));
var utcDate2 = new Date(Date.UTC(0, 0, 0, 0, 0, 0));

console.log(utcDate1.toUTCString());
// expected output: Fri, 02 Feb 1996 03:04:05 GMT

console.log(utcDate2.toUTCString());
// expected output: Sun, 31 Dec 1899 00:00:00 GMT
```

* valueOf() =>
```js
var date1 = new Date(Date.UTC(96, 1, 2, 3, 4, 5));

console.log(date1.valueOf());
// expected output: 823230245000

var date2 = new Date('02 Feb 1996 03:04:05 GMT');

console.log(date2.valueOf());
// expected output: 823230245000
```

[Date Docs](http://devdocs.io/javascript/global_objects/date)

### JSON

Here's a list of some JSON's methods:

* parse() =>
```js
var json = '{"result":true, "count":42}';
obj = JSON.parse(json);

console.log(obj.count);
// expected output: 42

console.log(obj.result);
// expected output: true
```

* stringify() =>
```js
console.log(JSON.stringify({ x: 5, y: 6 }));
// expected output: "{"x":5,"y":6}"

console.log(JSON.stringify([new Number(3), new String('false'), new Boolean(false)]));
// expected output: "[3,"false",false]"

console.log(JSON.stringify({ x: [10, undefined, function(){}, Symbol('')] }));
// expected output: "{"x":[10,null,null,null]}"

console.log(JSON.stringify(new Date(2006, 0, 2, 15, 4, 5)));
// expected output: ""2006-01-02T15:04:05.000Z""
```

[JSON Docs](http://devdocs.io/javascript/global_objects/json)

### Math

Here's a list of some math's methods:

* abs() =>
```js
function difference(a, b) {
  return Math.abs(a - b);
}

console.log(difference(3, 5));
// expected output: 2

console.log(difference(5, 3));
// expected output: 2

console.log(difference(1.23456, 7.89012));
// expected output: 6.6555599999999995
```

* ceil() =>
```js
console.log(Math.ceil(.95));
// expected output: 1

console.log(Math.ceil(4));
// expected output: 4

console.log(Math.ceil(7.004));
// expected output: 8

console.log(Math.ceil(-7.004));
// expected output: -7
```

* floor() =>
```js
console.log(Math.floor(5.95));
// expected output: 5

console.log(Math.floor(5.05));
// expected output: 5

console.log(Math.floor(5));
// expected output: 5

console.log(Math.floor(-5.05));
// expected output: -6
```

* max() =>
```js
console.log(Math.max(1, 3, 2));
// expected output: 3

console.log(Math.max(-1, -3, -2));
// expected output: -1

var array1 = [1, 3, 2];

console.log(Math.max(...array1));
// expected output: 3
```

* floor() =>
```js
function getRandomInt(max) {
  return Math.floor(Math.random() * Math.floor(max));
}

console.log(getRandomInt(3));
// expected output: 0, 1 or 2

console.log(getRandomInt(1));
// expected output: 0
```

[Math Docs](http://devdocs.io/javascript/global_objects/math)

### Number

Here's a list of some number's methods:

* isInteger() =>
```js
function fits(x, y) {
  if (Number.isInteger(y / x)) {
    return 'Fits!';
  }
  return 'Does NOT fit!';
}

console.log(fits(5, 10));
// expected output: "Fits!"
```

* isFinite() =>
```js
function div(x) {
  if (Number.isFinite(1000 / x)) {
    return 'Number is NOT Infinity.';
  }
  return 'Number is Infinity!';
}

console.log(div(0));
// expected output: "Number is Infinity!"

console.log(div(1));
// expected output: "Number is NOT Infinity."
```

* valueOf() =>
```js
var numObj = new Number(42);
console.log(typeof numObj);
// expected output: "object"

var num = numObj.valueOf();
console.log(num);
// expected output: 42

console.log(typeof num);
// expected output: "number"
```

[Number Docs](http://devdocs.io/javascript/global_objects/number)

### Arithmetic Operators

Addition (+)
The addition operator produces the sum of numeric operands or string concatenation.

Examples
```js
// Number + Number -> addition
1 + 2 // 3

// Boolean + Number -> addition
true + 1 // 2

// Boolean + Boolean -> addition
false + false // 0

// Number + String -> concatenation
5 + 'foo' // "5foo"

// String + Boolean -> concatenation
'foo' + false // "foofalse"

// String + String -> concatenation
'foo' + 'bar' // "foobar"
```

Subtraction (-)
The subtraction operator subtracts the two operands, producing their difference.

Examples
```js
5 - 3 // 2
3 - 5 // -2
'foo' - 3 // NaN
```

Division (/)
The division operator produces the quotient of its operands where the left operand is the dividend and the right operand is the divisor.

Examples
```js
1 / 2      // returns 0.5 in JavaScript
1 / 2      // returns 0 in Java 
// (neither number is explicitly a floating point number)

1.0 / 2.0  // returns 0.5 in both JavaScript and Java

2.0 / 0    // returns Infinity in JavaScript
2.0 / 0.0  // returns Infinity too
2.0 / -0.0 // returns -Infinity in JavaScript
```

Multiplication (*)
The multiplication operator produces the product of the operands.

Examples
```js
2 * 2 // 4
-2 * 2 // -4
Infinity * 0 // NaN
Infinity * Infinity // Infinity
'foo' * 2 // NaN
```

Remainder (%)
The remainder operator returns the remainder left over when one operand is divided by a second operand. It always takes the sign of the dividend, not the divisor. It uses a built-in modulo function to produce the result, which is the integer remainder of dividing var1 by var2 — for example — var1 modulo var2. There is a proposal to get an actual modulo operator in a future version of ECMAScript, the difference being that the modulo operator result would take the sign of the divisor, not the dividend.

Examples
```js
12 % 5 // 2
-1 % 2 // -1
1 % -2 // 1
NaN % 2 // NaN
1 % 2 // 1
2 % 3 // 2
-4 % 2 // -0
5.5 % 2 // 1.5
```

Exponentiation (**)
The exponentiation operator returns the result of raising first operand to the power second operand. that is, var1var2, in the preceding statement, where var1 and var2 are variables. Exponentiation operator is right associative. a ** b ** c is equal to a ** (b ** c).

Examples
```js
2 ** 3 // 8
3 ** 2 // 9
3 ** 2.5 // 15.588457268119896
10 ** -1 // 0.1
NaN ** 2 // NaN

2 ** 3 ** 2 // 512
2 ** (3 ** 2) // 512
(2 ** 3) ** 2 // 64
To invert the sign of the result of an exponentiation expression:

-(2 ** 2) // -4
To force the base of an exponentiation expression to be a negative number:

(-2) ** 2 // 4
```

Increment (++)
The increment operator increments (adds one to) its operand and returns a value.

If used postfix, with operator after operand (for example, x++), then it returns the value before incrementing.
If used prefix with operator before operand (for example, ++x), then it returns the value after incrementing.

Examples
```js
// Postfix 
var x = 3;
y = x++; // y = 3, x = 4

// Prefix
var a = 2;
b = ++a; // a = 3, b = 3
```

Decrement (--)
The decrement operator decrements (subtracts one from) its operand and returns a value.

If used postfix (for example, x--), then it returns the value before decrementing.
If used prefix (for example, --x), then it returns the value after decrementing.

Examples
```js
// Postfix 
var x = 3;
y = x--; // y = 3, x = 2

// Prefix
var a = 2;
b = --a; // a = 1, b = 1
```

Unary negation (-)
The unary negation operator precedes its operand and negates it.

Examples
```js
var x = 3;
y = -x; // y = -3, x = 3

//unary negation operator can convert non-numbers into a number
var x = "4";
y = -x; // y = -4
```

[Operator Docs](http://devdocs.io/javascript/global_objects/operator)

### RegExp

The RegExp constructor creates a regular expression object for matching text with a pattern.

```js
var regex1 = /\w+/;
var regex2 = new RegExp('\\w+');

console.log(regex1);
// expected output: /\w+/

console.log(regex2);
// expected output: /\w+/

console.log(regex1 === regex2);
// expected output: false
```

[RegExp Docs](http://devdocs.io/javascript/global_objects/regexp)

### String

Here's a list of some string's methods:

* includes() =>
```js
var str = 'To be, or not to be, that is the question.';

console.log(str.includes('To be'));       // true
console.log(str.includes('question'));    // true
console.log(str.includes('nonexistent')); // false
console.log(str.includes('To be', 1));    // false
console.log(str.includes('TO BE'));       // false
```

* indexOf() =>
```js
'Blue Whale'.indexOf('Blue');     // returns  0
'Blue Whale'.indexOf('Blute');    // returns -1
'Blue Whale'.indexOf('Whale', 0); // returns  5
'Blue Whale'.indexOf('Whale', 5); // returns  5
'Blue Whale'.indexOf('Whale', 7); // returns -1
'Blue Whale'.indexOf('');         // returns  0
'Blue Whale'.indexOf('', 9);      // returns  9
'Blue Whale'.indexOf('', 10);     // returns 10
'Blue Whale'.indexOf('', 11);     // returns 10
```

* length() =>
```js
var x = 'Mozilla';
var empty = '';

console.log('Mozilla is ' + x.length + ' code units long');
/* "Mozilla is 7 code units long" */

console.log('The empty string has a length of ' + empty.length);
/* "The empty string has a length of 0" */
```

* match() =>
```js
var str = 'For more information, see Chapter 3.4.5.1';
var re = /see (chapter \d+(\.\d)*)/i;
var found = str.match(re);

console.log(found);

// logs [ 'see Chapter 3.4.5.1',
//        'Chapter 3.4.5.1',
//        '.1',
//        index: 22,
//        input: 'For more information, see Chapter 3.4.5.1' ]

// 'see Chapter 3.4.5.1' is the whole match.
// 'Chapter 3.4.5.1' was captured by '(chapter \d+(\.\d)*)'.
// '.1' was the last value captured by '(\.\d)'.
// The 'index' property (22) is the zero-based index of the whole match.
// The 'input' property is the original string that was parsed.
```

* repeat() =>
```js
'abc'.repeat(-1);   // RangeError
'abc'.repeat(0);    // ''
'abc'.repeat(1);    // 'abc'
'abc'.repeat(2);    // 'abcabc'
'abc'.repeat(3.5);  // 'abcabcabc' (count will be converted to integer)
'abc'.repeat(1/0);  // RangeError

({ toString: () => 'abc', repeat: String.prototype.repeat }).repeat(2);
// 'abcabc' (repeat() is a generic method)
```

* replace() =>
```js
var str = 'Twas the night before Xmas...';
var newstr = str.replace(/xmas/i, 'Christmas');
console.log(newstr);  // Twas the night before Christmas...
```

* slice() =>
```js
var str1 = 'The morning is upon us.', // the length of str1 is 23.
    str2 = str1.slice(1, 8),
    str3 = str1.slice(4, -2),
    str4 = str1.slice(12),
    str5 = str1.slice(30);
console.log(str2); // OUTPUT: he morn
console.log(str3); // OUTPUT: morning is upon u
console.log(str4); // OUTPUT: is upon us.
console.log(str5); // OUTPUT: ""
```

* split() =>
```js
function splitString(stringToSplit, separator) {
  var arrayOfStrings = stringToSplit.split(separator);

  console.log('The original string is: "' + stringToSplit + '"');
  console.log('The separator is: "' + separator + '"');
  console.log('The array has ' + arrayOfStrings.length + ' elements: ' + arrayOfStrings.join(' / '));
}

var tempestString = 'Oh brave new world that has such people in it.';
var monthString = 'Jan,Feb,Mar,Apr,May,Jun,Jul,Aug,Sep,Oct,Nov,Dec';

var space = ' ';
var comma = ',';

splitString(tempestString, space);
splitString(tempestString);
splitString(monthString, comma);
```

* trim() =>
```js
var orig = '   foo  ';
console.log(orig.trim()); // 'foo'

// Another example of .trim() removing whitespace from just one side.

var orig = 'foo    ';
console.log(orig.trim()); // 'foo'
```

* valueOf() =>
```js
var x = new String('Hello world');
console.log(x.valueOf()); // Displays 'Hello world'
```

[String Docs](http://devdocs.io/javascript/global_objects/string)
