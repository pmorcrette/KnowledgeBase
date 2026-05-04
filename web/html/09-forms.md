# Forms

Forms collect user input and submit data to a server. Related: [Attributes](03-attributes.md), [Tables](10-tables.md), [Media](11-media.md).

## Basic Form

```html
<form action="/submit" method="POST">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name">
    
    <button type="submit">Submit</button>
</form>
```

## Input Types

```html
<input type="text">        <!-- Text -->
<input type="email">       <!-- Email -->
<input type="password">    <!-- Password -->
<input type="number">      <!-- Number -->
<input type="tel">         <!-- Phone -->
<input type="url">         <!-- URL -->
<input type="search">      <!-- Search -->
<input type="checkbox">    <!-- Checkbox -->
<input type="radio">       <!-- Radio -->
<input type="range">      <!-- Range slider -->
<input type="date">       <!-- Date -->
<input type="time">       <!-- Time -->
<input type="color">      <!-- Color picker -->
<input type="file">       <!-- File upload -->
<input type="hidden">     <!-- Hidden -->
```

## Form Elements

```html
<!-- Text input -->
<input type="text" name="username" placeholder="Enter name">

<!-- Textarea -->
<textarea name="message" rows="4" cols="50"></textarea>

<!-- Select dropdown -->
<select name="country">
    <option value="us">United States</option>
    <option value="uk">United Kingdom</option>
    <option value="ca">Canada</option>
</select>

<!-- Radio buttons -->
<input type="radio" name="gender" value="male"> Male
<input type="radio" name="gender" value="female"> Female

<!-- Checkbox -->
<input type="checkbox" name="terms"> I agree to terms

<!-- Button -->
<button type="submit">Submit</button>
<button type="reset">Reset</button>
<button type="button">Custom</button>
```

## Input Attributes (Related: [Attributes](03-attributes.md))

```html
<input type="text" 
       name="username"
       id="username"
       required
       readonly
       disabled
       maxlength="50"
       minlength="3"
       pattern="[A-Za-z]+"
       placeholder="Enter username">
```

## Form Attributes

```html
<form action="/submit" method="POST" enctype="multipart/form-data">
```

| Attribute | Description |
|-----------|-------------|
| `action` | URL to submit |
| `method` | GET or POST |
| `enctype` | Data encoding type |
| `target` | Response target |
| `novalidate` | Skip validation |

## Accessibility

```html
<label for="email">Email:</label>
<input type="email" id="email" name="email">

<!-- Or wrap input -->
<label>
    <input type="checkbox" name="agree"> I agree
</label>
```