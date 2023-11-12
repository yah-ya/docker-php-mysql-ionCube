# Docker Configuration for PHP, MySQL, and ionCube

This project provides a simple Docker configuration to set up the latest versions of PHP and MySQL, including the ionCube plugin for PHP. This configuration is designed to streamline the development and deployment of projects, particularly those involving ionCube, which is widely used in WordPress projects. These files are versatile and can be employed for working with WordPress projects as well.

### Table of Contents
1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Getting Started](#getting-started)
4. [Project Structure](#project-structure)
5. [Configuration Details](#configuration-details)
6. [Usage](#usage)
7. [Network and Ports](#network-and-ports)
8. [Volumes](#volumes)
9. [Environment Variables](#environment-variables)

### Introduction
This Docker configuration provides a quick and easy setup for running PHP, MySQL, and ionCube. It's particularly useful for projects, such as WordPress, that rely on ionCube functionality.

### Prerequisites
- Docker and Docker Compose installed on your machine.

### Getting Started
1. Clone this repository.
2. Navigate to the root directory of the cloned repository.

### Project Structure
- `docker-config/`: Contains Docker configuration files.
    - `php/`: Dockerfile for PHP with ionCube.
- `project/`: Place your PHP project files here.

### Configuration Details
#### PHP Service
- **Image:** PHP with ionCube.
- **Container Name:** laravel-app.
- **Volumes:**
    - `./project:/var/www/html`: Mounts your project files into the container.
- **Ports:**
    - Host: 8080, Container: 80.
- **Environment Variables:**
    - `APACHE_DOCUMENT_ROOT=/var/www/html/public`.

#### MySQL Service
- **Image:** MySQL latest version.
- **Container Name:** mysql-db.
- **Volumes:**
    - `laravel-mysql-data:/var/lib/mysql`: Persists MySQL data.
    - `./docker-config/mysql.cnf:/etc/mysql/my.cnf`: Custom MySQL configuration file.
- **Environment Variables:**
    - `MYSQL_ROOT_PASSWORD=root_password`
    - `MYSQL_DATABASE=laravel_db`
    - `MYSQL_USER=laravel_user`
    - `MYSQL_PASSWORD=laravel_password`

### Usage
1. Run `docker-compose up -d` to start the services.
2. Access your PHP project at `http://localhost:8080`.

### Network and Ports
- **Network:** laravel-net.
- **PHP Service Port:** 8080 (Host) mapped to 80 (Container).

### Volumes
- `laravel-mysql-data`: Volume for persisting MySQL data.

### Environment Variables
- PHP Service:
    - `APACHE_DOCUMENT_ROOT`: Specifies the document root for Apache.

- MySQL Service:
    - `MYSQL_ROOT_PASSWORD`: Root password for MySQL.
    - `MYSQL_DATABASE`: MySQL database name.
    - `MYSQL_USER`: MySQL user.
    - `MYSQL_PASSWORD`: Password for the MySQL user.

---