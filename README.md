# poridhi-test-be

Overall Project directory:
Full-stack-app
|- backend
|   |- index.js
|   |- package.json
|   |- Dockerfile
|   .
|
|- frontend
|   |- public
|   |- src
|   |- package.json
|   |- Dockerfile
|      
|- Makefile

Let's break it down step by step.
Step 1: Setting Up the Backend (Node.js with Express)
1.1. Create a Directory for the Backend
mkdir Full-stack-app
cd Full-stack-app
mkdir backend
cd backend

1.2. Initialize the Node.js Project
npm init -y


This will create a package.json file.
1.3. Install Dependencies
Install express to handle server routing.
npm install express cors


1.4. Create index.js for the Backend
In the backend directory, create a file called index.js:
touch index.js

Edit index.js with the following content:
const express = require('express');
const os = require('os');
const cors = require('cors');

const app = express();
const PORT = 4000;

app.use(cors()); // Enable CORS for all routes

app.get("/", (req, res) => {
    const message = "Hello world from the backend! 🚀";
    console.log(message);
    res.json({ message });
});

app.listen(PORT, () => {
    console.log(`Server Running at port ${PORT}`);
});

1.5. Create a Dockerfile for the Backend
In the backend directory, create a Dockerfile:
touch Dockerfile

Add the following content to the Dockerfile:
# Use the official Node.js image from the Docker Hub
FROM node:14

# Create and set the working directory inside the container
WORKDIR /app

# Copy package.json and install dependencies
COPY package*.json ./
RUN npm install

# Copy the rest of the app files
COPY . .

# Expose the port that your app will run on
EXPOSE 4000

# Start the server
CMD ["node", "index.js"]

