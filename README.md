# Domoticz
Projet GNU 2021

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

Booter la Raspberry Pi.
```` shell
$ modprobe i2c-dev
$ modprobe i2c-bcm2835
````


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