

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


-------

# KUBERNETES - HOLA MUNDO

Un práctico proyecto para entender muy rápidamente kubernetes. 

## Getting Started

Antes de comenzar creando nuestro primer pod con una imagen en nodeJS que desplegara nuestro Hola mundo en kubernetes. Commo muchos en el tema saben es tener corriendo el kubernetes en el namespace default. 

```
minikube start
```

Ahora si bien, construyamos nuestro pod con una imagen de una aplicacion en nuestro dockerhub. Kubectl es el comando para ejecutar operaciones docker.

```
kubectl run bootcamp --image=docker.io/jocatalin/kubernetes-bootcamp:v1 --port=8080
```

Con lo anterior revisamos la lista de despliegues

```
kubectl apply -f deployment.yml
```

Cersiorate de ver algo como esto

```
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
bootcamp   1/1     1            1           3h23m
```


### Estructura de Archivos

En el siguiente esquema se declara la lista de archivos que contiene este simple proyecto.

```
.
├── README.md
├── deployment.yml
├── ingress.yml
└── servicioBootcamp.yml
```

### Installing

A step by step series of examples that tell you how to get a development env running

Say what the step will be

```
Give the example
```

And repeat

```
until finished
```

End with an example of getting some data out of the system or using it for a little demo

## Running the tests

Explain how to run the automated tests for this system

### Break down into end to end tests

Explain what these tests test and why

```
Give an example
```

### And coding style tests

Explain what these tests test and why

```
Give an example
```

## Deployment

Add additional notes about how to deploy this on a live system

## Built With

- [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
- [Maven](https://maven.apache.org/) - Dependency Management
- [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags).

## Authors

- **Billie Thompson** - _Initial work_ - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

- Hat tip to anyone whose code was used
- Inspiration
- etc



