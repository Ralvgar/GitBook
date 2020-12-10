# LESS: Leaner Style Sheets

 LESS uses the standard CSS syntax with the `.less` file extension. This means that a valid `.css` file is a valid `.less` file as well. Therefore, it’s really easy to pick up the syntax if you already know CSS, even if LESS has a few extra elements that you won’t find in CSS, such as the `@` sign for variables.

 LESS variables also have scopes which make them accessible where they are defined and called. Moreover, they cannot only be used within CSS rules but also inside selector and property names, URLs, and `@import` statements. For instance, we can store frequently used URL paths in variables and access them whenever we need.

```css
@uploads: “../wp-content/uploads/”;
header {
  background-image: url(“@{uploads}/2018/03/bg-image.jpg);
}
```

 LESS mixins let us reuse a set of related style rules throughout the code. LESS also provide us with specific [guarded mixins](http://lesscss.org/features/#mixins-feature-mixin-guards-feature) that implement a basic conditional logic in LESS.

```css


.text-color (@bg-color) when (lightness(@bg-color) >= 50%) {
  color: black;
}
.text-color (@bg-color) when (lightness(@bg-color) < 50%) {
  color: white;
}
.text-color (@bg-color) {
  background-color: @bg-color;
}
.card-1 {
  .text-color (yellow);
}
.card-2 {
  .text-color (darkblue);
}
```

{% embed url="http://lesscss.org/" %}



