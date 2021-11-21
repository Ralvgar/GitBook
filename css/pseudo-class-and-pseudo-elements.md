# Pseudo class & Pseudo elements

## Pseudo-classes

A pseudo-class is used to define a special state of an element.

For example, it can be used to:

* Style an element when a user mouses over it
* Style visited and unvisited links differently
* Style an element when it gets focus

### Syntax

The syntax of pseudo-classes:

```
selector:pseudo-class {
  property: value;
}
```

## Pseudo-elements

A CSS pseudo-element is used to style specified parts of an element.

For example, it can be used to:

* Style the first letter, or line, of an element
* Insert content before, or after, the content of an element

### Syntax

The syntax of pseudo-elements:

```
selector::pseudo-element {
  property: value;
}
```

### The double colon

&#x20;The double colon (`::`) was introduced in CSS3 to differentiate pseudo-elements such as `::before` and `::after` from pseudo-classes such as `:hover` and `:active`. All browsers support double colons for pseudo-elements except Internet Explorer (IE) 8 and below.

{% embed url="https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Pseudo-classes_and_pseudo-elements" %}
