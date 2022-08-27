
## Deploy Book Info application
```sh
istioctl kube-inject -f book-info.yaml | kubectl apply -f -
```

## port forwarding
```sh
kubectl port-forward service/productpage 9080:9080
```

## Verify
http://localhost:9080/productpage?u=normal


## command to generate load
```sh
hey -c 2 -z 200s http://localhost:9080/productpage 
```