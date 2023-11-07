# Dockerized voting app
Live version available on [https://cats-vs-dogs.xyz](https://cats-vs-dogs.xyz/)

### Contributors :
Enzo DJABALI<br>
Baptiste LECLERT<br>
Younes BADDOU<br>

## Deploy locally the project with docker 🐳

Install docker:
```bash
sudo apt install docker -y
```

Add user to docker group (if not already added):
```bash
sudo usermod -aG docker $USER
```

Create a .env file (it stores the sensible information such as passwords):
```bash
cp .env.exemple .env
```

Build and start the containers:
```bash
docker compose up --build -d
```

<br>

Nice! You can now access the app on `http://localhost:8888` 🎉

Shut down the app:
```bash
docker compose down
```

<br>

## Explanation of the stack 📎

<img src="https://cdn.discordapp.com/attachments/894581763567931412/1171516625527263314/IMG_1846.jpg" height="500" />

## Docker Compose Configuration
Now, let's dive into the Docker Compose configuration used to run the voting app.
### Docker Compose File

The docker-compose.yml file defines the services and configurations for our application. It uses Docker Compose to manage the multi-container application. Here's a breakdown of the services:

##### Service "postgres": 
This is a PostgreSQL database service used to store votes.
##### Service "redis": 
Redis is used to transmit votes between components.
##### Service "vote": 
This is a Python web application that allows users to vote for one of two options. It depends on the Redis service for vote data.
##### Service "worker": 
A .NET service that consumes votes from Redis and stores them in the PostgreSQL database. It depends on both PostgreSQL and Redis services.
##### Service "result": 
A Node.js web application that displays real-time vote results. It depends on the PostgreSQL service to access vote data.
##### Service "nginx":
Nginx is a web server that exposes the app on port 80. It depends on the "vote" and "result" services to serve the application.
### Volumes
The Docker Compose file also defines volumes for data persistence:
##### "postgres-data":
A volume for the PostgreSQL database to store data.
##### "redis": 
A volume for the Redis service to store data.
These volumes ensure that data is retained even if the containers are stopped or removed.

By using this Docker Compose configuration, you can easily deploy and manage the entire multi-container application in a simplified manner.

<i>Thanks for reading 👋</i>