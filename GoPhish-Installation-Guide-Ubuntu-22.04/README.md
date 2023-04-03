# GoPhish-Installation-Guide-Ubuntu
Sistema de gestión de campañas de Phishing para test de la concienciación y precaución de los usuarios de mail en tu empresa

# GLPI-Installation-Guide-Ubuntu_22.04
GLPI Installation Guide Ubuntu 22.04

### 0.666 CONCLUSIONES FINALES

### 1. INSTALACIÓN DE APACHE

```shell
apt-get install apache2
```

<kbd>![image](https://user-images.githubusercontent.com/20743678/190367570-093d6ac2-c0b4-4a21-b824-cae5bb0f524e.png)</kbd>

En un navegador, accedemos a la URL de nuestro máquina virtual y comprobamos si funciona:

<kbd>![image](https://user-images.githubusercontent.com/20743678/190367841-1938c201-9728-45b7-85e6-ec12a9243a86.png)</kbd>

### 2. INSTALACIÓN DE PHP 8

```shell
sudo apt install ca-certificates apt-transport-https software-properties-common
```

<kbd>![image](https://user-images.githubusercontent.com/20743678/190368199-ff183676-8553-48b7-a5f1-d292dcc2c886.png)</kbd>

```shell
sudo add-apt-repository ppa:ondrej/php
```

<kbd>![image](https://user-images.githubusercontent.com/20743678/190368451-23265c03-e5ef-4f68-b0bf-31f9cd753b5d.png)</kbd>


```shell
sudo apt install php8.0 libapache2-mod-php8.0
```

<kbd>![image](https://user-images.githubusercontent.com/20743678/190368692-aac9c322-5e4f-49cc-8958-a81dd3dacc53.png)</kbd>


```shell
sudo systemctl restart apache2
```

```shell
php -v
```

<kbd>![image](https://user-images.githubusercontent.com/20743678/190368901-e0382902-a13d-4cd1-b787-579ea2a61183.png)</kbd>

#### 2.1 INSTALACIÓN DE LA EXTENSIÓN MYSQLI PARA PHP 8

```shell
sudo apt install php8.0-mysqli 
```

<kbd>![image](https://user-images.githubusercontent.com/20743678/190369709-a8a97c4f-1566-4406-b1f3-9002e1756e64.png)</kbd>

Para comprobar que funciona, creamos un fichero en /var/www/html llamado info.php por ejemplo

```shell
nano /var/www/html/info.php
```

y escribimos estas líneas:

 ```shell
<?php
phpinfo();
?>
```

<kbd>![image](https://user-images.githubusercontent.com/20743678/190370162-be39a198-143b-4dce-9141-5c5c39810069.png)</kbd>

Desde nuestro navegador, visitamos la URL de nuestro servidor Apache y añadimos el nombre del fichero que hemos creado:

```shell
http://192.168.46.214/info.php
```

Si todo está correcto hasta ahora, veremos algo similar a esto:

<kbd>![image](https://user-images.githubusercontent.com/20743678/190371854-5b08c8a9-bea8-4078-a629-b43c2156a28b.png)</kbd>

#### Warning - :skull: Haz un Snapshot :eyes:

### 3. INSTALACIÓN DE MYSQL DATABASE

```shell
sudo apt install mysql-server
```

<kbd>![image](https://user-images.githubusercontent.com/20743678/190381304-84dea3a9-69d8-4e68-8cda-6aca37be3508.png)</kbd>

#### 3.1 CONFIGURACIÓN DE MYSQL

```shell
sudo mysql_secure_installation
```
