# Global Attributes

Attributes available on all HTML elements. Related: [Attributes](03-attributes.md), [Forms](09-forms.md).

## All HTML Elements Support

```html
<div id="unique" class="class-name" style="color: red;" 
     title="Tooltip" lang="en" dir="ltr">
    Content
</div>
```

## Global Attributes Reference

| Attribute | Description |
|-----------|-------------|
| `accesskey` | Keyboard shortcut |
| `autocapitalize` | Capitalization hint |
| `class` | CSS classes |
| `contenteditable` | Allow editing |
| `dir` | Text direction (ltr/rtl/auto) |
| `draggable` | Enable drag |
| `hidden` | Hide element |
| `id` | Unique identifier |
| `inert` | Disable interaction |
| `inputmode` | Virtual keyboard hint |
| `is` | Custom element |
| `lang` | Language code |
| `part` | Shadow part |
| `slot` | Shadow slot |
| `spellcheck` | Enable spellcheck |
| `style` | Inline CSS |
| `tabindex` | Tab order |
| `title` | Tooltip |
| `translate` | Allow translation |

## Event Handler Attributes

```html
<!-- Common -->
<div onclick="handler()">Click me</div>
<div onmouseover="handler()">Hover me</div>
<div onload="handler()">Loaded</div>
```

## Custom Data Attributes

```html
<div data-user-id="123" data-role="admin">
    User info
</div>
```

```javascript
// Access with JavaScript
element.dataset.userId  // "123"
```

## ARIA Attributes (Related: [Accessibility](-accessibility))

```html
<div role="button" aria-label="Close" tabindex="0">
<div aria-expanded="true">
<div aria-controls="menu-id">
```