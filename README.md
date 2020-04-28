# PostgreSQL Docker starter

## Install docker in Ubuntu 19.04 (see how to install in your distro)
```
user@computer:~$ sudo snap install docker
```

## Check if docker was installed correctly
```
user@computer:~$ docker --version
Docker version 18.09.9, build 1752eb3
```

## if docker group does not exist, create it
```
user@computer:~$ sudo groupadd docker
```

## Add your user to the docker group
```
user@computer:~$ sudo usermod -aG docker $USER
```
*The user need to execute log in to see their new group added*

## Create the postgresql container
```
user@computer:~$ docker run --name database-name -e POSTGRES_PASSWORD=my-secret-password -p 5432:5432 -d postgres
```

## Check if postgresql was running
```
user@computer:~$ docker ps
```

## Check all containers 
```
user@computer:~$ docker ps -a
```

## Start the postgresql container
```
user@computer:~$ docker start <postgresql_container_id>
```

## Execute psql command
```
user@computer:~$ docker exec -it <postgresql_container_id> psql -U postgres
```

## Create database (after execute psql command)
```
postgres=# CREATE DATABASE database_name;
CREATE DATABASE
postgres=# \connect database_name;
You are connected to database "database_name" as user "postgres".
database_name=#\q
```
*\l list of databases*
*\dl list of relations*
*\q quit*

## Show statistics of postgresql container
```
user@computer:~$ docker stats <postgresql_container_id>
```

## Restart a postgresql container
```
user@computer:~$ docker restart <postgresql_container_id>
```

## Remove a postgresql container
```
user@computer:~$ docker rm <postgresql_container_id>
```

## Enable extension unaccent 
```
user@computer:~$ docker start postgres-container
user@computer:~$ docker exec -it postgres-container bash
user@computer:~$ su - postgres
psql
\connect database_name
You are now connected to database "database_name" as user "postgres".
database_name=# create extension unaccent;
CREATE EXTENSION
database_name=# \dx
                         List of installed extensions
   Name   | Version |   Schema   |                 Description                 
----------+---------+------------+---------------------------------------------
 plpgsql  | 1.0     | pg_catalog | PL/pgSQL procedural language
 unaccent | 1.1     | public     | text search dictionary that removes accents
database_name=# \q
```

