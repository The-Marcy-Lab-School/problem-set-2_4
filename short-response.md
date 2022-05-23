# Problem Set 2.4 - Scope

1. How do variables declared with `let`, `const`, and `var` differ? Be sure to touch on _scope_, _reassignment_, and _hoisting_ for each.

2. What will the following code log? Why?
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

3. What will the following code log? Why?
    ```javascript
    function hello() {
      let a = 'hello';
    }

    hello();
    console.log(a);
    ```

4. What does the following code log? Why?
    ```javascript
    console.log(a);

    var a = 1;
    ```
  
5. What does the following code log? Why?
    ```javascript
    console.log(a);

    let a = 1;
    ```

6. In the code snippet below, the function declaration comes _after_ the variable declaration in the code below. Why does it still work?
    ```javascript
    let name = "Devonte";

    function sayItLoud() {
      console.log(`${name}!!!`)
    }

    sayItLoud();
    ```
7. Why does the following code throw an error? What is the key difference between it and the example above?
    ```javascript
    sayItLoud();

    function sayItLoud() {
      console.log(`${greeting}!!!`)
    }

    let greeting = "Hello"
    ```

8. What does the following code log? Why?
    ```javascript
    let problemSet;

    function complete(assignment) {
      assignment = "done";
    }

    complete(problemSet);
    console.log(`Status for Problem Set: ${problemSet}`);
    ```

9. Why does this code throw an error? 
    ```javascript
    const isSunny = true;

    if (isSunny) {
      let advice = 'Wear your sunshades!';
    }

    console.log(advice);
    ```


10. So... why does this code work as intended?
    ```javascript
    const isRainy = true;

    if (isRainy) {
      var advice = 'Pack your umbrella.';
    }

    console.log(advice);
    ```
