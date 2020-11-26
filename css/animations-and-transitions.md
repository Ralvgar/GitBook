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

```css
.box {
  background: #2db34a;
  border-radius: 6px;
  transition: background .2s linear, border-radius 1s ease-in 1s;
}
.box:hover {
  color: #ff7b29;
  border-radius: 50%;
}

```

## Animations

An animation lets an element gradually change from one style to another. You can change as many CSS properties you want, as many times you want. 

To use CSS animation, you must first specify some keyframes for the animation. Keyframes hold what styles the element will have at certain times.

#### Animations Keyframes

 The `@keyframes` rule includes the animation name, any animation breakpoints, and the properties intended to be animated.

To get an animation to work, you must bind the animation to an element.

```css
@keyframes slide {
  0% {
    left: 0;
    top: 0;
  }
  50% {
    left: 244px;
    top: 100px;
  }
  100% {
    left: 488px;
    top: 0;
  }
}

```

#### Animation Name

 To do so, the `animation-name` property is used with the animation name, identified from the `@keyframes` rule, as the property value. The `animation-name` declaration is applied to the element in which the animation is to be applied to.

#### Animation Duration, Timing Function, & Delay

Animations need a duration declared using the `animation-duration` property. As with transitions, the duration may be set in seconds or milliseconds.

 A timing function and delay can be declared using the `animation-timing-function` and `animation-delay` properties respectively, it works like transitions.

#### Animation Iteration

By default, animations run their cycle once from beginning to end and then stop, you can use animation-iteration-count to have an animation repeat.  Values for the `animation-iteration-count` property include either an integer or the `infinite` keyword.

#### Animation Direction

You may declare the direction an animation completes using the `animation-direction` property.

 Values for the `animation-direction` property include `normal`, `reverse`, `alternate`, and `alternate-reverse`.

#### Animation Play State

 The `animation-play-state` property allows an animation to be played or paused using the `running` and `paused` keyword values respectively.

#### Animation Fill Mode

 The `animation-fill-mode` property identifies how an element should be styled either before, after, or before and after an animation is run. The `animation-fill-mode` property accepts four keyword values, including `none`, `forwards`, `backwards`, and `both`.

### Shorthand Animation <a id="shorthand-animations"></a>

 Fortunately [animations](https://developer.mozilla.org/en-US/docs/CSS/Using_CSS_animations), just like transitions, can be written out in a shorthand format.

 The order of values within the `animation` property should be `animation-name`, `animation-duration`, `animation-timing-function`, `animation-delay`, `animation-iteration-count`, `animation-direction`, `animation-fill-mode`, and lastly `animation-play-state`.

```css
.stage:hover .ball {
  animation: slide 2s ease-in-out .5s infinite alternate;
}
.stage:active .ball {
  animation-play-state: paused;
}

```

