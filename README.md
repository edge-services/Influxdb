
## InfluxDB for Time Series data at the Edge Device

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

