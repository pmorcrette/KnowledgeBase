# Media Queries

Mobile-first responsive design using media queries.

## Media Types

```css
@media screen { }
@media print { }
@media speech { }
@media all { }
```

## Media Features

```css
/* Width */
@media (width: 600px) { }
@media (min-width: 600px) { }
@media (max-width: 600px) { }

/* Height */
@media (min-height: 400px) { }

/* Orientation */
@media (orientation: portrait) { }
@media (orientation: landscape) { }

/* Aspect ratio */
@media (aspect-ratio: 16/9) { }

/* Resolution */
@media (resolution: 300dpi) { }
@media (min-resolution: 2dppx) { }
```

## Common Breakpoints

```css
/* Mobile */
@media (max-width: 575px) { }

/* Tablet */
@media (min-width: 576px) and (max-width: 991px) { }

/* Desktop */
@media (min-width: 992px) { }
```

## Mobile-First Approach

```css
/* Base styles (mobile) */
.container {
    width: 100%;
    padding: 1rem;
}

/* Tablet+ */
@media (min-width: 576px) {
    .container {
        max-width: 540px;
    }
}

/* Desktop+ */
@media (min-width: 992px) {
    .container {
        max-width: 960px;
    }
}
```

## Complex Queries

```css
/* AND */
@media (min-width: 600px) and (orientation: portrait) { }

/* OR (comma) */
@media (min-width: 600px), (hover: hover) { }

/* NOT */
@media not screen { }
```

## Hide/Show Elements

```css
.mobile-only {
    display: block;
}

.desktop-only {
    display: none;
}

@media (min-width: 992px) {
    .mobile-only {
        display: none;
    }
    .desktop-only {
        display: block;
    }
}
```