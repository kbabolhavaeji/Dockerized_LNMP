# Dockerized PHP Application with Nginx, MySQL, Redis, and PHPMyAdmin

This repository contains a Dockerized setup for a PHP application. It includes the following services:

- **Nginx**: Serves as the reverse proxy and web server.
- **PHP-FPM**: Runs your PHP application.
- **MySQL**: The database for storing application data.
- **Redis**: For in-memory caching.
- **PHPMyAdmin**: A web-based GUI for managing the MySQL database.

## Prerequisites

Ensure you have the following installed on your system:

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Project Structure

```bash

├── docker/
│   ├── nginx/
│   │   └── app.conf   # Nginx configuration file
│   ├── php/
│   │   └── php.ini    # Custom PHP configuration
│   ├── app/
│   │   └── Dockerfile # Dockerfile for the PHP application
├── .env               # Environment variables
├── docker-compose.yml # Docker Compose configuration
└── README.md   
```

# Project documentation


## Configuration

### `.env` File

The `.env` file is used to configure environment variables. Below is an example of its contents:
```
APP_NAME=my-app
PROJECT_HTTP_PORT=8080
ROOT_DIR=./src
MYSQL_PORT=3306
MYSQL_USER=root
MYSQL_ROOT_PASSWORD=securepassword
REDIS_PORT=6379
PHPMYADMIN_PORT=8081
PHPMYADMIN_FILE_UPLOAD=true
PHPMYADMIN_UPLOAD_LIMIT=10M
PHPMYADMIN_MEMORY_LIMIT=128M
PHPMYADMIN_POST_MAX_SIZE=20M
PHPMYADMIN_MAX_EXECUTION_TIME=60
PHPMYADMIN_PMA_ARBITARY=1

```

## Usage

### 1.Clone the Repository:

```
git clone <repository-url>
cd <repository-name>
```

### 2.Build and Start the Services:
```
docker-compose up --build
```

### 3.Access the Application:
- **PHP Application:** http://localhost:8080 (default port)
- **PHPMyAdmin:** http://localhost:8081 (default port)

### 4.Stop the Services:

```docker-compose down```

## Customization
- **Modify Nginx Configuration :**
Edit the `docker/nginx/app.conf` file to update Nginx settings as needed.

- **Modify PHP Configuration :**
Update `docker/php/php.ini` to change PHP settings such as memory limit, execution time, etc.

- ***Add More Services :***
Add additional services to the `docker-compose.yml` file as needed for your project.

## Data Persistence

- **MySQL Data:** Stored in `./docker/.data/mysql` (ensure this directory is backed up for persistent data).
- **Application Code:** Mapped from the host system using the `ROOT_DIR` variable in the `.env` file.

## Troubleshooting

- **Service Logs:** To view logs for a specific service:
```
docker-compose logs <service-name>
```

- **Rebuild Containers:** If you encounter issues, rebuild the containers:
```
docker-compose up --build
```

- **Database Connection Issues:** Ensure the MySQL environment variables (MYSQL_USER, MYSQL_ROOT_PASSWORD) in the .env file are correctly set.

## Contributions
Feel free to fork this repository and contribute by submitting a pull request. Suggestions and issues are welcome!

## License
This project is licensed under the MIT License. See the LICENSE file for details.
