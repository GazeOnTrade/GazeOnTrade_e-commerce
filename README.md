# 👋 Contributing to GazeOnTrade

Welcome to GazeOnTrade! We’re building a powerful, scalable e-commerce platform using a *microservice architecture* on the backend. This allows us to move fast, scale efficiently, and assign responsibilities clearly across services.

Please read this guide before contributing!

---

## 🧭 Project Structure

### 📦 Backend Architecture (Microservices)

Each backend feature runs as an independent microservice.

| Service Name     | Description                           | Tech Stack        |
|------------------|---------------------------------------|-------------------|
| auth-service   | Handles user login, signup, sessions  | Python (Flask)    |
| product-service| Manages products, categories, 3D try-on | Django/Flask      |
| order-service  | Manages cart, checkout, and payments  | Python (FastAPI)  |
| user-service   | User profile management               | Flask             |
| notification-service | Sends email/SMS/push alerts     | Node.js/Flask     |
| ai-recommender | AI recommendation engine              | Python (FastAPI)  |
| admin-service | Manages user verification, moderate    | Python (Flask)
                  listing and activity logs

Each service has its own folder, Dockerfile, and can be deployed independently.

### 🧱 Frontend

Monorepo or single repo (based on your setup) using *Next.js* and API calls to microservices.

---

## 🧭 Where to Start

1. Pick a service you're interested in from the /backend folder.
2. Read its README.md (if available).
3. Follow setup instructions and start developing in isolation.
4. Communicate with the team if your feature spans multiple services.

---

## 🚀 Local Development with Docker

Each service can be spun up individually using Docker:

```bash
cd backend/auth-service
docker-compose up --build
