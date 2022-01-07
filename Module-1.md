## Buil-in Delcarations and Inheritance
The browser has default css settings. e.g. in Chrome 86 [user-stylesheet](https://source.chromium.org/chromium/chromium/src/+/master:third_party/blink/renderer/core/html/resources/html.css)

```css
a {
  color: -webkit-link;
  cursor: pointer;
  text-decoration: underline;
}
```


## Inheritance

Certain CSS properties inherit for example: `color`. Certain do not e.g. `border`.

[List of inheritable properties](https://www.sitepoint.com/css-inheritance-introduction/#list-css-properties-inherit)

Even for inhertiable properties it is possible to override it by using `inherit` value on the property.

```html
<p style="color: red;">
  This is a red paragraph with <a href="#">another link</a>.
</p>

<style>
a {
  color: inherit
}
</style>
```

Above inherits the color from the parent i.e. `red`.

## The Cascade

It means that if we declare the value for a property and then override it later in the stylesheet, the last property takes effect.

```html
<style>
  p {
    font-weight: bold;
    color: hsl(0deg 0% 10%);
  }
  .introduction {
    color: violet;
  }
</style>
<p class="introduction">
  Hello world
</p>
```

color for `Hello World` is `violet`.

## Directions

1. Block: top to bottom
2. Inline: Left to right(english language type)

```css
p {
  display: block;
  margin-block-start: 1em; // top
  margin-block-end: 1em; // bottom
  margin-inline-start: 0px; // left
  margin-inline-end: 0px; // right
}
```

## The Box Model

By default browser is `content-box` which can be overridden by:

```css
box-sizing: border-box;
```

#### Padding

It is the inner space in the content area

#### Units

Units can be in px, rem, em

px - for padding, margin & border
rem - font-size

## Border

Valid border has to have atleast the border-style. If we don't specify a border color, it'll use the font's color by default.

```css
.good {
  /* 🙆‍♀️ Will produce a black, 3px-thick border */
  border: solid;
  border-radius: 25px; // can be used in different ways
}
```

#### Outline

The core difference is that outline doesn't affect layout. Outline is kinda more like box-shadow; it's a cosmetic effect draped over an element, without nudging it around, or changing its size.

## Margin

Margin increases the space around an element, giving it some breathing room.

- Margin can have negatives.

##### Auto Margins

The auto value seeks to fill the maximum available space.

```css
margin: auto
```

This only works for horizontal margin. Setting top/bottom margin to auto is equivalent to setting it to 0px.

This only works on elements with an explicit width. Block elements will naturally grow to fill the available horizontal space, so we need to give our element a width in order to center it.
