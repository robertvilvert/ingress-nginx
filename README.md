# Kubernetes ingress-controller and default-backend

## Install

#### required for all cloud platforms

```
kubectl apply -f ./deploy/namespace.yaml
kubectl apply -f ./deploy/custom-backend.yaml
kubectl apply -f ./deploy/configmap.yaml
kubectl apply -f ./deploy/tcp-services-configmap.yaml
kubectl apply -f ./deploy/udp-services-configmap.yaml
kubectl apply -f ./deploy/rbac.yaml
kubectl apply -f ./deploy/with-rbac.yaml
```

#### GKE
```
kubectl patch deployment -n ingress-nginx nginx-ingress-controller --type='json' \
  --patch="$(cat ./deploy/publish-service-patch.yaml)"
kubectl apply -f ./deploy/service.yaml  
kubectl apply -f ./deploy/patch-service-with-rbac.yaml
```

#### Monitoring
Require prometheus installed [project here](https://github.com/camilb/prometheus-kubernetes)

```
kubectl apply -f ./deploy/monitoring.yaml
```
