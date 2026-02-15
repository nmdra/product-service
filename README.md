# Product Service - Spring Boot Microservice

A RESTful microservice built with Spring Boot that provides CRUD operations for products, uses H2 in-memory database, and includes Swagger API documentation.

## Overview

This microservice manages product information with the following features:
- RESTful API endpoints for Create, Read, and Delete operations
- H2 in-memory database for data persistence
- Swagger UI for API documentation and testing
- Spring Data JPA for database operations
- Maven build system

## Technologies Used

- **Spring Boot 3.2.2**
- **Java 17**
- **Spring Web** - RESTful API implementation
- **Spring Data JPA** - Database operations
- **H2 Database** - In-memory database
- **Springdoc OpenAPI** - Swagger documentation
- **Maven** - Build and dependency management

## Project Structure

```
product-service/
├── src/
│   └── main/
│       ├── java/
│       │   └── com/
│       │       └── sliit/
│       │           └── productservice/
│       │               ├── ProductServiceApplication.java
│       │               ├── model/
│       │               │   └── Product.java
│       │               ├── repository/
│       │               │   └── ProductRepository.java
│       │               └── controller/
│       │                   └── ProductController.java
│       └── resources/
│           └── application.properties
├── pom.xml
└── README.md
```

## Prerequisites

- Java 17 or higher
- Maven 3.6 or higher

## How to Run the Application

### 1. Clone the repository
```bash
git clone https://github.com/nmdra/product-service.git
cd product-service
```

### 2. Build the project
```bash
mvn clean install
```

### 3. Run the application
```bash
mvn spring-boot:run
```

Alternatively, you can run the JAR file:
```bash
java -jar target/product-service-0.0.1-SNAPSHOT.jar
```

The application will start on **http://localhost:8080**

## API Endpoints

### Base URL
```
http://localhost:8080/api/products
```

### Available Endpoints

| Method | Endpoint | Description | Request Body | Response |
|--------|----------|-------------|--------------|----------|
| POST | `/api/products` | Create a new product | `{"name": "Product Name", "price": 99.99}` | 201 Created |
| GET | `/api/products` | Get all products | - | 200 OK |
| GET | `/api/products/{id}` | Get product by ID | - | 200 OK / 404 Not Found |
| DELETE | `/api/products/{id}` | Delete product by ID | - | 204 No Content / 404 Not Found |

### Example Requests

#### Create a Product
```bash
curl -X POST http://localhost:8080/api/products \
  -H "Content-Type: application/json" \
  -d '{"name": "Laptop", "price": 999.99}'
```

#### Get All Products
```bash
curl http://localhost:8080/api/products
```

#### Get Product by ID
```bash
curl http://localhost:8080/api/products/1
```

#### Delete a Product
```bash
curl -X DELETE http://localhost:8080/api/products/1
```

## Accessing Swagger UI

The Swagger UI provides an interactive interface to explore and test the API endpoints.

**URL**: http://localhost:8080/swagger-ui.html

**Alternative URL**: http://localhost:8080/swagger-ui/index.html

Through Swagger UI, you can:
- View all available API endpoints
- See request/response schemas
- Test API endpoints directly from the browser
- View API documentation

## Accessing H2 Database Console

The H2 console provides a web-based interface to view and query the in-memory database.

**URL**: http://localhost:8080/h2-console

### Connection Settings:
- **JDBC URL**: `jdbc:h2:mem:productdb`
- **User Name**: `sa`
- **Password**: (leave empty)

Click "Connect" to access the database console and run SQL queries.

## Product Model

```java
{
  "id": 1,              // Auto-generated (Long)
  "name": "Product Name", // String
  "price": 99.99        // Double
}
```

## HTTP Status Codes

- **200 OK** - Successful GET request
- **201 Created** - Successful POST request (product created)
- **204 No Content** - Successful DELETE request
- **404 Not Found** - Resource not found

## Testing

Run unit tests:
```bash
mvn test
```

## Building for Production

To create a production-ready JAR file:
```bash
mvn clean package
```

The JAR file will be created in the `target/` directory.

## Configuration

All configuration is in `src/main/resources/application.properties`:
- Database configuration
- JPA/Hibernate settings
- H2 console settings

