---
description: HyperText Markup Language
---

# HTML

Структура

![](<../../.gitbook/assets/изображение (2) (1).png>)

## Sample

```markup
<!DOCTYPE html>
<html>
 <head>
   <title>!DOCTYPE</title>
   <meta charset="utf-8">
   <meta name="author" content="John Doe"> 
   <meta name="description" content="where i will see it?">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
 </head>
 <body>
 <header>WHat mean "header" tag?</header>
    <h1>This is h1</h1>
  	<h2>This is h2</h2>
  	<h3>I still need to.. (h3)</h3>
  	<p>some text</p>
  	<noscript>Sorry, your browser does not support JavaScript!</noscript>
 </body> 
</html>
```

[https://www.w3schools.com/tags/tag\_head.asp](https://www.w3schools.com/tags/tag\_head.asp)

[https://www.w3schools.com/tags/ref\_keyboardshortcuts.asp](https://www.w3schools.com/tags/ref\_keyboardshortcuts.asp)

### Tags

The first thing to say about **unpaired tags** is that they have _no content_.

Most common tags:

```
<a>  — anchor;

<b>  — bold;

<hr> — horizontal rule;

<ol> — ordered list;

<ul> — unordered list;

<li> — list item;
```

[https://www.w3schools.com/tags/default.asp](https://www.w3schools.com/tags/default.asp)

[https://www.w3schools.com/tags/](https://www.w3schools.com/tags/)

### Audio tag

used to embed audio content into web pages

```
<audio src="media/example.mp3"></audio>
```

using a nested `<source>` tag and the same audio recording in different formats:

```
<audio>
  <source src="media/example.mp3" type="audio/mpeg">
  <source src="media/example.ogg" type="audio/ogg">
</audio>
```

displays the audio player control interface (playback buttons, pause, volume)

```
<audio controls src="media/example.mp3"></audio>
```

most commonly used attributes:

* `src` indicates the path to the file that's played
* `controls` displays the audio player control interface (playback buttons, pause, volume)
* `autoplay` is responsible for automatic playback of the file immediately after the page is loaded
* `loop` cycles the audio file
* `muted` mutes the sound when playing an audio file

![](<../../.gitbook/assets/image (13).png>)

### Attributes

The syntax of HTML attributes is also simple:\
each consists of **names** and **values**. The following example shows the syntax of attributes.

```markup
<tag_name atr_name="atr_value"> </tag_name>
//life examples
<a href="https://hyperskill.org">The link</a>
<img src="image.png">
<h1 id="title">Good Morning!</h1>
```

all list - [https://www.w3schools.com/tags/ref\_attributes.asp](https://www.w3schools.com/tags/ref\_attributes.asp)

#### Some examples

`enctype` — encoding type.\
`http-equiv` — HTTP equivalent.

### id attribute <a href="#id-attribute" id="id-attribute"></a>

* When creating a unique name, you can use only Latin alphabet characters (A-Z, a-z), numbers, hyphens, and underscores. For example, names `Navbar`, `nav_item` and `margin-b-40` will be correct.
* The `id` name should not contain spaces. That is, names like `our products` will not be valid.
* The `id` can be used for only one element; you will not be able to work with multiple elements that have identifiers with the same name.
* Identifiers are case-sensitive: `id="FirstHeader"` and `id="firstheader"` are different identifiers.

### class attribute <a href="#class-attribute" id="class-attribute"></a>

When you need to give many different elements the same look, `class` attribute comes in handy. As a value, it takes any name you come up with. Unlike the `id` attribute, a web page can have many elements with the same value for the `class` attribute. Consider an example:

```markup
<h1 class="blue">Desired job:</h1>
<p class="blue">Frontend developer</p>
<h2 class="blue">My skills:</h2>
<p class="blue">I know HTML and CSS</p>
```

You can apply several classes to one element. To do this, you just need to write the names of the classes separated by a space. It will look like this.

```
<p class="black big-text">Hi!</p>
```

In this example, the p element has two classes at once: `black` and `big-text`.

## Block-level Elements

**Block-level elements** are mostly used to create the structure of web pages or logically divide an HTML document into parts.\
[https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level\_elements#Elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level\_elements#Elements)

![](<../../.gitbook/assets/изображение (6).png>)

![](<../../.gitbook/assets/изображение (7).png>)

In HTML5, however, the elements are not just divided into block-level and inline, but also grouped by meaning and purpose, representing **categories of content**.

## Inline Elements

They can contain only data and other inline items. The exception to this rule is the `<a>` tag which can also contain block-level elements.

Before and after, the browser doesn't make a line break. Take a look at the behavior of inline elements and compare it with that of block-level elements:

![](<../../.gitbook/assets/изображение (8).png>)

## External CSS

CSS styles written in a separate file are called **External Style Sheets**. To include External Style Sheets in an HTML document, use an unpaired `<link>` tag.\
The `href` attribute specifies the file's address, and the `rel` attribute with the `stylesheet` value tells the browser that we are connecting styles and not something else.

```markup
    <link rel="stylesheet" href="style.css">
```

## Internal CSS

CSS styles can be written directly in HTML markup instead of a separate file. Such sets of styles are usually called **Internal Style Sheets**. They are wrapped in a paired `<style>` tag and must be located inside `<head>`

```markup
<head>
    <meta charset="utf-8">
    <title>Connecting Internal CSS to HTML</title>
    <style>
      There should be a CSS code here
    </style>
  </head>
```

### Connecting JavaScript <a href="#connecting-javascript-to-html" id="connecting-javascript-to-html"></a>

```markup
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Connecting JavaScript to HTML</title>
  </head>
  <body>
    <script src="assets/js/main.js"></script>
  </body>
</html>
```

### DOM <a href="#briefly-about-dom" id="briefly-about-dom"></a>

**DOM** (**Document Object Model)** is the representation of an HTML document as a tree structure that various programs can work with.

![](<../../.gitbook/assets/image (11).png>)

## Fonts

```
<head>
    <link href="https://fonts.googleapis.com/css2?family=Raleway:ital,wght@1,200&display=swap" 
          rel="stylesheet">
  </head>
```

## Comments

Comments can be used anywhere on the page **except** the `<title>` tag.

```
<!-- Any text -->
```
