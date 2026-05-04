# Colors and Units

CSS supports various color formats and measurement units. Related: [Variables](06-variables.md), [Typography](03-typography.md).

## Color Formats

```css
/* Named */
color: blue;

/* Hex */
color: #0000ff;
color: #00f;

/* RGB */
color: rgb(0, 0, 255);

/* RGBA */
color: rgba(0, 0, 255, 0.5);

/* HSL */
color: hsl(240, 100%, 50%);

/* HSLA */
color: hsla(240, 100%, 50%, 0.5);
```

## Length Units

| Unit | Description |
|------|-------------|
| `px` | Pixels (absolute) |
| `em` | Relative to font-size |
| `rem` | Relative to root font-size |
| `%` | Percentage |
| `vw` | 1% viewport width |
| `vh` | 1% viewport height |
| `vmin` | Smaller of vw/vh |
| `vmax` | Larger of vw/vh |

```css
/* Examples */
font-size: 16px;
width: 50%;
margin: 1rem;
font-size: 1.5em;
```

## CSS Variables (Related: [Variables](06-variables.md))

```css
:root {
    --primary: #007bff;
    --spacing: 1rem;
}

.card {
    background: var(--primary);
    padding: var(--spacing);
}
```