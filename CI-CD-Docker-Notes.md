# CI/CD Pipeline & Docker Implementation Notes

## Project

**ShiftX – MERN Task Management Application**

---

# Objective

The goal of this task was to automate the project's build process using GitHub Actions (CI) and containerize the application using Docker so that it can run consistently across different environments.

---

# What is CI/CD?

**CI (Continuous Integration)** is the practice of automatically building and validating a project whenever code is pushed to GitHub. This helps detect errors early and ensures that the project remains in a working state.

**CD (Continuous Delivery/Deployment)** extends CI by preparing the application for deployment automatically after successful validation.

In this project, the CI part has been implemented using **GitHub Actions**.

---

# CI Pipeline Implementation

Separate GitHub Actions workflows were created for both the frontend and backend.

## Frontend Pipeline

The frontend workflow automatically:

* Triggers on every push and pull request to the `main` branch
* Installs all project dependencies
* Builds the React (Vite) application
* Fails if any build errors are detected

This ensures that the frontend always remains buildable.

---

## Backend Pipeline

The backend workflow automatically:

* Triggers on every push and pull request
* Installs all Node.js dependencies
* Verifies that the Express backend starts correctly
* Detects dependency or configuration issues before deployment

---

# Docker Implementation

Docker was used to package both applications into isolated containers.

## Frontend Container

The frontend uses a multi-stage Docker build:

* Node.js installs dependencies and builds the React application.
* Nginx serves the optimized production build.

This produces a lightweight production-ready container.

---

## Backend Container

The backend container:

* Uses Node.js
* Installs all dependencies
* Loads environment variables from the `.env` file
* Starts the Express server using `npm start`

---

# Docker Compose

Docker Compose was used to run both containers together.

It automatically:

* Builds both images
* Creates a shared Docker network
* Starts the frontend and backend together
* Connects both services in a single command

The project can be started using:

```bash
docker compose up --build
```

and stopped using:

```bash
docker compose down
```

---

# Technologies Used

* GitHub Actions
* Docker
* Docker Compose
* Node.js
* React (Vite)
* Express.js
* MongoDB
* Nginx

---

# Outcome

Successfully implemented:

* ✅ GitHub Actions CI pipeline
* ✅ Docker containerization
* ✅ Docker Compose orchestration
* ✅ Automated project build verification
* ✅ Production-ready frontend container using Nginx
* ✅ Containerized backend with environment variable support

The application now builds automatically through GitHub Actions and can be launched locally with Docker Compose using a single command.
