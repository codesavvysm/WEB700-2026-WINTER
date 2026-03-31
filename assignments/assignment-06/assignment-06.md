# WEB700 – Assignment 6

## PostgreSQL (Neon), Sequelize, and Data Persistence

---

## Objective

Build an **Express** application that persists **Student** records in **PostgreSQL** using **Sequelize**. You will provision a database on **Neon**, configure **`new Sequelize(...)`** in **`server.js`** with your connection values (same approach as the course **[Relational-Database-Postgres](https://github.com/WPFoundations-Examples/Relational-Database-Postgres/blob/main/server.js)** example—no **`dotenv`** package), define a model, run **`sequelize.sync()`**, and use **real database reads and writes**. The UI follows that example: a **single** **`home.ejs`** with forms for list / update / delete / add.

Course reference: **`postgres-webapi.md`** in this folder (Neon, Sequelize, **`create`**, **`findAll`**, **`update`**, **`destroy`**, **`sync()`**, etc.).

**Example to mirror:** **[Relational-Database-Postgres](https://github.com/WPFoundations-Examples/Relational-Database-Postgres/tree/main)**—[`server.js`](https://github.com/WPFoundations-Examples/Relational-Database-Postgres/blob/main/server.js) and [`views/home.ejs`](https://github.com/WPFoundations-Examples/Relational-Database-Postgres/blob/main/views/home.ejs). Replace **`Name`** / **`fName`** / **`lName`** with **`Student`** and the Assignment 5 field set; use **`/addStudent`** and **`/updateStudent`**. **Delete:** clearing **both** **`studentId`** and **`studentName`** and clicking **Update** calls **`destroy`**, like clearing both name fields in the **`Name`** demo. Link **`public/css/main.css`** from **`home.ejs`**.

**Connection:** Put your Neon **database name**, **user**, **password**, and **host** directly in **`server.js`** in the **`Sequelize`** constructor (with **SSL** options for Neon as in **`postgres-webapi.md`**). **Do not** use the **`dotenv`** module for this assignment. For **Vercel**, you may either keep the same literals in the deployed **`server.js`** or switch the constructor to read **`process.env.PGDATABASE`**, **`process.env.PGUSER`**, etc.—Vercel injects those from **Project → Settings → Environment Variables** without any **`dotenv`** package.

---

## Reference Behaviour

- **`GET /`**: **`Student.findAll`** (with **`order`** on **`id`**). Render **`views/home.ejs`** with **`data`** (same as the [example](https://github.com/WPFoundations-Examples/Relational-Database-Postgres/blob/main/server.js)).
- **`home.ejs`**: Instructions for **change** / **remove** (clear **`studentId`** + **`studentName`** → **Update**) / **add** (bottom form → **Add New**). EJS **conditionals** / **`forEach`**; one **`POST /updateStudent`** form per row (hidden **`id`**); one **`POST /addStudent`** form at the bottom.
- **`POST /addStudent`**: **`Student.create`**, **`res.redirect('/')`**. Handle validation and unique **`studentId`** without crashing.
- **`POST /updateStudent`**: Both identifiers empty → **`destroy`**; else **`update`**; **`res.redirect('/')`**.
- **Styling:** **`public/css/main.css`** linked from **`home.ejs`**.

---

## Step 1: Neon and PostgreSQL

1. Create a **Neon** project (see **`postgres-webapi.md`**).
2. Copy **host**, **database**, **user**, and **password** from the Neon dashboard.
3. Paste them into **`server.js`** in the **`new Sequelize('database', 'user', 'password', { host: '...', ... })`** call (and **SSL** for Neon).

---

## Step 2: Project Setup

1. Create a folder (e.g. `assignment6`).
2. Run `npm init` (defaults are fine).
3. Install dependencies (**no `dotenv`**):

   ```bash
   npm install express ejs sequelize pg pg-hstore
   ```

4. **`.gitignore`**: at least **`node_modules`**.

---

## Step 3: Sequelize in `server.js`

1. **`new Sequelize(...)`** with your Neon values and **`dialect: 'postgres'`**, **`dialectOptions.ssl`** as in **`postgres-webapi.md`**.
2. **`sequelize.authenticate()`** then **`sequelize.sync()`** then **`app.listen`** (or equivalent chain).

---

## Step 4: Sequelize Model — `Student`

| Attribute       | Notes |
|-----------------|--------|
| **studentId**   | String, **unique**, required for normal rows. |
| **studentName** | String, required for normal rows. |
| **program**     | String. |
| **gpa**         | Float (or double). |
| **graduated**   | Boolean. |

Default **`id`**, **`createdAt`**, **`updatedAt`**. **`sync()`** before listening.

---

## Step 5: Express and EJS

- **`app.set('view engine', 'ejs');`**
- **`app.use(express.static('public'));`**
- **`app.use(express.urlencoded({ extended: true }));`**
- Port **8080** or **`process.env.PORT`**.

---

## Step 6: Student Fields (`home.ejs`)

| Field            | Notes |
|------------------|--------|
| **Student ID**   | **`studentId`**. |
| **Student Name** | **`studentName`**. |
| **Program**      | **`<select name="program">`**, BTT / CAA / CPP + placeholder. |
| **GPA**          | **`gpa`**. |
| **Graduated?**   | **Checkbox** **`graduated`**. |

Use **`<label>`** for every control.

---

## Step 7: Routes

| Method | Path             | Behaviour |
|--------|------------------|-----------|
| GET    | `/`              | **`findAll`**, **`render('home', { data })`**. |
| POST   | `/addStudent`    | **`create`**, **`redirect('/')`**. |
| POST   | `/updateStudent` | Empty id fields → **`destroy`**; else **`update`**; **`redirect('/')`**. |

---

## Step 8: CSS

**`public/css/main.css`**: layout for instructions, row forms, add form.

---

## Step 9: Deployment to Vercel

Deploy to **Vercel**. Ensure the app can reach **Neon** (SSL, pooled host if Neon recommends it). Submit the **live Vercel URL**.

---

## Notes

- **Sequelize:** **`create`**, **`findAll`**, **`update`**, **`destroy`**, **`sync()`** as above.
- **Security:** Putting passwords in **`server.js`** is acceptable for this assignment if your instructor allows it; use a **private** repository if possible. For production systems, prefer environment variables on the host (e.g. Vercel env vars + **`process.env`**), still **without** the **`dotenv`** npm package.

---

## Assignment Submission

At the top of **`server.js`**:

```js
/**********************************************************************************
WEB700 – Assignment 06
I declare that this assignment is my own work in accordance with Seneca Academic Policy.
No part of this assignment has been copied manually or electronically from any other source
(including 3rd party web sites) or distributed to other students.
Name: ______________________
Student ID: _________________
Date: __________________
**********************************************************************************/
```

Submit: **`server.js`**, **`models/`** (if used), **`views/home.ejs`**, **`public/css/main.css`**, **`package.json`**, **`.gitignore`**, **Live Vercel URL**

---

## Checklist

- [ ] **Neon** database; **`Sequelize`** configured in **`server.js`** (no **`dotenv`** package).
- [ ] **`Student`** model + **`sync`** before listening.
- [ ] UI matches **[Relational-Database-Postgres](https://github.com/WPFoundations-Examples/Relational-Database-Postgres)** pattern: **`home.ejs`**, **`GET /`**, **`POST /addStudent`**, **`POST /updateStudent`**, **`data`**, **Add New** + **Update** forms.
- [ ] **Delete** = clear **`studentId`** and **`studentName`** + **Update**.
- [ ] Assignment 5–style fields + **labels**; EJS **iteration** / **conditionals**.
- [ ] **`main.css`** linked.
- [ ] **Live URL** submitted.
