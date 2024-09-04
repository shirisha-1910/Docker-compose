# MERN Stack Application

A simple MERN (MongoDB, Express.js, React, Node.js) stack application with Docker support.Setting up and running the application using Docker.
## Prerequisites

- Docker and Docker Compose installed on our machine.
- Basic understanding of Docker and Docker Compose.

# Setup Instructions
## Manual Docker Setup
## 1. Create a Docker Network
To allow Docker containers to communicate, first we have to create a Docker network:
       docker network create mern
## 2. Build and Run the Client

The client is a React application. Perform the following steps:
 
1. Build the Client Image:

Navigate to the mern/frontend directory and build the Docker image:

           cd mern/frontend
           docker build -t mern-frontend .
2. Run the Client Container:

Run the container with the following command:

       docker run --name=frontend --network=mern -d -p 5173:5173 mern-frontend
       
3. Verify the Client is Running:

Open the browser and navigate to http://localhost:5173 to see the running client.

## 3. Run the MongoDB Container

To run MongoDB:

docker run --network=mern --name mongodb -d -p 27017:27017 -v ~/opt/data:/data/db mongo:latest

Explanation:

-   --network=mern connects MongoDB to the mern network.
-  -p 27017:27017 maps port 27017 on the host to port 27017 in the container.
-   -v ~/opt/data:/data/db mounts a local directory for MongoDB data persistence.
## 4. Build and Run the Server

The server is an Express.js application. Follow these steps:

1. Build the Server Image:
   
Navigate to the mern/backend directory and build the Docker image:
 
    cd mern/backend
    
    docker build -t mern-backend .
    
2. Run the Server Container:
   
Start the server container with the following command:
    
      docker run --name=backend --network=mern -d -p 5050:5050 mern-backend
   
## By Using Docker Compose file 

To simplify container management, use Docker Compose.

1. Start All Containers

Make sure that we have a docker-compose.yml file in our project root if not we should write the compose file, then use Docker Compose to start all services:

     docker compose up -d
     
2. Stop All Containers

To stop and remove all containers:

   docker compose down

[docker-compose.yaml](./docker-compose.yaml)

 

      
