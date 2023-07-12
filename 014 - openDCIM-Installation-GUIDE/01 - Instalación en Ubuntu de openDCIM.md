# openDCIM-Installation-Guide-Ubuntu
Sistema free basado en web para gestión de Infraestructuras de Data Centers.

Website: https://opendcim.org

# openDCIM-Installation-Guide-Ubuntu_22.04
openDCIM Installation Guide Ubuntu 22.04 Desktop

### 0.666 CONCLUSIONES FINALES

### 0. REQUISITOS INICIALES
Partimos de un Ubuntu Desktop 22.04 instalado como máquina virtual en un VMWare con 2cores, 4 GB de RAM y 20GB de disco duro, red tipo NAT con acceso a internet

El sistema lo tenemos actualizado con los comandos:

```shell
sudo apt-get update
```
<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/ac970b87-12b3-4951-82c5-2f0bb30a03df)</kbd>

```shell
sudo apt-get upgrade
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/225445d6-cc1c-4164-9e5d-c31fff1a2349)</kbd>

### 1. INSTALACIÓN DE APACHE

```shell
sudo apt-get install apache2
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/15f8dcdc-7cc2-4d2b-875b-054394a92173)</kbd>

:scissors: [imagen recortada]

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/5675ae76-529d-4f7b-ac41-0d372ea3ff5c)</kbd>

Una vez instalado, habilitamos que se inicie automáticamente el servicio en cada booteo del sistema, con el comando:

```shell
sudo systemctl enable apache2
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/04adc594-d450-4ab6-bf36-425378015de1)</kbd>

Podemos comprobar su estado con:

```shell
sudo systemctl status apache2
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/56634986-33ff-466f-bbc1-dfd3482ac6b9)</kbd>

En un navegador, accedemos a la URL http://localhost o http://127.0.0.1 o http://<nombre de nuestro máquina virtual> y comprobamos si funciona:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/fc8e915a-c765-4ba5-9011-899f11c81bb3)</kbd>

### 2. INSTALACIÓN DE PAQUETES ADICIONALES NECESARIOS

Los paquetes necesarios son:
+ php
+ php-snmp
+ snmp-mibs-downloader
+ php-curl
+ php-gettext
+ graphviz

Que podemos instalarlos todos al mismo tiempo con el ocmando siguiente:

```shell
sudo apt-get install php php-snmp snmp-mibs-downloader php-curl php-gettext graphviz
```

O de uno en uno :

```shell
sudo apt-get install php
```
<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/4a3935fe-7bf3-4ef6-9a14-2c7fb636f2c6)</kbd>

:scissors: [imagen recortada]

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/353d9e05-910e-4aaa-9114-44c3d617e989)</kbd>

```shell
sudo apt-get install php-snmp 
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/d494ea0d-1395-462a-a8d7-3a531dcc25c8)</kbd>

:scissors: [imagen recortada]

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/4a13f985-d14c-4211-b595-b354726f1d4d)</kbd>

```shell
sudo apt-get install snmp-mibs-downloader 
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/f44b101b-4813-4cb9-90f7-fd1fffee3c18)</kbd>

:scissors: [imagen recortada]

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/109910d3-e184-4be5-b12e-7e9c876f51a1)</kbd>


```shell
sudo apt-get install php-curl 
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/e694bb12-ffad-4be4-bd67-63fe00ed8832)</kbd>

Según la documentación oficial, el siguiente paquete adicional a instalar sería php-gettext, pero este nos ha dado un error al instalarlo, diciéndonos "Unable to locate package php-gettext", por lo que buscando en ointernet creemos que hace referencia a "gettext" directamente, por lo que procedemos a instalarlo usando ese segundo nombre:

```shell
sudo apt-get install gettext
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/4739e1b0-be1f-420c-b4d3-f3214cae23ea)</kbd>

```shell
sudo apt-get install graphviz
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/43d30a4e-846f-4293-86c8-913baa1b5cea)</kbd>

:scissors: [imagen recortada]

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/7f4e9b33-129a-48a1-a4f9-9fb1206d133e)</kbd>

### 3. DESCARGA Y DESCOMPRESIÓN DE openDCIM

Nos creamos una carpeta personal donde realizar la descarga, por ejemplo en /home/usuario que se llame openDCIM y dentro de ella nos descargamos el openDCIM. En el momento de hacer este tutorial la última versión es la 23.01, pero podemos revisar cual es la última accediendo a https://opendcim.org/downloads.html y viendo cual es la direción de la relesae que interese:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/a87aab7b-a288-4cdc-9055-4186a478f5f8)</kbd>

Y ese enlace será el que nos descargaremos haciendo uso del comando wget:

```shell
wget https://opendcim.org/packages/openDCIM-23.01.tar.gz
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/6ac332aa-43cf-49dc-b80b-4b3cdab317b7)</kbd>

Descomprimimos el fichero descargado con el comando

```shell
sudo tar zxpvf openDCIM-23.01.tar.gz 
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/07367666-457f-40a4-b5f9-9d2944d60e78)</kbd>

:scissors: [imagen recortada]

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/36661f74-b1ba-4c9d-bf99-ba0e34f9485e)</kbd>

y veremos que nos ha creado una carpera con todo el contenido del fichero comprimido:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/32bc6521-f33d-45f3-9bad-8897cc6b72c1)</kbd>

Como estamos usando Apache2, los ficheros de nuestro servidor web han de estar en /var/www/html, por lo que vamos a copiar todo el contenido de esta carpeta nueva descomprimida en la ruta /var/www/html con el siguiente comando:

```shell
cd /home/usuario/openDCIM-23.01
```

```shell
sudo cp -r *.* /var/www/html
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/35c6f085-7247-451a-beb2-e417c0ce8472)</kbd>

### 4. DAR PERMISOS A APACHE PARA ESCRITURA EN CIERTOS DIRECTORIOS

Según la propia documentación oficial:

'There are times when Apache will need to be able to write to two of the directories - specifically the /drawings (maps of your data centers) and /pictures (pictures of your devices) folders. To do this, we need to set the group for those folders to the group that Apache is running as. On a default Ubuntu 15.04 server, that group is called www-data.'

Pero al lanzar el comando citado, da error, pues los dos folders en concreto no existen ('pictures' ni 'drawings'). Hay una carpeta que pudiera ser similar llamada 'images'. De momento no hacemos nada, pero dejamos aquí pauntado el comando pr si en un futuro la ejecución de la plaicación nos arroja algún error, tal vez sea esta configuración que hemos de ejecutar:

```shell
sudo chgrp -R www-data /var/www/html/pictures /var/www/html/drawings
```

### 5.INSTALACIÓN DE MYSQL

```shell
sudo apt-get install mariadb-server
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/256fb5e5-95b1-4a2b-8f68-559c588a3a52)</kbd>

:scissors: [imagen recortada]

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/90648983-3360-4721-bee7-26b243e78e42)</kbd>

Si ya existe una instalación previa de MySQL o MariaDB en el sistema, nos avisará diciendo que va a guardar una copia de la carpeta con otro nombre para pder rescatar los datos si nos hace falta:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/85b8f351-1a6a-4a10-86a1-d775abe2b7d6)</kbd>

Hacemos que el servicio MariaDB arranque automáticamente en cada booteo del sistema con el comando:

```shell
systemctl enable mysql
```

EL servicio, aunque sea mariaDB-server, no se inicia con ese nombre, se hace con 'mysql':

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/2b48bbb1-51ec-467e-a12c-74ed2c378480)</kbd>

Podemos comprobar si está corriendo corectamente con el comando:

```shell
systemctl status mysql
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/ba4172a7-09e4-47a0-b0ae-4c7384e7d7e6)</kbd>

#### 5.1 Securizando MySQL

Vamos a realizar una serie de acciones para securizar el acceso al SQL. Ejecutaremos el siguiente comando:

```shell
sudo mysql_secure_installation
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/48e77d96-0b53-4387-a91e-0ff77e05cc1e)</kbd>

Y en la pregunta "Enter current password for root (enter for none):", no introduciremos ninguna contraseña, simplemente le daremos a ENTER:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/f351131c-96e1-4724-911b-893ca497d64a)</kbd>

Lo siguiente que nos pregunta es si queremos cambiar a "autenticación unix_socket", advirtiéndonos de que ya tenemos nuestra cuenta root protegida, mediante la pregunta "You already have your root account protected, so you can safely answer 'n'."
"Switch to unix_socket authentication [Y/n] " , a lo que responderemos "n"

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/10a160d6-3f7f-4256-95ae-b24a45741aaf)</kbd>

Después, nos pregunta si queremos cambiar la contraseña del usuario root, mediante la pregunta "You already have your root account protected, so you can safely answer 'n'.
Change the root password? [Y/n]", a lo que responderemos "n"

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/4fa2a9eb-f17c-4fbe-ae85-d27234414344)</kbd>

La siguiente pregunta es si queremos eliminar los usuarios anónimos que existen por defecto en MariaDB, mediante la pregunta "By default, a MariaDB installation has an anonymous user, allowing anyone
to log into MariaDB without having to have a user account created for them.  This is intended only for testing, and to make the installation go a bit smoother.  You should remove them before moving into a production environment.
Remove anonymous users? [Y/n]", a lo que responderemos "Yes" -> 'Y'

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/ed8c7ef9-0bcd-4f66-98ae-25e63755927e)</kbd>

La siguiente pregunta que nos hace es si queremos eliminar el acceso remoto del usuario root a la Base de Datos, mediante la pregunta "Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.
Disallow root login remotely? [Y/n] ", a lo que responderemos "Yes" -> "Y", ya que normalmente el usuario root siempre se conectará desde el propio equipo localhost, no desde una ubicación remota, por lo que de esta forma eliminamos esta posibilidad securizando nuestro servidor.

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/7214e0a8-0941-4428-9f58-2b97892bbe93)</kbd>

La siguiente consulta es si queremos eliminar la base de datos de pruebas llamada "test" que MariaDB trae por creada por defecto y que todos los usuarios tienen acceso, interesante para aprender y practicar en un entorno de desarrollo pero no recomendable en un entorno de producción, mediante la pregunta "By default, MariaDB comes with a database named 'test' that anyone can access.  This is also intended only for testing, and should be removed before moving into a production environment.
Remove test database and access to it? [Y/n]", a lo que responderemos "Yes" -> "Y"

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/def6e5fd-573a-4be5-ac4d-fac4ab58724e)</kbd>

Y ya, la última pregunta que nos hace, es si queremos aplicar todas las nuevas reglas a las tablas existentes y la nueva seguridad configurada, mediante la pregunta "Reloading the privilege tables will ensure that all changes made so far will take effect immediately.
Reload privilege tables now? [Y/n] ", a lo que responderemos "Yes" -> "Y"

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/0cb65ea2-76d8-4b78-aa35-2be49d764b8e)</kbd>

Finalmente, el último mensaje que nos sale es para indicarnos que todo está hecho y "Thanks for using MariaDB!"

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/524ee533-e97e-41cd-a78a-c7fa0084bb4a)</kbd>

### 6. CREACIÓN DE LA BASE DE DATOS

Llegados a este punto, crearemos la BBDD en MariaDB y asignaremos permisos a un usuario para poder trabajar con dicha BBDD. Para ello, accedemos al terminal de MariaDB con el siguiente comando:

```shell
sudo  mysql -u root -p
```

Con este comando le decimos que queremos iniciar el terminal de MariaDB con el usuario root (identificado con el parámetro -u) y con -p le decimos que nos pida el password del mismo 

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/7e85a095-080b-47a5-8e65-3f7fdc33c345)</kbd>

Ahora, dentro del terminal, creamos la nueva base de datos que se llamará ¡dcim' con el siguiente comando:

```shell
create database dcim;
```

y asignaremos todos los permisos a todas las tablas dentro de la basea de datos 'dcim' (dcim.*) al usuario 'dcim@localhost' y le asignaremos la contraseña 'passdcim', mediante el siguiente comando:

```shell
grant all privileges on dcim.* to'dcim@localhost' identified by 'passdcim';
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/e0568276-03c6-4059-bc9d-e1874dc16d7a)</kbd>

Finalmente saldremos con quit

```shell
quit
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/71e7ec5b-67b0-437f-b26f-e946a9b7017b)</kbd>

#### 6.1 Otros comandos

Podemos hacer varias comprobaciones de funcionamiento de MariaDB. Para ello, accedemos nuevamente al terminal de MySQL con el comando:

```shell
sudo mysql -u root -p
```

Y podemos ver la versión que tenemos corriendo con el comando siguiente:

```shell
SELECT VERSION();
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/d3516bda-8821-4220-b359-6d8bba52edc7)</kbd>


Podemos ver todas las bases de datos creadas con el comando:

```shell
show databases;
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/6cbcebbe-88f6-435c-b867-af1cc2ca4a25)</kbd>

O los usuarios asignados a las bases de datos:

```shell
SELECT u.User,Db FROM mysql.user u,mysql.db d WHERE u.User=d.User;
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/bbc0bc3c-d617-4185-b481-3ca8a976d2d0)</kbd>

### 7. CONFIGURACIÓN DE OPENDCIM PARA TENER ACCESO A LA BASE DE DATOS

Nuestros ficheros del servidor web están en /var/www/html, por lo que accedemos a esa carpeta y hacemos una copia del fichero db.inc.php-dist en otro nuevo llamado db.inc.php :

```shell
cd /var/www/html
```

```shell
sudo cp db.inc.php-dist db.inc.php
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/e4a05254-6b21-4cc8-91c9-f10c89413b1e)</kbd>

Luego lo editamos con nano y modificamos con los datos necesarios. En nuestro caso, el usuario de la base de datos, el password, el nombre de la base de datos si la hemos cambiado, etc.

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/1cdeddc6-b915-46c5-ac8b-0be3dede9d27)</kbd>

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/24921669-2f8c-41ef-8f60-dbbf82f8a11a)</kbd>

### 8. CONFIGURACIÓN DE APACHE 

El fichero de configuración de apache está en /etc/apache2/sites-available/000-default.conf y /etc/apache2/sites-available/default-ssl.conf

Vamos a editarlo para hacerle las modificaciones necesarias:

```shell
cd /etc/apache2/sites-available
```

```shell
sudo nano default-ssl.conf
```

Lo editamos con nano. Estos son dos pantallazos del antes y del después:

ANTES:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/433f88bb-47e7-491b-b7c3-1807ee1a9ec0)</kbd>

DESPUES:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/c0f14473-f20e-4e29-a967-bfb38dc388d4)</kbd>

### 9. CONFIGURAR EL ACCESO DEL USUARIO A NUESTRO WEBSITE

Vamos a posicionarnos en la carpeta /var/www/html y vamos a editar con nao un nuevo fichero llamado .htaccess

```shell
cd /
```

```shell
cd /var/www/html
```

```shell
sudo nano .htaccess
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/3bf11c8d-328f-4206-9d80-1a5b1b05fb5c)<kbd>

Y agregaremos estas 4 líneas:

```shell
AuthType Basic
AuthName "openDCIM"
AuthUserFile /var/www/opendcim.password
Require valid-user
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/853b3265-95b1-440b-bcbc-b470116f4bb4)<kbd>

Ahora asignamos permisos especiales al fichero /var/www/opendcim.password que es el que hemos indicado dentro de /var/www/html/.htaccess 

```shell
sudo htpasswd -cb /var/www/opendcim.password dcim dcim
```

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/f41b3b48-82dd-4560-877f-5a3fe3f911e7)

```shell
sudo a2enmod ssl
```

```shell
systemctl restart apache2
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/5fff4637-e0c3-4623-9cfb-f017d790a71c)</kbd>

```shell
sudo a2enmod rewrite
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/c587d2c5-4773-4dff-a8f2-a5780cf1675e)</kbd>

```shell
sudo a2ensite default-ssl
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/134c761b-089f-4e65-9fe1-4c5d062f0e6a)</kbd>


```shell
sudo systemctl restart apache2
```

```shell
sudo systemctl status apache2
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/1fe88533-1c2e-4150-9730-8801292baa19)</kbd>

### 10. PRUEBA DE FUNCIONAMIENTO DE NUESTRO WEBSITE

Accedemos a un navegador y visitamos https://localhost (recuerda el https)

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/96aef565-5dc3-4ab0-ae7c-81fd1adf6afb)</kbd>

Introduciomos las credenciales que habíamos configurado anteriormente: 

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/c1748b68-cb27-418b-9ca8-1bed104844fc)</kbd>

Ya parece que funciona, aunque nos arroja una serie de errores que solventaremos fácilmente:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/be3a117c-f97f-47ca-9442-28ff8baed0dc)</kbd>

```shell
sudo apt-get install php8.1-mbstring
```

```shell
sudo systemctl restart apache2
```

```shell
sudo apt-get install php8.1-gd
```

```shell
sudo systemctl restart apache2
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/2ef5e3fc-8aeb-4c0e-b1bd-94fc36f7d1dd)<kbd>

```shell
sudo apt-get install php8.1-zip
```

```shell
sudo systemctl restart apache2
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/93c099b3-ecc8-4fb2-ab7b-e58e0db4da35)</kbd>

```shell
sudo apt-get install php-mysql
```

```shell
sudo systemctl restart apache2
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/de655734-19fb-4c70-9f3d-32f87d542192)</kbd>

A partir de este momento, vamos a fijarnos sólamente en este último error, ya que si solucionamos alguno de los otros 2 veremos que ya nunca más podremos volver a esta pantalla de configuración previa de requisitos:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/7908048a-2a33-49f4-8f9e-042c46428235)</kbd>

Accedemos mediante el link a rightscheck.php y observamos la siguiente tabla resumen de carpetas a las que habría que conceder acceso:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/4a27ec8f-fbbb-4b4c-a0d8-7787fe3caf9f)</kbd>

Damos los permisos solicitados a los directorios:

```shell
sudo chmod 777 classes
sudo chmod 777 OSS_SNMP
sudo chmod 777 css
sudo chmod 777 template
sudo chmod 777 font
sudo chmod 777 images
sudo chmod 777 locales
sudo chmod 777 saml
sudo chmod 777 vendor
```

Y creamos los directorios que faltan. Luego también les asignamos los permisos:

```shell
cd /var/www/html
sudo mkdir assets
cd assets
sudo mkdir drawings
sudo mkdir pictures

sudo chmod 777 drawinds
sudo chmod 777 pictures
cd ..
sudo chmod 777 assets
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/d697d79c-67ce-4fd5-a129-78ec72e32f35)</kbd>

Así nos queda el cuadro resumen de la instalación:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/5e31a675-95c7-4da4-8ddc-20bdd5a6e2e5)</kbd>

Finalmente, hacemos una copia del fichero db.inc.ph-dist en db.inc.php tal y como se nos indica:

```shell
sudo cp db.inc.ph-dist db.inc.php
```

Y lo editamos para podener las credenciales de acceso a la BD si no lo habíamos hecho antes. Ahora nos aparece con un aspecto mucho más bonito y podemos seleccionar el idioma deseado:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/afaf9f8c-7a2c-434c-9191-f74c24bfa8fc)</kbd>


