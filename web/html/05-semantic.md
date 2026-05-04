# Semantic Elements

Semantic HTML elements clearly describe their meaning to browser and developer.

## Why Semantic HTML

- **Accessibility**: Screen readers understand structure
- **SEO**: Search engines understand content importance
- **Maintainability**: Code is self-documenting
- **Future-proof**: Standardized meaning

## Semantic Structure Elements (Related: [Structure](01-structure))

```html
<header>Header content</header>
<nav>Navigation links</nav>
<main>
    <section>
        <article>Independent content</article>
    </section>
    <aside>Related content</aside>
</main>
<footer>Footer content</footer>
```

## Semantic Elements Reference

| Element | Description |
|---------|-------------|
| `<header>` | Page/section header |
| `<nav>` | Navigation links |
| `<main>` | Main content (only one per page) |
| `<section>` | Thematic grouping |
| `<article>` | Self-contained content |
| `<aside>` | Tangentially related content |
| `<footer>` | Page/section footer |
| `<figure>` | Media with caption |
| `<figcaption>` | Caption for figure |

## Example Layout

```html
<body>
    <header>
        <h1>Website Title</h1>
        <nav>
            <a href="/">Home</a>
            <a href="/about">About</a>
        </nav>
    </header>
    
    <main>
        <article>
            <h2>Blog Post Title</h2>
            <p>Content...</p>
        </article>
    </main>
    
    <footer>&copy; 2024</footer>
</body>
```

## Non-Semantic Elements

| Element | Use When |
|---------|----------|
| `<div>` | No semantic meaning needed |
| `<span>` | No semantic meaning needed inline |

Choose semantic elements over `<div>`/`<span>` whenever possible.