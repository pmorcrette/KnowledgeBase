# CSS Overview

CSS (Cascading Style Sheets) styles HTML documents. It controls layout, colors, fonts, and presentation.

## Basic Syntax

```css
selector {
    property: value;
}
```

## Ways to Add CSS

```html
<!-- External -->
<link rel="stylesheet" href="style.css">

<!-- Internal -->
<style>
    body { background: white; }
</style>

<!-- Inline (not recommended) -->
<div style="color: red;">Red text</div>
```

## Key Concepts

- **Selectors**: Target HTML elements
- **Properties**: Style attributes
- **Values**: Property settings
- **Cascading**: Priority based on specificity and source order
- **Inheritance**: Styles pass to children