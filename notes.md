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

## Services

kubectl apply -f dual-stack-svc.yml
kubectl get svc
kubectl describe svc dual-stack-svc

kubectl apply -f deploy.yml
kubectl expose deployment svc-test --type=NodePort
kubectl get svc -o wide

kubectl delete svc svc-test

kubectl apply -f svc.yml

kubectl apply -f lb.yml

kubectl delete -f deploy.yml -f svc.yml -f lb.yml

## Ingress

kubectl get ing

https://github.com/kubernetes/ingress-nginx/releases
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/static/provider/cloud/deploy.yaml
kubectl get pods -n ingress-nginx -l app.kubernetes.io/name=ingress-nginx

kubectl get ingressclass
kubectl describe ingressclass nginx

kubectl apply -f app.yml
kubectl get pods

kubectl apply -f ig-all.yml
kubectl get ing
kubectl describe ing mcu-all

kubectl delete ingress mcu-all
kubectl delete -f app.yml