# Flask-App-on-Kubernetes-using-Helm-Chart
This repository is for deployment of Flask App on Minikube using Helm chart

To run this first need to Install docker, kubernetes, Minikube & Helm Chart

```
Minikube status
```
```
Minikube start
```

```
Minikube dashboard
```

# Helm Chart

To create the helm chart

```
helm create my-flask-app
```

Open vaules.yaml file and Provide the image name which was pushed to your docker registory
Provide the tag name if any. Update the port name.

# Deploy Helm Chart

helm install my-flask-app my-flask-app/ --values my-flask-app/values.yaml

# Run the deployment on your local

Get the application URL by running these commands:
```
  export POD_NAME=$(kubectl get pods --namespace default -l "app.kubernetes.io/name=my-flask-app,app.kubernetes.io/instance=my-flask-app" -o jsonpath="{.items[0].metadata.name}")
  export CONTAINER_PORT=$(kubectl get pod --namespace default $POD_NAME -o jsonpath="{.spec.containers[0].ports[0].containerPort}")
  echo "Visit http://127.0.0.1:8080 to use your application"
  kubectl --namespace default port-forward $POD_NAME 8080:$CONTAINER_PORT
```