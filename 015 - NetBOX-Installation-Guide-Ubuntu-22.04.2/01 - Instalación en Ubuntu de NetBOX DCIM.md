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

```shell

```
<kbd></kbd>
```shell

```
<kbd></kbd>
```shell

```
<kbd></kbd>
```shell

```
