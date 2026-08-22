<div align="center">

# Cafe Aurora API

### REST API for managing customers, products, and orders for a small coffee shop

![Java](https://img.shields.io/badge/Java-17-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.2.5-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![Spring Data JPA](https://img.shields.io/badge/Spring%20Data%20JPA-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white)
![H2](https://img.shields.io/badge/H2%20Database-1E5B94?style=for-the-badge&logo=h2&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)

</div>

---

## Overview

A REST API that models the backend of a small coffee shop, Cafe Aurora.
It manages customers, products, and orders, and exposes CRUD endpoints
for each of them, built on top of Spring Boot and Spring Data JPA.

## Features

- Full CRUD for **Customers**
- Full CRUD for **Products**
- Full CRUD for **Orders**
- Optional `PUT` update support for all three resources
- Relational persistence via Spring Data JPA
- JSON responses with proper HTTP status codes (`201`, `204`, `404`)

## Tech stack

| Technology | Purpose |
|---|---|
| **Java 17** | Core language |
| **Spring Boot 3.2.5** | Application framework |
| **Spring Web (MVC)** | REST endpoint layer |
| **Spring Data JPA** | Object-relational mapping |
| **H2 Database** | Default file-based relational database |
| **MySQL** | Optional production-style database |
| **Maven** | Build and dependency management |
| **Postman** | Manual API testing |

## Project structure

```
cafe-aurora-api/
├── pom.xml
└── src/main/
    ├── java/com/cafearora/api/
    │   ├── CafeAuroraApiApplication.java
    │   ├── model/
    │   │   ├── Cliente.java
    │   │   ├── Produto.java
    │   │   └── Pedido.java
    │   ├── repository/
    │   │   ├── ClienteRepository.java
    │   │   ├── ProdutoRepository.java
    │   │   └── PedidoRepository.java
    │   └── controller/
    │       ├── ClienteController.java
    │       ├── ProdutoController.java
    │       └── PedidoController.java
    └── resources/
        └── application.properties
```

## Getting started

### Requirements
- JDK 17+
- Maven (or an IDE that bundles it, such as Eclipse or IntelliJ)

### Run it

```bash
git clone https://github.com/YOUR_USERNAME/cafe-aurora-api.git
cd cafe-aurora-api
mvn spring-boot:run
```

Or, from an IDE: import as an existing Maven project and run
`CafeAuroraApiApplication.java` as a Java application.

The API starts at `http://localhost:8080`.

## API reference

### Customers (`/clientes`)

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/clientes` | Create a customer |
| `GET` | `/clientes` | List all customers |
| `GET` | `/clientes/{id}` | Get a customer by ID |
| `PUT` | `/clientes/{id}` | Update a customer *(optional)* |
| `DELETE` | `/clientes/{id}` | Delete a customer |

### Products (`/produtos`)

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/produtos` | Create a product |
| `GET` | `/produtos` | List all products |
| `GET` | `/produtos/{id}` | Get a product by ID |
| `PUT` | `/produtos/{id}` | Update a product *(optional)* |
| `DELETE` | `/produtos/{id}` | Delete a product |

### Orders (`/pedidos`)

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/pedidos` | Create an order |
| `GET` | `/pedidos` | List all orders |
| `GET` | `/pedidos/{id}` | Get an order by ID |
| `PUT` | `/pedidos/{id}` | Update an order *(optional)* |
| `DELETE` | `/pedidos/{id}` | Delete an order |

## Example requests

Create a customer:

```http
POST http://localhost:8080/clientes
Content-Type: application/json

{
  "nome": "Ana Torres",
  "clienteDesde": "2026-08-22"
}
```

Create a product:

```http
POST http://localhost:8080/produtos
Content-Type: application/json

{
  "nome": "Cafe Bourbon Amarelo 250g",
  "preco": 32.90,
  "estoque": true
}
```

Create an order:

```http
POST http://localhost:8080/pedidos
Content-Type: application/json

{
  "clienteId": 1,
  "produtoId": 1,
  "quantidade": 3
}
```

## Database

By default, the project runs on **H2**, a file-based relational database —
no separate installation required. With the app running, the web console
is available at:

```
http://localhost:8080/h2-console
```

- **JDBC URL:** `jdbc:h2:file:./data/cafeauroradb`
- **Username:** `sa`
- **Password:** *(blank)*

To switch to MySQL, update `application.properties` — the alternate
configuration is already included there, commented out.

## License

This project is open for personal and educational use.
