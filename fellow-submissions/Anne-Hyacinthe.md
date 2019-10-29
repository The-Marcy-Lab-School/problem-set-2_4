# Problem Set 2.4 - Scope

**1. How do variables declared with `let`, `const`, and `var` differ? Be sure to touch on _scope_, _reassignment_, and _hoisting_ for each.**

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
*```outer inner outer``` The first and last log were 'outer' because they don't have a local scope with an 'a' variable so they had to call the value from the global scope.
**3. What will the following code log? Why?**
    ```javascript
    function hello() {
      let a = 'hello';
    }

    hello();
    console.log(a);
    ```
*It will log an undefind error because ```console.log(a)``` is not in the functions scope and there is not an 'a' in the global scope to call either.
**4. What does the following code log? Why?**
    ```javascript
    console.log(a);

    var a = 1;
    ```
*It will log as 'undefined' becasue vars lexical environment value is 'undefined' until it's initialized, and 'a' is initialized after it is logged.
**5. What does the following code log? Why?**
    ```javascript
    console.log(a);

    let a = 1;
    ```
*It will log as an error becasue 'lets' lexical environment value is 'uninitialized' until it's initialized, and 'a' is initialized after it is logged.
**6. In the code snippet below, the function declaration comes _after_ the variable declaration in the code below. Why does it still work?**
    ```javascript
    let name = "Devonte";

    function sayItLoud() {
      console.log(`${name}!!!`)
    }

    sayItLoud();
    ```
*The code still runs because the function scope is available to call variables from the global scope.    
**7. Why does the following code throw an error? What is the key difference between it and the example above?**
    ```javascript
    sayItLoud();

    function sayItLoud() {
      console.log(`${greeting}!!!}`)
    }

    let greeting = "Hello"
    ```
*The code runs an error because 'greeting' is initialized after the function is read. 
**8. What does the following code log? Why?**
    ```javascript
    let problemSet;

    function complete(assignment) {
      assignment = "done";
    }

    complete(problemSet);
    console.log(`Status for Problem Set: ${problemSet}`);
    ```
it logs ```Status for Problem Set: undefined``` because _problemSet_ was never initialized causing the lexical environment value to remain 'undefined'.
**9. Why does this code throw an error?** 
    ```javascript
    const isSunny🌞 = true;

    if (isSunny🌞) {
      let advice = 'Wear your sunshades!';
    }

    console.log(advice);
    ```
* It throws an error because _advice_ is defined and initialized in a local scope but is being called in the global scope.
**10. So... why does this code work as intended?**
    ```javascript
    const isRainy🌧 = true;

    if (isRainy🌧) {
      var advice = 'Pack your umbrella.';
    }

    console.log(advice);
    ```
*It works as intended because 'var' is a global scope.