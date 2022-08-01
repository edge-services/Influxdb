# Influxdb service for Time Series data at the Edge Device


## Register InfluxDB Service with IBM Edge Application Manager

    - Make sure IEAM Agent is installed and can access IEAM Hub
    - Go inside "horizon" folder
    - Make sure deployment.policy.json has correct values
    - run following commands (CLI for openhorsizon)

```

export HZN_ORG_ID=myorg
export HZN_EXCHANGE_USER_AUTH=admin:HjWsfSKGB9XY3XhLQPOmqpJ6eLWN3U

export ARCH=arm64
eval $(hzn util configconv -f hzn.json) 

$hzn exchange service publish -f service.definition.json -P 
<!-- $hzn exchange service list -->
<!-- $hzn exchange service remove ${HZN_ORG_ID}/${SERVICE_NAME}_${SERVICE_VERSION}_${ARCH} -->

$hzn exchange service addpolicy -f service.policy.json ${HZN_ORG_ID}/${SERVICE_NAME}_${SERVICE_VERSION}_${ARCH}
<!-- $hzn exchange service listpolicy ${HZN_ORG_ID}/${SERVICE_NAME}_${SERVICE_VERSION}_${ARCH} -->
<!-- $hzn exchange service removepolicy ${HZN_ORG_ID}/${SERVICE_NAME}_${SERVICE_VERSION}_${ARCH} -->

$hzn exchange deployment addpolicy -f deployment.policy.json ${HZN_ORG_ID}/policy-${SERVICE_NAME}_${SERVICE_VERSION}
<!-- $hzn exchange deployment listpolicy ${HZN_ORG_ID}/policy-${SERVICE_NAME}_${SERVICE_VERSION} -->
<!-- $hzn exchange deployment removepolicy ${HZN_ORG_ID}/policy-${SERVICE_NAME}_${SERVICE_VERSION} -->

```
## InfluxDB 2.0 Docker (Standalone - for testing)

- Run docker image for running InfluxDB 2.0 container

```

docker run -d -p 8086:8086 \
      --name influxdb2 \
      -v $PWD/data:/var/lib/influxdb2 \
      -v $PWD/config:/etc/influxdb2 \
      -e DOCKER_INFLUXDB_INIT_MODE=setup \
      -e DOCKER_INFLUXDB_INIT_USERNAME=sinny777 \
      -e DOCKER_INFLUXDB_INIT_PASSWORD=1SatnamW \
      -e DOCKER_INFLUXDB_INIT_ORG=IBM \
      -e DOCKER_INFLUXDB_INIT_BUCKET=smartthings \
      -e DOCKER_INFLUXDB_INIT_RETENTION=30d \
      -e DOCKER_INFLUXDB_INIT_ADMIN_TOKEN=SatnamWaheguruJi1 \
      influxdb:2.0


docker run -p 8086:8086 \
      --name influxdb \
      -v $PWD/data:/var/lib/influxdb \
      -v $PWD/influxdb.conf:/etc/influxdb/influxdb.conf:ro \
      influxdb:1.8.10 -config /etc/influxdb/influxdb.conf
    
```

## Refrences

- [Edge Computing](https://github.com/sinny777/edge-computing)
- [Rule Engine](https://github.com/cachecontrol/json-rules-engine)


