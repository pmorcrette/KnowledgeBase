# Attributes

Attributes provide additional information about HTML elements. Related: [Elements](02-elements.md), [Forms](09-forms.md).

## Syntax

```html
<element attribute="value">Content</element>
```

## Global Attributes

| Attribute | Description |
|-----------|-------------|
| `id` | Unique identifier |
| `class` | CSS class(es) |
| `style` | Inline CSS |
| `title` | Tooltip text |
| `data-*` | Custom data storage |

## Common Attributes

```html
<!-- href for links -->
<a href="https://example.com">Link</a>

<!-- src for images -->
<img src="image.jpg" alt="Description">

<!-- src for scripts -->
<script src="script.js"></script>

<!-- href for links -->
<link rel="stylesheet" href="style.css">

<!-- Input attributes -->
<input type="text" name="username" value="default">
```

## Boolean Attributes

```html
<!-- Disabled attribute (no value needed) -->
<input type="text" disabled>
<input type="text" disabled="disabled">

<!-- Readonly -->
<input type="text" readonly>

<!-- Checked -->
<input type="checkbox" checked>
```

## Custom Data Attributes

```html
<div data-user-id="123" data-role="admin">
    User info
</div>
```

## Accessing in JavaScript (Related: [Forms](09-forms.md))

```javascript
element.dataset.userId
```