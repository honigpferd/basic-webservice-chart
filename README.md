# basic-webservice-chart

a basic chart to deploy a webservice

## usage
```Shell
APP=mywebservice
CHART=mywebservice
NAMESPACE=mywebservice
REPO_NAME=basic-webservice-chart
REPO_URL=https://honigpferd.github.io/basic-webservice-chart
helm repo add $REPO_NAME $REPO_URL
helm repo update
helm upgrade --install $APP $REPO_NAME/$CHART \
    --namespace $NAMESPACE --create-namespace
```
