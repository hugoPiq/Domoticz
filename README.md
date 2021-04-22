# Domoticz
Projet GNU 2021
## CAPTEUR D'HUMIDITE
### Installation
* Effectuer le branchement suivant:
* 








## MACHINE HÔTE (PC DISTANT)

### Installer le serveur Domoticz sur la machine hôte:
```curl -sSL install.domoticz.com | sudo bash```
On suit les instructions du launcher
```
sudo chmod +x domoticz.sh
./domoticz.sh
``` 
Il se met en arrière plan.

### Lancer l'interface cliente Domoticz :
On lance un navigateur sur le localhost du client (machine hôte) sur le port Internet : ```127.0.0.1:8080``` pour l'interface client.
Créer une rubrique température sur Domotics en suivant les instructions 


### MACHINE CIBLE (RASPBERRY PI)

### Lancer le serveur Domoticz sur la Raspberry Pi (machine cible):
````
/opt/domoticz/domoticz -daemon -www 8080 -sslwww 443
````
Il tourne en arrière plan.
