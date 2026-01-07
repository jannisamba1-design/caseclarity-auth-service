.

🔐 CaseClarity – Auth Domain Service

A reactive, secure authentication and authorization microservice built using Spring Boot WebFlux, JWT, and RBAC, designed following enterprise microservices architecture patterns (inspired by Verizon SOE architecture).

📌 Overview

The Auth Domain Service is responsible for:

User registration (Signup)

User authentication (Login)

JWT access & refresh token generation

Role-based authorization (RBAC)

Admin-level user role management

Secure endpoint protection

This service is stateless, reactive, and designed for horizontal scalability.

🧠 Architecture Context
Client (React / Microsite)
|
API Gateway
|
Auth SOE (optional)
|
Auth Domain Service  ← (This Repo)
|
PostgreSQL (R2DBC)

Key Architectural Principles

Reactive stack (non-blocking I/O)

Domain-driven microservice

Security at service boundary

Separation of concerns

Interview-ready enterprise design

🛠 Technology Stack
Layer	Technology
Language	Java 21
Framework	Spring Boot 3.2.5
Web	Spring WebFlux
Security	Spring Security (Reactive)
Auth	JWT (Access + Refresh tokens)
Persistence	PostgreSQL (R2DBC)
Build Tool	Maven
Testing	JUnit 5, Mockito, WebTestClient
Coverage	JaCoCo
Containerization	Docker (optional)
🔐 Security Features

JWT-based stateless authentication

Access & Refresh token flow

Role-based authorization (USER, ADMIN)

Method-level security using @PreAuthorize

Custom JWT authentication filter

Secure reactive SecurityContext

📂 Project Structure
src/main/java/com/caseclarity/auth
├── config          # Security & application config
├── controller      # REST controllers
├── dto             # Request / Response DTOs
├── entity          # Domain entities
├── repository      # Reactive repositories
├── security        # JWT, filters, converters
├── service         # Business logic
└── AuthDomainServiceApplication.java

🚀 API Endpoints
Public Auth APIs
Method	Endpoint	Description
POST	/internal/auth/signup	User registration
POST	/internal/auth/login	User login
POST	/internal/auth/refresh	Refresh access token
Secured APIs
Method	Endpoint	Role
GET	/secure/user	USER
GET	/secure/admin	ADMIN
PATCH	/internal/admin/users/{id}/role	ADMIN
🧪 Testing Strategy

Unit tests for services & security utilities

Integration tests for controllers

Security tests for RBAC & authorization

Context load test for application startup

WebFlux reactive testing using WebTestClient

Run tests:

mvn clean test


Generate coverage:

mvn clean verify


Open report:

target/site/jacoco/index.html

📊 Code Coverage

Controllers: ~100%

Security Layer: ~90%

Services: ~85%

Overall: 80%+ (enterprise-grade)

Focused on meaningful coverage, not artificial 100%.

▶️ Running the Application
Prerequisites

Java 21

Maven 3.9+

PostgreSQL (Docker recommended)

Run PostgreSQL (Docker)
docker run -d \
--name auth-postgres \
-e POSTGRES_DB=auth_db \
-e POSTGRES_USER=postgres \
-e POSTGRES_PASSWORD=password \
-p 5432:5432 postgres:15

Run Application
mvn spring-boot:run

🧠 Interview Talking Points

Reactive authentication with WebFlux

Stateless JWT security

RBAC using method-level security

R2DBC vs JPA trade-offs

Microservice isolation & scalability

Test slicing vs full-context security tests

🔮 Future Enhancements

API Gateway (WebFlux)

SOE layer for UI-ready aggregation

OAuth2 / OIDC integration

Multi-tenant support

Rate limiting & audit logging

Kubernetes deployment

👨‍💻 Author

CaseClarity Platform
Designed as an enterprise-grade interview preparation project covering system design, microservices, reactive programming, and security best practices.