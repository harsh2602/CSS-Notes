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
    color: inherit;
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
<p class="introduction">Hello world</p>
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
margin: auto;
```

This only works for horizontal margin. Setting top/bottom margin to auto is equivalent to setting it to 0px.

This only works on elements with an explicit width. Block elements will naturally grow to fill the available horizontal space, so we need to give our element a width in order to center it.

## Flow Layouts

Default mode.
Has `display` value of either `block`, `inline` or `inline-block`.

examples:

- block: `<div>, <p>`
- inline: `<a>, <strong>,`
  _Special Elements:_ `<img>, <button>`

NOTE: For images wrapped inside a div, it is possible that the height is more than the image height. The reason for this extra “magic space” is that the browser treats inline elements as if they're typography. It makes sense that with text, you'd want a bit of extra space, so that the lines in a paragraph aren't crammed in too tightly.

There are two ways we can fix this problem:

1. Set images to display: block — if you're noticing this problem, there's a good chance your images aren't interspersed with text, so setting them to display as blocks makes sense.

2. Set the line-height on the wrapping div to 0:

```
<div>
  <img alt="Cat licking itself" src="/course-materials/cat-300px.jpg" style="width: 300px;">
</div>
```

Inline elements can line-wrap.

Essentially, inline-block allows you to drop a block element into an inline context. Another way to phrase this: it's an element that internally acts like a block element, but externally acts like an inline element. The parent container will treat it as an inline element, since it's external. But the element itself can be styled like a block.

Inline-block elements don't `line-wrap`.

## Width Algorithms

When we use percentage-based widths, those percentages are based on the parent element's content space. If the body tag makes 400px of space available, any child with 100% width will become 400px wide, regardless of any other circumstances.

Block elements have a default width value of auto, not 100%. width: auto works very similar to margin: auto; it's a hungry value that will grow as much as it's able to, but no more.

It's a subtle but important distinction: by default, block elements have dynamic sizing. They're context-aware.

-`min-content`: When we set `width: min-content`, we're specifying that we want our content to become as small as it can, based on the child contents. 

-`max-content`: The element's width will be the smallest value that contains the content, without breaking it up

-`fit-content`: like min-content and max-content, the width is based on the size of the children. If that width can fit within the parent container, it behaves just like max-content, not adding any line-breaks.