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




