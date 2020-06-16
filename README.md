kubectl run bootcamp --image=docker.io/jocatalin/kubernetes-bootcamp:v1 --port=8080

kubectl apply -f deployment.yml

kubectl get deployments

-- con el uso de ingress no es necesario crear un servicio loadbalancer
-- kubectl expose deployment/bootcamp --type="LoadBalancer" --port 8080

-- se adjunta servicio e ingress yml para ser ejecutados con kubectl apply -f file.yml
kubectl get services

-- no es necesario esta parte dado que el ingress provee la ip externa
--export EXTERNAL_IP=$(kubectl get service bootcamp --output=jsonpath='{.status.loadBalancer.ingress[0].ip}')
--export PORT=$(kubectl get services --output=jsonpath='{.items[0].spec.ports[0].port}')
-- curl "$EXTERNAL_IP:$PORT"

minikube ip > ip

curl ip

Hello Kubernetes bootcamp! | Running on: bootcamp-390780338-2fhnk | v=1

--------------------------------------------- Fin
kubectl describe service bootcamp

Name: bootcamp
Namespace: default
Labels: run=bootcamp
Selector: run=bootcamp
Type: LoadBalancer
IP: 10.3.245.61
LoadBalancer Ingress: 104.155.111.170
Port: <unset> 8080/TCP
NodePort: <unset> 32452/TCP
Endpoints: 10.0.0.3:8080
... events and details left out ....

kubectl scale deployments/bootcamp --replicas=4

kubectl get deployments

kubectl delete deployment bootcamp

kubectl delete service bootcamp
