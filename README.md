# 🚗 Vehicle Insurance Management System - Microservices Architecture

## 📌 Overview

A microservices-based system for managing vehicle insurance policies and claims. This system enables customers to:
- Register their vehicles,
- Purchase insurance policies,
- Raise claims against policies,
- View claim status.

---

## 🧱 Architecture

### Microservices Involved

| Service              | Description                                                              |
|----------------------|--------------------------------------------------------------------------|
| `eureka-server`       | Central service registry using Spring Cloud Eureka                      |
| `api-gateway`         | Entry point to the system using Spring Cloud Gateway                    |
| `policy-service`      | Handles policy issuance and vehicle details                             |
| `claim-service`       | Handles insurance claims and communicates with Policy Service           |

---

## 🔁 Service Communication

- **Claim Service → Policy Service** using **OpenFeign** for vehicle & policy validation.
- **Policy Service → RabbitMQ** publishes events when new policy is issued.
- **Claim Service** listens to **RabbitMQ** for policy creation events.
- All services register with **Eureka**.
- API Gateway handles routing and filtering.

---

## 📌 Key Features

| Feature                          | Implementation Details                                        |
|----------------------------------|----------------------------------------------------------------|
| ✅ Multiple Microservices         | `Policy Service`, `Claim Service`                             |
| ✅ Exception Handling             | Global handler using `@ControllerAdvice`                      |
| ✅ Validation                     | DTO-level validation with `javax.validation`                  |
| ✅ Eureka Server                  | Spring Cloud Eureka-based discovery                           |
| ✅ API Gateway                    | Spring Cloud Gateway routes to services                       |
| ✅ OpenFeign                     | Claim → Policy validation                                     |
| ✅ CircuitBreaker                | Resilience4j for fallback in Feign calls                      |
| ✅ RabbitMQ                      | Policy events are published & consumed                        |
| ✅ Dockerized Services            | Dockerfiles + Docker Compose setup                            |
| ✅ H2 / MySQL Support             | H2 for dev/test, MySQL for production                         |

---

## 🛠️ Tech Stack

- Java 17+
- Spring Boot 3.x
- Spring Cloud (Gateway, Eureka, OpenFeign)
- RabbitMQ (Message Broker)
- Resilience4j (Circuit Breaker)
- H2 / MySQL (Persistence)
- Docker & Docker Compose

---

## 📂 Project Structure

```bash
vehicle-insurance-system/
│
├── eureka-server/
├── api-gateway/
├── policy-service/
├── claim-service/
├── docker-compose.yml
└── README.md
