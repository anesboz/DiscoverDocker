## TP 2 - Github Action session

### What are testcontainers?

Conteneurs Docker pour les tests, offrant une isolation et une gestion automatique des dépendances

### Secured Variables, why?

pour protéger les variables sensibles, gérer les secrets de manière centralisée, tout en contrôlant l'accès.

## For what purpose do we need to push docker images?

pour les déployer et les partager. Ainsi que pour gérer les versions.

---

## Commandes utilisées

## Lancer one shot

docker-compose up --build

## Publish x

docker tag tp1-httpd anesboz/tp1-httpd:1.0
docker push anesboz/tp1-httpd:1.0

## Lacer en wrac

#### db

docker build -t db-image .

<!-- docker run -d --name mydb-container -p 5432:5432 -v pg_data:/var/lib/postgresql/data --network=app-network db-image -->

docker run -d --name mydb-container -v pg_data:/var/lib/postgresql/data --network=app-network db-image

###### adminer

docker run -d --name adminer -p 8080:8080 --link mydb-container:mydb adminer

#### api

#### basic_api

docker build -t basic_api-image .
docker run -d --name basic_api-container -p 80:80 basic_api-image

#### simple_api

docker build -t simple_api-image .
docker run -d --name simple_api-container -p 80:8080 simple_api-image

#### simple_api_student

docker build -t simple_api_student-image .
docker run -d --name simple_api_student-container -p 80:8080 --network=app-network simple_api_student-image
