# Design Patterns

Design patterns in JavaScript are reusable templates to provide solutions to commonly occurring problems.

Design patterns help combine experiences of many developers to structure the codes in an optimized manner that meet the problems we are seeking solutions.

They decrease the overall codebase by doing away with unnecessary repetitions, thus makes our code more robust than the ad-hoc solutions.

#### Module Design Pattern

The different types of modifiers \(both private and public\) are set in the module pattern. You can create similar functions or properties without conflicts. There is the flexibility of renaming functions publicly. The daunting part of this is the inability to override the created functions from the outside environment.

```javascript
function AnimalContainter () {

    const container = [];

    function addAnimal (name) {
        container.push(name);
    }

    function getAllAnimals() {
        return container;
    }

    function removeAnimal(name) {
        const index = container.indexOf(name);
        if(index < 1) {
            throw new Error('Animal not found in container');
        }
        container.splice(index, 1)
    }

    return {
        add: addAnimal,
        get: getAllAnimals,
        remove: removeAnimal
    }
}

const container = AnimalContainter();
container.add('Hen');
container.add('Goat');
container.add('Sheep');

console.log(container.get()) //Array(3) ["Hen", "Goat", "Sheep"]
container.remove('Sheep')
console.log(container.get()); //Array(2) ["Hen", "Goat"]
```

#### Singleton Pattern

The Singleton  **pattern**  restricts the instantiation of a class to one "single" instance. This is useful when exactly one object is needed to coordinate actions across the system without having to recreate that object or losing the information inside of it.

```javascript
function DatabaseConnection () {

    let databaseInstance = null;
    
    // tracks the number of instances created at a certain time
    let count = 0;
    
    function init() {
        console.log(`Opening database #${count + 1}`);
    //now perform operation
    }
    function createIntance() {
        if(databaseInstance == null) {
            databaseInstance = init();
        }
        return databaseInstance;
    }
    function closeIntance() {
        console.log('closing database');
        databaseInstance = null;
    }
    return {
    open: createIntance,
    close: closeIntance
    }
}

const database = DatabseConnection();
database.open(); //Open database #1
database.open(); //Open database #1
database.open(); //Open database #1
database.close(); //close database
```

#### Factory Pattern

The factory pattern wraps a constructor for different types of objects and returns instances of the objects via a simple API. It makes it easy to create different objects by exposing a simple API that return the specified object type.

```javascript
const Laptop = function({ ram, hdd, name }) {
  this.ram = ram || 0;
  this.hdd = hdd || 0;
  this.name = name || "";
};
module.exports = Laptop;

const Tablet = function({ ram, hdd, name, network }) {
    this.ram = ram || 0;
    this.hdd = hdd || 0;
    this.network = network || 0;
    this.name = name || "";
};
module.exports = Tablet;


///
const Laptop = require("./laptop");
const Tablet = require("./tablet");
const gadget = { Laptop, Tablet };
module.exports = {
    createGadget(type, attributes) {
        const GadgetType = gadget[type];
        return new GadgetType(attributes);
    }
};

///
const gadgetFactory = require("./gadgetFactory");
const myLaptop = gadgetFactory.createGadget("Laptop", {
    ram: 8,
    ssd: 256,
    name: "Bab's MacBook Pro"
});
const myTablet = gadgetFactory.createGadget("Tablet", {
    ram: 4,
    hdd: 128,
    name: "Bab's iPad",
    network: '4G'
});
console.log(myLaptop); //Laptop { ram: 8, ssd: 256, name: 'Bab\'s MacBook Pro' }
console.log(myTablet); //Tablet { ram: 4, hdd: 128, network: '4G', name: 'Bab\'s iPad' }
```

#### Observer Pattern

 The observer pattern is a design pattern in which subjects \(which are simply just _objects_ with methods\) maintain a list of observers who are _registered_ to be notified of upcoming messages.

When they receive a notification event about something on the subject they are attached to, they can use these opportunities to do something useful, depending on what was received from them. Useful in situations when you need multiple objects to get notified simultaneously at the same time of recent changes to state.

```javascript
function Observer() {
    this.observerContainer = [];
}

Observer.prototype.subscribe = function (element) {
    this.observerContainer.push(element);
}

// the following removes an element from the container

Observer.prototype.unsubscribe = function (element) {

    const elementIndex = this.observerContainer.indexOf(element);
    if (elementIndex &gt; -1) {
        this.observerContainer.splice(elementIndex, 1);
    }
}

/**
* we notify elements added to the container by calling
* each subscribed components added to our container
*/
Observer.prototype.notifyAll = function (element) {
    this.observerContainer.forEach(function (observerElement) {
        observerElement(element);
    });
}
```

#### Conclusion

It is beneficial for JavaScript developers to use design patterns. Some major advantages of using design patterns include project maintainability and also cuts off unnecessary work on the development cycle.

