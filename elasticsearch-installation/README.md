# Installation

This is the Elasticsearch installation for the medium article.

To install it use helm:

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
helm install elasticsearch bitnami/elasticsearch -n cattle-logging-system -f ./elasticsearch-values.yaml
```

