# Управление трафиком внутри кластера

```
minikube start --cni=calico

# проверка, что всё запустилось (статус Running)
kubectl get pods -n kube-system | Select-String calico

kubectl run front-end-app --image=nginx --labels role=front-end --expose --port 80
kubectl run back-end-api-app --image=nginx --labels role=back-end-api --expose --port 80
kubectl run admin-front-end-app --image=nginx --labels role=admin-front-end --expose --port 80
kubectl run admin-back-end-api-app --image=nginx --labels role=admin-back-end-api --expose --port 80

kubectl apply -f network-policies.yaml
```