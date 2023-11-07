## Instalación de Kali Linux

Arrancamos la máquina y seleccionamos "Graphical install"

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/f9978aa1-aba2-40f0-bd53-f8515126fb58)</kbd>

Seleccionamos el idioma, en nuestro caso "Spanish":

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/8af4f6b7-a8ec-47a9-a33c-90b7be5e5ac2)</kbd>

Seleccionamos la ubicación, es nuestro caso "España":

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/0d5610ed-0ec3-41ef-880f-e7376a454f3c)

Elejimos la configuración del taclado:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/1b85b14d-21b4-4bb9-83c2-3f9987bd6d04)</kbd>

Esperamos a que terminen las configuraciones y revisiones:

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/7f1ee484-9132-4790-89af-33a37a6e55ad)

Asignamos un nomnre de red (hostname) para nuestra máquina virtual:

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/0a763732-6cac-4349-b102-3813c89579a2)

Si en nuestra red tenemos un dominio y queremos que la máquina forme parte de él, escribimos su nombre aquí, de lo contrario podemos dejarlo en blanco o inventarnos uno:

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/ebcc118e-3072-4bbd-9ca8-460e8cdea0d8)

Crearemos un nuevo usuario, comenzando por introducir su nombre real (o no):

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/0e74d391-9ba0-4795-ba75-22f5363c9e6c)

Continuando por su nombre de usuario elejido:

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/96f589b7-0f76-49bf-a56d-2c46a0d25cd4)

Y terminaremos creándole una contraseña a dicho usuario:

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/367af236-1757-4386-bb84-dd0fd9f6e4f4)

Configuraremos la zona horaria en la que nos encontremos:

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/90eeec9b-4d2c-49fb-991b-7c52431cb0aa)

Comenzará el particionado de discos:

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/cc5248f9-68a7-411b-9c4b-a2743e8ed8e3)

Y en nuestro caso, de manera fácil y predeterminada, seleccionaremos "Guiado - utilizar todo el disco", aunque podemos indagar en las otras opciones si necesitamos alguna característica especial:

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/59e64e7d-4265-452b-9ad5-164e83914714)

El siguiente paso es seleccionar el disco a particionar. Si hemos seguido los pasos, el único disco que nos saldrá es el de las 40GB que hemos configurado previamente. Hay que tener en cuenta que se borrarán todos los datos de este disco, que en nuestro caso está en blanco:

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/bf532896-c1ca-4282-ab09-81a28c10f0e2)

Seleccionamos "Todos los ficheros en una sola partición":

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/24f75573-d3fb-4716-8483-9a35a5fdddfb)



Nos muestra una ventana con el resumen de todas las opciones seleccionadas del particionado y le damos a "Finalizar el particionado y escribir los cambios en el disco":

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/649c7095-6b54-46cb-ac87-01f16498fa6d)


<kbd></kbd>
```shell
attrib -p +u /s
```
