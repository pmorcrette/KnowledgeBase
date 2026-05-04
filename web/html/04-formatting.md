# Text Formatting

Inline elements for formatting text. Related: [Headings](06-headings.md), [Semantic](05-semantic.md).

## Basic Formatting

```html
<p>This is <strong>bold</strong> text.</p>
<p>This is <em>italic</em> text.</p>
<p>This is <u>underlined</u> text.</p>
<p>This is <s>strikethrough</s> text.</p>
```

## Semantic Text

| Element | Meaning |
|---------|---------|
| `<strong>` | Important text |
| `<em>` | Emphasized text |
| `<mark>` | Highlighted text |
| `<small>` | Small text |
| `<sub>` | Subscript |
| `<sup>` | Superscript |

## Examples

```html
<p>H<sub>2</sub>O - Water formula</p>
<p>E = mc<sup>2</sup> - Einstein's formula</p>
<p><mark>Highlighted</mark> text</p>
<p><small>Copyright 2024</small></p>
```

## Quotes

```html
<blockquote cite="https://example.com">
    A longer quotation that spans multiple lines.
</blockquote>

<p>She said <q>A short quote</q>.</p>

<p>The book <cite>Title</cite> by Author</p>
```

## Code and Preformatted

```html
<code>console.log('Hello')</code>

<pre>
function hello() {
    console.log('Hello');
}
</pre>

<var>variable</var>
<kbd>Ctrl + S</kbd>
```

## Time

```html
<time datetime="2024-05-24">May 24, 2024</time>
```