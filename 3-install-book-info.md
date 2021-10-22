
## Deploy Book Info application
istioctl kube-inject -f book-info.yaml | kubectl apply -f -

## port forwarding
kubectl port-forward service/productpage 9080:9080

## Verify
http://localhost:9080/productpage?u=normal
