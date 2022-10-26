## centos-php

Bastaría con clonar o repositorio:
```
$ git clone https://github.com/jmarinho73/centos-php.git
```
Ir ao directorio principal:
```
$ cd centos-php
```
Nese directorio crear un ficheiro .env cos valores que se queiran para a base de datos. Por exemplo:
```
MYSQL_USER=web
MYSQL_PASSWORD=abc123.
MYSQL_ROOT_PASSWORD=abc123.
MYSQL_DATABASE=web
```
E finalmente arrancar os containers con:
```
$ sudo docker compose up -d
``` 
