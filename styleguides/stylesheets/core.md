# Stylesheet Standards

This document outlines a series of standards for creating stylesheets using:

- CSS
- SCSS
- LESS

## General Standards

##### Everything should be indented using 4 spaces

Bad:

```css
button {
  background-color: red;
  text-transform: capitalize;
}
```

Good:

```css
button {
    background-color: red;
    text-transform:   capitalize;
}
```

<small><i>Note: A tab with the size of 4 spaces will also work.</i></small>


##### Property values should be aligned by value

Bad:

```css
button {
   background-color: red;
   text-transform:   capitalize;
}
```

Good:

```css
button {
    background-color: red;
    text-transform:   capitalize;
}
```

##### Classes and IDs should be [kebab-case][kebab-case]

Bad:

```css
.button.button_danger {
    background-color: red;
    text-transform:   capitalize;
}
```

Good:

```css
.button.button-danger {
    background-color: red;
    text-transform:   capitalize;
}
```

##### Multi-value properties should go below the property

Bad:

```css
.button.button-danger {
    background-color: red;
    text-transform:   capitalize;
    transition:       background-color ease-in-out 150ms, color ease-in-out 150ms;
}
```

Good:

```css
.button.button-danger {
    background-color: red;
    text-transform:   capitalize;
    transition:
        background-color ease-in-out 150ms,
        color ease-in-out 150ms;
}
```

##### Child classes should be prefixed

Bad:

```css
.button.danger {
    background-color: red;
    text-transform:   capitalize;
}
```

Good:

```css
.button.button-danger {
    background-color: red;
    text-transform:   capitalize;
}
```

##### Colors should be readable

Bad:

```css
.button.button-danger {
    background-color: red;
    text-shadow:      0 2px 4px #ff0;
    color:            rgba(0,0,0,1); // rgb(0,0,0)
}
```

Good:

```css
.button.button-danger {
    background-color: red;
    text-shadow:      0 2px 4px #ff0;
    color:            rgba(0, 0, 0, 1); // rgb(0, 0, 0)
}
```

##### [Combinators][css-combinators] should have spaces around them

Bad:

```css
button>span {
	cursor: inherit;
}
```

Good:

```css
button > span {
	cursor: inherit;
}
```

##### Use shorthand properties where applicable

Bad:

```css
margin-top:    10px;
margin-bottom: 20px;
margin-left:   30px;
margin-right:  30px;
```

Good:

```css
margin: 10px 30px 20px;
```

<small><i>Note: Shorthand for `margin` goes [clockwise starting at the top][margin-shorthand].</i></small>


##### Do not put a unit after `0`

Bad:

```css
.button {
	padding: 0px;
}
```

Good:

```css
.button {
	padding: 0;
}
```

##### Do not overuse `calc`

Bad:

```scss
.button-group {
    .button {
        width:  calc(100% - 10px);
        margin: 0 5px;
    }
	
    > :first-child {
        margin-left: 0;
    }
	
    > :last-child {
        margin-right: 0;
    }
}
```

Good:

```scss
.button-group {
    display: flex;

    .button {
        flex-grow: 1;
        margin:    0 5px;
    }
	
    > :first-child {
        margin-left: 0;
    }
	
    > :last-child {
        margin-right: 0;
    }
}
```

<small><i>Note: [`flex`][flex] can cover most situations where `calc` would be used.</i></small>


## LESS/SCSS

In these examples variables will be used as shown in [SCSS][scss-variables]. If you are using [LESS][less-variables] make sure to change the syntax accordingly.

##### Styles should be broken up into entities and imported into a single file

Bad:

```
- styles/_app.scss

    * {}
    .button {}
    body {}
    .page {}
```

Good:

```
- styles/_app.scss

    @import './defaults';
    @import './controls';
    @import './containers';

- styles/defaults.scss

    * {}

- styles/controls.scss

    .button {}

- styles/containers.scss

    body {}
    .page {}

```

##### Variables should be prefixed and have the property within the name

Bad:

```scss
$variable: red;

// ...

.button {
	background-color: $variable;
}
```

Good:

```scss
$gobal-background-color: red;
$button-background-color: $global-background-color;

// ...

.button {
	background-color: $button-background-color;
}

```

##### Variables should go into their own file

Bad:

```
- styles/_app.scss

    @import './controls';
    
- styles/controls.scss

    $button-background-color: red;
    
    .button {
        background-color: $button-background-color;
    }
```

Good:

```
- styles/_app.scss

    @import './_variables';
    @import './controls';

- styles/_variables.scss

    $button-background-color: red;
    
- styles/controls.scss
    
    .button {
        background: $button-background-color;
    }
```

<small><i>Note: The variables file must be imported before anything otherwise a parse error will happen.</i></small>


[kebab-case]: https://stackoverflow.com/a/12273101/8176262
[css-combinators]: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors#Combinators
[margin-shorthand]: https://developer.mozilla.org/en-US/docs/Web/CSS/margin#More_examples
[scss-variables]: https://sass-lang.com/guide#topic-2
[less-variables]: http://lesscss.org/#variables
[flex]: https://developer.mozilla.org/en-US/docs/Web/CSS/flex
