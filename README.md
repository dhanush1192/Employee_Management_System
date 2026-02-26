# Employee Management System 🏢

A full-stack web application for managing employee records with department associations, built using React and Spring Boot.

![Java](https://img.shields.io/badge/Java-8-orange)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-Latest-brightgreen)
![React](https://img.shields.io/badge/React-18-blue)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-blue)
![License](https://img.shields.io/badge/License-MIT-yellow)

## 📋 Table of Contents
- [About](#about)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
- [Screenshots](#screenshots)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## 🎯 About

The Employee Management System is a comprehensive solution developed for **BridgeSoft** to streamline employee data management. This application provides a user-friendly interface to perform CRUD operations on employee records, manage departments, and maintain organizational structure efficiently.

## ✨ Features

- ✅ Create, Read, Update, and Delete employee records
- ✅ Department management and employee-department associations
- ✅ Responsive user interface with Bootstrap 5
- ✅ RESTful API architecture
- ✅ Exception handling and error management
- ✅ Real-time data updates
- ✅ Cross-Origin Resource Sharing (CORS) enabled
- ✅ Clean and modern UI design

## 🛠️ Technologies Used

### Frontend
- **HTML5** - Markup language
- **CSS3** - Styling
- **JavaScript (ES6+)** - Programming language
- **React 18** - UI library
- **Bootstrap 5** - CSS framework for responsive design

### Backend
- **Java 8** - Programming language
- **Spring Boot** - Application framework
- **Spring Web** - RESTful web services
- **Spring Data JPA** - Data persistence
- **Hibernate** - ORM framework
- **Lombok** - Boilerplate code reduction
- **Spring Boot DevTools** - Development utilities

### Database
- **PostgreSQL 15** - Relational database

### Tools
- **Maven** - Dependency management and build tool
- **Postman** - API testing
- **Git/GitHub** - Version control
- **VS Code / IntelliJ IDEA** - IDE

## 📁 Project Structure

### Frontend Structure
```
frontend/
│
├── node_modules/           # Dependencies
├── public/
│   ├── index.html         # Main HTML file
│   ├── manifest.json      # PWA manifest
│   └── favicon.ico        # App icon
│
├── src/
│   ├── index.js           # Entry point
│   ├── index.css          # Global styles
│   ├── App.js             # Root component
│   ├── App.css            # App styles
│   ├── App.test.js        # App tests
│   │
│   └── components/
│       ├── Header.js      # Header component
│       ├── EmployeeList.js # Employee listing component
│       └── Footer.js      # Footer component
│
├── package.json           # NPM dependencies
└── README.md             # Frontend documentation
```

### Backend Structure
```
backend/
│
├── src/main/java/
│   └── com.ihub.www/
│       ├── BackendApplication.java        # Main Spring Boot application
│       │
│       ├── model/
│       │   ├── Employee.java              # Employee entity
│       │   └── Department.java            # Department entity
│       │
│       ├── repo/
│       │   ├── EmployeeRepository.java    # Employee data access
│       │   └── DepartmentRepository.java  # Department data access
│       │
│       ├── service/
│       │   └── EmployeeService.java       # Business logic layer
│       │
│       ├── controller/
│       │   └── EmployeeController.java    # REST API endpoints
│       │
│       └── exception/
│           └── ResourceNotFoundException.java  # Custom exception
│
├── src/main/resources/
│   └── application.properties             # Configuration file
│
├── src/test/java/                         # Test files
│
└── pom.xml                                # Maven dependencies
```

## 📦 Prerequisites

Before running this application, make sure you have:

- **Java Development Kit (JDK) 8** or higher
- **Node.js** (v14 or higher) and **npm**
- **PostgreSQL Server** (v15 or higher)
- **Maven** (v3.6 or higher)
- **Git** (for cloning the repository)

## 🚀 Installation

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/employee-management-system.git
cd employee-management-system
```

### 2. Database Setup
```sql
-- Login to PostgreSQL
psql -U postgres

-- Create database
CREATE DATABASE employee_db;

-- Connect to the database
\c employee_db

-- Tables will be auto-created by Hibernate
```

### 3. Backend Setup
```bash
# Navigate to backend directory
cd backend

# Install dependencies (Maven will download them)
mvn clean install

# Skip tests if needed
mvn clean install -DskipTests
```

### 4. Frontend Setup
```bash
# Navigate to frontend directory
cd frontend

# Install dependencies
npm install
```

## ⚙️ Configuration

### Backend Configuration
Edit `backend/src/main/resources/application.properties`:

```properties
# Server Configuration
server.port=9191

# Database Configuration
spring.datasource.url=jdbc:postgresql://localhost:5432/employee_db
spring.datasource.username=postgres
spring.datasource.password=your_password
spring.datasource.driver-class-name=org.postgresql.Driver

# Hibernate Configuration
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect
spring.jpa.properties.hibernate.format_sql=true

# Logging
logging.level.org.hibernate.SQL=DEBUG
logging.level.org.hibernate.type.descriptor.sql.BasicBinder=TRACE
```

### Maven Dependency
Replace the MySQL dependency in `pom.xml` with the PostgreSQL driver:

```xml
<!-- Remove MySQL dependency -->
<!-- <dependency>
    <groupId>com.mysql</groupId>
    <artifactId>mysql-connector-j</artifactId>
    <scope>runtime</scope>
</dependency> -->

<!-- Add PostgreSQL dependency -->
<dependency>
    <groupId>org.postgresql</groupId>
    <artifactId>postgresql</artifactId>
    <scope>runtime</scope>
</dependency>
```

### Frontend Configuration
If needed, update API base URL in your React components:
```javascript
const API_BASE_URL = "http://localhost:9191/api/v1";
```

## 🎮 Running the Application

### Start Backend Server
```bash
# Navigate to backend directory
cd backend

# Run using Maven
mvn spring-boot:run

# Or run the JAR file
java -jar target/backend-0.0.1-SNAPSHOT.jar
```
Backend will start at: **http://localhost:9191**

### Start Frontend Development Server
```bash
# Navigate to frontend directory
cd frontend

# Start React development server
npm start
```
Frontend will start at: **http://localhost:3000**

## 📡 API Endpoints

### Employee Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET    | `/api/v1/employees` | Get all employees |
| GET    | `/api/v1/employees/{id}` | Get employee by ID |
| POST   | `/api/v1/employees` | Create new employee |
| PUT    | `/api/v1/employees/{id}` | Update employee |
| DELETE | `/api/v1/employees/{id}` | Delete employee |

### Request/Response Examples

#### Create Employee (POST)
```json
POST /api/v1/employees
Content-Type: application/json

{
  "firstName": "John",
  "lastName": "Doe",
  "email": "john.doe@bridgesoft.com",
  "departmentId": 1
}
```

#### Response
```json
{
  "id": 1,
  "firstName": "John",
  "lastName": "Doe",
  "email": "john.doe@bridgesoft.com",
  "department": {
    "id": 1,
    "name": "IT Department"
  }
}
```

## 🗄️ Database Schema

### Employee Table
```sql
CREATE TABLE employees (
    id BIGSERIAL PRIMARY KEY,
    first_name VARCHAR(255) NOT NULL,
    last_name VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    department_id BIGINT,
    FOREIGN KEY (department_id) REFERENCES departments(id)
);
```

### Department Table
```sql
CREATE TABLE departments (
    id BIGSERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    description VARCHAR(500)
);
```

## 🧪 Testing

### Test Backend APIs with Postman
1. Import the Postman collection (if available)
2. Set base URL: `http://localhost:9191`
3. Test each endpoint with sample data

### Run Backend Tests
```bash
cd backend
mvn test
```

### Run Frontend Tests
```bash
cd frontend
npm test
```

## 📦 Building for Production

### Build Backend
```bash
cd backend
mvn clean package
# JAR file will be created in target/ directory
```

### Build Frontend
```bash
cd frontend
npm run build
# Optimized build will be created in build/ directory
```

## 🐛 Troubleshooting

### Common Issues

**Issue: Database connection failed**
```bash
Solution: Check PostgreSQL service is running and credentials in application.properties are correct.
         Ensure PostgreSQL is listening on port 5432 (default).
```

**Issue: Port 9191 already in use**
```bash
Solution: Change server.port in application.properties or kill the process using the port
```

**Issue: CORS errors in browser**
```bash
Solution: Ensure @CrossOrigin annotation is present in controller or configure CORS globally
```

**Issue: PostgreSQL authentication error**
```bash
Solution: Verify the pg_hba.conf file allows password authentication for your user,
         or update the connection method to 'md5' or 'scram-sha-256'.
```

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👥 Team

**Client:** BridgeSoft

**Development Team:**
- Backend Developer
- Frontend Developer
- Full Stack Developer: DHANUSH BONTHALA

## 📧 Contact

**Project Link:** [https://github.com/dhanush1192/Employee_Management_System](https://employee-management-system-ycry.onrender.com)

**Email:** dhanushbonthala85@gmail.com

## 🙏 Acknowledgments

- Spring Boot Documentation
- React Documentation
- Bootstrap Team
- BridgeSoft for the opportunity

---

**⭐ If you found this project helpful, please give it a star!**

Made with ❤️ for BridgeSoft
