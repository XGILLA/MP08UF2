# Instal·lar Owncloud a Ubuntu 22.04 LTS
29 Set. 2022

## Requisits previs
Abans de poder instal·lar Owncloud al nostre equip amb Ubuntu hem de tenir instal·lat LAMP, per això pots consultar el tutorial per instal·lar LAMP a Linux.

## Instal·lar Apache:
Instal·lem el servidor Apache:

```
sudo apt install apache2
```
![1cap](1.png)

Desactivem el llistat de directoris del servidor:

```
sudo sed -i "s/Options Indexes FollowSymLinks/Options FollowSymLinks/" /etc/apache2/apache2.conf
```
![2cap](2.png)
sudo mysql -u root -p
## Instal·lar MariaDB:
Instal·lem MariaDB:

```
sudo apt-get install mariadb-server mariadb-client -y
```
![3cap](3.png)

I configurem la instal·lació:

```
sudo mysql_secure_installation
```
![4cap](4.png)

Per ultim reiniciem el servidor MariaDB

```
sudo systemctl restart mariadb.service` o `sudo service mariadb.service restart
```
![5cap](5.png)

## Creació Base de Dades Ownclowd:

Entrem a MariaDB:

```
sudo mysql -u root -p
```
![6cap](6.png)

Creem la base de dades:

```
CREATE DATABASE owncloud;
```
![7cap](7.png)

Creem un usuari anomenat ownclouduser amb una contrasenya que podria ser Admin1234:

```
CREATE USER 'ownclouduser'@'localhost' IDENTIFIED BY 'Admin1234';
```
![8cap](8.png)

Donem accés a l'usuari a la base de dades creada:

```
GRANT ALL ON owncloud.* TO 'ownclouduser'@'localhost' IDENTIFIED BY 'Admin1234' WITH GRANT OPTION;
```
![9cap](9.png)

Apliquem cambis i guardem:

```
FLUSH PRIVILEGES;
EXIT;
```
![10cap](10.png)
