# Filters and Effects

CSS visual effects and filters.

## Filters

```css
.filtered {
    /* Blur */
    filter: blur(5px);
    
    /* Brightness */
    filter: brightness(150%);
    filter: brightness(0.5);
    
    /* Contrast */
    filter: contrast(150%);
    
    /* Grayscale */
    filter: grayscale(100%);
    
    /* Sepia */
    filter: sepia(100%);
    
    /* Hue rotate */
    filter: hue-rotate(90deg);
    
    /* Invert */
    filter: invert(100%);
    
    /* Drop shadow */
    filter: drop-shadow(5px 5px 10px rgba(0,0,0,0.5));
    
    /* Multiple */
    filter: blur(2px) grayscale(50%) contrast(150%);
}
```

## Opacity

```css
.box {
    opacity: 0.5;
    opacity: 1;
    opacity: 0;
}
```

## Box Shadow

```css
.shadow {
    /* Basic */
    box-shadow: 5px 5px 10px rgba(0,0,0,0.3);
    
    /* Inset */
    box-shadow: inset 5px 5px 10px rgba(0,0,0,0.3);
    
    /* Multiple */
    box-shadow: 
        0 1px 3px rgba(0,0,0,0.12),
        0 1px 2px rgba(0,0,0,0.24);
}
```

## Text Shadow

```css
.text {
    text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
    text-shadow: 1px 1px 2px black;
}
```

## Backdrop Filter

```css
.overlay {
    backdrop-filter: blur(10px);
    backdrop-filter: grayscale(50%);
}
```