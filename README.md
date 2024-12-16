# Node Application with Docker 

This repository contains a Node.js application with a Docker setup to streamline development and deployment. Follow the instructions below to set up, run, and push your project to GitHub.

---

## Prerequisites

Ensure you have the following tools installed:
- [Node.js](https://nodejs.org/) (v16 or higher)
- [Docker](https://www.docker.com/)
- [Git](https://git-scm.com/)

---

## Steps to Create and Run a Node.js Application

### 1. Initialize the Node.js Application
1. Create a project directory:
   ```
   mkdir node-docker-app && cd node-docker-app
   ```
2. Initialize the project with npm:
   ```
   npm init -y
   ```
3. Install required dependencies:
   ```
   npm install express
   ```
4. Create a basic `index.js` file:
   ```
   const express = require('express');
   const app = express();

   app.get('/', (req, res) => {
       res.send('Hello, World!');
   });

   const PORT = 3000;
   app.listen(PORT, () => {
       console.log(`Server is running on port ${PORT}`);
   });
   ```

### 2. Create the Dockerfile
1. Add the following `Dockerfile`:
   ```
   # Base image
   FROM node:16

   # Set working directory
   WORKDIR /usr/src/app

   # Copy package.json and package-lock.json
   COPY package*.json ./

   # Install dependencies
   RUN npm install

   # Copy the application files
   COPY . .

   # Expose application port
   EXPOSE 3000

   # Start the application
   CMD ["npm", "start"]
   ```

### 3. Build and Run the Docker Container
1. Build the Docker image:
   ```
   docker build -t node-docker-app .
   ```
2. Run the container:
   ```
   docker run -p 3000:3000 node-docker-app
   ```
3. Open your browser and navigate to `http://localhost:3000` to see your app in action.

### 4. Push to GitHub
1. Initialize a Git repository:
   ```
   git init
   ```
2. Add files to the repository:
   ```
   git add .
   ```
3. Commit your changes:
   ```
   git commit -m "Initial commit with Dockerized Node app"
   ```
4. Create a repository on GitHub and push the changes:
   ```
   git remote add origin <repository_url>
   git branch -M main
   git push -u origin main
   ```

---

## Repository Structure
```
node-docker-app/
├── Dockerfile
├── index.js
├── package.json
└── package-lock.json
```
![image](https://github.com/user-attachments/assets/0b8c4a65-4b55-43ae-b2d8-a401ba08e076)

---

## Notes
- Update the `index.js` file to include additional routes or logic for your application.
- Modify the `Dockerfile` if additional dependencies or configurations are needed.
- Use `.dockerignore` to exclude unnecessary files from the Docker image.

