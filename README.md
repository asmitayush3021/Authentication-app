
# 🔐 Full Stack Authentication App

A complete **Full Stack Authentication Application** built with **React + Vite** on the frontend and **Spring Boot** on the backend.

The application provides secure authentication using **JWT**, **Google OAuth2**, and **GitHub OAuth2**.

---

## 🚀 Features

- 🔐 Username & Password Authentication
- 🎫 JWT-based Authentication
- 🔄 Access Token & Refresh Token
- 🌐 Google OAuth2 Login
- 🐙 GitHub OAuth2 Login
- 🛡️ Spring Security
- 👤 User Registration & Login
- 🔒 Protected APIs
- 🗄️ MySQL Database
- ⚡ React + Vite Frontend
- 📡 REST APIs
- 🍃 Spring Data JPA
- 🐳 Docker support for backend

---

# 🧱 Tech Stack

## 🖥️ Frontend

- React
- Vite
- Tailwind CSS
- Axios
- React Router DOM
- ShadCN UI

## ⚙️ Backend

- Java
- Spring Boot 3.x
- Spring Security 6.x
- Spring Data JPA
- MySQL
- OAuth2 Client
- JWT
- Lombok
- HikariCP
- Maven

## 🛠️ Tools

- Git
- GitHub
- Docker
- IntelliJ IDEA / VS Code
- Postman

---

# 📸 Screenshots

## 🏠 Home Page

<img src="auth%20app/screenshots/sc1.png" alt="Home Page" width="900"/>

---

## 🔐 Login Page

<img src="auth%20app/screenshots/sc2.png" alt="Login Page" width="900"/>

---

## ❌ Login Error

<img src="auth%20app/screenshots/sc3.png" alt="Login Error" width="900"/>

---

## 📝 Register Page

<img src="auth%20app/screenshots/sc4.png" alt="Register Page" width="900"/>

---

## 📊 Dashboard

<img src="auth%20app/screenshots/sc5.png" alt="Dashboard" width="900"/>

---

# 📁 Project Structure

```text
Authentication-app/
│
├── auth app/
│   │
│   ├── auth-backend/
│   │   ├── .mvn/
│   │   ├── src/
│   │   ├── .env
│   │   ├── Dockerfile
│   │   ├── mvnw
│   │   ├── mvnw.cmd
│   │   └── pom.xml
│   │
│   ├── auth-front/
│   │   ├── src/
│   │   ├── public/
│   │   ├── package.json
│   │   ├── vite.config.js
│   │   └── ...
│   │
│   ├── screenshots/
│   │   ├── sc1.png
│   │   ├── sc2.png
│   │   ├── sc3.png
│   │   ├── sc4.png
│   │   └── sc5.png
│   │
│   └── .gitignore
│
└── README.md
````

---

# 🔐 Authentication Architecture

The application uses **Spring Security + JWT + OAuth2** for authentication.

### Username / Password Flow

```text
┌──────────────┐
│ React Client │
└──────┬───────┘
       │
       │ Login Request
       ▼
┌──────────────────┐
│ Spring Boot API  │
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│ Spring Security  │
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│ MySQL Database   │
└────────┬─────────┘
         │
         ▼
   Generate JWT
         │
         ▼
┌──────────────────┐
│ React Application │
└──────────────────┘
```

---

# 🌐 OAuth2 Authentication

The application supports authentication through:

* Google
* GitHub

### Google / GitHub OAuth2 Flow

```text
┌──────────────┐
│ React Client │
└──────┬───────┘
       │
       ▼
┌─────────────────┐
│ Spring Security │
│     OAuth2      │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Google / GitHub │
└────────┬────────┘
         │
         │ OAuth Callback
         ▼
┌─────────────────┐
│ Spring Boot API │
└────────┬────────┘
         │
         ▼
     Generate JWT
         │
         ▼
┌──────────────┐
│ React Client │
└──────────────┘
```

---

# 🎫 JWT Authentication

JWT is used to authenticate requests after successful login.

The application uses:

* Access Token
* Refresh Token
* Token Expiration
* Token Refresh
* Secure Authentication Cookies

### Token Flow

```text
Login
  │
  ▼
Validate Credentials
  │
  ▼
Generate Access Token
  │
  ▼
Generate Refresh Token
  │
  ▼
Authenticated Requests
  │
  ▼
Access Token Expires
  │
  ▼
Refresh Token
  │
  ▼
Generate New Access Token
```

---

# ⚙️ Backend Setup

## Prerequisites

Install the following:

* Java 17 or higher
* Maven 3.9+
* MySQL 8+
* Git
* Docker (optional)

---

## 1. Clone the Repository

```bash
git clone https://github.com/asmitayush3021/Authentication-app.git
```

Navigate into the project:

```bash
cd Authentication-app
```

---

## 2. Navigate to Backend

```bash
cd "auth app/auth-backend"
```

---

## 3. Create MySQL Database

Open MySQL and execute:

```sql
CREATE DATABASE auth_app;
```

---

## 4. Configure Environment Variables

Create a `.env` file inside:

```text
auth app/auth-backend/.env
```

Add the following:

```env
JWT_SECRET=your-random-long-secret

GOOGLE_CLIENT_ID=your-google-client-id
GOOGLE_CLIENT_SECRET=your-google-client-secret

GITHUB_CLIENT_ID=your-github-client-id
GITHUB_CLIENT_SECRET=your-github-client-secret
```

> ⚠️ Never commit your actual `.env` file or OAuth secrets to GitHub.

---

# 🔑 Google OAuth2 Configuration

Create OAuth credentials from Google Cloud Console.

Configure the redirect URI according to your Spring Boot application.

Example:

```text
http://localhost:8081/login/oauth2/code/google
```

Then configure:

```env
GOOGLE_CLIENT_ID=your-client-id
GOOGLE_CLIENT_SECRET=your-client-secret
```

---

# 🐙 GitHub OAuth2 Configuration

Create an OAuth application in GitHub Developer Settings.

Use the callback URL:

```text
http://localhost:8081/login/oauth2/code/github
```

Then configure:

```env
GITHUB_CLIENT_ID=your-client-id
GITHUB_CLIENT_SECRET=your-client-secret
```

---

# ▶️ Run Backend

Using Maven:

```bash
mvn spring-boot:run
```

Or on Windows:

```bash
.\mvnw.cmd spring-boot:run
```

The backend will start on:

```text
http://localhost:8081
```

---

# 💻 Frontend Setup

Open another terminal.

Navigate to the frontend:

```bash
cd "auth app/auth-front"
```

Install dependencies:

```bash
npm install
```

---

## Configure Frontend Environment

Create:

```text
auth app/auth-front/.env
```

Add:

```env
VITE_BACKEND_URL=http://localhost:8081
```

---

## ▶️ Run Frontend

```bash
npm run dev
```

The frontend will normally be available at:

```text
http://localhost:5173
```

---

# 🔗 API Endpoints

| Method | Endpoint                       | Description                    |
| ------ | ------------------------------ | ------------------------------ |
| `POST` | `/api/auth/register`           | Register a new user            |
| `POST` | `/api/auth/login`              | Login using username/password  |
| `GET`  | `/api/auth/me`                 | Get current authenticated user |
| `POST` | `/api/auth/refresh`            | Refresh access token           |
| `POST` | `/api/auth/logout`             | Logout user                    |
| `GET`  | `/oauth2/authorization/google` | Google OAuth2 login            |
| `GET`  | `/oauth2/authorization/github` | GitHub OAuth2 login            |

---

# 🧩 Authentication Endpoints

### Register

```http
POST /api/auth/register
```

Used to create a new user account.

---

### Login

```http
POST /api/auth/login
```

Authenticates a user using username and password.

---

### Current User

```http
GET /api/auth/me
```

Returns information about the currently authenticated user.

---

### Refresh Token

```http
POST /api/auth/refresh
```

Generates a new access token using the refresh token.

---

### Logout

```http
POST /api/auth/logout
```

Logs out the current user and clears authentication tokens.

---

# 🔑 Environment Variables

| Variable               | Description                            |
| ---------------------- | -------------------------------------- |
| `JWT_SECRET`           | Secret key used for signing JWT tokens |
| `GOOGLE_CLIENT_ID`     | Google OAuth2 Client ID                |
| `GOOGLE_CLIENT_SECRET` | Google OAuth2 Client Secret            |
| `GITHUB_CLIENT_ID`     | GitHub OAuth2 Client ID                |
| `GITHUB_CLIENT_SECRET` | GitHub OAuth2 Client Secret            |
| `VITE_BACKEND_URL`     | Backend URL used by React              |

---

# 🗄️ Database

The application uses:

```text
MySQL
   │
   ▼
Spring Data JPA
   │
   ▼
Hibernate
   │
   ▼
Spring Boot
```

Database configuration is provided through environment variables/application configuration.

Hibernate can automatically manage the database schema using:

```yaml
spring:
  jpa:
    hibernate:
      ddl-auto: update
```

---

# 🐳 Docker

The backend contains a `Dockerfile` and can be containerized.

Build the Docker image:

```bash
docker build -t auth-backend .
```

Run the container:

```bash
docker run -p 8081:8081 auth-backend
```

The backend will then be available at:

```text
http://localhost:8081
```

---

# 🧰 Common Commands

## Backend

Run application:

```bash
mvn spring-boot:run
```

Build application:

```bash
mvn clean package
```

Run JAR:

```bash
java -jar target/*.jar
```

---

## Frontend

Install dependencies:

```bash
npm install
```

Run development server:

```bash
npm run dev
```

Build production version:

```bash
npm run build
```

Preview production build:

```bash
npm run preview
```

---

# 🔒 Security Considerations

For production deployment:

* Use HTTPS.
* Never expose JWT secrets.
* Never commit `.env` files.
* Use secure cookies.
* Configure appropriate CORS policies.
* Use strong JWT secrets.
* Store OAuth credentials securely.
* Use production database credentials.
* Enable secure cookie settings.
* Implement rate limiting where appropriate.

---

# 🚀 Future Improvements

* [ ] Docker Compose
* [ ] Redis integration
* [ ] Email verification
* [ ] Forgot password
* [ ] Password reset
* [ ] Role-Based Access Control
* [ ] Admin Dashboard
* [ ] Rate Limiting
* [ ] Email Notifications
* [ ] CI/CD Pipeline
* [ ] AWS Deployment
* [ ] Kubernetes Deployment
* [ ] Production HTTPS

---

# 📚 Concepts Demonstrated

This project demonstrates practical implementation of:

* Spring Boot
* Spring Security
* Authentication & Authorization
* JWT
* OAuth2
* Google OAuth2
* GitHub OAuth2
* REST APIs
* Spring Data JPA
* Hibernate
* MySQL
* React
* Vite
* Axios
* React Router
* Docker
* Environment Variables
* Secure Authentication

---

# 👨‍💻 Author

## Asmit Kumar Singh

**Java Backend Developer | Spring Boot | Microservices**

---

# ⭐ Support

If you found this project useful, consider giving the repository a ⭐ on GitHub.

````

