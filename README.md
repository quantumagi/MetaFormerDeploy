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

3. Add an .env file with the credentials of the Django Sqlite database.
   ```sh
   SUPERUSER_USERNAME=testuser
   SUPERUSER_EMAIL=test@example.com
   SUPERUSER_PASSWORD=testpassword
   ```

4. Build and start the containers.
   ```sh
   docker-compose up --build
   ```

This will start the various services as specified in docker-compose.yml. The Django application will perform database migrations, create a test user (if in DEBUG mode), and start the development server. The Celery worker will also start, and the React frontend will be available on port 3000.

### Services
The docker-compose.yml file defines the following services:

- db: PostgreSQL database service.
- redis: Redis service used as a message broker for Celery.
- django: The Django web application service.
- celery: The Celery worker service for processing background tasks.
- frontend: The React.js frontend service.

### Configuration
The deployment can be configured using environment variables in the docker-compose.yml file. For local development, you can set DEBUG=1 to enable Django's debug mode.

***Important***: Never deploy to production with DEBUG set to True.

### Custom Management Command
A custom management command create_test_user is included to create a test user when starting the Django service in development mode.

### Volumes
Persistent data for the PostgreSQL database and shared files between Django and Celery are managed using Docker volumes, as specified in the docker-compose.yml file.

### Accessing the Application
Once the containers are up, the following ports will be exposed:

- Django: http://localhost:8000
- React Frontend: http://localhost:3000

### License
This project is licensed under the MIT License - see the LICENSE.md file for details.







