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

## Deployments

kubectl apply -f deploy.yml
kubectl get deploy hello-deploy
kubectl describe deploy hello-deploy

kubectl apply -f svc.yml

kubectl get rs
kubectl scale deploy hello-deploy --replicas 5

kubectl apply -f deploy_v2.yml
kubectl rollout status deployment hello-deploy

kubectl rollout pause deployment hello-deploy 
kubectl describe deploy hello-deploy
kubectl rollout resume deployment hello-deploy 

kubectl rollout history deployment hello-deploy

kubectl rollout undo deployment hello-deploy --to-revision=1

kubectl delete -f deploy.yml
kubectl delete -f svc.yml



