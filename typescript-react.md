To use TypeScript with React, you can follow these steps:

1. **Create a new React project**: Set up a new React project using Create React App ([[CRA]]), which includes TypeScript support. Open your terminal and run the following command:
   ```bash
   npx create-react-app my-app --template typescript
   ```

   This will create a new React project with TypeScript configuration.

2. **File extensions**: By default, Create React App sets up TypeScript to use the `.tsx` file extension for React components and `.ts` for regular TypeScript files. You can start writing your React components in `.tsx` files.

3. **React Component with TypeScript**: Here's an example of a React component written in TypeScript:
   ```tsx
   import React from 'react';

   interface GreetingProps {
     name: string;
   }

   const Greeting: React.FC<GreetingProps> = ({ name }) => {
     return <div>Hello, {name}!</div>;
   };

   export default Greeting;
   ```

   In this example, we define a functional component `Greeting` that receives a prop `name` of type `string`. We use the `React.FC` type to define the component's type, specifying the prop type as `GreetingProps`.

4. **Using Props**: When using a component, you can pass props and provide the correct types. For example:
   ```tsx
   import React from 'react';
   import Greeting from './Greeting';

   const App: React.FC = () => {
     return <Greeting name="John" />;
   };

   export default App;
   ```

   In this case, we import the `Greeting` component and pass the `name` prop with the value `"John"`.

5. **Type Checking**: TypeScript will perform type checking during development and provide helpful error messages. It will ensure that you provide the correct props and handle them properly within your components.

6. **Running the Application**: To run your React application, use the following command in the project directory:
   ```
   npm start
   ```

   This will start the development server, and you can view your React app in the browser.

By using TypeScript with React, you can take advantage of static type checking, which can help catch errors and provide better development tooling support. It also enhances code maintainability and helps with documentation and collaboration.