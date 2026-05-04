# Metadata

Metadata provides information about the document. Related: [Structure](01-structure.md), [Elements](02-elements.md).

## Head Element (Related: [Structure](01-structure.md))

```html
<head>
    <title>Page Title</title>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
```

## Meta Tags

```html
<!-- Character encoding -->
<meta charset="UTF-8">

<!-- Viewport (responsive) -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!-- Description -->
<meta name="description" content="Page description">

<!-- Keywords -->
<meta name="keywords" content="html, css, javascript">

<!-- Author -->
<meta name="author" content="John Doe">

<!-- Robots -->
<meta name="robots" content="index, follow">

<!-- Refresh (redirect) -->
<meta http-equiv="refresh" content="5;url=https://example.com">
```

## Open Graph (Social Media)

```html
<meta property="og:title" content="Title">
<meta property="og:description" content="Description">
<meta property="og:image" content="image.jpg">
<meta property="og:url" content="https://example.com">
<meta property="og:type" content="website">
```

## Twitter Card

```html
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="Title">
<meta name="twitter:description" content="Description">
<meta name="twitter:image" content="image.jpg">
```

## Favicon

```html
<link rel="icon" href="favicon.ico">
<link rel="icon" type="image/png" href="favicon.png">
<link rel="apple-touch-icon" href="apple-icon.png">
```

## Styles and Scripts

```html
<!-- Internal CSS -->
<style>
    body { margin: 0; }
</style>

<!-- External CSS -->
<link rel="stylesheet" href="style.css">

<!-- Internal JS -->
<script>
    console.log('Hello');
</script>

<!-- External JS -->
<script src="script.js"></script>

<!-- Deferred JS -->
<script src="script.js" defer></script>

<!-- Async JS -->
<script src="script.js" async></script>
```