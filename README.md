# Kafka Helm Sandbox

A kafka helm commands collection for local sandbox envs. This chart is base on https://github.com/confluentinc/cp-helm-charts.

## Get Started

Install charts:

```shell
helm install sandbox-cluster kafka-sandbox/
```

Upgrade charts:

```shell
helm upgrade --install sandbox-cluster kafka-sandbox/
```

Uninstall

```shell
helm uninstall sandbox-cluster
kubectl delete pvc --selector=release=sandbox-cluster
```

## Ports

- kafka `localhost:30090,localhost:30091,localhost:30092`
- schema registry http://localhost:30081

## Kafka commands

Create a topic:

```shell
kafka-topics --create --bootstrap-server localhost:30090 \
    --replication-factor 3 \
    --partitions 3 \
    --topic test
```

Delete a topic:

```shell
kafka-topics --delete --bootstrap-server localhost:30090 \
    --topic test
```

List topics:

```shell
kafka-topics --bootstrap-server localhost:30090 --list
```

List Groups:

```shell
kafka-consumer-groups --bootstrap-server localhost:30090 --list
```

Delete group:

```shell
kafka-consumer-groups --bootstrap-server localhost:30090 --delete --group test
```

## Workstation setup

Install pre-commit:

```shell
pre-commit install
```
