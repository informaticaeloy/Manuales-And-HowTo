### Ralph Asset Management System

### Referencias

https://ralph-ng.readthedocs.io/en/stable/installation/installation/

<kbd>![image](https://user-images.githubusercontent.com/20743678/229485908-777aba22-1e51-48e9-a0b0-2637a5d0edf0.png)</kbd>

### Requisitos

- VM Ubuntu 22.04.2 Desktop 64 bits
- RAM 4GB
- 2 CPUs
- Hard Disk 30GB

### Instalación

```shell
curl -sL https://packagecloud.io/allegro/ralph/gpgkey | sudo apt-key add -
```

```shell
sudo sh -c "echo 'deb https://packagecloud.io/allegro/ralph/ubuntu/ bionic main' >  /etc/apt/sources.list.d/ralph.list"
```

```shell
sudo apt-get update
```
<kbd>![image](https://user-images.githubusercontent.com/20743678/229489799-cd2f57b6-a220-41fc-9bc4-0c76d059468f.png)</kbd>

```shell
sudo apt-get install mysql-server
```

<kbd>![image](https://user-images.githubusercontent.com/20743678/229490386-c8e3f6e2-31ce-48ac-830f-1ae85d2b4119.png)</kbd>

<kbd>![image](https://user-images.githubusercontent.com/20743678/229490508-df8e09cc-b941-44cf-ac7d-9d70e5764b16.png)</kbd>

```shell
sudo apt-get install nginx 
```

<kbd>![image](https://user-images.githubusercontent.com/20743678/229490759-8e0d59a9-77b1-4321-9f0b-5b4b233512c0.png)</kbd>

<kbd>![image](https://user-images.githubusercontent.com/20743678/229490864-6de0ce0b-52a0-461e-a4cd-29e2bb841a94.png)</kbd>

```shell
sudo apt-get install ralph-core
```

<kbd>![image](https://user-images.githubusercontent.com/20743678/229491191-587cd527-7527-4da3-9cf5-44226074af34.png)</kbd>

### Conclusiones finales

A partir de este momento pide tener instalado el paquete "libmysqlclient20", que está deprecated y ya puede instalarse en Ubuntu 22.04. Podríamos hacer un downgrade, peo nuestro sistema dejaría de ser seguro, por lo que abandonamos su despliegue. Probaré con CMDB o el propio Ralph con Docker.

<kbd>![image](https://user-images.githubusercontent.com/20743678/229492966-5264b8f2-5550-4977-9e0c-39e3aebfac69.png)</kbd>
