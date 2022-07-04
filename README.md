# Baselayer CSS

Baselayer CSS is a tiny CSS toolkit to facilitate the development of user interfaces.

## Get started

### Install options

- [Download the latest version](https://github.com/mattiashaal/baselayer-css/archive/main.zip)
- Clone the repo: `git clone https://github.com/mattiashaal/baselayer-css.git`
- Install with npm: `npm install baselayer-css`

## Concept

Scoped CSS and Utility CSS together in harmony.

### Layouts for composition

### Utilities for flexibility and consistency

### Components for complex design patterns

## Docs

### Base

### Layouts

#### Frame

Frame makes its child element responsive with a set aspect ratio. Often used for media elements.

```scss
// Default settings
.frame {
  --object-fit: cover;
  --ratio: 1/1;
  --object-x: 50%;
  --object-y: 50%;
}
```

```html
<!-- Display image in 1:1 format -->
<div class="frame">
  <img src="..." alt="..." loading="lazy" />
</div>

<!-- Display image in 16:9 format -->
<div class="frame" style="--ratio: 16/9;">
  <img src="..." alt="..." loading="lazy" />
</div>
```

#### Grid

Build responsive grid systems with total layout freedom using one single class and custom properties.

```scss
// Default settings
.grid {
  --flow: row; // grid-auto-flow
  --auto-cols: auto; // grid-auto-columns
  --auto-rows: auto; // grid-auto-rows
  --cols: 1; // grid-template-columns (repeat(var(--cols), var(--cols-size)))
  --cols-size: 1fr; // grid-template-columns (repeat(var(--cols), var(--cols-size)))
  --align: normal; // align-items
  --justify: normal; // justify-items
  --place: normal; // place-content (align-content justify-content)
  --gap: 0;
}

.grid > * {
  --col: auto; // grid-column
  --row: auto; // grid-row
  --align: auto; // align-self
  --justify: auto; // justify-self
  --order: 0;
}
```

```html
<!-- A simple responsive grid from one column to four columns -->
<div
  class="grid"
  style="--cols: 1; --sm-cols: 2; --md-cols: 3; --lg-cols: 4; --gap: 1rem;"
>
  <div>...</div>
  <div>...</div>
  <div>...</div>
  <div>...</div>
</div>

<!-- A responsive grid using auto-fit -->
<div
  class="grid"
  style="--cols: auto-fit; --cols-size: minmax(min(100%, 15rem), 1fr); --gap: 1rem;"
>
  <div>...</div>
  <div>...</div>
  <div>...</div>
  <div>...</div>
</div>
```

#### Layout

Layout handles box alignment and element composition with endless flexibility using one single class and custom properties.

```scss
// Default settings
.layout {
  --flow: row; // flex-direction
  --wrap: wrap; // flex-wrap
  --align: normal; // align-items
  --place: normal; // place-content (align-content justify-content)
  --width: auto;
  --gap: 0;
}

.layout > * {
  --basis: auto; // flex-basis
  --grow: 0; // flex-grow
  --shrink: 1; // flex-shrink
  --align: auto; // align-self
  --order: 0;
  --width: auto;
  --min-width: 0;
  --max-width: none;
}
```

```html
<!-- Align items along the center of the cross axis -->
<div class="layout" style="--align: center;">
  <div>...</div>
  <div>...</div>
</div>

<!-- Align an item along the center of the cross axis -->
<div class="layout">
  <div style="--align: center;">...</div>
  <div>...</div>
</div>

<!-- Pack rows in the center of the cross axis and justify items along the center of the main axis -->
<div class="layout" style="--place: center;">
  <div>...</div>
  <div>...</div>
</div>

<!-- Pack rows at the start of the cross axis and justify items along the center of the main axis -->
<div class="layout" style="--place: flex-start center;">
  <div>...</div>
  <div>...</div>
</div>
```

#### Stack

Control the space between stacked child elements along the y-axis.

```scss
// Default settings
.stack {
  --space: var(--space-tiny);
}
```

```html
<!-- Add default spacing between stacked elements -->
<div class="stack">
  <div>...</div>
  <div>...</div>
  <div>...</div>
  <div>...</div>
</div>

<!-- Add custom spacing between stacked elements -->
<div class="stack" style="--space: 2rem;">
  <div>...</div>
  <div>...</div>
  <div>...</div>
  <div>...</div>
</div>
```

#### Switch

Switch from a single column to a multi column layout when the width of the parent element is equal the breakpoint.

```scss
// Default settings
.switch {
  --breakpoint: 0;
  --cols: 1;
  --gap: 0rem;
  --multiplier: 999;
  --trim: 0.001%;
}

.switch > * {
  --col: var(--cols);
  --grow: 0;
}
```

```html
<!-- Switch to a multi column layout when the parent width is equal to 40rem -->
<div class="switch" style="--cols: 3; --breakpoint: 40rem;">
  <div>...</div>
  <div>...</div>
  <div>...</div>
</div>
```

#### Wrap

Wrap and align content with padding.

```scss
// Default settings
.wrap {
  --width: calc(100% - var(--padding));
  --max-width: 80rem;
  --padding: clamp(2rem, 10vw, 4rem);
}
```

```html
<!-- Wrap page content with default settings -->
<div class="wrap">
  <header>...</header>
  <main>...</min>
  <footer>...</footer>
</div>

<!-- Wrap an article to a more readable length -->
<div class="wrap" style="--max-width: 40rem;">
  <article>...</article>
</div>

<!-- Wrap an element without padding -->
<div class="wrap" style="--padding: 0;">
  <div>...</div>
</div>
```

### Utilities

#### Transform

```scss
// Default settings
.u-transform {
  --rotate: 0deg;
  --scale: 1;
  --skew: 0deg;
  --origin: center;
  --translate-x: 0;
  --translate-y: 0;
  --translate-z: 0;
}
```

```html
<!-- Basic use of u-transform -->
<div class="u-transform" style="--translate-x: -50%;">...</div>
```

#### Transition

```scss
// Default settings
.u-transition {
  --property: all;
  --duration: 200ms;
  --delay: 0ms;
  --easing: cubic-bezier(0.5, 0, 0.25, 1);
}
```

```html
<!-- Basic use of u-transition -->
<div
  class="u-transition"
  style="--property: opacity; --duration: 300ms; --easing: ease-out;"
>
  ...
</div>
```

#### Breakout link

```scss
// Default settings
.u-breakout-link {
  --zi: 1;
}

// Outline values are defined in :root but can be customized
.u-breakout-link:focus::before {
  --outline-width: 0.125rem;
  --outline-type: solid;
  --outline-color: currentColor;
}
```

### Customize
