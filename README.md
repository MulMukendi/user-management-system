# User Management System

A full-stack User Management System built to demonstrate modern backend development using **Spring Boot**, **React**, **MySQL**, **Redis**, and **Docker**. The application allows users to be created, searched, updated, and deleted while showcasing production-ready backend concepts such as RESTful APIs, server-side caching, containerization, and environment-based configuration.

---

## Features

- Create new users
- View all users
- Search users by first name
- View individual user details
- Update existing users
- Delete users
- Display the total number of users
- Display the three most recently added users
- Display the average age of all users
- Display the number of users created today
- Responsive React frontend
- RESTful Spring Boot backend
- Redis caching for improved performance
- Global exception handling
- Duplicate email and username validation
- Dockerized frontend, backend, MySQL, and Redis

---

## Tech Stack

### Frontend

- React
- Axios
- React Router
- CSS

### Backend

- Java 17
- Spring Boot
- Spring Data JPA
- Spring Cache
- Redis
- MySQL
- Maven

### Development Tools

- Docker
- Docker Compose
- Git
- GitHub
- IntelliJ IDEA
- Postman

---

## Architecture

```text
React Frontend
       │
       ▼
Spring Boot REST API
       │
       ├────────► Redis Cache
       │
       ▼
 MySQL Database
```

---

## Caching

This project uses **Spring Cache** with **Redis** to improve application performance by reducing unnecessary database queries.

The following data is cached:

- User by ID
- All users
- Total number of users
- Average user age
- Three most recently added users
- Number of users created today

Caches are automatically invalidated whenever a user is created, updated, or deleted to ensure cached data remains consistent with the database.

---

# Prerequisites

Before running the project, install:

- Docker Desktop
- Git

---

# Getting Started

## 1. Clone the repository

```bash
git clone <repository-url>
cd "User Management System"
```

---

## 2. Configure Docker

In the project root, rename:

```text
.env.example
```

to

```text
.env
```

Open the `.env` file and change the MySQL password:

```properties
MYSQL_PASSWORD=your_password
```

The remaining values should remain as follows:

```properties
MYSQL_HOST=mysql
MYSQL_PORT=3306
MYSQL_DATABASE=usersystem
MYSQL_USERNAME=root

REDIS_HOST=redis
REDIS_PORT=6379
```

---

## 3. Configure the Frontend

Navigate to:

```text
frontend/usersystem-ui
```

Rename:

```text
.env.example
```

to

```text
.env
```

The default value is:

```properties
VITE_API_URL=http://localhost:8080
```

This is the URL the React application uses to communicate with the backend.

---

## 4. Start the Application

Make sure Docker Desktop is running.

Then execute:

```bash
docker compose up --build -d
```

Docker Compose will automatically:

- Build the React frontend
- Build the Spring Boot backend
- Create the MySQL database
- Create the Redis server
- Connect all services together

---

## 5. Access the Application

Frontend:

```text
http://localhost:5173
```

Backend:

```text
http://localhost:8080/users
```

---

## Configuration

### Root `.env`

The root `.env` file contains the environment variables required by Docker Compose.

These variables are supplied to the backend and database containers when they start.

### Frontend `.env`

The frontend has its own `.env` file containing:

```properties
VITE_API_URL=http://localhost:8080
```

This allows the frontend to communicate with the backend without hardcoding the API URL.

### application-docker.properties

The backend uses `application-docker.properties` whenever the Docker profile is active.

Spring Boot automatically reads the environment variables provided by Docker Compose and uses them to configure:

- MySQL
- Redis

---

## API Endpoints

| Method | Endpoint                             | Description                |
| ------ | ------------------------------------ | -------------------------- |
| GET    | `/users`                             | Get all users              |
| GET    | `/users/{id}`                        | Get user by ID             |
| GET    | `/users/search?firstName=`           | Search users by first name |
| POST   | `/users`                             | Create a user              |
| PUT    | `/users/{id}`                        | Update a user              |
| DELETE | `/users/{id}`                        | Delete a user              |
| GET    | `/users/dashboard/stats/count`       | Total users                |
| GET    | `/users/recent`                      | Three most recent users    |
| GET    | `/users/dashboard/stats/average-age` | Average user age           |
| GET    | `/users/dashboard/stats/new-today`   | Users created today        |

---

## Future Improvements

- JWT Authentication
- Role-based authorization
- Pagination and sorting
- Advanced filtering
- Redis cache expiration (TTL)
- Unit and integration testing
- API documentation with Swagger/OpenAPI
- CI/CD pipeline
- Cloud deployment (AWS)

---

## Learning Objectives

This project was built to gain hands-on experience with:

- Spring Boot
- REST API development
- Spring Data JPA
- Redis caching
- Docker & Docker Compose
- Environment variables
- MySQL
- React
- Full-stack application architecture
- Git & GitHub

---

## Author

**Mulumba Mukendi**

Computer Science student passionate about backend development, cloud technologies, and building scalable web applications.
