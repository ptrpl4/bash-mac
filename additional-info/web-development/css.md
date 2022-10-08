---
description: Cascading Style Sheets
---

# CSS

## Basic syntax

![](<../../.gitbook/assets/изображение (3) (1).png>)

CSS syntax consists of two main parts: a **selector** and a **declaration block** that is put in curly brackets.

```css
selector { property: value; }
```

[**https://qhmit.com/css/properties/**](https://qhmit.com/css/properties/)

## **Selectors**

**Selector** indicates which HTML elements the styles will be applied to.

```css
h1 { color: red; }
```

In this case, the style will apply to all `h1` elements on the page.

You can write multiple selectors separated by commas, and all styles specified in the declaration block will be applied to them.

```css
h1, p { color: red; }
```

### **class Selector**

**CSS class Selector** is useful when you need to give a lot of different elements the same look. The name of the selector is taken from the value of the `class` attribute of the desired HTML tag. A dot `.` is placed in front of it so that the browser understands that this is a class selector.

```css
.blue {
  background-color: blue;
}
```

HTML code:

```markup
<h1 class="blue">The background color of this element should be blue.</h1>
```

### id Selector

**CSS id Selector** is used if you need to work with a specific element when there are many similar elements. It takes its name from the value of the `id` attribute of the HTML tag you need. A symbol `#` is placed in front of it so that the browser understands that this is an id selector.

```css
#big {
  font-size: 30px;
}
```

HTML code:

```markup
<p id="big">The text of this paragraph will change in font size.</p>
```

### Element + Selector id/class

if HTML

```markup
<div class="white-keys">
```

�then CSS

```css
.white-keys kbd {
}
```

�

## Declaration block

Each declaration includes a CSS **property** **name** and a **value** separated from each other by a colon.

```
div {
  width: 500px;
  height: 50px;
  color: yellow;
}
```

Declaration always ends with a semicolon, and declaration blocks are surrounded by curly braces.

## Comments

```css
/* Any text */
p {
  color: blue; /* the color of the text paragraph is blue */
}
/* The styles given
   to the paragraph
   with the text 
*/
p {
  color: blue;
  background-color: black;
}
/*
h1 {
  color: #33A1D9; 
  border-top: 2px solid;
  font-size: 3em;
}
*/
```

## Colors

special **keywords** that can be used to identify colors

[https://www.w3schools.com/colors/colors\_names.asp](https://www.w3schools.com/colors/colors\_names.asp)

```css
color: red;
color: rgb(255, 255, 255);
color: #FFFF00;
```

**decimal RGB values**\
[https://www.w3schools.com/colors/colors\_rgb.asp](https://www.w3schools.com/colors/colors\_rgb.asp)

**HEX** is essentially the same as RGB, but it is recorded in the **hexadecimal** notation.

[https://www.w3schools.com/colors/colors\_hexadecimal.asp](https://www.w3schools.com/colors/colors\_hexadecimal.asp)

## Margin and padding

![](<../../.gitbook/assets/image (10) (1).png>)

There are four properties for setting margins/padding for each side of the element: top, right, bottom, left. Definitions can be stated in any CSS unit (px, em, %).

* 4 values: sides of an element in this order: top, right, bottom, left; that is, clockwise.\
  `padding: 2px 5px 10px 5px`
* 3 values: the order is top, then one property for both the right and the left side, and then the bottom.\
  `padding: 2px 5px 10px`
* 2 values: first, one property is assigned for top and bottom, then another is set for both right and left.\
  `padding: 2px 5 px`
* 1 value means that a single property applies to every side.\
  `padding: 2px`

you can also use negative values for margins: (`margin-left: -5px`).

Use **margin** when:

1\. You need to center an element. If that element has a fixed width, it will be centered horizontally by `margin: auto`

`margin: auto` will only work if the block width is set.

2\. It is necessary to make some content stand out by putting it separately without other elements touching it.

Use **padding** when:

1\. You want to increase the size of the element. Padding will increase the size to accommodate the gap.

2\. You need the element to have a background in the produced gap.

3\. You need some space around the content (see point 2 in **margin**).

## Fonts

### from HTML

```
p {
  font-family: 'Raleway', sans-serif;
}
```

### from CSS

```
@import url('https://fonts.googleapis.com/css2?family=Raleway:ital,wght@1,200&display=swap');
 
p {
  font-family: 'Raleway', sans-serif;
}
```

## Positioning Properties

[https://www.w3schools.com/cssref/pr\_class\_position.asp](https://www.w3schools.com/cssref/pr\_class\_position.asp)

Before we begin to work with positioning, it's important to note one small but very important detail. The properties discussed in the next section will not work unless the `position` property is specified for the required elements. The default value of this property is `static`.

The value can be anything but `static`. Thus, we can move an element with `position: relative;` from its original location to the one we specify with the help of the studied properties.

### examples

`left`, `right`, `top`, `bottom` will not be applied unless the position property is specified for the item.

{% tabs %}
{% tab title="top" %}
```css
div {
  position: relative; 
  top: 10px;
}
```
{% endtab %}

{% tab title="bottom" %}
```css
p {
  position: relative; 
  bottom: 5px;
}
```
{% endtab %}

{% tab title="left" %}
```css
kbd {
  position: relative; 
  left: -25px;
}
```
{% endtab %}

{% tab title="right" %}
```css
div {
  position: relative; 
  right: -2%;
}
```
{% endtab %}
{% endtabs %}
