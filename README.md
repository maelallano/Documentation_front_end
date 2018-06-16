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

[Math Docs](http://devdocs.io/javascript/global_objects/math)

### Number

Here's a list of some number's methods:

[Number Docs](http://devdocs.io/javascript/global_objects/number)

### Operators

Here's a list of some operators's methods:

[Operator Docs](http://devdocs.io/javascript/global_objects/operator)

### RegExp

Here's a list of some regExp's methods:

[RegExp Docs](http://devdocs.io/javascript/global_objects/regexp)

### String

Here's a list of some string's methods:

[String Docs](http://devdocs.io/javascript/global_objects/string)











