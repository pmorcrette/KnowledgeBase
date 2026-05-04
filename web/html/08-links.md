# Links

Links connect pages and resources on the web. Related: [Semantic](05-semantic), [Structure](01-structure).

## Anchor Element

```html
<a href="https://example.com">Visit Example</a>
```

## Link Attributes

```html
<!-- External link -->
<a href="https://google.com" target="_blank">Google</a>

<!-- Internal link -->
<a href="/about">About Page</a>

<!-- Link to section -->
<a href="#section-id">Go to Section</a>

<!-- Download -->
<a href="/files/document.pdf" download>Download PDF</a>

<!-- Email link -->
<a href="mailto:email@example.com">Send Email</a>

<!-- Phone -->
<a href="tel:+1234567890">Call Us</a>
```

## Same Page Links

```html
<a href="#top">Back to Top</a>

<h2 id="section-id">Section Title</h2>
```

## Link States

```css
a:link     /* Unvisited */
a:visited /* Visited */
a:hover   /* Mouse over */
a:active  /* Being clicked */
a:focus   /* Keyboard focus */
```

## Best Practices

- Use descriptive link text
- Don't use "click here"
- Keep links accessible
- Use absolute paths for external, relative for internal