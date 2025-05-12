# Products Launcher Microservices

A modern e-commerce platform built with microservices architecture for scalable and maintainable online store operations.

## Technology Stack

### Core Technologies

- **Node.js**: Backend runtime environment
- **NestJS**: Primary framework for building microservices
- **TypeScript**: Type-safe development language

### Database Technologies

- **MongoDB**: Used by Auth microservice (MongoDB Atlas)
- **Prisma ORM**: Database interaction layer
- **SQLite**: Local development database (products-ms)
- **PostgreSQL**: Used by Orders microservice

### Infrastructure & DevOps

- **Docker**: Containerization
- **Docker Compose**: Local development and production orchestration
- **Kubernetes**: Container orchestration for deployment
- **Helm**: Kubernetes package manager

### Authentication & Security

- **JWT**: JSON Web Tokens for authentication
- **bcrypt**: Password hashing and security

### Payment Processing

- **Stripe**: Payment gateway integration

### API & Communication

- **Microservice Architecture**: NestJS microservices pattern
- **RESTful APIs**: Service communication
- **API Gateway Pattern**: Single entry point for clients

## Components

### Client Gateway (Port: 3000)

- API gateway for client requests
- Routes requests to appropriate microservices
- Handles client authentication

### Auth Microservice

- User authentication and authorization
- MongoDB Atlas database
- JWT token generation and validation

### Products Microservice

- Product catalog management
- SQLite database with Prisma ORM

### Orders Microservice

- Order processing and management
- PostgreSQL database

### Payments Microservice (Port: 3003)

- Payment processing
- Stripe integration
- Order payment status management

## Getting Started

### Prerequisites

- Node.js 21.x
- Docker and Docker Compose
- Git
- Kubernetes (for production deployment)

### Development Setup

1. Clone the repository with submodules:

   ```
   git clone <repository_url>
   cd products-launcher
   git submodule update --init --recursive
   ```

2. Install dependencies for each microservice:

   ```
   cd auth-ms && npm install
   cd ../client-gateway && npm install
   cd ../orders-ms && npm install
   cd ../payments-ms && npm install
   cd ../products-ms && npm install
   ```

3. Set up environment variables (create a .env file in each microservice directory)

4. Run the development environment:
   ```
   docker-compose up
   ```

### Steps to Create Git Submodules

1. Create a new repository on GitHub
2. Clone the repository to your local machine
3. Add the submodule, where `repository_url` is the URL of the repository and `directory_name` is the name of the folder where you want to store the sub-module (should not exist in the project)

```
git submodule add <repository_url> <directory_name>
```

4. Add the changes to the repository (git add, git commit, git push)
   Example:

```
git add .
git commit -m "Add submodule"
git push
```

5. Initialize and update Sub-modules, when someone clones the repository for the first time, they must execute the following command to initialize and update the sub-modules

```
git submodule update --init --recursive
```

6. To update the sub-module references

```
git submodule update --remote
```

## Production Build

```
docker compose -f docker-compose.prod.yml up
```

## Kubernetes Deployment

1. Ensure you have kubectl and Helm installed
2. Apply Kubernetes configurations:
   ```
   cd k8s/tienda
   helm install products-launcher .
   ```

## Important

If working in the repository that has sub-modules, **first update and push** in the sub-module and **then** in the main repository.

If done in reverse, sub-module references in the main repository will be lost and conflicts will need to be resolved.
