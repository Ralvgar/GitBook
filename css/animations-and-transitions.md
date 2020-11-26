---
description: >-
  Transitions provide a change from one state to another, while animations can
  set multiple points of transition upon different keyframes.
---

# Animations & Transitions

## Transitions

With a transition an element have to change in state and different styles must be identified for each state. For determining styles for diferents states we use  `:hover`, `:focus`, `:active`, and `:target` pseudo-classes.

#### **Transitional Properties**

determines exactly what properties will be altered, we can use the keyword `all` to transition all properties of an element. Not all properties may be transitioned.

#### Transition Duration

That property defines the length of time that a transition takes. Can be set using general timing values, including seconds \(`s`\) and milliseconds \(`ms`\). 

#### Transition Timing

That property describes how the intermediate values used during a transition will be calculated. It allows for a transition to change speed over its duration. A few of the more popular keyword values are   `linear`, `ease-in`, `ease-out`, and `ease-in-out`.

#### Transition Delay

That property defines when the transition will start. Can be set using general timing values, including seconds \(`s`\) and milliseconds \(`ms`\). 

#### Shorthand Transition

 Using the `transition` value alone, you can set every transition value in the order of `transition-property`, `transition-duration`, `transition-timing-function`, and lastly `transition-delay`.

### Animations <a id="animations"></a>

\*\*\*\*

