### Install the Chaos Operator using plain vanilla YAML file
```sh
kubectl create ns litmus
helm install chaos litmuschaos/litmus --namespace=litmus

kubectl port-forward service/chaos-litmus-frontend-service 9091:9091 -n litmus
# admin / litmus                 ----- admin123
```

=======  NETWORK DELAY ==========

### Install the Chaos Experiment 
```sh
kubectl apply -f https://hub.litmuschaos.io/api/chaos/2.12.0?file=charts/generic/pod-network-latency/experiment.yaml
```

### Setup service account
```sh
kubectl apply -f https://hub.litmuschaos.io/api/chaos/2.12.0?file=charts/generic/pod-network-latency/rbac.yaml
```

### apply delay
```sh
kubectl apply -f network-delay-engine.yaml
```
