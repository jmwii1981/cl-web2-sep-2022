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

 
## Introducing Sets
Sets enable us to store _unique_ values of any type, whether primitive values or object references. This means that values that are duplicates are ignored.

| Properties | Methods  |
| :---       | :---     |
| Size       | Add      |
|            | Clear    |
|            | Delete   |
|            | Entries  |
|            | forEach  |
|            | Has      |
|            | Keys     |
|            | Values   |

## TITLE
Text

**Example**
```javascript

```


## TITLE
Text

**Example**
```javascript

```

 
## TITLE
Text

**Example**
```javascript

```


## TITLE
Text

**Example**
```javascript

```


## TITLE
Text

**Example**
```javascript

```

 