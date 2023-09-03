## README


The instructions are on how to run on LINUX (UBUNTU)
### What is Saleor Platform?

Saleor Platform is the easiest way to start local development with all the major Saleor services:
- [Core GraphQL API](https://github.com/saleor/saleor)
- [Dashboard](https://github.com/saleor/saleor-dashboard)
- Mailpit (Test email interface)
- Jaeger (APM)
- The necessary databases, cache, etc.

## Requirements
1. [Docker](https://docs.docker.com/install/)


## How to install docker

First Setup Docker repository on new machine:
(SKIP TO STEP 7 IF ALREADY DONE)
Run the following commands in superuser mode:

1 - 
```shell
sudo apt-get update
```

2 - 
```shell
sudo apt-get install ca-certificates curl gnupg
```
3 - 
```shell
sudo install -m 0755 -d /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
4 - 
```shell
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```
5 - 
```shell
  echo \
      "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
      "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
      sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
6 - 
```shell
sudo apt-get update
```
7 - 
```shell
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin   
    docker-compose-plugin
```
# to check if docker is setup run:
8 - 
```shell
sudo docker run hello-world ()
```
## How to clone the repository?

To clone the repository, run the following command

```
git clone https://github.com/saleor/saleor-platform.git
```

## How to run it?


2. Go to the cloned directory:
```shell
cd saleor-platform
```

3. Build the application:
```shell
docker compose build
```

4. Apply Django migrations:
```shell
docker compose run --rm api python3 manage.py migrate
```

5. Populate the database with example data and create the admin user:
```shell
docker compose run --rm api python3 manage.py populatedb --createsuperuser
```
*Note that `--createsuperuser` argument creates an admin account for `admin@example.com` with the password set to `admin`.*

6. Run the application:
```shell
docker compose up
```

## Where is the application running?
- Saleor Core (API) - http://localhost:3009
- Saleor Dashboard - http://localhost:9003
- Jaeger UI (APM) - http://localhost:16686
- Mailpit (Test email interface) - http://localhost:8025

