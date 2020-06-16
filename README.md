



kubectl scale deployments/bootcamp --replicas=4

kubectl get deployments

kubectl delete deployment bootcamp

kubectl delete service bootcamp


-------

# KUBERNETES - HOLA MUNDO

Un práctico proyecto para entender muy rápidamente kubernetes. 

## Getting Started

Antes de comenzar creando nuestro primer pod con una imagen en nodeJS que desplegara nuestro Hola mundo en kubernetes. Como muchos en el tema ya saben, hay que verificar que el minikube este corriendo en el namespace default. 

Para apuntar nuestro minikube al namespace default 




```
minikube start
```

Ahora si bien, construyamos nuestro pod con una imagen de una aplicacion en nuestro dockerhub. Kubectl es el comando para ejecutar operaciones docker.

```
kubectl run bootcamp --image=docker.io/jocatalin/kubernetes-bootcamp:v1 --port=8080
```

Apliquemos nuestro files deployment.yml que contiene las referencia de nuestra imagen y va a ser contenidas en nuestro pod creado anteriormente.

```
kubectl apply -f deployment.yml
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

Creamos nuestro servicio que va a contener el deployment previamente cargado

```
kubectl apply -f servicioBootcamp.yml
```

Si quieres ver el servicio generado

```
kubectl get services
```
Deberias ver algo asi como lo siguiente:

```
NAME               TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)    AGE
bootcamp-service   ClusterIP   10.101.6.222   <none>        8080/TCP   3h27m
kubernetes         ClusterIP   10.96.0.1      <none>        443/TCP    4h8m
```

Creamos nuestro ingress que va a asociar la <ip externa> que exponga creada automaticamente y la va a asociar al servicio creado anteriormente. para eso ejecutamos la siguiente instrucción.

```
kubectl apply -f ingress.yml
```

Igual que en el caso anterior para ver los <ingress> activos en kubernetes, le damos a la siguiente expresión.

```
kubectl get ingress
```

Deberías visualizar lo siguiente, donde podemos ver la ip por la cual ya podemos acceder a nuestra imagen que desplegara Hola mundo.

```
NAME               CLASS    HOSTS   ADDRESS         PORTS   AGE
bootcamp-ingress   <none>   *       192.168.64.12   80      3h24m
```

Testeamos lo anterior apuntando a la ip indicada, y ?
```
curl 192.168.64.12
```

Tenemos la respuesta de nuestra aplicacion, por medio de esta IP Expuesta en el puerto 80. 

```
Hello Kubernetes bootcamp! | Running on: bootcamp-75669f6c6d-btfw2 | v=1
```
  
## Obtener informacion Detallada de nuestro Bootcamp

```
kubectl describe service bootcamp
```

Encontramos el siguiente detalle 

```
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
```

## Escalar los Deployment

```
kubectl scale deployments/bootcamp --replicas=4
```

## Eliminar nuestro POD, Deployment Servicio, Ingress, 

kubectl delete ingress bootcamp

kubectl delete service bootcamp

kubectl delete deployment bootcamp

kubectl delete pod bootcamp


### Estructura de Archivos

En el siguiente esquema se declara la lista de archivos que contiene este simple proyecto.

```
.
├── README.md
├── deployment.yml
├── ingress.yml
└── servicioBootcamp.yml
```


## Built With

- [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
- [Maven](https://maven.apache.org/) - Dependency Management
- [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds


## Authors

- **Alejandro Sandoval** - _Initial work_ - [Alejandro Sandoval](https://github.com/catchai)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Para saber más de kubernet

- Visitar el bootcamp de kubernetes [bootcamp](https://kubernetesbootcamp.github.io/kubernetes-bootcamp/index.html)



