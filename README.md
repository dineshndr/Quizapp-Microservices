Here’s a structured `README.md` file for your GitHub repository based on your description and typical best practices for microservice-based Java/Spring Boot applications:

---

# Quiz Application Microservices

This project demonstrates a **Quiz Application Microservice** communicating with a **Question Application Microservice** using an **API Gateway**. The architecture leverages **Spring Boot**, **Spring Cloud**, **Eureka Server** for service discovery, and **OpenFeign** for inter-service communication.

## 🧩 Microservices Overview

### 1. **Quiz Application Microservice**

* Handles quizzes and interacts with the Question microservice to fetch questions.
* Uses OpenFeign to consume REST APIs exposed by the Question service.

### 2. **Question Application Microservice**

* Manages the questions and exposes REST APIs.

### 3. **API Gateway**

* Routes incoming requests to the appropriate microservice.
* Central point for routing, load balancing, and filtering.

### 4. **Eureka Discovery Server**

* Enables service registration and discovery among microservices.

---

## 🔗 Microservice Communication

* The **Quiz Microservice** communicates with the **Question Microservice** through REST APIs.
* **OpenFeign Client** is used for simplified and declarative HTTP communication.
* **Service discovery** is enabled using **Eureka Server** to register and locate services dynamically.

```java
@FeignClient("QUESTION-MICROSERVICE-APP")
public interface QuizInterface {
    @GetMapping("question/generate")
    public ResponseEntity<List<Integer>> getQuestionsForQuiz(@RequestParam String categoryName, @RequestParam Integer numOfQuestions);

    @PostMapping("question/getQuestions")
    public ResponseEntity<List<QuestionWrapper>> getQuestionsFromId(@RequestBody List<Integer> questionIds);

    @PostMapping("question/getScore")
    public ResponseEntity<Integer> getScore(@RequestBody List<Response> responses);
}
```

---

## 🚀 How to Run the Application

### ✅ Prerequisites

Ensure the following are installed:

* Java 11+
* Maven
* Git

### 📥 Steps to Download and Run

```bash
# 1. Clone the repository
git clone https://github.com/your-username/Quizapp-Microservices.git
cd Quizapp-Microservices

# 2. Unzip and navigate to root folder
unzip Quizapp-Microservices-main.zip
cd Quizapp-Microservices-main
```

### 📦 Start Microservices in the following order

1. **Eureka Discovery Server**

   ```bash
   cd discovery-server
   mvn spring-boot:run
   ```

2. **Question Service**

   ```bash
   cd question-service
   mvn spring-boot:run
   ```

3. **Quiz Service**

   ```bash
   cd quiz-service
   mvn spring-boot:run
   ```

4. **API Gateway**

   ```bash
   cd api-gateway
   mvn spring-boot:run
   ```

### 🌐 Access Services

* **Eureka Dashboard**: `http://localhost:8761`
* **API Gateway Base URL**: `http://localhost:8080`

---

## 📚 Tech Stack

* Java
* Spring Boot
* Spring Cloud
* Eureka
* OpenFeign
* API Gateway
* Maven

---

## ✨ Features

* Microservice architecture with service discovery.
* RESTful API-based communication.
* OpenFeign integration for inter-service calls.
* Modular and scalable codebase.

---

Let me know if you'd like me to extract any specific service info from your `.zip` or further enhance the README with screenshots, database setup, Swagger docs, or Docker support.
