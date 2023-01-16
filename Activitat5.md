Explicar els passos seguits durant la instal·lació de Moodle (4 punts).

Instal·lació Moodle (1p).
Inserir les captures de pantalla dels moments delicats de la instal·lació, explicant què es fa a la captura (4 punts).

Instal·lació Moodle (1p).
Documentar els problemes que hem tingut durant la instal·lació (2 punts).
Com hem sapigut quina versió de PHP instal·lar (1p).
Altres (1p).

Insta·lacio de Moodle

El primer sera tindre instal·lat LAMP (Apache, mySQL o mariaDB y PHP) i es fa de la seguent manera:
1. sudo apt-get update
2. sudo apt-get install apache2
Ara tenim que instal·lar una base de dades en el nostre cas instal·larem MariaDB:
1. sudo apt-get install mariadb-server
2. sudo mysql_secure_installation
3. sudo mysql -u root -p
Per ultim queda instal·lar PHP:
1. sudo apt install php libapache2-mod-php php-mysql
2. Editarem el següent directori: /etc/apache2/mods-enabled/dir.conf
![image](https://user-images.githubusercontent.com/107154929/212700217-a37925e4-3203-4c7c-ae76-0495809ebcf1.png)
3. sudo service apache2 restart
4. sudo service apache2 status

Un cop tenim les dependecies indicades anteriorment podem començar amb la instal·lació de Moodle.
1. Ara tenim que escollir quina versio de moodle volem instal·lar.
wget https://download.moodle.org/download.php/direct/stable38/moodle-latest-38.zip
2. sudo unzip moodle-latest-38.zip -d /var/www/html/
3. sudo chown www-data:www-data /var/www/html/moodle
Ara creem un directori de fitxers:
4. cd /home
sudo mkdir moodledata
sudo chown www-data:www-data moodledata/
Per continuar configurem la BDD:
5. mysql -u root -p
6. CREATE USER 'moodlemanager'@'localhost' IDENTIFIED BY 'managermoodle';
7. CREATE DATABASE moodle;
8. GRANT ALL PRIVILEGES ON moodle.* TO 'moodlemanager'@'localhost';
FLUSH PRIVILEGES;
Per finalitzar configurarem Moodle:
1. ipdelamaquina/moodle
![image](https://user-images.githubusercontent.com/107154929/212704709-8e4c6b6b-5c07-48f0-9b84-5d926065074a.png)
