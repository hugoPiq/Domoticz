# DOMOTICZ CAPTEUR D'HUMIDITE

#### Date: Avril 2021
#### Auteurs
* **Estelle Arricau** _alias_ [@estellearrc](https://github.com/estellearrc)
* **Hugo Piquard** _alias_ [@hugoPiq](https://github.com/hugoPiq)
#### Nous sommes en stage dès le 26 avril.
Projet GNU 2021



## CAPTEUR D'HUMIDITE
### Installation
* Booter la Raspberry Pi avec l'image *sdcard.img* dessus ainsi que les modifications apportées dans le *config.txt* pour permettre la communication I2C.
* Taper les commandes suivantes pour activer l'I2C :

```` shell
$ modprobe i2c-dev
$ modprobe i2c-bcm2835
````

* Déplacer le binaire ```/bin/domo``` qui est à la racine du dépôt **Domoticz** dans le dossier ```/etc/init.d/``` de la Raspberry.
* Effectuer le branchement suivant:

![alt text](https://github.com/hugoPiq/Domoticz/blob/main/img/176168470_506479097198002_6097645515706769262_n.jpg)

*Remarque*: Bien mettre les câbles d'alimentation des diodes sur les GPI05 et GPIO6. Concernant le capteur, VCC sur PIN2, SCL sur GPIO3, SDA sur GPIO2 et connecter le GROUND. 

* Allumer la Raspberry en branchant cette dernière sur le secteur. Si une des deux LED est allumée, la Raspberry est bien en fonctionnement.

![alt text](https://github.com/hugoPiq/Domoticz/blob/main/img/ImagePinSwitchON.jpg)

De plus, les données de température, pression et humidité s'affichent dans le terminal :
````
24.09 deg C, 1009.64 hPa, 39.91%
24.10 deg C, 1009.64 hPa, 39.91%
24.10 deg C, 1009.64 hPa, 39.88%
24.11 deg C, 1009.64 hPa, 39.91%
24.12 deg C, 1009.63 hPa, 39.88%
24.12 deg C, 1009.64 hPa, 39.90%
24.13 deg C, 1009.64 hPa, 39.87%
24.14 deg C, 1009.64 hPa, 39.88%
24.14 deg C, 1009.64 hPa, 39.88%
24.14 deg C, 1009.63 hPa, 39.87%
24.15 deg C, 1009.64 hPa, 39.88%
24.15 deg C, 1009.64 hPa, 39.86%
24.16 deg C, 1009.64 hPa, 39.86%
24.16 deg C, 1009.64 hPa, 39.86%
24.17 deg C, 1009.64 hPa, 39.85%
24.17 deg C, 1009.63 hPa, 39.84%
24.17 deg C, 1009.64 hPa, 39.86%
24.18 deg C, 1009.64 hPa, 39.85%
24.18 deg C, 1009.63 hPa, 39.84%
24.18 deg C, 1009.64 hPa, 39.85%
24.19 deg C, 1009.63 hPa, 39.84%
````

### Utilisation
* Si l'humidité est supérieur à 80% , la LED rouge clignote.
* Sinon la LED verte clignote.
Pour arrêter le programme, appuyer sur ```Ctrl+C``` (le signal est rattrapé). Les GPIO utilisés pour les leds seront *unexported* de façon à ce que le programme **domo** puisse être relancé sans que les pin restent *busy*.

## Détails
Au démérage, le binaire ```/etc/init.d/domo``` est lancé.
Ce dernier reçoit les données du capteur de pression/humidité et change la couleur de la LED en fonction.

### SERVEUR DOMOTICZ

### Machine hôte (UBUNTU)
#### Lancer l'interface cliente Domoticz :
Lancer un navigateur sur le localhost du client (machine hôte) sur le port Internet : ```172.20.11.251:8080```.
Créer une rubrique température sur Domotics en suivant les instructions suivantes:
Pour créer un capteur virtuel, aller dans l'onglet Setup puis dans le menu Hardware. Créer alors un capteur virtuel en indiquant un nom et le type Dummy:

![alt text]https://github.com/pblottiere/embsys/blob/master/labs/rpi3/imgs/domoticz_dummy.png

Finalement, cliquer sur Create Virtual Sensors et indiquer Temperature comme type:

![alt text]https://github.com/pblottiere/embsys/blob/master/labs/rpi3/imgs/domoticz_virtual.png

Le nouveau capteur est alors disponible dans l'onglet Temperature de l'interface:

![alt text]https://github.com/pblottiere/embsys/blob/master/labs/rpi3/imgs/domoticz_temp0.png

##### Remarque: pour installer le serveur Domoticz sur la machine hôte en local:
```curl -sSL install.domoticz.com | sudo bash```
Suivre les instructions du launcher.
```
sudo chmod +x domoticz.sh
./domoticz.sh
``` 
Il se met en arrière plan.
Lancer un navigateur sur le localhost ```172.0.0.0:8080```.


#### MACHINE CIBLE (RASPBERRY PI)
Le serveur se lance automatiquement sur la Rasberry. Mais nous n'avons configué le serveur (mauvais IP: 0.0.0.0).
##### Remarque: pour lancer le serveur Domoticz sur la Raspberry Pi (machine cible) avec la bonne adresse IP:
````
/opt/domoticz/domoticz -daemon -www 8080 -sslwww 443
````
Il tourne en arrière plan.

Nous n'avons pas eu le temps de faire le script de commande curl pour envoyer les données du capteur sur le serveur Domoticz.
