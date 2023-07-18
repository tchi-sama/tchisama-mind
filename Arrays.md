



1. `concat()` - Joins two or more arrays and returns a new array:

```javascript
const array1 = [1, 2, 3];
const array2 = [4, 5, 6];
const newArray = array1.concat(array2);

console.log(newArray); // Output: [1, 2, 3, 4, 5, 6]
```

2. `filter()` - Creates a new array with elements that pass a test:

```javascript
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = numbers.filter(num => num % 2 === 0);

console.log(evenNumbers); // Output: [2, 4]
```

3. `forEach()` - Executes a provided function once for each array element:

```javascript
const fruits = ['apple', 'banana', 'orange'];

fruits.forEach(fruit => {
  console.log(fruit);
});
// Output:
// apple
// banana
// orange
```

4. `map()` - Creates a new array with the results of calling a function on each element:

```javascript
const numbers = [1, 2, 3];
const doubledNumbers = numbers.map(num => num * 2);

console.log(doubledNumbers); // Output: [2, 4, 6]
```

5. `push()` - Adds one or more elements to the end of an array:

```javascript
const numbers = [1, 2, 3];
numbers.push(4, 5);

console.log(numbers); // Output: [1, 2, 3, 4, 5]
```

6. `pop()` - Removes the last element from an array and returns that element:

```javascript
const numbers = [1, 2, 3, 4, 5];
const removedElement = numbers.pop();

console.log(removedElement); // Output: 5
console.log(numbers); // Output: [1, 2, 3, 4]
```

7. `find()` - Returns the first element in an array that passes a test:

```javascript
const users = [
  { id: 1, name: 'John' },
  { id: 2, name: 'Jane' },
  { id: 3, name: 'Bob' }
];

const user = users.find(user => user.id === 2);

console.log(user); // Output: { id: 2, name: 'Jane' }
```

8. `reduce()` - Applies a function to reduce the array to a single value:

```javascript
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce((accumulator, currentValue) => accumulator + currentValue, 0);

console.log(sum); // Output: 15
```

9. `sort()` - Sorts the elements of an array in place:

```javascript
const fruits = ['banana', 'apple', 'orange', 'grape'];
fruits.sort();

console.log(fruits); // Output: ['apple', 'banana', 'grape', 'orange']
```

10. `slice()` - Extracts a section of an array and returns a new array:

```javascript
const numbers = [1, 2, 3, 4, 5];
const slicedNumbers = numbers.slice(1, 3);

console.log(slicedNumbers); // Output: [2, 3]
```

11. `indexOf()` - Returns the first index at which a specified element is found:

```javascript
const fruits = ['apple', 'banana', 'orange'];
const index = fruits.indexOf('banana');

console.log(index); // Output: 1
```

12. `includes()` - Checks if an array contains a specified element:

```javascript
const numbers = [1, 2, 3, 4, 5];
const includesThree = numbers.includes(3);

console.log(includesThree); // Output: true
```

13. `join()` - Joins all elements of an array into a string:

```javascript
const fruits = ['apple', 'banana', 'orange'];
const joinedString = fruits.join(', ');

console.log(joinedString); // Output: 'apple, banana, orange'
```

14. `reverse()` - Reverses the order of the elements in an array:

```javascript
const numbers = [1, 2, 3, 4, 5];
numbers.reverse();

console.log(numbers); // Output: [5, 4, 3, 2, 1]
```


15. `splice()` - Adds or removes elements from an array:

```javascript
const fruits = ['apple', 'banana', 'orange'];
fruits.splice(1, 1, 'grape', 'kiwi');

console.log(fruits); // Output: ['apple', 'grape', 'kiwi', 'orange']
```

16. `some()` - Checks if at least one element in the array passes a test:

```javascript
const numbers = [1, 2, 3, 4, 5];
const hasEvenNumber = numbers.some(num => num % 2 === 0);

console.log(hasEvenNumber); // Output: true
```

17. `every()` - Checks if all elements in the array pass a test:

```javascript
const numbers = [1, 2, 3, 4, 5];
const allPositive = numbers.every(num => num > 0);

console.log(allPositive); // Output: true
```

18. `findIndex()` - Returns the index of the first element that passes a test:

```javascript
const numbers = [10, 20, 30, 40, 50];
const index = numbers.findIndex(num => num > 30);

console.log(index); // Output: 3
```

19. `toLocaleString()` - Converts the elements of an array into a localized string:

```javascript
const numbers = [1000, 2000, 3000];
const localizedString = numbers.toLocaleString('en-US');

console.log(localizedString); // Output: '1,000, 2,000, 3,000'
```

21. `toString()` - Converts an array to a string:

```javascript
const fruits = ['apple', 'banana', 'orange'];
const stringRepresentation = fruits.toString();

console.log(stringRepresentation); // Output: 'apple,banana,orange'
```






Sure! Here's a table of commonly used array methods in JavaScript:

| Method                | Description                                               |
| --------------------- | --------------------------------------------------------- |
| `concat()`            | Joins two or more arrays and returns a new array           |
| `filter()`            | Creates a new array with elements that pass a test         |
| `find()`              | Returns the first element in an array that passes a test   |
| `findIndex()`         | Returns the index of the first element that passes a test  |
| `forEach()`           | Executes a provided function once for each array element   |
| `includes()`          | Checks if an array contains a specified element            |
| `indexOf()`           | Returns the first index at which a specified element is found |
| `join()`              | Joins all elements of an array into a string               |
| `map()`               | Creates a new array with the results of calling a function on each element |
| `pop()`               | Removes the last element from an array and returns that element |
| `push()`              | Adds one or more elements to the end of an array           |
| `reduce()`            | Applies a function to reduce the array to a single value   |
| `reverse()`           | Reverses the order of the elements in an array             |
| `shift()`             | Removes the first element from an array and returns that element |
| `slice()`             | Extracts a section of an array and returns a new array     |
| `some()`              | Checks if at least one element in the array passes a test  |
| `sort()`              | Sorts the elements of an array in place                    |
| `splice()`            | Adds/Removes elements from an array                        |
| `toLocaleString()`    | Converts the elements of an array into a string, localized |
| `toString()`          | Converts an array to a string                              |
| `unshift()`           | Adds one or more elements to the beginning of an array     |

These are just some of the methods available for working with arrays in JavaScript. Each method has its own specific purpose and can be used to manipulate, iterate, filter, and transform array elements. It's recommended to consult the official JavaScript documentation for more detailed information about each method, including their parameters and usage.

