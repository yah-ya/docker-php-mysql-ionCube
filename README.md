# Docker Configuration for PHP and MySQL with ionCube

This project provides a Docker configuration to set up PHP, MySQL, and ionCube for streamlined development and deployment of Laravel projects, especially those involving ionCube functionality.

## Table of Contents
1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Getting Started](#getting-started)
4. [Project Structure](#project-structure)
5. [Configuration Details](#configuration-details)
6. [Usage](#usage)
7. [Network and Ports](#network-and-ports)
8. [Volumes](#volumes)
9. [Environment Variables](#environment-variables)

## Introduction
This Docker configuration provides a quick and easy setup for running PHP, MySQL, and ionCube. It's particularly useful for Laravel projects that may require ionCube functionality.
No need to install MAMP or WAMP or manual php/mysql on your machine. Just install Docker and Docker Compose and you're good to go.

## Prerequisites
- [Docker](https://docs.docker.com/get-docker/) and [Docker Compose](https://docs.docker.com/compose/install/) installed on your machine.

## Getting Started
1. Clone this repository.
2. Navigate to the root directory of the cloned repository.

## Project Structure
- `docker-config/`: Contains Docker configuration files.
  - `php/`: Dockerfile for PHP with ionCube.
- `html/`: Place your project files here.

## Configuration Details
### PHP Service
- **Image:** PHP with ionCube.
- **Container Name:** app.
- **Volumes:**
  - `./html:/var/www/html`: Mounts your project files into the container.
- **Ports:**
  - Host: 8080, Container: 80.
- **Environment Variables:**
  - `APACHE_DOCUMENT_ROOT=/var/www/html`

### MySQL Service
- **Image:** MySQL latest version.
- **Container Name:** mysql-db.
- **Ports:**
  - Host: 3316, Container: 3306 (default MySQL port).
- **Environment Variables:**
  - `MYSQL_ROOT_PASSWORD=root_password`
  - `MYSQL_DATABASE=db`
  - `MYSQL_USER=admin`
  - `MYSQL_PASSWORD=secret`

## Usage
1. Ensure that you have [Docker](https://docs.docker.com/get-docker/) installed on your machine.
2. Build the Docker Compose configuration by running the following command in the project root directory:
   ```bash
   docker-compose build
(Note: This step may take some time, as it builds the Docker images based on the configuration.)
3. Start the services by running:
   ```bash
   docker-compose up -d
4. You can now access your Laravel project at http://localhost:8080.
5. To stop the services, run:
   ```bash
   docker-compose down
## Network and Ports
- Network: network.
- PHP Service Port: 8080 (Host) mapped to 80 (Container).
- MySQL Service Port: 3316 (Host) mapped to 3306 (Container).

## Volumes
- mysql-data: Volume for persisting MySQL data.
## Environment Variables
### PHP Service
- APACHE_DOCUMENT_ROOT: Sets the document root for Apache.
### MySQL Service
- MYSQL_ROOT_PASSWORD: Sets the root password for MySQL.
- MYSQL_DATABASE: Sets the database name for MySQL.
- MYSQL_USER: Sets the username for MySQL.
- MYSQL_PASSWORD: Sets the password for the MySQL user.
