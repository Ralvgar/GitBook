---
description: Syntactically Awesome Stylesheet
---

# Sass: Syntactically Awesome Style Sheet

Sass is an extension to CSS and completely compatible with all versions of CSS,  a valid `.css` file is a valid `.scss` file as well. Sass follows the [DRY \(Don’t Repeat Yourself\)](http://wiki.c2.com/?DontRepeatYourself) programming principle in order to avoid duplication so it reduces repetition of code, make it easier to maintain and therefore saves time.

It provide several mechanisms available in more traditional programming languages, particularly object-oriented languages: Variables, Nesting, Loops, Arguments... 

### Syntax

Sass has two syntaxes. The `.sass` file extension uses the older syntax that is indentation-based and omits semicolons and curly brackets from the code. The newer and more widely used syntax belonging to the `.scss` file extension. It uses the standard CSS syntax with braces and semicolons.

#### Variables

In Sass, we can use variables to store values we want to reuse throughout the code. Sass variables are prepended with a `$` sign, these have scope so that we can use variables both locally and globally, which makes them quite versatile.

```css
$primary-color: seashell;
$primary-bg: darkslategrey;

body {
  color: $primary-color;

  background: $primary-bg;

}
```

#### Mixins

also you can use Mixins, it make possible to create a bunch of related CSS rules and quickly apply them to any property. For instance, the following mixin creates a simple card layout with width, height, background, and border as parameters.

```css
@mixin card($width, $height, $bg, $border) {
  width: $width;

  height: $height;

  background: $bg;

  border: $border;

}
```

 Whenever we want to create a new card, we simply call the `card` mixin using the `@include` rule and pass four arguments.

```css
.card-1 {
  @include card(300px, 200px, yellow, red 2px solid);
}
.card-2 {
  @include card(400px, 300px, lightblue, black 1px dotted);
}
```

####  @extend

The `@extend rule` brings inheritance to the Sass language.  With the `@extend` rule, we can add the properties of any class to another one in the following way:

```css
.class-1 {
  width: 100%;

  height: auto;

}
.class-2 {
  @extend .class-1;

}
```

@extend also extends all nested selectors, as Sass allows nesting as well.

#### Nesting

it highly improves code readability and maintainability. It can be used when we have selectors that share the same parent, for instance:

```css
article {
  p {
    line-height: 1.5;

  }
  img {
    max-width: 100%;

  }
}
```

#### Loops and conditionals

 they allow us to write CSS rules just like in any scripting language. Sass has a built-in `if()` function and an `@if` directive with which we can test different conditions and a `@for`, an `@each`, and a `@while` loop with which we can repeatedly output specific sets of styles. 

#### modularity

Sass supports modularity as well by letting us use partial Sass files that contain smaller code blocks we want to use many times.  Partials can be added to any other Sass file with the `@import` rule.

####  built-in functions

 The Sass preprocessor also has built-in functions we can use to convert and mix colors, manipulate strings, perform mathematical calculations, and apply other dynamic functionalities to our design. And we can define our own custom Sass functions as well.

{% embed url="https://sass-lang.com/" %}



