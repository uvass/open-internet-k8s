# Installation

This is the Kibana installation for the medium article.

To install it use helm:

```
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
helm install kibana bitnami/kibana -n cattle-logging-system -f ./kibana-values.yaml
```
