# HTML Standards and Style Guide

## Line length

Lines should ideally be kept to a maximum of 120 characters.

This applies to HTML found in regular HTML files, Blade files, and 
HTML which is present in frontend framework files.

## Formatting HTML tags

If a HTML tag would normally exceed the maximum line length,
its attributes should be split onto their own lines. In this case, 
the tag name should sit alone.

This is best shown with examples. 

If a tag breaches the maximum line length, the following is ideal.

```html
<img
    id="<an id>"
    class="<a class>"
    src="<a src>"
/>
```

However, if a tag fits on a single line, the following works fine.

```html
<a style="display:inline-block;" alt="Big A" />
```

Try to avoid formatting HTML tags as shown below.

```html
<!-- For multi-line tags, the tag name should sit alone. Not like this. -->
<img id="<an id>"
    class="<a class>"
    src="<a src>"
/>
```

```html
<!-- This tag could fit on a single line so does not need this extra spacing. -->
<a 
        style="display:inline-block;" alt="Big A"
/>
```