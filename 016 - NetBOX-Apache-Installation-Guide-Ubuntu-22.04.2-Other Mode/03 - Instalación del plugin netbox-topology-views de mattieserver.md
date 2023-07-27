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

Para asegurar que el plugin se reinstala automáticamente cada vez que se hace un upgrade de NetBox, crea un fichero llamado 'local_requirements.txt' (si todavía no existe) en el directorio raiz de NetBox y añade el paquete nextbox-plugin-device-map:

##### Instalación del plugin desde PyPI:

```shell
echo netbox-plugin-device-map | sudo tee -a /opt/netbox/local_requirements.txt
```

```shell
pip3 install -U -r /opt/netbox/local_requirements.txt
```

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
 'netbox_device_map'
]
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/a284eb01-7721-420c-bddd-4275e29cead3)</kbd>

Reiniciamos el servicio NetBox WSGI para aplicar los cambios:

```shell
sudo systemctl restart netbox
```

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/b17c860e-edee-47af-82e0-09513aa74d47)</kbd>

Y ya podremos ver algo similar a esto en nuestro navegador:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/d38b4829-f815-4513-9da4-641d23f0e539)</kbd>



