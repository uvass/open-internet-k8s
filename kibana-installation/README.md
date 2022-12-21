# Installation

This is the Kibana installation for the medium article.

To install it use helm:

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
helm install kibana bitnami/kibana -n cattle-logging-system -f ./kibana-values.yaml
```

Add the pipeline for processing the Snowflake logs in the DevTools by using the following command:

```bash
PUT _ingest/pipeline/logs-snowflake
{
    "description": "Parses the snowflake log files",
    "processors": [
      {
        "grok": {
          "field": "message",
          "patterns": [
            "there were %{NUMBER:connections:int} connections. Traffic Relayed ↑ %{GREEDYDATA:upload-text}, ↓ %{GREEDYDATA:download-text}."
          ]
        }
      },
      {
        "bytes": {
          "field": "upload-text",
          "target_field": "upload"
        }
      },
      {
        "bytes": {
          "field": "download-text",
          "target_field": "download"
        }
      }
    ]
  }
  ```

Inport the snowflake-dashboard.ndjson in Kibana under Stack Management -> Saved Objects
