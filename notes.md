## pods

kubectl exec hello-pod -- ps aux

kubectl apply -f sidecar-local.yml

http://localhost:30001
kubectl delete service git-sync   
kubectl delete service git-sync   

## Namespaces

kubectl api-resources
kubectl get namespaces
kubectl describe ns default
kubectl get svc --namespace kube-system

kubectl create ns hydra
kubectl apply -f shield-ns.yml
kubectl delete ns hydra

kubectl config set-context --current --namespace shield

kubectl apply -f shield-app.yml

http://localhost:31112/


kubectl delete -f shield-app.yml
kubeclt delete ns shield
