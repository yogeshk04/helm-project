
# Create the helmchart

```
Create new helmchart folder
> helm create webapp
Update the template manfest deployment, service and configmap
> helm install mywebapp webapp
```
New mywebapp will get deployed. Here if you are using docker-desktop or minikube then use **Kube Forwarder** software to do service port forwarding and access the application.

OR

There is a NOTES.txt file which will show the command to do the port forwarding.

## Install the first one
```
helm install mywebapp-release webapp/ --values webapp/values.yaml
```

## Upgrade after templating
```
helm upgrade mywebapp-release webapp/ --values webapp/values.yaml
```

## Create dev/prod
```
k create namespace dev
k create namespace prod
helm install mywebapp-release-dev webapp/ --values webapp/values.yaml -f webapp/values-dev.yaml -n dev
helm install mywebapp-release-prod webapp/ --values webapp/values.yaml -f webapp/values-prod.yaml -n prod
helm ls --all-namespaces
```
