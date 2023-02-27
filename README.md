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
3. Install app server (like Tomcat)
4. Deploy war file on app server

### Service : example for tomcat
In */etc/systemd/system* :
- ***tomcat.service***

Enable service :
```shell
sudo systemctl daemon-reload && sudo systemctl enable tomcat.service
```
