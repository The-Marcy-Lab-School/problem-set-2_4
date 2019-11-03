# Problem Set 2.4 - Scope

**1. How do variables declared with `let`, `const`, and `var` differ? Be sure to touch on _scope_, _reassignment_, and _hoisting_ for each.**

  A variable declared with `var`, `let`, or `const` will have a global scope if declared outside of a function. If the variable `let`, or `const` is declared within the function it will have a local/function scope and `var` variables can be used outside of function scopes. Variables that are declared as `var` and `let` can be reassigned while variables declared as `const` cannot be reassigned. All variable declarations are hoisted however they are initialized to `undefined` unless they are `const` in which it will return a reference error. 
  
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
    The code will log 'outer' for lines 16 and 18 as the code logs the globally declared variable a that has been assigned to the string 'outer'. Line 17 will log 'inner' as it returns the locally scoped variable a that has been assigned to the string 'inner'. 
  
**3. What will the following code log? Why?**
    ```javascript
    function hello() {
      let a = 'hello';
    }

    hello();
    console.log(a);
    ```
    Line 28 will return undefined because there is no return statement or action taking place for the variable a. Line 29 will not log and will give a reference error as the variable a does not exists outside of the scope of the function hello and is undefined. 
    

**4. What does the following code log? Why?**
    ```javascript
    console.log(a);

    var a = 1;
    ```
    The code will log 1 as the `var`, a, is hoisted. 
  
**5. What does the following code log? Why?**
    ```javascript
    console.log(a);

    let a = 1;
    ```
    The code logs to a reference error as the variable declared as `let` must be defined before it can be accessed in a call to log.  

**6. In the code snippet below, the function declaration comes _after_ the variable declaration in the code below. Why does it still work?**
    ```javascript
    let name = "Devonte";

    function sayItLoud() {
      console.log(`${name}!!!`)
    }

    sayItLoud();
    ```
    
    The code still works because the function sayItLoud looks within its function scope for the variable name. Since it is not found within the function scope it looks within the outer scope, in this case it is in the global scope that the variable name is found. The function takes in the varible and passes its value into the console log. 
    
**7. Why does the following code throw an error? What is the key difference between it and the example above?**
    ```javascript
      sayItLoud();
  
      function sayItLoud() {
        console.log(`${greeting}!!!}`)
      }
  
      let greeting = "Hello"
    ```
    The code issues an error because a function cannot be called before a variable is declared. The previous example declared the variable before the function call. 
    
**8. What does the following code log? Why?**
    ```javascript
    let problemSet;

    function complete(assignment) {
      assignment = "done";
    }

    complete(problemSet);
    console.log(`Status for Problem Set: ${problemSet}`);
    ```
    Line 83 returns undefined as the variable problemSet is intialized to the value of undefined and is not reassigned in the fuction. Line 84 returns 'Status for Problem Set: undefined' again because problemSet still maintains being undefined. 

**9. Why does this code throw an error?** 
    ```javascript
    const isSunny🌞 = true;

    if (isSunny🌞) {
      let advice = 'Wear your sunshades!';
    }

    console.log(advice);
    ```
  The variable advice that is declared as a `let` variable does not exist outside of the function scope of isSunny therefore returns a reference error. 

**10. So... why does this code work as intended?**
    ```javascript
    const isRainy🌧 = true;

    if (isRainy🌧) {
      var advice = 'Pack your umbrella.';
    }

    console.log(advice);
    ```
    This code works as intended being as `var` variables can be accessed outside of their function scope. 
