### Install Istio into cluster
```sh
$istioctl install --set profile=demo -y
```

### Install monitoring system
```sh
$export ISTIO_RELEASE_URL=https://raw.githubusercontent.com/istio/istio/release-1.11/
$kubectl apply -f $ISTIO_RELEASE_URL/samples/addons/jaeger.yaml
$kubectl apply -f $ISTIO_RELEASE_URL/samples/addons/prometheus.yaml
$kubectl apply -f $ISTIO_RELEASE_URL/samples/addons/grafana.yaml
$kubectl apply -f $ISTIO_RELEASE_URL/samples/addons/kiali.yaml
```

### Open monitoring dashboards
```sh
$istioctl dashboard kiali  
$istioctl dashboard jaeger

$istioctl dashboard grafana
$istioctl dashboard prometheus
```

## Deploy Book Info application
```sh
$istioctl kube-inject -f book-info.yaml | kubectl apply -f -
```

## port forwarding
```sh
$kubectl port-forward service/productpage 9080:9080
```

## Verify
http://localhost:9080/productpage?u=normal


## command to generate load
```sh
$hey -c 2 -z 200s http://localhost:9080/productpage 
```

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