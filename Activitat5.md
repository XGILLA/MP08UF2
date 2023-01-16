# Insta·lacio de Moodle

## El primer sera tindre instal·lat LAMP (Apache, mySQL o mariaDB y PHP) i es fa de la seguent manera:
1. ``` sudo apt-get update ```
2. ``` sudo apt-get install apache2 ```

## Ara tenim que instal·lar una base de dades en el nostre cas instal·larem MariaDB:
1. ``` sudo apt-get install mariadb-server ```
2. ``` sudo mysql_secure_installation ```
3. ``` sudo mysql -u root -p ```

Per ultim queda instal·lar PHP:
1. ``` sudo apt install php libapache2-mod-php php-mysql ```
2. Editarem el següent directori: /etc/apache2/mods-enabled/dir.conf
![image](https://user-images.githubusercontent.com/107154929/212700217-a37925e4-3203-4c7c-ae76-0495809ebcf1.png)
3. ``` sudo service apache2 restart ```
4. ``` sudo service apache2 status ```

## Un cop tenim les dependecies indicades anteriorment podem començar amb la instal·lació de Moodle.
1. Ara tenim que escollir quina versio de moodle volem instal·lar.
``` 
wget https://download.moodle.org/download.php/direct/stable38/moodle-latest-38.zip 
```
2. ``` sudo unzip moodle-latest-38.zip -d /var/www/html/ ```
3. ``` sudo chown www-data:www-data /var/www/html/moodle ```
## Ara creem un directori de fitxers:
4. 
``` cd /home ```

``` sudo mkdir moodledata ```

``` sudo chown www-data:www-data moodledata/ ```
## Per continuar configurem la BDD:
5. ``` mysql -u root -p ```
6. ``` CREATE USER 'moodlemanager'@'localhost' IDENTIFIED BY 'managermoodle'; ```
7. ``` CREATE DATABASE moodle; ```
8. ``` GRANT ALL PRIVILEGES ON moodle.* TO 'moodlemanager'@'localhost'; ```
``` FLUSH PRIVILEGES; ```
## Per finalitzar configurarem Moodle:
1. ipdelamaquina/moodle
![image](https://user-images.githubusercontent.com/107154929/212704709-8e4c6b6b-5c07-48f0-9b84-5d926065074a.png)
2. Just després Moodle farà una comprovació de requisits, en el nostre cas es troba que falten dos mòduls de PHP que necessitarà Moodle: curl i zip.
![image](https://user-images.githubusercontent.com/107154929/212704901-9012f5ab-9fb4-4580-9819-b39881ce30aa.png)
3. Com hem instal·lat PHP només hem de buscar en aptitude els paquets indicats, per a curl:
![image](https://user-images.githubusercontent.com/107154929/212705142-2668f557-7704-414b-a0f2-2ba7aa25925e.png)
4. Y per a zip:
![image](https://user-images.githubusercontent.com/107154929/212705243-191e9138-5fbe-4828-8790-888ad7cade5a.png)
5. I després recarregar el servidor web, en el nostre cas en ser Apache:
sudo service apache2 reload
6. Lo siguiente que nos pregunta Moodle es la URL de Moodle, donde está el directorio de Moodle y donde el directorio de datos de usuarios.
![image](https://user-images.githubusercontent.com/107154929/212705526-aa37c46e-353d-4973-9d8e-8fef4c9975e8.png)

## Aqui acaba el tutorial ja que tots els següents pasos es anar seguint les pantalles de elecció.

L'unic problema que ens a sorgit a sigut que com utilitzem maquina virtual teniem que configurar l'arxiu corresponent per posar la IP correcta ja que al navegador no ens mostraba res.
