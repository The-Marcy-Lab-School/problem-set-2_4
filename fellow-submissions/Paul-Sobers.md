# Problem Set 2.4 - Scope

**1. How do variables declared with `let`, `const`, and `var` differ? Be sure to touch on _scope_, _reassignment_, and _hoisting_ for each.**
Answer: `Let` and `const` are local block scopes . `var` is a global scope. `let` and `var` values can be reassign. `const` value cannot be reassign. Only `var` can be hoisted because it is a global scope.

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
Answer: The following code will log "outer", "inner", "outer" because line 15 logs the variable `a` that is defined outside the function scope. Line 15 calls the fucntion testScope and the `a` that was defined inside that block scope the value was assigned 'inner' so it logs 'inner'. Line 17 does the same as line 15.

**3. What will the following code log? Why?**
    ```javascript
    function hello() {
      let a = 'hello';
    }

    hello();
    console.log(a);
    ```
Answer: The following code will throw an error saying `a` is not defined because we are declaring `a` inside a local scope and we tried to call it outside it's scope and it couldn't see. If we moved line 28 on under line 24 our code will work and log "hello" because we are now inside the block scope and it can see `a` is defined .

**4. What does the following code log? Why?**
    ```javascript
    console.log(a);
    var a = 1;
    ```
Answer: This code logs "undefined" becaue since `var` is a global scope it can be hoisted and only vaiables that can be hosited logs undefined.  
  
**5. What does the following code log? Why?**
    ```javascript
    console.log(a);

    let a = 1;
    ```
Answer: This code throw an error saying `a` is not defined because let variables can not be hoisted and you can call it before it is defined.

**6. In the code snippet below, the function declaration comes _after_ the variable declaration in the code below. Why does it still work?**
    ```javascript
    let name = "Devonte";

    function sayItLoud() {
      console.log(`${name}!!!`)
    }

    sayItLoud();
    ```
Answer: It still works becaue function scope can reach out to their parent scopes and reference them. Since name was declared globally it became the parent scope , when we created a fucntion and inisde this function scope we are logging `name` and "!!!" using  string interpolation. So we are reaching out to the global scope to see if `name` is defined and if it is use it.

**7. Why does the following code throw an error? What is the key difference between it and the example above?**
    ```javascript
    sayItLoud();

    function sayItLoud() {
      console.log(`${greeting}!!!}`)
    }

    let greeting = "Hello"
    ```
Answer: The following code throw an error because we defined `greeting` at the end of our code so our function is logging an variable that is not defined yet. The key difference between it and the example above we are declaring `name` globally before our function and here we are declaring greeting after our function.

**8. What does the following code log? Why?**
    ```javascript
    let problemSet;

    function complete(assignment) {
      assignment = "done";
    }

    complete(problemSet);
    console.log(`Status for Problem Set: ${problemSet}`);
    ```
Answer: The code log "Status for Problem Set : undefined" because `problemSet` was declared but not assigned a value.

**9. Why does this code throw an error?** 
    ```javascript
    const isSunny🌞 = true;

    if (isSunny🌞) {
      let advice = 'Wear your sunshades!';
    }

    console.log(advice);
    ```
Answer: The code throw an error because `advice` was declared inside a block scope using `let` and we are trying to reference a block scope outside its scope. So it does not see `advice` being declared inside the `if` statement and throw and error sayind advice is not defined.

**10. So... why does this code work as intended?**
    ```javascript
    const isRainy🌧 = true;

    if (isRainy🌧) {
      var advice = 'Pack your umbrella.';
    }

    console.log(advice);
    ```
Answer: This code works because `var` is a global scope so it can be access anywhere in the code and the example above use `let` to declare a variable and `let` is a local scope that can only be accessed in its scope.