# DOM

Before explaning DOM, An overview of a web browser:

* **The Navigator** represents the state and identity of the browser, which is in JavaScript represented by the `Navigator` object. We can use this object to retrieve things like the user-agent, user’s settings or access user’s computer hardware i.e. webcam etc.
* **The Window** is the browser tab that a web page is loaded into, which is represented by the `Window` object in JavaScript. We can do many things with this object such as get the current width/height of the window, access user’s storage or attach an event handler…
* The **Document** is the actual page loaded into the window, and is represented in JavaScript by the `Document` object. This is also as known as DOM, the super star in the web development. Most of the modifications we made to the web is by manipulating the document.

 **The Document Object Model**

DOM is the thing that gets generated after your browser parses the HTML that it gets. The DOM tree consist in many types of nodes:

* **Element node**: An element, as it exists in the DOM.
* **Root node**: The top node in the tree, which in the case of HTML is always the `HTML` node \(other markup vocabularies like SVG and custom XML will have different root elements\).
* **Child node**: A node _directly_ inside another node. For example, `IMG` is a child of `P` in the above example.
* **Descendant node**: A node _anywhere_ inside another node. For example, `IMG` is a child of `P` in the above example, and it is also a descendant. `IMG` is not a child of `BODY`, as it is two levels below it in the tree, but it is a descendant of `BODY`.
* **Parent node**: A node which has another node inside it. For example, `BODY` is the parent node of `P` in the above example.
* **Sibling nodes**: Nodes that sit on the same level in the DOM tree. For example, `H1` and `P` are siblings in the above example.
* **Text node**: A node containing a text string.

## D**OM manipulation** <a id="2a17"></a>

 The concept of DOM Manipulation can be broken down to **CRUD**, to make it more understandable.

 CRUD stands for **Create, Read, Update and Delete.** In reference to DOM, it ****refers to:  
_**1.** Creating DOM Nodes  
**2.** Reading the DOM Nodes  
**3.** Updating the DOM Nodes  
**4.** Deleting the DOM Nodes_

### Reading DOM Nodes

There are many ways to read/access the DOM nodes. Some of the most important ones are:

**querySelector**

The querySelector\(\) method \(of the document object\) returns the **first element** that matches a specified _CSS selector\(s\)_ in the document.

```text
Syntax: document.querySelector(‘<CSS Selector>’);
```

**Important:** [Click here](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors) to access the list of various CSS Selectors.document.querySelector\(\)

**querySelectorAll**

The querySelectorAll\(\) method \(of the document object\) returns **all** **elements** that match a specified _CSS selector\(s\)_ in the document.

```text
Syntax: document.querySelectorAll(‘<CSS Selector>’);
```

### Updating DOM Nodes

**Every node** in the DOM has a set of **properties** and **methods** attached to it.

These properties and methods are used to update the respective DOM nodes.

For instance:  
To change the **text** node of a particular element node, **innerText** property of element node is used.

```text
Syntax: elementNode.innerText = 'Modified Text';
```

### Creating DOM Nodes

Different types of DOM nodes are created using **different syntaxes**.

```text
//creating a new element node
Syntax: document.createElement('<HTML element>');//creating a new text node
Syntax: document.createTextNode('New text content');
```

## Adding elements to DOM <a id="b721"></a>

The nodes that are created using JavaScript, need to be **added to the DOM** also, else there is **no use** of creating the node.

Addition of a node to the DOM **makes it visible** in the browser.

The **newly created** node is **appended** to an **existing** node. This is done by using **appendChild\(\)**.

**appendChild**

```text
Syntax: elementNode.appendChild(elementNode);
```

### Example:

This quotes of code are from[ Smoothie List project](https://github.com/Ralvgar/Smoothies).

```javascript
document.addEventListener("DOMContentLoaded", () => {
  // Select necessary elements from DOM
  trainBtnEl = document.getElementById('btn-train');
  resetBtnEl = document.getElementById('btn-reset');
  predictBtnEl = document.getElementById('btn-predict');
  numericResultEl = document.getElementById('numeric-result');

  // Attach necessary event listeners
  trainBtnEl.addEventListener('click', onClickOnTrain);
  resetBtnEl.addEventListener('click', onClickOnReset);
  predictBtnEl.addEventListener('click', onClickOnPredict);

  initializeSmoothieList();
  renderSmoothieListToDOM(smoothieList);
  renderStarStatesFromSmoothieList(smoothieList);
});
```

```javascript
const renderStarStatesFromSmoothieList = () => {
  const smoothieElements = document.querySelectorAll('.smoothie-list-item');
  smoothieElements.forEach((smoothieEl, idx) => {
    const stars = smoothieEl.querySelectorAll('.star');
    stars.forEach(star => star.classList.remove('star--active'));
    stars[smoothieList[idx].value].classList.add('star--active');
  })
}
```

```javascript
const renderSmoothieListToDOM = (smoothieList) => {
  smoothieList.forEach((smoothie, idx) => {

    // Creates necessary elements and appends them to the DOM
    const ulEl = document.createElement('ul');
    const smoothieContainerEl = document.createElement('div');
    smoothieContainerEl.appendChild(ulEl)

    // CSS
    smoothieContainerEl.setAttribute("class", "col-6 text-center smoothie-list-item");

    // Generate fruit list elements
    const fruitLiItems = smoothie.fruits.map(fruit => {
      const li = document.createElement('li');
      li.textContent = fruit;
      li.setAttribute("class", "list-inline-item h1 mx-0");
      return li;
    });

    // Generate star list elements
    const starLiItems = generateStarLiItems((value) => onClickOnStar(idx, value));
    [...fruitLiItems, ...starLiItems].forEach((li) => ulEl.appendChild(li));

    // Select element to insert div elements
    const smoothieListContainerEl = document.querySelector('#smoothie-list-container');

    // Append UL to DIV and DIV to DOM
    smoothieContainerEl.appendChild(ulEl)
    smoothieListContainerEl.appendChild(smoothieContainerEl);
  })
};
```

## &lt;template&gt; Tag

Another method I could have used is the &lt;template&gt; tag, it's used to hold some content that will be hidden when the page loads and then with JavaScript you can display it.

Code from my classmate [Josemi](https://github.com/JosemiChaves9):

```javascript
<template id="smoothie-template">
    <div class="smoothie d-flex justify-content-center">
        <div class="list-inline pr-5">
            <ul>
                <li class="list-inline-item m-0"></li>
                <li class="list-inline-item m-0"></li>
                <li class="list-inline-item m-0"></li>
                <li class="list-inline-item m-0"></li>

            </ul>
        </div>
        <div>
            <ul class="rating">
                <li class="list-inline-item star star--active" data-score="1">⭐</li>
                <li class="list-inline-item star" data-score="2">⭐</li>
                <li class="list-inline-item star" data-score="3">⭐</li>
                <li class="list-inline-item star" data-score="4">⭐</li>
                <li class="list-inline-item star " data-score="5">⭐</li>
            </ul>
        </div>
    </div>
</template>

///

const template = document.getElementById("smoothie-template");

const renderSmoothieListToDom = (smoothieList) => {
    smoothieList.forEach((smoothieData, idx) => {
        const clone = template.content.cloneNode(true);
        var li = clone.querySelectorAll("li");
        li[0].textContent = smoothieData.smoothie[0];
        li[1].textContent = smoothieData.smoothie[1];
        li[2].textContent = smoothieData.smoothie[2];
        li[3].textContent = smoothieData.smoothie[3];
        setStarEventListeners(clone, idx);
        container.append(clone);
    });
};
```



