# Udagram Services

Udagram is a Instragram like application. It consists on three basic applications a feed service, an user service and a frontend.

Each application has its own docker image. To build them and run locally, read the following instructions.

## Build images

To build the images you have to install docker. You could use the docker-compose tool and build all three application with:

`docker-compose -f udacity-c3-deployment/docker/docker-compose-build.yaml build --parallel`

## Run images
After building, you can run the applications by running:

`docker-compose up`

## Kubernetes
In this repository you will find some kubernetes configurations that allows you to deploy the applications to your own kubernetes cluster. With your cluster running and kubectl configured, you could go to the k8s directory in udacity-c3-deployment folder and run:

```
kubectl apply -f frontend-deployment.yaml
kubectl apply -f backend-feed-deployment.yaml
kubectl apply -f backend-user-deployment.yaml
kubectl apply -f reverseproxy-deployment.yaml

kubectl apply -f frontend-service.yaml
kubectl apply -f backend-feed-service.yaml
kubectl apply -f backend-user-service.yaml
kubectl apply -f reverseproxy-service.yaml
```

After applying everything, kubernetes will start the application and you could configure a port foward to the application that allows you to use the application in your browser:

```
kubectl port-forward service/frontend 8100:8100
kubectl port-forward service/reverseproxy 8080:8080
```

After running both port fowarding, you can go to:

`http://localhost:8100`
