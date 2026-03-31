# Week 12 — In-Class Exercise: Web API Overview

Example repository: [Web-API-Overview](https://github.com/WPFoundations-Examples/Web-API-Overview)

Modify the example from the course as described below.

---

## Task 1

- In **home.html**, keep **only one** button labeled **Get All Users**.
- When the button is clicked, call **GET** `/api/users` and **log** the response (the `users` data from the server) to the **browser console**.

In **server.js**, define the `users` array like this:

```javascript
const users = [
  {
    fName: "Bob",
    lName: "Jones",
  },
  {
    fName: "Wanda",
    lName: "Smith",
  },
];
```

Expose **GET** `/api/users` so it returns this array (for example as JSON).

---

## Task 2

- Add **`add.html`** under the **`views`** folder (alongside **`home.html`** in the sample repo).
- On **home.html**, add a **link** (not an extra button—Task 1 still allows only one button) to the add page, for example **`<a href="/add.html">Add user</a>`**. If the starter app does not already serve **`views/add.html`**, add a **`GET /add.html`** route in **server.js** that uses **`res.sendFile`** to send **`views/add.html`**.
- The page should have a form with text inputs for **First Name** and **Last Name**, and a **Submit** button.
- On submit, send a **POST** to **`/api/users`** with a JSON body using **`fName`** and **`lName`** (matching the starter **server.js**), so the server **appends** the new user to the `users` array.
- After a successful add, navigate to the **home** page. In the sample project, home is served at **`/`** (the file is `views/home.html`—do not assume `/views/home.html` is a valid URL unless you add that route).

---
