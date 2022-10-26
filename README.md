## centos-php

Bastaría con clonar o repositorio:
```
git clone https://github.com/jmarinho73/centos-php.git
```
Ir ao directorio principal:
```
cd centos-php
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
sudo docker compose up -d
``` 
----
#### Soporte para MySQL 8.0 

Se se quere usar a versión 8.0 de MySQL no canto da 5.7 engadimos un ficheiro docker-compose para iso.
Para probalo bastaría con:
```
  sudo docker compose -f docker-compose-mysql8.yaml up -d
```
----
Os datos da base de datos e o directorio raíz do servidor web están en volumes compartidos co anfitrión. Isto facilita o desenvolvemento de páxinas web que poden ser editadas e visualizadas ao momento de xeito sinxelo.
