# ISARD_VDI-Installation-Guide

### 0. Prerrequisitos

Fedora 36 Workstation VM under VMWare, 2 cores, 8192 RAM, 20GB HD, network bridge

### 1. Preparación de Fedora

> Buscar actualizaciones:

```shell
sudo dnf upgrade --refresh
```

![image](https://user-images.githubusercontent.com/20743678/187608306-bb4c52b0-9f51-4548-825c-d065ae15c1ed.png)

![image](https://user-images.githubusercontent.com/20743678/187608379-4468a0dc-c910-4571-844b-4a26dceea289.png)

> Actualiza el plugin de DNF:

```shell
sudo dnf install dnf-plugin-system-upgrade
```

![image](https://user-images.githubusercontent.com/20743678/187608534-439b69ce-4e03-408a-966f-8e17492ce425.png)

### 2. Instalación de Docker y Docker Compose

sudo dnf remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-selinux \
                  docker-engine-selinux \
                  docker-engine
                  
![image](https://user-images.githubusercontent.com/20743678/187667171-0cbafde3-97d6-4771-ba55-503a3b2405a0.png)

sudo dnf -y install dnf-plugins-core

sudo dnf config-manager \
    --add-repo \
    https://download.docker.com/linux/fedora/docker-ce.repo
    
![image](https://user-images.githubusercontent.com/20743678/187667509-84ed79a3-98ad-4711-aa35-21f3356feee8.png)

![image](https://user-images.githubusercontent.com/20743678/187667605-4226217a-7c00-4ae9-ba07-d640c881d129.png)

sudo systemctl start docker

sudo systemctl enable docker

![image](https://user-images.githubusercontent.com/20743678/187667770-3756529d-4f05-49b1-9598-d98b5067285a.png)

sudo yum install python3-pip

![image](https://user-images.githubusercontent.com/20743678/187667945-7ba17426-56c3-4869-b189-b787705322de.png)

sudo pip3 install docker-compose

![image](https://user-images.githubusercontent.com/20743678/187668051-bfb329c8-1d57-4e90-868b-8f2128cc70ea.png)

![image](https://user-images.githubusercontent.com/20743678/187668099-02b23020-6af8-4747-bbbb-233719b0b414.png)

### 3. Descargar de IsardVDI y despliegue de docker

wget https://isardvdi.com/docker-compose.yml

sudo docker-compose pull

![image](https://user-images.githubusercontent.com/20743678/187668678-16df9e11-0f8b-4228-8307-b9f8f9fd4c68.png)


