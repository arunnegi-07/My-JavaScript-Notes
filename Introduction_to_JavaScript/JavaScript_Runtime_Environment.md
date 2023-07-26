### Question for you: 
 > Why do we say JavaScript is a **Single Threaded** language ?
 
So, we are at the good position to answer this question as we know about **call stack**, it's functionality and how it works. We know JavaScript has only one **call stack** which keeps track of the order in which program is executed and having only **one call stack** means that it executes one operation at a time in a single sequence, following a single path of execution. <br>
This is reason we say JavaScript is a single threaded language and this behaviour of JavaScript makes it **Synchronous**.
 
 The reason for JavaScript being **single-threaded** lies in its design and **historical context**:

- **JavaScript** was initially developed to be a client-side language for web browsers. In the context of web browsers, JavaScript's primary use is to manipulate the **Document Object Model** (DOM) and **handle events** such as user interactions (clicks, keypresses, etc.). Being single-threaded makes it easier to manage and synchronize these event-driven operations.

> But does it mean **JavaScript** only perform tasks **Synchronously** and execute only single task at a time 
   and cannot handle **Asynchronous** tasks ?

- Here **JavaScript Runtime Environment** comes into picture. Every browser contains **JSRE** which has **JS Engine** as one of it's component  and it also contain other components like **Event Loop**, **Web APIs**, and **Callback Queue** and these components collectively  work together to provide an efficient and **asynchronous** execution.

**Note :** There are some **inbuilt features** of JavaScript like  **Promises** (introduced in ES6) and **Async/Await** (introduced in ES8)  to provide a more structured and readable way to work with asynchronous operations. We will discuss them in separate module in which we talk about **Asynchronous JavaScript**. 



## JavaScript Runtime Environment
Every web browser contains a **JavaScript Runtime Environment** (**JSRE**), which facilitates the execution of JavaScript code. The **JS Engine** is an integral part of this **JSRE**, responsible for **parsing** and **executing** the JavaScript code. Additionally, the **JSRE** includes other important components such as the **Event Loop**, **Web APIs**, and **Callback Queue**. These components collectively work together to provide an efficient and **asynchronous** execution environment for JavaScript within the browser.
 
<br>
<p align="center">
<img src="https://files.catbox.moe/u97gsw.svg" alt="Call-Stack-Heap" border="0">
</p>
 <br>

**1. Web APIs**

Web APIs (Application Programming Interfaces) are a set of built-in interfaces provided by web browsers that allow JavaScript code to interact with the browser environment. <br>
Web APIs cover a wide range of functionalities, but some of the most commonly used ones include:

-  **DOM API (Document Object Model)**: The DOM API allows JavaScript to interact with the HTML and XML documents displayed in the browser. It provides methods to access, manipulate, and modify the structure, content, and style of the document. For example, you can use DOM API methods like `getElementById()`, `querySelector()`, `appendChild()`, `setAttribute()`, etc., to manipulate the HTML elements and modify the content on the page.
    
-  **Fetch API**: The Fetch API provides an interface for fetching resources across the network by using generic definitions of the Request and Response objects.

- **Web Storage API**: The Web Storage API provides two mechanisms for storing data on the client-side: `localStorage` and `sessionStorage`. These APIs allow you to store data as key-value pairs in the browser, providing a way to save user preferences, cache data, or share data between different pages of a website.

- **Delayed Code Execution**: `setTimeout` is a function provided by the browser that allows you to schedule the execution of a callback function after a specified delay. It is commonly used to create timed events or introduce delays in the execution flow.

**2. Callback queue**

- The Callback Queue (Task Queue) is a component of the JavaScript runtime that holds **completed** **asynchronous** tasks (callbacks).

- The **Event Loop** continuously checks the **Call Stack**. When the stack is empty, the Event Loop **dequeues** and executes callbacks from the Callback Queue.

- This process ensures that asynchronous tasks are handled efficiently without blocking the **main thread**, enabling JavaScript to remain non-blocking and responsive.
<br>
<p align="center">
<img src="https://files.catbox.moe/ti08k1.svg" alt="Call-Stack-Heap" border="0">
</p>
 <br>


**3. Event loop**

- It continuously monitors the state of the Call Stack and the Callback Queue.

- When the Call Stack is empty (no synchronous code is being executed), the Event Loop checks the Callback Queue for any pending tasks (callbacks).

- If there are callbacks waiting in the queue, the Event Loop dequeues and executes them one by one, allowing JavaScript to handle asynchronous operations efficiently without blocking the main thread.

**Conclusion :** In the browser's **JavaScript Runtime Environment**, several components work together to facilitate the execution of JavaScript code. These components include the **JS Engine**, responsible for parsing and executing JavaScript, the **Event Loop**, which handles asynchronous tasks, **Web APIs** for interacting with the browser environment, and the **Callback Queue***, which manages asynchronous callbacks. Their collaboration creates an efficient and asynchronous execution environment for JavaScript in the browser.