# Docker-compose files for a simple uptodate
# Home Assistant
# + ZWaveJS
# + InfluxDB
# + Grafana

Home Assistant is an open source tool for home automation.

Sensor data (temperature, item status, power usage, etc...) is stored in Home Assistant for a short time but will be send to InfluxDB for the long term. Grafana is used to observe and monitor this sensor data.

This setup runs on a Synology 220+ with Docker and Docker Compose.

## Hardware

* Synology 220+
* Z-Wave USB Stick (ZMEEUZB1) by Z-Wave.ME
* Qubino ZMNHID1 Flush on/Off Thermostat
* Eurotronics Spirit Thermostatic Valve
* ThermoFloor Floor thermostat
* Philps Hue Bridge
* Philps Hue Dimmer switch
* Philps Hue White ambiance 3x
* Philps Hue White 2x

## Install on Synology NAS

Docker

USB drivers for Zwave stick and P1 cable (UsbSerialDrivers DSM)

http://www.jadahl.com/drivers_6.2/

## Install (only once):

```
git clone https://github.com/earlhickey/home-assistant.git
cd home-assistant
```

## Update settings (only once):

Grafana user 742 needs access to data folder
```
chown 472:472 ./grafana
```

Copy and adjust secrets file
```
cp hass/secrets_example.yaml hass/secrets.yaml
vi hass/secrets.yaml
```

## Run your stack:

```
docker-compose up -d

```

## Show me the logs:

```
docker-compose logs
```

## Stop it:

```
docker-compose stop
docker-compose rm
```

## Login into running docker machine
```
docker exec -it influxdb /bin/bash
```

## Handy commands

```
# home assistant dir on NAS
cd /volume1/docker/home-assistant/
# list containers
docker-compose ps
```

## Url's:

Home Assistant
http://home.assistant:8123/

Grafana (admin/admin)
http://home.assistant:3000/

ZWaveJS2MQTT
http://home.assistant:8091/
