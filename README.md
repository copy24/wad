# Node.js WAD Practicals — All Experiments

## ⚡ Installation & Run Commands

> **Prerequisites:** [Node.js](https://nodejs.org) and [MySQL](https://dev.mysql.com/downloads/) must be installed on your machine.

### Experiment 1 — Basic HTTP Server (No dependencies)
```cmd
cd "hehe exp 1"
node server.js
```

### Experiment 2 — Express Static Server
```cmd
cd "hehe exp 2"
npm install
node server.js
```

### Experiment 3 — CRUD with MySQL
```cmd
cd "hehe exp 3"
npm install
```
> First run the SQL file in MySQL: `source schema.sql` (sets up `studentdb`)
```cmd
node app.js
```

### Experiment 4 — User Registration & Login with Bcrypt
```cmd
cd "hehe exp 4"
npm install
```
> First run the SQL file in MySQL: `source schema.sql` (sets up `registration_db`)
```cmd
node server.js
```

### Experiment 5 — Secure Login (CSRF + Helmet + Validator)
```cmd
cd "hehe exp 5"
npm install
node app.js
```
> MySQL database `secure_node_app` with a `users` table (username, password) must exist.

### Experiment 6 — Session-based To-Do App (CRUD API)
```cmd
cd "hehe exp 6"
npm install
node server.js
```
> MySQL database `wad_crud` with `users` and `todos` tables must exist.

---

All experiments run at **http://localhost:3000** by default.

---

## 📖 Experiment Explanations

---

### Experiment 1 — Basic Node.js HTTP Server
This experiment demonstrates how to create a simple web server using Node.js's built-in `http` module without any third-party libraries. The server listens on port 3000 and responds to every request with a plain HTML page containing a heading and a paragraph. It covers the core concepts of `http.createServer()`, setting response headers with `res.writeHead()`, writing HTML with `res.write()`, and ending the response with `res.end()`. This is the foundation of understanding how HTTP works at the lowest level in Node.js before introducing frameworks like Express.

---

### Experiment 2 — Express.js Static File Server
This experiment introduces the Express.js framework and demonstrates how to serve static HTML files from a `public/` folder using `express.static()` middleware. Multiple routes (`/`, `/about`, `/hello`) are defined to handle different URL paths — some serving static files and one returning a plain text response. It shows the difference between `res.sendFile()` and `res.send()`, and how Express simplifies routing compared to raw Node.js. The experiment also uses a separate `app.js` for application logic and `server.js` as the entry point.

---

### Experiment 3 — Full CRUD Operations with MySQL
This experiment builds a complete CRUD (Create, Read, Update, Delete) web application that connects to a MySQL database (`studentdb`) using the `mysql2` library. User data (name, email, mobile, password) is managed through HTML forms and Express routes organized in a dedicated `routes/users.js` file, keeping the code modular. The database connection is abstracted into a `database.js` module that exports a promise-based connection. It uses `body-parser` middleware to parse form submissions and demonstrates the use of parameterized SQL queries (`?` placeholders) to safely insert, update, and delete records.

---

### Experiment 4 — User Registration & Login with Password Hashing
This experiment implements a user authentication system with registration and login functionality backed by a MySQL database (`registration_db`). Passwords are never stored in plain text — they are hashed using the `bcrypt` library before being saved. On login, `bcrypt.compare()` verifies the entered password against the stored hash. Sessions are managed with `express-session` to track logged-in users across requests and protect a `/dashboard` route. The EJS templating engine is used to render server-side HTML views, demonstrating a complete MVC-style web app structure.

---

### Experiment 5 — Secure Node.js App (CSRF + Helmet + Validation)
This experiment focuses on web security best practices for a Node.js login application. It uses `helmet` to set secure HTTP response headers that protect against common attacks like XSS and clickjacking. `express-validator` is used to sanitize and validate user inputs (username length, password minimum length) before any database query is executed. CSRF (Cross-Site Request Forgery) protection is added using `csrf-sync`, which generates and validates tokens on every form submission. The MySQL queries use parameterized placeholders to prevent SQL injection, and sessions are configured with `httpOnly` and `sameSite` cookie flags for added security.

---

### Experiment 6 — Session-based To-Do App with REST API
This experiment builds a session-authenticated To-Do application that exposes a RESTful JSON API (`/api/todos`) supporting all four CRUD operations — POST (create), GET (read), PUT (update), and DELETE (delete). Users must log in first; sessions are tracked with `express-session` and an `auth` middleware function guards every API route. The EJS templating engine renders the dashboard and to-do pages. Each to-do task belongs to the logged-in user (stored with `user_id` in the `todos` MySQL table), ensuring users can only access their own data. This experiment ties together sessions, REST API design, database-backed storage, and EJS views in a single full-stack application.

