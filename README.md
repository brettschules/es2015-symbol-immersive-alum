# Symbol

## Overview

In this lesson, you will get to know ES2015's new data type Symbol.

## Objectives

1. Understand how to declare symbols.
2. Understand the memory is allocated differently for symbols than other data types.
3. Understand how to find symbol properties on an Object.
4. Become familiar with some of Symbol's methods.

## ~ ?min

<!-- iframe of video lecture goes here -->

*The code examples from this lesson can be run by pasting them into [Babel's online REPL](https://babeljs.io/repl/)*

## Understanding Symbols

JavaScript allows us to fill our apps with the primitive data types: numbers, strings, and boolean. In ES2015 we get an additional primitive data type known as a Symbol.

### What Is a Symbol?

Symbols are a unique and immutable data type. This means that once created they reserve a unique place in memory. They are like a snowflake.

### Making Symbols

We can create a symbol by using the Symbol object like so `var snowflake = Symbol();`. Optionally you can also give them a string description as an argument `var snowflake = Symbol("a unique snowflake")`. This description can be used for debugging purposes, but we would not use the description string to access the symbol itself. In this case we would just refer to its var label `sym`.

Let's take this snowflake for a spin:  
```javascript
var snowflake = Symbol();
typeof snowflake; // 'symbol'.
``` 

## Uniqueness

To appreciate a symbols uniqueness lets compare symbols to strings:  
```javascript
// comparing strings
var str1 = "hello";
var str2 = "hello";

console.log(str1 === str2) // true

var sym1 = Symbol();
var sym2 = Symbol();
console.log(sym1 === sym2) // false
```  
Because symbols are unique, they can be used to avoid namespace issues. Meaning even if a variable or object key in our code is the same as another library we are using one will not overright the other, they will be seen as separate things.

Let's take a look at this by assigning a symbol as a key to an object property:
```javascript
//...
```
...

### 


## Summary

- Symbols can be declared like this `var symbol = Symbol("")`

## Resources

- [MDN - JavaScript - Symbol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol)
- [Mozilla Hacks - Symbols in Depth Tutorial](https://hacks.mozilla.org/2015/06/es6-in-depth-symbols/)