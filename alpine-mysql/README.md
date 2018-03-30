# alpine-mysql
a docker image base on alpine with mysql

# build image
```
docker build -t ehlxr/alpine-mysql .
```

# build image (docker-compose)

```
docker-compose build
```

# Usage
```
docker run -it --name mysql -p 3306:3306 -v $(pwd)/db-data:/data -e MYSQL_DATABASE=admin -e MYSQL_USER=ehlxr -e MYSQL_PASSWORD=prY6KaQC -e MYSQL_ROOT_PASSWORD=eDWyvjS2 ehlxr/alpine-mysql
```

> It will create a new db(default is `admin`) whith user `ehlxr` set password is `prY6KaQC`, and set mysql root password(default is `#Q*2.&tY`)

# Usage (docker-compose)
```
docker-compose up -d
```

> It will create a new db(default is `admin`) whith user `ehlxr` set password is `prY6KaQC`, and set mysql root password(default is `eDWyvjS2`)
