# Airbnb Clone Project

## Overview
The Airbnb Clone Project is a full-stack application designed to simulate a real-world booking platform like Airbnb. The primary focus of this project is backend development, including robust API creation, database modeling, and deployment automation. This project enhances collaboration, security, and system design skills essential for building scalable applications.

### Project Goals
- Build a scalable booking system.
- Practice full-stack collaboration using GitHub workflows.
- Implement secure APIs and efficient CI/CD pipelines.
- Integrate Django, MySQL, and GraphQL in a unified backend stack.

---

## Team Roles

### Backend Developer
Responsible for building and maintaining server-side application logic using Django. This includes implementing business rules, handling API endpoints, and ensuring optimal performance.

### Database Administrator (DBA)
Designs, implements, and maintains the database system. Focuses on data integrity, indexing, backup strategies, and performance tuning.

### DevOps Engineer
Implements CI/CD pipelines and manages infrastructure automation using tools like GitHub Actions and Docker. Ensures seamless code deployment and monitoring.

### QA Engineer
Writes and executes test cases to ensure the application works as expected. Also implements automated tests and performs regression testing.

### Project Manager
Oversees project timelines, facilitates team collaboration, and ensures milestones are achieved according to plan.

---

## Technology Stack

- **Django**: Web framework for rapid development of secure and scalable APIs.
- **MySQL**: Relational database management system to store and query structured data.
- **GraphQL**: API query language to fetch precise data and reduce over-fetching/under-fetching issues.
- **Docker**: Containerization platform for environment consistency across development and production.
- **GitHub Actions**: CI/CD tool to automate testing, builds, and deployments.
- **Markdown**: For documentation and collaborative editing of README files and wiki pages.

---

## Database Design

### Key Entities

#### User
- `id`
- `username`
- `email`
- `password_hash`
- `date_joined`

#### Property
- `id`
- `host_id` (FK to User)
- `title`
- `description`
- `location`

#### Booking
- `id`
- `user_id` (FK to User)
- `property_id` (FK to Property)
- `start_date`
- `end_date`

#### Review
- `id`
- `user_id` (FK to User)
- `property_id` (FK to Property)
- `rating`
- `comment`

#### Payment
- `id`
- `booking_id` (FK to Booking)
- `amount`
- `payment_method`
- `status`

### Relationships
- A **user** can host multiple **properties**.
- A **booking** is associated with one **user** and one **property**.
- **Reviews** are linked to both **users** and **properties**.
- Each **booking** can have one **payment** record.

---

## Feature Breakdown

### User Management
Handles user registration, authentication, profile editing, and account settings. Crucial for personalized booking and property management.

### Property Management
Allows users to list, edit, and delete properties. Includes image uploads, location tagging, and availability settings.

### Booking System
Enables users to search, view, and book available properties for specific dates. Ensures date conflict validation and confirmation messaging.

### Review System
Permits users to leave ratings and comments for properties after their stay. Helps build credibility and improve property visibility.

### Payment Processing
Handles secure transactions, stores payment statuses, and integrates with payment gateways. Ensures transaction integrity.

---

## API Security

### Authentication
Implemented using token-based authentication (e.g., JWT). Ensures only authorized users can access protected endpoints.

### Authorization
Controls user access based on roles (e.g., guest, host, admin). Prevents unauthorized actions on resources.

### Rate Limiting
Prevents API abuse and brute-force attacks by limiting the number of requests per user/IP.

### Data Validation & Input Sanitization
Avoids SQL injection and XSS attacks by strictly validating incoming data.

### Secure Communication
Uses HTTPS to encrypt data in transit, protecting against man-in-the-middle attacks.

---

## CI/CD Pipeline

### What is CI/CD?
CI/CD (Continuous Integration/Continuous Deployment) automates the process of integrating code, running tests, and deploying updates to the application. It helps identify issues early, speeds up development, and ensures code quality.

### Tools Used
- **GitHub Actions**: Automates workflows like testing and deployment.
- **Docker**: Standardizes application environments across development and production.
- **pytest / unittest**: Runs automated test cases during integration.
- **Heroku / AWS / DigitalOcean** *(optional)*: For hosting the deployed application.

---

