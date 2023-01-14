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

## Service Discovery

kubectl apply -f sd-example.yml

kubectl get all --namespace dev
kubectl get all --namespace prod

kubectl exec -it jump --namespace dev -- bash
cat /etc/resolv.conf
apt-get update && apt-get install curl -y
curl ent:8080
curl ent.prod.svc.cluster.local:8080

kubectl get deploy -n kube-system -l k8s-app=kube-dns
kubectl get pod -n kube-system -l k8s-app=kube-dns
kubectl logs coredns-95db45d46-6h8gv -n kube-system
kubectl get svc kube-dns -n kube-system
kubectl get endpointslice -n kube-system -l k8s-app=kube-dns
kubectl run -it dnsutils --image gcr.io/kubernetes-e2e-test-images/dnsutils:1.3
nslookup kubernetes

kubectl delete pod -n kube-system -l k8s-app=kube-dns

kubectl delete -f sd-example.yml


## Storage

kubectl get sc
kubectl describe sc premium-rwo

kubectl get pv
kubectl get pvc

kubectl apply -f pvc-gke-premium.yml
kubectl apply -f prempod.yml

kubectl delete pod volpod
kubectl delete pvc pvc-prem

kubectl apply -f sc-gke-fast-repl.yml
kubectl apply -f vol-app.yml

kubectl delete -f vol-app.yml
kubectl delete sc sc-fast-repl

kubectl get pv
kubectl delete pv ....
// then delete disk

## ConfigMaps

kubectl create configmap testmap1 --from-literal shortname=AOS --from-literal longname="Agents of Shield"