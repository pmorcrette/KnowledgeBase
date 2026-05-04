# CSS Variables

CSS custom properties for reusable values. Related: [Colors](02-colors-units.md), [Selectors](01-selectors.md).

## Defining Variables

```css
:root {
    /* Color */
    --primary: #007bff;
    --secondary: #6c757d;
    --success: #28a745;
    --danger: #dc3545;
    --warning: #ffc107;
    
    /* Spacing */
    --spacing-xs: 0.25rem;
    --spacing-sm: 0.5rem;
    --spacing-md: 1rem;
    --spacing-lg: 2rem;
    
    /* Typography */
    --font-base: 16px;
    --font-lg: 1.25rem;
    
    /* Borders */
    --border-radius: 0.25rem;
}
```

## Using Variables

```css
.button {
    background: var(--primary);
    color: white;
    padding: var(--spacing-sm) var(--spacing-md);
    border-radius: var(--border-radius);
}
```

## Fallback Values

```css
.box {
    background: var(--brand-color, blue);
}
```

## Scope

```css
/* Global */
:root { --color: red; }

/* Local */
.card { --color: green; }
.alert { background: var(--color); }
```

## JavaScript Access

```javascript
// Get
const color = getComputedStyle(el).getPropertyValue('--color');

// Set
el.style.setProperty('--color', 'blue');
```