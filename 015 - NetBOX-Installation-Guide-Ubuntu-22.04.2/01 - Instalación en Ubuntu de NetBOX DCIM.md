# NetBOX-Installation-Guide-Ubuntu
Sistema free basado en web para gestión de Infraestructuras de Data Centers.

:house_with_garden: Website: https://netbox.dev/

:books: Wiki: https://docs.netbox.dev/

:computer: GitHub: https://github.com/netbox-community/netbox

:rocket: Releases: https://github.com/netbox-community/netbox/releases

Versión instalada descrita en este manual: v3.5.6 - 2023-07-10

# NetBOX-Installation-Guide-Ubuntu_22.04
NetBOX Installation Guide Ubuntu 22.04 Desktop

### 0.666 CONCLUSIONES FINALES

### 0. REQUISITOS INICIALES
Partimos de un Ubuntu Desktop 22.04 instalado como máquina virtual en un VMWare con 2cores, 4 GB de RAM y 20GB de disco duro, red tipo NAT con acceso a internet

El sistema lo tenemos actualizado con los comandos:

```shell
sudo apt-get update && sudo apt-get upgrade
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/68ef6d8b-83d8-4d66-87a5-60219bb4dfba)</kbd>

### 1. INSTALACIÓN DE POSTGRESQL DATABASE

Instalamos PostgreSQL con el siguiente comando:

```shell
sudo apt install -y postgresql
```


<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/18699fae-b569-41db-9a74-c759edf1cfc9)</kbd>

:scissors: [imagen recortada]

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/2268f48f-6484-4e21-b2bb-da8140fc825f)</kbd>

Comprobamos si se ha instalado correctamente y qué versión se ha instalado:

```shell
psql -V
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/56f095e6-a99c-43ea-96f5-ac1b432c7469)</kbd>

#### 1.1 CREACIÓN DE LA BASE DE DATOS DENTRO DE POSTGRESQL

Creamos una carpeta temporal para destinarla a carpeta de trabajo. La llamaremos /temp

```shell
cd /
```

```shell
sudo mkdir temp
```

```shell
cd temp
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/6b8b2206-59ac-427e-8e52-1d20a00081ef)</kbd>

Accedemos a la consola de PostgreSQL como root:

```shell
sudo -u postgres psql
```
<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/66223b92-3847-4877-a3f0-019f85c2c40f)</kbd>

Creamos la base de datos llamada 'netbox' dentro de PostgrSQL:

```shell
CREATE DATABASE netbox;
```

Creamos el usuario llamado 'netbox' dentro de PostgreSQL. Ponemos la contraseña que queramos para el usuario. En este ejemplo pondremos una insegura: "passnetbox". Pon una contraseña segura en un entorno de producción.

```shell
CREATE USER netbox WITH PASSWORD 'passnetbox';
```

Asignamos permisos a la base de datos "netbox" para el usuario 'netbox':

```shell
ALTER DATABASE netbox OWNER TO netbox;
```

Salimos con el comando '\q':

```shell
\q
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/043ea5f0-838c-486c-9d4a-a4cd8a1f5f8d)</kbd>

Probamos la conexión del nuevo usuario a la BD. Si estás intentando conectar desde un pc a otro remotamente, cambia 'localhost' por el nombre del equipo remoto. En esta caso, como estamos haciendo la conexión desde el mismo equipo donde está instalado PostgrSQL, usamod 'localhost:

```shell
psql --username netbox --password --host localhost netbox
```

Una ver dentro de la consola de PostgreSQL, vcerificamos la información de la conexión con el comando siguiente:

```shell
\conninfo
```

Salimos con el comando siguiente:

```shell
\q
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/a57c3e05-76d1-4ed9-a473-d4ec694f718a)</kbd>

#### 1.2 INSTALACIÓN DE REDIS

Redis es un almacén de KEY-VALUE en memoria que NetBox emplea para el almacenamiento en caché y la cola. Esta sección implica la instalación y configuración de una instancia local de Redis. Si ya tienes un servicio de Redis instalado, pasa a la siguiente sección.

Lo instalamos con el comando siguiente:

```shell
sudo apt-get install -y redis-server
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/4a73a7e5-71ea-425d-8a9e-7d583908596e)</kbd>

Verificamos que se ha instalado correctamente y confirmamos que la versión instalada es posterior a la 4.0 para que sea compatible con la versión de NetBOX::

```shell
redis-server -v
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/84623fcf-0330-4c25-a736-c9031856ebde)</kbd>

El fichero de configuración de REDIS está en /etc/redis.conf o /etc/redis/redis.conf, pero con la configuración por defecto es suficiente.

Podemos probar si funciona correctamente con el siguiente comando:

```shell
redis-cli ping
```

Si todo funciona bien, deberíamos recibir el mensaje 'PONG':

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/c9a1340e-6adc-4adc-90af-e860fc419aa0)</kbd>

#### 1.3 INSTALACIÓN DE NETBOX

NetBOX requiere Python 3.8, 3.9, 3.10 or 3.11. Lo instalamos junto con varias dependencias a otros paquetes con el comando siguiente:

```shell
sudo apt install -y python3 python3-pip python3-venv python3-dev build-essential libxml2-dev libxslt1-dev libffi-dev libpq-dev libssl-dev zlib1g-dev
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/b6a0c978-58cf-46e7-9b33-e25caa0fa739)</kbd>

:scissors: [imagen recortada]

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/fa592b5d-2bde-41c2-8051-b9ea055c1a2d)</kbd>

Verificamos la versión instalada:

```shell
python3 -V
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/4e5a7f8a-69cd-4a8a-8e8a-a8c334677566)</kbd>

Buscamos en esta URL cuál es la última versión y revisamos qué ruta es:

:rocket: https://github.com/netbox-community/netbox/releases

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/df3f7e90-0caa-444d-96f9-b12427d222c3)</kbd>

Nos la apuntamos para poder usarla después.

La descargamos con 'wget'. La opción general sería esta:

```shell
sudo wget https://github.com/netbox-community/netbox/archive/refs/tags/vX.Y.Z.tar.gz
```

Sustituyendo la X.Y.Z por la versión deseada, en este caso

```shell
sudo wget https://github.com/netbox-community/netbox/archive/refs/tags/v3.5.6.tar.gz
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/919dbea4-f38a-4d2a-a5bb-b3a563203fa8)</kbd>

Descomprimimos el fichero en la carpeta /opt con el comando siguiente. La opeción general sería:

```shell
sudo tar -xzf vX.Y.Z.tar.gz -C /opt
```

Y en nuestro caso, sustituyendo la X.Y.Z por la versión deseada, sería con este comando:

```shell
sudo tar -xzf v3.5.6.tar.gz -C /opt
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/6d2f0a4b-6948-452b-8348-8dc9ca18d5e7)</kbd>

El contenido del fichero comprimido se ha descomprimido en /opt y se ha creado la carpeta/opt/netbox-3.5.6. Podemos acceder a esta carpeta con el comando:

```shell
cd /opt/netbox-3.5.6
```

y ver el contenido con 'ls':

```shell
ls
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/e8728ad9-1422-44ac-8e36-4391f1c0d6df)</kbd>

La idea es dejar esta carpeta tal y como está, con su nombre incluyendo el nº de versión de NetBOX, y crear un symlink que apunte a ella en /opt/netbox . Lo hacemos con el siguiente comando general:

```shell
sudo ln -s /opt/netbox-X.Y.Z/ /opt/netbox
```

En nuestro caso para la versión c3.5.6 sería este:

```shell
sudo ln -s /opt/netbox-3.5.6/ /opt/netbox
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/425e9ed8-b074-4673-b33f-3f1afce1f45b)</kbd>

De esta forma, podemos tener otras versiones instaladas en paralelo y cuando queramos actualizar, simplemente tendremos que actualizar el symlink a /opt . Para ver la configuración de este symlink, haremos lo siguiente:

```shell
ls -l /opt | grep netbox
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/9fa146e5-5145-4ca4-adde-63253bcf556a)<kbd>

Ahora crearemos una cuenta de usuario del sistema llamada 'netbox'. Configuraremos los servicios WSGI y HTTP para que se ejecuten en esta cuenta. También asignaremos a este usuario la propiedad del directorio multimedia. Esto asegura que NetBox podrá guardar los archivos cargados. Lo haremos con los comandos siguientes:

```shell
sudo adduser --system --group netbox
```

```shell
sudo chown --recursive netbox /opt/netbox/netbox/media/
```

```shell
sudo chown --recursive netbox /opt/netbox/netbox/reports/
```

```shell
sudo chown --recursive netbox /opt/netbox/netbox/scripts/
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/071507be-8596-41cc-9b22-200e0941bf98)</kbd>

Ahora configuraremos NetBOX. Para ello, iremos al directorio de configuración de NetBox (/opt/netbox/netbox/netbox) y haremos una copia del fichero 'configuration_example.py' en 'configuration.py'. Este archivo contendrá todos los parámetros de configuración locales.

```shell
cd /opt/netbox/netbox/netbox
```

```shell
sudo cp configuration_example.py configuration.py
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/81cbe49f-b46b-4791-b5b2-65f8b5ae9afc)</kbd>

Editaremos este fichero:

```shell
sudo nano configuration.py
```

y configuraremos lo siguiente:

##### ALLOWED_HOSTS

Aquí añadiremos los host desde los que se puede acceder a nuestro sistema. Podemos poner nombres de hosts o direcciones IP. A modo de ejemplo sería:

```shell
ALLOWED_HOSTS = ['netbox.example.com', '192.0.2.123']
```

En los que sólo el host con nombre 'netbox.example.com' o el equipo con la IP '192.0.2.123' podrían acceder.

En nuestro caso, para que cualquier equipo pueda acceder, escribiremos lo siguiente:

```shell
ALLOWED_HOSTS = ['*']
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/3b8bcfa3-17e0-4000-9b87-df24e52030db)</kbd>

##### DATABASE

Este parámetro contiene los detalles de configuración de la base de datos. Hay que definir el nombre de usuario y la contraseña que se utilizó cuando se configuró PostgreSQL. Si el servicio se ejecuta en un host remoto, actualice los parámetros HOST y PORT según corresponda. 

```
DATABASE = {
    'NAME': 'netbox',               # Database name
    'USER': 'netbox',               # PostgreSQL username
    'PASSWORD': 'J5brHrAXFLQSif0K', # PostgreSQL password
    'HOST': 'localhost',            # Database server
    'PORT': '',                     # Database port (leave blank for default)
    'CONN_MAX_AGE': 300,            # Max database connection age (seconds)
}
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/0d105ba3-c60d-4ca9-9f07-0806e41176bd)</kbd>


