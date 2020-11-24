# OOCSS

OOCSS advocates the separation of structure from skin. The methodology makes a clear distinction between content and its containers.

In OOCSS, style rules are written exclusively using CSS class selectors.

a goal of the OOCSS methodology is to reduce duplication of the same properties throughout your various style rules.

```css
.button {
  box-sizing: border-box;
  height: 50px;
  width: 100%;
}
.grey-btn {
  background: #EEE;
  border: 1px solid #DDD;
  box-shadow: rgba(0, 0, 0, 0.5) 1px 1px 3px;
  color: #555;
}
```

