# jQuery Fluid Typography

A super lightweight jQuery plugin to allow an elements font-size (or any other property) to be a percentage of its parent container's height or width. For some reason, you still can't do this with CSS in 2019.

Feel free to fork or critique.

## Installation

```
$ npm install --save jquery-fluid-typography
```

## Usage

Just add jQuery and the fluid typography plugin to your project.

```
<script src="http://code.jquery.com/jquery-latest.min.js"></script>
<script src="jquery-fluid-typography/index.js"></script>
```

###$.responsiveFonts(elements) takes an array of objects, each object represents one element that needs scaling, its properties are as follows:

**parent** - A jQuery selector of the parent element which contains the targeted element.

**target** - A jQuery selector of the element which needs font scaling (it doesn't have to be nested, but will be in most use cases).

**factor** - A number which will be used to calculate the font-size of the element in relation to the parent element's height (A factor of 0.5 will cause the resulting elements font-size to be half the size of it's parent height in pixels).

**useContainerWidth(optional)** - If set to true, the element will be scaled using the parent containers width, instead of using it's height.

**property(optional)** - Maybe you want to set another CSS property besides font-size (such as line-height), just use 'property' to override the default property of font-size, if you need font-size and another property, just make another object.

###Example:
```
var elements = [
    {
        parent: '.parent-container',
        target: '.element-whose-font-needs-to-scale',
        factor: 0.2
    },
    {
        parent: '.parent-container',
        target: '.element-whose-font-needs-to-scale-off-container-width',
        factor: 0.4,
        useContainerWidth: true
    },
    {
        parent: '.parent-container',
        target: '.element-whose-line-height-needs-to-scale',
        factor: 0.4,
        property: 'line-height'
    }
];
```
...Or if you want to set the font size to the container itself (for all of its children to use).
```
{
    parent: '.parent-container',
    target: '.parent-container',
    factor: 0.5,
}
```
###To set once...
```
$.responsiveFonts(elements);
```
or perhaps within jQuerys ready function
```
$(document).ready(function() {
    $.responsiveFonts(elements);
});
```
###...or on page load and window resize (recommended), to make it truly responsive
```
$(document).ready(function() {
    $.responsiveFonts(elements);
});

$(window).resize(function() {
    $.responsiveFonts(elements);
});
```

Link to my [GitHub](https://github.com/MichaelSpencer1995/jquery-fluid-typography).