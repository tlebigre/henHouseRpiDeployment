[![en](https://img.shields.io/badge/lang-en-ab4b52.svg)](https://github.com/tlebigre/henHouseRpiDeployment/blob/main/README.md)
[![fr](https://img.shields.io/badge/lang-fr-318ce7.svg)](https://github.com/tlebigre/henHouseRpiDeployment/blob/main/README.fr.md)

# Deploiement du poulailler sur raspberry pi
## Activer l'horloge en temps réél
Activer i2c

## Déploiement de henHouseBoardBackendApi

1. Installer :
- adafruit_ds3231 (voir https://github.com/adafruit/Adafruit_CircuitPython_DS3231) 
```shell
pip install adafruit-circuitpython-ds3231 
```
- grpc (see https://grpc.io) 
```shell
pip install grpcio
```

2. Code (in *home/pi/henHouse/henHouseBoardBackendApi*) voir https://github.com/tlebigre/henHouseBoardBackendApi

3. Service (in */etc/systemd/system*) :
- ***henHouseBoardBackendApi.service***

4. Activer le service :
```shell
sudo systemctl daemon-reload && sudo systemctl enable henHouseBoardBackendApi.service
```

## Déploiement de henHouseBackendApi

1. Installer java (min Java 17) 
2. Générer le fichier war de henHouseBackendApi (voir https://github.com/tlebigre/henHouseBackendApi) 
> :warning: ***Vous pouvez générer le fichier war en dehors du raspberry pi (sur votre environnement de développement par exemple)***

3. Installer un serveur d'application (comme Tomcat)
4. Deployer le fichier war dessus

### Service : exemple pout Tomcat
Dans mon cas la version de Tomcat est 10.1.5 dans */opt/tomcat/apache-tomcat-10.1.5*

Dans */etc/systemd/system* :
- ***tomcat.service***

Activer le service :
```shell
sudo systemctl daemon-reload && sudo systemctl enable tomcat.service
```

## Déploiement de henHouseFrontend

1. Installer NodeJs
2. Construire (see https://github.com/tlebigre/henHouseFrontend#building)
> :warning: ***Vous pouvez construire l'application en dehors du raspberry pi (sur votre environnement de développement par exemple)***

3. Copier dans */home/pi/henHouse/henHouseFrontend/* (depuis le dossier de construction) :
- build (dossier)
- node_modules (dossier)
- package.json (fichier)

3. Service (in */etc/systemd/system*) :
- ***henHouseFrontend.service***

4. Activer le service :
```shell
sudo systemctl daemon-reload && sudo systemctl enable henHouseFrontend.service
```

