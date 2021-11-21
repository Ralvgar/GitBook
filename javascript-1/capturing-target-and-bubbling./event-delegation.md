# Event delegation

Event delegation is a pattern to handle events efficiently. We add an event listener to a parent element and call an event on a particular target using the .target property of the event object.

```
const customUl = document.createElement('ul');

function responding(evt) {
    if (evt.target.nodeName === 'li')
        console.log('Responding')
}

for (var i = 1; i <= 10; i++) {
    const newElement = document.createElement('li');
    newElement.textContent = "This is line " + i;
    customUI.appendChild(newElement);
}

customUI.addEventListener('click', responding);
```

In order to avoid unnecessary function creations, instead of creating one function for each element, or create only one function and pass to every event listener the reference of the function. **We only create the event listener once** into the parent component and we capture the target into the function, then when the parent is clicked, the event goes in the capturing phase, reaches to the target and switches to the bubbling phase. When it hits the parent returning back, it runs the event listener, and with event.target inside the function we have access to the element that was clicked.

{% embed url="https://javascript.info/event-delegation" %}
