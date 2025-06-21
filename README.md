# Airbnb Clone Project

## 🧭 Project Overview
The **Airbnb Clone Project** is a full-stack web application that replicates core features of the Airbnb platform. It is designed for learners to gain practical experience with backend development, API design, database modeling, CI/CD workflows, and secure application deployment.

### 🎯 Project Goals
- Understand backend system design and architecture.
- Implement secure and scalable RESTful and GraphQL APIs.
- Learn collaborative software development using GitHub.
- Build a functional database schema using MySQL.
- Set up and manage CI/CD pipelines for automated deployment.
- Apply modern DevOps tools (Docker, GitHub Actions).

---

## 👥 Team Roles

| Role | Description |
|------|-------------|
| **Backend Developer** | Builds the business logic and API endpoints using Django. |
| **Database Administrator (DBA)** | Designs and manages the MySQL schema, ensures data integrity and performance. |
| **DevOps Engineer** | Sets up CI/CD pipelines, manages Docker containers and deployment environments. |
| **Project Manager** | Oversees task distribution, timelines, and documentation efforts. |
| **Security Engineer** | Implements security best practices including API protection, authentication, and data encryption. |

---

## 🧰 Technology Stack

| Technology | Purpose |
|------------|---------|
| **Django** | A high-level Python framework for building secure, scalable backends. |
| **MySQL** | Relational database system for storing users, listings, bookings, and reviews. |
| **GraphQL** | API query language used for flexible and efficient data fetching. |
| **Docker** | Containerizes the application for consistent deployment across environments. |
| **GitHub Actions** | Automates CI/CD workflows for testing, building, and deploying the application. |

---

## 🧱 Database Design

### Entities and Fields

#### 1. **User**
- `user_id` (Primary Key)
- `email`
- `password_hash`
- `full_name`
- `date_joined`

#### 2. **Property**
- `property_id` (Primary Key)
- `owner_id` (Foreign Key → User)
- `title`
- `description`
- `location`
- `price_per_night`

#### 3. **Booking**
- `booking_id` (Primary Key)
- `user_id` (Foreign Key → User)
- `property_id` (Foreign Key → Property)
- `check_in_date`
- `check_out_date`
- `total_price`

#### 4. **Review**
- `review_id` (Primary Key)
- `booking_id` (Foreign Key → Booking)
- `rating` (1–5)
- `comment`
- `review_date`

#### 5. **Payment**
- `payment_id` (Primary Key)
- `booking_id` (Foreign Key → Booking)
- `amount`
- `payment_method`
- `payment_status`

### Relationships
- A **User** can have many **Bookings** and many **Properties**.
- A **Property** can have many **Bookings**.
- A **Booking** has one **Payment** and may have one **Review**.

---

## 🚀 Feature Breakdown

- **User Registration & Login** (with authentication)
- **Property Listing Management** (create, update, delete listings)
- **Search & Filtering** for available properties
- **Booking System** (select dates, calculate price)
- **Review System** (submit and view feedback)
- **Payment Integration** (mock or real gateway support)
- **Admin Dashboard** (for managing users and listings)

---

## 🔐 API Security

- **Authentication**: Uses token-based auth (JWT) for secure access.
- **Authorization**: Role-based permissions to restrict access to sensitive actions.
- **Rate Limiting**: Prevents abuse by limiting API calls per user/IP.
- **Input Validation & Sanitization**: Protects against SQL injection and XSS.
- **HTTPS/TLS**: Ensures encrypted data transmission.

---

## 🔄 CI/CD Pipeline

### What is CI/CD?
CI/CD stands for **Continuous Integration** and **Continuous Deployment**. It is a set of practices that enable teams to deliver code changes more frequently and reliably.

### Benefits
- Speeds up the release cycle.
- Automatically runs tests on every push or pull request.
- Reduces manual errors in the deployment process.
- Ensures consistent deployment environments.

### Tools Used
- **GitHub Actions**: Automates testing, building, and deploying the app.
- **Docker**: Creates a consistent development and production environment.
- **Shell Scripts**: Used to automate database migrations and service restart

- Entities and Attributes
User
user_id: Primary Key, UUID, Indexed
first_name: VARCHAR, NOT NULL
last_name: VARCHAR, NOT NULL
email: VARCHAR, UNIQUE, NOT NULL
password_hash: VARCHAR, NOT NULL
phone_number: VARCHAR, NULL
role: ENUM (guest, host, admin), NOT NULL
created_at: TIMESTAMP, DEFAULT CURRENT_TIMESTAMP
Property
property_id: Primary Key, UUID, Indexed
host_id: Foreign Key, references User(user_id)
name: VARCHAR, NOT NULL
description: TEXT, NOT NULL
location: VARCHAR, NOT NULL
pricepernight: DECIMAL, NOT NULL
created_at: TIMESTAMP, DEFAULT CURRENT_TIMESTAMP
updated_at: TIMESTAMP, ON UPDATE CURRENT_TIMESTAMP
Booking
booking_id: Primary Key, UUID, Indexed
property_id: Foreign Key, references Property(property_id)
user_id: Foreign Key, references User(user_id)
start_date: DATE, NOT NULL
end_date: DATE, NOT NULL
total_price: DECIMAL, NOT NULL
status: ENUM (pending, confirmed, canceled), NOT NULL
created_at: TIMESTAMP, DEFAULT CURRENT_TIMESTAMP
Payment
payment_id: Primary Key, UUID, Indexed
booking_id: Foreign Key, references Booking(booking_id)
amount: DECIMAL, NOT NULL
payment_date: TIMESTAMP, DEFAULT CURRENT_TIMESTAMP
payment_method: ENUM (credit_card, paypal, stripe), NOT NULL
Review
review_id: Primary Key, UUID, Indexed
property_id: Foreign Key, references Property(property_id)
user_id: Foreign Key, references User(user_id)
rating: INTEGER, CHECK: rating >= 1 AND rating <= 5, NOT NULL
comment: TEXT, NOT NULL
created_at: TIMESTAMP, DEFAULT CURRENT_TIMESTAMP
Message
message_id: Primary Key, UUID, Indexed
sender_id: Foreign Key, references User(user_id)
recipient_id: Foreign Key, references User(user_id)
message_body: TEXT, NOT NULL
sent_at: TIMESTAMP, DEFAULT CURRENT_TIMESTAMP
Constraints
User Table
Unique constraint on email.
Non-null constraints on required fields.
Property Table
Foreign key constraint on host_id.
Non-null constraints on essential attributes.
Booking Table
Foreign key constraints on property_id and user_id.
status must be one of pending, confirmed, or canceled.
Payment Table
Foreign key constraint on booking_id, ensuring payment is linked to valid bookings.
Review Table
Constraints on rating values (1-5).
Foreign key constraints on property_id and user_id.
Message Table
Foreign key constraints on sender_id and recipient_id.
Indexing
Primary Keys: Indexed automatically.
Additional Indexes:
email in the User table.
property_id in the Property and Booking tables.
booking_id in the Booking and Payment tables.
