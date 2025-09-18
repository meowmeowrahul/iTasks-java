# iTasks - Full-Stack Task Management Application

A comprehensive task management web application built with Spring Boot backend and React frontend, featuring JWT authentication, MySQL database, and modern UI components.

## 📋 Overview

iTasks is a full-stack web application that allows users to manage their tasks efficiently. The application provides secure user authentication, task CRUD operations, filtering and searching capabilities, and a responsive user interface.

## ✨ Features

- **User Authentication**: Secure JWT-based authentication with HttpOnly cookies
- **Task Management**: Create, read, update, and delete tasks
- **Task Filtering**: Filter tasks by completion status, due dates, and custom labels
- **Search Functionality**: Search tasks by title, content, or labels
- **Priority System**: Set task priorities (Least, Medium, High, Highest)
- **Label System**: Add custom labels to organize tasks
- **Responsive Design**: Modern UI built with React and Tailwind CSS
- **Secure Backend**: Spring Security with JWT token validation
- **RESTful API**: Well-structured REST endpoints for all operations

## 🛠 Tech Stack

### Backend
- **Java 17+**
- **Spring Boot 3.x**
- **Spring Security**
- **Spring Data JPA**
- **MySQL 8.0+**
- **JWT (JSON Web Tokens)**
- **Lombok**
- **BCrypt Password Encryption**

### Frontend
- **React 18**
- **Vite**
- **Tailwind CSS**
- **Axios**
- **React Context API**
- **React Hooks**

### Database
- **MySQL 8.0+**

## 📁 Project Structure

```
iTasks/
├── backend/
│   ├── src/main/java/com/meowmeowrahul/to_do/
│   │   ├── config/
│   │   │   ├── SecurityConfig.java
│   │   │   └── JwtFilter.java
│   │   ├── controller/
│   │   │   └── UserController.java
│   │   ├── model/
│   │   │   ├── Users.java
│   │   │   ├── Task.java
│   │   │   └── UserPrincipal.java
│   │   ├── repo/
│   │   │   ├── UserRepo.java
│   │   │   └── TaskRepo.java
│   │   ├── service/
│   │   │   ├── UserService.java
│   │   │   ├── JwtService.java
│   │   │   └── MyUserDetailsService.java
│   │   └── ToDoApplication.java
│   └── src/main/resources/
│       └── application.properties
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── Navbar.jsx
│   │   │   ├── AddTask.jsx
│   │   │   ├── TaskCard.jsx
│   │   │   └── Login.jsx
│   │   ├── context/
│   │   │   └── Context.jsx
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── index.html
│   ├── package.json
│   └── vite.config.js
└── README.md
```

##Few ScreenShots 

### Login Page

[Login](/img/login-page.png)

### Demo State 1

[ScreenShot1](/img/img1.png)

### Demo State 2

[ScreenShot2](/img/img2.png)

### Demo Mobile State

[mobile](/img/mobile-page.png)

## 🚀 Prerequisites

Before running the application, ensure you have the following installed:

### Required Software
- **Java 17 or higher** - [Download Java](https://www.oracle.com/java/technologies/downloads/)
- **MySQL 8.0 or higher** - [Download MySQL](https://dev.mysql.com/downloads/installer/)
- **Git** - [Download Git](https://git-scm.com/downloads)

### Optional but Recommended
- **MySQL Workbench** - For database management
- **VS Code or IntelliJ IDEA** - For code editing
- **Postman** - For API testing

## 📦 Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/iTasks.git
cd iTasks
```

### 2. Database Setup

#### Install and Configure MySQL

1. **Download and install MySQL** from [official website](https://dev.mysql.com/downloads/installer/)

2. **Start MySQL server** and create the database:

```sql
-- Connect to MySQL as root
mysql -u root -p

-- Create database
CREATE DATABASE ToDo_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

-- Create user (optional, you can use root)
CREATE USER 'todouser'@'localhost' IDENTIFIED BY 'your_password';
GRANT ALL PRIVILEGES ON ToDo_db.* TO 'todouser'@'localhost';
FLUSH PRIVILEGES;

-- Exit MySQL
EXIT;
```

3. **Verify database creation**:
```sql
SHOW DATABASES;
USE ToDo_db;
```

### 3. Backend Setup (Spring Boot)

#### Navigate to the backend directory:
```bash
cd backend
```

#### Configure Database Connection

Edit `src/main/resources/application.properties`:

```properties
# Database Configuration
spring.datasource.url=jdbc:mysql://localhost:3306/ToDo_db
spring.datasource.username=root
spring.datasource.password=YOUR_MYSQL_PASSWORD
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# JPA Configuration
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect

# JWT Configuration (Change these in production)
jwt.secret=zIK34SHPro8YHr+cAvNFr9Zn/ukgS0aiHq46TUWFGGg=
jwt.expiration=1800000
jwt.issuer=to-do

# Application Configuration
spring.application.name=to-do
```

#### Build and Run the Backend

**Using Maven Wrapper (recommended):**
```bash
# Make wrapper executable (Linux/Mac)
chmod +x ./mvnw

# Clean and install dependencies
./mvnw clean install

# Run the application
./mvnw spring-boot:run
```

**Using Maven (if installed globally):**
```bash
mvn clean install
mvn spring-boot:run
```

**Using your IDE:**
- Import the project as a Maven project
- Run the `ToDoApplication.java` main class

The backend server will start on `http://localhost:8080`

#### Verify Backend Installation
Test the server by visiting: `http://localhost:8080/check-token`

### 4. Frontend Setup (React + Vite)

#### Navigate to the frontend directory:
```bash
cd ../frontend
```

#### Install Dependencies

**Using npm:**
```bash
npm install
```

**Using yarn:**
```bash
yarn install
```

#### Configure API Base URL (if needed)

The frontend is configured to connect to `http://localhost:8080`. If your backend runs on a different port, update the API calls in the components.

#### Run the Development Server

**Using npm:**
```bash
npm run dev
```

**Using yarn:**
```bash
yarn dev
```

The frontend will start on `http://localhost:5173`

### 5. Verify Complete Setup

1. **Backend**: Visit `http://localhost:8080/check-token`
2. **Frontend**: Visit `http://localhost:5173`
3. **Database**: Check that tables are created automatically when you start the backend

## 🎯 Usage Guide

### Getting Started

1. **Open the application** in your browser at `http://localhost:5173`

2. **Register a new account**:
   - Click on the registration form
   - Enter your username and password
   - Submit the form

3. **Login**:
   - Use your registered credentials
   - The system will authenticate you and store a secure JWT token

4. **Create your first task**:
   - Click the "Add Task" button
   - Fill in the task details:
     - **Header**: Task title
     - **Content**: Task description
     - **Priority**: Select from Least, Medium, High, Highest
     - **End Date**: Optional due date
     - **Labels**: Add custom labels for organization

5. **Manage tasks**:
   - **Mark as complete**: Click the checkbox
   - **Edit task**: Click the edit button
   - **Delete task**: Click the delete button
   - **Filter tasks**: Use the filter options in the navbar
   - **Search tasks**: Use the search bar to find specific tasks

### API Endpoints

The backend provides the following REST endpoints:

#### Authentication
- `POST /register` - Register new user
- `POST /login` - User login
- `GET /check-token` - Verify JWT token

#### Task Management
- `GET /tasks` - Get all user tasks
- `POST /tasks` - Create new task
- `PUT /tasks/{id}` - Update task
- `DELETE /tasks/{id}` - Delete task
- `GET /tasks/search/{value}` - Search tasks
- `GET /tasks/filter/completed` - Filter completed tasks
- `GET /tasks/sort/today` - Get today's tasks

## ⚙️ Configuration

### Backend Configuration Options

Edit `application.properties` for:

- **Database connection settings**
- **JWT token configuration** (secret, expiration, issuer)
- **Server port** (default: 8080)
- **CORS settings** (configured for localhost:5173)

### Frontend Configuration

- **API base URL**: Update axios calls if backend URL changes
- **Port**: Modify `vite.config.js` to change development port

## 🔧 Development

### Running in Development Mode

1. **Start MySQL server**
2. **Run backend**: `./mvnw spring-boot:run`
3. **Run frontend**: `npm run dev`
4. **Access application**: `http://localhost:5173`

### Database Schema

The application automatically creates the following tables:
- `users` - User accounts
- `task` - Task information
- `task_labels` - Task labels (many-to-many relationship)

## 🛡️ Security Features

- **JWT Authentication** with HttpOnly cookies
- **Password encryption** using BCrypt
- **CSRF protection** disabled (using JWT)
- **CORS configuration** for cross-origin requests
- **Stateless session** management
- **Secure cookie handling**

## 🚨 Troubleshooting

### Common Issues

1. **MySQL Connection Failed**
   - Verify MySQL server is running
   - Check database credentials in `application.properties`
   - Ensure database `ToDo_db` exists

2. **Backend Port Conflicts**
   - Change port in `application.properties`: `server.port=8081`
   - Update frontend API calls accordingly

3. **Frontend Build Issues**
   - Delete `node_modules` and `package-lock.json`
   - Run `npm install` again
   - Check Node.js version compatibility

4. **CORS Errors**
   - Verify CORS configuration in `SecurityConfig.java`
   - Ensure frontend URL matches allowed origins

5. **JWT Token Issues**
   - Check JWT secret configuration
   - Verify token expiration settings
   - Clear browser cookies and login again

### Debug Mode

Enable debug logging in `application.properties`:
```properties
logging.level.com.meowmeowrahul.to_do=DEBUG
logging.level.org.springframework.security=DEBUG
```

---

**Happy Task Managing! 🎉**
