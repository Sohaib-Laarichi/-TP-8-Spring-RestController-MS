# 🏦 TP 8 - Spring Boot REST API for Bank Account Management

## 📖 Project Overview

A comprehensive Spring Boot REST API designed for banking operations management. This enterprise-grade application provides a complete CRUD system for bank account management with support for multiple data formats and modern Spring Boot architecture patterns.

## ✨ Key Features

- 🔗 **RESTful API Architecture**: Complete CRUD operations with proper HTTP status codes
- 📊 **Multi-format Support**: Seamless JSON/XML content negotiation
- 💾 **H2 In-Memory Database**: Fast development and testing environment
- 🛡️ **CORS Configuration**: Cross-origin requests enabled for frontend integration
- 📚 **API Documentation**: Interactive Swagger UI with OpenAPI 3.0
- ⚡ **Lombok Integration**: Clean, boilerplate-free code
- 🔄 **Auto Data Population**: Sample data loaded on startup
- 🖥️ **H2 Console**: Web-based database management interface

## 🛠️ Technology Stack

| Technology | Version | Purpose |
|------------|---------|---------|
| **Java** | 17 | Core programming language |
| **Spring Boot** | 3.5.7 | Application framework |
| **Spring Web** | Latest | REST API development |
| **Spring Data JPA** | Latest | Data persistence layer |
| **H2 Database** | Latest | In-memory database |
| **Lombok** | Latest | Code generation |
| **Jackson XML** | Latest | XML serialization |
| **SpringDoc OpenAPI** | 2.8.3 | API documentation |

## 🚀 Quick Start

### Prerequisites
- Java 17 or higher
- Maven 3.6+ (or use included wrapper)

### Running the Application

```bash
# Clone the repository
git clone <repository-url>

# Navigate to project directory
cd "TP 8  Spring @RestController"

# Run with Maven wrapper
./mvnw spring-boot:run

# Or on Windows
mvnw.cmd spring-boot:run
```

### Access Points
- 🌐 **Application**: `http://localhost:8082`
- 🔍 **H2 Console**: `http://localhost:8082/h2-console`
- 📖 **API Documentation**: `http://localhost:8082/swagger-ui.html`

## 📡 API Reference

### Base URL: `http://localhost:8082/banque`

| HTTP Method | Endpoint | Description | Request Body | Response |
|-------------|----------|-------------|--------------|----------|
| `GET` | `/comptes` | Retrieve all accounts | - | Array of accounts |
| `GET` | `/comptes/{id}` | Get account by ID | - | Single account |
| `POST` | `/comptes` | Create new account | Account object | Created account |
| `PUT` | `/comptes/{id}` | Update existing account | Account object | Updated account |
| `DELETE` | `/comptes/{id}` | Delete account | - | 200 OK or 404 |

### Request/Response Format

Both JSON and XML formats are supported. Set appropriate `Content-Type` and `Accept` headers:

- **JSON**: `application/json`
- **XML**: `application/xml`

### Account Entity Schema

```json
{
  "id": 1,
  "solde": 5000.0,
  "dateCreation": "2025-11-01",
  "type": "COURANT"
}
```

### Account Types
- `COURANT` - Current/Checking account
- `EPARGNE` - Savings account

## ⚙️ Configuration

### Database Configuration
```properties
spring.datasource.url=jdbc:h2:mem:banque
spring.datasource.username=sa
spring.datasource.password=
spring.h2.console.enabled=true
```

### Server Configuration
```properties
server.port=8082
spring.jpa.hibernate.ddl-auto=update
```

## 🧪 Testing Examples

### Create Account (JSON)
```bash
curl -X POST http://localhost:8082/banque/comptes \
  -H "Content-Type: application/json" \
  -d '{"solde": 1000.0, "dateCreation": "2025-11-01", "type": "COURANT"}'
```

### Get All Accounts (XML)
```bash
curl -X GET http://localhost:8082/banque/comptes \
  -H "Accept: application/xml"
```

### Update Account
```bash
curl -X PUT http://localhost:8082/banque/comptes/1 \
  -H "Content-Type: application/json" \
  -d '{"solde": 1500.0, "dateCreation": "2025-11-01", "type": "EPARGNE"}'
```

## 🏗️ Project Structure

```
src/
├── main/
│   ├── java/com/example/Tp8/
│   │   ├── Tp8Application.java          # Main application class
│   │   ├── config/
│   │   │   └── WebConfig.java           # CORS configuration
│   │   ├── controllers/
│   │   │   └── CompteController.java    # REST endpoints
│   │   ├── entities/
│   │   │   ├── Compte.java             # Account entity
│   │   │   └── TypeCompte.java         # Account type enum
│   │   └── repositories/
│   │       └── CompteRepository.java    # Data access layer
│   └── resources/
│       └── application.properties       # Configuration
└── test/
    └── java/com/example/Tp8/
        └── Tp8ApplicationTests.java     # Unit tests
```

## 🔧 Development Features

- **Hot Reload**: Spring DevTools enabled for rapid development
- **Auto Schema Generation**: Database tables created automatically
- **Sample Data**: Three accounts pre-loaded for testing
- **Error Handling**: Proper HTTP status codes and responses
- **Validation Ready**: Bean validation framework integrated

## API Testing Demonstration

## Create account :
### JSON :
<img width="1917" height="973" alt="CreateJSON" src="https://github.com/user-attachments/assets/e20e2c15-0899-421a-9b7b-3b7c723fe2ce" />

### XML :
<img width="1919" height="963" alt="CreateXML" src="https://github.com/user-attachments/assets/f0afa70f-4674-45d6-b94e-e7e7e6d8c6d6" />

## Update account :
### JSON :
<img width="1919" height="972" alt="UpdateJSON" src="https://github.com/user-attachments/assets/c6ebaa6f-94ea-4e19-ace4-ce6e5f7b891a" />

### XML :
<img width="1919" height="977" alt="UpdateXML" src="https://github.com/user-attachments/assets/c59d652d-815f-4d2f-899f-4525135e34e7" />

## Delete account :
<img width="1919" height="983" alt="DeleteAcc" src="https://github.com/user-attachments/assets/e8459ad3-5e5d-45e9-ae90-e659827ecb22" />

## Get accounts :
### JSON :
<img width="1919" height="969" alt="GetJSON" src="https://github.com/user-attachments/assets/4c57cf45-b107-4f3a-977f-66ac24179be4" />

### XML :
<img width="1919" height="982" alt="GetXML" src="https://github.com/user-attachments/assets/06be9de5-02f2-4428-9ed1-4bf135543455" />
