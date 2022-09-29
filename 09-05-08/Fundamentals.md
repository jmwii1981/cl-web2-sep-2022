# JavaScript Fundamentals
From the video [Title](https://a-url.com)


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