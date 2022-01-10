# Problem Set 2.4 - Scope

**1. How do variables declared with `let`, `const`, and `var` differ? Be sure to touch on _scope_, _reassignment_, and _hoisting_ for each.**

<!---->
   Firstly, const cannot change its value. Thats the purpose of it so that variable will never be able to reassign to a new value. Unlike
   let and var which are able to be reassigned.
   
   Secondly, let and const hoist but you can't access them before the declaration is read by the console. Check out Questions 6 & 7
   in this .md file for a good example of this.
   
   Thirdly, var can be accessible anywhere in function but let and const can only be accessible inside the block where you first declare them.

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
    <!---->
    console.log(a) will ALWAYS log as outer. The function called on line 15 is refering to the variable 'a' thats initialized within itself
    so it'll always refer to that value which is inner.
    //ouput    outer --> inner --> outer

**3. What will the following code log? Why?**
    ```javascript
    function hello() {
      let a = 'hello';
    }

    hello();
    console.log(a);
    ```
    <!---->
    Code will result in an error, because a is not defined. this is because let has a block scope so the value of a cannot be 
    accessed because the "let" keyword is only accessible inside the block where they are declared, 
    just like "const" and unlike "var".

**4. What does the following code log? Why?**
    ```javascript
    console.log(a);

    var a = 1;
    ```
    <!---->
    The code logs as undefined. This is because var may have a normal scope so due to hoisting the console knows a 
    variable named a does exist but it is called upon because that variable is initialized, and cannot retrieve the value.
  
**5. What does the following code log? Why?**
    ```javascript
    console.log(a);

    let a = 1;
    ```
    <!---->
    The code results in an error saying that 'a' is not defined. This is signaificantly different from the previous example because
    let has it's own scope of block.  It cannot be called upon at all due to this. So when ran to the console, it does not run because
    the console thinks youre asking for something that does not exist.

**6. In the code snippet below, the function declaration comes _after_ the variable declaration in the code below. Why does it still work?**
    ```javascript
    let name = "Devonte";

    function sayItLoud() {
      console.log(`${name}!!!`)
    }

    sayItLoud();
    ```
    <!---->
    This still works because the variable name is declared and initialized outside of the function and has a global scope allowing it
    to be called upon at any point our script. Will work with any variable keyword such as var, let & const.
     
**7. Why does the following code throw an error? What is the key difference between it and the example above?**
    ```javascript
    sayItLoud();

    function sayItLoud() {
      console.log(`${greeting}!!!}`)
    }

    let greeting = "Hello"
    ```
    <!---->
    The key difference between this and the previous example is that the function is called upon at the evry start
    and the function is defined later on. It gives an error because that function is not hoisted to the top and read as is.
    It's actually let alone and read from top to bottom and since thats the case the console does not know what is within sayItLoud()
    becasue it has not been defined yet.

**8. What does the following code log? Why?**
    ```javascript
    let problemSet;

    function complete(assignment) {
      assignment = "done";
    }

    complete(problemSet);
    console.log(`Status for Problem Set: ${problemSet}`);
    ```
    
    <!---->
    Code logs the following line;
    
    // undefined
    // Status for Problem Set: done
    
    This is because on line 72 the function is called and refers to the global variable problemSet which is undefined within
    the scope of the function. complete() function scope lasts only from line 68-70. It does not reach outside to define problemSet. 
    On the next line, the console logs the same function with a string beforehand. Within that, it refers to the same problemSet variable
    but this time it works because the console.log is outside of the function and can grab the data from the global scope.

**9. Why does this code throw an error?** 
    ```javascript
    const isSunny🌞 = true;

    if (isSunny🌞) {
      let advice = 'Wear your sunshades!';
    }

    console.log(advice);
    ```
    <!---->
    advice was initialized within the scope of the conditional so it cannot be reached when called by the console. This is due to
    the "let" keyword which has it's own scope.

**10. So... why does this code work as intended?**
    ```javascript
    const isRainy🌧 = true;

    if (isRainy🌧) {
      var advice = 'Pack your umbrella.';
    }

    console.log(advice);
    ```
    <!---->
    The code runs as intended because of the keyword var used rather than the keyword let or const. var can be accessible anywhere but 
    let and const can only be accessible inside the block where they are declared.
    
    
