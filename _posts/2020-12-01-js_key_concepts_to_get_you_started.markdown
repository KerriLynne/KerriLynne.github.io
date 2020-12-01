---
layout: post
title:      "JS Key Concepts to Get You Started"
date:       2020-12-01 16:07:26 -0500
permalink:  js_key_concepts_to_get_you_started
---


After being introduced to JavaScript, concepts can seem pretty foreign to a new coder with no JS experience.  These were a few key terms that helped me begin to grasp the overall language and make sense of this whole new territory.

**Function Declaration** - must begin with “function” and will execute when it is invoked(called). Declarations are hoisted to the top of other code.

    function myFunction(a, b) {
      return a * b;
    }

**Function Expression** - a function expression can be stored in a variable, the variable can be used as a function.  Functions stored in variables do not need function names. They are always invoked (called) using the variable name and expressions are not hoisted.

    var x = function (a, b) {return a * b};
		
**Fetch** - is an interface for making an AJAX request in JavaScript. It is implemented widely by modern browsers and is used to call an API. Calling fetch returns a promise, with a Response object. Fetch method can be used with many types of requests such as GET, POST, PUT and DELETE.

    fetch('https://www.yourdomain.com', {
           method: 'get'
       })
       .then(response => response.json())
       .then(jsonData => console.log(jsonData))
       .catch(err => {
           //error block
       }

**preventDefault()** -a method that cancels the event if it is cancelable, meaning that the default action that belongs to the event will not occur.

**ES6 JS syntax** - allows you to write less code and do more. ES6 introduces us to many great features like arrow functions, template strings, class usage, Modules and more.

**Arrow Functions** - a new feature introduced in ES6 that is a more concise syntax for writing function expressions. While both regular JavaScript functions and arrow functions work in a similar manner, below are some benefits of arrow functions:
* same result, fewer lines of code
* if only one argument parenthesis aren’t required
* implicit return (can use return but don’t need it)
* more intuitive scoping and `this` binding.

```
hello = () => {
  return "Hello World!";
  }
```

**Hoisting** - JavaScript hoisting occurs during the creation phase of the execution context that moves the variable and function declarations to the top of the script.  The JavaScript engine hoists the variables declared using the let keyword but it doesn’t initialize them as the variables declared with the var keyword.  Function expressions and arrow functions aren’t hoisted.

**Template literals**- Template literals are string literals allowing embedded expressions. You can use multi-line strings and string interpolation features with them. Template literals are created by wrapping your text in backticks.

    let greeting = `Hi ${firstName}, ${lastName}`;
		
**Variables** `const` **and** `let`  - An important addition to ES6; these are both blocked-scope(only available within its scope).
`const` is a new keyword in ES6 for declaring variables. It is more powerful than `var`, once used, the variable can’t be reassigned. In other words, it’s an immutable variable.
`let` can be reassigned and take a new value. It creates a mutable variable and is the same as `const` in that both are blocked-scope. This means that the variable is only available within its scope.



