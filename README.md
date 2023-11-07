# Dockerized voting app

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

Nice! You can now access the app at `localhost:8888` 🎉

<br>

## Useful tips 📎

Grant permissions to www-data (might solve cache errors from liip/imagine-bundle):
```bash
sudo chown -R $USER:www-data bde-supinfo-caen/ && sudo chmod -R g+r+x+w bde-supinfo-caen/
```

Load fixtures with faker (in php container):
```sh
bin/console d:f:l
```
<br>

## Access and manage database 🐘

Access PostgreSQL container:
```bash
docker exec -it bde-supinfo-caen_database_1 sh
```

Connect to database:
```sh
psql -U symfony -d app
```

List users:
```sql
SELECT * FROM public.user;
```

Set user verified:
```sql
UPDATE public.user SET verified = true WHERE id = 1;
```

Set user super admin:
```sql
UPDATE public.user SET roles = '["ROLE_SUPER_ADMIN"]' WHERE id = 1;
```
<br />
<i>Thanks and enjoy 👋</i>
