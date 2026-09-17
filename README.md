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
  ```

The Client sends an HTTP request (fetch) to the Server's endpoint (/api/products).

The Server receives the request, processes it, and responds with data formatted as JSON.

The Client receives the JSON and uses it in the interface!

---

- **URL (Uniform Resource Locator)**: The unique web address used to identify and locate a specific resource (like a web page, file, or API endpoint) on the internet.

  **Structure of a URL**:
  `https://api.example.com:3000/v1/products?category=electronics#details`
  - **Protocol**: `https://` (How the client and server communicate)
  - **Domain / Host**: `api.example.com` (The server's name/address)
  - **Port**: `:3000` (The specific channel open on the server)
  - **Path / Endpoint**: `/v1/products` (The specific resource path)
  - **Query Parameters**: `?category=electronics` (Extra filter criteria)
  - **Anchor / Fragment**: `#details` (Points to a specific section on the page)

  ***
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

  ***

- **HTTPS (Hypertext Transfer Protocol Secure)**: The secure, encrypted version of HTTP that protects data sent between a client and a server using SSL/TLS protocols.

  **Why encryption matters**:
  - **HTTP (Unsecure)**: Data is sent as plain text 📄 (Anyone on the network can read it).
  - **HTTPS (Secure)**: Data is encrypted into unreadable ciphertext 🔐 (Only the client and server have the keys to decode it).

  **Key Benefits**:
  - 🛡️ **Security**: Protects sensitive user data (passwords, payment info).
  - 🔑 **Authentication**: Verifies that the server really belongs to the domain name.
  - 📈 **SEO & Trust**: Search engines prioritize HTTPS sites, and browsers display a lock icon 🔒.

  ***

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

  ***

- **CRUD (Create, Read, Update, Delete)**: The four fundamental operations performed on persistent data in a database or application backend.

  **Mapping CRUD to REST & HTTP**:
  - **C**reate ➕ ➔ `POST` (e.g., Creating a new user account)
  - **R**ead 📥 ➔ `GET` (e.g., Viewing a user's profile)
  - **U**pdate ✏️ ➔ `PUT` / `PATCH` (e.g., Changing your profile picture)
  - **D**elete 🗑️ ➔ `DELETE` (e.g., Deleting an account)

  ***

======================================================================================

## HTTP is the protocol, REST is the pattern/style, and CRUD is the database operation.

Here is how they align side-by-side:

| **HTTP Method** *CRUD Operation *REST Action** \*Real-World Analogy** 🛒
| :------------------ | :----------- | :------------------ | :---------------------------- |
| **`POST`** | **C**reate | Add a new resource | Submitting a new order |
| **`GET`** | **R**ead | Retrieve a resource | Looking at your shopping cart |
| **`PUT` / `PATCH`** | **U**pdate | Modify a resource | Changing the shipping address |
| **`DELETE`** | **D**elete | Remove a resource | Canceling the order |

======================================================================================

---

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
  ```

📖 Human-Readable: Easy for developers to inspect and debug.
🤖 Language Independent: Works seamlessly across Node.js, Python, Java, PHP, and modern web browsers.
⚡ Lightweight: Fast to transfer over HTTP networks.

---

In JSON, data is organized in key-value pairs, just like a word and its definition in a dictionary:

The key is the label or name (always in quotes on the left). 🔑
The value is the actual data stored inside that key (on the right). 📦

---

**Key-Value Pair Structure**:
| Key 🔑 | Value 📦 | Data Type |
| :--- | :--- | :--- |
| `"id"` | `101` | Number |
| `"productName"` | `"Wireless Mouse"` | Text (String) |
| `"inStock"` | `true` | Boolean (True/False) |
| `"tags"` | `["electronics", "accessories"]` | List (Array) |

---

---

- **ESM (ECMAScript Modules)**: The standard format for organizing and sharing reusable JavaScript code across multiple files using `import` and `export` syntax.

  **Code Example**:

  ```javascript
  // math.js - Exporting a function 📤
  export function add(a, b) {
    return a + b;
  }

  // app.js - Importing and using the function 📥
  import { add } from "./math.js";
  console.log(add(2, 3)); // 5
  ```

---

- **CommonJS (CJS)**: The original module system used in Node.js to import and export code between files using `require()` and `module.exports`.

  **Code Example**:

  ```javascript
  // math.js - Exporting a function 📤
  function add(a, b) {
    return a + b;
  }
  module.exports = { add };

  // app.js - Importing the function 📥
  const { add } = require("./math.js");
  console.log(add(2, 3)); // 5
  ```

================
CommonJS vs. ESM:

📜 CommonJS: Uses require() and module.exports (Synchronous loading).
⚡ ESM: Uses import and export (Asynchronous loading, modern web standard).
===============

---

- **NPM (Node Package Manager)**: The default package manager for Node.js, consisting of a command-line tool and an online registry of open-source JavaScript packages.

  **Core Files & Commands**:
  - `package.json` 📄: The manifest file that lists your project's details, scripts, and installed dependencies.
  - `package-lock.json` 🔒: Records the exact versions of every installed package to ensure consistent builds across environments.
  - `node_modules/` 📁: The folder where NPM downloads and stores all the third-party library files.

  **Essential Commands**:
  - `npm init -y`: Initializes a new Node.js project and creates a `package.json` file.
  - `npm install <package-name>`: Downloads a package (e.g., `npm install express`) and saves it to your dependencies.
  - `npm start`: Runs the start script defined in your `package.json`.

  ***

- **REPL (Read-Eval-Print Loop)**: An interactive programming environment that takes individual user inputs, executes them, and returns the result to the user.

  **The 4 Phases**:
  - 📖 **Read**: Takes JavaScript code entered by the user.
  - ⚙️ **Eval**: Evaluates/executes the code.
  - 🖨️ **Print**: Prints the output to the console.
  - 🔄 **Loop**: Waits for the next command.

  **How to access in Node.js**:
  Type `node` in your terminal to start the REPL, and press `Ctrl + C` twice to exit.

  ***

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
SELECT \* FROM users; is the query (the exact message sent to get those profiles).

### 🔄 How HTTP, CRUD, REST, and SQL Work Together

| **CRUD Operation** 🧰 | **HTTP Method** 🌐  | **REST Action** 🏗️  | **SQL Command** 🗄️    | **Real-World Analogy** 🛒     |
| :-------------------- | :------------------ | :------------------ | :-------------------- | :---------------------------- |
| **C**reate            | **`POST`**          | Add a new resource  | `INSERT INTO ...`     | Submitting a new order        |
| **R**ead              | **`GET`**           | Retrieve a resource | `SELECT ... FROM ...` | Looking at your shopping cart |
| **U**pdate            | \*_`PUT` / `PATCH`_ | Modify a resource   | `UPDATE ... SET ...`  | Changing the shipping address |
| **D**elete            | **`DELETE`**        | Remove a resource   | `DELETE FROM ...`     | Canceling the order           |

---

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

  ***

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

  ***

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
    age: Number,
  });

  const User = mongoose.model("User", userSchema);

  // Creating a new document 📝
  await User.create({ name: "Alice", email: "alice@example.com", age: 25 });
  ```

---

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

---

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

  ***

- **PK (Primary Key)**: A column (or set of columns) in a relational database table that uniquely identifies each row or record.

What it means in simple terms: A Primary Key is a unique identifier 🆔 for a specific row
in a database table. Just like a Social Security Number, a student ID, or a driver's
license number, no two rows in the same table can ever have the exact same Primary Key.

In backend development: Every main table in a relational database needs a Primary Key so
your backend code can pinpoint, retrieve, update, or delete one specific record
without affecting any others.

**Core Rules**:

- 🚫 **Unique**: No two rows can share the same Primary Key value.
- ❌ **Non-Null**: A Primary Key can never be empty or `NULL`.
- ☝️ **One Per Table**: Each table can have only one Primary Key constraint.

**Common Primary Key Types**:

- 🔢 **Auto-incrementing Integer**: Simple sequential numbers (e.g., `1`, `2`, `3`).
- 🆔 **UUID (Universally Unique Identifier)**: Standardized 128-bit random strings
  (e.g., `123e4567-e89b-12d3-a456-426614174000`) used to prevent predictable IDs in public web links.

---

- **FK (Foreign Key)**: A column (or group of columns) in one table that references
  the Primary Key of another table, establishing a link between the data in both tables.

What it means in simple terms: A Foreign Key is a column in one table that
links directly to the Primary Key of another table 🤝. It creates a formal
relationship between two tables, acting as a pointer to keep your data organized and connected.

In backend development: Foreign Keys ensure referential integrity 🛡️.
This means you cannot create a record that points to a non-existent record
in another table (e.g., creating an order for a user_id that does not exist),
and it prevents referenced data from accidentally being deleted.

**Key Rules**:

- 🔗 **Establishes Relationships**: Links child records (e.g., `orders`) to parent records (e.g., `users`).
- 🛡️ **Referential Integrity**: Prevents "orphan" records by ensuring a Foreign Key value must match an existing Primary Key in the referenced table.
- 🔄 **Cascading Actions**: Can be configured to automatically handle deletes or updates (e.g., `ON DELETE CASCADE` removes all orders if the parent user account is deleted).

**Example Structure**:

- `users` table ➔ `id` (Primary Key: `101`)
- `orders` table ➔ `id` (Primary Key: `1`), `user_id` (Foreign Key: `101`)

---

- **Database Normalization (1NF, 2NF, 3NF)**: A systematic approach to structuring
  relational database schemas to eliminate redundant data and ensure logical data dependencies.

What it means in simple terms: Normalization is the process of organizing data in a
relational database 🗄️ to reduce redundant (duplicated) data and improve data integrity.
It follows a series of rules called "Normal Forms" (1NF, 2NF, 3NF). its like organizing a closet:
instead of throwing everything into one big messy pile, you sort items into specific
drawers so every item has a single, logical place.

In backend development: Properly normalized databases prevent data anomalies—like
updating a user's address in one row but forgetting to update it in another row.

**The First Three Normal Forms**:

- 1️⃣ **1NF (First Normal Form)**: **Atomic Values** ⚛️ — Each cell must contain a single, indivisible value, and there can be no repeating groups or lists in a single field.
- 2️⃣ **2NF (Second Normal Form)**: **Full Functional Dependency** 🔗 — Must be in 1NF, and all non-key columns must depend on the _entire_ Primary Key (eliminates partial dependencies when using composite keys).
- 3️⃣ **3NF (Third Normal Form)**: **No Transitive Dependency** 🚫 — Must be in 2NF, and non-key columns must depend _only_ on the Primary Key, not on other non-key columns ("no fields depend on non-key fields").

---

- **JWT (JSON Web Token)**: An open standard (RFC 7519) that defines a compact,
  self-contained way to securely transmit information between parties as a JSON object,
  commonly used for authentication and authorization.

What it means in simple terms: A JSON Web Token is a compact, digitally signed token 🎟️
used to securely share information between a client (like a browser) and a server. It is
like a digital event wristband 🎟️: once you log in and receive it, you show that wristband
on every future request to prove who you are without having to type your password again.

In backend development: JWTs are widely used for stateless authentication 🔐.
Instead of keeping session data on the server's database, the server encodes the user's ID
into a token, signs it with a secret key, and sends it to the client.
The client sends this token back in the Authorization header for protected API routes.

**The 3 Parts of a JWT** (Separated by dots `.`):

- 🔴 **Header**: Specifies the algorithm used to sign the token (e.g., `HS256`).
- 🟡 **Payload**: Contains the claims/data (e.g., `userId`, `role`, expiration time `exp`).
- 🔵 **Signature**: Created by combining the encoded header, payload, and a secret key to verify the sender and ensure the data wasn't tampered with.

**How Authentication Works**:

1. 🔑 **Login**: User submits credentials to the server.
2. 🎟️ **Issue**: Server verifies credentials and returns a signed JWT.
3. 📦 **Store**: Client stores the JWT (e.g., in `localStorage` or an `httpOnly` cookie).
4. 🚀 **Request**: Client sends the JWT in the `Authorization: Bearer <token>` header for subsequent API calls.

======================================================================================

### 🪙 JWT Code Example (Express.js)

======================================================================================

```javascript
const express = require('express');
const jwt = require('jsonwebtoken');

const app = express();
app.use(express.json());

const SECRET_KEY = 'your-secret-key-keep-it-safe'; 🔒

// 1. LOGIN ROUTE: Generating the JWT 🎟️
app.post('/login', (req, res) => {
  const { username, password } = req.body;

  // Verify credentials against database 🗄️
  if (username === 'alice' && password === 'password123') {
    const userPayload = { userId: 101, username: 'alice', role: 'admin' };

    // Sign and issue token (expires in 1 hour) ✍️
    const token = jwt.sign(userPayload, SECRET_KEY, { expiresIn: '1h' });
    return res.json({ message: 'Login successful!', token });
  }

  res.status(401).json({ error: 'Invalid credentials' });
});

// 2. MIDDLEWARE: Verifying the JWT 🛡️
function authenticateToken(req, res, next) {
  const authHeader = req.headers['authorization'];
  const token = authHeader && authHeader.split(' ')[1]; // Extract "Bearer <TOKEN>"

  if (!token) return res.status(401).json({ error: 'Access denied: No token provided' });

  jwt.verify(token, SECRET_KEY, (err, decodedUser) => {
    if (err) return res.status(403).json({ error: 'Invalid or expired token' });

    req.user = decodedUser; // Attach payload to the request object 👤
    next();
  });
}

// 3. PROTECTED ROUTE: Requires valid JWT 🔒
app.get('/dashboard', authenticateToken, (req, res) => {
  res.json({ message: `Welcome to your dashboard, ${req.user.username}!` });
});


`======================================================================================
---------------------------------------------------------------------------------------

`- **MFA (Multi-Factor Authentication)**: An electronic authentication method that grants
access to a website or application only after a user successfully presents two or more
pieces of evidence (or factors) to an authentication mechanism.

  **The 3 Common Authentication Factors**:
  - 🧠 **Knowledge (Something you know)**: Passwords, PINs, or security questions.
  - 📱 **Possession (Something you have)**: An authenticator app (e.g., Google Authenticator), security key, or SMS code.
  - 🧬 **Inherence (Something you are)**: Biometrics like fingerprints, facial recognition, or iris scans.

  **Key Benefits**:
  - 🛡️ **Enhanced Security**: Drastically reduces the risk of account compromise from leaked or weak passwords.
  - 🔒 **Defense-in-Depth**: A stolen password alone is not enough to gain access.

`-------------------------------------------------------------------------------------

- **2FA (Two-Factor Authentication)**: A specific type of Multi-Factor Authentication 
(MFA) that requires exactly two different security factors to verify a user's identity.

  **MFA vs. 2FA**:
  - ✌️ **2FA**: Always uses **exactly 2** factors (e.g., Password + SMS Code).
  - 🛡️ **MFA**: Uses **2 or more** factors (e.g., Password + Hardware Key + Fingerprint Scan).

  **Common 2FA Combinations**:
  - 🔑 **Password** (Factor 1: Knowledge) + 📱 **Authenticator App Code** (Factor 2: Possession)
  - 🔑 **Password** (Factor 1: Knowledge) + 👆 **Fingerprint Scan** (Factor 2: Inherence)

------------------------------------------------------------------------------------`

- **TOTP (Time-based One-Time Password)**: An extension of the HOTP (HMAC-based One-Time Password) 
algorithm that generates a unique, short-lived passcode by combining a shared secret key with the current time.

What it means in simple terms: TOTP is a temporary, 6-digit passcode generated by an 
authenticator app (like Google Authenticator or 1Password). It automatically recalculates 
and changes every 30 seconds.

In backend development: TOTP relies on a shared secret key (stored in the database and 
scanned via QR code) combined with the current UNIX timestamp. 
Both the client app and the server run the exact same cryptographic formula (HMAC-SHA1) 
to generate identical codes without transmitting the secret key over the network.

  **Core Characteristics**:
  - ⏳ **Short Lifetime**: Typically valid for only 30 seconds to prevent replay attacks.
  - 🌐 **Offline Generation**: Authenticator apps can generate valid codes even without internet access because generation relies strictly on the current clock time.
  - 🔐 **Shared Secret**: The QR code scanned during setup contains a secret key shared exclusively between the client device and the backend database.

`-----------------------------------------------------------------------------------

- - **OAuth 2.0**: An open authorization framework that allows applications to secure 
limited access to user accounts on an HTTP service (e.g., Google, GitHub) without exposing user credentials.

What it means in simple terms: OAuth 2.0 is an industry-standard protocol for 
delegated authorization 🤝. It allows a user to grant a third-party application 
limited access to their resources (like their contacts or profile info) without 
giving that application their password! It is like a hotel key card 🗝️: the front 
desk gives you a card that unlocks your room for two days, but it isn't the master key to the whole building.

In backend development: You use OAuth 2.0 when implementing features like "Log in with Google,
" "Log in with GitHub," or when granting access to external APIs. Instead of storing passwords, 
your backend exchanges an authorization code for an Access Token from an Identity Provider (IdP).

  **Core Roles**:
  - 👤 **Resource Owner**: The user who owns the data.
  - 🌐 **Client**: The application requesting access to the user's data.
  - 🔐 **Authorization Server**: The server that authenticates the user and issues access tokens (e.g., Google OAuth server).
  - 🗄️ **Resource Server**: The API hosting the protected user data.

  **Common Flow (Authorization Code Grant)**:
  1. 👈 User clicks "Login with Google".
  2. 🔀 User is redirected to Google to approve access.
  3. 🎟️ Google sends an **Authorization Code** back to the backend.
  4. 🔄 Backend exchanges the code for an **Access Token**.
  5. 🚀 Backend fetches user profile using the Access Token.
  
  ------------------------------------------------------------------------------------

- **OIDC (OpenID Connect)**: An identity layer built on top of the OAuth 2.0 framework that enables clients to verify the identity of an end-user based on authentication performed by an Authorization Server.

What it means in simple terms: OpenID Connect is an identity layer built right on top 
of OAuth 2.0 🏗️. While OAuth 2.0 is purely about authorization (granting permission 
to access data), OIDC adds authentication (verifying who the user is).
OAuth 2.0 as giving someone a keycard to a hotel room 🔑, and OIDC as adding an ID 
badge 💳 that confirms their name and profile photo.

In backend development: OIDC introduces a standardized JWT called an ID Token alongside the standard OAuth 2.0 Access Token. This ID Token contains profile information about the user (like their name, email, and user ID), making single sign-on (SSO) standardized across different platforms.

  **OAuth 2.0 vs. OIDC**:
  - 🔓 **OAuth 2.0**: Handles **Authorization** ("What resources can this application access?"). Issues an **Access Token**.
  - 🆔 **OIDC**: Handles **Authentication** ("Who is the user currently logged in?"). Issues an **ID Token** (a JWT) + Access Token.

  **Key Features**:
  - 🪙 **ID Token**: A signed JWT containing user profile claims (e.g., `sub`, `email`, `name`).
  - 🔗 **Standardized UserInfo Endpoint**: A standard API path to fetch additional profile details using the Access Token.
  - 🔐 **Single Sign-On (SSO)**: Allows users to log into multiple applications using one central identity provider (e.g., Okta, Auth0, Google).

---------------------------------------------------

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
```
