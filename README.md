[![en](https://img.shields.io/badge/lang-en-ab4b52.svg)](https://github.com/tlebigre/henHouseRpiDeployment/blob/main/README.md)
[![fr](https://img.shields.io/badge/lang-fr-318ce7.svg)](https://github.com/tlebigre/henHouseRpiDeployment/blob/main/README.fr.md)

# Hen house delpoyment on raspberry pi
## Enable RTC
Enable i2c

## henHouseBoardBackendApi deployment

1. Install :
- FastAPI (see https://circus.readthedocs.io) 
```shell
pip install "fastapi[all]" 
```
- adafruit_ds3231 (see https://github.com/adafruit/Adafruit_CircuitPython_DS3231) 
```shell
pip install adafruit-circuitpython-ds3231 
```
- circus (see https://circus.readthedocs.io) 
```shell
pip install circus 
```

2. Code (in *home/pi/henHouse/henHouseBoardBackendApi*) :
- main.py (see https://github.com/tlebigre/henHouseBoardBackendApi)
- ***circus.ini***

3. Service (in */etc/systemd/system*) :
- ***henHouseBoardBackendApi.service***

4. Enable service :
```shell
sudo systemctl daemon-reload && sudo systemctl enable henHouseBoardBackendApi.service
```

## henHouseBackendApi deployment

1. Install java (min Java 17) 
2. Generate war file of henHouseBackendApi (see https://github.com/tlebigre/henHouseBackendApi) 
> :warning: ***You can generate war file outside raspberry pi (on your development environment)***

3. Install app server (like Tomcat)
4. Deploy war file on app server

### Service : example for tomcat
In my case Tomcat version is 10.1.5 in */opt/tomcat/apache-tomcat-10.1.5*

In */etc/systemd/system* :
- ***tomcat.service***

Enable service :
```shell
sudo systemctl daemon-reload && sudo systemctl enable tomcat.service
```

## henHouseFrontend deployment

1. Install NodeJs
2. Build (see /home/pi/henHouse/henHouseFrontend/)
> :warning: ***You can build app outside raspberry pi (on your development environment)***

3. Copy in */home/pi/henHouse/henHouseFrontend/* (from build folder) :
- build (folder)
- node_modules (folder)
- package.json (file)

3. Service (in */etc/systemd/system*) :
- ***henHouseFrontend.service***

4. Enable service :
```shell
sudo systemctl daemon-reload && sudo systemctl enable henHouseFrontend.service
```
