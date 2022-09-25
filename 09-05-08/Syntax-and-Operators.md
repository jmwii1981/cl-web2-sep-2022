> FORMATTING SHORT-KEY
> # The largest heading
> ## The second largest heading
> ###### The smallest heading

> Formatting code
> ```
> this
> is
> some code
> ```

# Syntax and Operators

**Note to self** – Review all of the material in this section in the YDKJS series by Kyle Simpson. Keep in mind that the series focuses on ES 6 in some regards and note the differences.

## Using for/in Loops

## Using for/of Loops

## Break / Continue Statements

## Labeled Statements ('A No-No')

## Switch Statements

## Using Math and Comparison Operators
 - typical math operators are ...
    - `+`
    - `-`
    - `*`
    - `/`
    - `**`
    - `%`

### Operators
 - operand operator operand
 - operands are what's being "operated" on by the operator
 - every operator will have an operand on both its left and right sides
 
 **Example**
 ```
let operand = 10;
let result;

result = operand + operand; // the expression evaluates to 20 and result becomes === 20.
```

### Plus Caveats (Addition/Concatination)
 - `"strings" + "strings"` is concatination and combines the two strings together to become `stringsstrings`
 - `10 + 10` or _integer_ `+` _integer_ is addition and is evaluated

### Assignment Operators
 - the below shorthand can move things a little faster
    - `price = 5 // var price is set to equal 5`
    - `price += 5 // price = price + 5 (or price = 5 + 5); evaluates to 10`
    - `price *= 5 // price = price * 5 (or price = 5 * 5); evaluates to 25`
    - `price /= 5 // price = price / 5 (or price = 5 / 5); evaluates to 1`
    - `price **= 5 // price = price ** 5 (or price = 5^5 [5 to the power of 5]); evaluates to 3125`
    - `price %= 5 // price = price / 5 to get the remainder of 1 (this can be used to evaluate whether an integer is odd or even)`

### Comparison Operators (In order of precedence)
 - `< // Less than`
 - `<= // Less than or equal to`
 - `> // Greater than`
 - `>= // Greater than or equal to`
 - `== // Equal to (means only the value is considered during evaluation despite it being a string or integer)`
 - `!= // Not equal to`
 - `=== // Strict equals (means value and date type are considered during evaluation)`
 - `!== // Strict not equal`

### 'use strict'
 - always make sure to use `'use strict'`, as it's considered a best practice

 Rules that `'use strict'` imposes and things to note ...
 - **Note** `'use strict'` is ignored by older browsers
 - You will be forced to declare variables first, before their use, and they will be scoped locally where declared
 - You won't be able to use "reserved" key words in JS as variable names (e.g. `eval`, `arguments`)
 - You won't be able to delete variables (e.g. `delete result`)
 - You won't be able to delete functions (e.g. `delete thisIsAFunction`)
 - **If you are not using** '`use strict'` then **you are able to do all of the above**
 - **If you are not using** `'use strict'`then **mis-typed variable names will be globally scoped** (declared globally)

### Truthy, Falsy
 - Any var with a value of a `"non-empty string"`, `10` (integer greater or less than a `0`, but never `0`), or the `true` boolean are considered **`true`**
 - any var with a value of `undefined`, `null`, `NaN`,`false`, or one that contains an empty string `""` evaluates to **`false`**

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

### And (`&&`), Or (`||`) Operators
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
````

### Not (`!`) Operator
- `!` must go in front of the full expression being evaluated

**Example**

````
function myFunction() {
    let x = 9;
    if (!x > 10) { // evaluates to true
        document.write("true");
    } else {
        document.write("false");
    }
}
myFunction(); // outputs true
````

### Short Circuiting
- in the case of `&&`, if the first part of the expression (or left side of the full expression) evaluates to false, then the second part of the expression (or right side of the full expression) are *not* evaluated.
- in the case of `||`, if the first part of the expression (or left side of the full expression) evaluates to true, then the second part of the expression (or right side of the full expression) are *not* evaluated.

### Order of Precedence
The order of operation precedence is as follows ... top of the stack is highest precedence, and lowest of the stack is lowest precedence ...
 - Grouping `()`
 - Not `!`
 - Multiplication `*`
 - Division `/`
 - Modulus `%`
 - Addition `+`
 - Subtraction `-`
 - Less than `<`
 - Less than or equal to `<=`
 - Greater than `>`
 - Greater than or equal to`>=`
 - Equal to `==`
 - Not equal to`!=`
 - Strict equal to `===`
 - Strict not equal to `!==`
 - And `&&`
 - Or `||`
 - Assignment `=`  

### Try, Catch, Finally
Here's what they do ...
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

Types of Errors to familiarize yourself with are ...
 - `referenceError`
 - `rangeError`
 - `typeError`
 - `uriError`
 - `syntaxError`
 - `evalError`

These are built-in Error objects to check for.

### Primitive Data Types
Primitive data types are as follows ...
 - boolean: either `true`, or `false`
 - null: is described as having no value and usually represented as `null`
 - undefined: is described as a variable having been declared with no value, or an empty variable. Usually represented as `undefined`
 - number: usually represented by types of numbers such as integers, decimals, floats, etc.
 - string: an array (or series) of characters

### Object Data Types
 - `new Array()`: typically a collection of values
 - `new Error()`: contains properties of name and message
 - `new Function()`: contains a block of code to be executed when called by the function's name
 - `new Object()`: a wrapper around any data type
 - `new RegExp()`: a regular expression
 - `new Boolean()`: an object that contains either true or false
 - `new Number()`: an object that contains a numeric value
 - `new String()`: an object that contains a series of characters

Objects take up more memory space than primitive data types. Use primitive where possible in an effort to eliminate overuse of objects.

### `typeof` Operator
The `typeof` operator returns an evaluation of an object's type when you pass that object to it.

**Example**
```
typeof "Hello"; // evaluates to 'string'
```

### The Object Data Type's Constructor Property
 - All object data types inherit from objects. Conversely, primitive data types do not inherit
 - All objects have a constructor property
 - The constructor property returns a reference to the object it belongs to ... this allows us to learn a few things about the object itself

**Example**
```
// Pseudo code
data_type.constructor.toString(); // will output a string value that tells us what data type 'data_type' is

data_type.primitive.constructor.toString(); // will output to a string value that tell you what it is after constructor applies (assigns) a constructor property to the primitive. Meanwhile, objects _already have_ constructors
```

### `instanceof` Operator
 - tests if an instance of an object inherits from another object (not a primitive)
 - tests for a specific type of object, or an object itself

**Example**
```
let prod = new Product(680, "Road Frame");
console.log(prod instanceof Product.toString()); // above returns output of \`true\`
```



### `this`

