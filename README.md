## Site WordPress com Mysql Docker Compose

De forma bem simples e descomplicada de subir um site em docker com wordpress e mysql

 *[WORDPRESS](https://hub.docker.com/_/wordpress/) - Última versão do wordpress
 
  
 *[MYSQL](https://hub.docker.com/_/mysql/)

 
### Pré-requisitos

Criar um arquivo chamado docker-compose.yml e copiar o código abaixo:

```
version: '3'

services:
  # Database
  db:
    image: mysql:5.7
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: password
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
      
   # Wordpress
  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    ports:
      - '8000:80'
    restart: always
    volumes: ['./:/var/www/html']
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
    
volumes:
  db_data:
```


### Deploy

docker compose up 

DEPLOY COM SWARM

docker stack deploy -c docker-compose.yml wordpress_site

```
```

## Testes

http://IP:8080

