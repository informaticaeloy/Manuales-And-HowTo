## Uso de ONE DRIVE para que sólo almacene datos en el CLOUD

La idea es hacer que ONE DRIVE funcione exclusivamente en modo CLOUD, sin hacer uso de almacenamiento local.

Existe la posibilidad de usar el "Sensor de almacenamiento" de Windows 10 y 11, pero nos hemos encontrado con que o hay que lanzarlo manualmente, o esperar a que se cumplan unas condiciones, como son ejecutarlo diariamente, semanalmente, mensualmente o cuando haya poco espacio en disco.

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/a3329afe-20c7-4e71-b427-2ef8acf78dce)</kbd>

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/86434499-a08d-409f-a4bd-7c390bb01116)</kbd>

En un entorno en el que se generen muchos documentos, necesitamos hacer que esta tarea se ejecute por ejemplo cada 5 minutos. Para ello, procedemos de la siguiente forma:

1. Instalamos ONE DRIVE versión escritorio
2. Vinculamos ONE DRIVE con nuestra cuenta
3. Por defecto nos crea la carpeta 'c:\users\usuario\OneDrive'
4. Desvinculamos la cuenta de ONE DRIVE
5. Desinstalamos ONE DRIVE y lo volvemos a instalar. Al hacerlo, detecta que ya hay una carpeta de sincronización anterior, y al vincular de nuevo la cuenta, nos deja elejir la carpeta donde queremos guardar nuestra fotos, por ejemplo "e:\almacen\fotos one drive"

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/143c2cce-56b1-4a54-a622-35af0c1a910b)</kbd>

6. Cuando copiamos ficheros a esta carpeta, nos marca todos los ficheros como “local” y “cloud”

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/eccf5c6e-447d-4967-9206-1cf6cb0cf485)</kbd>

7. En este punto podríamos esperar a que actúe el sensor de almacenamiento de Windows, que deja sólo una copia en la nube si se llena el disco duro o si no se abre un fichero en x días, pero para forzarlo, ejecutamos el siguiente comando.
8. Abrimos un CMD y ejecutamos en la ruta deseada (en este caso todo e: ) el comando :

```shell
attrib -p +u /s
```

9.	Vemos que cambia el icono de los ficheros a “sincronizando”, y una vez terminado los ha dejado sólo en el cloud:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/d5ccc5b5-eed5-4ed3-a547-b2c02e933424)</kbd>






