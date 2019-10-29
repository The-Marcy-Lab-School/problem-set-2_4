# Problem Set 2.4 - Scope

**1. How do variables declared with `let`, `const`, and `var` differ? Be sure to touch on _scope_, _reassignment_, and _hoisting_ for each.**
    Variables starting with var can have either global scope or a function scope, which is like having a bubble around the variable
    that is created depending on where it is declared. This allows you to initialize a variable before and after the variable has been
    delared.Var variables can be reassigned as many times as you want just as long as the reassigning is being done in its scope. When 
    being hoisted, only the var variables declaration will be "read" first, then as the program is compiled it will read the initialization. 
    Both let and const variables have block scopes, which is like a bubble after the variable has been declared depending on where it was 
    declared. This allows you to only initialize the variable after the declaration. let variables can also be reassigned as many times, just as 
    long it is done after the declaration of the variable and in its scope. While const variables can never be reassigned to anything else, even 
    if it is being done inside it's scope. Var hoisting variables allows the declaration to be read the declration before it is even declared and
    will set its value to undefined, while let and const variables don't get hoisted meaning that they aren't read before they are declared, 
    they are read when they are declared.  

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
    This will console log :
    outer
    inner
    outer
    
    Because the variable a creates a block scope surrounding the whole program, so when a is called the value that it has is "outer", but inside
    the function testScope it is declared and initialized again but this doesn't affect the first variable since this one only exists inisde the
    function. So when it is called inisde the function the value is "inner".
**3. What will the following code log? Why?**
    ```javascript
    function hello() {
      let a = 'hello';
    }

    hello();
    console.log(a);
    ```
    This will console log:
    undefined
    a is undefined
    
    Because the function isn't returning anything so it's just undefined. Since the variable a only exists inside the function hello, it can't 
    be accessed outside the function/scope. 
**4. What does the following code log? Why?**
    ```javascript
    console.log(a);

    var a = 1;
    ```
   This will console log:
   Undefined
   
   Because even though the variable is being hoisted, only the declaration is being read so it isn't initialized until it is fully compiled. 
   
**5. What does the following code log? Why?**
    ```javascript
    console.log(a);

    let a = 1;
    ```
    This will console log:
    a is undefined
    
    Because let variables don't get hoisted, they don't exist before they are declared. So the variable a is something that doesn't exist
    
**6. In the code snippet below, the function declaration comes _after_ the variable declaration in the code below. Why does it still work?**
    ```javascript
    let name = "Devonte";

    function sayItLoud() {
      console.log(`${name}!!!`)
    }

    sayItLoud();
    ```
    Because name is a variable who's blockscope includes the function sayItLoud, so when that function uses the variable name, it will
    take the value it was assigned to.
    
**7. Why does the following code throw an error? What is the key difference between it and the example above?**
    ```javascript
    sayItLoud();

    function sayItLoud() {
      console.log(`${greeting}!!!}`)
    }

    let greeting = "Hello"
    ```
    This doesn't work because the function sayItLoud doesn't exist inside the variables greeting's scope so greeting inside the function doesn't
    exist.

**8. What does the following code log? Why?**
    ```javascript
    let problemSet;

    function complete(assignment) {
      assignment = "done";
    }

    complete(problemSet);
    console.log(`Status for Problem Set: ${problemSet}`);
    ```
    This will console log:
    undefined
    
    Because the variable problemSet is declared but not initialized, and it's being console logged in it's scope so it exists but has no value.

**9. Why does this code throw an error?** 
    ```javascript
    const isSunny🌞 = true;

    if (isSunny🌞) {
      let advice = 'Wear your sunshades!';
    }

    console.log(advice);
    ```
    This throws an error because the variable advice doesn't exist outside of the if function since it can't be hoisted.

**10. So... why does this code work as intended?**
    ```javascript
    const isRainy🌧 = true;

    if (isRainy🌧) {
      var advice = 'Pack your umbrella.';
    }

    console.log(advice);
    ```
    This works because the variable advice gets hoisted so it exists before the variable is even declared. 
    
