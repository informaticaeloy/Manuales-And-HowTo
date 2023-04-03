# ThePhish-Installation-Guide-Docker
Instalación de ThePhish usando Dockers en Ubuntu Desktop 22.04 LTS

Welcome to the ThePhish-Installation-Guide-Docker wiki!

* Instalar Ubuntu Desktop 22.04LTS (VM en VMWare, 4GB RAM, 2 Cores, 30GB HD, network en Bridge)
* Tras todo el asistente inicial:
  ```shell
  sudo apt-get update 
  ```
  ```shell
  sudo apt-get upgrade
  ```
* Pasos previos

  > configurar la dirección IP 

  > instalar el servicio SSH 

  ```shell
  sudo apt-get install ssh
  ```

  > configurar el autoarranque de SSH

  ```shell
  sudo systemctl enable ssh
  ```

  > comprobar estado del servicio ssh

  ```shell
  sudo systemctl status ssh
  ```

  > instalar Java
  ```shell
  sudo apt-get install default-jre
  ```
  
  > instalar las vm-tools para poder copiar y pegar y arrastrar ficheros entre la máquina anfitrion y la virtual
  ```shell
  sudo apt-get install open-vm-tools-desktop
  ```

* Instalar Dockers y Dockers-compose

  > Primero, actualice su lista de paquetes existente:
    
  ```shell
  sudo apt-get update
  ```
    
  > A continuación, instale algunos paquetes de requisitos previos que permitan a apt-get usar paquetes a través de HTTPS:
     
  ```shell
  sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
  ```
      
  > Luego, añada la clave de GPG para el repositorio oficial de Docker en su sistema:
    
  ```shell
  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
   ```
      
    > Agregue el repositorio de Docker a las fuentes de APT:
    > 
    ```shell
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
     ```
     
    > A continuación, actualice el paquete de base de datos con los paquetes de Docker del repositorio recién agregado:
    > 
    ```shell
    sudo apt-get update
     ```
     
    > Asegúrese de estar a punto de realizar la instalación desde el repositorio de Docker en lugar del repositorio predeterminado de Ubuntu:
    > 
    ```shell
    apt-cache policy docker-ce
     ```
     
    > Si bien el número de versión de Docker puede ser distinto, verá un resultado como el siguiente:
     
    ```
    docker-ce:
    Installed: (none)
    Candidate: 5:20.10.17~3-0~ubuntu-focal
    Version table:
    5:20.10.17~3-0~ubuntu-focal 500
         500 https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
    ```
    
    > Observe que docker-ce no está instalado, pero la opción más viable para la instalación es del repositorio de Docker para Ubuntu 20.04 (focal).
    
    > Por último, instale Docker:
    
    ```shell
    sudo apt-get install docker-ce
    ```
      
    > Instalamos Docker-Compose
    
    ```shell
    sudo apt-get install docker-compose
    ```

* Ejecute los contenedores con Docker Compose
   
   > Clonar el repositorio
   
   ```shell
   git clone https://github.com/emalderson/ThePhish.git
    ```

   > Si nos sale un error de ejecución o no tenemos git instalado en el sistema:

   ```shell
   sudo apt-get install git-all
   ```
 
   > Se nos creará la carpeta 'ThePhish' y una subcarpeta llamada 'docker'. Accedemos a ella:
   ```shell
   cd /ThePhish/docker
   ```

   > Y dentro de la subcarpeta docker, ejecutamos el comando siguiente:
   ```shell
   sudo docker-compose up
   ```

   > Esperamos a que termine la instalación:

   ![image](https://user-images.githubusercontent.com/20743678/181035255-03b6db11-52a4-47df-8666-8d8bb79a6331.png)

   > Si nos salen muchos errores, como en el ejemplo de la imagen...
   
   ![image](https://user-images.githubusercontent.com/20743678/181040161-78dfabc5-8d05-4cca-8c66-fd8cab779a1c.png)

   > ...puede que Docker-compose no tenga permisos de escritura en alguna carpeta. Para solucionarlo, hacemos CTRL + C dos veces para forzar el stop y luego ejecutamos los siguientes comandos:
   
   ```shell
   sudo docker-compose stop
   ```
   
   ```shell
   sudo chown -R 1000:1000 vol/index vol/data vol/elastic*
   ```
   
   ```shell
   sudo docker-compose up
   ```
   > Si nos siguen saliendo erroes, como en el ejemplo de la imagen...  

   ![image](https://user-images.githubusercontent.com/20743678/181041828-648b174a-f370-4687-a51b-6b214cb53f41.png)
   
   > Comprobaremos varios parámetros:

![image](https://user-images.githubusercontent.com/20743678/181042546-89cedb97-3776-47a5-a974-9f8efeae09b5.png)

![image](https://user-images.githubusercontent.com/20743678/181042777-780522ce-607e-4c73-9dc6-ad59df4fb9dc.png)

![image](https://user-images.githubusercontent.com/20743678/181042882-03896957-8d57-4581-a1af-bdfe5356e367.png)

![image](https://user-images.githubusercontent.com/20743678/181043074-1235d004-016d-4cc9-8a8c-166df92a1562.png)

![image](https://user-images.githubusercontent.com/20743678/181044468-c022927c-dd84-42f3-9c46-c78b97a43002.png)

![image](https://user-images.githubusercontent.com/20743678/181047764-f9cade92-52ac-485b-bd78-78a10b131351.png)

cd thehive
sudo nano application.conf

![image](https://user-images.githubusercontent.com/20743678/181048967-7d84f95d-92d0-4d11-a6cc-eb9e06388656.png)

![image](https://user-images.githubusercontent.com/20743678/181049780-fa27225e-def0-4aa0-b635-a467140c4736.png)

![image](https://user-images.githubusercontent.com/20743678/181051871-2e930f0b-c30e-475e-952e-a7ae2235e2c2.png)

![image](https://user-images.githubusercontent.com/20743678/181052536-0d790ab1-ecf4-48a1-9a18-15dd13e88ddc.png)

![image](https://user-images.githubusercontent.com/20743678/181051656-612bf520-af66-4488-a906-db99ffdc47b7.png)

Configure the IMAP server

![image](https://user-images.githubusercontent.com/20743678/181052060-5706a38b-afd6-4d59-9de5-11fcdd42f4d3.png)

Configure the MISP container

![image](https://user-images.githubusercontent.com/20743678/181194851-8191f8a2-3722-4c76-ad5b-752242c99160.png)

![image](https://user-images.githubusercontent.com/20743678/181199302-b4b5425e-09a7-4fa7-86cd-c8c489262cc2.png)

si nos da problemas Mozilla Firefox, instalamos Chrome:

![image](https://user-images.githubusercontent.com/20743678/181201426-21c76d97-e120-4123-a7d9-48183c8cdcaf.png)

Primero descargamos el paquete con el Google Chrome más reciente:

wget -c https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

Cuando el proceso termine, actualizamos con el comando:

sudo apt-get update

Y una vez termine de actualizar instalamos la librería de indicadores de sistema para poder ver el icono de Google Chrome en nuestro lanzador (y algunos más):

sudo apt-get install libappindicator1

Y para terminar, instalamos Google Chrome:

sudo dpkg -i google-chrome-stable_current_amd64.deb

![image](https://user-images.githubusercontent.com/20743678/181206015-fe3b65df-97bf-4cba-8737-629342c537b8.png)

Configure the MISP container
Go to https://localhost (https://localhost en un navegador en la propia máquina. En remoto no funciona ya que nos redirecciona a localhost hasta que lo configuremos)
and log in with the default credentials:
Username: admin@admin.test
Password: admin
Create a new organization
Administration -> Add Organization
Name: <YourOrganizationName>
Click on "Generate UUID"
Click on "Submit"
Change settings
Administration -> Server Settings and Maintenance -> MISP Settings
Change the field MISP.live to True
Change the field MISP.baseurl to https://localhost
Change the field MISP.external_base_url to https://localhost
Change the field MISP.org to <YourOrganizationName>
Change the field MISP.host_org_id to <YourOrganizationName>
Create a new user that is used for the integration with TheHive and Cortex
Administration -> Add User
email: sync_user@<YourOrganizationDomain>
organization: <YourOrganizationName>
role: Sync User
Uncheck all the checkboxes
click on "Create user"
Obtain the Authentication key of the Sync User
Administration -> List Users
Click on the "Eye" on the right for the just created user (View)
Click on "Auth Keys"
Delete the already created auth key
Administration -> List Users (again)
Click on the "Eye" on the right for the just created user (again)
Click on "Auth Keys" (again)
Click on "Add authentication key"
Click on "Submit" and save it for later
Enable MISP feeds
Sync Actions -> List Feeds -> Load default feed metadata -> All feeds
Select the feeds to enable
Click on "Enable selected" (Marcamos todos de las 4 páginas que salen. Hay 71 en total)
  
Configure the Cortex container
Go to http://localhost:9001 and click on "Update database"
Create a new admin user
Login: admin@<YourOrganizationName>
Name: admin
Password: <Password>
Create a new organization
Organizations -> Add Organization
Name: <YourOrganizationName>
Description: <YourOrganizationDescription>
Create a new orgadmin user in that organization
Click on the newly created organization <YourOrganizationName>
Click on "Add user"
Login: thephish@<YourOrganizationName>
Full name: ThePhish
Roles: read, analyze, orgadmin
Click on "New password" for the newly created user and set a password for that user
Create another user in that organization that is used for the integration with TheHive and to use the API
Click on the newly created organization <YourOrganizationName>
Click on "Add user"
Login: integration_account@<YourOrganizationName>
Full name: integration_account
Roles: read, analyze
Click on "Create API key" and then on "Reveal" for the newly created user and save it for later
Log out the admin user and log in the orgadmin user (ThePhish)
