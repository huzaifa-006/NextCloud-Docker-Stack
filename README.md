🐳 Nextcloud Self-Hosted Cloud Stack (Multi-Service)

🚀 Project Title

Nextcloud Self-Hosted Cloud Stack (Docker Compose Deployment)

📝 Description

This project provides an Infrastructure-as-Code solution for deploying the popular Nextcloud platform. It uses Docker Compose to orchestrate two containers: the Nextcloud web server and a separate PostgreSQL/MariaDB database. This architecture is standard practice, ensuring scalability, security, and demonstrating proficiency in building robust, persistent, multi-container applications.

🛠️ Prerequisites

Docker Desktop: Required for running the containers and the docker-compose command.

.env File: Must be created in the root directory to securely store database credentials.

📦 Quick Start

Follow these steps to deploy the Nextcloud service stack:

Clone the repository:

git clone [repo-url]


Navigate into the folder:

cd nextcloud-docker-compose


Create the .env file with your desired database credentials and user.

Run the containers:

docker-compose up -d


Access the application: Wait 1-2 minutes for initialization, then open:

http://localhost:8080


💡 Key Configuration Explained

Configuration Detail

YAML Line

Why it's Important (DevOps Value)

Data Isolation

services: db / app

Clearly separates the application logic from the persistent data storage. This simplifies maintenance, backups, and scaling of each service independently.

Data Persistence

volumes: - ./data/nextcloud:/var/www/html

Creates a Bind Mount to save all user files, application configuration, and installed apps outside the container, ensuring data is never lost.

Port Mapping

ports: - "8080:80"

Maps the standard container web port (80) to a non-standard host port (8080) to prevent conflicts with other services already running on the host machine.

Inter-Service Networking

MYSQL_HOST=db

The application is configured to connect to the database container using its service name (db) because Docker Compose automatically creates an internal network where services can communicate by name.

Dependencies

depends_on: - db

Ensures the database starts before the application attempts to connect, increasing the reliability of the deployment process.

🛑 Stopping and Cleanup

To stop the containers while preserving all Nextcloud data and database records:

docker-compose down


To stop the containers and delete all user data, database records, and volumes (total reset):

docker-compose down -v
