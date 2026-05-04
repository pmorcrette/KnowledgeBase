# Background

CSS background properties for element backgrounds.

## Background Properties

```css
.box {
    /* Color */
    background-color: #f0f0f0;
    
    /* Image */
    background-image: url('image.jpg');
    background-image: linear-gradient(to bottom, red, blue);
    background-image: radial-gradient(circle, red, blue);
    
    /* Repeat */
    background-repeat: repeat;
    background-repeat: repeat-x;
    background-repeat: repeat-y;
    background-repeat: no-repeat;
    
    /* Position */
    background-position: center;
    background-position: top left;
    background-position: 50% 50%;
    
    /* Size */
    background-size: cover;
    background-size: contain;
    background-size: 100px 100px;
    
    /* Attachment */
    background-attachment: scroll;
    background-attachment: fixed;
    background-attachment: local;
}
```

## Shorthand

```css
.bg {
    background: #f0f0f0 url('img.jpg') no-repeat center/cover;
}
```

## Multiple Backgrounds

```css
.multi {
    background: 
        url('foreground.png') center,
        url('background.png') cover;
}
```

## Gradients

```css
.linear {
    background: linear-gradient(to right, red, blue);
    background: linear-gradient(45deg, red, blue, green);
}

.radial {
    background: radial-gradient(circle, red, blue);
}
```