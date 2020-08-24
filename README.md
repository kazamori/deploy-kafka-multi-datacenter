# deploy-kafka-multi-datacenter

Test environment for kafka cluster in multi-datacenter

## How to use

Start all services in containers.

```bash
$ docker-compose up -d
```

Confirm all services are available.

```bash
$ docker-compose ps
       Name                    Command            State                          Ports
--------------------------------------------------------------------------------------------------------------
broker1-dc1           /etc/confluent/docker/run   Up      0.0.0.0:9091->9091/tcp, 9092/tcp
broker2-dc1           /etc/confluent/docker/run   Up      0.0.0.0:9092->9092/tcp
broker3-dc1           /etc/confluent/docker/run   Up      9092/tcp, 0.0.0.0:9093->9093/tcp
broker1-dc2           /etc/confluent/docker/run   Up      9092/tcp, 0.0.0.0:9094->9094/tcp
broker2-dc2           /etc/confluent/docker/run   Up      9092/tcp, 0.0.0.0:9095->9095/tcp
broker3-dc2           /etc/confluent/docker/run   Up      9092/tcp, 0.0.0.0:9096->9096/tcp
schema-registry-dc1   /etc/confluent/docker/run   Up      0.0.0.0:8081->8081/tcp
schema-registry-dc2   /etc/confluent/docker/run   Up      8081/tcp, 0.0.0.0:8082->8082/tcp
zookeeper-dc1         /etc/confluent/docker/run   Up      0.0.0.0:2181->2181/tcp, 2888/tcp, 3888/tcp
zookeeper-dc2         /etc/confluent/docker/run   Up      2181/tcp, 0.0.0.0:2182->2182/tcp, 2888/tcp, 3888/tcp
```

Stop all services.

```bash
$ docker-compose stop
```

Remove all containers.

```bash
$ docker-compose rm
```

Stop all sevices and remove containers, networks, images, and volumes.

```bash
$ docker-compose down
```

## How to mirror

```bash
$ kafka-mirror-maker.sh --consumer.config consumer.properties \
                        --producer.config producer.properties \
                        --whitelist EventCounterPerDayResults
```

## Reference

* https://github.com/confluentinc/examples
