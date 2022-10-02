# JavaScript Fundamentals
From the video [Title](https://a-url.com)


## Functions
**Note** When talking about functions, it's important to note the difference between parameters, and arguments. A parameter is the variable in the declaration of the function. For instance, consider `foo function(parameter1, parameter2){ bar; }`. Meanwhile, an argument is the actual value of this variable that gets passed to the function. Usually an argument will get passed to the function from another source such as another variable, or from an element within an object, or even an object itself.

**Example**
```
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
**Example**
```
```

## Default Parameters
**Example**
```
```

## TITLE
**Example**
```
```

## TITLE
**Example**
```
```

## TITLE
**Example**
```
```

## TITLE
**Example**
```
```
