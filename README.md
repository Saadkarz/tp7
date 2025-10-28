# JAX-RS REST API with Spring Boot

A RESTful web service built with **Spring Boot**, **JAX-RS (Jersey)**, **JPA/Hibernate**, and **H2 Database** for managing bank accounts (Comptes).

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
- [Testing the API](#testing-the-api)
- [H2 Database Console](#h2-database-console)
- [Screenshots](#screenshots)

## 🎯 Overview

This project demonstrates a complete RESTful API implementation using JAX-RS (Jersey) integrated with Spring Boot. It provides CRUD (Create, Read, Update, Delete) operations for bank account management with support for both JSON and XML formats.

## ✨ Features

- ✅ Full CRUD operations for bank accounts
- ✅ JAX-RS (Jersey) REST API implementation
- ✅ Support for both JSON and XML content types
- ✅ JPA/Hibernate for data persistence
- ✅ H2 in-memory database
- ✅ Lombok for reducing boilerplate code
- ✅ Spring Boot DevTools for hot reload
- ✅ H2 Console for database visualization
- ✅ Auto-initialization with sample data

## 🛠️ Technologies Used

| Technology | Version | Description |
|------------|---------|-------------|
| **Java** | 21 | Programming language |
| **Spring Boot** | 3.4.1 | Framework for building Java applications |
| **JAX-RS (Jersey)** | - | REST API specification |
| **Spring Data JPA** | - | Data persistence layer |
| **Hibernate** | - | ORM framework |
| **H2 Database** | - | In-memory database |
| **Lombok** | - | Java library to reduce boilerplate code |
| **Maven** | - | Build and dependency management |

## 📁 Project Structure

```
jaxrs/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── ma/ws/jaxrs/
│   │   │       ├── JaxrsApplication.java       # Main application class
│   │   │       ├── config/
│   │   │       │   └── MyConfig.java           # Jersey configuration
│   │   │       ├── entities/
│   │   │       │   ├── Compte.java             # Account entity
│   │   │       │   └── TypeCompte.java         # Account type enum
│   │   │       ├── repositories/
│   │   │       │   └── CompteRepository.java   # JPA repository
│   │   │       └── rest/
│   │   │           └── CompteRest.java         # REST controller
│   │   └── resources/
│   │       ├── application.properties          # Application configuration
│   │       ├── static/
│   │       └── templates/
│   └── test/
│       └── java/
│           └── ma/ws/jaxrs/
│               └── JaxrsApplicationTests.java
├── pom.xml                                     # Maven configuration
├── mvnw                                        # Maven wrapper (Unix)
├── mvnw.cmd                                    # Maven wrapper (Windows)
└── README.md                                   # This file
```

## 📦 Prerequisites

Before running this application, make sure you have the following installed:

- **Java 21** or higher
- **Maven 3.6+** (or use the included Maven wrapper)
- **IDE** (IntelliJ IDEA, Eclipse, VS Code, etc.)

## 🚀 Installation

1. **Clone the repository** (or download the project):
   ```bash
   cd C:\Users\karzo\OneDrive\Bureau\study\lachgar\jaxrs
   ```

2. **Build the project** using Maven:
   ```bash
   mvnw.cmd clean install
   ```
   Or if you have Maven installed globally:
   ```bash
   mvn clean install
   ```

## ▶️ Running the Application

### Using Maven Wrapper (Recommended):
```bash
mvnw.cmd spring-boot:run
```

### Using Maven:
```bash
mvn spring-boot:run
```

### Using IDE:
Run the `JaxrsApplication.java` class directly from your IDE.

The application will start on **http://localhost:8080**

## 🌐 API Endpoints

### Base URL
```
http://localhost:8080/banque
```

### Available Endpoints

| Method | Endpoint | Description | Request Body | Response |
|--------|----------|-------------|--------------|----------|
| **GET** | `/banque/comptes` | Get all accounts | - | List of accounts (JSON/XML) |
| **GET** | `/banque/comptes/{id}` | Get account by ID | - | Account object (JSON/XML) |
| **POST** | `/banque/comptes` | Create new account | Compte object | Created account (JSON/XML) |
| **PUT** | `/banque/comptes/{id}` | Update existing account | Compte object | Updated account (JSON/XML) |
| **DELETE** | `/banque/comptes/{id}` | Delete account | - | No content |

### Data Model: Compte

```json
{
  "id": 1,
  "solde": 5432.10,
  "dateCreation": "2025-10-28",
  "type": 0
}
```

**Fields:**
- `id`: Long (auto-generated)
- `solde`: Double (account balance)
- `dateCreation`: Date (creation date)
- `type`: Integer (0=COURANT, 1=EPARGNE)

### Account Types (TypeCompte Enum)
- `COURANT` (0) - Current account
- `EPARGNE` (1) - Savings account

## 🧪 Testing the API

### 1. Get All Accounts (JSON)
```bash
curl -X GET http://localhost:8080/banque/comptes -H "Accept: application/json"
```

### 2. Get All Accounts (XML)
```bash
curl -X GET http://localhost:8080/banque/comptes -H "Accept: application/xml"
```

### 3. Get Account by ID
```bash
curl -X GET http://localhost:8080/banque/comptes/1 -H "Accept: application/json"
```

### 4. Create New Account (JSON)
```bash
curl -X POST http://localhost:8080/banque/comptes ^
  -H "Content-Type: application/json" ^
  -H "Accept: application/json" ^
  -d "{\"solde\":1500.50,\"dateCreation\":\"2025-10-28\",\"type\":1}"
```

### 5. Update Account
```bash
curl -X PUT http://localhost:8080/banque/comptes/1 ^
  -H "Content-Type: application/json" ^
  -H "Accept: application/json" ^
  -d "{\"solde\":2500.75,\"dateCreation\":\"2025-10-28\",\"type\":0}"
```

### 6. Delete Account
```bash
curl -X DELETE http://localhost:8080/banque/comptes/1
```

### Using Postman or Browser

You can also test the API using:
- **Postman**: Import the endpoints and test each operation
- **Browser**: Navigate to `http://localhost:8080/banque/comptes` to see all accounts in JSON format

## 💾 H2 Database Console

Access the H2 database console to view and query the data directly:

1. Navigate to: **http://localhost:8080/h2-console**
2. Use the following credentials:
   - **JDBC URL**: `jdbc:h2:mem:banque`
   - **Username**: `root`
   - **Password**: *(leave empty)*
3. Click **Connect**

You can run SQL queries like:
```sql
SELECT * FROM COMPTE;
```

## 📸 Screenshots

### 1. Application Results
<img width="1900" height="1137" alt="Results" src="https://github.com/user-attachments/assets/07411fd5-4bc1-483c-a2c6-bcae17f6f9d1" />

*Application console output showing Spring Boot startup with Jersey REST API enabled and sample data initialization*

### 2. GET Request - JSON Format

<img width="1602" height="1000" alt="Get request Json" src="https://github.com/user-attachments/assets/efe18686-1082-4066-b388-3eff54caf909" />

*Retrieve all bank accounts in JSON format using GET request to `/banque/comptes`*

### 3. GET Request - XML Format

<img width="1589" height="1012" alt="Get request XML" src="https://github.com/user-attachments/assets/e4f449b5-42d4-403a-acae-42fb5773d6c9" />

*Retrieve all bank accounts in XML format with Content-Type: application/xml header*

## 🔧 Configuration

### Application Properties (`application.properties`)

```properties
# Application name
spring.application.name=jaxrs

# H2 Database configuration
spring.datasource.url=jdbc:h2:mem:banque
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=root
spring.datasource.password=

# JPA/Hibernate configuration
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

# H2 Console configuration
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

# Jersey configuration
spring.jersey.application-path=/

# Server configuration
server.port=8080
```

## 📝 Key Components

### 1. Entity: Compte.java
Represents a bank account with JPA annotations for persistence and JAXB annotations for XML serialization.

### 2. Repository: CompteRepository.java
Spring Data JPA repository providing built-in CRUD operations.

### 3. REST Controller: CompteRest.java
JAX-RS resource class implementing REST endpoints with support for JSON and XML.

### 4. Configuration: MyConfig.java
Configures Jersey ResourceConfig and registers REST resources.

### 5. Main Application: JaxrsApplication.java
Spring Boot main class with CommandLineRunner to initialize sample data on startup.

## 🎓 Learning Objectives

This project demonstrates:
- ✅ Building REST APIs with JAX-RS (Jersey)
- ✅ Integrating Jersey with Spring Boot
- ✅ Using Spring Data JPA for data persistence
- ✅ Content negotiation (JSON/XML)
- ✅ H2 in-memory database setup
- ✅ Lombok annotations to reduce boilerplate
- ✅ RESTful API best practices

## 🐛 Troubleshooting

### Common Issues:

1. **Port 8080 already in use**
   - Change the port in `application.properties`: `server.port=8081`

2. **Maven dependency issues**
   - Run: `mvnw.cmd clean install -U` to force update dependencies

3. **Java version mismatch**
   - Ensure Java 21 is installed and set in your JAVA_HOME

4. **H2 Console not accessible**
   - Verify `spring.h2.console.enabled=true` in application.properties

## 📚 Additional Resources

- [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- [JAX-RS / Jersey Documentation](https://eclipse-ee4j.github.io/jersey/)
- [Spring Data JPA](https://spring.io/projects/spring-data-jpa)
- [H2 Database](https://www.h2database.com/)
- [Lombok](https://projectlombok.org/)

## 👨‍💻 Author

**Saad Karzouz**

- Date: October 2025


---



