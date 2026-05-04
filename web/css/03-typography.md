# Typography

CSS text and font properties. Related: [Layout](05-layout.md), [Colors](02-colors-units.md).

## Font Properties

```css
.text {
    /* Font family */
    font-family: Arial, sans-serif;
    font-family: "Times New Roman", serif;
    font-family: "Fira Code", monospace;
    
    /* Font size */
    font-size: 16px;
    font-size: 1rem;
    font-size: 100%;
    
    /* Font weight */
    font-weight: normal;
    font-weight: bold;
    font-weight: 400;
    font-weight: 700;
    
    /* Font style */
    font-style: normal;
    font-style: italic;
}
```

## Text Properties

```css
.text {
    /* Color */
    color: #333;
    
    /* Alignment */
    text-align: left;
    text-align: center;
    text-align: right;
    text-align: justify;
    
    /* Decoration */
    text-decoration: none;
    text-decoration: underline;
    text-decoration: line-through;
    
    /* Transformation */
    text-transform: uppercase;
    text-transform: lowercase;
    text-transform: capitalize;
    
    /* Indentation */
    text-indent: 2em;
    
    /* Line height (for readability) */
    line-height: 1.5;
    line-height: 150%;
    
    /* Letter spacing */
    letter-spacing: 0.05em;
    
    /* Word spacing */
    word-spacing: 0.1em;
    
    /* White space */
    white-space: normal;
    white-space: nowrap;
    white-space: pre;
}
```

## Shorthand

```css
/* font: style weight size/line-height family */
font: italic bold 1rem/1.5 Arial, sans-serif;
```