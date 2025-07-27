# 🏥 Patient Management System – Microservices-Based Application

This project is a **microservices-based patient management system** built using **Java 21**, **Spring Boot**, and modern DevOps practices. It simulates a real-world healthcare system with **patient registration**, **billing**, **authentication**, **analytics**, and **API gateway routing**. The goal of this system is to demonstrate a complete, production-like architecture covering development, containerization, inter-service communication, and deployment.

---
## 📐 Architecture Diagram

<img width="1139" height="557" alt="PM-System" src="https://github.com/user-attachments/assets/95c5bf17-7959-41f2-8754-3b54b59c080d" />

---

## 🚀 Features

- **Patient Service**: CRUD operations for patient records
- **Billing Service**: Generates billing account using **gRPC**
- **Analytics Service**: Listens to Kafka events for patient creation
- **Auth Service**: Generates and validates **JWT tokens**
- **API Gateway**: Routes external API calls to internal services using **Spring Cloud Gateway**
- **Asynchronous communication** using **Apache Kafka**
- **PostgreSQL** as the persistent database for key services
- **Dockerized** architecture with shared networking
- **Integration Testing** for core services
- **Infrastructure as Code (IaC)** using **LocalStack** to simulate AWS deployment

---

## 🧱 Microservices Overview

| Service         | Role                                                                 |
|----------------|----------------------------------------------------------------------|
| `patient-service`   | REST CRUD APIs for patient records, gRPC call to billing, Kafka producer |
| `billing-service`   | gRPC server to create billing accounts                             |
| `analytics-service` | Kafka consumer to process and analyze patient events               |
| `auth-service`      | JWT-based authentication & authorization                          |
| `api-gateway`       | Single entry point to route all API requests                      |

---

## 🛠️ Technologies Used

- **Java 21**, **Spring Boot**
- **Spring Cloud Gateway**
- **gRPC with Protocol Buffers**
- **Apache Kafka**
- **JWT Token for Authentication**
- **PostgreSQL**
- **Docker & Docker Compose**
- **Spring Security**
- **Integration Testing** (with Testcontainers/JUnit)
- **LocalStack** for AWS simulation
- **Layered Architecture** (Controller, Service, Repository, DTO)

---

## ☁️ AWS Cloud Transformation (LocalStack)
This project includes Infrastructure as Code (IaC) and is tested locally with LocalStack to simulate AWS:
- Deploys containers to simulated AWS ECS

---

## 🔐 Authentication Workflow (JWT)
Call auth-service to authenticate and receive a JWT token.
- Pass the token in headers like:
- Authorization: Bearer <token>
- All internal APIs validate JWT using the shared key.

---
## 📦 gRPC Communication (Billing)
- gRPC is used between patient-service and billing-service.
- When a patient is created, the patient service makes a gRPC call to create the billing account.
- Protocol Buffers are defined in proto/ and compiled during build.

## 📊 Kafka Messaging (Analytics)
- Kafka broker is deployed via Docker.
- patient-service acts as producer and publishes patient creation events.
- analytics-service consumes messages from Kafka.

