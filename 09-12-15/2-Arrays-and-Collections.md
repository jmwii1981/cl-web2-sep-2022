# JavaScript Arrays And Collections
From the video series [JavaScript Arrays and Collections](https://app.pluralsight.com/library/courses/javascript-arrays-collections/table-of-contents)


## Creating An Array from a List of Arguments
In the example below, we use the `Array` Object and the `Array.of` Method to build out a couple of arrays from a list of pre-defined arguments.

**Example**
```javascript
// Creates an array with 5 available nodes
let fiveSpots = Array(5);

// Creates an array with three arguments '2, 9, 3' acting as values for three nodes within this  new Array, 'threeSpots'
let threeSpots = Array.of(2, 9, 3);
```


## Methods for Working with Arrays
Below is an example of how you might use the `Array.of` method within an object to build a chart using [Chart.js](https://www.chartjs.org/)

**Example**
```javascript
// The selection of our chosen HTML canvas elements by id
let ctx = document.getElementById('monthlySales').getContext('2d');
let pieCtx = document.getElementById('deptSales').getContext('2d');

// Chart Data that we wish to use in our objects, created with 'Array.of'
let monthlySales = Array.of(12,9,3);
let monthlyLabels = Array.of('Oct','Nov','Dec');
let deptSales = Array.of(12,9,3);
let deptLabels = Array.of('Hiking','Running','Hunting');

// Bar Chart with our newly built-out arrays
var monthlySalesChart = new Chart(ctx, {
    type: 'bar',
    data: {
        labels: monthlyLabels,
        datasets: [{
            label: '# of Sales',
            data: monthlySales,
            backgroundColor: [
                'rgba(238, 184, 104, 1)',
                'rgba(75, 166, 223, 1)',
                'rgba(239, 118, 122, 1)',
            ],
            borderWidth: 0,
        }]
    },
    options: {
        scales: {
            yAxes: [{
                ticks: {
                    beginAtZero: true,
                }
            }]
        }
    }
});
```

 
## Using the Spread Operator
In the example below, we use the Spread Operator (`...`) to pass an array into a var for later use.

**Example**
```javascript
let monthlySales = Array.of(12,9,3);

// In addition to the example above, we decide to calculate our yearly total, so we are declaring and building out a function to return the sum of three values that the yearly total will deliver
function addYearlyTotal(num1, num2, num3){
    return num1 + num2 + num3;
}
// Below, we are using the 'yearlyTotal' var to store the value returned by 'addYearlyTotal' function and passing the 'monthlySales' Array in hopes to achieve our goal of getting the total yearly revenue from each year's sales
let yearlyTotal = addYearlyTotal(monthlySales); // Returns '12,9,3undefinedundefined'
```
As you can see in our example above, we did not receive the hopeful output, rather we received the undesired output, '12,9,3undefinedundefined'. This is because if we were to pass `monthlySales` using the correct syntax, it would need to be like so ..
`let yearlyTotal = addYearlyTotal(monthlySales[0],monthlySales[1],monthlySales[2]);`

This could take a while depending on the size of the Array. And, in some cases, we may not know how large the Array will be if it is built dynamically. So, an easier and better way to do this is by using the Spread Operator (`...`) like so ..
`let yearlyTotal = addYearlyTotal(...monthlySales);`

So, essentially, the spread operator will count the number of arguments to pass, and them pass them all for you (in the correct syntax) without you needing to write them out. We'll get into more about this later. If you'd like to read more about the Spread Operator from one of the previous series of videos, you can do so in the notes for [Syntax and Operators](../09-05-08/3-Syntax-and-Operators.md).


## Using `Array.find` to Find a Value, and `findIndex` to Find a Value's Position in an Array
See the example below.

**Example**
```javascript
let monthlySales = Array.of(500,9000,3000);

// Below, we use 'findOver1000' to find the first value greater than or equal to '1000'
function findOver1000() {
    let firstThousand = monthlySales.find(element => element >= 1000);
    return firstThousand; // Returns '9000'
}

// Below, we use 'findOver1000' to find the first value greater than or equal to '1000'
function findOver1000Position() {
    let firstThousandPosition = monthlySales.findIndex(element => element >= 1000);
    return firstThousandPosition; // Returns '1'
}
```


## Using Array Fill
Using the `fill` method, you can reset all values in an Array to zero or some other value.

**Example**
```javascript
let monthlySales = Array.of(500,9000,3000);

function resetNum() {
    monthlySales.fill(0);
}
```


## Methods for Iterating Through Arrays
Unlike in the previous example where we had to use the `addYearlyTotal` with three parameters to add up a sum of three numbers, now we want to be able to add an unpredictable set of numerical values together to get our `yearlyTotal`. See the example below on how we can use the `forEach` method to do this.

**Example**
```javascript
let monthlySales = Array.of(500,9000,3000);
let yearlyTotal = 0;

// Here, in 'addYearlyTotal' we want to pass as many numbers as we want to get our total. So, we only need to pass one parameter, 'nums'. Then, we'll use that parameter to do some math that adds up the total.
function addYearlyTotal(numToAdd) {
    yearlyTotal = numToAdd + yearlyTotal;
}

// Now we can use the 'forEach' method on the 'monthlySales' Array's values to get our 'yearlyTotal' sum. 'addYearlyTotal' achieves this by adding each value together as they get passed through the appropriate parameter 'numToAdd'. The 'forEach' method passes the values of the 'monthlySales' Array as arguments to 'addYearlyTotal' so that 'addYearlyTotal' can do this each time 'forEach' calls it and updates the 'yearlyTotal' variable.
monthlySales.forEach(addYearlyTotal);
```


## What Are Data Collections?
A **Data Collection** stores and structures large amounts of data types for easy access, and provides methods to access that data.

| Before ECMAScript | After ECMAScript |
| :---              | :---             |
| Arrays            | Sets             |
| Objects           | Maps             |
|                   | WeakSets         |
|                   | WeakMaps         |

There are eight different data types that we can work with when it comes to using Data Collections ..

| Primitives | Objects |
| :---       | :---    |
| Booleans   | _Objects_ |
| Null       |
| Undefined  |
| Number     |
| BigInt     |
| String     |
| Symbol     |

Seven of the data types above are Primitives and then the final one is an Object. In the case of Data Collections, Primitives really can't be changed. However, Objects are data types that can be referenced by an identifier.

 
## Introducing `Set()`, Its Properties And Methods
`Set()` enables us to store _unique_ values of any type, whether primitive values or object references. This means that _values that are duplicates are ignored_.

| Properties | Methods     |
| :---       | :---        |
| `size()`   | `add()`     |
|            | `clear()`   |
|            | `delete()`  |
|            | `entries()` |
|            | `forEach()` |
|            | `has()`     |
|            | `keys()`    |
|            | `values()`  |

So what do all of the properties and values of Sets (`Set()`) do?

**The** `Set().size` **Property**
 - `size()`: Returns the number of elements in a `Set()`. If the `Set()` is empty the size of the `Set()` will be returned as `0`.

**All of** `Set()`**'s Methods**
 - `add()`: Used to append an element with a specified value in a `Set()`. It modifies the existing `Set()` by appending the new element _but does not return a new_ `Set()`. The `add()` method _does not modify the `Set()` if the element with a specified value already exists_ in the `Set()`.
 - `clear()`: Used for the removal of _all elements_ from a `Set()` and makes it empty. No arguments are required to be sent as parameters to the `Set().clear()` method and it returns with the value of `undefined`.
 - `delete()`: Used to 'delete' an element with a specified value in a `Set()` and return a _boolean value_ depending upon the availability of the element. It will not modify the `Set()` if the element with specified value does not exist in the `Set()` and return a value of `false` instead.
 - `entries()`: Returns a new _Iterator Object_ that contains an array of `[value, value]` for each element in a `Set()`, in the order of their insertion. For `Set()` Objects specifically, _there is no key like in `Map()` Objects_. However, to keep the API similar to the `Map()` Object, each entry has the same value for its key and value, thus an Array with `[value, value]` is returned.
 
> **Note** – An _Iterator_ is an Object which defines a sequence and potentially a return value upon its termination.
 - `forEach()`: Executes a specified function once for each value in a specified `Set()` Object. It maintains an insertion order. Unlike `Map()`, the `Set()` Object doesn't use keys externally.
 - `has()`: Returns `true` or `false` indicating whether or not an element with a specified value exists in a `Set()` Object.
 - `values()`: Returns a new Iterator Object  containing the values for each element in a specified `Set()` in insertion order.
 
> **Note** – The `keys()` method _is an alias for the `values()` method_ (giving it similarity to `Map()` Objects). The `keys()` method therefore, behaves exactly the same as the `values()` method and returns values of `Set()` elements.
 - `keys()`: Returns a new Iterator Object containing the values for each element in a specified `Set()` in insertion order.

## Adding To and Deleting Values From A `Set()`
Below, see an example of how to use the `add()` and `delete()` methods for `Set()`.

**Example**
```javascript
// Values are entered from the form and stored in these variables
let newAmount = document.getElementById('newAmount');
let newMonth = document.getElementById('newMonth');
let deleteAmount = document.getElementById('deleteAmount');

// Here we create a new 'Set()' Object which can be used to store values that are passed to it. In this case, we're passing values from form fields in an HTML document assigned to vars 'newAmount' and 'newMonth'
const monthlySalesAmounts = new Set();
const specifiedMonths = new Set();

// Here we have a function that then adds values from the user's input (one at a time) into a 'Set()' object ... so, let's pretend the user adds two 'sets' of values and those entered values are ...
// 1 - newMonth = 'Oct' and newAmount = '1200'
// 2 - newMonth = 'Nov' and newAmount = '1500'
function addSale() {
    monthlySalesAmounts.add(newAmount.value); // Equivalent to [1200, 1500]
    specifiedMonths.add(newMonth.value); // Equivalent to [Oct, Nov]

    // Here, we return the number of sales the user has added.
    return `You have entered ${monthlySalesAmounts.size} sales.`; // Returns 'You have entered 2 sales.'
    // Here, we log out the values from the monthlySales 'Set()' that we created.
    console.log(monthlySalesAmounts); // Returns '[1200, 1500]'
}

// Here we create a function to allow the user to specify a value to delete
function deleteSaleAmount() {
    monthlySalesAmounts.delete(deleteAmount.value); // Deletes the amount that the user enters, if it's available
}

// Other handy things to note ...
    // You may "chain" 'add()' methods together
    someSet.add(5).add(6) // Adds [5, 6] to the set 'someSet'
    // You may also create a 'Set()' with values directly inside of it to start
    const someSet = new Set([7, 8, 9, 10]);
    // Note – You may also pass strings, and objects
        // Strings
        const someSetWithString = new Set(["I'm a string!", "So am I"]);
        // Objects
        const someSetWithObjects = new Set([{
                                            key1: "value1",
                                            key2: "value2",
                                            key3: "and so forth",
                                        }]);
```


## Iterating A `Set()`
Below, see an example of how to use a `for (let foo of bar)` (for of) loop to iterate through a `Set()`. We'll also use the `forEach()` and ... methods to iterate the `Set()` as well.

**Example**
```javascript
// Using a 'for of' loop to iterate ...
function addTotal() {
    for (let amount of monthlySalesAmounts) {
        return amount; // Loops through each of the values in our last example (above) and returns '1200' and '1500' as it steps through each value in the 'Set()' as specified by the for of loop
    }
}

// Using a 'forEach()' method to iterate ...
function deleteVal() {
    monthlySalesAmounts.forEach((value1, value2, monthlySalesAmounts) => {
        alert(value1);
    });
}
```


## Difference Between A `Set()` And `WeakSet()`
`Set()`s can store any value while `WeakSet()`s can only hold objects within its collection. `WeakSet()`s cannot store primitive values. In other words, integers, booleans, and strings are not allowed.

The nice thing about a `WeakSet()` is that unless it is used, it is not stored in memory. This means that an Object in a `WeakSet()` can be "garbage collected" if there is no other reference to it in the program.

Other differences are ...
 - `Set()`s can store any value. `WeakSet()`s are collections of Objects only.
 - `WeakSet()` does not have `size()` property.
 - `WeakSet()` does not have `clear()`, `keys()`, `values()`, `entries()`, `forEach()` methods.
 - `WeakSet()` is not iterable.


## Introducing `Map()` Objects ... What Are They?
Unlike `Array[]`s, `Map()`s are a collection of data that uses key-value pairs and _keeps the original insertion order of the keys_. As you iterate through an `Array[]`, for example, you aren't guaranteed that the iteration won't bounce around, whereas with a `Map()` you are. Any value (objects _and_ primitives) may be used as either a key or a value.

Thus, when using a `Map()`, you must pass it both a key and a value using the `set()` method.

**Example**
```javascript
// 'Set()'s vs 'Map()'s
someSet.add(value); // In sets, we only have to set a value
someMap.set(key, value); // Here we set a 'key value pair' using the 'set()' method.

// Examples of what can be passed to a 'Map()' as a key (this can also apply to values)
    // Strings as keys
    someMap.set('sale', 200);

    // Numbers as keys
    someMap.set(100, 'label');

    // Functions as keys
    someMap.set(myFunc(), 300);

    // Objects as keys
    someMap.set({sale: 100}, 200);

```

Some properties and methods that come with `Map()`s are ...

| Properties | Methods     |
| :---       | :---        |
| `size()`   | `clear()`   |
|            | `delete()`  |
|            | `entries()` |
|            | `forEach()` |
|            | `get()`     |
|            | `set()`     |
|            | `has()`     |
|            | `values()`  |
|            | `keys()`    |

**The** `Map().size` **Property**
 - `size()`: Returns the number of elements in a `Map()`. If the `Map()` is empty the size of the `Map()` will be returned as `0`.

**All of** `Map()`**'s Methods**
 - `clear()`: Used for the removal of _all elements_ from a `Map()` and makes it empty. No arguments are required to be sent as parameters to the `Map().clear()` method and it returns with the value of `undefined`.
 - `delete()`: Used to 'delete' an element with a specified value in a `Map()` and return a _boolean value_ depending upon the availability of the element. It will not modify the `Map()` if the element with specified value does not exist in the `Map()` and return a value of `false` instead.
 - `entries()`: Returns a new _Iterator Object_ that contains an array of `[key, value]` (key-value pairs) for each element in a `Map()`, in the order of their insertion. For `Set()` Objects specifically, _there is no key like in `Map()` Objects_. However, to keep the API similar to the `Map()` Object, each entry has the same value for its key and value, thus an Array with `[value, value]` is returned.
 - `forEach()`: Executes a specified function once for each key-value pair in a specified `Map()` Object. It maintains an insertion order. Unlike `Map()`, the `Set()` Object doesn't use keys externally.
 - `get()`: Returns a specified element from a `Map()` object. If the value that is associated to the provided key is an Object, then you will get a reference to that Object and any change made to that Object will effectively modify it inside the `Map()` object.
 - `set()`: Adds or updates an entry in a `Map()` Object with a specified key and a value.
 - `has()`: Returns `true` or `false` indicating whether or not an element with a specified value exists in a `Map()` Object.
 - `values()`: Returns a new Iterator Object containing the _values_ for each element in a specified `Map()` in insertion order.
  - `keys()`: Returns a new Iterator Object containing the _keys_ for each element in a specified `Map()` in insertion order.


## Creating `Map()` Objects, and Adding And Removing Values In Them
Text

**Example**
```javascript
const monthlySales = new Map();

// Adds adds a user inputted value relative to a defined key "newSale"
function addSale() {
    monthlySales.set('newSale', newAmount.value);
    console.log(monthlySales); // Returns a 'Map()' Object with a key of "newSale" and a value of the users' 'newAmount.value' entry, we'll pretend it's "1200" as a string.
}

// Finds a key and returns the key's value
function findSale() {
    console.log(monthlySales.get('newSale')); // Returns the value of the key "newSale", which is "1200".
    
}

// Deleting a value by deleting it's key
function addSale() {
    monthlySales.delete('newSale');
    console.log(monthlySales); // Returns  'No Entries' because we have deleted the value and key together (as they're tied together).
}

// Ask the Map() Object if it has a value for a given key
function doesSaleHave() {
    console.log(monthlySales.has('newSale')); // Returns a boolean value of 'true' or 'false' depending on whether the specified key exists.
}
```

## Iterating Through `Map()`s
Iterating through a `Map()` is similar to the way we would iterate through a `Set()` in that we can use the `forEach` method and the `for (let foo of bar)` (for of) loop. 

**Note** – In the example below, we use the `Array.from` method. The `Array.from()` static method creates a new, shallow-copied Array instance from an iterable or array-like object. To read more about `Array.from` visit the [MDN Article, "Array.from()"](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from)

**Example**
```javascript
var yearlyTotal = 0;

let newMonth = {
    value: 'Oct',
}

let newAmount = {
    value: '1200',
}

const monthlySales = new Map();

function addSale() {
    monthlySales.set(newMonth.value, newAmount.value);
    
    console.log(Array.from(monthlySales.keys()));
}
addSale();
```


## Understanding The Differences Between `Map()`s and Objects
One of the benefits of using a `Map()` over an Object or `Array[]`, is that `Map()`s are faster to iterate through. Another benefit is the kind of data types that a `Map()` can hold vs. an Object. In Objects, _keys must be simple data types_. In `Map()`s, _keys can be any data type_ you need them to be.

| Object   | Map      |
| :---     | :---     |
| Integers | Object   |
| Strings  | Array    |
| Symbols  | Function |

As we've discussed before, `Map()`s guarantee a specific order based on the order of insertion while Objects do not.

A `Map()` is inherited from an Object which means that a `Map()` can get the different methods and properties of an Object. However, an Object cannot inherit different methods and properties of a `Map()`.

A functional benefit of a `Map()` over an Object is the way we create `Map()`s. `Map()`s are actually much simpler to create because there's only one way to create them. See the example below.

**Example**
```javascript
// Creating an Object
var obj = {};
var obj = new Object();
var obj = Object.create(null);

// Creating a 'Map()'
var map = new Map();
```

The same simplicity applies to _getting_, _checking_, _adding_, and getting the _size_ of Objects vs. `Map()`s. `Map()`s are _just easier to use_. See the examples below.

**Example**
```javascript
// Getting
    // Getting with an Object
    obj.id;
    obj['id'];

    // Getting with a 'Map()'
    map.get(1);

// Checking
    // Checking with an Object
    Object - var isExist = obj.id === undefined;
    isExist = 'id' in obj;

    // Checking with a 'Map()'
    map.has(1);

// Adding
    // Adding with an Object
    obj['gender] = 'female';
    obj.gender = male;

    // Adding with a 'Map()'
    map.set('gender', 'female');

// Size
    // Sizing with an Object
    console.log(Object.keys(obj).length);

    // Sizing with a 'Map()'
    console.log(map.size);
```


## Understanding The Differences Between `Map()`s and `WeakMap()`s
Many of the differences between `Map()`s and `WeakMap()`s are very similar to the differences between `Set()`s and `WeakSet()`s.

A quick overview of the differences between `Map()`s and `WeakMap()`s ..
 - _Keys_ must be _Objects_.
 - Objects are held "weakly".
 - Not iterable.
 - Garbage collected (i.e. if not used, then not stored in memory).
 - Not enumerable (or cannot be fully counted).
 - `WeakMap()`s _only_ have the methods `delete()`, `get()`, `set()`, or `has()`.
 - `WeakMap()`s _do not_ have the methods `keys()`, `values()`, `clear()`, `entries()`, or `forEach()`.


## Defining Typed Arrays
Typed Arrays are a specific kind of Array that handle direct memory allocation. This means you may actually store items in memory and work with them that way in order to help your software application run faster. In essence, Typed Arrays are Array-like Objects that provide a mechanism for accessing raw binary data which allows you to work with it quicker and easier. Typed Arrays are known for strictly controlling the data it stores by disallowing just any type of data stored. A wide variety of APIs support the usage of Typed Arrays so that you may take advantage of their faster performance.

Some of the Native APIs that Typed Arrays may interact with are .. 
 - WebGL
 - Canvas
 - Web Audio
 - XMLHttpRequests
 - Fetch
 - Web Sockets
 - Web Workers
 - Media Source
 - File

To get started with Typed Arrays, you will need to know how to use an Array Buffer. In Array Buffers you define how many bites you actually want to work with inside of your Typed Array. However, code within JS documents cannot communicate directly with Array Buffers. So, you are required to create what is called a View. Each View will contain a certain number and type of structures and bites. Some View types and a short overview of general details about them are as follows..
 - UInt8Array (1 bite each); 16 structures (0-15) to work with; allows use of certain low-value numbers.
 - UInt16Array (2 bites each); 8 structures (0-7) to work with; allows use of certain lower-value numbers, but higher value than UInt8Arrays.
 - UInt32Array (4 bites each); 4 structures to work with; allows work with higher value numbers.
 - UInt64Array (8 bites each); 2 structures to work with; allows work with much higher value numbers.

Below is a table of the Array Types in more detail ..
| Type             | Value Range               | Size in Bytes | Description                                                              |
| :---             | :---                      | :---          | :---                                                                     |
|Int8Array         | -128 to 127               | 1             | 8-bit two's complement signed integer.                                   |
|UInt8Array        | 0 to 255                  | 1             | 8-bit unsigned integer.                                                  |
|UInt8ClampedArray | 0 to 255                  | 1             | 8-bit unsigned integer (clamped).                                        |
|Int16Array        | -32768 to 32767           | 2             | 16-bit two's complement signed integer.                                  |
|UInt16Array       | 0 to 65535                | 2             | 16-bit unsigned integer.                                                 |
|Int32Array        | -2147483648 to 2147483647 | 4             | 32-bit two's complement signed integer.                                  |
|UInt32Array       | 0 to 4294967295           | 4             | 32-bit unsigned integer.                                                 |
|Float32Array      | 1.2x10-38 to 3.4x1038     | 4             | 32-bit IEEE floating point number (7 significant digits e.g. 1.1234567). |

**Example**
```javascript

```

 
## Typed Arrays vs. Standard Arrays
Text

**Example**
```javascript

```

 
## Creating Typed Array Buffers
Text

**Example**
```javascript

```

 
## Accessing Typed Arrays With View
Text

**Example**
```javascript

```