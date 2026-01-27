# Objective:

The second assignment will focus on more advanced JavaScript skills
including: promises, using / defining objects using the "class"
keyword and passing functions as parameters (callback functions).

The main objective is to create and test a single JavaScript file
(`assignment2.js`) that is responsible for pulling **employee** and
**department** data from multiple files as well as providing multiple
promise-based functions that "resolve" with the data.

# Specification:

This assignment will consist of a few files, including: a main
`assignment2.js` file and a `data` folder containing two files
(`departments.json` & `employees.json`).

### **<u>Step 1:</u>** Create the Files & Directories

> Whenever we start a new project or example for this course, we will
> always create a new folder to contain the code. For this assignment,
> start by creating a new folder somewhere on your local machine to
> house all of your code. Once you have done this, open it up in Visual
> Studio Code and create the following file / folder structure:
>
> `assignment2.js`  
> `data/`  
> &nbsp;&nbsp;&nbsp;&nbsp;`departments.json`  
> &nbsp;&nbsp;&nbsp;&nbsp;`employees.json`

### **<u>Step 2</u>:** Using the Data (employees.json & departments.json)

The data for this assignment is already provided for you in two separate
files in the `data` folder:

- `data/employees.json`
- `data/departments.json`

**Recall:**
[JSON](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON)
stands for **JavaScript Object Notation** and is a way of representing
JavaScript Objects in a plain-text format.

Simply use the existing JSON data in your local `data` folder.

### **<u>Step 3</u>:** Managing the Employee / Department Data in `assignment2.js`

### **<u>Data Class</u>**

To help us manage the data in this file, we must create a **class**
called `Data` according to the following specification:

- This class only contains a single constructor which takes two
  parameters: **employees** and **departments**.

  - This constructor will take the value from the **employees** parameter
    and use it as the value for a property called `employees` within the
    class.

  - Similarly, the constructor will take the value from the
    **departments** parameter and use it as the value for a property
    called `departments` within the class.

Once the class definition is complete, proceed to declare the variable
`dataCollection` beneath the class and assign it to ***null***. This
will be the variable that holds an *instance* of the `Data` class once
it's created (within the `initialize` function defined below).

### **<u>Functions</u>**

Each of the below functions are designed to work with the employees and
departments datasets. Since we have no way of knowing how long each function
will take (we cannot assume that they will be instantaneous, ie: what if
we move from .json files to a remote database, or introduce hundreds of
thousands of objects into our .json dataset? - this would increase lag
time), **<u>every one of the below functions</u> must return a promise**
that **passes the data** via its `"resolve"` method (or - if **an
error occurred**, passes an **error message** via its `"reject"`
method).

We will be assuming that they return a promise and we will respond
appropriately with either **`.then()`** and **`.catch()`** or **`async/await`**
syntax (you may choose whichever approach you prefer).

**initialize()**

- This function will read the contents of the `./data/employees.json`
  file.  
    
  **hint**: see "[Reading files with
  Node.js](https://nodejs.org/en/learn/manipulating-files/reading-files-with-nodejs)" (from
  the documentation), ie:  
    
```
fs.readFile('somefile.json', 'utf8', function(err,  dataFromSomeFile){
  if (err){
    console.log(err); // or reject the promise (if used in a promise)
    return; // exit the function
  }

  let data = JSON.parse(dataFromSomeFile); // convert the JSON from the file into an array of objects
  console.log(data);
});    
```
  
- Only once the read operation for `./data/employees.json` has completed
  successfully (not before), repeat the process for the
  `./data/departments.json` file.

- Once these two operations have finished successfully, create a new
  *instance* of the **Data** class (defined above) and assign it to the
  variable `dataCollection` using the data returned from your
  `fs.readFile` operations, ie:  
    
  `dataCollection = new Data(employeeDataFromFile, departmentDataFromFile);`  
    
  Going forward, you can access the full array of **employees** and
  **departments** in your other functions using the **`dataCollection`**
  object, ie: `dataCollection.employees` or `dataCollection.departments`.

- Finally, invoke the **resolve** method for the promise to communicate
  back to the rest of your code that the operation was a success.

- **NOTE:** If there was an error at any time during this process,
  instead of outputting an error to the console, invoke the **reject**
  method for the promise and pass an appropriate message, ie:
  `reject("unable to read employees.json");`.

**getAllEmployees()**

- This function will provide the full array of `"employee"` objects using
  the **resolve** method of the returned promise.

- If for some reason, the length of the array is 0 (no results
  returned), this function must invoke the **reject** method and pass a
  meaningful message, ie: `"no results returned"`.

**getManagers()**

- This function will provide an array of `"employee"` objects whose
  `isManager` (or equivalent) property is **true** using the **resolve**
  method of the returned promise.

- If for some reason, the length of the array is 0 (no results
  returned), this function must invoke the **reject** method and pass a
  meaningful message, ie: `"no results returned"`.

<u>getDepartments()</u>

- This function will provide the full array of `"department"` objects using
  the **resolve** method of the returned promise.

- If for some reason, the length of the array is 0 (no results
  returned), this function must invoke the **reject** method and pass a
  meaningful message, ie: `"no results returned"`.

### **<u>Step 4</u>:** Using the Functions in `assignment2.js`

The final development step in the assignment is to use the functions
that you defined in `assignment2.js` to test the functionality of your
code.

- First, at the top of `assignment2.js`, ensure that you require the built-in
  Node module for working with files:

  - `const fs = require("fs");`

- Next, invoke the `initialize` function and output a success message to
  the console if it was successful and an error message if it failed
  (using either `.then()` and `.catch()` or `async/await` with `try/catch` -
  choose whichever approach you prefer).

- Once this is complete, try running your code. If you see the success
  message, then you were able to successfully read both files and you
  can proceed with the rest of the assignment. If you see the error
  message, go back and look at that `initialize` function and make sure
  there aren't any errors.

- Now that you're confident that your `initialize` function works
  properly, you can delete your temporary success message and in its
  place, write code to test (invoke) all 3 of your other functions:

**getAllEmployees()**

- To ensure that this function is working properly, output the number of
  employees to the console in the format:  
  `"Successfully retrieved x employees"`, where **x** is the number of
  employees (**HINT**: You can use the
  [array.length](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/length)
  property to get the number of elements in an array).

**getDepartments()**

- Testing this function is almost identical to what was done for
  `getAllEmployees()`, however it will display the number of
  `"departments"` returned in the format:
  `"Successfully retrieved x departments"`, where **x** is the number of
  departments.

**getManagers()**

- This is the final function to test. To ensure it works properly,
  display the number of `"managers"` returned in the format:
  `"Successfully retrieved x managers"`, where **x** is the number of
  managers.

**NOTE**: Do not forget to handle the possibility that a promise may get
**reject**ed in the future, so do not forget to include `.catch`
functions where appropriate (or `try/catch` blocks if using `async/await`).

### **<u>Step 5</u>:** Confirming the Output 

If everything is working properly once the program starts, you should
see the following in the console:

Successfully retrieved 260 employees

Successfully retrieved 11 departments

Successfully retrieved 30 managers

## Assignment Submission:

1.  Add the following declaration at the top of your `assignment2.js` file:

> /*************************************************************  
> \* WEB700 – Assignment 2  
> \* I declare that this assignment is my own work in accordance with  
> \* Seneca Academic Policy.  
> \* No part of this assignment has been copied manually or  
> \* electronically from any other source  
> \* (including web sites) or distributed to other students.  
> \*  
> \* Name: ______________________ Student ID: ______________________ Date: ____________________  
> \*  
> *************************************************************/

2.  Submit your assignment2.js file as per instructions in the Blackboard

## Important Note:

- **NO LATE SUBMISSIONS** for assignments. Late assignment submissions
  will not be accepted and will receive a **grade of zero (0)**.


