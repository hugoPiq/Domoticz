# DOMOTICZ CAPTEUR D'HUMIDITE

#### Date: Avril 2021
#### Auteurs
* **Estelle Arricau** _alias_ [@estellearrc](https://github.com/estellearrc)
* **Hugo Piquard** _alias_ [@hugoPiq](https://github.com/hugoPiq)
#### Nous sommes en stage dès le 26 avril.
Projet GNU 2021

## CAPTEUR D'HUMIDITE
### Installation
* Effectuer le branchement suivant:

![alt text](https://github.com/hugoPiq/Domoticz/blob/main/176168470_506479097198002_6097645515706769262_n.jpg)

* Allumer la Raspberry en branchant cette dernière sur le secteur. Si une des deux LED est allumée, la Raspberry est bien en fonctionnement
### Utilisation
* Si l'humidité est supérieur à 80% , la LED rouge clignote.
* Sinon la LED verte clignote.

## Détails
Au démérage, le binaire ```/etc/init.d/XXXXXX``` est lancée.
Ce dernier reçoit les données du capteur de pression/humidité et change la couleur de la LED en fonction.






### SERVEUR DOMOTICZ

## Machine hôte (UBUNTU)
### Lancer l'interface cliente Domoticz :
On lance un navigateur sur le localhost du client (machine hôte) sur le port Internet : ```172.20.11.251:8080``` pour l'interface client.
Créer une rubrique température sur Domotics en suivant les instructions 

#### Remarque: pour installer le serveur Domoticz sur la machine hôte en local:
```curl -sSL install.domoticz.com | sudo bash```
On suit les instructions du launcher
```
sudo chmod +x domoticz.sh
./domoticz.sh
``` 
Il se met en arrière plan.
Lancer un navigateur sur le localhost ```172.0.0.0:8080```.


### MACHINE CIBLE (RASPBERRY PI)
Le serveur se lance automatiquement sur la Rasberry. Mais nous n'avons configué le serveur (mauvais IP: 0.0.0.0).
#### Remarque: pour lancer le serveur Domoticz sur la Raspberry Pi (machine cible) avec la bonne adresse IP:
````
/opt/domoticz/domoticz -daemon -www 8080 -sslwww 443
````
Il tourne en arrière plan.

Nous n'avons pas eu le temps de faire le script de commande curl pour envoyer les données du capteur sur le serveur Domoticz.
