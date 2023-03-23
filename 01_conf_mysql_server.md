# Proceso de configuracion manual de MySQL 8

Conectar al gestor de la base de datos

* `sudo mysql`

```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 65
Server version: 8.0.32 MySQL Community Server - GPL

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 

```
Cambiar el password para el usuario root en la terminal/cosola de MySQL

```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by 'mypasss11122332';
quit

```

Configurar la opciones de seguridad basicas del gestor de base de datos MySQL 8

* `sudo mysql_secure_installation`

Configurar repo mysql-apt-config_0.8.12

* `cd /usr/src/asterisk-certified-16.8-cert14/`
* `sudo wget https://dev.mysql.com/get/mysql-apt-config_0.8.12-1_all.deb`
* `sudo dpkg -i mysql-apt-config_0.8.12-1_all.deb`
* `sudo apt-get update`
* `sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 467B942D3A79BD29`
* `sudo apt install -f mysql-client=8.0* mysql-community-server=8.0* mysql-server=8.0*`
* `sudo apt-get install unixodbc`




