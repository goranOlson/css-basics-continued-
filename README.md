## CSS Basics Continued

### CSS Variables
A CSS variable is just a value on a CSS property that we save in a central place. This value can we then reuse throughout the application. A very common case for a CSS variable is when using colors. Usually you have a bunch of those in different settings and most of the time you are using the same color in several places. It would be nice if you want to change this color to just change it in one place.

To create a CSS variable, you need to attache it to a specific element.This element should be at the top of your DOM tree, and that element usually the `html` tag. You can also use the `:root` tag, this is essentially the same thing as the `html` tag.

The variable is created with two dashes and a variable name and then the value and end the css rule with a semi-colon

```css
html {
    --main_color: #04aa6d;
    --background_color: #c8c8c8;
}

p {
    /* To access the variable you just substitute your value with the CSS variable inside parentheses and the `var` keyword */
    color: var(--main_color);
    background-color: var(--background_color);
}
```

A CSS variable dosen't only have to be colors, it can be anything really that you want to resuse in your project.
```
html {
    --main_color: #04aa6d;
    --background_color: #c8c8c8;
    --border_styling: 2px solid #9763f6;
}
```
In this case we create a standard border styling that we can use in multiple places in our css.

A CSS variable dosen't have to be defined in the `html` tag, we can also create them locally by defining them on spacific elemens. In this case the variables will only apply on those elements and every child element to that specific element.

### More advanced CSS Selectors

The specificty of a selector is decided via a point system in CSS. Different selectors are given different ponts that can be added together with ther selecorse in order to create a final specificicty of the given selector.

Naturally we usually want a selector with a hight specificity so the styling applied is only applied to the given element, unless we want otherwise.

Here is a link to details ablut the point system of CSS selectors:

[CSS Spacificity](https://www.w3schools.com/css/css_specificity.asp)

```css
/* Elements are given 1 point */
div {
    background-color: blue;
}

/* Classes are given 10 points */
.container {
    background-color: red;
}

/* Id:s are given 100 points */
#checkout {
    backgroud-color: green;
}
```
You also have the choise of createing inline styling, whitch be the way is not recommended. But inline styling is given 1000 points.

#### !important

This option is also availabel, althought it should only be used as a last resource. This will override any styling applied to the same property on the given element.

```css

/* The specificity points for this is 101 */
main#about-page {
    display: flex;
}

/* main specificity = 1. With '!important' we override everything */
main {
    display: block !important;
}
```
In this example above, the styling applied to just the main element with the `!important`, will override the more specificic selcetor above.

### Advanced CSS Selectors

To create more advanced CSS selectors your need to combine them. You can combine in multiple different ways, and to point of doing this is to create a specific selector the fits your specific case and also gives controll over whitch CSS styles that are applined to which selector.

The most basic selector is the usage of one kint, element, class or id. In this case we choose at class.

```css
.text {
    color: white;
}
```
The selector will target all element that have a class called 'text'

---

```css
.text.bold {
    font-weight: 700;
}
```
This selector will target every element that has BOTH the classes `text` and `bold`. So more classes, (or id:s) seperated by a period (.) or (# in the case of id:s) will have the same behaviour. The points of the classes or id:s are added together so this example above gives the selector 20 points. 10 for each class.

---
```css
.checkout .price-table {
  display: flex;
}
```
This selector contains a white space between the classes. This means we are targeting an element that has the class `price-table` AND is a decendant child-element to an element with the class `checkout`. The specificity on this one is also 20. 10 for each class. Same behaviour applies to id:s or a combination of elements, classes and id:s.

```css
section .footer .text.bold {
  font-weight: 700;
}
```
This selector is of course more complicated. But we are looking for an element that has BOTH of the classes `text` AND `bold`, but is a decendant element to an element with the class `footer` which in turn is a decendant element to a `section`. The points here are 31 (I think), 1 for the element and 10 per class.

---
How about this selector? What does it mean?
```css
section > div > .text {
  color: yellow;
}
```
This sign > means that the element must be a direct child element of the parent element.

---
```css
section + p {
  color: black;
}
```

This selector targets a p tag that is a sibling tag of a div. They must be on the same level in the DOM.

---
There are of course many more ways you can create your selectors but it's to many to cover just now. Here are some links for further reading.

[Different CSS Selectors](https://www.w3schools.com/cssref/css_selectors.php)

[CSS Specificity](https://www.w3schools.com/css/css_specificity.asp)

[The !important property](https://www.w3schools.com/css/css_important.asp)