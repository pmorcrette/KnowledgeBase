# Box Model

Every element is a rectangular box with content, padding, border, and margin. Related: [Layout](05-layout), [Background](08-background).

## Box Model Layers

```
+-------------+
|   margin    |
+-------------+
|   border   |
+-------------+
|  padding  |
+-------------+
|  content  |
+-------------+
```

## Properties

```css
.box {
    /* Content size */
    width: 200px;
    height: 100px;
    
    /* Padding */
    padding: 20px;
    padding-top: 10px;
    padding-right: 15px;
    padding-bottom: 10px;
    padding-left: 15px;
    /* Shorthand: top right bottom left */
    
    /* Border */
    border: 1px solid black;
    border-width: 1px;
    border-style: solid;
    border-color: black;
    border-radius: 4px;
    
    /* Margin */
    margin: 20px;
    margin: 10px 15px; /* vertical horizontal */
    margin: 10px 15px 10px 15px;
}
```

## Box-sizing (Related: [Layout](05-layout))

```css
/* Default: content-box */
*, *::before, *::after {
    box-sizing: border-box;
}

/* Width includes padding + border */
.box {
    width: 200px;
    padding: 20px;
    border: 1px solid;
    /* Actual rendered width = 200px, not 242px */
}
```

## Auto Margins

```css
.box {
    margin-left: auto;  /* Push right */
    margin-right: auto; /* Push left */
    margin: auto;     /* Center horizontally */
}
```