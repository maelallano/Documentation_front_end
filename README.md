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

## [Flexboxgrid](http://flexboxgrid.com/)

## JavaScript
[JavaScript](http://devdocs.io/javascript/)

### Array
Exemple on how to declare an array + what does the method ".length" does:
```js
var fruits = ['Apple', 'Banana'];

console.log(fruits.length);
// 2
```
[Array](http://devdocs.io/javascript/global_objects/array)

### Boolean
[Boolean](http://devdocs.io/javascript/global_objects/boolean)
### Classes
[Classes](http://devdocs.io/javascript/global_objects/classes)
### Date
[Date](http://devdocs.io/javascript/global_objects/date)
### JSON
[JSON](http://devdocs.io/javascript/global_objects/json)
### Math
[Math](http://devdocs.io/javascript/global_objects/math)
### Number
[Number](http://devdocs.io/javascript/global_objects/number)
### Operators
[Operator](http://devdocs.io/javascript/global_objects/operator)
### RegExp
[RegExp](http://devdocs.io/javascript/global_objects/regexp)
### String
[String](http://devdocs.io/javascript/global_objects/string)











