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
  - +
  - -
  - *
  - /
  - **
  - %

### Operators
 - operand operator operand
 - operands are what's being "operated" on by the operator

### Plus Caveats (Addition/Concatination)
 - "strings" + "strings" is concatination and combines the two strings together
 - number + number is addition

### Assignment Operators
- price = 5 // var price is set to equal 5
 - price += 5 // price = price + 5 (or price = 5 + 5); evaluates to 10
 - price *= 5 // price = price * 5 (or price = 5 * 5); evaluates to 25
 - price /= 5 // price = price / 5 (or price = 5 / 5); evaluates to 1
 - price **= 5 // price = price ** 5 (or price = 5^5 [5 to the power of 5]); evaluates to 3125
 - price %= 5 // price = price / 5 to get the remainder of 1 (this can be used to evaluate whether an integer is odd or even)

### Comparison Operators (In order of precedence)
 - < // Less than
 - <= // Less than or equal to
 - > // Greater than
 - >= // Greater than or equal to
 - == // Equal to (means only the value is considered during evaluation despite it being a string or integer)
 - != // Not equal to
 - === // Strict equals (means value and date type are considered during evaluation)
 - !== // Strict not equal

### 'use strict'
 - always be using (best practice)
 - it is ignored by older browsers
 - it forces variables to be declared first, before use
 - can't use "reserved" key words in JS as variable names (e.g. "eval", "arguments)
 - can't delete variables (e.g. "delete result")
 - can't delete functions (e.g. "delete thisIsAFunction")
 - if you **don't have 'use strict' in effect** then you **can do** all of the above
 - mis-typed variable names will be globally scoped (declared globally) if you are **not using 'use strict'**

### Truthy, Falsy
 - any var with a value of "non-empty string", 10 (integer greater or less than a 0), or the `true` boolean are considered **true**
 - any var with a value of `undefined`, `null`, `NaN`,`false`, or that contains an empty string `""` evaluates to **false**

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

 - rather than use an if statement, you can use the Boolean() function

 **Example**

 ```
 function myFunction() {
    let color = null;
    document.write(Boolean(color));
 }
 myFunction(); // evaluates to false
 ```

### And, Or Operators



Notes

**Example**
```

```



> Section-by-section content template
## Title

Notes

**Example**
```

```



> Section-by-section content template
## Title

Notes

**Example**
```

```



> Section-by-section content template
## Title

Notes

**Example**
```

```



> Section-by-section content template
## Title

Notes

**Example**
```

```



> Section-by-section content template
## Title

Notes

**Example**
```

```



> Section-by-section content template
## Title

Notes

**Example**
```

```



> Section-by-section content template
## Title

Notes

**Example**
```

```



> Section-by-section content template
## Title

Notes

**Example**
```

```



> Section-by-section content template
## Title

Notes

**Example**
```

```



> Section-by-section content template
## Title

Notes

**Example**
```

```



> Section-by-section content template
## Title

Notes

**Example**
```

```



