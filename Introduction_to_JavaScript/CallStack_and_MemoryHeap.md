## Call Stack and Memory Heap
- The JavaScript engine performs many tasks for us, but two of its most significant jobs are reading and executing code. It needs a place to store and manage our data, and another place to keep track of the code being executed line by line. This is where the call stack and memory heap play crucial roles. 

- The call stack helps manage the order of function calls, while the memory heap is where the engine stores objects and data. Together, they ensure that our code runs smoothly and that data is stored and accessed correctly during program execution.

### Call Stack:
 
-   The **call stack** is a data structure used by the JavaScript engine to keep track of **function calls** and their **execution contexts** during the program's execution.
	> **Execution Context :** Each time a function is called, a new execution context is created, which includes information about the function call, local variables, parameters, and the scope chain.

-   When a JavaScript program starts running, the engine creates a **global execution context** (**GEC**) and places it at the bottom of the call stack.
	> **Global Execution Context :**  The global execution context is the outermost or top-level execution context in any JavaScript program. It is created when the program starts running and exists throughout the entire lifetime of the program.
All code that is not inside any function or block is considered to be part of the global execution context.

-   As functions are called, the engine adds new execution contexts (representing function calls) on top of the stack, forming a stack of execution contexts. Each execution context contains information about the function call, such as local variables, parameters, and the scope chain.

-   The topmost execution context on the call stack is the one currently being executed. The engine executes the code of this context, and once it's done, the context is removed from the stack, and the control goes back to the previous context.

**Example :**
``` js
function greet(name) {  // Finally this greet(name) function is pushed 
    console.log("Hello, " + name + "!"); 
}

function sayHello() {  // then this sayHello() function is pushed
    greet("Alice");    // which the calls greet(name) with 'name' as a parameter
}

sayHello(); // First this function is pushed into the stack after GEC
```
<br>
<p align="center">
<img src="https://i.ibb.co/wL56tks/Call-Stack.png" alt="Call-Stack" border="0">
</p>

**Stack Overflow  :**
Stack overflow is a situation in computer programming where the memory allocated for the stack **exceeds** its **maximum capacity**. This typically occurs when a large number of function calls are made without returning, specifically in cases involving **recursive calls** that lack a **base condition** or **stopping condition**. In such scenarios, the function continues to call itself infinitely, causing the stack to overflow.

**Simple Example :**
```js
function stackOverflow() { 
	stackOverflow(); // The function calls itself infinitely without a base condition. 
} 

stackOverflow();
```
### Memory Heap :

-   The memory heap is an area in the JavaScript engine where **dynamic memory allocation** occurs for objects and variables during the program's execution.

-   Objects, arrays, and other data structures are stored in the memory heap. When you create an object in JavaScript, memory is allocated in the heap to store its **properties** and **values**.

-   Memory allocation in the heap is dynamic, meaning that memory is allocated when an object is created and deallocated when it is no longer in use or references to it are lost (garbage collection).

-   Variables that are primitive types, such as **numbers** and **booleans**, are stored directly in the **call stack**, while complex objects and data structures are stored in the memory heap.


**Example :**
``` js
function createPerson(name, age) { // objects are stored in the Heap Memory
	const person = { 
		name: name, 
		age: age 
	};
	 return person; 
} 

let person1 = createPerson("John", 30);  // these function calls are stored in the stack
let person2 = createPerson("Alice", 25); // along with their local variables
```
<br>
<p align="center">
<img src="https://files.catbox.moe/q08wn0.svg" alt="Call-Stack-Heap" border="0">
</p>