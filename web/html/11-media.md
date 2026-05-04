# Images and Media

Embedding images and media content in HTML. Related: [Links](08-links), [Semantic](05-semantic).

## Images

```html
<img src="image.jpg" alt="Description" width="500" height="300">
```

## Image Attributes

| Attribute | Description |
|-----------|-------------|
| `src` | Image source URL |
| `alt` | Alternative text |
| `width` | Display width |
| `height` | Display height |
| `loading` | lazy or eager |
| `srcset` | Multiple sources |

## Responsive Images

```html
<img src="small.jpg"
     srcset="small.jpg 500w, medium.jpg 1000w, large.jpg 2000w"
     sizes="(max-width: 600px) 100vw, 50vw"
     alt="Description">
```

## Figure and Figcaption

```html
<figure>
    <img src="chart.png" alt="Sales chart">
    <figcaption>Figure 1: Annual Sales</figcaption>
</figure>
```

## Audio

```html
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    <source src="audio.ogg" type="audio/ogg">
    Your browser doesn't support audio.
</audio>
```

## Video

```html
<video controls width="800" poster="poster.jpg">
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
    <track src="subtitles.vtt" kind="subtitles" srclang="en">
    Your browser doesn't support video.
</video>
```

## Embed

```html
<!-- YouTube -->
<iframe width="560" height="315" 
        src="https://www.youtube.com/embed/video-id">
</iframe>

<!-- PDF -->
<object data="file.pdf" type="application/pdf">
</object>
```