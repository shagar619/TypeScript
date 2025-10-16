<!-- markdownlint-disable MD012 MD026 MD001 MD022 MD032 MD029 MD019 MD034 MD031 MD047 MD040 MD009 MD058 MD024  -->

# TYPESCRIPT

## 🔷 What is TypeScript?

TypeScript is a programming language developed and maintained by Microsoft. It is a strict syntactical superset of **JavaScript**, which means any valid JavaScript code is also valid TypeScript code. However, TypeScript adds optional static typing and other powerful features that help in building large-scale, robust applications.

At its core:

- TypeScript = JavaScript + Types

It’s compiled (or "transpiled") down to JavaScript using the TypeScript compiler (`tsc`), so it can run in any environment where JavaScript runs — such as browsers or Node.js.

#### Why Use TypeScript?

1. **Static Typing**: TypeScript allows you to define variable types, function return types, and more. This helps catch errors at compile time rather than runtime.

2. **Enhanced IDE Support**: With TypeScript, you get better autocompletion, navigation, and refactoring capabilities in your IDE.

3. **Improved Code Quality**: TypeScript encourages best practices and design patterns, leading to more maintainable and scalable code.

4. **Interoperability**: TypeScript is designed to work seamlessly with existing JavaScript code and libraries.

5. **Growing Popularity**: Many modern frameworks and libraries (like Angular) are built with TypeScript, making it a valuable skill in the job market.

Example: 
```typescript
interface User {
  name: string;
}

function greet(user: User): string {
  return "Hello " + user.name;
}
```

## 📘 Categories of TypeScript Data Types

TypeScript has several built-in data types that can be categorized as follows:

#### 💡 **Primitive Types**
- **`number`**: Represents both integer and floating-point numbers.
```typescript
let age: number = 30;
let price: number = 19.99;
```
- **`string`**: Represents text data.
```typescript
let name: string = "John Doe";
let greeting: string = `Hello, ${name}!`;
```
- **`boolean`**: Represents a logical value, either `true` or `false`.
```typescript
let isActive: boolean = true;
let isComplete: boolean = false;
```
- **`null`**: Represents an intentional absence of any value.
```typescript
let emptyValue: null = null;
```
- **`undefined`**: Represents a variable that has been declared but not assigned a value.
```typescript
let notAssigned: undefined;
```
- **`symbol`**: Represents a unique and immutable value, often used as object property keys.
```typescript
let uniqueId: symbol = Symbol("id");
```
- **`bigint`**: Represents integers with arbitrary precision, useful for very large numbers.
```typescript
let bigNumber: bigint = 1234567890123456789012345678901234567890n;
```


#### 💡 **Object Types**
- **`object`**: Represents a non-primitive type that can hold collections of values and more complex entities.
```typescript
let user: object = {
  name: "Alice",
  age: 25
};
```
- **`Array`**: Represents a collection of values of a specific type.
```typescript
let numbers: number[] = [1, 2, 3, 4, 5];
let strings: Array<string> = ["apple", "banana", "cherry"];
```
- **`Tuple`**: Represents an array with a fixed number of elements, where each element can have a different type.
```typescript
let tuple: [string, number] = ["Alice", 30];
```
- **`Function`**: Represents a callable object that can take parameters and return a value.
```typescript
function add(a: number, b: number): number {
  return a + b;
}
let multiply: (x: number, y: number) => number = (x, y) => x * y;
```


#### 💡 **Special Types**
- **`any`**: Represents any type of value, effectively opting out of type checking. Use sparingly as it defeats the purpose of TypeScript's type system.
```typescript
let anything: any = "Could be anything";
anything = 42; // Now it's a number
anything = true; // Now it's a boolean
```
- **`unknown`**: Similar to `any`, but safer because you must perform some type checking before using the value.
```typescript
let unknownValue: unknown = "Could be anything";
if (typeof unknownValue === "string") {
  console.log(unknownValue.toUpperCase()); // Safe to use as a string
}
```
- **`never`**: Represents a value that never occurs, often used for functions that throw errors or have infinite loops.
```typescript
function throwError(message: string): never {
  throw new Error(message);
}
function infiniteLoop(): never {
  while (true) {}
}
```
- **`void`**: Represents the absence of a value, typically used for functions that do not return anything.
```typescript
function logMessage(message: string): void {
  console.log(message);
}
```





#### 💡 **Union and Intersection Types**
- **Union Types**: Allows a variable to hold values of multiple types.
```typescript
let id: string | number = "123"; // Can be a string or a number
id = 456; // Now it's a number
```
- **Intersection Types**: Combines multiple types into one, requiring all properties from each type.
```typescript
interface Person {
  name: string;
}
interface Employee {
  id: number;
}
type Worker = Person & Employee; // Worker has both name and id properties
let worker: Worker = {
  name: "Bob",
  id: 1
};
```


#### 💡 **Enums**
- **Enums**: Define a set of named constants, which can be numeric or string-based.
```typescript
enum Direction {
  Up = "UP",
  Down = "DOWN",
  Left = "LEFT",
  Right = "RIGHT"
}
let move: Direction = Direction.Up; // move can be Direction.Up, Direction.Down, etc.
```


#### 💡 **Literal Types**
- **String Literal Types**: Represents specific string values.
```typescript
let direction: "left" | "right" = "left"; // Can only be "left" or "right"
```
- **Numeric Literal Types**: Represents specific numeric values.
```typescript
let status: 200 | 404 = 200; // Can only be 200 or 404
```
- **Boolean Literal Types**: Represents specific boolean values.
```typescript
let isEnabled: true | false = true; // Can only be true or false
```


#### 💡 **Literal Inference**
- **Literal Inference**: TypeScript can infer literal types based on the values assigned to variables.
```typescript
let literalString = "Hello"; // Type is inferred as "Hello"
let literalNumber = 42; // Type is inferred as 42
let literalBoolean = true; // Type is inferred as true
```

#### 💡 **Template Literal Types**
- **Template Literal Types**: Allow the creation of string types based on template literals, enabling dynamic string manipulation.
```typescript
type Greeting<T extends string> = `Hello, ${T}!`;
type UserGreeting = Greeting<"Alice">; // "Hello, Alice!"
```


#### 💡 **Keyof Operator**
- **Keyof Operator**: Creates a type that represents the keys of an object type.
```typescript
type User = {
  name: string;
  age: number;
};
type UserKeys = keyof User; // "name" | "age"
```


#### 💡Spread & Rest operators
- **Spread Operator**: Allows you to expand an iterable (like an array) into individual elements.
```typescript
let numbers = [1, 2, 3];
let moreNumbers = [...numbers, 4, 5]; // [1, 2, 3, 4, 5]
```
- **Rest Operator**: Allows you to collect multiple elements into an array.
```typescript
function sum(...args: number[]): number {
  return args.reduce((acc, curr) => acc + curr, 0);
}
let total = sum(1, 2, 3, 4); // total is 10
```

#### 💡 **Function Types**
- **Function Types**: Define the type of a function, including its parameters and return type.
```typescript
type AddFunction = (a: number, b: number) => number;
let add: AddFunction = (x, y) => x + y; // add is a function that takes two numbers and returns a number
```

#### 💡 **Readonly Types**
- **Readonly Types**: Create types where properties cannot be reassigned, ensuring immutability.
```typescript
type ReadonlyPoint = {
  readonly x: number;
  readonly y: number;
};
let point: ReadonlyPoint = { x: 10, y: 20 };
// point.x = 15; // Error: Cannot assign to 'x' because it is a read-only property
```

#### 💡 **Optional Properties**
- **Optional Properties**: Allow properties in an object type to be optional, meaning they may or may not be present.
```typescript
type User = {
  name: string;
  age?: number; // age is optional
};
let user1: User = { name: "Alice" }; // Valid, age is not required
let user2: User = { name: "Bob", age: 30 }; // Valid
```
#### 💡 **Nullish Coalescing**
- **Nullish Coalescing**: Provides a way to set default values for variables that may be `null` or `undefined`.
```typescript
let value: string | null = null;
let defaultValue = value ?? "Default Value"; // If value is null or undefined, use "Default Value"
console.log(defaultValue); // "Default Value"
```

#### 💡Destructuring
- **Destructuring**: Allows unpacking values from arrays or properties from objects into distinct variables.
```typescript
let user = { name: "Alice", age: 30 };
let { name, age } = user; // Destructuring the user object
console.log(name); // "Alice"
console.log(age); // 30
```


#### 💡 **Ternary Operator** & **Optional chaining**
- **Ternary Operator**: A shorthand for `if-else` statements, allowing conditional expressions.
```typescript
let isLoggedIn = true;
let message = isLoggedIn ? "Welcome back!" : "Please log in.";
console.log(message); // "Welcome back!"
```
- **Optional Chaining**: Allows safe access to deeply nested properties without having to check each level for `null` or `undefined`.
```typescript
let user = { profile: { name: "Alice" } };
let userName = user.profile?.name; // Safe access, returns "Alice"
let userAge = user.profile?.age; // Safe access, returns undefined if age is not present
console.log(userName); // "Alice"
console.log(userAge); // undefined
```

#### 💡**Never**, **unknown** &  **nullable** type
- **Never**: Represents a type that never occurs, often used for functions that throw errors or have infinite loops.
```typescript
function throwError(message: string): never {
  throw new Error(message);
}
function infiniteLoop(): never {
  while (true) {}
}
```
- **Unknown**: Represents a value that could be of any type, but requires type checking before use.
```typescript
let uncertainValue: unknown = "Could be anything";
if (typeof uncertainValue === "string") {
  console.log(uncertainValue.toUpperCase()); // Safe to use as a string
}
```
- **Nullable Type**: Represents a type that can be `null` or `undefined`, allowing for more flexible handling of optional values.
```typescript
let nullableValue: string | null = null; // Can be a string or null
let undefinedValue: string | undefined = undefined; // Can be a string or undefined
```


#### 💡 **Generics**
- **Generics**: Allow you to create reusable components that can work with any data type. They enable type-safe code while maintaining flexibility.
```typescript
function identity<T>(arg: T): T {
  return arg;
}
let str = identity<string>("Hello, TypeScript!"); // T is string
let num = identity<number>(42); // T is number
```


#### 💡 **Interfaces**
- **Interfaces**: Define the shape of an object, similar to type aliases but can be extended and implemented, making them more versatile for object-oriented programming.
```typescript
interface Animal {
  name: string;
  sound(): void;
}
interface Dog extends Animal {
  breed: string;
}
let dog: Dog = {
  name: "Buddy",
  breed: "Golden Retriever",
  sound: () => console.log("Woof!")
};
```


#### 💡 **Type Aliases**
- **Type Aliases**: Create a new name for a type, allowing for more readable and maintainable code.
```typescript
type Point = {
  x: number;
  y: number;
};
let point: Point = { x: 10, y: 20 };
```

#### 💡 **Indexed Access Types**
- **Indexed Access Types**: Allow you to access the type of a specific property in an object type.
```typescript
type User = {
  name: string;
  age: number;
};
type UserNameType = User["name"]; // string
type UserAgeType = User["age"]; // number
```


#### 💡 **Type Assertions**
- **Type Assertions**: Allow you to override TypeScript's inferred type for a variable, telling the compiler to treat it as a specific type.
```typescript
let someValue: any = "Hello, TypeScript!";
let strLength: number = (someValue as string).length; // Using 'as'
let strLength2: number = (<string>someValue).length; // Using angle-bracket syntax
```



#### 💡 **Type Guards**
- **Type Guards**: Functions or expressions that narrow down the type of a variable within a specific scope, allowing for safer type handling.
```typescript
function isString(value: any): value is string {
  return typeof value === "string";
}
function processValue(value: string | number) {
  if (isString(value)) {
    console.log("String value:", value.toUpperCase());
  } else {
    console.log("Number value:", value.toFixed(2));
  }
}
```

- **Type Guards using typeof & in**:
```typescript
function isNumber(value: any): value is number {
  return typeof value === "number";
}
function isArray(value: any): value is Array<any> {
  return Array.isArray(value);
}
function isObject(value: any): value is object {
  return typeof value === "object" && value !== null;
}
function processValue(value: string | number | any[]) {
  if (isNumber(value)) {
    console.log("Number value:", value.toFixed(2));
  } else if (isArray(value)) {
    console.log("Array value:", value.join(", "));
  } else if (isObject(value)) {
    console.log("Object value:", JSON.stringify(value));
  } else {
    console.log("String value:", value);
  }
}
```
- **Type Guards using instanceof**:
```typescript
class Animal {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
}
class Dog extends Animal {
  bark() {
    console.log("Woof!");
  }
}
function isDog(animal: Animal): animal is Dog {
  return animal instanceof Dog;
}
function makeSound(animal: Animal) {
  if (isDog(animal)) {
    animal.bark(); // Safe to call bark() because animal is a Dog
  } else {
    console.log(`${animal.name} makes a sound.`);
  }
}
makeSound(new Dog("Buddy")); // "Woof!"
makeSound(new Animal("Mittens")); // "Mittens makes a sound."
```


#### 💡 **Utility Types**
- **Utility Types**: Predefined types provided by TypeScript to facilitate common type transformations.
```typescript
type Partial<T> = {
  [P in keyof T]?: T[P];
};
type Required<T> = {
  [P in keyof T]-?: T[P];
};
type Pick<T, K extends keyof T> = {
  [P in K]: T[P];
};
type Omit<T, K extends keyof any> = {
  [P in Exclude<keyof T, K>]: T[P];
};
```


#### 💡 **Conditional Types**
- **Conditional Types**: Allow you to define types based on conditions, enabling powerful type transformations.
```typescript
type IsString<T> = T extends string ? "Yes" : "No";
type Result1 = IsString<string>; // "Yes"
type Result2 = IsString<number>; // "No"
```

#### 💡 **Modules**
- **Modules**: Allow you to split your code into separate files, each with its own scope. You can export and import types, functions, classes, and variables between modules.
```typescript
// In file math.ts
export function add(x: number, y: number): number {
  return x + y;
}
// In file main.ts
import { add } from './math';
let result = add(5, 3); // 8
```


#### 💡 **Mapped Types**
- **Mapped Types**: Create new types by transforming existing ones, often used for creating variations of existing types.
```typescript
type Readonly<T> = {
  readonly [P in keyof T]: T[P];
};
type User = {
  name: string;
  age: number;
};
type ReadonlyUser = Readonly<User>; // All properties of User are now readonly
let readonlyUser: ReadonlyUser = {
  name: "Alice",
  age: 30
};
// readonlyUser.name = "Bob"; // Error: Cannot assign to 'name' because it is a read-only property
```


#### 💡 **Decorators**
- **Decorators**: Special types of declarations that can be attached to a class, method, accessor, property, or parameter. They provide a way to modify the behavior of the target.
```typescript
function Log(target: any, propertyKey: string, descriptor: PropertyDescriptor) {
  const originalMethod = descriptor.value;
  descriptor.value = function (...args: any[]) {
    console.log(`Calling ${propertyKey} with arguments:`, args);
    return originalMethod.apply(this, args);
  };
}
class Example {
  @Log
  greet(name: string) {
    return `Hello, ${name}!`;
  }
}
let example = new Example();
console.log(example.greet("Alice")); // Logs: Calling greet with arguments: [ 'Alice' ]
```


### 💡 **Type Compatibility**
- **Type Compatibility**: TypeScript uses structural typing, meaning that types are compatible based on their structure rather than their explicit declarations. This allows for flexible type relationships.
```typescript
interface Point {
  x: number;
  y: number;
}
function logPoint(point: Point) {
  console.log(`Point: (${point.x}, ${point.y})`);
}
let point = { x: 10, y: 20, z: 30 }; // Extra property 'z' is allowed
logPoint(point); // Works because point has the required structure
```


### 💡. **Type Inference**
- **Type Inference**: TypeScript can automatically infer types based on the values assigned to variables, reducing the need for explicit type annotations.
```typescript
let inferredString = "Hello, TypeScript!"; // Type is inferred as string
let inferredNumber = 42; // Type is inferred as number
let inferredBoolean = true; // Type is inferred as boolean
```



#### 💡 **Namespaces**
- **Namespaces**: Provide a way to group related code together, helping to avoid naming conflicts and organize code in larger applications.
```typescript
namespace MathUtils {
  export function add(x: number, y: number): number {
    return x + y;
  }
  export function subtract(x: number, y: number): number {
    return x - y;
  }
}
let sum = MathUtils.add(5, 3); // 8
let difference = MathUtils.subtract(5, 3); // 2
```


### 🧱 Constraints
- **Constraints**: Allow you to restrict the types that can be used with generics, ensuring type safety while maintaining flexibility.
```typescript
function identity<T extends string | number>(arg: T): T {
  return arg;
}
let str = identity("Hello"); // Type is inferred as string
let num = identity(42); // Type is inferred as number
```

### 🧱 Class & Object
- **Class**: A blueprint for creating objects, encapsulating data and behavior. Classes can have properties, methods, and constructors.
```typescript
class Person {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  greet(): string {
    return `Hello, my name is ${this.name} and I am ${this.age} years old.`;
  }
}
let person = new Person("Alice", 30);
console.log(person.greet()); // "Hello, my name is Alice and I am 30 years old."
```
- **Object**: An instance of a class, representing a specific entity with its own state and behavior.
```typescript
let car = {
  make: "Toyota",
  model: "Camry",
  year: 2020,
  start() {
    console.log("Car started");
  }
};
car.start(); // "Car started"
```

### 🧱 Inheritance
- **Inheritance**: A mechanism that allows a class to inherit properties and methods from another class, promoting code reuse and establishing a parent-child relationship.
```typescript
class Animal {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  speak(): string {
    return `${this.name} makes a sound.`;
  }
}
class Dog extends Animal {
  speak(): string {
    return `${this.name} barks.`;
  }
}
let dog = new Dog("Buddy");
console.log(dog.speak()); // "Buddy barks."
```

### 🧱 Asynchronous Programming in Typescript
- **Asynchronous Programming**: TypeScript supports asynchronous programming using `async` and `await`, allowing you to write cleaner and more readable asynchronous code.
```typescript
async function fetchData(url: string): Promise<string> {
  const response = await fetch(url);
  if (!response.ok) {
    throw new Error("Network response was not ok");
  }
  return await response.text();
}
fetchData("https://api.example.com/data")
  .then(data => console.log(data))
  .catch(error => console.error("Error fetching data:", error));
```

### 🧱 Access Modifiers
- **Access Modifiers**: TypeScript supports three access modifiers: `public`, `private`, and `protected`. These determine the scope of class members (properties and methods).
```typescript
class Person {
  public name: string;
  private age: number;
  protected gender: string;
  constructor(name: string, age: number, gender: string) {
    this.name = name;
    this.age = age;
    this.gender = gender;
  }
  public getName(): string {
    return this.name;
  }
  private getAge(): number {
    return this.age;
  }
  protected getGender(): string {
    return this.gender;
  }
}
let person = new Person("John", 30, "Male");
console.log(person.getName()); // "John"
console.log(person.getAge()); // Error: Property 'getAge' is private and only accessible within class 'Person'.
console.log(person.getGender()); // Error: Property 'getGender' is protected and only accessible within class 'Person' and its subclasses.
```

### 🧱 getter & setter
- **Getters and Setters**: TypeScript allows you to define getter and setter methods for class properties, providing controlled access to the properties.
```typescript
class Rectangle {
  private _width: number;
  private _height: number;

  constructor(width: number, height: number) {
    this._width = width;
    this._height = height;
  }

  get width(): number {
    return this._width;
  }

  set width(value: number) {
    if (value < 0) {
      throw new Error("Width cannot be negative");
    }
    this._width = value;
  }

  get height(): number {
    return this._height;
  }

  set height(value: number) {
    if (value < 0) {
      throw new Error("Height cannot be negative");
    }
    this._height = value;
  }

  area(): number {
    return this._width * this._height;
  }
}
let rect = new Rectangle(10, 5);
console.log(rect.area()); // 50
rect.width = 15; // Using setter
console.log(rect.area()); // 75
rect.height = -5; // Throws error: Height cannot be negative
```

### 🧱 Statics in OOP
- **Statics**: Static members (properties and methods) belong to the class itself rather than to instances of the class. They can be accessed without creating an instance of the class.
```typescript
class MathUtils {
  static PI: number = 3.14159;

  static areaOfCircle(radius: number): number {
    return this.PI * radius * radius;
  }
}
console.log(MathUtils.PI); // 3.14159
console.log(MathUtils.areaOfCircle(5)); // 78.53975
```


### ⚙️ TypeScript Configuration

#### 🔹 Create `tsconfig.json` file
You can create a `tsconfig.json` file in your project root to configure TypeScript compiler options.
```bash
tsc --init
```

#### ✅ Example tsconfig.json for a Modern Project
```json
{
  "compilerOptions": {
    "target": "es2020",
    "module": "commonjs",
    "strict": true,
    "outDir": "./dist",
    "rootDir": "./src",
    "esModuleInterop": true,
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "forceConsistentCasingInFileNames": true,
    "skipLibCheck": true
  },
  "include": ["src"],
  "exclude": ["node_modules", "dist"]
}
```

#### 🔹 Target & Module
- **`target`**: Specifies the ECMAScript target version (e.g., `es5`, `es6`, `esnext`).
- **`module`**: Specifies the module system to use (e.g., `commonjs`, `es6`, `amd`, `umd`).


#### 🔹 Directories
- **`outDir`**: Specifies the output directory for compiled JavaScript files.
- **`rootDir`**: Specifies the root directory of input files.
Example:
```json
{
  "compilerOptions": {
    "outDir": "./dist",
    "rootDir": "./src"
  }
}
```




#### 📂 TypeScript Compiler
```bash
tsc
```
- **`tsc`**: The TypeScript compiler command to compile TypeScript files into JavaScript.
- **`tsc --watch`**: Compiles TypeScript files and watches for changes, automatically recompiling when files are modified.
```bash
tsc --watch
```
#### 📂 TypeScript Linting
```bash
tslint
```
- **`tslint`**: A linter for TypeScript code to enforce coding standards and catch potential errors.
- **`tslint --fix`**: Automatically fixes linting issues in TypeScript files.
```bash
tslint --fix
```
#### 📂 TypeScript Formatting
```bash
prettier --write "**/*.ts"
```
- **`prettier`**: A code formatter that formats TypeScript files according to a consistent style.
- **`prettier --write`**: Formats TypeScript files in the specified directory.
```bash
prettier --write "**/*.ts"
```

#### ⚙️ Debug a TypeScript file
To debug a TypeScript file, you can use the built-in debugging capabilities of your IDE (like Visual Studio Code) or use Node.js with the `--inspect` flag.
```bash
node --inspect-brk dist/index.js
```
- **`--inspect-brk`**: Starts the Node.js process in debug mode and breaks before the first line of code, allowing you to set breakpoints and inspect variables.
- **`dist/index.js`**: The compiled JavaScript file to debug.


#### The purpose of noImplicitAny

The `noImplicitAny` option in TypeScript is a compiler setting that helps catch potential errors related to the use of the `any` type. When this option is enabled, TypeScript will raise an error whenever it infers a variable or parameter to be of type `any` without an explicit type annotation.

```typescript
function greet(name) { // Error: Parameter 'name' implicitly has an 'any' type.
  return "Hello, " + name;
}
```

#### Contextual typing

Contextual typing is a feature in TypeScript that allows the type of a variable to be inferred based on its usage context. This means that TypeScript can determine the type of a variable by looking at how it is used in the code, rather than relying solely on explicit type annotations.

```typescript
let numbers = [1, 2, 3];
numbers.forEach(num => {
  console.log(num.toFixed(2)); // 'num' is contextually typed as 'number'
});
```
In this example, the type of `num` is inferred to be `number` based on its usage within the `forEach` method, which expects a callback function that takes a `number` as an argument.

#### TypeScript syntax to create function overloads
Function overloads in TypeScript allow you to define multiple function signatures for a single function implementation. This is useful when you want a function to behave differently based on the types or number of arguments passed to it.