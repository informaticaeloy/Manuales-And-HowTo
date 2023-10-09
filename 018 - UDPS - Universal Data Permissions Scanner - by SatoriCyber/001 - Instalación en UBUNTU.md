## sadfasd
### dsfadfads

#### Requisitos inciales

Partimos de una máquina virtual Ubuntu con 20Gb y 4 de RAM

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/35cea666-14af-417f-8eff-36981bb42c1d)

```shell
sudo apt update

sudo apt upgrade
```

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/a1228b68-108b-457a-a378-6cab6193e139)


#### 1. Instalamos UDPS

Si no tenemos pip instalado en el equipo, lo hacemos con el siguiente comando:

```shell
sudo apt install pip
```

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/10d5550f-6423-4c53-bb94-fcac42e491af)

Cuando tengamos pip instalado, ejecutamos el siguiente comando:

```shell
sudo pip install udsp
```

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/7d420632-638b-4d5b-b114-e713cb337efa)

Si nos da error alguna de las dependencias, como por ejemplo esta:

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/11a9db83-00c9-4690-bcce-0c19dc793ff5)

Podemos instalarlo manualmente:

```shell
pip install psycopg2-binary
```

![image](https://github.com/informaticaeloy/Manuales-And-HowTo/assets/20743678/d51ec0d1-8bdf-4f6f-88ab-677d2cbc6230)

