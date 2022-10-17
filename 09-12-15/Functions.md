# Functions
From the video series [Javascript: Functions](https://app.pluralsight.com/library/courses/javascript-functions/table-of-contents)

Functions make coding JS faster, easier, and less prone to errors. A function is a block of organized, reusable code that is used to perform a single, related action.

A function **parameter** is a variable that we list as part of a function definition. An **argument** is a value that we pass to a function parameter when we invoke it. 

The `argument` Object allows us to pass as many arguments as we need to. See the below example for usage.

**Example**

A simple function declaration, passing the argument `John` to the function's parameter `name`.
```
// Below, we define or 'declare' the function 'greetings()'
function greetings(name) {
    console.log(`Hello, ${name}!`);
}
greetings('John'); // Here we invoke the function; Returns 'Hello, John!'
```

**Example**

A simple function declaration, using a return value `Hello, John!`. Notice that we store the return value that `greetings()` gives us in the `message` variable. This is so that the return value doesn't get lost, and we can use it like we do in the `console.log()` method below. If you do not store the return value in a variable, it is lost (i.e. not stored in memory).
```
// Below, we define or 'declare' the function 'greetings()'
function greetings() {
    return 'Hello, John!';
}
let message = greetings();
console.log(message); // Returns 'Hello, John!'
```

**Example**

Using the `argument` Object.
```
function printAll() {
    for(let i = 0; i < arguments.length; i++) {
        console.log(arguments[i]);
    }
}
printAll(1, 2, 3, 4, 5); // Returns '1 2 3 4 5'
printAll(10, 20); // Returns '10 20'
```

## Function and Block Scope
Function scope refers to any code that is inside a function. Block scope refers to any code within curly brackets `{}` that is not a function. A variable declared with `const` or `let` honor the scope rules. A variable declared with the `var` keyword, do _not_ honor scope rules.

When a variable is _in scope_ it exists in the same function or block of code where it was declared and initiated. A variable is _out of scope_ when it is declared in a function, or a block, but can't be referenced and manipulated in a separate function or block, or the global space (where it hasn't been declared previously). Any variable declared in the global space is available in the global space's functions and code blocks.

Read more in-depth material on [Function, Block, and Lexical Scope](https://www.freecodecamp.org/news/javascript-lexical-scope-tutorial/).


## Additional Material
Additional learning material from this lesson has been eliminated to reduce repetition. You can find more information about the below list of topics in either the [JS Fundamentals](../09-05-08/2-Fundamentals.md) or [Syntax and Operators](../09-05-08/3-Syntax-and-Operators.md) notes files from pervious lessons and series of videos.

Topics from this video series that were dropped since they were already covered in [JS Fundamentals](../09-05-08/2-Fundamentals.md) and [Syntax and Operators](../09-05-08/3-Syntax-and-Operators.md), include ...
 - Immediately Invoked Function Expressions (IIFE)
 - How Closures Work
 - Arrow Functions
 - Function Context
 - call() Method
 - apply() Method
 - bind() Method
 - Built-in JS Functions
 - Default Parameters
 - Rest Parameters
 - The Spread Operator


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

## TITLE
**Example**
```
```

## TITLE
**Example**
```
```



