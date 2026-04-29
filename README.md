# 📢 User Notification Preference & Delivery API

A complete Spring Boot REST API that allows managing users, configuring their notification preferences, and sending notifications based on those preferences.

---

## ✨ Features

### 👤 User Management

* Create a new user
* Fetch user by ID
* Retrieve all users

### 🔔 Notification Preferences

* Enable/Disable Email, SMS, Push notifications
* Store preferences per user

### 📬 Notification Delivery

* Send notifications based on user preferences
* Supports multi-channel logic (Email/SMS/Push simulation)

---

## 📁 Project Structure

```
src/main/java/com/yourpackage/
│
├── controller/        # REST Controllers (API layer)
├── service/           # Business logic
├── repository/        # Database access layer (JPA)
├── entity/            # Database models (Entities)
├── config/            # Configuration (Security, etc.)
└── dto/               # Request/Response objects (optional)
```

---

## ⚙️ Setup Instructions

### 1. Clone Repository

```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
```

---

### 2. Configure MySQL Database

Create a database:

```sql
CREATE DATABASE notification_db;
```

Update `application.properties`:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/deliveryAPI
spring.datasource.username=root
spring.datasource.password=root


spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.database-platform=org.hibernate.dialect.MySQLDialect

server.port=8080
```

---

### 3. Run Application

```bash
mvn spring-boot:run
```

Server runs at:

```
http://localhost:8080
```

---

## 📡 API Endpoints

---

### 👤 User APIs

#### ➤ Create User

```
POST /users
```

Request:

```json
{
  "name": "Nikhil",
  "email": "nikhil@example.com",
  "phone": "9876543210"
}
```

---

#### ➤ Get User by ID

```
GET /users/{id}
```

---

#### ➤ Get All Users

```
GET /users
```

---

### 🔔 Notification Preference APIs

#### ➤ Set Preferences

```
POST /preferences
```

Request:

```json
{
  "userId": 1,
  "emailEnabled": true,
  "smsEnabled": false,
  "pushEnabled": true
}
```

---

#### ➤ Get Preferences

```
GET /preferences/{userId}
```

---

### 📬 Notification APIs

#### ➤ Send Notification

```
POST /notifications/send
```

Request:

```json
{
  "userId": 1,
  "message": "Hello! This is a test notification"
}
```

---

## 🔄 Workflow

1. Create a user
2. Set notification preferences
3. Send notification
4. System checks preferences
5. Notification delivered via enabled channels

---

## 🗄️ Database Design

### 🧾 User Table

| Column | Type      |
| ------ | --------- |
| id     | Long (PK) |
| name   | String    |
| email  | String    |
| phone  | String    |

---

### 🔔 Notification Preference Table

| Column        | Type      |
| ------------- | --------- |
| id            | Long (PK) |
| user_id       | Long (FK) |
| email_enabled | Boolean   |
| sms_enabled   | Boolean   |
| push_enabled  | Boolean   |

---

## 🧪 Testing (Postman)

* Use **Content-Type: application/json**
* Test flow:

  1. Create User
  2. Set Preferences
  3. Send Notification


## 📌 Use Cases

* Notification systems (apps/web platforms)
* User preference management systems
* Backend microservice design practice

