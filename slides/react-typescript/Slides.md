---
marp: true
html: true
theme: default
paginate: true
style: |
  .columns {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 1rem;
  }
  .vert {
    vertical-align: middle
  }
  .fa-twitter { color: aqua; }
  .fa-linkedin { color: blue; }
  .fa-window-maximize { color: skyblue; }
  .fa-th-large {
    color: blue;
  }
  .qrcode {
    width: 150px;
    height: 150px;
  }

  @import 'https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.2.1/css/all.min.css'

---

## Naim Gkamperlo
### Associate Director of Engineering<br>**GWI**</br>

<i class="fa-brands fa-twitter"></i> Twitter: @ngkamperlo
<i class="fa-brands fa-linkedin"></i> LinkedIn: [https://linkedin.com/in/ngkamperlo](https://linkedin.com/in/ngkamperlo)
<i class="fa fa-window-maximize"></i> Blog: [https://medium.com/ngkamperlo](https://medium.com/ngkamperlo)
<i class="fa-brands fa-github"></i> GitHub: [https://github.com/ngkamperlo](https://github.com/ngkamperlo)




---
# Typescript and React foundations

--- 

# Introduction to Typescript 

---

Here are the requested slides on TypeScript foundations, written in Marp markdown. Please note that Marp doesn't directly support including interactive code examples. If you're using a platform that supports embedded code snippets, you might want to replace the code text with actual embeds:

```markdown

---
theme: default
---

# TypeScript Foundations

---

# What is TypeScript?

TypeScript is an open-source language which builds on JavaScript by adding static type definitions.

---

# Why TypeScript?

- Predictability
- Readability
- Tooling and community
- Enhanced development experience
- Improved maintainability and scalability

---

# TypeScript vs. JavaScript

JavaScript is dynamically typed, meaning the type is checked during execution. TypeScript is statically typed, meaning type checking is done during compile time.

---

# Setting up TypeScript

1. Install Node.js and npm
2. Install TypeScript globally: `npm install -g typescript`
3. Compile .ts to .js: `tsc myfile.ts`

---

# TypeScript Configuration

You can control the TypeScript compiler options using a special file called `tsconfig.json`.

---

# Basic Types in TypeScript

1. Boolean
2. Number
3. String
4. Array
5. Tuple
6. Enum
7. Any
8. Void
9. Null and Undefined
10. Never

--- 
# Boolean

The most basic datatype is the simple true/false value, which JavaScript and TypeScript call a `boolean`.

```typescript
let isDone: boolean = false;
```
--- 
# Number
As in JavaScript, all numbers in TypeScript are floating point values.

```typescript

let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
```
--- 
# String
Another fundamental part of creating programs in JavaScript for webpages and servers alike is working with textual data.

```typescript

let color: string = "blue";
color = 'red';
```

--- 
# Array
TypeScript, like JavaScript, allows you to work with arrays of values.

```typescript

let list: number[] = [1, 2, 3];
let list: Array<number> = [1, 2, 3]; // another way
```

--- 
# Tuple
Tuple types allow you to express an array with a fixed number of elements whose types are known.

```typescript

let x: [string, number];
x = ["hello", 10]; // OK
x = [10, "hello"]; // Error
```

--- 
# Enum
A helpful addition to the standard set of datatypes from JavaScript is the enum.

```typescript

enum Color {
    Red,
    Green,
    Blue
}
let c: Color = Color.Green;
```

--- 
# Any
We may need to describe the type of variables that we do not know when we are writing an application.

```typescript

let notSure: any = 4;
notSure = "maybe a string instead";
notSure = false; // okay, definitely a boolean
```

--- 
# Void
void is a little like the opposite of any: the absence of having any type at all.

```typescript

function warnUser(): void {
    console.log("This is my warning message");
}
```

--- 
# Null and Undefined
Much like JavaScript, TypeScript has null and undefined as possible values for any type.

```typescript

let u: undefined = undefined;
let n: null = null;
```

--- 
# Never
The never type represents the type of values that never occur.

```typescript

function error(message: string): never {
    throw new Error(message);
}
```

--- 
# Interfaces
One of TypeScript’s core principles is that type checking focuses on the shape that values have.

```typescript

interface LabelledValue {
    label: string;
}
```

--- 
# Function Types
Interfaces can also describe function types.

```typescript

interface SearchFunc {
    (source: string, subString: string): boolean;
}
```

--- 
# Classes in TypeScript
TypeScript includes full support for classes, as in object-oriented programming.

```typescript

class Greeter {
    greeting: string;
    constructor(message: string) {
        this.greeting = message;
    }
    greet() {
        return "Hello, " + this.greeting;
    }
}
```

--- 
# Public, private, and protected modifiers
Each member is public by default. You can also mark members as private or protected.


--- 
# Generics
Generics allow you to define the type of a variable at a future point.

```typescript

function identity<T>(arg: T): T {
    return arg;
}
```

--- 
# Union Types
Union types are a powerful way to express a variable with multiple types.

```typescript

function padLeft(value: string, padding: string | number) {
    //...
}
```

--- 
# Type Guards and Differentiating Types
A common idiom in JavaScript to differentiate between two possible values.

```typescript

function isFish(pet: Fish | Bird): pet is Fish {
    return (pet as Fish).swim !== undefined;
}
```

--- 
# Type Aliases
Type aliases create a new name for a type.

```typescript

type StringOrNumber = string | number;

```
--- 
# Advanced Typescript
---
# Interfaces

_Interfaces are powerful ways to define contracts within your code_

```typescript
interface Animal {
  name: string;
  makeSound(): void;
}
```
---

# Defining a Contract
```typescript

class Dog implements Animal {
  name = "Dog";
  
  makeSound() {
    console.log('Bark');
  }
}
```
---

# Optional Properties in Interfaces
Interfaces can have optional properties, marked with a '?‘.

```typescript

interface Employee {
  name: string;
  age?: number;
}
```
---

# Readonly Properties
Properties can be marked as readonly for variables that should not be changed

```typescript

interface Config {
  readonly path: string;
  readonly timeout: number;
}
```
---

# Indexable Types
You can also define indexable types

```typescript

interface StringArray {
  [index: number]: string;
}
```
---

# Extending Interfaces
Interfaces can be extended

```typescript

interface Bird extends Animal {
  fly(): void;
}
```
---

# Generics
Generics provide a way to make components work with any data type

```typescript

function identity<T>(arg: T): T {
  return arg;
}
```
---

# Working with Generic Variables
```typescript

function loggingIdentity<T>(arg: T[]): T[] {
  console.log(arg.length);
  return arg;
}
```
---

# Generic Types
```typescript

let myIdentity: <T>(arg: T) => T = identity;
```
---

# Generic Classes
```typescript

class GenericNumber<T> {
  zeroValue: T;
  add: (x: T, y: T) => T;
}
```

---

# Decorators
Decorators provide a way to add both annotations and a meta-programming syntax for class declarations and members

```typescript

function sealed(target) {
  Object.seal(target);
  Object.seal(target.prototype);
}
```
---

# Decorator Factories
```typescript

function color(value: string) {
  return function (target) {
    // logic
  }
}
```

---

# Modules
Modules are executed within their own scope, not in the global scope

```typescript

import { ZipCodeValidator } from "./ZipCodeValidator";
```
---

# Export
Exporting a declaration

```typescript

export interface StringValidator {
  isAcceptable(s: string): boolean;
}
```
---

# Default exports
Each module can optionally export a default export

```typescript

export default class ZipCodeValidator {
  // Class logic
}
```
---

# Merging Namespaces with Classes, Functions, and Enums
```typescript

class Album {
  label: Album.AlbumLabel = new Album.AlbumLabel();
}
namespace Album {
  export class AlbumLabel { }
}
```
---

# Advanced Types
Partial Types

```typescript

interface Todo {
  title: string;
  description: string;
}

function updateTodo(todo: Todo, fieldsToUpdate: Partial<Todo>) {
  // Logic
}
```
---

# Conditional Types
```typescript

type TypeName<T> = 
  T extends string ? "string" :
  T extends number ? "number" :
  T extends boolean ? "boolean" :
  T extends undefined ? "undefined" :
  "object";
```
---

# Using Third Party Libraries
Type declarations

```typescript

import * as Lodash from "lodash";
```
---

# Module Augmentation
You can add your own functions to existing third party modules

```typescript

declare module "lodash" {
  interface LoDashStatic {
    myFunction(param: number): void;
  }
}
```

---
## Introduction to **React**
- JavaScript library for building user interfaces
- Developed by Facebook
- Component-based architecture
---
## Why use React?
- Declarative: Make your code more predictable and easier to debug
- Component-Based: Encapsulated components that manage their own state
- Learn Once, Write Anywhere: You can develop new features without rewriting existing code
---
## React + TypeScript
- Benefits of combining React with TypeScript
- Strong typing and reduced runtime bugs
- Improved developer experience
---
## Using React foundations to build practical web applications
- Understanding the basic building blocks
- Setting up a new React project with TypeScript
- Exploring the file structure
---
## Create your first React component
- Understanding JSX
- How to define and use components
- Props and state
---
## Component Lifecycle
- Understanding the component lifecycle
- Mounting, Updating, Unmounting phases
---
## React Hooks
- Introduction to Hooks
- useState and useEffect
- Custom Hooks
---
## Designing class components and stateful function components
- Class components vs function components
- Understanding 'state' in class and function components
- Handling events
---
## Using TypeScript with Class Components
- Defining Props and State types
- Using TypeScript specific features in class components
---
## Using TypeScript with Function Components
- Defining Props types
- Using TypeScript specific features in function components
---
## Designing one-way flow data and behavior
- Understanding 'props' and state
- Understanding 'lift state up'
- Introduction to Context API
---
## Data flow in React
- Parent to child component data flow
- Child to parent data flow
- Sibling components data flow
---
## React Context API
- Using Context API for global state management
- Creating a context
- Providing and consuming a context
---
## Using TypeScript with Context API
- Defining Context type
- Using TypeScript specific features with Context API
---
# Intro to Modern JavaScript Features Used with React

---

# JavaScript ES6 & Beyond

- New Variables: `let` & `const`
- Arrow Functions
- Default Parameters
- Rest & Spread Operator
- Destructuring Assignment
- Modules

---

# New Variables: `let` & `const`

```
let name = 'John';
name = 'Jane'; // Allowed

const age = 30;
age = 31; // Error: Assignment to constant variable.
```
--- 

# Arrow Functions
```
const add = (a, b) => a + b;

add(3, 5); // Returns 8
```

--- 
# Default Parameters

```typescript
function introduce(name = "John Doe") {
  return `Hello, my name is ${name}`;
}

introduce(); // Returns "Hello, my name is John Doe"
```
--- 
# Rest & Spread Operator
```typescript
// Spread
const numbers = [1, 2, 3];
const moreNumbers = [...numbers, 4, 5];

// Rest
function sum(...args) {
  return args.reduce((total, current) => total + current, 0);
}

sum(1, 2, 3); // Returns 6
```

--- 

# Destructuring Assignment
```typescript
const person = {
  name: 'John',
  age: 30
};

const { name, age } = person;
```

--- 
# Modules
```typescript
// math.js
export const add = (a, b) => a + b;

// main.js
import { add } from './math';

console.log(add(1, 2)); // Outputs 3
```
--- 

# Analysis of Core React Tasks
React Overview
- JSX
- Components
- Props
- State & Lifecycle
- Hooks

--- 

# JSX

JavaScript XML (JSX) - Syntax extension for JavaScript
Looks like HTML, but it's JavaScript
JSX elements are treated as JavaScript expressions
```typescript
const element = <h1>Hello, world!</h1>;
```
--- 

# Components
Components let you split the UI into independent, reusable pieces
Two types of components: Functional and Class components
```typescript
// Functional component
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

// Class component
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

--- 

# Props
Properties (props) - way to pass data from parent to child components
```typescript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

const element = <Welcome name="John" />;
```

--- 

# State & Lifecycle

State - Similar to props but private and fully controlled by the component
Lifecycle methods - special methods in the component class to run code at particular times in the process
```typescript
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  componentDidMount() {
    this.timerID = setInterval(
      () => this.tick(),
      1000
    );
  }

  tick() {
    this.setState({
      date: new Date()
    });
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
```

--- 

# Hooks
Hooks let you use state and other React features without writing a class
```typescript
import React, { useState } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

--- 
# How to Create a Rapid Feedback Development Environment
## Rapid Feedback Development
- Use Create React App (CRA)
- Setup Hot Module Replacement (HMR)
- Setup Fast Refresh
- Use TypeScript for Type Checking
- Automate Testing
--- 
# Use Create React App (CRA)
Create React App - an officially supported way to start a new React single-page application
No build configuration
```bash
npx create-react-app my-app
```
--- 
# Setup Hot Module Replacement (HMR)
HMR exchanges, adds, or removes modules while an application is running, without a full reload
Speeds up the development process
```typescript
if (module.hot) {
  module.hot.accept();
}
```
--- 

# Use TypeScript for Type Checking
TypeScript is a typed superset of JavaScript
Helps catch errors early
Provides autocompletion and type checking
```tsx
type Props = {
  name: string;
};

function Greeting({ name }: Props) {
  return <h1>Hello, {name}</h1>;
}
```

--- 
# Automate Testing
Jest and React Testing Library
Write tests for all components to ensure they work as expected
```typescript
import { render, screen } from '@testing-library/react';
import App from './App';

test('renders learn react link', () => {
  render(<App />);
  const linkElement = screen.getByText(/learn react/i);
  expect(linkElement).toBeInTheDocument();
});
```


---

# Thank You! 🤘
# Naim Gkamperlo

<i class="fa-brands fa-twitter"></i> Twitter: @ngkamperlo
<i class="fa-brands fa-linkedin"></i> LinkedIn: [https://linkedin.com/in/ngkamperlo](https://linkedin.com/in/ngkamperlo)
<i class="fa fa-window-maximize"></i> Blog: [https://medium.com/ngkamperlo](https://medium.com/ngkamperlo)
<i class="fa-brands fa-github"></i> GitHub: [https://github.com/ngkamperlo](https://github.com/ngkamperlo)

