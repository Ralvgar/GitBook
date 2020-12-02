---
description: phases of event propagation
---

# Capturing, Target and Bubbling.

The standard [DOM Events](http://www.w3.org/TR/DOM-Level-3-Events/) describes 3 phases of event propagation:

1. Capturing phase – the event goes down to the element.
2. Target phase – the event reached the target element.
3. Bubbling phase – the event bubbles up from the element.

 Here’s the picture of a click on `<td>` inside a table, taken from the specification:

![](../.gitbook/assets/image%20%283%29.png)

 That is: for a click on `<td>` the event first goes through the ancestors chain down to the element \(capturing phase\), then it reaches the target and triggers there \(target phase\), and then it goes up \(bubbling phase\), calling handlers on its way.

