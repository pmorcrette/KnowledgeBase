# Cascading and Inheritance

How CSS determines which styles apply.

## Cascading Order

1. Importance (!important)
2. Origin (author, user, user agent)
3. Specificity
4. Source order

## Specificity

```css
/* Highest specificity */
#id { color: blue; }

/* Middle */
.class { color: green; }

/* Lowest */
element { color: red; }
```

## !important

```css
/* Overrides normal rules */
.button {
    color: white !important;
}
```

## Inheritance

```css
/* Inherited by default */
color: inherit;
visibility: inherit;
line-height: inherit;
font-family: inherit;

/* Not inherited by default */
border: inherit;
padding: inherit;
margin: inherit;
```

## `inherit` Keyword

```css
.child {
    color: inherit;  /* Same as parent */
}
```

## `initial` and `unset`

```css
.box {
    color: initial;   /* Reset to default */
    color: unset;    /* Inherit or initial */
}
```

## `all` Shorthand

```css
* {
    all: initial;
    all: inherit;
    all: unset;
}
```