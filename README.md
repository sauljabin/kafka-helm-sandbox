# Kafka Helm Sandbox

A kafka helm commands collection for local sandbox envs. This chart is base on https://github.com/confluentinc/cp-helm-charts.

## Get Started

Install charts:

```shell
helm upgrade --install kafka-sandbox kafka-sandbox/
```

Uninstall

```shell
helm uninstall kafka-sandbox
kubectl delete pvc --selector=release=kafka-sandbox
```

## Kafka commands

Create a topic:

```shell
kafka-topics --create --bootstrap-server localhost:31090 \
    --replication-factor 3 \
    --partitions 3 \
    --topic test
```

Delete a topic:

```shell
kafka-topics --delete --bootstrap-server localhost:31090 \
    --topic test
```

List topics:

```shell
kafka-topics --bootstrap-server localhost:31090 --list
```

List Groups:

```shell
kafka-consumer-groups --bootstrap-server localhost:31090 --list
```

Delete group:

```shell
<<<<<<< HEAD
kafka-consumer-groups --bootstrap-server ${BOOTSTRAP_SERVERS} --delete --group test
=======
kafka-consumer-groups --bootstrap-server localhost:31090 --delete --group test
```

## Workstation setup

Install pre-commit:

```shell
pre-commit install
>>>>>>> 938d500 (Add kafka and zookeeper charts)
```
