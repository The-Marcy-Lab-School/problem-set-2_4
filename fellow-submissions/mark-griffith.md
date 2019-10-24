# Problem Set 2.4 - Scope

**1. How do variables declared with `let`, `const`, and `var` differ? Be sure to touch on _scope_, _reassignment_, and _hoisting_ for each.**
   
   Var is a globally scoped variable that can be reassigned.It also can be declared again, but don't do this. The variable is hoisted.
   Let is a block scoped variable that can be reassigned.This variable can not be hoisted.
   Const is a block scoped variable that cannot be reassigned.This variable can not be hoisted.
   
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
    The console will log "outer" then "inner" the "outer".
    The first time a is logged it references the globally scoped value and logs.
    Since "inner" is in the functiom scope JavaScript will run with the value of a within that scope. So the function logs the inner value.
    Finally the console logs the original value of a since it was only reassigned in the function scope and not the global scope. 
    
**3. What will the following code log? Why?**
    ```javascript
    function hello() {
      let a = 'hello';
    }

    hello();
    console.log(a);
    ```
    The code will not log anything when hello(); is called because the function is only declaring a variable.
    Console.log(a) will also not log anything, but it would throw an error.
    Since a is declared in the function scope and not the global scope the variable cannot be accessed in the global scope.
    It will opt to throw an error stating a is undefined.
    
**4. What does the following code log? Why?**
    ```javascript
    console.log(a);

    var a = 1;
    ```
    This code will log 1 since the variable declared by the var keyword would be hoisted up when called.
  
**5. What does the following code log? Why?**
    ```javascript
    console.log(a);

    let a = 1;
    ```
    This will not run because variables declared with the let keyword are not hoisted.

**6. In the code snippet below, the function declaration comes _after_ the variable declaration in the code below. Why does it still work?**
    ```javascript
    let name = "Devonte";

    function sayItLoud() {
      console.log(`${name}!!!`)
    }

    sayItLoud();
    ```
    The code would log "Devonte!!!" since the function would look for a variable called name after first checking the local scope.
    Since a child scope can view data from a parent scope it will see the variable declared there and use its value for the function.
    It will then use string concatenation to add exclamation points to the string and return it.
    
**7. Why does the following code throw an error? What is the key difference between it and the example above?**
    ```javascript
    sayItLoud();

    function sayItLoud() {
      console.log(`${greeting}!!!}`)
    }

    let greeting = "Hello"
    ```
    The variable greeting is not declared before the function is called so the function will not be able to access it.
    Variables under the let keyword are not declared so the variable would not be hoisted either.

**8. What does the following code log? Why?**
    ```javascript
    let problemSet;

    function complete(assignment) {
      assignment = "done";
    }

    complete(problemSet);
    console.log(`Status for Problem Set: ${problemSet}`);
    ```
    The first line will return undefined and the second will log "Status for Problem Set: undefined".
    Since complete(problemSet) is referencing the variable problemSet it will take its value which will return undefined since it was not reassigned in the function.
    As a consequence the second line logs undefined because of the same problem.
    
**9. Why does this code throw an error?** 
    ```javascript
    const isSunny🌞 = true;

    if (isSunny🌞) {
      let advice = 'Wear your sunshades!';
    }

    console.log(advice);
    ```
   Since advice is initialized and declared in a local scope the log cannot see it and an error is thrown.
   

**10. So... why does this code work as intended?**
    ```javascript
    const isRainy🌧 = true;

    if (isRainy🌧) {
      var advice = 'Pack your umbrella.';
    }

    console.log(advice);
    ```
    Variables declared under the var keyword are globally scoped so the value is accessable in this case.