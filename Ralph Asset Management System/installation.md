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

```shell
sudo apt-get install mysql-server nginx ralph-core
```

<kbd>![image](https://user-images.githubusercontent.com/20743678/229489799-cd2f57b6-a220-41fc-9bc4-0c76d059468f.png)</kbd>
