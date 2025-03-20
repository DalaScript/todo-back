# Todo API - Task Management System

## 🚀 Overview
This is a **task management API** that allows users to **register, log in, create, update, and delete tasks**. The API uses **MongoDB** for data storage and **JWT authentication** for security. It also includes **rate limiting** and **logging** for better performance and monitoring.

---

## 📌 Features
- ✅ **User Authentication** (Register, Login, Password Reset)
- ✅ **Task Management** (Create, Read, Update, Delete)
- ✅ **Role-Based Access** (Admin vs Regular Users)
- ✅ **Secure API** (JWT Authentication)
- ✅ **Rate Limiting** (Prevents API abuse)
- ✅ **Logging System** (Tracks API activity & errors)
- ✅ **Optimized Database Queries** (MongoDB Indexes for Speed)

---

## 📦 Setup & Installation
### **1️⃣ Clone the Repository**
```bash
git clone https://github.com/yourusername/task-api.git
cd task-api
```

### **2️⃣ Install Dependencies**
```bash
npm install
```

### **3️⃣ Configure Environment Variables**
Create a `.env` file in the root folder and add:
```env
PORT=5000
MONGO_URL=your_mongodb_connection_string
DB_NAME=your_database_name
JWT_SECRET=your_secret_key
EMAIL_USER=your_email@gmail.com
EMAIL_PASS=your_email_password
```

### **4️⃣ Start the Server**
```bash
npm run dev
```
Server will start at: `http://localhost:5000`

---

## 📡 API Endpoints
### **🔹 User Authentication**
| Method | Endpoint | Description | Auth Required? |
|--------|---------|-------------|---------------|
| **POST** | `/auth/register` | Register a new user | ❌ No |
| **POST** | `/auth/login` | Log in & get JWT token | ❌ No |
| **POST** | `/auth/request-reset` | Request password reset email | ❌ No |
| **POST** | `/auth/reset-password?token=your_token` | Reset password | ❌ No |

### **🔹 Task Management**
| Method | Endpoint | Description | Auth Required? |
|--------|---------|-------------|---------------|
| **GET** | `/tasks` | Get all tasks (Admins: all, Users: their own) | ✅ Yes |
| **POST** | `/tasks` | Create a new task | ✅ Yes |
| **PATCH** | `/tasks/{task_id}` | Update a task | ✅ Yes |
| **DELETE** | `/tasks/{task_id}` | Delete a task | ✅ Yes |

---

## 📚 API Documentation | Testing in Postman
### **1️⃣ User Authentication**
#### 🔹 Register
```http
POST /auth/register
```
**Body:**
```json
{
  "username": "testuser",
  "password": "password123",
  "phone": "123456789",
  "email": "testuser@example.com"
}
```
**Response:**
```json
{
  "message": "User registered successfully",
  "userId": "some_id",
  "role": "user"
}
```
---
#### 🔹 Login
```http
POST /auth/login
```
**Body:**
```json
{
  "username": "testuser",
  "password": "password123"
}
```
**Response:**
```json
{
  "message": "Login successful",
  "token": "your_jwt_token",
  "role": "user"
}
```
---
#### 🔹 Request Password Reset
```http
POST /auth/request-reset
```
**Body:**
```json
{
  "email": "testuser@example.com"
}
```
**Response:**
```json
{
  "message": "Reset email sent"
}
```
---
#### 🔹 Reset Password
```http
POST /auth/reset-password?token=your_reset_token
```
**Body:**
```json
{
  "newPassword": "newSecurePassword"
}
```
**Response:**
```json
{
  "message": "Password reset successful"
}
```

---

### **2️⃣ Task Management**
#### 🔹 Create a Task
```http
POST /tasks
Authorization: Bearer your_jwt_token
```
**Body:**
```json
{
  "task": "Complete coding project",
  "priority": 1,
  "completed": false
}
```
**Response:**
```json
{
  "message": "Task created successfully!",
  "taskId": "some_id"
}
```
---
#### 🔹 Get All Tasks
```http
GET /tasks
Authorization: Bearer your_jwt_token
```
**Response:**
```json
[
  {
    "title": "Complete coding project",
    "completed": false,
    "priority": 1
  }
]
```
---
#### 🔹 Update a Task
```http
PATCH /tasks/{task_id}
Authorization: Bearer your_jwt_token
```
**Body:**
```json
{
  "completed": true
}
```
**Response:**
```json
{
  "message": "Task updated successfully!"
}
```
---
#### 🔹 Delete a Task
```http
DELETE /tasks/{task_id}
Authorization: Bearer your_jwt_token
```
**Response:**
```json
{
  "message": "Task deleted successfully!"
}
```

---

## ⚙️ Additional Features
### **✅ Rate Limiting**
| Endpoint | Max Requests | Time Window |
|----------|-------------|-------------|
| `/auth/*` | 30 | 15 minutes |
| `/tasks/*` | 60 | 1 minute |

If the limit is exceeded, the response will be:
```json
{ 
   "error": "Too many requests, please try again later" 
}
```

### **✅ Logging System**
- **All logs are stored in `logs/` folder.**
- `combined.log` → Tracks API requests & activities.
- `error.log` → Stores errors & failures.

---

## 🛠️ Technologies Used
- **Node.js**
- **MongoDB**
- **bcryptjs** (for password hashing)
- **jsonwebtoken** (for authentication)
- **nodemailer** (for password reset emails)
- **winston** (for logging)
- **Rate Limiting Middleware** (Prevents excessive requests)
- **MongoDB Indexing** (Improves query performance)
- **Error Handling Middleware** (Ensures stability)

---

## 🎯 Next Steps
The next step is to **build the frontend** for this application to provide a user-friendly interface.

---

## 🤝 Contributing
Feel free to fork and submit issues!

**Created with LineDev by DalaScript** 💻


---

## Author

### Connect with Me

- [Instagram](https://www.instagram.com/DalaScript)
- [YouTube](https://www.youtube.com/@DalaScript)

### Coding Profiles

- [freeCodeCamp](https://www.freecodecamp.org/DalaScript)
- [FrontendMentor](https://www.frontendmentor.io/profile/DalaScript)
- [GitHub](https://github.com/DalaScript)

