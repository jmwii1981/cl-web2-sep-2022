# JavaScript (JS) Fundamentals
From the video series [JS Fundamentals](https://app.pluralsight.com/library/courses/javascript-fundamentals/table-of-contents)

## Object Parameters and Arguments
**Note** When talking about object parameters and arguments, it's important to note the difference between them. A parameter is the variable in the declaration of the function. For instance, consider `foo function(parameter1, parameter2){ bar; }`. Meanwhile, an argument is the actual value of this variable that gets passed to the function. Usually an argument will get passed to the function from another source such as another variable, or from an element within an object, or even an object itself.

## Syntax Caveats of Controlling Loops
In addition to the basics of controlling loops, there are some caveats to be aware of. See the examples below for an illustration of what to look out for.

Variable initialization. Below you may see a strange syntax with an empty space before the `;` within the for loop's counter arguments. The empty space is actually ok, and the `i` var does not need to be initialized, but the `;` must be present. Above, you will see that this is because `i` has already been initialized with the zero value.

**Example**
```javascript
let i = 0;

for (; i<12; i++) {
    if (i === 8) {
        break;
    }
}
console.log(i); // Returns 8
```

Using `continue`. With `continue` in the block of the loop below, you'll notice that if i is strict equals to 2, then `continue` will execute. When the `continue` keyword or command executes it will **not** execute the remaining code block that might exist below it. Rather, `continue` acts as if any code beneath it within the loop that it resides, doesn't exist, but will continue the loop, if the loop's arguments haven't been fully fulfilled.

**Example**
```javascript
for (let i = 0; i < 4; i++) {
    if (i === 2) {
        continue; // Acts as if the loop's body has finished execution, but does not 'exit' the loop's criteria for continuing to loop the way 'break' does.
    }
    console.log(i); // Returns 0 1 3
}
```

## Rest Parameters
Rest parameters allow a function to store multiple arguments in a single array.

**Example**
```javascript
// The '...allCarIDs' is a rest parameter that will build an array called 'allCarIDs'

function sendCars(...allCarIDs) {
    allCarIDs.forEach(id => console.log(id));
}

sendCars(100, 200, 555); // All of these are arguments that are getting passed through the sendCars function, and each argument is accepted as a parameter within the function; Returns "100 200 555"

// Normal parameters and rest parameters can be mixed, but rest parameters must always be listed last, for instance, in the following example, 'day' is the normal parameter which collects the 'Monday' argument, and the rest parameter 'allCarIDs' collects the remainder of the arguments as an array of arguments

function sendCars(day, ...allCarIDs) {
    callCarIDs.forEach(id => console.log(id)); // Here, we're only planning on returning the 'ids' from the TBD allCarIDs array ... meaning, 'Monday' will be left out
}
sendCars('Monday', 100, 200, 555); // Returns "100 200 555; Monday is left out.
```

## Destructuring Arrays
We can easily assign values within an array to variables by "destructuring arrays."

**Example**
```javascript
let carIDs = [1, 2, 5];
let [car1, car2, car3] = carIDs; // Destructuring (and restructuring) happens here ...

//Essentially, this means that the above converts to :
// carIDs = [
//     "car1": 1,
//     "car2": 2,
//     "car3": 5,
//]

// Thus ...
console.log(car1, car2, car3); // 1 2 5

//******//

// **Destructuring and recompisitioning array**

let carIDs = [1, 2, 5];
let remainingCars;

[, ... remainingCars] = carIDs; // The leading comma, skips the value 1 ... you can use as many commas as you want to skip as many values as you want

console.log(remainingCars); // [2, 5]

//******//

// Using rest parameters

let CarIDs = [100, 200, 300];
let [car1, car2, ...theRest] = carIDs;

console.log(car1, car2, theRest); // Returns values 100 200; 'theRest' returns an array ... [300]; all together this looks like: "100 200 [300]"
```

## Destructuring Objects
Destructuring objects is a bit different from destructuring arrays. With objects, we'll use curly braces rather than square brackets. See the example below for more details.

**Example**
```javascript
// Destructuring an object, like so ...
let car = {id: 5000, style: 'convertible' }; // The object to destructure
let { id, style } = car; // This destructures cars into two individual vars: 'id' and 'style' which now house the values from the object itself which holds like-named keys
console.log{ id, style }; // The logging of ...; Returns 5000 Convertible

// Another way of achieving the above ...
let car = {id: 5000, style: 'convertible' };
let id, style; 
({id, style} = car);
console.log{ id, style }; // Returns 5000 Convertible
```

## Spread Syntax
Spread syntax does the opposite of rest in that it pulls arrays apart, where rest puts them together ... see the example below for more details.

**Example**
```javascript
// Example 1
function startCars(car1, car2, car3) {
    console.log(car1, car2, car3);
}

let carIDs = [100, 300, 500];

startCars(...carIDs); // Returns "100 300 500"; a spread of params


// Example 2
function startCars(car1, car2, car3) {
    console.log(car1, car2, car3);
}

let carCodes = 'abc';
startCars(...carCodes); // Spreads the value of 'abc' out into parameters so that they get returned as individuals arguments "a b c"

// Example 3
function startCars(car1, car2, car3, ...rest) {
    console.log(rest); // Returns "[4, 5, 6]" as an array
}

let carIDs = [1, 2, 3, 4, 5, 6];
startCars(...carIDs);
```

## Block and Function Scope
Below, we cover Block and Function Scope. To read about other types of scope such as module scope, lexical scope and global scope read [An introduction to scope in JavaScript, by Cristian Salcescu](https://www.freecodecamp.org/news/an-introduction-to-scope-in-javascript-cbd957022652/)

**Block scope** refers to when a 'let' var has been declared both outside of a function and within a function at the same time. Essentially, when declared and initiatlized in both places, the function's intialized 'let' var will override the one that exists outside of it's brackets (scope). This does not apply to the 'var' keyword for declaring a variable, but only the 'let' keyword for declaring a variable.

**Example**
```javascript
// Block Scope
Note: there is no such thing as 'block scope' for the 'var' keyword, this only pertains to 'let'
let message = 'outside';
if (conditional parameters) {
    let message = 'inside';
    console.log(message); // Returns 'inside'
}
console.log(message); // Returns 'outside'
```

**Function scope** refers to vars that are initialized within a function first. These vars cannot be _accessed_ outside of the function unless they have been _intialized_ outside of the function. If you attempt to access a var outside of a function when it is only initialized within a function, then you will receive a reference error.

**Example**
```javascript
// Function Scope
if (conditional parameters) {
    let message = 'inside';
}
consol.log(message); // Reference error.
```

## IIFE (Immediately Invoked Function Expression)
An IIFE is a function that is invoked immediately after it has been declared. IIFEs are a way to isolate code so that it won't interfere with other code. IIFE stands for Immediately Invoked Function Expression. 

A _function expression_ means to take a function and do something with it; usually assigning it to a variable. To be immediately invoked means to immediately run a function after it has been declared.


**Example**
```javascript
// Example 1

(function () {
    console.log("I'm an IIFE!");
})(); // The argument call ... '()' ... invokes this function

// Example 2
let app = (function() { // Everything inside of the function body gets assigned to "app"
    let carID = 123;
    console.log(`This is in the 'app' function`);
    return {}; // This empthy object would typically return a group of functions () assigned to "app. This is where the value of an IIFE comes into play as it creates a "closure"
})(); // Adding the semi-colon indicates that this function is an expression

// Example 3
let app = (function() {
    let carID = 123;
    console.log(`This is in the 'app' function`);
    return {};
})();
console.log(app); // Returns "This is in the 'app' function"; and an empty object: "{} " ... In summary, the full return looks like this: This is in the 'app' function {}

```

## Closures
When functions are invoked and run through all of their code (once they are complete) their vars, nested functions, etc. go out of scope. However, sometimes we want that function and its code setup to hang around, and that's what a closure is for.

**Example**
```javascript
// How we can create a closure with the IIFE pattern
let app = (function() { // 'app' is assigned an IIFE with the code block below
    let carID = "123"; // var 'carID' is assigned the value of "123"
    let getID = function () { // A nested function assigned the name 'getID'
        returns the value of the var 'carID' (assigned above)
    };
    return { // The var 'app' gets associated with the return value of the IIFE 'app' which all together becomes 'app.getID()'
        getID: getID // References the 'getID()' function above and returns the value of "123" per the instructions of the 'getID()' function
    };
})(); // Ends 'app' immediately invoked function expression
console.log(app.getID()); // Returns the value "123"
```

## The `this` keyword
This is a special keyword that refers to the context of an object/function.

**Example**
```javascript
// Example 1 – Using this without 'use strict'
let fn = function() {
    console.log(this === window);
}
fn(); // Returns true because the 'this' keyword is referring to the global object since we're not using 'use strict'

// Example 2
// The example below is the most common use of 'this': within functions that act as nested properties themselves of a parent object
let iAmAnObject = { // The parent object 'iAmAnObject'
    carID: 123, // The 'carID' var is assigned the value 123
    getID: function() { // The 'getID()' function is declared here
        return this.carID; // The 'this' keyword here refers to the 'iAmAnObject' object that holds the function 'getID()' and returns the value of the var 'carID' which is 123
    }
};
console.log(iAmAnObject.getID()); // Here, we access 'this.carID' and it returns the value of 123

// Example 3 – Logging out the value of 'this' from the above scenario
let iAmAnObject = {
    carID: 123,
    getID: function() {
        console.log(this); // Returns carID: 123, getID() ... etc., basically the entire object ... this is how you can test what 'this' is referencing
        return this.carID;
    }
};
```

## Using `call` and `apply`
Most of the time when you call a function, you're going to specify the opening and closing parantheticals, and place any arguments there. There are two additional ways to call a function as well using the `call` or `apply` functions. The main purpose of these two functions is to change the value of `this`. That is, to change the object which is the context of the function, and `this` is important for object-oriented scenarios. Note that `call` and `apply` do not make a "copy" of the function, but they do "call" the function.

**Example**
```javascript
// Example of 'call'

let o = {
    cardID: 123;
    getID: function() {
        return: this.cardID;
    }
};
let newCard = { cardID: 456 }; // Here we are creating a new object and assigning it a new 'cardID' value
console.log( o.getID.call(newCard) ); // We can use the original object's 'getID' method along with the 'call' function AND pass the 'newCard' object; This returns the 'newCard' object's 'cardID' value of '456'


// Example of 'apply'
// 'apply' is similar to 'call'; the only difference is that with 'apply' you have the ability to pass arguments

let o = {
    cardID: 123;
    getID: function(prefix) {
        return: prefix + this.cardID;
    }
};
let newCard = { cardID: 456 };
console.log( 0.getID.apply(newCard, ['ID: ']) ); // Here 'apply' accepts an array of arguments, and returns ID: 456
```

## Using `bind`
Unlike `call` and `apply`, we can call a `bind` on a function, and it makes a copy of that function, assigning it a new context which then applies also to `this` when `this` is used to access a value.

**Example**
```javascript
let o = {
    cardID: 123,
    getID: function() {
        return this.cardID; // This would typically return 123
    }
};
let newCard = { cardID: 456 }; // Here we create a newCard object with cardID 456
let newFn = o.getID.bind( newCard ); // Here, rather than calling 'call' or 'apply', we make a "copy" of the 'getID' function by calling 'bind' with 'getID' allowing for a new context where we can now pass the new value per 'this'
console.log( newFn() ); // Returns 456
// In summary, the copy of the original function 'getID' is now stored in a variable called 'newFn'
```

## Arrow Functions
Arrow Functions are simply a term that describes modern syntax for declaring functions.

In the below example, you will see a simple Arrow Function. The empty `()` describe the function has having no parameters listed. After the parameters list, you'll notice that there is a `=>` that indicates that this line of code is declaring an arrow function. The `123` is the return value of the function.

**Example**
```javascript
let getID = () => 123;
console.log( getID() ); // Returns '123'
```

In the first example, below, you'll notice that the Arrow Function's parameter is the _only one_ parameter declared, and thus, does not need to be wrapped in `()`. The second example demonstrates the need for the `()` when there is _more than one_ parameter.

**Example**
```javascript
// A Single Parameter
let getID = parameter => parameter + 123;
console.log( getID('ID: ') ); // Returns 'ID: 123'

// Multiple Parameters
let getID = (parameter1, parameter2) => parameter1 + 123 + parameter2;
console.log( getID('ID: ', '!') ); // Returns 'ID: 123!'
```

## Template Literals and Interpolation
A string literal or anonymous string is a string value in the source code of a computer program. String interpolation is replacing placeholders with values in a string literal.

Normally, when you want to combine output from expressions along with a string's set of  characters or words, you'd concatenate them using the addition operator `"Hi, I'm " + name + " ."` in order to create a full expression ready for output. However, this can make code hard to read. So instead (as of ES 2015), we can now use Template Literals and String Interpolation with backtics and placeholders `` `Hi, I'm ${name}.` ``.

In order to create a template literal, you must enclose a string expression with backticks `` ` `` instead of double `"` or single `'` quotes. 

Placeholders are expressions delimited by a dollar sign and curly braces which are embedded within a string literal `${expressionPlaceholder}`.

You can see an example dof template literals below.

**Example**
```javascript
let trackCar = function(carID, city = 'NY') {
    console.log(`Tracking ${carID} in ${city}.`); // Not the backticks in this example.
}

console.log(trackCar(123)); // Returns 'Tracking 123 in NY.'
console.log(trackCar(123, 'Chicago')); // Returns 'Tracking 123 in Chicago.'
```

## Default Parameters
Parameters can be given default values as of ES 2015. In the example below, you can see that `city` has been set to the 'default value' of `NY`.

**Example**
```javascript
let trackCar = function(carID, city = 'NY') {
    console.log(`Tracking ${carID} in ${city}.`);
}

console.log(trackCar(123)); // Returns 'Tracking 123 in NY.'
console.log(trackCar(123, 'Chicago')); // Returns 'Tracking 123 in Chicago.'
``` 

## Constructor Functions
Constructor Functions are used to instantiate new objects. While it looks a lot like a regular function, it behaves differently in that it acts as a blueprint for its own instances.

In the example below, we have a constructor function `Car()`. Notice the use of a capital 'C' in the constructor function's name. Capitalizing the first letter of a function's name is a convention reserved for constructor functions.

**Example**
```javascript
function Car() { // Car() is a new object aka constructor function

}
let car = new Car();
```

In the below example, we create an object called `Vehicle()`. This object has two properties and a function. The function is called a 'method' in this case because it's attached to the object `Vehicle()`. Further, in this particular case, the method is attached _directly_ to the object `Vehicle()`. Learn more about why this is important in the next section on 'Prototypes'.

**Example**
```javascript
function Vehicle(make, model) {
    this.make = make; // property
    this.model = model; // property
    this.start = function() { // method
        console.log('Start the ' + this.make + " " + this.model + '!');
    };
}

let car = new Vehicle('Kia', 'Forte');
car.start(); // Returns 'Start the Kia Forte!'
```

## Prototypes
Rather than copying the method from the previous example within every instance of the `Vehicle()` object we created (i.e. `car`), we can use prototype to attach the function separately. Doing this will save memory as more and more instances of `Vehicle()` are created.

**Example**
```javascript
function Vehicle(make, model) {
    this.make = make;
    this.model = model;
}

Vehicle.prototype.start = function() {
    console.log('Start the ' + this.make + " " + this.model + '!');
}

let car = new Vehicle('Kia', 'Forte');
car.start(); // Returns 'Start the Kia Forte!'
```

## Expanding Objects Using Prototypes
The most common use of prototypes is to attach methods to objects. The second most common use is to expand objects by giving new functionality to all instances of an object. In the example below, we can use the built-in `String()` object and expand it with new functionality by attaching a new prototype called 'hello'.

**Example**
```javascript
String.prototype.hello = function() {
    return this.toString() + ', hello';
};
console.log('foo'.hello()); // Returns 'foo, hello'
```

## JS Object Notation (JSON)
The purpose of JSON is to transmit JS objects over the wire. In most cases, JSON can be used to work with an API such as a RESTful API on the web. To convert JS objects to JSON, you can use the global JSON object together with the `.stringify()` method. All together ... `JSON.stringify(arguments)`.

**Example**
```javascript
// Convert a JS Object to JSON
let car = {
    id: 123,
    style: 'convertible'
};
console.log( JSON.stringify(car) ); // Returns '{"id": 123, "style": "convertible"}'

// Convert an Array to JSON
let carIDs = [
    { carID: 123 },
    { carID: 456 },
    { carID: 789 },
];
console.log( JSON.stringify(carIDs) ); // Returns '[{"carID": 123}, {"carID": 456}, {"carID": 789}]'
```

What if we need to accept JSON from another server and convert it into a JS object for us to use? We'll need to parse the JSON string that we've received. In the example below, we create a variable called `jsonIn` which has accepted the JSON string that we've just received. Then, we use the global `JSON` object's `parse()` method to pass the jsonIn argument we've created, and in turn, the `parse()` method creates a JS object for us to use within our code.

**Example**
```javascript
// Parsing JSON
let jsonIn =
`
    [
        {"carID": 123},
        {"carID": 456},
        {"carID": 789}
    ]
`;
let carIDs = JSON.parse(jsonIn);
console.log(carIDs); // Returns ''
```

## Array Iteration
You may iterate an array object using either of the global `Array` object's methods: `forEach()`, `filter()`, `every`, or `find`.

In the example below, the `forEach()` method is called on the `carIDs` Array object. When this runs, we use an arrow function `car => console.log(car)` to declare a parameter `car` and then log out each instance of the `car` parameter using each property of the `carIDs` array as an argument. Similarly, when passing an additional parameter `index` within our arrow function `car => console.log(car, index)` and then logging it out, we receive not only one of the `carIDs` array's properties (a car parameter object), but we also receive the numerical value of the index where that car object sits in the array.

**Example**
```javascript
let carIDs = [
    { carID: 123, style: 'sedan'},
    { carID: 456, style: 'convertible' },
    { carID: 789, style: 'sedan' }
];

// Logging out each of the three car objects
carIDs.forEach(car => console.log( car ));

// Logging out each of the three car objects along with the index of where it sits in the array
carIDs.forEach((car, index) => console.log( car, index ));
```

To _filter_ an array so that a specific property or set of properties is returned, you would use the `filter` method by calling the `filter` method on your `carIDs` array object as is shown in the example below. Then when you log out the `convertibles` parameter with `console.log()` you'll notice that the only `carID` that was returned was `456`. That's because it's the only instance of the `carIDs` array's properties that matches the filter value `'convertible'`.

**Example**
```javascript
let carIDs = [
    { carID: 123, style: 'sedan'},
    { carID: 456, style: 'convertible' },
    { carID: 789, style: 'sedan' }
];

let convertibles = carIDs.filter(
    car => car.style === 'convertible'
);

console.log(convertibles);
```

The `every` method searches through an array with a given test condition and returns a boolean value of `true` or `false` based on how that condition is met. This test condition is applied to all array elements. In the example below, `car => car.carID > 0` is validating whether the carID exists on each element.

**Example**
```javascript
let carIDs = [
    { carID: 123, style: 'sedan'},
    { carID: 456, style: 'convertible' },
    { carID: 789, style: 'sedan' }
];

let result = carIDs.every(
    car => car.carID > 0
);

// Here we log 'ALL' of the car objects because the `carID` values are all greater than `0`.
console.log(result);
```

`find` will locate a single instance of an array element that matches a given test condition.

**Example**
```javascript
let carIDs = [
    { carID: 123, style: 'sedan'},
    { carID: 456, style: 'convertible' },
    { carID: 789, style: 'sedan' }
];

let car = carIDs.find(
    car => car.carID > 500
);

// Here we log out the first instance of 'carID' where the value of 'carID' is greater than 500
console.log(car);
```

## JS Classes

Below is a basic example of how to write a Class in JS.

**Example**
```javascript
class Car {

}

let car = new Car();
```

## Class Constructors, Properties and Methods
A Constructor is a function that gets executed when a new instance of an object gets created.

When working with Constructors always use the `this` keyword when creating properties of those Constructors.

Below is an example of a Constructor Function within a Class.

**Example**
```javascript
class Car {
    constructor(id) {
        thid.id = id; // Here we use the 'this' keyword
    }
}

let car = new Car(123);
console.log(car.id); // Returns '123'
```

Methods are functions that exist on an object.

**Example**
```javascript
class Car {
    constructor(id) {
        this.id = id;
    }
    identify() { // Our method. Notice we don't need a 'function' keyword, we can just go right ahead and name it.
        return `Car ID: ${this.id}`;
    }
}

let car = new Car(123); // Instantiation of new 'car' with 'Car' class
console.log(car.identify()); // Returns 'Car ID: 123'
```

With Methods, since we can pass arguments, you could also do this ...

**Example**
```javascript
class Car {
    constructor(id) {
        this.id = id;
    }
    identify(suffix) { // We add the parameter suffix
        just go right ahead and name it.
        return `Car ID: ${this.id}${suffix}`;
    }
}

let car = new Car(123);
console.log(car.identify('!!!')); // We pass the argument '!!!'; Returns 'Car ID: 123!!!'
```

## Inheritance and Classes
One way to avoid duplicating code (keeping code DRY) is to use Inheritance. Classes make Inheritance easy.

In the example below, let's say that we have a Class called `Vehicle`, and we might have several different types of vehicles with their own Classes that can be derived from the _Super Class_, `Vehicle`.

**Example**
```javascript
// The Super Class, 'Vehicle'
class Vehicle {
    constructor() {
        this.type = 'No vehicle type declared'; // Here we set the 'type' default to 'No vehicle declared'
    }
    start() {
        return `Starting: ${this.type}`;
    }
}

// The new 'Car' class that is derived from the 'Vehicle' Class (or _extends_ the 'Vehicle' Class) and inherits the 'Vehicle' Class's properties
class Car extends Vehicle {

}
let car = new Car();
console.log( car.type ); // Returns 'No vehicle type declared', which is inherited from the 'Vehicle' Super Class
```

In the next example below, we want to have the `Car` Class which `extend`s the `Vehicle` class to return some additional information.

**Example**
```javascript
class Vehicle {
    constructor() {
        this.type = 'No vehicle type declared';
    }
    start() {
        return `Your ${this.type}`;
    }
}

class Car extends Vehicle {
    constructor() {
        super(); // MUST call 'super()' to call the constructor from the original class before you can extend this new constructor with new properties
        this.make = 'No make declared';
        this.model = 'No model declared';
    }
    start() { // This method will override the method from the Super Class
        return `${super.start()} is a ${this.make} ${this.model}.`;
    }
}
let car = new Car();
    car.type = 'car';
    car.make = 'KIA';
    car.model = 'Sportage';
console.log( car.start() ); // Returns 'Your car is a KIA Sportage.'
```


## Modules, and Importing and Exporting Them with Webpack
Modules are used to organize JS code. Any JS code can be placed in a file that represents a block of code we call a Module. Conventionally, Modules are usually organized into a folder called 'modules' within your project. Within that folder, files are placed to organize the code. 

**Note:** In order to use the strategy in the examples below with the JS syntax's `import` and `export` keywords, you must install Webpack within your development environment to simplify file references in your HTML file via "bundling" which is a service that Webpack provides. There is not a tutorial of how to bundle files for easier reference in your HTML files below. So, read the documentation on Webpack to learn more about how this is done.
[Learn more about Webpack](https://webpack.js.org/concepts/).

And, though you may use [Webpack](https://webpack.js.org/concepts/) for simplified HTML JS file references via Webpack's bundling feature, as mentioned above, you may also use other solutions provided via well known and stable JS package managers, frameworks, etc. These other solutions all come with their own set of concepts and implementation methods. Here are links to the documentation of some noteworthy solutions, to name a few ...
 - [Node Package Manager (NPM)](https://www.npmjs.com/)
 - [Gulp](https://gulpjs.com/)
 - [Babel](https://babeljs.io/)
 - [Parcel](https://parceljs.org/)
 - [Grunt](https://gruntjs.com/)
 - [RequireJS](https://requirejs.org/)

Below, see an example of how a Module is created and used in JS.

**Example**

In a new folder called **'modules'** and a new file called **'vehicles.js'** the following code is added with the keyword `export`.
```javascript
export class Vehicle {
    constructor() {
        this.type = 'No vehicle type declared';
    }
    start() {
        return `Your ${this.type}`;
    }
}
```

Within your **'modules'** folder you create a new folder called **'vehicles'** and add a file called **'cars.js'**. From there, you add the following line of code to the **'cars.js'** file with the `import` keyword.
```javascript
import { Vehicle } from '../vehicles.js'

class Car extends Vehicle {
    constructor() {
        super(); // MUST call 'super()' to call the constructor from the original class before you can extend this new constructor with new properties
        this.make = 'No make declared';
        this.model = 'No model declared';
    }
    start() { // This method will override the method from the Super Class
        return `${super.start()} is a ${this.make} ${this.model}.`;
    }
}
let car = new Car();
    car.type = 'car';
    car.make = 'KIA';
    car.model = 'Sportage';
console.log( car.start() ); // Returns 'Your car is a KIA Sportage.'
```

Lastly, after the above setup, remember, you'll need to use [Webpack](https://webpack.js.org/concepts/) to bundle and reference the files appropriately within your project.


## Programming the Browser Object Model (BOM) and Document Object Model (DOM)
Referencing different methods of the BOM and DOM can be useful for a variety of things. For instance, BOM can be used to change the URL you're pointing at, get information form the URL, etc. The DOM is equally as useful for manipulating the webpage document. 

Below are some simple things to note about JS programming referencing the BOM and DOM objects and their methods.


## The `window` Object
`window` is the global Object in JS. Below is a table listing of some of the Properties, Methods, and Events attached to the `window` Object.

| Properties                   | Methods   | Events       |
| :---                         | :---      | :---         |
| document _(the DOM)_         | alert()   | (not common) |
| location _browser location_  | back()    |              |
| console                      | confirm() |              |
| innerHeight                  |           |              |
| innerWidth                   |           |              |
| pageXOffset                  |           |              |
| pageYOffset                  |           |              |

With `window` being the global Object, everything gets passed to `window`. However, when working with a module, you must reference `window` separately. See the examples below.

**Example**

Here we create a variable `year` and then reference it as part of the `window` Object.
```javascript
let year = 1956;
console.log(window.year); // Returns '1956'
```

**Example**

Here we use a Module, and as you can see, a `ReferenceError` is returned. You must declare variables when working with Modules because those variables will not be placed on the `window` object the way they are when a Module isn't being imported.
```javascript
import { Vehicle } from '../vehicles.js'
let year = 1956;
console.log(window.year); // Returns 'ReferenceError: year is not defined'
```

**Example** `[check this knowledge]`

In modules, a variable declared outside any function is hidden and not available to other modules unless it is explicitly 
exported. To resolve this issue, we can use the `let` keyword to declare the `year` variable at the Module (file) level and then export it for use.

In **vehicles.js** `[check this knowledge]`
```javascript
// module 'vehicles.js'

class Vehicle {
    constructor() {
        this.type = 'No vehicle type declared';
    }
    start() {
        return `Your ${this.type}`;
    }
}

let year = 1956;

export { Vehicle, year };
```

Then, in **year.js** `[check this knowledge]`
```javascript
// file 'year.js'

import { year, Vehicle } from '../vehicles.js'
console.log(window.year); // Returns '1956'
```

## Timers
Timers fire asynchronously so that events can get handled and other code can execute while you're waiting for a timer to fire. Timers are used for animation, to handle things with the user interface, for video games, and lot of other uses.

Some timer functions ...
 - `setTimeout()`
 - `setInterval()`

**Example**

`setTimeout()` will fire only once. The first parameter is a function that logs out a message and the second parameter is the number of milliseconds setTimeout should wait before executing its first parameter. If `clearTimeout()` is called, then it will cancel the setTimeout method all together before it fires unless you call it first. Think of this as erasing it before or after it's used. See the example below for usage.

```javascript
let timeoutID = setTimeout(
    function() {
        console.log(`1 second just passed!`); // Returns '1 second just passed!' each second
    },
    1000 // 1,000 milliseconds equates to 1 second
);

// Cancel setTimeout()
clearTimeout(timeoutID);
```

**Example**

`setInterval()` will fire its first parameter repeatedly based on the second parameters measurement of time until it is canceled. Below, we are passing it two arguments. One is a function that logs out a message to the console, and the other is the length in milliseconds (intervals) we wish for it wait or pause before firing.

If you need to cancel the repeatedly firing `setInterval()` method, you can do so by setting it to the `intervalID` variable and then using the `clearInterval()` method like in the example below.

```javascript
let intervalID = setInterval(
    function() {
        console.log(`1 second just passed!`); // Returns '1 second just passed!' each second
    },
    1000 // 1,000 milliseconds equates to 1 second
);

// Cancel setInterval()
clearInterval(intervalID);
```


## The `location` Object
The `location` object is attached to the DOM Object. The `location` Object gives us information on the URL that the browser is pointing to. Below are some properties, methods, and events that the `location` object can be used with.

| Properties | Methods  | Events       |
| :---       | :---     | :---         |
| href       | assign() | (not common) |
| hostname   | reload() |              |
| port       |          |              |
| pathname   |          |              |
| search     |          |              |

Below, we'll log out the `location` object's `href` property on both the global `window` Object and the `document` Object.

**Example**
```javascript
// location property on 'window' Object
console.log(location.href); // Returns '://the-url-in-your-browsers-address-bar.net'

// similarly ...
console.log(window.location.href); // Returns '://the-url-in-your-browsers-address-bar.net'

// location property on 'document' Object
console.log(document.location.href); // Returns '://the-url-in-your-browsers-address-bar.net'
```

## The `document` Object
Common properties, methods, and events used with the `document` Object are ...

| Properties | Methods                  | Events       |
| :---       | :---                     | :---         |
| body       | createElement()          | onload       |
| forms      | createEvent()            | onclick      |
| links      | getElementById()         | onkeypress   |
|            | getElementsByClassName() |              |

## Selecting DOM Objects
To select the `document` Object's elements, we use the following like so...
 - `document.getElementById('elementID');`
 - `document.getElementsByClassName('elementsClassName');`
 - `document.getElementsByTagName('elementsTagName');`

## Modifying DOM Objects
We modify the `document` Object's elements because we conventionally wish to change their properties, set up event handlers, and modify the visual aspect of the web page any way we'd like. In order to modify a `document` Object's element, we need to select it first (see above).

Here are a few things we can do to modify the `document` Object's elements after we select the element we'd like to modify ...
**Example**
```javascript
let element = document.getElementById('elementID');
```
 - element.textContent = '';
 - element.setAttribute('attribute-name', 'attribute-value');
 - element.classList.add('classNameToAdd');
 - element.style.color = 'blue';

## Error Handling Using `try` and `catch`
When running into an error in a JS application, execution will halt and an error will get thrown. This is the default behavior. However, in most cases, we don't want the entire JS application to stop executing just because a specific code block has failed. We can handle this gracefully using the `try` and `catch` keywords.



**Example**
```javascript
```

## TITLE
Text_here

**Example**
```javascript
```

## TITLE
Text_here

**Example**
```javascript
```

## TITLE
Text_here

**Example**
```javascript
```

## TITLE
Text_here

**Example**
```javascript
```

## TITLE
Text_here

**Example**
```javascript
```