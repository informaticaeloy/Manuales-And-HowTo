## Instalación y uso de Wi-Fi HeatMapper de hnykda en Windows

### Requisitos iniciales
- Microsoft Windows 10/11

### Referencias

https://github.com/hnykda/wifi-heatmapper

<kbd>![image]<img width="1600" height="449" alt="image" src="https://github.com/user-attachments/assets/867dc0a1-f695-4de3-9a37-0aeaa4e93b49" />
</kbd>

### Instalación

Descargamos el .zip del repositorio y lo descomprimimos en nuestra carpeta local:

<kbd><img width="829" height="735" alt="image" src="https://github.com/user-attachments/assets/a80a0822-02d6-4265-9093-721fda5b5453" /></kbd>

Si tenemos instalado git, también lo podemos descargar con el siguiente comando:
```shell
git clone https://github.com/hnykda/wifi-heatmapper.git
cd wifi-heatmapper
```

Si no tenemos npm instalado, lo instalamos con el siguiente comando:

```shell
winget install OpenJS.NodeJS.LTS
```

<kbd><img width="875" height="204" alt="image" src="https://github.com/user-attachments/assets/e078252b-0f89-4cd7-b11e-074adcbd757c" /></kbd>

Si queremos forzar la instalación de otra versión de npm, buscamos las posibles versiones con el siguiente comando:

```shell
winget search OpenJS.NodeJS
```

<kbd><img width="525" height="422" alt="image" src="https://github.com/user-attachments/assets/93d9fa8a-faee-46e4-8437-7fea10a16ee2" />
</kbd>

Y podemos forzar la instalación de la versión deseada, por ejemplo la 25.9.0 con el siguiente comando:

```shell
winget install -e --id OpenJS.NodeJS
```
