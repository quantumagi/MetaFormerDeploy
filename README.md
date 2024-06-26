# MetaFormer Deployment Repository

## Overview
This repository contains the Docker configuration necessary to deploy the MetaFormer application, a full-stack web application with a Django backend, Celery for background task processing, PostgreSQL as the database, Redis as the message broker, and a React.js frontend.

## Prerequisites
Before proceeding with the deployment, ensure that you have the following installed:
- Docker
- Docker Compose

## Quick Start
To get the application up and running, follow these steps:

1. Clone the repository to your local machine.
   ```sh
   git clone https://github.com/quantumagi/MetaFormerDeploy.git
   ```

2. Navigate to the cloned directory.
   ```sh
   cd MetaFormerDeploy
   ```

3. Add or edit the .env file in the project root:
   ```sh
   SUPERUSER_USERNAME=testuser
   SUPERUSER_EMAIL=test@example.com
   SUPERUSER_PASSWORD=testpassword
   DB_NAME=postgres
   DB_USER=postgres
   DB_PASSWORD=postgres
   DB_PORT=5432
   DEBUG=1
   ```

4. Build and start the containers.
   ```sh
   docker compose up
   ```
   or
   ```sh
   docker-compose up
   ```

This will start the various services as specified in docker-compose.yml. The Django application will perform database migrations, create the Django SQLite super-user, and start the development server. The Celery worker will also start, and the React frontend will be available on port 3000.

### Services
The docker-compose.yml file defines the following services:

- db: PostgreSQL database service.
- redis: Redis service used as a message broker for Celery.
- django: The Django web application service with a local Sqlite user database.
- celery: The Celery worker service for processing background tasks.
- frontend: The React.js frontend service.

### Accessing the Application
Once the containers are up, the following ports will be exposed:

- Django API: http://localhost:8000/api
- Django Admin: http://localhost:8000/admin
- React Frontend: http://localhost:3000

### License
This project is licensed under the MIT License - see the LICENSE.md file for details.







