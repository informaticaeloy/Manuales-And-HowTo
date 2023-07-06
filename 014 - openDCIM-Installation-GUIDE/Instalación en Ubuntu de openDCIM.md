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
+ php-snmp
+ snmp-mibs-downloader
+ php-curl
+ php-gettext
+ graphviz

Que podemos instalarlos todos al mismo tiempo con el ocmando siguiente:

```shell
sudo apt-get install php-snmp snmp-mibs-downloader php-curl php-gettext graphviz
```

O de uno en uno :

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

<kdb>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/109910d3-e184-4be5-b12e-7e9c876f51a1)</kdb>


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

<kdb>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/35c6f085-7247-451a-beb2-e417c0ce8472)</kdb>

### 4. DAR PERMISOS A APACHE PARA ESCRITURA EN CIERTOS DIRECTORIOS

Según la propia documentación oficial:

'There are times when Apache will need to be able to write to two of the directories - specifically the /drawings (maps of your data centers) and /pictures (pictures of your devices) folders. To do this, we need to set the group for those folders to the group that Apache is running as. On a default Ubuntu 15.04 server, that group is called www-data.'

Pero al lanzar el comando citado, da error, pues los dos folders en concreto no existen ('pictures' ni 'drawings'). Hay una carpeta que pudiera ser similar llamada 'images'. De momento no hacemos nada, pero dejamos aquí pauntado el comando pr si en un futuro la ejecución de la plaicación nos arroja algún error, tal vez sea esta configuración que hemos de ejecutar:

```shell
sudo chgrp -R www-data /var/www/html/pictures /var/www/html/drawings
```

### 5.INSTALACIÓN DE MYSQL

```shell
sudo apt-get install mysql-client mysql-server
```

<kdb>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/f6e91c53-21b0-403c-9bda-035520a62aa8)</kdb>

:scissors: [imagen recortada]

<kdb>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/cd622087-9fea-4173-908c-368ce573080e)</kdb>

### 6. CREACIÓN DE LA BASE DE DATOS


