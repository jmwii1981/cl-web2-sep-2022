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



## Working With `WeakSet()` Objects
Text

**Example**
```javascript

```

 
## Creating And Using `Map()` Objects
Text

**Example**
```javascript

```


## Introducing `Map()` Objects
Text

**Example**
```javascript

```

 
## Adding And Removing Values In `Map()` Objects
Text

**Example**
```javascript

```

 
## Iterating Through A `Map()` Object
Text

**Example**
```javascript

```

 
## Difference Between `Map()` Objects And O...
Text

**Example**
```javascript

```

 
## Understanding The Difference Of `Map()` Objects
Text

**Example**
```javascript

```


## Exploring Typed Arrays
Text

**Example**
```javascript

```

 
## Defining Typed Arrays
Text

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