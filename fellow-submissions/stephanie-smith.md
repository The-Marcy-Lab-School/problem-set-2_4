# Problem Set 2.4 - Scope

**1. How do variables declared with `let`, `const`, and `var` differ? Be sure to touch on _scope_, _reassignment_, and _hoisting_ for each.**
- Variables declared with `var` can be reassigned as often as you want, and you can access them regardless of scope. However, if you are going to use `var` with function expressions, you cannot hoist them, so you'll have to declare it after the function expression is initialized.
  Variables declared with `let` can also be reassigned, but you cannot access them outside their scopes, so you can use the same variable in different scopes and get different results. Regarding hoisting, they also cannot be hoisted so you'll have to declare them after they're initialized. Variables declared with `const` cannot be reassigned, so whatever is initialized in the variable remains that way. They also cannot be hoisted, and just like `let`, they cannot be accessed outside their scope.

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
  - It will log 'outer', then 'a is not defined' , because the function `hello()` was called first, allowing the variable `a` to log its value. However, when you console.log `a` without calling the function, it does not work because there is no `a` in the global scope. Since the `a` in the function can't be accessed from the global scope, it simply remains undefined because `a` technically does not exist.

**4. What does the following code log? Why?**
    ```javascript
    console.log(a);

    var a = 1;
    ```
  - It will log undefined because `a` was declared, but not initialized. It then calls upon `a`, which is still undefined, and only after it's called is it defined to be equal to 1.
  
**5. What does the following code log? Why?**
    ```javascript
    console.log(a);

    let a = 1;
    ```
  - This will log an error because `a` is not defined. `let` variables do not get initialized with anything, so there will be a reference error.

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
  - The function is called before it is even declared, so `greeting` doesn't even exist yet despite it being in the global scope.

**8. What does the following code log? Why?**
    ```javascript
    let problemSet;

    function complete(assignment) {
      assignment = "done";
    }

    complete(problemSet);
    console.log(`Status for Problem Set: ${problemSet}`);
    ```
  - It logs "Status for Problem Set: undefined" because problemSet was never initialized, so it becomes undefined.

**9. Why does this code throw an error?** 
    ```javascript
    const isSunny🌞 = true;

    if (isSunny🌞) {
      let advice = 'Wear your sunshades!';
    }

    console.log(advice);
    ```
  - The variable `advice` is declared and initialized in the function, so it's not accessible in the global scope. Instead, it's better to call the function and return `advice` in the function.

**10. So... why does this code work as intended?**
    ```javascript
    const isRainy🌧 = true;

    if (isRainy🌧) {
      var advice = 'Pack your umbrella.';
    }

    console.log(advice);
    ```
  - This code works because `var` is accessible regardless of scope. Even if `advice` is inside the function, the global scope can access it and log 'Pack your umbrella'.