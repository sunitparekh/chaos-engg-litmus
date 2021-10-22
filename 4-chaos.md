### Install the Chaos Operator using plain vanilla YAML file
```sh
$kubectl apply -f https://litmuschaos.github.io/litmus/litmus-operator-v2.2.0.yaml
```

=======  NETWORK DELAY ==========

### Install the Chaos Experiment 
```sh
$kubectl apply -f https://hub.litmuschaos.io/api/chaos/2.2.0?file=charts/generic/pod-network-latency/experiment.yaml
```

### Setup service account
```sh
$kubectl apply -f https://hub.litmuschaos.io/api/chaos/2.2.0?file=charts/generic/pod-network-latency/rbac.yaml
```

### apply delay
```sh
$kubectl apply -f network-delay-engine.yaml
```

======= NETWORK CORRUPTION =========

### Install the Chaos Experiment 
```sh
$kubectl apply -f https://hub.litmuschaos.io/api/chaos/2.1.0?file=charts/generic/pod-network-corruption/experiment.yaml
```

### Setup service account
```sh
$kubectl apply -f https://hub.litmuschaos.io/api/chaos/2.1.0?file=charts/generic/pod-network-corruption/rbac.yaml
```

### apply network corruption
```sh
$kubectl apply -f network-corrpution-engine.yaml
```