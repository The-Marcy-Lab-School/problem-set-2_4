# Problem Set 2.4 - Scope

**1. How do variables declared with `let`, `const`, and `var` differ? Be sure to touch on _scope_, _reassignment_, and _hoisting_ for each.**
  - Variables declared with `let` and `const` have a *block* scope while `var` varibales are initialized in the lexical scope. `var` and `let` variables can be reassigned but variables declared with `const` cannot, although their values can be mutated. All variables are hoisted, but only those with keyword `var` are initialized as undefined. 

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
    - This snippet logs `outer` `inner` `outer` because the first log refers to the variable `a`, which is only defined in its scope to be `outer`. `inner` is logged when the function `testScope()` is invoked because the console log inside that function has another variable by that name in its immidiate scope.

**3. What will the following code log? Why?**
    ```javascript
    function hello() {
      let a = 'hello';
    }

    hello();
    console.log(a);
    ```
    - This snippet returns a `ReferenceError` along the lines of `a is not defined`. This occurs because the console log refers to a variable outside of its global scope. 

**4. What does the following code log? Why?**
    ```javascript
    console.log(a);

    var a = 1;
    ```
    - This snippet logs undefined because the variable `a` is hoisted and thus available in the lexical scope, however, hoisted variables are initialized as undefined until assigned.
  
**5. What does the following code log? Why?**
    ```javascript
    console.log(a);

    let a = 1;
    ```
    - This snippet returns a `ReferenceError` because variables with the `let` keyword are hoisted but not initialized at all.

**6. In the code snippet below, the function declaration comes _after_ the variable declaration in the code below. Why does it still work?**
    ```javascript
    let name = "Devonte";

    function sayItLoud() {
      console.log(`${name}!!!`)
    }

    sayItLoud();
    ```
    - This snippet works because blocks can access their parent scopes if a reference isn't present in their immidiate scope.
    
**7. Why does the following code throw an error? What is the key difference between it and the example above?**
    ```javascript
    sayItLoud();

    function sayItLoud() {
      console.log(`${greeting}!!!}`)
    }

    let greeting = "Hello"
    ```
    - The differece between this snippet and the one above is the order in which important code is executed. The function `sayItLoud` is executed before the variable `greeting` is assigned. This matters here because its a variable declared with the `let` keyword and hoisted as uninitialized.

**8. What does the following code log? Why?**
    ```javascript
    let problemSet;

    function complete(assignment) {
      assignment = "done";
    }

    complete(problemSet);
    console.log(`Status for Problem Set: ${problemSet}`);
    ```
    - This snippet logs `Status for Problems Set: done` because `problemSet` was the argument os `complete`, a function that reassigned its value to `'done'`.

**9. Why does this code throw an error?** 
    ```javascript
    const isSunny🌞 = true;

    if (isSunny🌞) {
      let advice = 'Wear your sunshades!';
    }

    console.log(advice);
    ```
    - This code returns a error because the variable `advice` is outside of the scope of the console log that refers to it. 
    
**10. So... why does this code work as intended?**
    ```javascript
    const isRainy🌧 = true;

    if (isRainy🌧) {
      var advice = 'Pack your umbrella.';
    }

    console.log(advice);
    ```
    - This code 'works' because variable `advice` is hoisted and then assigned `Pack your umbrella.`
