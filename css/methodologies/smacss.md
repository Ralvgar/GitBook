# SMACSS

This methodology focuses on 5 main types of structures to organize our CSS:

&#x20;**Base**: Base styles are, that apply to base selectors. These should be very simple such as font color and family, link styles, etc.

```css
body { font-family: sans-serif; }
p { font-size: 1rem; }
a { text-decoration: none; }
```

&#x20;**Layout**: Layout styles are meant for logic-less container elements that are solely included in your HTML to provide positioning, padding, or other layout-based purposes.  By default, SMACSS recommends us to begin our layout styles with the** l- prefix**:

```css
.l-container { max-width: 58rem; margin-left: auto; margin-right: auto; }
.l-horizontal-padding { padding: 0 1em; }
```

&#x20;**Module: **most of the CSS of our web pages. We should style a block of HTML code with independent, semantic content as a module with children elements.

```css
.menu { list-style: none; }
// child element of menu
.menu-item { float: left; padding: 1em; }
```

&#x20;**State**: States are the styles that should be triggered by Javascript (i.e. showing an element, hiding an element, marking an element as active, etc.) — and should normally begin with the **is- prefix:**

```css
.is-hidden { position: absolute; left: -999rem; }
.is-visible { position: static; }
```

&#x20;**Theme**: The purpose is to provide styles for various themes — where the core styles of a series of pages stay the same, but small things may change like background colors, fonts, etc.
