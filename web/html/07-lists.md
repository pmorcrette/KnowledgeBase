# Lists

HTML provides several list types for different content organization. Related: [Semantic](05-semantic.md), [Formatting](04-formatting.md).

## Unordered List

```html
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```

## Ordered List

```html
<ol>
    <li>First item</li>
    <li>Second item</li>
    <li>Third item</li>
</ol>
```

## List Attributes

```html
<!-- Start number -->
<ol start="5">
    <li>Starts at 5</li>
</ol>

<!-- Reversed -->
<ol reversed>
    <li>Count down</li>
    <li>Three</li>
    <li>Two</li>
    <li>One</li>
</ol>

<!-- Type (1, A, a, I, i) -->
<ol type="A">
    <li>Alphabetical</li>
</ol>
```

## Definition List

```html
<dl>
    <dt>Term 1</dt>
    <dd>Definition for term 1</dd>
    <dt>Term 2</dt>
    <dd>Definition for term 2</dd>
</dl>
```

## Nested Lists

```html
<ul>
    <li>Fruits
        <ul>
            <li>Apple</li>
            <li>Banana</li>
        </ul>
    </li>
    <li>Vegetables</li>
</ul>
```