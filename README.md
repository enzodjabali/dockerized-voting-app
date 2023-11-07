# Dockerized voting app

## Symfony BDE SUPINFO CAEN

### Contributors :
Enzo DJABALI
Baptiste LECLERT
Younes BADDOU

## Deploy project with docker 🐳

Install docker and docker-compose:
```bash
sudo apt install docker -y && sudo apt install docker -y
```

Add user to docker group (if not already added):
```bash
sudo usermod -aG docker $USER
```

Grant docker sock permission:
```bash
sudo chmod 666 /var/run/docker.sock
```

Create a symbolic link to /usr/bin:
```
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

Restart docker service:
```bash
sudo service docker restart
```

Clone the project:
```bash
git clone https://github.com/enzodjabali/bde-supinfo-caen
```

Create and start containers:
```bash
cd bde-supinfo-caen/ && docker-compose up
```
<br />

<b>Create a copy of the `.env` file then name it `.env.local` and fill it out</b>
Database connection:
```env
DATABASE_URL="postgresql://symfony:PASSWORD@database:5432/app?serverVersion=13&charset=utf8"
```

<br />

Connect to php container:
```bash
docker exec -it php sh
```

Install dependencies with composer:
```sh
composer install
```

Update var/ directory:
```sh
chmod -R 777 var/
```

Create database:
```sh
bin/console d:d:c
```

Migrate database:
```sh
bin/console d:m:m
```

Congrats! You can now access your app server at `localhost:8080` 🎉

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
