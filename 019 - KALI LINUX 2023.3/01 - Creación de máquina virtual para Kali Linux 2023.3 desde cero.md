## INSTALACIÓN DE KALI LINUX EN VMWARE

Lo primero de todo es descargar la ISO de instalación de la web oficial de Kali:

https://www.kali.org/

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/f2d1d971-cb38-49b9-9954-46e85d420066)</kbd>

Luego vamos a "Installer Images" (prefiero siempre hacer mi propia instalación desde cero antes que descargar una OVA, que es una máquina ya virtualizada completa, pero no controlo según qué opciones que ya trae configuradas por defecto)

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/0be22950-ac18-4811-8717-7d1f7de8e1c0)</kbd>

EN este caso descargaremos la versión para 64 bits y con descarga directa. Podemos descargar si nos interesa la de 32 bits o la versión ARM64 para Raspberry, o mediante torrent en vez de descarga directa.

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/652add30-fab6-4dd7-a815-86efcfe6fb99)</kbd>

Una vez descargado, en VMWARE, VirtualBox, Hyper-V, ESXi, ... crearemos la máquina virtual nueva:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/36f34907-0f81-4a8a-b6c9-df20144e7165)</kbd>

Seleccionamos como sistema de instalación la ISO descargada:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/30b7c440-5bc5-4546-bcc3-76482dccac91)</kbd>

Le decimos que es un sistema operativo tipo Linux:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/823e707a-49ad-47dc-b91b-bde108ba3173)</kbd>

Le asignamos un nombre a la máquina virtual y seleccionamos el lugar donde se guardarán sus ficheros:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/871d2157-4d79-4057-9333-fb75f5d45629)</kbd>

Especificamos el nº de procesadores y cores, en este caso 2 procesadores y 1 core por procesador:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/45adcbdd-53ea-4058-9260-7d6e0e94cd54)</kbd>

Le asignamos la memoria RAM deseada, en este caso nos recomienda 4GB:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/226390c4-499d-445f-9a5e-9372cb831f6f)</kbd>

El adaptador de red, lo dejaremos como NAT, para que la IP de la máquina sea compartida con el anfitrión, en vez de comportarse como una IP más de la red general, que sería BRIDGE:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/5154e9a1-0de3-4f3b-a5e8-2da57ac64d87)</kbd>

Los controladores I/O los dejamos como salen por defecto, en LSI Logic:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/ebf2cf4b-6d12-49d4-ab0e-87dd46081ceb)</kbd>

Y el tipo de disco virtual también, lo dejamos en SCSI:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/ea983132-83c5-4903-bbef-2bd7793ff09f)</kbd>

Creamos un disco virtual nuevo (podemos asignarle un disco virtual más tarde, pero lo hacemos ya):

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/9c1fe918-05b4-4734-a0c5-20e789a76926)</kbd>

A este disco le asignamos 40GB. El asistente nos recomienda 20GB, pero se queda algo escaso si vamos a almacenar alguna captura de paquete con wireshark  o descargar algún programa extra. NO marcamos la opción de "Allocate all disk space now", para que cree dicho disco nuevo, con un tope de 40GB pero usando el espacio real que necesite. Es un disco dinámico, que, conforme vaya creaciendo irá usando más espacio en disco. De la otra forma, ya nos asignaría un espacio de 40GB fijos aunque no se necesiten. También le dajamos marcada la opción de "Split virtual disk into multiple files", para que en vez de crearnos un fichero grande con el disco duro virtual de la máquina, nos lo vaya partiendo en varios ficheros más pequeños, para que sea más manejable:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/3c13fb79-2d6b-4e6d-8fa7-0132bca2f544)</kbd>

Pdemos asignar un nombre para estos múltiple ficheros del disco duro virtual, pero lo dejamos por defecto:

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/db70ffef-843b-4dd6-9b3b-b1993599057c)</kbd>

Al final del asistente nos sale un resumen con todas las opciones seleccionadas anteriormente. Hacemos click en "Finish":

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/5e9eb892-c514-405d-9362-11be630dd611)</kbd>

Ya podemos arrancar nuestra máquina virtual. Para ello la seleccionamos y le damos a "Start Up Guest":

<kbd>![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/4c15bb59-ff73-484c-a5ee-5b8c3e215d92)</kbd>

Siguiente paso -> arranque e instalación de Kali Linux en este enlace https://github.com/informaticaeloy/Manuales-And-HowTo/blob/3ef1709ee6827ca17cf537af025b2dcb5eac9d41/019%20-%20KALI%20LINUX%202023.3/02%20-%20Instalaci%C3%B3n%20de%20Kali%20Linux.md

