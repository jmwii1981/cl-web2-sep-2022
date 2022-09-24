# JS 2018 Variables and Types Video and Class Notes

## Block Scope

"var" has "global and function scope" and doesn't have a "block scope"

**Example**
```
function MyFunction() {
    var x = 10;

    if (true) {
        var x = "Hello";
    }

    // x is the string of "Hello" here
}
```

"let" has a "block scope"

**Example**
```
function MyFunction() {
    var x = 10;

    if (true) {
        let x = "Hello";
        // x is the string of "Hello" here
    }

    // x is the value of 10 here
}
```

Just like "let", "const" has a "block scope"

**Example**
```
function MyFunction() {
    var x = 10;

    if (true) {
        const x = "Hello";
        // x is the string of "Hello" here
    }

    // x is the value of 10 here
}
```

If the x var does not exist outside of the if statement then it will throw an error when you call the x variable later

**Example**
```
function MyFunction() {

    if (true) {
        const x = "Hello";
        // x is the string of "Hello" here
    }

    console.log(x.length);
    // results in an error
}
```


## Redeclaring Variables

You may not declare a variable a second time with "let" witin the same scope after it has already been declared. However, as mentioned before, "var" can be re-declared within the scope that it belongs to.

**Example**
```
function MyFunction() {
    var y = 2;
    let y = 4; // not allowed    

    if (true) {
        var y = 4;
        let y = 2; // not allowed
    }

    console.log(x.length);
    // results in an error
}
```

However, you may redeclare "let" within different scopes as seen below.

**Example**
```
function MyFunction() {
   
    if (true) {
        let y = 2; // allowed
    }
    if (true) {
        let y = 3; // allowed
    }
    if (true) {
        let y = 6; // allowed
    }
}
```


## The Const Keyword

Notes

**Example**
```
    const arr=[3, 4, 5];
```