## Instalación de Kali Linux

Arrancamos la máquina y seleccionamos "Graphical install"

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/f9978aa1-aba2-40f0-bd53-f8515126fb58)</kbd>

Seleccionamos el idioma, en nuestro caso "Spanish":

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/8af4f6b7-a8ec-47a9-a33c-90b7be5e5ac2)</kbd>

Seleccionamos la ubicación, es nuestro caso "España":

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/0d5610ed-0ec3-41ef-880f-e7376a454f3c)

Elejimos la configuración del taclado:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/1b85b14d-21b4-4bb9-83c2-3f9987bd6d04)</kbd>

Esperamos a que terminen las configuraciones y revisiones:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/7f1ee484-9132-4790-89af-33a37a6e55ad)</kbd>

Asignamos un nomnre de red (hostname) para nuestra máquina virtual:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/0a763732-6cac-4349-b102-3813c89579a2)</kbd>

Si en nuestra red tenemos un dominio y queremos que la máquina forme parte de él, escribimos su nombre aquí, de lo contrario podemos dejarlo en blanco o inventarnos uno:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/ebcc118e-3072-4bbd-9ca8-460e8cdea0d8)</kbd>

Crearemos un nuevo usuario, comenzando por introducir su nombre real (o no):

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/0e74d391-9ba0-4795-ba75-22f5363c9e6c)</kbd>

Continuando por su nombre de usuario elejido:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/96f589b7-0f76-49bf-a56d-2c46a0d25cd4)</kbd>

Y terminaremos creándole una contraseña a dicho usuario:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/367af236-1757-4386-bb84-dd0fd9f6e4f4)</kbd>

Configuraremos la zona horaria en la que nos encontremos:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/90eeec9b-4d2c-49fb-991b-7c52431cb0aa)</kbd>

Comenzará el particionado de discos:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/cc5248f9-68a7-411b-9c4b-a2743e8ed8e3)</kbd>

Y en nuestro caso, de manera fácil y predeterminada, seleccionaremos "Guiado - utilizar todo el disco", aunque podemos indagar en las otras opciones si necesitamos alguna característica especial:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/59e64e7d-4265-452b-9ad5-164e83914714)</kbd>

El siguiente paso es seleccionar el disco a particionar. Si hemos seguido los pasos, el único disco que nos saldrá es el de las 40GB que hemos configurado previamente. Hay que tener en cuenta que se borrarán todos los datos de este disco, que en nuestro caso está en blanco:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/bf532896-c1ca-4282-ab09-81a28c10f0e2)</kbd>

Seleccionamos "Todos los ficheros en una sola partición":

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/24f75573-d3fb-4716-8483-9a35a5fdddfb)</kbd>

Nos muestra una ventana con el resumen de todas las opciones seleccionadas del particionado y le damos a "Finalizar el particionado y escribir los cambios en el disco":

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/649c7095-6b54-46cb-ac87-01f16498fa6d)</kbd>

Y finalmente nos pide una confirmación más. Cambiamos a "SI", si estamos seguros:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/4e81e372-5c1d-411e-94d0-4112f87da786)</kbd>

Y ya, comeinza la instalación:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/f72b5d3f-b21b-416b-b837-557831b469cc)</kbd>

En la siguiente ventana nos pregunta por los programas que queremos instalar. Las opciones or defecto son suficientes, pero podemos elegir distintos entornos de escritorio (Xfce, GNOME; KDE, ...). Personalmente, ninguno termina de gustarme, pero prefiero Xfce de entre las opciones. También nos facilita la instalación automática de las aplicaciones más usadas:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/6050e7f7-cf30-45cb-aff8-5b3c180eca9b)</kbd>

Comienza la descarga de programas del repositorio de Kali. Si diese error, comprueba si tu salida a internet es a través de un firewall o proxy que analiza las descargas, ya que la descarga de alguna de las aplicaciones puede ser bloquedada por estos:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/b7f20c3f-7666-4366-89ab-71831ee8ad65)</kbd>

Cuando termina, nos pregunta si instalar el cargador de arranzuqe GRUB. Esto es el menú para seleccionar el sistema operativo que queremos que arranque y varias opciones de inicio de este propio Kali. Le decimos que "SI". Si en el mismo disco tuviéramos otro sistema operativo, un windows por ejemplo, en este menú podríamos selccionar si arrancar con KALI o con WINDOWS:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/5c7e50d2-84ae-48b3-ab38-36018a8bb302)</kbd>

Seleccoinamos nuestro disco, en este caso /dev/sda:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/8354d3bf-7b84-4b0e-b888-6fd0aff79b30)</kbd>

Durante todo el proceso, nos ha salido un banner en la parte inferior indicándonos que sería bueno instalar las VMware Tools para mejorar ciertas características. Al finalizar la instalación, el asistente las instala él mismo. Si nos diese algún problema, podríamos instalarlas a mano posteriormente:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/69cf65fa-b054-464f-886a-5f070f653c75)</kbd>

Llegados a este punto, la instalación ha terminado y nos pide hacer click en "Continuar" para reiniciar el equipo:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/9c335670-1bff-4301-8748-29678810d98a)</kbd>

La máquina ahora se reinicia, y después entra hasta la ventana de login de KALI. Escribimos los datos que hemos configurado anteriormente de usuario y contraseña:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/d31eb99a-16d4-49b3-8cd6-c8726ccfb2b8)</kbd>

Y ya tenemos nuestro KALI listo para trabajar:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/853846ea-230d-422b-866d-4e84cc6a9a4e)</kbd>

En el siguiente apartado recorreremos alguna mejoras y buenas prácticas a realizar sobre nuestro KALi antes de empezar a trabajar con él. Ver en el siguiente link:



