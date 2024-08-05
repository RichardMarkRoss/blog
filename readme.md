# Blog Platform Project

This project consists of a frontend built with Nuxt.js and a backend API built with Laravel. The entire setup is containerized using Docker and managed with Docker Compose.

## Prerequisites

Before running the application, ensure you have the following installed on your machine:

- **Docker**: [Install Docker](https://docs.docker.com/get-docker/)
- **Docker Compose**: Docker Compose comes bundled with Docker Desktop, but you can [install it separately](https://docs.docker.com/compose/install/) if needed.

## Getting Started

Follow these instructions to get the project up and running on your local machine.

### 1. Clone the Repository

Clone the project repository to your local machine.

```bash
git clone <repository-url>
cd <repository-directory>
```

 ### 2. Environment Setup
Ensure that the environment variables are correctly set up in the .env files.

Backend (7-blog-backend/.env):

```bash
# env
APP_NAME=Laravel
APP_ENV=local
APP_KEY=base64:8VJeOVwQ/6EjIfZpytXAWroHBoQKdvcOT9fO4oxZs4A=
APP_DEBUG=true
APP_URL=http://localhost

LOG_CHANNEL=stack
LOG_DEPRECATIONS_CHANNEL=null
LOG_LEVEL=debug

DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=blog
DB_USERNAME=user
DB_PASSWORD=password

BROADCAST_DRIVER=log
CACHE_DRIVER=file
FILESYSTEM_DISK=local
QUEUE_CONNECTION=sync
SESSION_DRIVER=database
SESSION_LIFETIME=120

MEMCACHED_HOST=127.0.0.1

REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379

MAIL_MAILER=smtp
MAIL_HOST=mailpit
MAIL_PORT=1025
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null
MAIL_FROM_ADDRESS="hello@example.com"
MAIL_FROM_NAME="${APP_NAME}"

AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_DEFAULT_REGION=us-east-1
AWS_BUCKET=
AWS_USE_PATH_STYLE_ENDPOINT=false

PUSHER_APP_ID=
PUSHER_APP_KEY=
PUSHER_APP_SECRET=
PUSHER_HOST=
PUSHER_PORT=443
PUSHER_SCHEME=https
PUSHER_APP_CLUSTER=mt1

VITE_APP_NAME="${APP_NAME}"
VITE_PUSHER_APP_KEY="${PUSHER_APP_KEY}"
VITE_PUSHER_HOST="${PUSHER_HOST}"
VITE_PUSHER_PORT="${PUSHER_PORT}"
VITE_PUSHER_SCHEME="${PUSHER_SCHEME}"
VITE_PUSHER_APP_CLUSTER="${PUSHER_APP_CLUSTER}"
```
### 3. Build and Run the Containers
Use Docker Compose to build and start the containers. This command will build the images, set up the services, and start the containers.

bash
Copy code
docker-compose up --build
This command will:

Build the frontend and backend Docker images.
Set up the MySQL database.
Run the Laravel backend and Nuxt.js frontend services.
### 4. Access the Application
Once the containers are up and running, you can access the different parts of the application:

Backend API: http://localhost:9000
Frontend: http://localhost:3000
### 5. Stopping the Containers
To stop the running containers, use:

bash
Copy code
docker-compose down
This command stops and removes all containers defined in the Docker Compose file, but it does not remove the built images or volumes.

### 6. Database Initialization
The Laravel backend is set up to automatically run migrations and seeders on startup. If you need to manually run migrations or seed the database, you can do so by accessing the backend container:

```bash
docker-compose exec backend php artisan migrate --force
docker-compose exec backend php artisan db:seed --force
```
Additional Notes
Mailpit: If you're using Mailpit for email testing, you can access its web interface at http://localhost:8025.
Logs and Debugging: Check the container logs for any issues or errors. You can view logs using docker-compose logs.
Troubleshooting
Build Failures: If the build fails, check the error messages for clues. Ensure all dependencies are correctly specified and accessible.
Network Issues: Ensure your Docker network settings are correctly configured if you encounter network-related issues.
Contributing
Contributions are welcome! Please fork this repository and submit pull requests for any changes.

### License
This project is licensed under the MIT License - see the LICENSE file for details.

### Notes

- **Environment Variables**: Make sure the `.env` files contain the correct settings, especially for database connections.
- **Docker Compose Commands**: The `docker-compose up --build` command builds and runs the containers, while `docker-compose down` stops them.
- **Database Management**: Migrations and seeders should be run automatically on startup, but you can also do this manually.
- **Mailpit**: If included in your setup, access the Mailpit web interface for testing email functionalities.
- **Logs and Debugging**: Use Docker logs to troubleshoot issues during setup or runtime.