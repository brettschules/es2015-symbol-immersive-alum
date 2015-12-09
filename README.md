# Symbol

## Overview

In this lesson, you will get to know ES2015's new data type Symbol.

## Objectives

1. Understand how to declare symbols.
2. Understand how symbols are different than other data types.
3. Understand how to find symbol properties on an Object.
4. Become familiar with some of Symbol's methods.

## ~ ?min

<!-- iframe of video lecture goes here -->

*The code examples from this lesson can be run by pasting them into [Babel's online REPL](https://babeljs.io/repl/)*

## Understanding Symbols

JavaScript allows us to fill our apps with different primitive data types: numbers, strings, and boolean. In ES2015 we get an additional primitive data type known as a Symbol.

### What Is a Symbol?

Symbols are a unique and immutable data type. This means that once created they reserve a unique place in memory. They are like a snowflake.

### Making Symbols

We can create a symbol by using the Symbol object like so  
```javascript
var snowflake = Symbol();
```  
Optionally you can also give them a string description as an argument:  
```javascript
var snowflake = Symbol("a unique snowflake")`. 
console.log(snowflake); // Symbol(a unique snowflake)
``` 
This description can be used for debugging purposes, but we would not use the description string to access the symbol itself. In this case to access the symbols value we would just refer to its label `snowflake`.
We can demonstrate their data type as follows:  
```javascript
console.log(typeof snowflake); // 'symbol'
```
One thing to note is that you can't declare a symbol using the new keyword:
```javascript
// This is correct:
var snowflake = Symbol();

// This is not proper!:
var snowflake = new Symbol(); // Uncaught TypeError: Symbol is not a constructor
```
Symbols do to their uniqueness, make them excellent choices as labels for object keys. Especially if we want to protect the key from being overwritten by someone else whom used the same label in another code library we are linking to.

### Uniqueness

To appreciate a symbols uniqueness let's compare symbols to strings:  
```javascript
var str1 = "hello";
var str2 = "hello";

console.log(str1 === str2) // true

var sym1 = Symbol();
var sym2 = Symbol();

console.log(sym1 === sym2) // false
```  
In the above code you can see that two strings with the same characters are equal to each other (not unique) where as the two symbols are not equal (each is a unique label in memory).

### Assigning Symbols as Object Keys

Let's take a look at assigning a symbol as a key to an object property:
```javascript
// first we will create an object

var ghostBusters = {};

// Then let's create a new symbol.

var members = Symbol('array of ghost busting team');

// Next we will create a new key on our object using [] square brackets and assign it a value.

ghostBusters[members] = ['Egon Spengler', 'Peter Venkman', 'Ray Stantz', 'Winston Zeddemore'];

console.log(ghostBusters[members]); // ['Egon Spengler', 'Peter Venkman', 'Ray Stantz', 'Winston Zeddemore']

// Notice that using dot notation does not refer to our unique key

console.log(ghostBusters.members); // undefined
```  
In the code above, you can see that we first created an empty object called ghostBusters. Then we declared our symbol called members and optionally passed a description of what this symbol is for 'array of ghost busting team'. To set a symbol as a unique key on our object we need to use `[]` surrounding our symbol such as `ghostBusters[members]`. Notice that later if we use dot notation `ghostBusters.members` this does not refer to our property symbol but some undefined property name. Interesting... Let's better understand the difference between using a string label for an object key vs a symbol label.  
```javascript
var ghostBusters = {};
var members = Symbol('array of ghost busting team');

// Assign a key using a string:

ghostBusters['members'] = ['Louis Tully', 'Janine Melnitz'];

// Assign a key using a symbol:

ghostBusters[members] = ['Egon Spengler', 'Peter Venkman', 'Ray Stantz', 'Winston Zeddemore'];

// Check the values using string labeled key:
console.log(ghostBusters['members']); // ['Louis Tully', 'Janine Melnitz'];

// Check the values using symbol labeled key:
console.log(ghostBusters[members]); // ['Egon Spengler', 'Peter Venkman', 'Ray Stantz', 'Winston Zeddemore'];

// Check the values using dot notation (defaults to the string labeled key):
console.log(ghostBusters.members); // ['Louis Tully', 'Janine Melnitz'];)
```

### Looking Up Property Symbols

In past versions of JavaScript, if you needed to look up all the properties of an object you could use the Object method `getOwnPropertyNames()`. In order to get a list of all the symbol properties instead we can use the Object method `getOwnPropertySymbols()`. To demonstrate this let's look at the following code and take into account the code of the previous example above:  
```javascript
// display all (string) name properties

console.log(Object.getOwnPropertyNames(ghostBusters)); // [ 'members' ]

// display all symbol properties

console.log(Object.getOwnPropertySymbols(ghostBusters)); // [ Symbol(array of ghost busting team) ]
```

Symbols also give us many baked in methods that are useful for manipulating them.

### Symbol Methods

We won't cover Symbol methods in this lesson, but you can refer to the complete list and get its current browser support details at [MDN - JavaScript - Symbol - Methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol#Methods).

## Summary

- Symbols can be declared using the Symbol object and optionally can be given a description of what they are for `var members = Symbol('array of ghost busting team')`.
- Symbols are unique snowflakes that are ideal as object properties `ghostBusters[members] = [...]`.
- These properties are not accesable in the ways that string labeled property names are.
- Symbols have many useful built in methods for operating on them.

## Resources

- [MDN - JavaScript - Symbol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol)
- [Mozilla Hacks - Symbols in Depth Tutorial](https://hacks.mozilla.org/2015/06/es6-in-depth-symbols/)