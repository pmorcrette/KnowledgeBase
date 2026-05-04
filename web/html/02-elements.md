# Elements and Tags

HTML elements are the building blocks of web pages. Related: [Attributes](03-attributes.md), [Structure](01-structure.md).

## Element Anatomy

```html
<tagname attribute="value">Content</tagname>
```

- Opening tag: `<tagname>`
- Content: The text between tags
- Closing tag: `</tagname>`
- Attributes: Additional info in opening tag

## Void Elements (Self-Closing)

```html
<img src="image.jpg" alt="Description">
<br>
<input type="text">
<meta charset="UTF-8">
<link rel="stylesheet" href="style.css">
<hr>
```

## Nested Elements

```html
<p>This is <strong>important</strong> text.</p>
```

## Common Elements

| Element | Use |
|---------|-----|
| `<p>` | Paragraph |
| `<h1>` to `<h6>` | Headings |
| `<a>` | Link |
| `<img>` | Image |
| `<div>` | Division/block container |
| `<span>` | Inline container |
| `<ul>` / `<ol>` | Unordered/ordered list |
| `<li>` | List item |
| `<table>` | Table |
| `<form>` | Form |
| `<input>` | Input field |