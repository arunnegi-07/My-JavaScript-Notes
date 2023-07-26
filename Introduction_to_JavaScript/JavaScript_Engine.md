## JavaScript Engine
- To enable **JavaScript** code to run on browsers, an intermediary component called the **JavaScript Engine** is used. A **JavaScript Engine** is a computer program to which you provide JavaScript code, and it processes the code to instruct the computer on how to execute it. <br>

- The JavaScript engine is a part of the web browser responsible for processing and executing JavaScript code. It takes the **human-readable** JavaScript code and translates it into **machine-understandable** instructions, typically in the form of **bytecode** or **machine code**. This allows the browser to execute the JavaScript instructions and interact with the **Document Object Model** (DOM) to dynamically update the content and behavior of web pages.

- Every web browser has its own **JavaScript Engine**, but they all follow the same set of rules called **'ECMAScript'** standards. This means that while the inner workings of the engines may be different, they generally work in a similar way. 
 
- This makes sure that JavaScript code written according to the **'ECMAScript'** rules will work well on all browsers, due to which the general structure of a JavaScript Engine is nearly same and shown below :
<br>

<p align="center">
<img src="https://files.catbox.moe/r9k3ee.svg" alt="JS-Engine-1" border="0">
</p>

<br>

> Some of the famous **JavaScript Engines** are :

|    Browser      | Name of JavaScript Engine |
|-----------------|---------------------------|
| Google Chrome   |            V8             |
| Edge            |          Chakra           |
| Mozilla Firefox |       Spider Monkey       |
| Safari          |   JavaScript Core Webkit  |

**Let's see in brief step-by-step process of a JavaScript Engine, from taking a JS file as input until producing machine code:**
1.  **Lexical Analysis (Tokenization)**:
    
    -   The JavaScript engine takes the JS file as input.
    -   The first step is to perform lexical analysis, also known as **tokenization**. The code is broken down into individual tokens like keywords, identifiers, operators, and literals. The tokens represent the smallest meaningful units in the code.
    
2.  **Parsing (Abstract Syntax Tree creation)**:

    -   Using the tokens generated in the previous step, the JavaScript engine constructs an **Abstract Syntax Tree** (AST).
    -   The AST represents the hierarchical structure of the code and shows how different elements of the code relate to each other. It does not contain specific details about the program's execution yet.
    
3.  **Interpreter (Baseline Execution)**:
    
    -   The interpreter starts executing the code based on the AST.
    -   It goes through the AST node by node, executing the operations as it encounters them.
    -   During this baseline execution, the engine may use various techniques to optimize the performance of frequently executed code.
    
4.  **Profiler (Optional)**:
    
    -   Some JavaScript engines include a profiler that collects information about the code's execution during baseline execution.
    -   The profiler gathers data on which parts of the code are executed frequently, how much time is spent on each function, and other performance-related metrics, this helps compiler in optimizing the code if required.
    
5.  **Optimizing Compiler (Optional)**:
    
    -   If the JavaScript engine has an optimizing compiler (like **V8's TurboFan**), it uses the profiling data to optimize the code further.
    -   The optimizing compiler may apply various advanced optimization techniques to generate highly efficient machine code.
    - Such compilers in which **profiler** watches for frequently used code and flags then passes is to the compiler to be optmized are called as **"Just-in-time"** (JIT) compilers.
    
6.  **Machine Code Generation**:
    
    -   After the interpreter has executed the code or the optimizing compiler has applied optimizations, the JavaScript engine generates machine code.
    -   Machine code is a low-level representation of the JavaScript code that the computer's processor can directly execute.
    -   This machine code is much faster than the interpreted JavaScript code as it directly utilizes the underlying hardware capabilities.
    
7.  **Execution**:
    
    -   Finally, the JavaScript engine executes the generated machine code.
    -   The processor interprets and executes the machine code instructions, performing the desired operations of the JavaScript program.

It's important to note that the exact implementation and steps of the JavaScript engine can vary between different browsers and environments. Some engines may skip certain optimization steps if they do not have an optimizing compiler, and others might have additional optimizations.
Nonetheless, this step-by-step process outlines the primary stages involved in how a JavaScript engine processes and executes JavaScript code.

**Note:** We will see **Call Stack** and **Memory Heap** later.

### Question for you: 
 > In **JS Engine** we have seen both **Interpreter** as well as **Compiler** working to convert the **JS file** to a **machine code**,<br>
 > So, is JS a Interpreted language or Compiled language ?
 
 So, the answer is **it depends**, **JavaScript** can be considered both an interpreted language and a compiled language, depending on the context and the specific **JavaScript engine** being used.
 -  **Interpreted Language**:
    
    -   In the early days of JavaScript, it was primarily interpreted. When a JavaScript program is executed, the JavaScript engine would read the source code line by line, interpret it, and execute the code directly without a separate compilation step.
    -   The interpreter processes the JavaScript code on the fly and executes it without creating an intermediate representation like machine code. This makes the initial execution of JavaScript code relatively fast, but in long run doing this way made JavaScript run very slow and this led to creation of **combo** of both interpreter and compiler which is known as **Just-in-Compiler** (JIT).

- **Compiled Language (Just-in-Time Compilation)**:
    
    -   Modern JavaScript engines, like **V8** used in Google Chrome and Node.js, employ a technique known as **Just-in-Time** (JIT) compilation.
    -   During the initial execution of JavaScript code, the engine uses an interpreter to execute the code quickly (**baseline execution**). However, it also collects **profiling** information about the code's performance, such as which parts of the code are executed frequently (**hotspots**).
    -   Based on this profiling data, the engine may apply optimizations and generate highly optimized machine code through a process called JIT compilation. The generated machine code is stored in memory and used for subsequent executions, improving the performance of the code.
    - The name **"Just-in-Time"** comes from the idea that the compiler is brought into action "just in time" to optimize the specific parts of the code that are identified as hotspots (frequently executed code segments). Instead of compiling the entire code upfront before execution, the JIT compiler focuses on optimizing the most performance-critical sections of the code during runtime.

**Conclusion:** JavaScript is both an interpreted language and a compiled language due to the presence of the JIT compilation in modern JavaScript engines. The interpreter helps with fast initial execution, and the JIT compilation generates optimized machine code for improved performance on subsequent executions.