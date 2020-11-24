# BEM

BEM is to differentiate CSS classes that fulfill different roles. This is done by naming CSS classes in a way that indicates their role.

BEM complements OOCSS.

A **block** is an independent, modular UI component. A block may be composed of multiple HTML elements, or even multiple blocks.  

An **element** is a component of a block. An element serves a singular purpose. For example, if you have a navigation menu block, then elements of it might be your navigation menu’s links

 A **modifier** is a CSS class that changes the default presentation of a block or element.

This is the BEM class-naming syntax:

* `.block`
* `.block--modifier`
* `.block__element`
* `.block__element--modifier`

```markup
<form class="loginform loginform--errors">
  <label class="loginform__username loginform__username--error">
    Username <input type="text" name="username" />
  </label>
  <label class="loginform__password">
    Password <input type="password" name="password" />
  </label>
  <button class="loginform__btn loginform__btn--inactive">
    Sign in
  </button>
</form>
```

