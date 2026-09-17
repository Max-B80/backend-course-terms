# Course Terms and Abbreviations

This overview collects the central terms, abbreviations, and principles from the backend course from Week 1 through September 15, 2026. Research their meanings yourself and add your own notes.

## Abbreviations

- **API (Application Programming Interface)**: A set of rules and protocols that allows different software applications to communicate and share data with each other (like a bridge between a frontend client and a backend server).

  **Example**: How two applications communicate using Node.js/Express and `fetch`:

  ```javascript
  // 1. The Backend (Express Server App)
  import express from 'express';
  const app = express();

  // Endpoint where data is exposed
  app.get('/api/products', (req, res) => {
    res.json([
      { id: 1, name: 'Laptop' },
      { id: 2, name: 'Phone' }
    ]);
  });

  app.listen(3000);

  // 2. The Frontend (Client App)
  // Requesting data from the server's API endpoint
  fetch('http://localhost:3000/api/products')
    .then(response => response.json())
    .then(data => console.log(data));

    How they talk:

The Client sends an HTTP request (fetch) to the Server's endpoint (/api/products).

The Server receives the request, processes it, and responds with data formatted as JSON.

The Client receives the JSON and uses it in the interface!

----------------------------------------------------------------------------------------

- **URL (Uniform Resource Locator)**: The unique web address used to identify and locate a specific resource (like a web page, file, or API endpoint) on the internet.

  **Structure of a URL**:
  `https://api.example.com:3000/v1/products?category=electronics#details`

  - **Protocol**: `https://` (How the client and server communicate)
  - **Domain / Host**: `api.example.com` (The server's name/address)
  - **Port**: `:3000` (The specific channel open on the server)
  - **Path / Endpoint**: `/v1/products` (The specific resource path)
  - **Query Parameters**: `?category=electronics` (Extra filter criteria)
  - **Anchor / Fragment**: `#details` (Points to a specific section on the page)
  
  --------------------------------------------------------------------------------------

  - **HTTP (Hypertext Transfer Protocol)**: The foundational protocol used for transmitting data across the web, enabling communication between clients (e.g., browsers) and servers.

  **Common HTTP Methods**:
  - `GET`: Retrieve data from a server 📥
  - `POST`: Send new data to a server 📤
  - `PUT` / `PATCH`: Update existing data on a server ✏️
  - `DELETE`: Remove data from a server 🗑️

  **Common HTTP Status Codes**:
  - `200 OK`: Request succeeded 🎉
  - `201 Created`: Resource successfully created ✨
  - `400 Bad Request`: Client sent invalid data ❌
  - `404 Not Found`: Resource does not exist 🔍
  - `500 Internal Server Error`: Something went wrong on the server 💥

  ------------------------------------------------------------------------------------

- **HTTPS (Hypertext Transfer Protocol Secure)**: The secure, encrypted version of HTTP that protects data sent between a client and a server using SSL/TLS protocols.

  **Why encryption matters**:
  - **HTTP (Unsecure)**: Data is sent as plain text 📄 (Anyone on the network can read it).
  - **HTTPS (Secure)**: Data is encrypted into unreadable ciphertext 🔐 (Only the client and server have the keys to decode it).

  **Key Benefits**:
  - 🛡️ **Security**: Protects sensitive user data (passwords, payment info).
  - 🔑 **Authentication**: Verifies that the server really belongs to the domain name.
  - 📈 **SEO & Trust**: Search engines prioritize HTTPS sites, and browsers display a lock icon 🔒.

  ------------------------------------------------------------------------------------

- **REST (Representational State Transfer)**: An architectural style for designing networked applications, using standard HTTP methods to perform CRUD operations on resources via predictable URL endpoints.

  **Core CRUD Operations & HTTP Verbs**:
  - **Create**: `POST /api/products` (Add a new item) 📤
  - **Read**: `GET /api/products` (Fetch all items) or `GET /api/products/123` (Fetch item 123) 📥
  - **Update**: `PUT /api/products/123` (Replace item) or `PATCH /api/products/123` (Modify part of item) ✏️
  - **Delete**: `DELETE /api/products/123` (Remove item) 🗑️

  **Key Principles**:
  - 🌐 **Stateless**: The server does not store client session state between requests; every request must contain all necessary information.
  - 🏷️ **Resource-Based**: URLs identify nouns/resources (e.g., `/users`), not actions (e.g., `/getUsers`).
  - 📦 **Standardized Responses**: Data is usually exchanged in **JSON** format.

  ------------------------------------------------------------------------------------

- **CRUD (Create, Read, Update, Delete)**: The four fundamental operations performed on persistent data in a database or application backend.

  **Mapping CRUD to REST & HTTP**:
  - **C**reate ➕ ➔ `POST` (e.g., Creating a new user account)
  - **R**ead 📥 ➔ `GET` (e.g., Viewing a user's profile)
  - **U**pdate ✏️ ➔ `PUT` / `PATCH` (e.g., Changing your profile picture)
  - **D**elete 🗑️ ➔ `DELETE` (e.g., Deleting an account)

  ------------------------------------------------------------------------------------

======================================================================================
  ## HTTP is the protocol, REST is the pattern/style, and CRUD is the database operation.
  Here is how they align side-by-side:


| **HTTP Method**     *CRUD Operation   *REST Action**      *Real-World Analogy** 🛒 
| :------------------ | :----------- | :------------------ | :---------------------------- |
| **`POST`**          | **C**reate   | Add a new resource  | Submitting a new order        |
| **`GET`**           | **R**ead     | Retrieve a resource | Looking at your shopping cart |
| **`PUT` / `PATCH`** | **U**pdate   | Modify a resource   | Changing the shipping address |
| **`DELETE`**        | **D**elete   | Remove a resource   | Canceling the order           |
  
======================================================================================

--------------------------------------------------------------------------------------

- **JSON (JavaScript Object Notation)**: A lightweight, text-based data format used to transmit data between a server and a web application in readable key-value pairs.

  **Example JSON Object**:
  ```json
  {
    "id": 101,
    "productName": "Wireless Mouse",
    "inStock": true,
    "tags": ["electronics", "accessories"]
  }

  Key Features:

📖 Human-Readable: Easy for developers to inspect and debug.
🤖 Language Independent: Works seamlessly across Node.js, Python, Java, PHP, and modern web browsers.
⚡ Lightweight: Fast to transfer over HTTP networks.

------
In JSON, data is organized in key-value pairs, just like a word and its definition in a dictionary:

The key is the label or name (always in quotes on the left). 🔑
The value is the actual data stored inside that key (on the right). 📦
------

**Key-Value Pair Structure**:
  | Key 🔑          | Value 📦                         | Data Type            |
  | :---            | :---                             | :---                 |
  | `"id"`          | `101`                            | Number               |
  | `"productName"` | `"Wireless Mouse"`               | Text (String)        |
  | `"inStock"`     | `true`                           | Boolean (True/False) |
  | `"tags"`        | `["electronics", "accessories"]` | List (Array)         |

------
------------------------------------------------------------------------------------

- **ESM (ECMAScript Modules)**: The standard format for organizing and sharing reusable JavaScript code across multiple files using `import` and `export` syntax.

  **Code Example**:
  ```javascript
  // math.js - Exporting a function 📤
  export function add(a, b) {
    return a + b;
  }

  // app.js - Importing and using the function 📥
  import { add } from './math.js';
  console.log(add(2, 3)); // 5

------------------------------------------------------------------------------------

- **CommonJS (CJS)**: The original module system used in Node.js to import and export code between files using `require()` and `module.exports`.

  **Code Example**:
  ```javascript
  // math.js - Exporting a function 📤
  function add(a, b) {
    return a + b;
  }
  module.exports = { add };

  // app.js - Importing the function 📥
  const { add } = require('./math.js');
  console.log(add(2, 3)); // 5

================
CommonJS vs. ESM:

📜 CommonJS: Uses require() and module.exports (Synchronous loading).
⚡ ESM: Uses import and export (Asynchronous loading, modern web standard).
===============
------------------------------------------------------------------------------------

- **NPM (Node Package Manager)**: The default package manager for Node.js, consisting of a command-line tool and an online registry of open-source JavaScript packages.

  **Core Files & Commands**:
  - `package.json` 📄: The manifest file that lists your project's details, scripts, and installed dependencies.
  - `package-lock.json` 🔒: Records the exact versions of every installed package to ensure consistent builds across environments.
  - `node_modules/` 📁: The folder where NPM downloads and stores all the third-party library files.

  **Essential Commands**:
  - `npm init -y`: Initializes a new Node.js project and creates a `package.json` file.
  - `npm install <package-name>`: Downloads a package (e.g., `npm install express`) and saves it to your dependencies.
  - `npm start`: Runs the start script defined in your `package.json`.

  ---------------------------------------------------------------------------------


- **REPL (Read-Eval-Print Loop)**: An interactive programming environment that takes individual user inputs, executes them, and returns the result to the user.

  **The 4 Phases**:
  - 📖 **Read**: Takes JavaScript code entered by the user.
  - ⚙️ **Eval**: Evaluates/executes the code.
  - 🖨️ **Print**: Prints the output to the console.
  - 🔄 **Loop**: Waits for the next command.

  **How to access in Node.js**:
  Type `node` in your terminal to start the REPL, and press `Ctrl + C` twice to exit.

  ---------------------------------------------------------------------------------


- **SQL (Structured Query Language)**: The standard domain-specific language used to manage, query, and manipulate data stored in relational databases.

  **Common SQL Commands mapped to CRUD**:
  - **Create** ➕ ➔ `INSERT INTO users (name) VALUES ('Alice');`
  - **Read** 📥 ➔ `SELECT * FROM users WHERE id = 1;`
  - **Update** ✏️ ➔ `UPDATE users SET name = 'Bob' WHERE id = 1;`
  - **Delete** 🗑️ ➔ `DELETE FROM users WHERE id = 1;`

  **Popular SQL Databases**:
  - 🐘 **PostgreSQL**: Feature-rich, highly reliable open-source database.
  - 🐬 **MySQL**: Extremely popular, widely used across web applications.
  - 🪶 **SQLite**: Lightweight, file-based database often used for mobile or testing.

  How SQL Queries Perform CRUD 🔄
CRUD is just a concept—it describes the four actions you want to take on data. A SQL Query is the actual command you write in code to make that action happen in the database!

CRUD is the goal (e.g., "I want to Read user profiles").
SQL is the tool (the query language).
SELECT * FROM users; is the query (the exact message sent to get those profiles).

### 🔄 How HTTP, CRUD, REST, and SQL Work Together

| **CRUD Operation** 🧰 | **HTTP Method** 🌐 | **REST Action** 🏗️  | **SQL Command** 🗄️    | **Real-World Analogy** 🛒     |
| :-------------------- | :----------------- | :------------------ | :-------------------- | :--------------------------
| **C**reate            | **`POST`**         | Add a new resource  | `INSERT INTO ...`     | Submitting a new order        |
| **R**ead              | **`GET`**          | Retrieve a resource | `SELECT ... FROM ...` | Looking at your shopping cart |
| **U**pdate            | **`PUT` / `PATCH`* | Modify a resource   | `UPDATE ... SET ...`  | Changing the shipping address |
| **D**elete            | **`DELETE`**       | Remove a resource   | `DELETE FROM ...`     | Canceling the order           |


  ---------------------------------------------------------------------------------


  What it means in simple terms: NoSQL refers to a family of non-relational databases 🗃️ that store data in formats other than traditional tables with rigid rows and columns. Instead of fixed schemas, NoSQL databases often store information as flexible JSON-like documents 📄, key-value pairs, or graphs.

    In backend development: NoSQL databases are popular for modern web apps because they allow you to change your data structure on the fly without running complex database migrations. They are great for scaling quickly, handling massive amounts of unstructured data, or working directly with JSON objects.  
---
- **NoSQL (Not Only SQL)**: A broad category of database management systems that store 
    and retrieve data using non-relational models (such as document, key-value, or graph structures) without fixed schemas.

  **Key Features**:
  - 🔓 **Flexible Schema**: Documents can have different structures without breaking the database.
  - ⚡ **High Scalability**: Designed to easily scale horizontally across multiple servers.
  - 📦 **JSON-Friendly**: Data is naturally stored and queried using JSON-like formats.

  **Popular NoSQL Database Types**:
  - 📄 **Document Databases**: Stores data in JSON-like documents (e.g., **MongoDB** 🍃).
  - 🔑 **Key-Value Stores**: Super-fast in-memory caching (e.g., **Redis** 🔴).
  - 🕸️ **Graph Databases**: Manages highly connected network data (e.g., **Neo4j** 🟢).

  ---------------------------------------------------------------------------------

- **ORM (Object-Relational Mapping)**: A programming technique and library that maps
     database tables to code objects, allowing developers to query and manipulate data using their native programming language instead of writing raw SQL.

  **Code Comparison**:
  - 🗄️ **Raw SQL**: `SELECT * FROM users WHERE age > 18;`
  - 💻 **ORM (e.g., Prisma / Sequelize)**: `await User.findMany({ where: { age: { gt: 18 } } });`

  **Pros and Cons**:
  - ✅ **Speed & Safety**: Faster to write, easier to maintain, and helps prevent SQL injection security flaws.
  - ❌ **Performance Overhead**: Can generate inefficient SQL queries behind the scenes for very complex data operations.

  **Popular ORMs**:
  - 💎 **Prisma**: Modern, type-safe ORM popular in the Node.js / TypeScript ecosystem.
  - 🔷 **Sequelize**: Traditional, widely used promise-based Node.js ORM.
  - 🐍 **SQLAlchemy**: Standard ORM choice for Python backends.

  --------------------------------------------------------------------------------

- **ODM (Object-Document Mapper)**: A library that translates between JavaScript 
    objects and document-based NoSQL databases (like MongoDB), allowing developers 
    to define schemas and manage data using native code.

  **ORM vs. ODM**:
  - 🗄️ **ORM**: Maps code objects ➔ **SQL Relational Tables** (Rows & Columns).
  - 📄 **ODM**: Maps code objects ➔ **NoSQL Documents** (JSON-like objects).

  **Code Example (Mongoose)**:
  ```javascript
  // Defining a schema 📐
  const userSchema = new mongoose.Schema({
    name: String,
    email: String,
    age: Number
  });

  const User = mongoose.model('User', userSchema);

  // Creating a new document 📝
  await User.create({ name: 'Alice', email: 'alice@example.com', age: 25 });

--------------------------------------------------------------------------------


- **ACID (Atomicity, Consistency, Isolation, Durability)**: A set of four properties 
that guarantee database transactions are processed reliably, preserving data 
integrity even in the event of errors or system crashes.

What it means in simple terms: ACID is a set of four fundamental rules 🛡️ that 
guarantee database transactions are processed reliably. A transaction is a group 
of database operations that must be treated as a single unit. Think of ACID like 
a bank transfer: if money leaves account A, it must arrive in account B, or the 
entire operation is canceled so no money vanishes into thin air.

In backend development: SQL databases (like PostgreSQL and MySQL) follow ACID properties 
strictly to ensure data integrity, even during power outages, crashes, or when thousands 
of users write data simultaneously.

  **The 4 Pillars**:
  - ⚛️ **Atomicity ("All or Nothing")**: The whole transaction succeeds, or the entire thing rolls back (fails). No partial updates.
  - 🔄 **Consistency**: Data must transition from one valid state to another, strictly following all schema rules and constraints.
  - 🔒 **Isolation**: Concurrent transactions execute independently without interfering with each other.
  - 💾 **Durability**: Once a transaction is committed, its changes are permanently saved—even if the power goes out immediately after.

  ------------------------------------------------------------------------------

- **MVCC (Multi-Version Concurrency Control)**: A database concurrency control method 
that allows multiple transactions to read and write to the same data simultaneously 
by maintaining multiple historical versions of the data.


  **Key Benefits**:
  - 🚀 **High Performance**: Readers never block writers, and writers never block readers.
  - 🔒 **Consistency**: Each transaction sees a consistent snapshot of the data at a single point in time.

  **How it Works**:
  - **Reads** 📖: Fetch an older, stable version of the data.
  - **Writes** ✍️: Create a new version of the data without overwriting the old one immediately.
  - **Cleanup** 🧹: Unused older versions are automatically removed later (e.g., PostgreSQL's Garbage Collection / VACUUM).
  -----------------------------------------------------------------------------
- PK
- FK
- 1NF, 2NF, 3NF
- JWT
- MFA
- 2FA
- TOTP
- OAuth 2.0
- OIDC
- SSO
- CSRF
- XSS
- CORS
- OWASP
- SDK
- SaaS
- DBMS

## Week 1: Node.js, npm, and Express Fundamentals

- Node.js
- Backend
- Client-server model
- Event Loop
- Asynchronous programming
- Module
- `package.json`
- `package-lock.json`
- `dependencies`
- `devDependencies`
- `node_modules`
- Semantic versioning
- Express.js
- Middleware
- Route
- Handler
- Static route
- Dynamic route
- Route parameters
- Query parameters
- `req`
- `res`
- `next()`
- `next(err)`
- JSON middleware

## HTTP, APIs, and CRUD

- Request
- Response
- HTTP method
- Endpoint
- Request body
- Header
- Status code
- `200 OK`
- `201 Created`
- `204 No Content`
- `400 Bad Request`
- `401 Unauthorized`
- `403 Forbidden`
- `404 Not Found`
- `500 Internal Server Error`
- REST resource
- `PUT`
- `PATCH`
- 404 fallback
- Central error handling
- In-memory storage
- Postman
- Pre-request
- Response test

## Databases and Data Models

- Database
- Database server
- Relational database
- Table
- Row / record
- Column
- Data type
- PostgreSQL
- Postgres
- `psql`
- pgAdmin
- MongoDB
- MongoDB Atlas
- Document
- Collection
- Mongoose
- Schema
- Model
- Relation
- One-to-many
- Normalization
- Constraint
- `PRIMARY KEY`
- `FOREIGN KEY`
- `UNIQUE`
- `NOT NULL`
- `CHECK`
- `DEFAULT`
- Index
- SQL query
- `CREATE DATABASE`
- `CREATE TABLE`
- `INSERT`
- `SELECT`
- `WHERE`
- JOIN
- Transaction
- Rollback
- JSONB
- Prisma
- Prisma Schema
- Prisma Client
- Prisma Migrate
- Query Builder
- Drizzle

## Authentication and Sessions

- Authentication
- Authorization
- Identity
- Password hash
- Salt
- Hashing
- Argon2id, scrypt, bcrypt
- Brute force
- Credential stuffing
- Phishing
- Session
- Session ID
- Session store
- Cookie
- Session cookie
- `HttpOnly`
- `Secure`
- `SameSite`
- Session fixation
- Session hijacking
- Session regeneration
- Session timeout
- Sliding expiration
- Bearer token
- Passkey
- WebAuthn
- Clerk
- Auth-as-a-Service
- Vendor lock-in

## JWT and Token Security

- JWT header
- JWT payload
- Claim
- JWT signature
- Base64URL
- JWS
- `HS256`
- `RS256`
- `sub`
- `iss`
- `aud`
- `exp`
- `nbf`
- `iat`
- `jti`
- `jsonwebtoken`
- `jwt.sign()`
- `jwt.verify()`
- `jwt.decode()`
- Refresh token
- Token rotation
- Token revocation

## API Security and CORS

- Attack surface
- Input validation
- Parsing
- Normalization
- Allowlist / whitelist
- Denylist / blacklist
- Injection
- SQL injection
- NoSQL injection
- Command injection
- Broken Object Level Authorization
- Broken Object Property Level Authorization
- Mass assignment
- Data minimization
- Rate limiting
- Unrestricted resource consumption
- Security misconfiguration
- Same-origin principle
- Origin
- Cross-origin request
- CORS headers
- Preflight
- `Access-Control-Allow-Origin`
- `Access-Control-Allow-Methods`
- `Access-Control-Allow-Headers`
- HTTPS/TLS
- Logging
- Monitoring
- Deny by default
- Never trust the client
