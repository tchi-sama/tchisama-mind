

1. Closures:
   ```javascript
   function outerFunction() {
     let outerVariable = 'I am outer';
     
     function innerFunction() {
       console.log(outerVariable);
     }
     
     return innerFunction;
   }
   
   const inner = outerFunction();
   inner(); // Output: "I am outer"
   ```

2. Higher-Order Functions:
   ```javascript
   function multiplyBy(factor) {
     return function (number) {
       return number * factor;
     };
   }
   
   const multiplyByTwo = multiplyBy(2);
   console.log(multiplyByTwo(5)); // Output: 10
   ```

3. Arrow Functions:
   ```javascript
   const numbers = [1, 2, 3, 4, 5];
   const squaredNumbers = numbers.map((num) => num * num);
   console.log(squaredNumbers); // Output: [1, 4, 9, 16, 25]
   ```

4. Promises:
   ```javascript
   function fetchData() {
     return new Promise((resolve, reject) => {
       setTimeout(() => {
         const data = 'Fetched data';
         resolve(data);
       }, 2000);
     });
   }
   
   fetchData()
     .then((data) => console.log(data))
     .catch((error) => console.error(error));
   ```

5. Generators:
   ```javascript
   function* fibonacci() {
     let prev = 0, curr = 1;
     
     while (true) {
       yield curr;
       [prev, curr] = [curr, prev + curr];
     }
   }
   
   const fib = fibonacci();
   
   console.log(fib.next().value); // Output: 1
   console.log(fib.next().value); // Output: 1
   console.log(fib.next().value); // Output: 2
   console.log(fib.next().value); // Output: 3
   // ...
   ```

These examples demonstrate the practical use of advanced functions in JavaScript to achieve specific functionality.