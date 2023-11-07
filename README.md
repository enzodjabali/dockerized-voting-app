# Dockerized voting app
Live version available on [http](https://cats-vs-dogs.xyz/)

### Contributors :
Enzo DJABALI<br>
Baptiste LECLERT<br>
Younes BADDOU<br>

## Deploy project with docker 🐳

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


<i>Thanks and for reading 👋</i>
