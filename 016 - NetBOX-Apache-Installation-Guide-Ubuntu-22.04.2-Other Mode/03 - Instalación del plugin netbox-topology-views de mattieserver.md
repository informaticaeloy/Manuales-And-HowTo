### REFERENCIAS

https://github.com/mattieserver/netbox-topology-views

### INSTALACIÓN DE PLUGINS

Para hacer una instalación de plugin necesitamos estar como 'root'. No vale con ejecutar los comandos con 'sudo', por lo que lo primero que haremos será cambiarnos a 'root':

```shell
sudo su
```

Si tu instalación de NetBox use entronos virtuales, actívalo de esta forma:

```shell
source /opt/netbox/venv/bin/activate
```

#### 1. Instalar el plugin

Para asegurar que el plugin se reinstala automáticamente cada vez que se hace un upgrade de NetBox, crea un fichero llamado 'local_requirements.txt' (si todavía no existe) en el directorio raiz de NetBox y añade el paquete netbox-topology-views:

##### Instalación del plugin desde PyPI:

```shell
echo netbox-topology-views | sudo tee -a /opt/netbox/local_requirements.txt
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/e3a7819c-1b6f-4594-ab8d-3ebb1609b98c)</kbd>

Como ya es el segundo plugin que vamos a instalar, el fichero local_requirements.txt tendrá este aspecto:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/fbf7622a-a292-4008-8350-1ce04a82adfb)</kbd>

Lanzamos la instalación:

```shell
pip3 install -U -r /opt/netbox/local_requirements.txt
```

En la línea 1 del fichero tenemos el requerimiento de un plugin ya instalado, el netbox-plugin-device-map, por lo que nos alerta de que el requerimiento ya está satisfecho (ver imagen con la marca (1) en rojo), por lo que continúa instalando la línea 2 del fichero, donde está el segundo plugin, netbox-topology-views, el cual instala directamente (ver imagen con la marca (2) en verde):

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/170d09eb-d3f9-4064-b57f-e495caa7ed4b)</kbd>

##### Hacemos un 'Collect' de los ficheros estáticos

```shell
python3 /opt/netbox/netbox/manage.py collectstatic
```

Para activar el plugin, añadimos el nombre del plugin a la lista 'PLUGINS'del fichero 'configuration.py' (que suele estar en '/opt/netbox/netbox/netbox/'):

```shell
sudo nano /opt/netbox/netbox/netbox/configuration.py
```

```shell
PLUGINS = [
 'netbox_device_map',
 'netbox_topology_views'
]
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/8c75dc7e-f625-4b27-b7cd-a6f35583875c)</kbd>

Y la configuración del plugin la haremos bajo el apartado 'PLUGINS_CONFIG':

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/cbee0d71-b546-42af-9aaa-f83df7f274b6)</kbd>

Reiniciamos el servicio NetBox WSGI para aplicar los cambios:

```shell
sudo systemctl restart netbox
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/b17c860e-edee-47af-82e0-09513aa74d47)</kbd>

Hacemos un 'migrate' de la BD con los campos nuevos que usará el plugin:

```shell
python3 /opt/netbox/netbox/manage.py migrate
```

Y un 'collectstatic' para importar ciertos ficheros necesarios a su ruta:

```shell
python3 /opt/netbox/netbox/manage.py collectstatic --no-input
```


<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/0fa591a9-410b-44d9-9c2e-a8730d8bf97e)</kbd>

Y ya podremos ver algo similar a esto en nuestro navegador:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/d65cbdfa-1cfd-443f-b37f-09d28aabcaf9)</kbd>

Si obtenemos un error similar a este al entrar en 'Topology Views' -> 'Images', tendremos que crear la carpeta que hemos definido signar permisos a las nuevas carpetas:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/49e7e532-1f4e-4af0-83f9-fe227b3ec860)</kbd>


