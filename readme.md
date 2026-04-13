# 🛒 Simple CRUD Products API

> Spring Boot REST API for managing products with embedded H2 database

[![Java](https://img.shields.io/badge/Java-17+-blue?logo=java)](https://www.oracle.com/java/technologies/downloads/#java17)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.0.5-green?logo=spring)](https://spring.io/projects/spring-boot)
[![Maven](https://img.shields.io/badge/Maven-3.8+-orange?logo=apache-maven)](https://maven.apache.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)

---

## 📋 Table of Contents

- [Prerequisites](#prerequisites)
- [Project Structure](#project-structure)
- [How to Build](#how-to-build)
- [How to Run](#how-to-run)
- [Testing API](#testing-api)
- [Database](#database)
- [API Documentation](#api-documentation)
- [Troubleshooting](#troubleshooting)

---

## 📌 Prerequisites

- **Java JDK 17+** - [Download](https://www.oracle.com/java/technologies/downloads/#java17) or [Adoptium](https://adoptium.net/temurin/releases/)
- **Maven 3.8+** - [Download](https://maven.apache.org/download.cgi) (or use system package manager)
- **Git** - for cloning the repository

### Verify Installation

```bash
java --version      # Should show Java 17+
mvn --version       # Should show Maven 3.8+

📁 Project Structure

simple-crud/
│
├── src/
│   ├── main/java/
│   │   └── com/softserve/academy/
│   │       ├── controller/      # REST endpoints
│   │       ├── service/         # Business logic
│   │       ├── repository/      # Data access
│   │       ├── entity/          # Models
│   │       └── Application.java # Main class
│   └── resources/
│       ├── application.properties
│       └── data.sql             # Initial DB data
│
├── pom.xml                      # Maven configuration
├── mvnw, mvnw.cmd             # Maven wrapper (optional)
├── simplecrud-endpoints.http   # API test examples
└── README.md

🔨 How to Build

git clone https://github.com/yourusername/simple-crud.git
cd simple-crud

Step 2: Build Project

# Using system Maven (recommended)
mvn clean package

# Or using Maven wrapper
chmod 755 ./mvnw
./mvnw clean package

Thinking
✅ ДА! Вот обновленный README
Замени весь текст на это:

markdown


# 🛒 Simple CRUD Products API

> Spring Boot REST API for managing products with embedded H2 database

[![Java](https://img.shields.io/badge/Java-17+-blue?logo=java)](https://www.oracle.com/java/technologies/downloads/#java17)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.0.5-green?logo=spring)](https://spring.io/projects/spring-boot)
[![Maven](https://img.shields.io/badge/Maven-3.8+-orange?logo=apache-maven)](https://maven.apache.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)

---

## 📋 Table of Contents

- [Prerequisites](#prerequisites)
- [Project Structure](#project-structure)
- [How to Build](#how-to-build)
- [How to Run](#how-to-run)
- [Testing API](#testing-api)
- [Database](#database)
- [API Documentation](#api-documentation)
- [Troubleshooting](#troubleshooting)

---

## 📌 Prerequisites

- **Java JDK 17+** - [Download](https://www.oracle.com/java/technologies/downloads/#java17) or [Adoptium](https://adoptium.net/temurin/releases/)
- **Maven 3.8+** - [Download](https://maven.apache.org/download.cgi) (or use system package manager)
- **Git** - for cloning the repository

### Verify Installation

```bash
java --version      # Should show Java 17+
mvn --version       # Should show Maven 3.8+
📁 Project Structure


simple-crud/
│
├── src/
│   ├── main/java/
│   │   └── com/softserve/academy/
│   │       ├── controller/      # REST endpoints
│   │       ├── service/         # Business logic
│   │       ├── repository/      # Data access
│   │       ├── entity/          # Models
│   │       └── Application.java # Main class
│   └── resources/
│       ├── application.properties
│       └── data.sql             # Initial DB data
│
├── pom.xml                      # Maven configuration
├── mvnw, mvnw.cmd             # Maven wrapper (optional)
├── simplecrud-endpoints.http   # API test examples
└── README.md
🔨 How to Build
Step 1: Clone Repository
bash


git clone https://github.com/yourusername/simple-crud.git
cd simple-crud
Step 2: Build Project
bash


# Using system Maven (recommended)
mvn clean package

# Or using Maven wrapper
chmod 755 ./mvnw
./mvnw clean package
First build takes ~2-3 minutes (downloads dependencies)

✅ Success: You should see BUILD SUCCESS

⚠️ If build fails: See Troubleshooting

🚀 How to Run
Start the Server

java -jar ./target/simplecrud-0.0.1-SNAPSHOT.jar --server.port=8080

Expected output:

Started Application in X seconds

⏱️ Server starts in ~15 seconds

✅ Runs at: http://localhost:8080

✅ Verify Server is Running
Option 1: curl

curl -s 'http://localhost:8080/actuator/health'

Expected response:

{"status":"UP"}

Option 2: Browser
Open: http://localhost:8080/swagger-ui/index.html

🧪 Testing API
Option 1: Swagger UI (Recommended) ✨
Open browser: http://localhost:8080/swagger-ui/index.html
Click on any endpoint
Click "Try it out"
Click "Execute"
See response!
Option 2: curl

# Get all products
curl -X GET http://localhost:8080/products | jq

# Get specific product
curl -X GET http://localhost:8080/products/1 | jq

# Create product
curl -X POST http://localhost:8080/products \
  -H "Content-Type: application/json" \
  -d '{"name":"Coffee","price":45.50}' | jq

# Update product
curl -X PUT http://localhost:8080/products/1 \
  -H "Content-Type: application/json" \
  -d '{"name":"Sugar","price":40.00}' | jq

# Delete product
curl -X DELETE http://localhost:8080/products/6 | jq

Option 3: HTTP File (VS Code)
Use simplecrud-endpoints.http with REST Client extension

🗄️ Database
Type: H2 (Embedded)

| Property | Value |
| :-- | :-- |
| File | ./productsDB.mv.db |
| JDBC URL | jdbc:h2:file:./productsDB |
| Username | sa |
| Password | (empty) |

Initial Data

[
  {"id":"1", "name":"Sugar", "price":32.00},
  {"id":"2", "name":"Salt", "price":19.00},
  {"id":"3", "name":"Bread", "price":20.00},
  {"id":"4", "name":"Butter", "price":62.00},
  {"id":"5", "name":"Milk", "price":32.00}
]

Access Database
Web Console: http://localhost:8080/h2

Use credentials above to connect

Reset Database: Delete ./productsDB.mv.db file and restart server

📚 API Documentation
Swagger UI (Interactive)

http://localhost:8080/swagger-ui/index.html

✨ Test API directly in browser without code!

Features:

📖 Full endpoint documentation
🧪 Try endpoints
📤 See request/response examples
✅ Automatic generation from code
API Endpoints

| Method | Endpoint | Description |
| :-- | :-- | :-- |
| GET | /products | Get all products |
| GET | /products/{id} | Get product by ID |
| POST | /products | Create new product |
| PUT | /products/{id} | Update product |
| DELETE | /products/{id} | Delete product |

Example Request/Response
GET /products

bash

curl http://localhost:8080/products

[
  {
    "id": 1,
    "name": "Sugar",
    "price": 32.0
  },
  {
    "id": 2,
    "name": "Salt",
    "price": 19.0
  }
]

📊 Monitoring
Health Check

http://localhost:8080/actuator/health

View Logs

http://localhost:8080/actuator/logfile

🛠️ Technologies

| Component | Version | Purpose |
| :-- | :-- | :-- |
| Java | 17+ | Programming Language |
| Spring Boot | 3.0.5 | Web Framework |
| Spring Data JPA | 3.0.4 | Database ORM |
| H2 | 2.1.214 | Embedded Database |
| Swagger/OpenAPI | 2.1.0 | API Documentation |
| Lombok | 1.18.30 | Code Generation |
| Maven | 3.8+ | Build Tool |

🐛 Troubleshooting
Issue: "BUILD FAILURE" - Lombok Error
Symptoms:

java.lang.NoSuchFieldError: Class com.sun.tools.javac.tree.JCTree$JCImport

Solution: Update pom.xml

<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>1.18.30</version>
    <scope>provided</scope>
</dependency>

Then add to maven-compiler-plugin:

<annotationProcessorPaths>
    <path>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
        <version>1.18.30</version>
    </path>
</annotationProcessorPaths>

Issue: "no main manifest attribute"
Solution: Add to pom.xml in <build><plugins>:

<plugin>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-maven-plugin</artifactId>
    <version>3.0.5</version>
</plugin>

Issue: Port 8080 Already in Use
Solution:

# Use different port
java -jar ./target/*.jar --server.port=9090

# Or kill existing process
lsof -ti:8080 | xargs kill -9

📚 Resources
Spring Boot Docs
Spring Data JPA
Swagger/OpenAPI
H2 Database
Maven Guide
👨‍💻 Author
Created as an educational project for learning Spring Boot REST API development.