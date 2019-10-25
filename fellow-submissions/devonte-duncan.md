# Problem Set 2.4 - Scope

**1. How do variables declared with `let`, `const`, and `var` differ? Be sure to touch on _scope_, _reassignment_, and _hoisting_ for each.**

   To begin with, the declaration of all three of these variable types are automatically 
   hoisted by javascript right before runtime, simply because they are variables.
   As for their differences, variables declared with `const`, are designed to
   be constant and therefore, JavaScript does not allow it's value to be reassigned.
   On the other hand, using `let` to declare a variable does allow you to reassign 
   its value later on. `let` and `const` are scoped variables, which means that its
   existence can only be detected within its parent scope, whether that be global 
   or local. As for `var` its properties are the same as `let`, except for the fact
   that its scope is global regardless of the location of its declaration.

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
    This above code will log:
        "outer"
        "undefined"
        "outer"
        
    This is logged because the string variable `a` is declared both in the global 
    scope as well as in the local scope of the `testScope` function. The value of `a` 
    that gets logged on lines 24 and 26 is "outer" because that's the onlt value of `a`
    that it has access to. Meanwhile "undefined" is logged because the function `testScope`
    is referenced, however there is no return value within it, thus "undefined" is logged.

**3. What will the following code log? Why?**
    ```javascript
    function hello() {
      let a = 'hello';
    }

    hello();
    console.log(a);
    ```
    This above code will log:
        "undefined"
        "ReferenceError: a is not defined"
    
    This is logged because the string variable `a` is declared only in the local scope 
    of the `hello` function, thus trying to log `a` to the console will result in an error.
    "undefined" is logged because the function `hello` is referenced, however there is no return 
    value within it, thus "undefined" is logged.
    

**4. What does the following code log? Why?**
    ```javascript
    console.log(a);

    var a = 1;
    ```
    The above code will log:
        "undefined"
    
    This logs "undefined" because even though the declaration of the variable `a` is hoisted
    before runtime, while its initialization is not. Thus the value of `a` on line 60 is
    logged as "undefined", until it assigned a value of 1 on line 62.
    
  
**5. What does the following code log? Why?**
    ```javascript
    console.log(a);

    let a = 1;
    ```
    This logs an error, because `let` is a scoped variable, JavaScript cannot access it until 
    it's been initialized. Therefore, even though it's declaration is hoisted, its initialization
    must also occur before it's referenced in order to work.

**6. In the code snippet below, the function declaration comes _after_ the variable declaration in the code below. Why does it still work?**
    ```javascript
    let name = "Devonte";

    function sayItLoud() {
      console.log(`${name}!!!`)
    }

    sayItLoud();
    ```
    The variable `name` was declared and initialized within the global scope, and 
    therefore can be seen/accessed from all other scopes as well.
    
**7. Why does the following code throw an error? What is the key difference between it and the example above?**
    ```javascript
    sayItLoud();

    function sayItLoud() {
      console.log(`${greeting}!!!}`)
    }

    let greeting = "Hello"
    ```
    This logs an error, because `let` is a scoped variable, JavaScript cannot access it until 
    it's been initialized. Therefore, even though it's declaration is hoisted and it's declared in 
    the global scope, its initialization must also occur before it's referenced in order to work.

**8. What does the following code log? Why?**
    ```javascript
    let problemSet;

    function complete(assignment) {
      assignment = "done";
    }

    complete(problemSet);
    console.log(`Status for Problem Set: ${problemSet}`);
    ```
    
    This code logs "Status for Problem Set: undefined". This is because the variable
    `problemSet` is declared globally, and then initialized locally within the `complete` 
    function. Therefore, the console log on line 118 has no access to the value assigned 
    on line 114.

**9. Why does this code throw an error?** 
    ```javascript
    const isSunny🌞 = true;

    if (isSunny🌞) {
      let advice = 'Wear your sunshades!';
    }

    console.log(advice);
    ```
   The variable `advice` is declared locally within the if statement, therefore when 
   trying to log its value on line 134, JavaScript logs an error because its existence 
   is unknown globally.

**10. So... why does this code work as intended?**
    ```javascript
    const isRainy🌧 = true;

    if (isRainy🌧) {
      var advice = 'Pack your umbrella.';
    }

    console.log(advice);
    ```
    
    This code works despite the variable `advice` being declared locally because
    it was declared using `var`, and `var` doesn't play by the same rules as `const`
    or `let`, its accessible globally and locally regardless of the scope of its 
    declaration location.
