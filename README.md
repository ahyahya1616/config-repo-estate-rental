# RealEstate-Rental-Project Configuration Repository

This repository serves as the centralized configuration management for the [RealEstate-Rental-Project](https://github.com/RealEstate-Rental-Project) organization. It utilizes **Spring Cloud Config** to provide externalized configuration for all microservices in the ecosystem.

## 🏗️ Architecture Overview

The system is built on a microservices architecture where each service retrieves its settings from the [Config Service](https://github.com/RealEstate-Rental-Project/config-service-rental-estate).

- **Config Server:** `config-service-rental-estate`
- **Config Storage:** This repository (`config-repo-estate-rental`)
- **Discovery Service:** Eureka Server
- **API Gateway:** Spring Cloud Gateway

## 📂 Configuration Hierarchy

Configurations are organized using a hierarchical structure:

1.  **`application.yml` (Global):** Contains configurations shared across **all** microservices. This includes:
    *   Actuator endpoint exposure (health, info, metrics, etc.).
    *   Micrometer/Prometheus monitoring tags.
    *   Common logging levels for security and Feign clients.

2.  **Service-Specific Configs:** Files named `{service-name}.yml` contain settings unique to that specific service.

3.  **Environment Profiles:**
    *   **Default:** `{service-name}.yml`
    *   **Development:** `{service-name}-dev.yml`
    *   **Production:** `{service-name}-prod.yml`

## 🛠️ Microservices & Their Roles

| Service | Configuration File | Role & Key Features |
| :--- | :--- | :--- |
| **Gateway Service** | `gateway-service.yml` | Entry point of the system. Handles routing, CORS, Resilience4j (Circuit Breakers), and OAuth2 Resource Server configuration. |
| **User Management** | `user-management-service.yml` | Manages user profiles, registration, and Metamask wallet integrations. |
| **Auth Server** | `auth-server.yml` | Spring Authorization Server for handling OAuth2/OIDC, tokens, and JWKS. |
| **Property Service** | `property-microservice.yml` | Manages real estate listings and property data. |
| **Rental Agreement** | `RentalAgreement-microservice.yml` | Handles smart contracts, blockchain interaction (Web3j), and Kafka messaging for agreements. |
| **Notification** | `notification-service.yml` | Manages system notifications via REST and WebSocket. |
| **Eureka Service** | `eureka-service.yml` | Service discovery and registry settings. |

## 🚀 Key Technologies Configured

- **Resilience4j:** Circuit breakers and time limiters configured in the Gateway and Rental Agreement services.
- **Web3j:** Blockchain connectivity settings for smart contract interaction.
- **Kafka:** Message broker configuration for asynchronous communication.
- **OAuth2 / JWT:** Centralized security settings for token validation and issuance.
- **Actuator & Prometheus:** Standardized monitoring across the entire organization.

---

