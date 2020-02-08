# Docker starter postgresql

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

