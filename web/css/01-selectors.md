# Selectors

Selectors target HTML elements for styling. Related: [Box Model](04-box-model.md), [Cascading](07-cascade.md).

## Basic Selectors

```css
/* Element */
p { }

/* Class (. notation) */
.highlight { }

/* ID (# notation) */
#header { }

/* Universal (* notation) */
* { }

/* Attribute */
[type="text"] { }
```

## Combinators

```css
/* Descendant (space) */
div p { }

/* Child (>) */
div > p { }

/* Adjacent sibling (+) */
h1 + p { }

/* General sibling (~) */
h1 ~ p { }
```

## Pseudo-classes

```css
/* State */
:hover { }
:focus { }
:active { }
:checked { }
:disabled { }

/* Structural */
:first-child { }
:last-child { }
:nth-child(2n) { }
:nth-of-type(odd) { }
```

## Pseudo-elements (Related: [Box Model](04-box-model.md))

```css
::before { }
::after { }
::first-line { }
::first-letter { }
```

## Specificity (Related: [Cascading](07-cascade.md))

| Selectors | Specificity |
|----------|------------|
| `#id` | 1,0,0 |
| `.class` | 0,1,0 |
| `element` | 0,0,1 |