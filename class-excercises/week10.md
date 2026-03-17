# Week 10 — In-Class Exercise: Template Engines

Use the course material to create an Express website using **EJS** as the template engine.

---

## Requirements

### 1. Three pages

| Route       | Template        |
|------------|------------------|
| `/`        | `home.html`      |
| `/about`   | `about.html`     |
| `/viewData`| `viewData.ejs`   |

### 2. Page content

- **Home** (`home.html`): Display the text **"Welcome to this website"** inside an `<h1>` tag.
- **About** (`about.html`): Display the text **"About me"** inside an `<h1>` tag.
- **View Data** (`viewData.ejs`): Display the product data below in **table format**.

### 3. Product data (for `/viewData`)

Use the following array and render it in a table. Columns: **type**, **model**, **price**, **condition**.

```javascript
[
  {
    type: 'Laptop',
    model: 'MacBook Pro 14"',
    price: 2499,
    condition: 'New',
  },
  {
    type: 'Phone',
    model: 'iPhone 15 Pro',
    price: 1199,
    condition: 'Refurbished',
  },
  {
    type: 'Laptop',
    model: 'Dell XPS 15',
    price: 1899,
    condition: 'Like New',
  },
]
```

### 4. Navigation

- Include a **header** (navigation) on each page.
- Make the font **bold** for the link that corresponds to the **current page**, following the course material.

### 5. Push to Git and deploy to Vercel

- Create a **new Git repository** (on your personal GitHub account, not the Seneca one) and push your project to it.
- **Deploy** the project to **Vercel**
