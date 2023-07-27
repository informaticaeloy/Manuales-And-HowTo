### INSTALACIÓN DE PLUGINS

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
sudo pip3 install -U -r /opt/netbox/local_requirements.txt
```

##### Hacemos un 'Collect' de los ficheros estáticos

*IMPORTANTE:* no hacerlo con sudo

```shell
 python3 /opt/netbox/netbox/manage.py collectstatic
```

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/d2e92de4-bf65-42cf-8509-a211e2ed3754)

To enable plugin, add the plugin's name to the PLUGINS list in configuration.py (it's usually located in /opt/netbox/netbox/netbox/) like so:

PLUGINS = [
    'netbox_device_map'
]

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/a284eb01-7721-420c-bddd-4275e29cead3)

Restart NetBox WSGI service to apply changes:

sudo systemctl restart netbox
