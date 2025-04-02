# Functions

Functions let us organize code, name them, and make them reusable. \
\
In this page we will learn how to:

- Use built-in functions
- Define functions
- Call our functions
- Passing functions to other functions

# Built-in Functions

Javascript comes with a lot of pre-define functions. Here are the ones we covered in class (I've added a link to the MDN documentation for each function):

- [`Math.random`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random) generates a random number between 0 and 1
- [`Math.abs`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/abs) removes the negative sign from a number if it's negative
- [`Math.round`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/round) rounds a number with a decimal point to the closes integer
- [`Math.ceil`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/ceil) rounds a number up to the next integer
- [`Math.floor`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/floor) rounds a number down to the previous integer
- [`Object.keys`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys) gives you a string array of an object's keys
- [`Object.values`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/values) gives you an array of an object's values
- [`Object.entries`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries) gives you an array where each item is an array of \["key", value]
- [`console.log`](https://developer.mozilla.org/en-US/docs/Web/API/console/log_static) prints output to the console
- [`console.table`](https://developer.mozilla.org/en-US/docs/Web/API/console/table_static) prints output to the console as a table
- [`console.time`](https://developer.mozilla.org/en-US/docs/Web/API/console/time_static) starts a timer
- [`console.timeEnd`](https://developer.mozilla.org/en-US/docs/Web/API/console/timeend_static) ends the timer and prints the total amount of time between start and end in milliseconds

We also covered "methods" (functions that you can call on values) for strings and arrays

- [`"string".charAt`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/charAt) returns the character at an index
- [`"string".startsWith`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/startsWith) returns `true` if a string starts with a value
- [`"string".endsWith`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/endsWith) returns `true` if a string ends with a value
- [`"string".replace`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace) replaces a substring with a different string
- [`"string".includes`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/includes) returns `true` if a substring is found within a string
- [`"string".trim`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/trim) removes whitespace from the start and end of a string
- [`"string".toUpperCase`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toUpperCase) transforms the string to ALL UPPER CASE
- [`"string".toLowerCase`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase) transforms a STRING to all lower case
- [`[1, 2, 3].filter`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) filters an array with a filter function
- [`[1, 2, 3].map`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) transforms each element in an array with a function
- [`[1, 2, 3].forEach`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach) like a for loop, but the body of the for loop is a function

It's worth taking a look at the MDN pages for [String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) and [Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) functions to see what other methods exist (things like `.sort`, `.reverse` and more).

# Calling Functions

To call a function, we use the name of the function followed by parantheses:

```javascript
function addNumbers(num1, num2) {
  return num1 + num2;
}

const result = addNumbers(1, 2); // result = 3
```

If a function doesn't have the `return` keyword in it, it will return `undefined`

```javascript
function addNumbers(num1, num2) {
  const addition = num1 + num2;
}

const result = addNumbers(num1, num2); // result = undefined
```

# Defining Functions

There are two syntaxes for functions. The basic syntax is as follows:

```javascript
/**
 * A simple function to add two numbers.
 * @param {number} num1 - The first number.
 * @param {number} num2 - The second number.
 * @return {number} The sum of the two numbers
 */
function addNumbers(num1, num2) {
  // body of the function goes in here
  return num1 + num2;
}
```

Some notes on the code above:

- This comment style is called a "JSDoc" and using it automatically creates documentation for your function which Visual Studio Code will show you when you use it.
- `function` is a keyword, and it describes the code block as a function.
- `addNumbers` is the name of your function, and it can be anything you want. The same rules that apply to variable names, apply to function names.
- `(num1, num2)` are called "function parameters". They are the list of variables which can be passed in to the function when it is called. A function can also have zero paramteres, in which case you will simply have an set of parentheses () with nothing between them.
- the return keyword marks the end of the function, and the expression following the return keyword is what the caller of the function gets when the function completes running. If a function has no return statement, it returns `undefined` .

The other syntax, which is called "function expression" syntax (or fat arrow, anonymous syntax, callback, or lambda) is as follows:

```javascript
const addNumbers = (num1, num2) => {
  return num1 + num2;
};
```

When we use a function expression, and there's only one statement in it, we can skip the curly braces and the `return` keyword:

```javascript
const addNumbers = (num1, num2) => num1 + num2;
```

# Passing Functions

The most straightforward way to use functions is to call them. But sometimes we don't call our functions directly, we just pass them to another function. This is particularly useful when we use array methods. For example, if we have a list of students `const students = ["Chaim Stern", "Moshe Weiss", "Duvid Stern", "Yakov Klein"]` and we want to filter them to get only the ones that are named "Stern". We can define our filter in a function, and then use `Array.filter` to filter the list;

```javascript
const students = ["Chaim Stern", "Moshe Weiss", "Duvid Stern", "Yakov Klein"];

function studentFilter(student) {
  return student.endsWith("Stern");
}

const studentsNamedStern = students.filter(studentFilter);
// studentsNamedStern = ["Chaim Stern", "Duvid Stern"]
```

Javascript also lets us define the filter function "inline" by using the function expression syntax

```javascript
const studentsNamedStern = students.filter((student) => {
  return student.endsWith("Stern");
});
```

Remember how one-line function expressions don't need the `return` keyword? We can make the above even shorter:

```javascript
const studentsNamedStern = students.filter((student) =>
  student.endsWith("Stern")
);
```

Similarly, we can use the `map` array method to transform the values in an array

```javascript
const students = ["chaim", "moshe", "yankel", "duvid"];
const upperCaseStudents = students.map((student) => student.toUpperCase());
// upperCaseStudents = ["CHIAM", "MOSHE", "YANKEL", "DUVID"
```
