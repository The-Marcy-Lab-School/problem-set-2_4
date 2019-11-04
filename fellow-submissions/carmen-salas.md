# Problem Set 2.4 - Scope

**1. How do variables declare with `let`, `const`, and `var` differ? Be sure to touch on _scope_, _reassignment_, and _hoisting_ for each.**

*Variable keywords ‘let’ and ‘const’ have a block scope. The keyword ‘const’ can not be reassigned a new value but can be mutated. 
*All declaration keywords in Javascript are hoisted, except for variables declared with the keyword ‘var’, it will add that variable to the lexical environment and initialize it with undefined. Variables with ‘let’ and ‘const’ declarations are uninitialized. 

**2. What will the following code log? Why?**
    ```javascript
    let a = 'outer';

    function testScope() {
      let a = 'inner';
      console.log(a);
    }

    console.log(a);
    testScope();
    console.log(a);
    ```
*This code will log “outer”, “inner”, “outer”. This is because the variable ‘a’ is declared with the value “outer” outside the function “testScope”. 
*In the function the variable ‘a’ is declared with the value “inner”. When ‘a’ is logged outside of the function ‘testScope’ is returns the value of the global variable ‘a’ and when the function ‘testScope’ is called it returns the value of the variable ‘a’ in the function scope which is ‘inner’.
*When the variable ‘a’ is logged again is returns ‘outer’ and not ‘inner’ because the value ‘inner’ only applies to the ‘a’ variable in the local scope of the function ‘testScope’


**3. What will the following code log? Why?**
    ```javascript
    function hello() {
      let a = 'hello';
    }

    hello();
    console.log(a);
    ```
    *This will return undefined first then will result as an error and log ‘a is not defined’. This is because when the variable ‘a’ is declared in the function ‘hello’, it is never returned in the function, so the function does not return anything and does not take in a parameter, therefore it returns undefined. 
    *When the variable ‘a’ is logged outside of the function scope it returns an error because the variable does not exist outside of its local scope. 

**4. What does the following code log? Why?**
    ```javascript
    console.log(a);

    var a = 1;
    ```
*It will result as an error and log ‘a is not defined. This is because the variable ‘a is declared after it is logged and because it is declared with ‘var’ it is not hoisted. 

**5. What does the following code log? Why?**
    ```javascript
    console.log(a);

    let a = 1;
    ```
*This will result as an error and ‘a is not defined’ because the variable ‘a’ is declared with ‘let’ it is hoisted but not initialized. 

**6. In the code snippet below, the function declaration comes _after_ the variable declaration in the code below. Why does it still work?**
    ```javascript
    let name = "Devonte";

    function sayItLoud() {
      console.log(`${name}!!!`)
    }

    sayItLoud();
    ```
*This will work because local scopes can access variables declared in the global scope, therefore in the function ‘sayItLoud’ when the variable ‘name’ is called, it will return the value ‘Devonte’ because it was initialized in the global scope and is a global variable. 
*If a variable was declared in the local scope it would not be able to be called in the global scope. 

**7. Why does the following code throw an error? What is the key difference between it and the example above?**
    ```javascript
    sayItLoud();

    function sayItLoud() {
      console.log(`${greeting}!!!}`)
    }

    let greeting = "Hello"
    ```
*This throws an error because the function ‘sayItLoud’ is not initialized before it is called. The variable ‘greeting’ is not decalared before the function is initiated or called. 

**8. What does the following code log? Why?**
    ```javascript
    let problemSet;

    function complete(assignment) {
      assignment = "done";
    }

    complete(problemSet);
    console.log(`Status for Problem Set: ${problemSet}`);
    ```
*This will return ‘Status for problem set: undefined’. This is because when the variable ‘problemSet’ is declared, it is not initialized with a value therefore it would return undefined when called.
*In the function ‘complete’ the parameter ‘assignment’ was assigned a value of “done”. However, when the function is called taking in the variable ‘problemSet’ as a parameter it returns the value of the global variable which was undefined, because the reassignment of the parameter ‘assignment’ doesn’t reassign the variable ‘problemSet’
*When logging the variable ‘problemSet’ it will return undefined because it was never initiated with a value. 

**9. Why does this code throw an error?** 
    ```javascript
    const isSunny🌞 = true;

    if (isSunny🌞) {
      let advice = 'Wear your sunshades!';
    }

    console.log(advice);
    ```
*This will throw an error because the variable ‘advice’ was declared in the local scope of the if statement. 

**10. So... why does this code work as intended?**
    ```javascript
    const isRainy🌧 = true;

    if (isRainy🌧) {
      var advice = 'Pack your umbrella.';
    }

    console.log(advice);
    ```
*This is because variables declared with the keyword ‘var’ outside any function are global variables. So even though the variable ‘advice’ is called inside a scope it is not a function so it is global. 


