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
sudo apt-get ipdate
```

```shell
sudo apt-get upgrade
```

### 1. INSTALACIÓN DE APACHE

```shell
apt-get install apache2
```

<kbd>![image](https://user-images.githubusercontent.com/20743678/190367570-093d6ac2-c0b4-4a21-b824-cae5bb0f524e.png)</kbd>

En un navegador, accedemos a la URL de nuestro máquina virtual y comprobamos si funciona:

<kbd>![image](https://user-images.githubusercontent.com/20743678/190367841-1938c201-9728-45b7-85e6-ec12a9243a86.png)</kbd>

### 2. INSTALACIÓN DE PHP 8
