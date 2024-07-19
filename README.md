Nome: Derek Christopher Dos Santos

AMBIENTE DO MINIKUBE: Minikube v1.33.1 on Windows 11 (x64) Docker container (CPUs=2, Memory=2200MB)
VERSÃO DO DOCKER Client: Docker Engine - Community Version: 26.1.0 API version: 1.45 Go version: go1.21.9 Git commit: 9714adc Built: Mon Apr 22 17:06:41 2024 OS/Arch: linux/amd64 Context: default

2 Deployments (Nginx e Apache); 1 Configmap; 1 Secret; 1 Namespace; 1 Service.

Comandos usados:
kubectl get pods -n k8s-prd -o wide kubectl get svc -n k8s-prd kubectl get deployments -n k8s-prd kubectl get ns
kubectl get cm -n k8s-prd 
kubectl get secret -n
k8s-prd kubectl describe cm -n
k8s-prd configmap-k8s
kubectl describe secret -n
k8s-prd secret-k8s kubectl exec -it -n
k8s-prd deploy-apache-k8s-6b5958bf88-8l4mq -- env | grep -i DATABASE
kubectl exec -it -n k8s-prd deploy-nginx-k8s-8558fbddb8-cprp9 -- env | grep -i DATABASE



