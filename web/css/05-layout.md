# Layout

CSS layout techniques for positioning elements. Related: [Box Model](04-box-model.md), [Responsive](09-responsive.md).

## Display

```css
.box {
    display: block;
    display: inline;
    display: inline-block;
    display: none;
    display: flex;
    display: grid;
}
```

## Flexbox

```css
.container {
    display: flex;
    flex-direction: row;
    flex-direction: column;
    justify-content: flex-start;
    justify-content: center;
    justify-content: space-between;
    align-items: stretch;
    align-items: center;
    gap: 1rem;
    flex-wrap: wrap;
}

.item {
    flex: 1 1 auto;
    flex-grow: 1;
    flex-shrink: 0;
}
```

### Flex Properties

| Property | Values |
|----------|--------|
| `flex-direction` | row, column |
| `justify-content` | flex-start, center, space-between |
| `align-items` | stretch, flex-start, center |
| `flex-wrap` | wrap, nowrap |
| `gap` | spacing |

## CSS Grid

```css
.container {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-columns: repeat(3, 1fr);
    grid-template-columns: 200px auto;
    grid-template-rows: auto;
    gap: 1rem;
    grid-template-areas:
        "header header"
        "sidebar main"
        "footer footer";
}

.item {
    grid-column: 1 / 3;
    grid-row: 1 / 2;
}
```

### Grid Properties (Related: [Responsive](09-responsive.md))

```css
.container {
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
}
```

## Positioning

```css
.box {
    position: static;
    position: relative;
    position: absolute;
    position: fixed;
    position: sticky;
    
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 10;
}
```

| Value | Context |
|-------|---------|
| static | Normal flow |
| relative | Offset from original position |
| absolute | Nearest positioned ancestor |
| fixed | Relative to viewport |
| sticky | Fixed after scrolling past |