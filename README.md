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

🔄 Workflow (Interns & Collaborators)

(Keep the fork/clone steps here same as before)

Just make sure you’re working inside the specific service folder, not the entire backend root.

⸻

✅ Pull Request Checklist (Updated)
	•	I worked in a specific microservice, not the monolith
	•	My service starts successfully (e.g., Docker or local run)
	•	I tested APIs manually or with unit tests
	•	I documented any new endpoints in the service README.md

⸻

📁 Folder Naming Guidelines (Updated)
	•	/backend/auth-service/
	•	/backend/product-service/
	•	/backend/order-service/
	•	/frontend/
	•	/docs/
	•	/infra/

Each service is responsible for:
	•	Its own models
	•	Routes
	•	Logic
	•	Database (can be shared or independent)
	•	Tests
	•	Dockerfile

⸻

🤝 Best Practices in Microservices
	•	Keep services decoupled
	•	Communicate between services using REST, gRPC, or message queues (RabbitMQ, etc. — if/when added)
	•	Handle failures gracefully (timeouts, retries)
	•	Write logs per service
	•	Use .env files or secret management (never hardcode)

⸻

💬 Communication Between Services

We’re using HTTP APIs for now. Document endpoints clearly in each service repo.

Coming soon: Shared API contracts (OpenAPI/Swagger) and service discovery.

⸻

💡 First-Time Contributors

Start with services like:
	•	auth-service
	•	product-service
	•	or tasks labeled good first issue

⸻

✨ You’re helping us build the next big thing — welcome to GazeOnTrade!

## 📖 API Documentation with Swagger (OpenAPI)

Each microservice *must include its own Swagger docs* using the appropriate library.

This allows:
- Developers to understand how to use your service
- Frontend to test endpoints without manual instructions
- Easy onboarding for new team members
- Future automation and integration

---

### ✅ Minimum Swagger Docs Must Include:
- Summary of what the endpoint does
- Input body & parameters (with types)
- Expected status codes (e.g. 200, 201, 400, 404, 500)
- Example requests & responses

---

### 🔧 How to Set Up Swagger per Framework

#### Flask (with flasgger)
```bash
pip install flasgger

In your app.py or Service main file:
Python
from flasgger import Swagger
app = Flask(_name_)
swagger = Swagger(app)

@app.route('/login', methods=['POST'])
def login():
    """
    User Login
    ---
    tags:
      - Auth
    parameters:
      - name: body
        in: body
        required: true
        schema:
          id: Login
          required:
            - email
            - password
          properties:
            email:
              type: string
            password:
              type: string
    responses:
      200:
        description: Successful login
      401:
        description: Invalid credentials
    """
    return jsonify(...)


cd backend/auth-service
docker-compose up --build
