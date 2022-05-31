# basic-webservice-chart

a basic chart to deploy a webservice

## usage
```Shell
# define defaults
: "${APP:=mywebservice}"
: "${DOMAIN:=mywebservice.my.example.org}"
: "${CHART:=mywebservice}"
: "${NAMESPACE:=mywebservice}"
: "${REPO_NAME:=basic-webservice-chart}"
: "${REPO_URL:=https://honigpferd.github.io/basic-webservice-chart}"

# load repo
helm repo add $REPO_NAME $REPO_URL
helm repo update

# install chart
helm upgrade --install $APP $REPO_NAME/$CHART \
    --namespace $NAMESPACE --create-namespace \
    --set ingress.enabled=true \
    --set ingress.annotations."kubernetes\.io\/ingress\.class"=nginx \
    --set ingress.annotations."cert-manager\.io\/cluster-issuer"=letsencrypt-prod \
    --set ingress.hosts[0].host=$DOMAIN \
    --set ingress.hosts[0].paths[0].pathType=/ \
    --set ingress.hosts[0].paths[0].pathType=ImplementationSpecific \
    --set ingress.tls[0].secretName=$DOMAIN-tls \
    --set ingress.tls[0].hosts[0]=$DOMAIN
```
