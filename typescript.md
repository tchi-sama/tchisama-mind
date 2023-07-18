

[[typescript-react]]


Certainly! TypeScript is a statically typed superset of JavaScript that adds optional static typing to the language. It allows you to write JavaScript code with additional type information, which helps catch errors during development and provides better tooling support. Here's a brief introduction to TypeScript:

1. **Installation**: To get started with TypeScript, you need to install it globally on your system using npm (Node Package Manager). Open a terminal and run the following command:
   ```bash
   npm install -g typescript
   ```

2. **Creating a TypeScript file**: Create a new file with a `.ts` extension, for example, `app.ts`. This will be your TypeScript file where you'll write your code.

3. **Basic Types**: TypeScript provides various built-in types to define variables. Here are a few commonly used ones:
   - `number`: Represents numeric values like 1, 2, 3, etc.
   - `string`: Represents textual values like "hello", "world", etc.
   - `boolean`: Represents true or false.
   - `array`: Represents an ordered list of values of a particular type.
   - `any`: Represents any type (similar to JavaScript's dynamic typing).
   - `void`: Represents the absence of any type.
   - `object`: Represents any JavaScript object (non-primitive types).

4. **Variable Declarations**: In TypeScript, you can explicitly declare variables with their types using the colon (`:`) syntax. For example:
   ```typescript
   let age: number = 25;
   let name: string = "John";
   let isStudent: boolean = true;
   ```

5. **Functions**: Functions in TypeScript can also have type annotations for parameters and return types. Here's an example:
   ```typescript
   function addNumbers(a: number, b: number): number {
     return a + b;
   }
   ```

6. **Interfaces**: Interfaces in TypeScript define the structure of an object. They specify the names and types of properties an object should have. Here's an example:
   ```typescript
   interface Person {
     name: string;
     age: number;
   }

   let person: Person = {
     name: "John",
     age: 25
   };
   ```

7. **Classes**: TypeScript supports class-based object-oriented programming. You can define classes with properties and methods, and even use access modifiers like `public`, `private`, and `protected`. Here's a basic class example:
   ```typescript
   class Animal {
     name: string;
     constructor(name: string) {
       this.name = name;
     }
     move(distance: number) {
       console.log(`${this.name} moved ${distance} meters.`);
     }
   }

   let cat = new Animal("Tom");
   cat.move(10);
   ```

8. **Compiling TypeScript**: After writing TypeScript code, you need to compile it to JavaScript before running it in a browser or Node.js. Use the `tsc` command followed by the name of your TypeScript file to compile it. For example:
   ```
   tsc app.ts
   ```

   This will generate a corresponding JavaScript file (`app.js`) that you can execute using Node.js or include in your HTML file.

These are just the basics of TypeScript. There's a lot more to explore, including advanced type features, modules, generics, and more. I recommend referring to the official TypeScript documentation (https://www.typescriptlang.org/docs/) for more detailed information and examples.