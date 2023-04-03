# osTicket-Installation-Guide-Windows
Guía de instalación de osTicket Core, v1.17-rc4 en Windows 10

### 0.666

Ver última parte antes de instalar. Al final fue imposible hacer funcionar

:'(

### 0.  PRERREQUISITOS

To install osTicket, your web server must have PHP 8.0 and MySQL 5.0 (or better) installed. If you are unsure whether your server meets these requirements, please check with your host or webmaster before proceeding with the installation.

You will need one MySQL database with valid user, password and hostname handy during installation. MySQL user must have FULL privileges on the database. If you are unsure whether you have these details or if the user has sufficient permissions, please consult your host or database admin before proceeding.

### 1. CONFIGURACIÓN DE IIS

![image](https://user-images.githubusercontent.com/20743678/190078787-7da0c0d9-053f-4d2f-9c65-d8bbb7de73a7.png)

![image](https://user-images.githubusercontent.com/20743678/190078879-4204ad11-c339-4bbb-bd00-67852f19949a.png)

![image](https://user-images.githubusercontent.com/20743678/190079016-4208960f-f229-4433-b87f-647d9121ee9c.png)

### 2. INSTALACIÓN DE PHP

![image](https://user-images.githubusercontent.com/20743678/190082233-d32582ab-a434-48a0-bbf2-6994313d785b.png)

https://windows.php.net/downloads/releases/php-8.0.17-nts-Win32-vs16-x64.zip

![image](https://user-images.githubusercontent.com/20743678/190077537-8eff03dd-fd09-44c9-a562-84a4094bfcac.png)

https://windows.php.net/downloads/releases/

![image](https://user-images.githubusercontent.com/20743678/190077771-e8944e20-544d-4946-8187-a88182e1af8b.png)

https://windows.php.net/downloads/releases/php-8.1.10-nts-Win32-vs16-x64.zip

![image](https://user-images.githubusercontent.com/20743678/190078069-8455caa1-6fcc-4df2-91b3-0e89b9ae729e.png)

++++++++++++++++++++++++++++++++++++++++++++++++++

![image](https://user-images.githubusercontent.com/20743678/190080418-cf33fde7-5b40-4950-8c54-24ac6474b23f.png)

![image](https://user-images.githubusercontent.com/20743678/190080639-9d424d32-8f94-414b-af73-ad41c123ac04.png)

![image](https://user-images.githubusercontent.com/20743678/190080960-f6ef7feb-71ef-41b6-8d80-517ecb59d62a.png)


### 3. INSTALACION DE MARIA DB

![image](https://user-images.githubusercontent.com/20743678/190081285-202d4112-49ef-446c-9957-a181d6da9bc7.png)

![image](https://user-images.githubusercontent.com/20743678/190081602-d99dfa89-d8ed-496b-8328-411a0df7049d.png)

![image](https://user-images.githubusercontent.com/20743678/190081829-db1301aa-1b4e-4b2b-b5a0-50ae567c491f.png)

![image](https://user-images.githubusercontent.com/20743678/190081903-59a76f34-924c-49b8-85f1-9e9d9d4ba019.png)

### 4. INSTALACION DE PHP MANAGER FOR IIS

![image](https://user-images.githubusercontent.com/20743678/190082137-c141be74-988d-42c4-868e-8cd62690bc21.png)

![image](https://user-images.githubusercontent.com/20743678/190082547-40ab720c-f9cd-4ef2-a00e-9f8ad27e5b38.png)

https://www.phpmanager.xyz/

![image](https://user-images.githubusercontent.com/20743678/190082712-1f1e94fe-38a7-4200-9c6b-c7ba7c935264.png)

![image](https://user-images.githubusercontent.com/20743678/190082859-90aa0b02-3e5f-425c-8b18-6010481b0299.png)

![image](https://user-images.githubusercontent.com/20743678/190086815-6b5ea9ef-13ef-4062-b5aa-fde8149742df.png)

![image](https://user-images.githubusercontent.com/20743678/190087006-d54919c7-5707-4dbc-94f8-05e488af0201.png)

### 5. CONFIGURACION

![image](https://user-images.githubusercontent.com/20743678/190087387-a3352cb5-c1b4-475e-b38e-68045e62c849.png)

![image](https://user-images.githubusercontent.com/20743678/190087795-d7435760-0323-417b-be58-027c7488f1d9.png)

![image](https://user-images.githubusercontent.com/20743678/190089041-e3cf195e-e5c3-4d1a-9af8-a65846b6078b.png)

Cerrar el administrador de IIS y volver a abrirlo

![image](https://user-images.githubusercontent.com/20743678/190089526-b296d635-9bf7-469f-b93f-666d80f2bb84.png)

![image](https://user-images.githubusercontent.com/20743678/190096999-173292be-0fe1-44f0-b234-46d09d97677b.png)

![image](https://user-images.githubusercontent.com/20743678/190097177-5151217d-6642-45d3-b071-c3c088da6a1e.png)

![image](https://user-images.githubusercontent.com/20743678/190097305-37a9d6b4-44fe-4794-96f2-2268a8de6daf.png)

### 6. INSTALACION DE OS TICKET

![image](https://user-images.githubusercontent.com/20743678/190097531-2456b393-7fb3-44c3-85ac-7ec5c25b3fa7.png)

![image](https://user-images.githubusercontent.com/20743678/190097746-e45d3bc6-c810-473b-8663-c8d662ed361c.png)

![image](https://user-images.githubusercontent.com/20743678/190097894-41613b2a-c060-4243-8342-5ef55f5321ae.png)

![image](https://user-images.githubusercontent.com/20743678/190098002-538abad2-ceac-43e0-b421-9123807d3d92.png)

![image](https://user-images.githubusercontent.com/20743678/190098154-0a1c786e-af43-4aac-a78a-b0198e61e475.png)

![image](https://user-images.githubusercontent.com/20743678/190098505-6575faa9-c3a9-49e1-8eb6-0e69efd6f876.png)

Contenido de UPLOAD a /

![image](https://user-images.githubusercontent.com/20743678/190099594-3a43c7f2-c781-4ccd-a3f4-c33d6c958774.png)

![image](https://user-images.githubusercontent.com/20743678/190104142-efe255fe-13b0-4a58-8d5e-0cc323943cb4.png)

![image](https://user-images.githubusercontent.com/20743678/190104574-b6d96312-5cc5-4a18-8a9e-53ff769ca7b9.png)


### 7. CONCLUSION FINAL

No pude terminar de configurar todas las dependencias del IIS para el PHP . Abando y pruebo con Ubuntu y Apache
