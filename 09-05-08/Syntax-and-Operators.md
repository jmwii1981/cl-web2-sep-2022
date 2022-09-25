# Syntax and Operators
From the video [JS 7 Syntax and Operators](https://external.ink?to=/app.pluralsight.com/course-player?clipId=3b2cbc2a-d4aa-401a-8f51-0cbc78d95799)

**Note to self** – Review all of the material in this section in the YDKJS series by Kyle Simpson. Keep in mind that the series focuses on ES 6 in some regards and note the differences.

## Using for/in Loops
> TBD

## Using for/of Loops
> TBD

## Break / Continue Statements
> TBD

## Labeled Statements ('A No-No')
> TBD

## Switch Statements
> TBD

## Using Math and Comparison Operators
Typical math operators are ...
 - `+`: Addition
 - `-`: Subtraction
 - `*`: Multiplication
 - `/`: Division
 - `**`: To the power of ...
 - `%`: Modulus

## Operators
Operands are what's being "operated" on by the operator. Every operator will have an operand on both its left and right sides (e.g. `operand operator operand`).

 **Example**
 ```
let operand = 10;
let result;

result = operand + operand; // the expression evaluates to 20 and result becomes === 20.
```

## Plus Sign Caveats (Addition/Concatination)
 - `"strings" + "strings"` is concatination and combines the two strings together to become `stringsstrings`
 - `10 + 10` or _integer_ `+` _integer_ is addition and is evaluated

## Assignment Operators
 The below shorthand can move things a little faster
 - `price = 5 // var price is set to equal 5`
 - `price += 5 // price = price + 5 (or price = 5 + 5); evaluates to 10`
 - `price *= 5 // price = price * 5 (or price = 5 * 5); evaluates to 25`
 - `price /= 5 // price = price / 5 (or price = 5 / 5); evaluates to 1`
 - `price **= 5 // price = price ** 5 (or price = 5^5 [5 to the power of 5]); evaluates to 3125`
 - `price %= 5 // price = price / 5 to get the remainder of 1 (this can be used to evaluate whether an integer is odd or even)`

## Comparison Operators
The following comparison operators are listed in order of precedence
 - `< // Less than`
 - `<= // Less than or equal to`
 - `> // Greater than`
 - `>= // Greater than or equal to`
 - `== // Equal to (means only the value is considered during evaluation despite it being a string or integer)`
 - `!= // Not equal to`
 - `=== // Strict equals (means value and date type are considered during evaluation)`
 - `!== // Strict not equal`

## 'use strict'
Always make sure to use `'use strict'`, as it's considered a best practice.

Rules that `'use strict'` imposes and things to note ...
 - **Note** `'use strict'` is ignored by older browsers
 - You will be forced to declare variables first, before their use, and they will be scoped locally where declared
 - You won't be able to use "reserved" key words in JS as variable names (e.g. `eval`, `arguments`)
 - You won't be able to delete variables (e.g. `delete result`)
 - You won't be able to delete functions (e.g. `delete thisIsAFunction`)
 - **If you are not using** '`use strict'` then **you are able to do all of the above**
 - **If you are not using** `'use strict'`then **mis-typed variable names will be globally scoped** (declared globally)

## Truthy, Falsy
Here's how these booleans work.
 - Any var with a value of a `"non-empty string"`, `10` (integer greater or less than a `0`, but never `0`), or the `true` boolean are considered **`true`**
 - Any var with a value of `undefined`, `null`, `NaN`,`false`, or one that contains an empty string `""` evaluates to **`false`**

**Example**
 ```
 function myFunction() {
    let x = "";
    
    if (x) {
        document.write("TRUE");
    } else {
        document.write("FALSE");
    }
 }
 myFunction(); // evaluates to false
 ```
 
 - rather than use an if statement, you can use the Boolean() function to evaluate a var value for truthiness or falsiness

 **Example**
 ```
 function myFunction() {
    let color = null;
    document.write(Boolean(color));
 }
 myFunction(); // evaluates to false
 ```

## And (`&&`), Or (`||`) Operators
- in the case of the `&&` operator
    - **both sides of the operator** must be `true` for the full expression to evaluate as `true`
    - in the event that an expression on either side of the `&&` are `false`, the full expression evaluates to `false`
- in the case of the `||` operator
    - **either side of the operator** must be `true` for the full expression to evaluate as `true`
    - in the event that an expression on either side of the `||` are false, then as long as one expression is `true`, then the full expression evaluates to `true`

**Example**
```
function myFunction() {
    let x = 200;
    if (x > 10 && x < 1600) { // evaluates to true because both sides are true
        document.write("true");
    } else {
        document.write("false");
    }
    
}
myFunction(); // outputs 'true'

function myFunction() {
    let x = 200;
    if (x > 300 || x > 1600) { // evaluates to false because both sides aren't true
        document.write("true");
    } else {
        document.write("false");
    }
    
}
myFunction(); // outputs false

function myFunction() {
    let x = 200;
    if (x > 300 || x < 1600) { // evaluates to true because one side of the operator is true, eventhough the other if false
        document.write("true");
    } else {
        document.write("false");
    }
    
}
myFunction(); // outputs true
```

## Not (`!`) Operator
- `!` must go in front of the full expression being evaluated

**Example**

```
function myFunction() {
    let x = 9;
    if (!x > 10) { // evaluates to true
        document.write("true");
    } else {
        document.write("false");
    }
}
myFunction(); // outputs true
```

## Short Circuiting
- in the case of `&&`, if the first part of the expression (or left side of the full expression) evaluates to false, then the second part of the expression (or right side of the full expression) are *not* evaluated.
- in the case of `||`, if the first part of the expression (or left side of the full expression) evaluates to true, then the second part of the expression (or right side of the full expression) are *not* evaluated.

## Order of Precedence
The order of operation precedence is as follows ... top of the stack is highest precedence, and lowest of the stack is lowest precedence ...
 - `()`: Grouping
 - `!`: Not
 - `*`: Multiplication
 - `/`: Division
 - `%`: Modulus
 - `+`: Addition
 - `-`: Subtraction
 - `<`: Less than
 - `<=`: Less than or equal to
 - `>`: Greater than
 - >=`: Greater than or equal to
 - `==`: Equal to
 - !=`: Not equal to
 - `===`: Strict equal to
 - `!==`: Strict not equal to
 - `&&`: And
 - `||`: Or
 - `=`  : Assignment

## Try, Catch, Finally, and the Throw Statement
A `try`, `catch`, and `finally` code block should always be wrapped around "dangerous" code, or code that might throw an error.

Here's what `try`, `catch`, and `finally` do ...
 - The `try` statement defines a code block to run (to try)
 - The `catch` statement defines a code block to handle any error
 - The `finally` statement defines a code block to run regardless of the result

 **Example**
 ```
 function myFunction() {
    let result;

    try {
        document.write(`Starting the 'try, catch, finally' code block.`);
        result = x / 10; // an error occurs here
        document.write(`This line won't run.`); // any line after an error in the 'try' code block will never run
    }
    catch(error) { // 'error' here is the JS predefined or built-in keyword 'error' that will tell you what the error is
        document.write(`<br>The error message given is: <em>` + error.message + `</em>`); // this line will run if there was an error in the try code block
    }
    finally { // always runs no matter what
        document.write(`<br>Done executing the 'try, catch, finally' code block.`); // this line of code will always run whether there is an error or not
    }
}
myFunction();
// Output from myFunction() is as follows ...
// Starting the 'try, catch, finally' code block.
// The error message given is: x is not defined.
// Done executing the 'try, catch, finally' code block.
}
```

Here's what the `throw` statement does ...
 - The `throw` statement defines a custom error message
 - To create an effective `throw` statement, you must create an object with at least two properties, the suggested properties are
     - `name`
     - `message`

**Example**
```
function attemptDivision() {
    let result;

    try {
        result = x / 10;
    } catch (error) {
        throw {
            "message" : "In the attemptDivsion() method, the following error occurred: " + error.message,
            "name" : "CustomError",
        }
    }    
}
function throwError() {
    try {
        attemptDivision();
    } catch (error) {
        console.log(error.message + " - Error Type: " + error.name);
    }
}
throwError(); // the console shows the followiing ... "In the attemptDivsion() method, the following error occurred: x is not defined - Error Type: CustomError"
```

Custom errors can also handle errors based on the type of error using a conditional statement.

**Example**
```
function handleError(error) {
    switch(error.name) {
        case 'ReferenceError';
            console.log("Reference error: " + error.message);
            break;
        case 'RangeError';
            console.log("Range error: " + error.message);
            break;
        case 'TypeError';
            console.log("Type error: " + error.message);
            break;
        case 'URIError';
            console.log("URI error: " + error.message);
            break;
        case 'SyntaxError';
            console.log("Syntax error: " + error.message);
            break;
    }
}
```

**Note:** Types of Errors to familiarize yourself with are ...
 - `referenceError`
 - `rangeError`
 - `typeError`
 - `uriError`
 - `syntaxError`
 - `evalError`

These are built-in Error objects to check for.

## Primitive Data Types
Primitive data types are as follows ...
 - **boolean**: either `true`, or `false`
 - **null**: is described as having no value and usually represented as `null`
 - **undefined**: is described as a variable having been declared with no value, or an empty variable. Usually represented as `undefined`
 - **number**: usually represented by types of numbers such as integers, decimals, floats, etc.
 - **string**: an array (or series) of characters

## Object Data Types
 - `new Array()`: typically a collection of values
 - `new Error()`: contains properties of name and message
 - `new Function()`: contains a block of code to be executed when called by the function's name
 - `new Object()`: a wrapper around any data type
 - `new RegExp()`: a regular expression
 - `new Boolean()`: an object that contains either true or false
 - `new Number()`: an object that contains a numeric value
 - `new String()`: an object that contains a series of characters

Objects take up more memory space than primitive data types. Use primitive where possible in an effort to eliminate overuse of objects.

## The `typeof` Operator
The `typeof` operator returns an evaluation of an object's type when you pass that object to it.

**Example**
```
typeof "Hello"; // evaluates to 'string'
```

## The Object Data Type's Constructor Property
 - All object data types inherit from objects. Conversely, primitive data types do not inherit
 - All objects have a constructor property
 - The constructor property returns a reference to the object it belongs to ... this allows us to learn a few things about the object itself

**Example**
```
// The following is pseudo code
data_type.constructor.toString(); // will output a string value that tells us what data type 'data_type' is

data_type.primitive.constructor.toString(); // will output to a string value that tell you what it is after constructor applies (assigns) a constructor property to the primitive. Meanwhile, objects _already have_ constructors
```

## The `instanceof` Operator
The `instaceof` Operator ...
 - Tests to see whether an instance of an object inherits from another object (not a primitive)
 - Tests for a specific type of object, or an object itself

**Example**
```
let prod = new Product(680, "Road Frame");
console.log(prod instanceof Product.toString()); // above returns output of 'true'
```

## What `this` _Really_ Is
`this` ...
 - Refers to an object; that object in which the current code is running
 - Sometimes, the object can be changed

In the following example, `this` is directly inside of the _window global object_ so that is what it is referencing.

**Example**
```
<script>
    console.log(this.toString()); // prints [Object window]
</script>
```

In the following example, `this` is the _object literal_ `person`. `this` will have different values based on the context of which your code is excuting. 

**Example**
```
person {
    firstName: "John",
    lastName: "Smith",
    fullName: function() {
        return this.firstName + ` ` + this.lastName;
    },
}
```

In a method/function, `this` refers to the object that _owns_ the method ... or holds the method inside of it. 

> **check this – doesn't seem accurate the way it's written**
> In a function declared outside of your declared _owner_ object, `this` refers to the _window global object_.

In an event (e.g. a click event), `this` refers to the HTML element that receives the event (i.e. HTML elements are considered JS objects).

In a call() or apply() function, `this` refers to the object passed in `call(object);` or `apply(object)`.

**Example**
```
function callAndApply() {
    let product = {
        "productID": 680,
        "name": "Road Frame",
        "standardCost": 1059.31,
        "listPrice": 1431.50,
        grossProfit: function() {
            return(this.listPrice - this.standardCost).toLocaleString("en-US", {"style": "currency", "currency": "USD"});
        }
    };

    let prod2 = {
        "standardCost": 500,
        "listPrice": 850
    }

    // Call using reference to 'product' properties ... here 'this' refers to the product object
    console.log(product.grossProfit.call(product));
    
    // Call using reference to 'prod2' properties ... here 'this' refers to the prod2 object
    console.log(product.grossProfit.call(prod2));
    console.log("");
    console.log(product.grossProfit.apply(product)); // $372.19
    console.log(product.grossProfit.apply(prod2)); // $350.00
}
```

You can think of `this` as being affected by ...
 - Global scope
 - Function scope
 - `use strict`

If you use `this` within global scope whil also using `use strict`, then `this` is `undefined`.

Considering `this` and object literals, or instance objects ...
 - _Object literals_ are _"flat"_ and do not provide private scope, or a scope of their own, to themselves.
 - An _instance object_ (or an object that is capable of having an instance of itself) has a constructor and can have new a instance of it exist with it being the _main blueprint instance_.
 - `this` is an _object literal_.
 - `this` inside of an object literal always refers to the _properties_ of that object literal.

When `this` is used inside of call() or apply() functions ...

**Example**
```
// Continued from example above ...
function constructorFunction() {
    let prod1 = new Product(680, "Road Frame", 1059.31, 1431.50);
    let prod2 = new Product (707, "Helmet", 13.08, 34.99);
    console.log(prod1.grossProfit); // $372.19
    console.log(prod2.grossProfit); // $21.91
}
```

## The spread `...` Operator
The spread syntax `...` is a new addition to the set of operators in JS ES6.

It takes in an _iterable_ (such as an _array_) and _expands it into individual elements_. Spread is commonly used to make _shallow copies of JS objects_. Using this operator _makes the code concise_ and _enhances its readability_. 

In other words, spread `...` allows an _iterable_, such as an _array_ or _string_, to be _expanded_ in places where ... 

 - _zero or more arguments_ for _function calls_ are expected
 - **or** _elements_ for _array literals_ are expected
 
In an _object literal_, the spread syntax
 - _enumerates the properties of an object_ 
 - **and** _adds the key-value pairs to the object being created_.

So, to review, the spread `...` operator ...
 - Syntax uses the ellipsis symbol `...`
 - Is used to expand any _iterable_ array such as a string or other collection of indexed data into a new array object
 - Is also used to pass multiple arguments to a method
 - Is always on the right side of an equal sign

**Note** IE and Edge (at time of writing) do not support the `spread` operator


## String to Array
**Example**
```
// String to array
function stringToArray() {
    let productNumber = "FR-R92B-58";
    let values = [...productNumber];
    console.log(values);
}
stringToArray();
// Returns (10) ['F', 'R', '-', 'R', '9', '2', 'B', '-', '5', '8']
```

## Copy An Array of Primitives
**Example**
```
// Copy array (normally you would use the 'slice' method to copy an array, but for purposes of demonstration, we'll use the 'spread' operator for the moment ...)
function copyArray() {
    let arr1 = [1, 2, 3];
    let arr2 = [...arr1];

    // Make changes to duplicated array
    arr2.push(4);
    arr2[0] = 99;

    console.log(arr1); // Returns (3)[1, 2, 3]
    console.log(arr2); // Returns (4)[99, 2, 3, 4]
}
copyArray();
```

## Copy An Array of Objects
**Example**
```
let _products = [{
        productID: 680,
        name: "Road Frame",
        productNumber: "FR-R92B-58",
        color: "Black",
        standardCost: 1059.31,
        listPrice: 1431.50,
    },
    {
        productID: 707,
        name: "Helmet",
        productNumber: "HL-U509-R",
        color: "Red",
        standardCost: 13.08,
        listPrice: 34.99,
    },
    {
        productID: 708,
        name: "Socks",
        productNumber: "SO-B909-M",
        color: "White",
        standardCost: 3.3963,
        listPrice: 9.50,
    }];

function objectArrays() {
    // **Careful with object arrays** – The array is copied, but the underlying objects are not copied moreso than they are just pointed to (where they are in memory) ... this means that you would be changing the actual original values of the objects being pointed to themselves if you were to make changes
    let diff = [.._products];

    // Modify a property of the new array; but ALSO modifies the property of the original ...
    diff[0].productID = 999;

    console.log(_products[0].productID); // Returns 999
    console.log(diff[0].productID); // Returns 999

    // This happens because the objects inside of the original array (above) are not copied by value, they're copied by reference
}
objectArrays();
```

## Concatenate Two Arrays Together
**Example**
```
let _products = [{
        productID: 680,
        name: "Road Frame",
        productNumber: "FR-R92B-58",
        color: "Black",
        standardCost: 1059.31,
        listPrice: 1431.50,
    },
    {
        productID: 707,
        name: "Helmet",
        productNumber: "HL-U509-R",
        color: "Red",
        standardCost: 13.08,
        listPrice: 34.99,
    },
    {
        productID: 708,
        name: "Socks",
        productNumber: "SO-B909-M",
        color: "White",
        standardCost: 3.3963,
        listPrice: 9.50,
    }];

let _newProducts = [{
        productID: 712,
        name: "Logo Cap",
        productNumber: "CA-1098",
        color: "Multi",
        standardCost: 6.9223,
        listPrice: 8.99,
    },
    {
        productID: 821,
        name: "Front Wheel",
        productNumber: "FW-T905",
        color: "Black",
        standardCost: 96.7964,
        listPrice: 218.01,
    }];

// Concatenation
function concatenateArray() {
    // The original way of doing this in JS ...
    let allProducts = _products.concat(_newProducts);
    console.log(allProducts.length); // Returns 5; because there are now five objects

    // The new way to do this with the 'spread' operator is to ...
    let spProducts = [..._products, ..._newProducts];
    console.log(spProducts.length); // Returns 5; because there are now five objects
}
concatenateArray();
```

## A Note About Parameters and Arguments within Functions
Parameter variables are used to import arguments into functions. 

Note the difference between _parameters_ and _arguments_: Function parameters are _the names listed in the function's definition_. Function arguments are _the real values passed to the function_.

 - Function parameters are the named variables listed in the function's declaration.
 - Function parameters are initialized to the values of the arguments supplied.
 - Function arguments are the real values passed to the function.

**Example**
```
// Parameters are the names listed in the function's definition, such as the one below
function example(parameter) {
  console.log(parameter); // Output = foo
}

// Arguments are the real values passed to the function (above), which is then able to output 'foo'
const argument = "foo";

example(argument); // Returns 'foo'
```

## Using `Spread` To Pass Parameters To A Constructor
**Example**
```
// Use with 'new' constructor instance of an object
function spreadInConstructors() {

    // Calling 'new Date()' returns a constructor instance of the Date() object ... And, we're using the following parameters: year, monthIndex, day. (e.g. new Date(year, monthIndex, day)).

        // Here, we let dt = our new Date() constructor with some pre-defined Date() parameter arguments (real values) (i.e. 2019, 11, 15)
        
        let dt = new Date(2019, 11, 15);
        console.log(dt); // Returns Fri Nov 15 2019 00:00:00 GMT-0600 (Central Standard Time)

        // Here we create an array of new parameter arguments (real values) to build a new date with (i.e. 2019, 12, 25)
    
        let dateFields = [2019, 12, 25]; // Returns an array like so ... (3)[2019, 12, 25]
        
        // Here we're passing the previously made array of parameter arguments (real values) into the 'new' Date object
    
        dt = new Date(...dateFields); 
        console.log(dt); // Returns Sun Dec 15 2019 00:00:00 GMT-0600 (Central Standard Time)
}
spreadInConstructors();
```

## Pass Parameters To A Function
One of the benefits of using the spread operator is that it will create a new reference to its primitive values, copying them. As you can see, the spread operator is useful for creating new instances of arrays that do not behave unexpectedly due to old references.

**Example**
```
// 'spreadForFunctionArgs()' is declared here and invokes 'multipleParams()' in two ways: the traditional approach, and the spread approach ...

    function spreadForFunctionArgs() {

        // 'multipleParams()' first invocation; The traditional way of passing multiple function/method parameters.

            // The 'multipleParams()' function/method is invoked here, and argument values '1, 2, 3' are declared _and_ passed as individual arguments to the 'multipleParams()' function/method.
            
            multipleParams(1, 2, 3);

        // 'multipleParams()' second invocation; Using 'spread' (...) to pass multiple parameter arguments to a function/method.

            // An 'args' array is declared with the elements of 1, 2, 3, returning (3)[1, 2, 3] via the console when tested. Each of these is a parameter argument to be passed.
            
            let args = [1, 2, 3]; 

            // Then, the 'multipleParams()' function/method is invoked here, and the 'args' array's elements (declared from above) are copied via the spread (...) operator and passed to the 'multipleParams()' function/method for reception as invidual parameter arguments ... '1, 2, 3 'within the given array collection. 
            
            // This approach functions much like the traditional approach in that it outputs the same parameter arguments (or real values), only it allows us to be more verbose via spread's functionality, making the code cleaner and more readable.
            
            multipleParams(...args); 
    }

// 'multipleParams()' is declared here with named variables thing1, thing2, and thing 3. This allows both the traditional and spread approach elements to be passed to 'multipleParams()'.

    function multipleParams(param1, param2, param3) {

        // This evaluates to ...

            // 'param1's argument = parameter 1 becomes real value '1'
            
            console.log(param1); // Returns '1',

            // 'param2's argument = parameter 2 becomes real value '2'
            
            console.log(param2); // Returns '2'

            // 'param3's argument = parameter 3 becomes real value '3'
            
            console.log(param3); // Returns '3'
    }

spreadForFunctionArgs();
```

## Shallow Copy on Object Literals
**Example**
```
function objectliterals() {
    // A literal object called product assigned a few different properties
    let product = {
        productID: 680,
        name: "Road Frame",
        standardCost: 1059.31,
        listPrice: 1431.50
    };

    // The following peforms a 'shallow' copy of the object literal's properties one-by-one into a new object literal 
    'prod2' (This functionality, in a way, is similar to Object.assign())
    let prod2 = { ...product }

    // Here we change the value of the newly copied object literal's property 'productID'
    prod2.productID = 999;

    // Here we display the objects as they are now formed, after changes and declarations, in the console
    console.log(product);
    // Returns product = { productID: 680, name: "Road Frame", standardCost: 1059.31, listPrice: 1431.50 }

    console.log(prod2);
    // Returns prod2 = { productID: 999, name: "Road Frame", standardCost: 1059.31, listPrice: 1431.50 } 

    // Display the changed value on its own ... (for "funzzies??")
    console.log(product.productID); // Returns 680
    console.log(prod2.productID); // Returns 999
}
```

# THE END