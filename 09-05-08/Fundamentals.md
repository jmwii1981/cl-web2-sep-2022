# JavaScript Fundamentals
From the video series [JavaScript Fundamentals](https://app.pluralsight.com/library/courses/javascript-fundamentals/table-of-contents)

## Object Parameters and Arguments
**Note** When talking about object parameters and arguments, it's important to note the difference between them. A parameter is the variable in the declaration of the function. For instance, consider `foo function(parameter1, parameter2){ bar; }`. Meanwhile, an argument is the actual value of this variable that gets passed to the function. Usually an argument will get passed to the function from another source such as another variable, or from an element within an object, or even an object itself.

## Syntax Caveats of Controlling Loops
In addition to the basics of controlling loops, there are some caveats to be aware of. See the examples below for an illustration of what to look out for.

Variable initiatlization. Below you may see a strange syntax with an empty space before the `;` within the for loop's counter arguments. The empty space is actually ok, and the `i` var does not need to be initiatlized, but the `;` must be present. Above, you will see that this is because `i` has already been initiatlized with the zero value.

**Example**
```
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
```
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
```
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
```
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
```
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
```
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
**Block scope** refers to when a 'let' var has been declared both outside of a function and within a function at the same time. Essentially, when declared and initiatlized in both places, the function's intialized 'let' var will override the one that exists outside of it's brackets (scope). This does not apply to the 'var' keyword for declaring a variable, but only the 'let' keyword for declaring a variable.

**Example**
```
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
```
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
```
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
```
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
```
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
```
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
```
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
```
let getID = () => 123;
console.log( getID() ); // Returns '123'
```

In the first example, below, you'll notice that the Arrow Function's parameter is the _only one_ parameter declared, and thus, does not need to be wrapped in `()`. The second example demonstrates the need for the `()` when there is _more than one_ parameter.

**Example**
```
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
```
let trackCar = function(carID, city = 'NY') {
    console.log(`Tracking ${carID} in ${city}.`); // Not the backticks in this example.
}

console.log(trackCar(123)); // Returns 'Tracking 123 in NY.'
console.log(trackCar(123, 'Chicago')); // Returns 'Tracking 123 in Chicago.'
```

## Default Parameters
Parameters can be given default values as of ES 2015. In the example below, you can see that `city` has been set to the 'default value' of `NY`.

**Example**
```
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
```
function Car() { // Car() is a new object aka constructor function

}
let car = new Car();
```

In the below example, we create an object called `Vehicle()`. This object has two properties and a function. The function is called a 'method' in this case because it's attached to the object `Vehicle()`. Further, in this particular case, the method is attached _directly_ to the object `Vehicle()`. Learn more about why this is important in the next section on 'Prototypes'.

**Example**
```
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
```
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
```
String.prototype.hello = function() {
    return this.toString() + ', hello';
};
console.log('foo'.hello()); // Returns 'foo, hello'
```

## JavaScript Object Notation (JSON)
The purpose of JSON is to transmit JavaScript objects over the wire. In most cases, JSON can be used to work with an API such as a RESTful API on the web. To convert JavaScript objects to JSON, you can use `JSON.stringify()`. See a few examples below.

**Example**
```
// Convert a JS Object to JSON
let car = {
    id: 123,
    style: 'convertible'
};
console.log( JSON.stringify(car) ); // Returns '{"id": 123, "style": "convertible"}'
```

## TITLE
Text_here
**Example**
```
```

## TITLE
Text_here
**Example**
```
```

## TITLE
Text_here
**Example**
```
```

## TITLE
Text_here
**Example**
```
```