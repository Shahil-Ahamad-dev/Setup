## Setting Up Node.js and Express.js in VS Code

## Prerequisites

Before getting started, ensure you have the following installed:

- [Node.js](https://nodejs.org/) (LTS version recommended)
- [Visual Studio Code](https://code.visualstudio.com/)

---

## Table of Contents

1. [Setting Up Node.js and Express.js](#setting-up-nodejs-and-expressjs)
   - [Initialize a New Node.js Project](#step-1-initialize-a-new-nodejs-project)
   - [Install Express.js](#step-2-install-expressjs)
   - [Create an Express.js Server](#step-4-create-an-expressjs-server)
   - [Run the Server](#step-5-run-the-server)
2. [Adding TypeScript Support](#adding-typescript-support)
   - [Install TypeScript and Dependencies](#step-1-install-typescript-and-dependencies)
   - [Configure TypeScript](#step-2-configure-typescript)
   - [Set Up Project Structure](#step-3-set-up-project-structure)
   - [Update Server for TypeScript](#step-4-update-serverts-for-typescript)
   - [Compile and Run the Server](#step-5-compile-and-run-the-server)

---

## Setting Up Node.js and Express.js

### Step 1: Initialize a New Node.js Project

1. Open your terminal or command prompt.
2. Create a new directory for your project and navigate to it:
   ```bash
   mkdir my-express-app
   cd my-express-app
   ```
3. Initialize a new Node.js project:
   ```bash
   npm init -y
   ```
   This creates a `package.json` file with default settings.

---

### Step 2: Install Express.js

1. Install Express.js as a dependency:
   ```bash
   npm install express
   ```
2. Verify the installation by checking the `package.json` file. The `dependencies` section should include `express`.

---

### Step 3: Open the Project in VS Code

1. Launch Visual Studio Code.
2. Open the `my-express-app` directory:
   ```bash
   code .
   ```

---

### Step 4: Create an Express.js Server

1. In the VS Code Explorer, create a new file named `server.js`.
2. Add the following code to `server.js`:

   ```javascript
   const express = require("express");
   const app = express();

   const PORT = 3000;

   app.get("/", (req, res) => {
     res.send("Hello, Express!");
   });

   app.listen(PORT, () => {
     console.log(`Server is running on http://localhost:${PORT}`);
   });
   ```

---

### Step 5: Run the Server

1. Open the integrated terminal in VS Code (`Ctrl + ~` or `Cmd + ~` on macOS).
2. Start the server:
   ```bash
   node server.js
   ```
3. Open your browser and navigate to [http://localhost:3000](http://localhost:3000). You should see **"Hello, Express!"** displayed.

---

## Adding TypeScript Support

### Step 1: Install TypeScript and Dependencies

1. Install TypeScript and its associated Node.js types:

   ```bash
   npm install --save-dev typescript @types/node @types/express
   ```

2. Verify the installation by running:
   ```bash
   npx tsc --version
   ```

---

### Step 2: Configure TypeScript

1. Initialize a TypeScript configuration file:

   ```bash
   npx tsc --init
   ```

2. Open the `tsconfig.json` file and configure it:
   ```json
   {
     "compilerOptions": {
       "target": "ES6",
       "module": "commonjs",
       "strict": true,
       "rootDir": "./src",
       "outDir": "./dist",
       "esModuleInterop": true
     },
     "include": ["src/**/*"],
     "exclude": ["node_modules"]
   }
   ```

---

### Step 3: Set Up Project Structure

1. Create a `src` directory:
   ```bash
   mkdir src
   ```
2. Move your `server.js` file into the `src` folder and rename it to `server.ts`.

---

### Step 4: Update `server.ts` for TypeScript

1. Modify your `server.ts` file to use TypeScript features:

   ```typescript
   import express, { Request, Response } from "express";

   const app = express();
   const PORT = 3000;

   app.get("/", (req: Request, res: Response) => {
     res.send("Hello, TypeScript with Express!");
   });

   app.listen(PORT, () => {
     console.log(`Server is running on http://localhost:${PORT}`);
   });
   ```

---

### Step 5: Compile and Run the Server

1. Compile TypeScript to JavaScript:

   ```bash
   npx tsc
   ```

   The compiled files will appear in the `dist` directory.

2. Run the server:

   ```bash
   node dist/server.js
   ```

3. Open your browser and navigate to [http://localhost:3000](http://localhost:3000). You should see **"Hello, TypeScript with Express!"** displayed.

---

## Tips and Tricks

- Use **Nodemon** for automatic server restarts during development:

  ```bash
  npm install --save-dev nodemon
  ```

  Update the `package.json` scripts:

  ```json
  "scripts": {
      "start": "node dist/server.js",
      "dev": "nodemon dist/server.js"
  }
  ```

  Run the development server:

  ```bash
  npm run dev
  ```

- Add a `.gitignore` file to exclude `node_modules` and `dist`:
  ```
  node_modules
  dist
  ```

---
