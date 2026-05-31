# HR Employee DB API

A MuleSoft REST API that delivers employee data to HR management systems. It connects directly to a MySQL database and exposes employee records via standardized RESTful endpoints.

---

## Table of Contents

- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [API Endpoints](#api-endpoints)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [License](#license)

---

## Overview

The `hr-employee-db-sapi` is a **REST API** built with **MuleSoft Anypoint Platform**. It connects directly to a MySQL database and exposes clean REST endpoints for HR management, handling all CRUD operations on employee records.

---

## Tech Stack

| Component | Technology |
|---|---|
| Integration Platform | MuleSoft Anypoint Platform |
| Runtime | Mule 4.10.1 |
| API Specification | RAML (via Anypoint Exchange) |
| HTTP Connector | mule-http-connector 1.11.0 |
| Database Connector | mule-db-connector 1.14.17 |
| APIkit Module | mule-apikit-module 1.11.10 |
| Database | MySQL 8.0+ |
| JDBC Driver | mysql-connector-java 8.0.30 |
| Build Tool | Maven (mule-maven-plugin 4.7.0) |

---

## Prerequisites

Before running this project, make sure you have:

- **Anypoint Studio 7.x** installed
- **Mule Runtime 4.10.1**
- **Java 8 or 11** (JDK)
- **Maven 3.6+**
- A running **MySQL** instance with the HR employee database
- Access to **Anypoint Exchange** (for the RAML spec dependency)

---

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/TarunAika/hr-employee-db-sapi.git
cd hr-employee-db-sapi
```

### 2. Import into Anypoint Studio

- Open Anypoint Studio
- Go to **File → Import → Anypoint Studio → Anypoint Studio Project from File System**
- Select the cloned project directory and click **Finish**

### 3. Configure database connection

Update the database configuration properties with your MySQL connection details (see [Configuration](#configuration) below).

### 4. Build the project

```bash
mvn clean install
```

---

## Project Structure

```
hr-employee-db-sapi/
├── src/
│   ├── main/
│   │   ├── mule/          # Mule flow XML files
│   │   └── resources/     # Properties and configuration files
│   └── test/
│       └── munit/         # MUnit test suites
├── exchange-docs/         # API documentation assets
├── .vscode/               # VSCode settings
├── mule-artifact.json     # Mule deployment descriptor
├── pom.xml                # Maven build configuration
├── .gitignore
└── LICENSE
```

---

## API Endpoints

This API follows the RAML specification published on Anypoint Exchange (`hr-db-employee-sapi`). Typical endpoints include:

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/employees` | Retrieve all employees |
| `GET` | `/employees/{id}` | Retrieve a specific employee by ID |
| `POST` | `/employees` | Create a new employee record |
| `PUT` | `/employees/{id}` | Update an existing employee |
| `DELETE` | `/employees/{id}` | Delete an employee record |

> **Note:** Refer to the RAML specification on Anypoint Exchange for the full request/response schema and parameter details.

---

## Configuration

Database and HTTP listener settings should be defined in your properties file (e.g., `src/main/resources/application.properties` or environment-specific config):

```properties
# HTTP Listener
http.listener.host=0.0.0.0
http.listener.port=8081

# MySQL Database
db.host=localhost
db.port=3306
db.name=hr_employee_db
db.user=<your-db-username>
db.password=<your-db-password>
```

> **Security tip:** Never commit credentials to version control. Use Anypoint Secrets Manager or environment-specific property files that are excluded via `.gitignore`.

---

## Running the Application

### In Anypoint Studio

Right-click the project → **Run As → Mule Application**

The API will start on `http://localhost:8081` by default.

### Via Maven

```bash
mvn clean package
```

Then deploy the generated `.jar` from `target/` to your Mule Runtime or CloudHub.

---

## License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.