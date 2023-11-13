---
title: "Deploying a Two-Tier Flask App with Docker Compose"
datePublished: Mon Nov 13 2023 07:45:12 GMT+0000 (Coordinated Universal Time)
cuid: clowlnlch001l08kx1v9644cc
slug: deploying-a-two-tier-flask-app-with-docker-compose
canonical: https://arjunmenon.hashnode.dev/day-19-docker-for-devops-engineers-part-3
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1699861894449/1810ab8c-e104-4a1d-bc47-7b61817049e0.png
tags: cloud, linux, docker, aws, devops

---

## Introduction

DevOps practices have revolutionized the software development lifecycle, emphasizing collaboration and automation. In this tutorial, we will explore the deployment of a two-tier Flask app with a MySQL database using Docker. The primary concepts covered in this project are Docker volumes and Docker networks, ensuring data persistence and efficient communication between containers.

## Prerequisites 🛠️

Before diving into the tutorial, make sure you have Docker installed on your machine. You can download Docker from [here](https://www.docker.com/products/docker-desktop).

## Step 1: Clone the Repository 🧑‍💻

Begin by cloning the project repository from GitHub:

```bash
git clone https://github.com/ArjunMnn/two-tier-flask-app.git
cd two-tier-flask-app
```

## Step 2: Build the Flask App Image🖼️

Navigate to the Flask app directory and build the Docker image using the provided Dockerfile:

```bash
docker build -t flask-app .
```

## Step 3: Create Docker Network🌐

Create a Docker network to facilitate communication between the Flask app and MySQL containers:

```bash
docker network create -d bridge two-tier-app-nw
```

## Step 4: Create Docker Volume💾

Create a Docker volume to ensure persistent storage for the MySQL database:

```bash
docker volume create --name two-tier-app-volume --opt type=none --opt device=/home/ubuntu/volumes/two-tier-app --opt o=bind
```

## Step 5: Run MySQL Container🚢

Start the MySQL container with the following command:

```bash
docker run -d -p 3306:3306 -v two-tier-app-volume:/var/lib/mysql/ -e MYSQL_ROOT_PASSWORD=test@123 -e MYSQL_DATABASE=testdb -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin --network=two-tier-app-nw --name mysql mysql:latest
```

## Step 6: Run Flask App Container🏃‍♂️

Run the Flask app container, ensuring it connects to the created network:

```bash
docker run -d -p 5000:5000 -e MYSQL_HOST=mysql -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin -e MYSQL_DB=testdb --network=two-tier-app-nw --name flask-app flask-app:latest
```

## Step 7: Access MySQL Container🛢️

Access the MySQL container to create a table inside the `testdb` database:

```bash
docker exec -it CONTAINER_ID bash
```

Inside the container, run the following MySQL query to create a table:

```bash
CREATE TABLE messages (
    id INT AUTO_INCREMENT PRIMARY KEY,
    message TEXT
);
```

Exit the container.

## Step 8: Add Data to Flask App💬

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699858494619/1e0e44ad-caa0-4fdc-9f54-d3aab7e76fe1.png?auto=compress,format&format=webp align="left")

With the Flask app running, access it through your browser and add some data.

## Step 9: Restart MySQL Container🔄

Stop and remove the MySQL container:

```bash
docker stop mysql
docker rm mysql
```

Then, restart the MySQL container to demonstrate data persistence:

```bash
docker run -d -p 3306:3306 -v two-tier-app-volume:/var/lib/mysql/ -e MYSQL_ROOT_PASSWORD=test@123 -e MYSQL_DATABASE=testdb -e MYSQL_USER=admin -e MYSQL_PASSWORD=admin --network=two-tier-app-nw --name mysql mysql:latest
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699858827164/478472d7-87f5-4dfb-beda-2fe224f86a2e.png?auto=compress,format&format=webp align="left")

# Simplify Deployment with Docker Compose 🚢

So far, we've meticulously followed the step-by-step process for deploying our two-tier Flask app using individual Docker commands. Now, let's take it a step further and streamline the entire deployment process with Docker Compose.

### Docker Compose Configuration

Create a `docker-compose.yml` file in your project directory with the following content:

```bash
version: '3'
services:
  mysql:
    image: mysql:latest
    container_name: mysql
    ports:
      - "3306:3306"
    volumes:
      - two-tier-app-volume:/var/lib/mysql/
    environment:
      MYSQL_ROOT_PASSWORD: test@123
      MYSQL_DATABASE: testdb
      MYSQL_USER: admin
      MYSQL_PASSWORD: admin
    networks:
      - two-tier-app-nw

  flask-app:
    image: flask-app:latest
    container_name: flask-app
    ports:
      - "5000:5000"
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: admin
      MYSQL_PASSWORD: admin
      MYSQL_DB: testdb
    networks:
      - two-tier-app-nw

volumes:
  two-tier-app-volume:
    external: true

networks:
  two-tier-app-nw:
    driver: bridge
```

### Deploy with Docker Compose

With the `docker-compose.yml` file in place, deploying the entire stack becomes a breeze. Run the following command:

```bash
docker-compose up -d
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699860804558/991ecec0-9cab-4875-aaec-8dd6c4554940.png?auto=compress,format&format=webp align="left")

Docker Compose will orchestrate the deployment of both the MySQL and Flask app containers, ensuring seamless communication between them. This single command replaces the manual execution of each Docker command we used earlier.

### Additional Commands

To stop and remove the containers created by Docker Compose, use:

```bash
docker-compose down
```

This concludes our journey in deploying a two-tier Flask app using both individual Docker commands and the efficiency of Docker Compose. Choose the approach that best suits your needs and workflow.

## Conclusion🎉

Congratulations! You have successfully deployed a two-tier Flask app with a MySQL database using Docker. This tutorial covered essential DevOps practices, including Docker volumes and networks, ensuring seamless container orchestration and data persistence. Feel free to explore and extend this project based on your requirements. Happy coding!