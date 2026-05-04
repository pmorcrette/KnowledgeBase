# Document Structure

The skeleton of an HTML document. Related: [Elements](02-elements.md), [Semantic](05-semantic.md).

## Required Elements

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document Title</title>
</head>
<body>
</body>
</html>
```

## Document Elements

| Element | Description |
|---------|-------------|
| `<!DOCTYPE>` | Document type declaration |
| `<html>` | Root element |
| `<head>` | Metadata container |
| `<body>` | Visible content |

## Head Elements

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Page description">
    <meta name="keywords" content="keyword1, keyword2">
    <link rel="stylesheet" href="style.css">
    <script src="script.js"></script>
    <title>Page Title</title>
</head>
```

## Semantic Structure (Related: [Semantic Elements](05-semantic.md))

```html
<body>
    <header>
        <nav>Navigation</nav>
    </header>
    <main>
        <section>
            <article></article>
        </section>
        <aside>Side content</aside>
    </main>
    <footer>Footer</footer>
</body>
```