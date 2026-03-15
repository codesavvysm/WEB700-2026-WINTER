# WEB700 – Assignment 5

## Forms, Body Parsing, and Template Engines (EJS)

---

## Objective

Create an **Express** application that uses **HTML forms**, **body-parsing middleware** to handle submissions, and the **EJS** template engine to render pages with server-side data. You will build a simple **Student Records** app: a form to add a student (with the fields listed below), a POST route to process it, and a view that displays submitted students using EJS (including partials and basic logic).

---

## Reference Behaviour

- **Home page (“/”)**: Rendered with EJS. Shows a short welcome message and links to “Add Student” and “View Students”.
- **Add Student page (“/add”)**: Rendered with EJS. Displays a form with the exact fields listed in Step 4 (Student ID, Student Name, Program, GPA, Graduated?). Submitting the form sends a POST request to your server.
- **After submit**: The server processes the form data and redirects the user to “View Students”.
- **View Students page (“/entries”)**: Rendered with EJS. Displays previously submitted students (stored in memory) in a table or list. Use EJS logic (e.g. iteration, conditionals) and at least one **partial** (e.g. header).
- **Styling**: Use a **single external CSS file** (e.g. in `public/css/main.css`) for layout and appearance; link it from your EJS templates. No inline styles for the main design.

---

## Step 1: Project Setup

1. Create a new folder (e.g. `assignment5`).
2. Run `npm init` (defaults are fine).
3. Install dependencies: `npm install express ejs`.
4. Add `node_modules` to a `.gitignore` file.
5. Use a structure similar to:

   ```
   assignment5
   ├── public
   │   └── css
   │       └── main.css
   ├── views
   │   ├── partials
   │   │   └── header.ejs
   │   ├── index.ejs
   │   ├── add.ejs
   │   └── entries.ejs
   ├── server.js
   ├── package.json
   └── .gitignore
   ```

---

## Step 2: Express Server and EJS

In **server.js**:

- Create an Express app.
- Set the view engine to **EJS**: `app.set('view engine', 'ejs');`
- Use `express.static('public')` so that files in `public` (e.g. CSS) are served at the root.
- Add the **body-parsing** middleware for URL-encoded form data:  
  `app.use(express.urlencoded({ extended: true }));`
- Start the server on port **8080** (or `process.env.PORT` if set).
- Log a message when the server starts (e.g. “Server listening on port 8080”).

Visiting `http://localhost:8080/` must serve the home view (rendered from `views/index.ejs`).

---

## Step 3: In-Memory Storage

For this assignment, store submitted students in an **in-memory array** in **server.js**. For example:

```js
let students = [];
```

When the form is submitted (POST), push the parsed form data (after normalizing the “Graduated?” checkbox to a boolean) onto `students`. The “View Students” page will render this array using EJS.

---

## Step 4: Form Page (“/add”) and Form Fields

Create a **GET** route for **/add** that renders `views/add.ejs` (the form page).

In **views/add.ejs**, implement a **single form** with **exactly** these fields (each with a proper **label** and a **name** attribute so values appear in `req.body`):

| Field          | Notes |
|----------------|--------|
| **Student ID** | Required. Use `name` e.g. `studentId`. |
| **Student Name** | Required. Use `name` e.g. `studentName`. |
| **Program**    | **Dropdown.** At least three program options (e.g. BTT, CAA, CPP) plus an optional “Please choose” placeholder. Use `name` e.g. `program`. |
| **GPA**        | Use `name` e.g. `gpa`. You may set `min`, `max`, or `step` as needed. |
| **Graduated?** | **Checkbox.** Yes/no: checked = yes (graduated), unchecked = no (not graduated). Use `name` e.g. `graduated`. Associate with a label (e.g. “Graduated?” or “Yes”). |
| **Submit**     | Submits the form. |

- **form** element: `method="post"`, `action="/add"` (or your POST route). Omit `enctype` so the default `application/x-www-form-urlencoded` is used.
- Use **labels** for every field (using `for`/`id` on the label and input, or wrapping the control in a `<label>`), as in the course material.

---

## Step 5: POST Route and Checkbox Handling

Create a **POST** route that matches the form’s `action` (e.g. **POST /add**).

- Read the submitted data from `req.body` (e.g. `studentId`, `studentName`, `program`, `gpa`, `graduated`).
- **Graduated? checkbox:** Normalize to a boolean. Checkboxes submit `"on"` when checked and are `undefined` when unchecked.
- Push the resulting object onto your in-memory `students` array.
- Respond with a **redirect** to the View Students page: `res.redirect('/entries');`

---

## Step 6: EJS Views and Partials

- **views/index.ejs**: Home page. Include a title, welcome text, and links to “Add Student” (`/add`) and “View Students” (`/entries`). Use your **header** partial so the layout is consistent.
- **views/add.ejs**: Add Student form page. Use the same **header** partial. Render the form with the five fields from Step 4 (Student ID, Student Name, Program, GPA, Graduated? checkbox).
- **views/entries.ejs**: View Students page. Use the **header** partial. Pass the `students` array from the route to the view. Use EJS to:
  - **Iterate** over the students (e.g. `forEach` or `for...of` inside `<% ... %>` and output each student’s fields with `<%= ... %>`).
  - **Conditionally** show something (e.g. “No students yet” when `students.length === 0`, or display “Yes”/“No” for the graduated field using an `if`/`else`).

Create **views/partials/header.ejs**. The header should include:

- A site title (e.g. “Student Records”).
- Navigation links: **Home** (`/`), **Add Student** (`/add`), **View Students** (`/entries`).
- Use the **include** syntax: `<%- include('partials/header', { page: '/add' }) %>` and pass a `page` variable so you can optionally highlight the current page in the nav (e.g. bold the current link) using EJS conditionals or a ternary in the partial.

All views must be valid HTML5 (e.g. `<!DOCTYPE html>`, `<html>`, `<head>`, `<body>`, `<meta charset="utf-8">`, `<title>`). Link the external stylesheet from the **head** of each EJS file:  
`<link rel="stylesheet" href="/css/main.css" />`

---

## Step 7: Routes Summary

Your server must implement at least:

| Method | Path      | Behaviour |
|--------|-----------|-----------|
| GET    | /         | Render `index.ejs` (home). |
| GET    | /add      | Render `add.ejs` (Add Student form). |
| POST   | /add      | Parse body, set `req.body.graduated` to boolean, push to `students`, redirect to `/entries`. |
| GET    | /entries  | Render `entries.ejs` with `{ students: students }`. |

---

## Step 8: CSS

Put **all** styling in **public/css/main.css**. Do not use inline styles for the required layout and look.

Your CSS should provide:

- Consistent layout for all pages (header, main content).
- Styled navigation (e.g. horizontal list or inline links).
- Readable form layout (labels, spacing, alignment).
- A clear table or list for the View Students page (e.g. columns for Student ID, Name, Program, GPA, Graduated; borders, spacing, alternating rows optional).
- Typography and spacing so the app is clear and readable.

You may choose colours and exact values; the result should look intentional and consistent.

---

## Step 9: Deployment to Vercel

You must deploy your application to **Vercel**.

Requirements:

- The deployed application must run without errors.
- The home page, Add Student form, form submission, and View Students page must all work on the deployed version.
- You must include the **live Vercel URL** in your submission.

**Note:** In-memory storage is lost on restart. After deployment, submitting the form and then visiting “View Students” should still show the new student until the server restarts (e.g. after a new deploy or timeout). This is acceptable for this assignment.

---

## Notes

- The form has **exactly** the five fields listed in Step 4: Student ID, Student Name, Program (select), GPA (number), Graduated? (checkbox). Use one form and one POST route for “Add Student”.
- **EJS:** Use `<%= %>` for escaped output, `<%- %>` for includes (and unescaped HTML when needed), `<% %>` for logic (if/else, loops). Use at least one **partial** (header) and **iteration** and **conditionals** in `entries.ejs` (e.g. show “Yes”/“No” for graduated).
- The application must run locally and on Vercel.

---

## Assignment Submission

At the top of **server.js**, include:

```js
/**********************************************************************************
WEB700 – Assignment 05
I declare that this assignment is my own work in accordance with Seneca Academic Policy.
No part of this assignment has been copied manually or electronically from any other source
(including 3rd party web sites) or distributed to other students.
Name: ______________________
Student ID: _________________
Date: __________________
**********************************************************************************/
```

Submit your project (ZIP or repository link) with:

- **server.js**
- **views/** (all .ejs files, including partials)
- **public/css/main.css**
- **package.json**
- **.gitignore**
- **Live Vercel URL** (link to your deployed site)

---

## Checklist

- [ ] Express server with EJS view engine, `express.urlencoded()`, and `express.static('public')`, runs on port 8080.
- [ ] In-memory `students` array; POST /add parses body, sets `graduated` to true/false, pushes to `students`, redirects to `/entries`.
- [ ] **GET /** renders home (index.ejs) with links to Add Student and View Students.
- [ ] **GET /add** renders form (add.ejs) with **exactly**: Student ID, Student Name, Program (select), GPA (number), Graduated? (checkbox), Submit; each with a label and `name`.
- [ ] **GET /entries** renders entries.ejs with `{ students: students }`; EJS iterates over students and uses at least one conditional (e.g. “No students yet” or “Yes”/“No” for graduated).
- [ ] At least one **EJS partial** (e.g. header.ejs) with nav: Home, Add Student, View Students.
- [ ] All styling in **main.css**; no inline styles for main layout; pages readable and consistent.
- [ ] Deployed to **Vercel**; live URL included in submission.
