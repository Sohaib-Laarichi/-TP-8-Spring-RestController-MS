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

## 🧪 API Testing Demonstration

Cette section présente des captures d'écran réelles des tests de l'API, démontrant le fonctionnement de tous les endpoints CRUD avec les formats JSON et XML.

## 📝 Create Account (Création de compte)

### 🔵 Format JSON
*Démonstration de la création d'un nouveau compte bancaire via une requête POST avec un payload JSON. L'image montre la structure de la requête, les headers nécessaires, et la réponse du serveur avec le compte créé incluant l'ID auto-généré.*

<img width="1917" height="973" alt="CreateJSON" src="https://github.com/user-attachments/assets/e20e2c15-0899-421a-9b7b-3b7c723fe2ce" />

### 🟠 Format XML
*Même opération de création de compte mais utilisant le format XML. Cette capture illustre la capacité de l'API à gérer la négociation de contenu et à accepter/retourner des données au format XML grâce à la configuration Jackson XML.*

<img width="1919" height="963" alt="CreateXML" src="https://github.com/user-attachments/assets/f0afa70f-4674-45d6-b94e-e7e7e6d8c6d6" />

## ✏️ Update Account (Modification de compte)

### 🔵 Format JSON
*Test de mise à jour d'un compte existant via PUT request. L'image montre comment modifier les propriétés d'un compte (solde, type, date) en utilisant l'ID du compte dans l'URL et en envoyant les nouvelles données au format JSON.*

<img width="1919" height="972" alt="UpdateJSON" src="https://github.com/user-attachments/assets/c6ebaa6f-94ea-4e19-ace4-ce6e5f7b891a" />

### 🟠 Format XML
*Démonstration de la même fonctionnalité de mise à jour mais avec des données XML. Cette capture prouve que l'API peut traiter les modifications de comptes indépendamment du format de données utilisé.*

<img width="1919" height="977" alt="UpdateXML" src="https://github.com/user-attachments/assets/c59d652d-815f-4d2f-899f-4525135e34e7" />

## 🗑️ Delete Account (Suppression de compte)
*Test de suppression d'un compte via une requête DELETE. L'image illustre l'utilisation de l'endpoint DELETE avec l'ID du compte dans l'URL et la réponse du serveur confirmant la suppression (status code 200 OK).*

<img width="1919" height="983" alt="DeleteAcc" src="https://github.com/user-attachments/assets/e8459ad3-5e5d-45e9-ae90-e659827ecb22" />

## 📋 Get Accounts (Récupération des comptes)

### 🔵 Format JSON
*Démonstration de la récupération de tous les comptes via une requête GET. L'image montre la réponse JSON contenant la liste complète des comptes avec toutes leurs propriétés (ID, solde, date de création, type).*

<img width="1919" height="969" alt="GetJSON" src="https://github.com/user-attachments/assets/4c57cf45-b107-4f3a-977f-66ac24179be4" />

### 🟠 Format XML
*Même opération de récupération des comptes mais avec une réponse au format XML. Cette capture démontre la capacité de l'API à sérialiser automatiquement les données Java en XML grâce à la configuration Spring Boot et Jackson XML.*

<img width="1919" height="982" alt="GetXML" src="https://github.com/user-attachments/assets/06be9de5-02f2-4428-9ed1-4bf135543455" />

## 🎯 Points Techniques Démontrés

- ✅ **Négociation de contenu** : Headers `Accept` et `Content-Type` appropriés
- ✅ **Codes de statut HTTP** : 200 OK, 201 Created, 404 Not Found
- ✅ **Sérialisation automatique** : Conversion Java ↔ JSON/XML
- ✅ **Validation des endpoints** : Tous les endpoints CRUD fonctionnels
- ✅ **Gestion des erreurs** : Responses appropriées pour les ressources inexistantes
- ✅ **Structure REST** : URLs cohérentes et méthodes HTTP appropriées
