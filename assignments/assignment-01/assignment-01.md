# Submission Deadline:

Sunday, Jan 24<sup>th</sup> @ 11:59 PM

# Assessment Weight:

5% of your final course grade

# Objective:

This first assignment will focus primarily on applying JavaScript
fundamental concepts including: defining / using variables, arrays,
functions, looping / conditional control structures and commenting code.

The main objective is to create a very simple "Web Server Simulator"
function that responds to requests for data using a specific HTTP Verb
(ie: "GET", "POST", etc) and path (ie: "/home") combination. Once this
is complete, a second "tester" function will be created to invoke the
"Web Server Simulator" function with a random request from a predefined
list.

# Specification:

This assignment will consist of a single JavaScript file (".js"),
developed using [Visual Studio Code](https://code.visualstudio.com/). To
execute our code, we will be using the [Node.js](https://nodejs.org/en/)
JavaScript runtime from within the [Integrated
Terminal](https://code.visualstudio.com/docs/editor/integrated-terminal)
included with Visual Studio Code.

### **<u>Step 1:</u>** Download & Install the Required Software

> Download and install the following software for your operating system:

- [Visual Studio Code](https://code.visualstudio.com/)

- [Node.js](https://nodejs.org/en/)

- [Git](https://git-scm.com/downloads) Command Line Tool (Used later in
  the course)

### **<u>Step 2</u>:** "Hello World"

> With all our software successfully installed, it's time to create the
> file and make sure that we can execute JavaScript code using Node.js

- Somewhere on your computer, create a folder for your assignment 1 code

- Open Visual Studio Code and Choose **File \> Open** to open your newly
  created folder

- Using Visual Studio Code, create a new file within the folder called
  "assignment1.js"

- In the code editor, type the JavaScript code: **console.log("Hello
  World!");**

- Save the file and open the “Integrated Terminal” using either the
  “View” menu and choosing “Terminal” or using the key combination
  ctrl + \`

- In the "Integrated Terminal" type the command: **node assignment1.js**
  to execute your code.

### **<u>Step 3</u>:** Creating the "Server Paths"

> Now that we know that we can execute JavaScript code, we can remove
> the "Hello World!" code and create some predefined paths (later
> referred to as "routes") for our web server simulator to "listen" for.
>
> Use the following table to create 3 variables (serverVerbs,
> serverPaths, and serverResponses) at the top of the file that each
> store an array with the following data (strings):
>
> **Note**: Fill in your own Student Name / Email in the spaces
> indicated

|                 | **\[0\]**                        | **\[1\]**                 | **\[2\]**         | **\[3\]**             | **\[4\]**      | **\[5\]**                                           |
| --------------- | -------------------------------- | ------------------------- | ----------------- | --------------------- | -------------- | --------------------------------------------------- |
| serverVerbs     | "GET"                            | "POST"                    | "GET"             | "GET"                 | "POST"         | "GET"                                               |
| serverPaths     | "/"                              | "/register"               | "/products"       | "/services"           | "/cart"        | "/profile"                                          |
| serverResponses | "Welcome to WEB700 Assignment 1" | "Registration Successful" | "Product Catalog" | "Service Information" | "Cart Updated" | "Profile: **_Student Name_** (**_Student Email_**)" |

> By defining the arrays in the above order, we can associate a specific
> "server Response" with the matching "verb" + "path" combination. For
> example, a "POST" request on the "/register" path should cause the "web
> server simulator" function (defined below) to return a message
> containing the text "Registration Successful". Similarly, a "GET" request on
> the default path ("/") should return a string containing the text
> "Welcome to WEB700 Assignment 1"

### **<u>Step 4</u>:** Creating the "web server simulator" Function - "httpRequest"

> The next step is to implement the actual function that will do the
> work of our simple web server (see: [JavaScript Functions in Week
> 2](https://wpf.gitpages.senecapolytechnic.ca/JavaScript-Fundamentals/functions)). We'll call this
> function "httpRequest" and it will accept two parameters: **httpVerb**
> and **path**. This function will behave according to the following
> specification:

- If the **httpVerb** parameter and **path** parameter can **both** be
  found at the **same index** in the global "serverVerbs" and
  "serverPaths" arrays (see step 3), the matching "serverResponses"
  value will be returned including the status code "200".

  For example, if **httpRequest("GET", "/")** is invoked, then the
  function should return "200: Welcome to WEB700 Assignment 1", since
  the serverVerbs\[0\] == "GET" and "serverPaths\[0\] == "/". Similarly,
  if **httpRequest("POST", "/register")** is invoked, then the function
  should return "200: Registration Successful", since serverVerbs\[1\] == "POST"
  && serverPaths\[1\] == "/register".

  The idea here is that the **httpVerb** parameter must be found in the
  **serverVerbs** array at the same **index** as the **path** parameter
  in the **serverPaths** array. If this is the case, the
  **serverResponses** array at the same **index** will be returned along
  with the 200 status code.

  **HINT:** You can use a "for loop" to loop through all the server
  paths (using serverPaths.length) and make sure that the current index
  of the loop (ie 0) returns the requested value from the
  **serverVerbs** array AND the **serverPaths** array.

- If a mismatch occurs, ie: the **httpVerb** value of **"GET"** is found
  at index 0 and the **path** value is found at index 1 (ie:
  **httpRequest("GET", "/register")**), then the server has encountered an
  error with the client request (404). If this is the case, the function
  should instead return the string: "404: Unable to process
  **_httpVerb_** request for **_path_**" where **httpVerb** and **path**
  are the values passed to the function (ie: "404: Unable to process
  **GET** request for **/register**"

### **<u>Step 5</u>:** Manually Testing the "httpRequest" Function

> Before we create our next function, manually test the "httpRequest"
> function by calling it with each of the possible combinations
> including a non-matching combination. For example:

- console.log(httpRequest("GET", "/")); // shows "200: Welcome to WEB700
  Assignment 1"

- console.log(httpRequest("GET", "/products")); // shows "200: Product Catalog"

> and so on, including a "404" error:

- console.log(httpRequest("PUT", "/products")); // shows "404: Unable to process
  PUT request for /products"

### **<u>Step 6</u>:** Automating the Tests by creating a "automateTests" Function

> Now that we're confident that our "httpRequest" function is behaving
> correctly, let's introduce another function that will continuously
> invoke it with a random request that consists of a "GET" or "POST"
> verb along with one of our predefined paths (including some "notFound"
> paths). It will consist of 0 parameters, since the testing logic and
> parameters will be defined entirely within the function.
>
> However, before we begin to create the function, we will need to first
> introduce a new "utility" function near the top of our code that will
> help us generate a random integer value between 0 and a specified
> maximum.
>
> You can find this function here:
> <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random>
>
> It's called "getRandomInt(max)" and you are free to copy/paste the
> function for use within your code.
>
> With this function in place, we can now define our new "automateTests"
> function to use the following code / logic:

- As a first step, define the following arrays:

|           | **\[0\]** | **\[1\]**   | **\[2\]**   | **\[3\]**   | **\[4\]** | **\[5\]**  | **\[6\]**        | **\[7\]**        |
| --------- | --------- | ----------- | ----------- | ----------- | --------- | ---------- | ---------------- | ---------------- |
| testVerbs | "GET"     | "POST"      |             |             |           |            |                  |                  |
| testPaths | "/"       | "/register" | "/products" | "/services" | "/cart"   | "/profile" | "/invalidRoute1" | "/invalidRoute2" |

- Next, within this function, define another function called
  **randomRequest** (accepts 0 parameters) - we will use the
  [setInterval](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setInterval)
  function to repeat this function over and over again every 1 second

- Inside the new randomRequest function, declare the following
  variables:

  - **randVerb** - A random value from the **testVerbs** array (ie:
    testVerbs\[_some random index between 0 and 1 inclusive_\])

  - **randPath** - A random value from the **testPaths** array (ie:
    testPaths\[_some random index between 0 and 7 inclusive_\])

- Now that these variables are declared, we can use them to invoke our
  "httpRequest" function with the random values! (**NOTE:** be sure to
  **console.log()** the result, so that we can see the result of the
  request in the console.

- Underneath the **randomRequest** function definition (but still inside
  the **automateTests** function), use the
  [setInterval](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setInterval)
  function to execute the **randomRequest** function over and over again
  every 1 second (1000 milliseconds)

### **<u>Step 7</u>:** Invoke the "automateTests" function

> At the bottom of your code, beneath all function definitions and
> variable declarations, add the code to invoke the "automateTests"
> function. When we run our assignment1.js file, this function will be
> responsible for kicking off the testing process.

### **<u>Step 8</u>:** Running the Code

> As a final test to ensure that the code is working properly, open the
> **Integrated Terminal** and execute the command: **node
> assignment1.js**. At this point, you should see your program
> continuously outputting values every second to the console, ie:
>
> 404: Unable to process GET request for /register  
> 404: Unable to process GET request for /invalidRoute1  
> 200: Registration Successful  
> 200: Product Catalog  
> 200: Cart Updated
>
> …
>
> etc, etc.
>
> What we are essentially doing here is testing a very high-level
> approximation of a web server that responds to random requests from
> clients.
>
> **NOTE:** This code will continuously generate random requests once
> every second. However, there is nothing in our code to put a stop to
> it. The only way to stop the program at this point is to use the
> command **ctrl + c** in the **Integrated Terminal** to stop the code
> execution.

## Assignment Submission:

1.  Add the following declaration at the top of your assignment1.js
    file:

> /\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*  
> \* WEB700 – Assignment 1  
> \* I declare that this assignment is my own work in accordance with
> Seneca Academic Policy.  
> \* No part of this assignment has been copied manually or
> electronically from any other source  
> \* (including AI, other web sites) or distributed to other students.
> \*  
> \* Name: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ Student ID:
> \_\_\_\_\_\_\_\_\_\_\_\_\_\_ Date: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
> \*  
> \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*/

2.  Submit your assignment1.js file as per instructions in the Blackboard
