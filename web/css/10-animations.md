# Transitions and Animations

Adding motion to elements.

## Transitions

```css
.button {
    transition: property duration timing-function delay;
    transition: all 0.3s ease;
    transition: background-color 0.3s ease-in-out;
    transition: transform 0.3s, opacity 0.3s;
}

.button:hover {
    background-color: blue;
    transform: scale(1.1);
}
```

## Timing Functions

| Function | Description |
|----------|-------------|
| `ease` | Slow start, fast, slow end |
| `linear` | Constant speed |
| `ease-in` | Slow start |
| `ease-out` | Slow end |
| `ease-in-out` | Slow start and end |

## Keyframe Animations

```css
@keyframes slideIn {
    from {
        opacity: 0;
        transform: translateX(-100%);
    }
    to {
        opacity: 1;
        transform: translateX(0);
    }
}

/* Using animation */
.slide {
    animation: slideIn 0.5s ease forwards;
}
```

## Animation Properties

```css
.animated {
    animation-name: slideIn;
    animation-duration: 0.5s;
    animation-timing-function: ease;
    animation-delay: 0s;
    animation-iteration-count: 1;
    animation-direction: normal;
    animation-fill-mode: none;
}
```

## Shorthand

```css
.animated {
    animation: slideIn 0.5s ease 0s 1 normal none;
}
```

## Animation Properties Values

| Property | Values |
|----------|--------|
| `animation-iteration-count` | 1, 2, infinite |
| `animation-direction` | normal, reverse, alternate |
| `animation-fill-mode` | none, forwards, backwards, both |

## Transform

```css
.transformed {
    /* Translation */
    transform: translate(10px, 20px);
    transform: translateX(10px);
    transform: translateY(10px);
    
    /* Scale */
    transform: scale(1.5);
    transform: scaleX(1.5);
    
    /* Rotation */
    transform: rotate(45deg);
    
    /* Skew */
    transform: skew(10deg);
    
    /* Combine */
    transform: translate(10px, 10px) rotate(45deg) scale(1.5);
}
```

## Transform Origin

```css
.transformed {
    transform-origin: center;
    transform-origin: top left;
    transform-origin: 50% 50%;
}
```