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
...
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

### 2. INSTALACIÓN DE PHP 8
