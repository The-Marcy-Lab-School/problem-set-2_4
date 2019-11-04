# Problem Set 2.4 - Scope

**1. How do variables declared with `let`, `const`, and `var` differ? Be sure to touch on _scope_, _reassignment_, and _hoisting_ for each.**
- Variables declared with `var` can be reassigned as often as you want, and they are scoped by functions. If they are inside a function, they will not be defined if they are referenced from a global scope. `let` and `const` variables are block scoped, meaning that whenever their scope a block `{}`, and those variables are declared and initialized inside that block, they cannot be accessed from the global scope. `let` variables can also be reassigned as often as you want, but with `const`, they cannot be reassigned because it is a constant, so it will throw an error if it is reassigned. When it comes to these variables being hoisted, it depends on how or where they are declared. JavaScript only hoists declarations, not initializations; with `var`, the variable gets hoisted and initialized as undefined, so if it is called before it is reassigned, it will return undefined. With `let` and `const`, these variables get hoisted, but unlike `var`, they don't get initialized with anything. If you try to access them before they are initialized, it will give you a reference error, since you can't access the variable before initialization.

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
  - It will first log 'outer', then it will log 'inner', then it will log 'outer' again. The global scope will be called first because there is no direct reference to the scope that 'inner' is in. However, when the function is called, `a`'s value changes into what it is in the scope, and logs that out instead. Then it refers back to the global scope.

**3. What will the following code log? Why?**
    ```javascript
    function hello() {
      let a = 'hello';
    }

    hello();
    console.log(a);
    ```
  - It will log 'a is not defined'. The function `hello()` does not return anything since nothing is returned in the function; only a variable is declared. This variable cannot be referenced in the global scope however, so when you try to log `a`, it will say it is not defined because it does not exist outside of the function.

**4. What does the following code log? Why?**
    ```javascript
    console.log(a);

    var a = 1;
    ```
  - It will log undefined. When `a` is hoisted, it is initialized as undefined because it uses `var` to declarate it. When you log `a` first, it gives you what it is initialized as instead of the reassignment, which comes afterwards. 
  
**5. What does the following code log? Why?**
    ```javascript
    console.log(a);

    let a = 1;
    ```
  - This will log an error because `a` is not defined. `let` variables, when they're hoisted, do not get initialized with anything, so there will be a reference error.

**6. In the code snippet below, the function declaration comes _after_ the variable declaration in the code below. Why does it still work?**
    ```javascript
    let name = "Devonte";

    function sayItLoud() {
      console.log(`${name}!!!`)
    }

    sayItLoud();
    ```
  - Local scopes can access variables that are declared and initialized in the global scope, but global scopes can't access variables in the local scope, so in this case, it will still work.
    
**7. Why does the following code throw an error? What is the key difference between it and the example above?**
    ```javascript
    sayItLoud();

    function sayItLoud() {
      console.log(`${greeting}!!!}`)
    }

    let greeting = "Hello"
    ```
  - The function `sayItLoud()` gets hoisted along with its initialization, so it will not give you an error for calling the function before it is initialized. However, it is trying to log `greeting`, and when you hoist a `let` variable, it isn't initialized with anything. This is where the reference error comes in; `greeting` does not have a value that can be logged into the console. 

**8. What does the following code log? Why?**
    ```javascript
    let problemSet;

    function complete(assignment) {
      assignment = "done";
    }

    complete(problemSet);
    console.log(`Status for Problem Set: ${problemSet}`);
    ```
  - It logs "Status for Problem Set: undefined". `problemSet` is not initialized as anything in the beginning, which is also what it looks like when it is hoisted. `complete()` reassigns `problemSet`, but in the function, it does not return the value, so the new value ends up being stuck in the block scope of the function, and  `problemSet` becomes undefined when it is logged.

**9. Why does this code throw an error?** 
    ```javascript
    const isSunny🌞 = true;

    if (isSunny🌞) {
      let advice = 'Wear your sunshades!';
    }

    console.log(advice);
    ```
  - It throws an error because `let` is block scoped, meaning that `advice` can't be referenced outside of the if statement. This would mean that `advice` is not defined or initialized in the global scope.

**10. So... why does this code work as intended?**
    ```javascript
    const isRainy🌧 = true;

    if (isRainy🌧) {
      var advice = 'Pack your umbrella.';
    }

    console.log(advice);
    ```
  - This code works because `var` has a function scope. Block scopes do not apply to this specific type of variable, so it is still accessible even in the if statement.