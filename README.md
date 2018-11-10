![Beta](https://img.shields.io/badge/status-beta-yellowgreen.svg?style=flat "Beta")
![Community](https://img.shields.io/badge/support-community-blue.svg?style=flat "Community")

# SURF-input-jti

Standalone container running fluentd and Juniper Telemetry plugin.  

This container has been designed to work with the project OpenNTI but it has ben (shamelessly) ripped from the open-nti project.
Multiple types of outputs are supported and can be defined at launch time:
- Influxdb (default)
- Kafka
- Stdout

This container can run in standalone mode or it can you can run multiple behind a load-balancer using docker-compose.
A docker-compose configuration file is (not yet) provided.

## Environment variables

So parameters can be overwritten using environment variables define at launch time.   
Here is the list of variables available with their default value.

```yaml
OUTPUT_KAFKA: false
OUTPUT_INFLUXDB: true
OUTPUT_STDOUT: false

## Ports Numbers for Juniper Telemetry Input Plugins
PORT_JTI: 50000
PORT_ANALYTICSD: 50020

## Information for Influxdb Output plugin
INFLUXDB_ADDR: localhost
INFLUXDB_PORT: 8086
INFLUXDB_DB: juniper
INFLUXDB_USER: juniper
INFLUXDB_PWD: juniper

## Information for Kafka
KAFKA_ADDR: localhost
KAFKA_PORT: 9092
```

Here is an example to build this container and define an environment variable
```
docker build -t surf-input-jti https://github.com/makzdot/SURF-input-jti.git
docker run -d -e INFLUXDB_ADDR='influxhost.example.com' surf-input-jti
```
