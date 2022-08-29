# Kafka Helm Sandbox
A kafka helm commands collection for local sanbox envs

## Get Started

Add repositories:

```shell
helm repo add confluentinc https://confluentinc.github.io/cp-helm-charts/
```

Update:

```shell
helm repo update
```

Intall charts:

```shell
helm install confluent confluentinc/cp-helm-charts -f confluent-values.yaml
```

Unistall

```shell
helm uninstall confluent
kubectl delete statefulset confluent-cp-kafka confluent-cp-zookeeper
kubectl delete pvc --selector=release=confluent
```

## Client

Run a client pod:

```shell
kubectl apply -f charts/kafka-client.yaml
kubectl exec -it kafka-client -- /bin/bash
```

Delete pod:

```shell
kubectl delete pod kafka-client
```

Control center:

```shell
kubectl port-forward service/confluent-cp-control-center 9021:9021
```

> Then open http://localhost:9021

## Kafka commands

Create a topic:

```shell
kafka-topics --create --bootstrap-server ${BOOTSTRAP_SERVERS} \
    --replication-factor 3 \
    --partitions 3 \
    --topic test
```

Delete a topic:

```shell
kafka-topics --delete --bootstrap-server ${BOOTSTRAP_SERVERS} \
    --topic test
```

List topics:

```shell
kafka-topics --bootstrap-server ${BOOTSTRAP_SERVERS} --list
```

List Groups:

```shell
kafka-consumer-groups --bootstrap-server ${BOOTSTRAP_SERVERS} --list
```

Delete group:

```shell
kafka-consumer-groups --bootstrap-server ${BOOTSTRAP_SERVERS} --delete --group test
```