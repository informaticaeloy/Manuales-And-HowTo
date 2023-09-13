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

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/3551e030-c144-4574-8c12-c78367fb175a)</kbd>

10. Ahora, si hacemos doble click en cualquier fichero, procede a descargarlo y luego lo abre con el programa asociado. Posteriormente vuelve a quedar en modo ‘local + cloud’

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/6bd3e571-f522-4ea2-aa19-7d7382be94d6)</kbd>

11. Podríamos guardar este comando en un fichero CMD y ejecutarlo cada 5 minutos con una tarea programada:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/f7eb5866-ebed-481d-9dc1-2c942e7c4597)</kbd>

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/3e0b3ead-4ee9-46a3-bb8e-f5a042224553)</kbd>

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/5719907f-3903-45a8-a63b-d909f40f1024)</kbd>

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/dd11da61-ea04-4855-be26-78253373b3b2)</kbd>

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/b09b5253-f211-4f2c-9488-16ceda834971)</kbd>

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/bc5b9b2e-f8b5-40d1-bb8f-e6a48fe7dacb)</kbd>

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/87d2b4fa-10d9-43da-a8d7-eded60a05237)</kbd>

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/866ecab0-4f3a-461b-85d1-d38b66508c89)</kbd>

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/ed126926-f675-483a-822d-7d12d992c001)</kbd>

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/712c032c-ea0b-4d6d-910b-79133e4095de)</kbd>

12. Y de esta forma podemos tener una carpeta local, almacenada en ONE DRIVE, y disponer de los datos bajo demanda, descargándolos de internet sólo cuando los necesitemos, sin ocuparnos espacio en disco local. Todo dependerá de la cuota de espacio que tengamos en ONE DRIVE. En este ejemplo, se ha usado una cuenta FREE de Microsoft (5GB) y se ha sincronizado con una partición local de 1GB para comprobar que funcionaba correctamente:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/2f0f3a30-a5c8-40d1-ab24-880555971d90)</kbd>

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/a020093f-977a-479a-bf15-ab14c20b5007)</kbd>

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/cf51a7f8-a1d3-4b39-b116-96ce8c0eed03)</kbd>
