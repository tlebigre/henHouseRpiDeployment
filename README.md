# Hen house delpoyment on raspberry pi
## aaa
cam
rtc

## henHouseBoardBackendApi deployment

1. Install circus see https://circus.readthedocs.io/en/latest/installation

2. Code (in "home/pi/henHouse/henHouseBoardBackendApi") :
- main.py (see https://github.com/tlebigre/henHouseBoardBackendApi)
- circus.ini

3. Service (in "/etc/systemd/system") :
- ***henHouseBoardBackendApi.service***

4. Enable service :
```shell
sudo systemctl daemon-reload && sudo systemctl enable henHouseBoardBackendApi.service
```
