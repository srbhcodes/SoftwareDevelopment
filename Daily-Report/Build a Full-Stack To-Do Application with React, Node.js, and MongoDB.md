# Project Report: Full-Stack To-Do Application

**Author:** Sourabh  
**Date:** 19 Dec  
**Title:** Build a Full-Stack To-Do Application with React, Node.js, and MongoDB
Epic Name: GIT COMMANDS
Git link: https://github.com/srbhcodes/TodoApp

---

## Scope of Project:

To design and develop a full-stack To-Do application that allows users to manage their tasks efficiently. The app includes the ability to:

- Add, edit, and delete tasks.
- Retrieve tasks stored in a MongoDB database.
- Provide a seamless frontend-backend connection for real-time task management.

---

## Technologies Used:

- **Frontend:** React.js (JavaScript, JSX, and CSS)
- **Backend:** Node.js with Express.js
- **Database:** MongoDB (NoSQL)
- **Tools & Services:**
    - Vite (for React app setup)
    - Postman (for API testing)
    - Git (for version control)
    - GitHub (for repository hosting)

---

## Steps:

1. **Initialize the Project**:
    
    - Set up a Git repository.
    - Created a new React app using Vite for the frontend.
    - Initialized a Node.js server with Express.js for the backend.
2. **Design Database Schema**:
    
    - Used MongoDB to store tasks.
    - Defined a schema for tasks with properties: `title` and `description`.
3. **Set Up Backend APIs**:
    
    - Created RESTful APIs to handle CRUD operations:
        - `POST /tasks`: Add a new task.
        - `GET /tasks`: Retrieve all tasks.
        - `PUT /tasks/:id`: Update a task.
        - `DELETE /tasks/:id`: Delete a task.
4. **Connect MongoDB to Backend**:
    
    - Installed and configured Mongoose for database interactions.
    - Verified the connection using MongoDB Compass and CLI tools.
5. **Frontend Integration**:
    
    - Designed the user interface in React.
    - Integrated API calls using `fetch` to display and modify tasks.
6. **Testing**:
    
    - Verified API endpoints using Postman.
    - Tested the complete workflow in the browser.
7. **Error Handling and Debugging**:
    
    - Handled error responses in API calls and user notifications.
    - Addressed server and database connection issues.
8. **Deploy and Version Control**:
    
    - Set up the project on GitHub.
    - Fixed Git authentication issues by generating and using a Personal Access Token (PAT).

---

## Project Outcome:

- Successfully built a functional To-Do application with features to add, view, update, and delete tasks.
- Achieved real-time data storage and retrieval using MongoDB.
- Delivered a seamless user experience with React for the frontend.

---

## Issues Faced:

1. **Initial Setup Errors**:
    
    - Faced challenges with installing Vite and initializing the backend.
    - Resolved issues by ensuring all dependencies were installed correctly.
2. **Database Connection Issues**:
    
    - Encountered errors while connecting to MongoDB.
    - Solved by configuring MongoDB URI and testing with Mongoose.
3. **CORS Errors**:
    
    - Cross-origin requests were blocked during frontend-backend integration.
    - Fixed by enabling CORS in the Express.js server.
4. **Authentication Problem with GitHub**:
    
    - Faced an issue with GitHub password authentication.
    - Resolved by generating and using a Personal Access Token (PAT).
5. **Testing and Debugging**:
    
    - Errors in API calls (e.g., missing fields in requests).
    - Debugged using Postman and resolved issues in request payloads.

---

### Screenshots

Server running:
![[Pasted image 20250107210537.png]]

Backend API Endpoints:
![[Pasted image 20250107210735.png]]

Tasks available on client side:
![[Pasted image 20250107210852.png]]