# Specificity

The browser follows some rules to determine which CSS rule is most specific and therefore wins out.

### Specificity Hierarchy

Every selector has its place in the specificity hierarchy. There are four categories which define the specificity level of a selector:

**Inline styles** - An inline style is attached directly to the element to be styled. &lt;h1 style="color: \#ffffff;"&gt;.

**IDs** - An ID is a unique identifier for the page elements. such as \#navbar.

**Classes, attributes and pseudo-classes** - This category includes .classes, \[attributes\] and pseudo-classes such as :hover, :focus etc.

**Elements and pseudo-elements** - This category includes element names and pseudo-elements, such as h1, div, :before and :after.

### How to Calculate Specificity?

Start at 0, add 1000 for style attribute, add 100 for each ID, add 10 for each attribute, class or pseudo-class, add 1 for each element name or pseudo-element.

![](../.gitbook/assets/image%20%281%29.png)

 **Equal specificity: the latest rule counts**

