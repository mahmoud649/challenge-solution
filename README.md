# Challenge : solved

## Overview

This repository contains the api and frontend app with :

1. **API Dockerfile**: Inside the API directory you can find the Dockerfile for the api "running in apache" serves as the backend for the application and listens on port 8000.
2. **Client Dockerfile**: Inside the client directory you can find the Dockerfile for the frontend of the application and listens on port 3000.
3. **docker-compose.yml**: in the root directory you can find the Docker compose file for running "nginx as the proxy, frontend, backend, and database(MySQL)" and creating the network and the database volume. 

## How to run the application (1)

- **Run the docker-compose.yml**: use "docker compose up -d" command to pull the images from the docker hub and run the application in the background.
- **Access the application**: use the browser at "localhost:443" to access the application.

## How to run the application (2)

- **Run the docker-compose-build.yml**: first rename "docker-compose-build.yml"  to "docker-compose.yml" then use "docker compose up --build -d" command to build the images from the repo and run the application in the background.
- **Access the application**: use the browser at "localhost:443" to access the application.
