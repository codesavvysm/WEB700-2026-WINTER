# WEB700 – Assignment 3

## Express Routing, Middleware, and Deployment

## Objective

The objective of this assignment is to practice building a web server using **Node.js** and **Express.js**, with a specific focus on **Express middleware**.

---

## Provided Files

You are provided with the following data files:

/data  
 ├── [employees.json](data/employees.json)  
 └── [departments.json](data/departments.json)

These files contain the data that your Express routes will serve.

You can load the data in your application using:

```js
const employees = require("./data/employees.json");
const departments = require("./data/departments.json");
```

---

## Step 1: Project Setup

1. Create a new folder called `assignment3`
2. Open the folder in Visual Studio Code
3. Initialize a Node.js project using npm
4. Install Express
5. Create the following structure:

assignment3
├── data  
│ ├── [employees.json](data/employees.json)  
│ └── [departments.json](data/departments.json)  
├── server.js  
├── package.json  
└── .gitignore

6. **Do not push `node_modules` to Git.** Create a `.gitignore` file in your project root and add `node_modules` to it so that dependencies are not committed to your repository.

---

## Step 2: Creating the Express Server

In `server.js`:

- Import the Express module
- Create an Express application
- Start a server on port 8080 (or `process.env.PORT` if defined)

When the server starts, it must log a message indicating that the server is running.

---

## Step 3: Application-Level Middleware

Before defining any routes, create **application-level middleware** that:

- Logs every incoming request to the console
- Includes the user-agent and the current date/time
- Attaches the log message to the `req` object (for example: `req.log`)
- Calls the `next()` function to allow the request to continue

This middleware must execute for **every request**.

---

## Step 4: Required Routes

### GET /

Return the following plain-text message:

Welcome to the WEB700 Express Server

---

### GET /employees

Return all employee objects from employees.json as JSON.

---

### GET /employees/:num

Return a single employee whose `employeeNum` matches the `:num` route parameter.

- If the employee is found, return the employee object as JSON
- If no employee is found, return the following JSON message with an HTTP status code of 404:

{ "message": "Employee not found" }

---

### GET /departments

Return all department objects from departments.json as JSON.

---

### GET /departments/:id

Return a single department whose `departmentId` matches the `:id` route parameter.

- If the department is found, return the department object as JSON
- If no department is found, return the following JSON message with an HTTP status code of 404:

{ "message": "Department not found" }

---

## Step 5: Route-Level Middleware

Create a **route-level middleware function** that restricts access to a secure route.

- The middleware should randomly allow or deny access
- If access is denied, respond with HTTP status code 403 and a message indicating access is denied
- If access is allowed, call `next()`

Create the following route using this middleware:

### GET /secure

If access is allowed, return the message:

Welcome to the secure area

---

## Step 6: 404 Middleware

Create middleware that handles requests to **unknown routes**.

- This middleware must be placed **after all route handlers**
- It must return the following message:

Page Not Found

- The HTTP status code must be 404

---

## Step 7: Deployment to Vercel

You must deploy your Express application to **Vercel**.

Requirements:

- The deployed application must run without errors
- All required routes must work on the deployed version
- You must include the **live Vercel URL** in your submission

---

## Notes & Constraints

- Middleware must correctly use the `next()` function
- The application must run locally and on Vercel

---

## Assignment Submission

At the top of your `server.js` file, include the following declaration:


```js
/**********************************************************************************  
WEB700 – Assignment 03
I declare that this assignment is my own work in accordance with Seneca  Academic Policy.  
No part of this assignment has been copied manually or electronically from any other source 
(including 3rd party web sites) or distributed to other students.
Name: ______________________    Sudent ID: _________________   Date: __________________
**********************************************************************************/
```
