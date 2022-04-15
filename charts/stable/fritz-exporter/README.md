# fritz-exporter

![Version: 0.2.1](https://img.shields.io/badge/Version-0.2.1-informational?style=flat-square) ![AppVersion: v2.0.0](https://img.shields.io/badge/AppVersion-v2.0.0-informational?style=flat-square)

FritzBox Exporter

**Homepage:** <https://github.com/k8s-at-home/charts/tree/master/charts/incubator/fritzbox-exporter>

## Source Code

* <https://github.com/pdreker/fritz_exporter>

## Requirements

Kubernetes: `>=1.16.0-0`

| Repository | Name | Version |
|------------|------|---------|
| https://library-charts.k8s-at-home.com | common | 4.3.0 |
| https://nolte.github.io/helm-charts-repo/ | externalsecrets(external-secrets-manifests) | 0.1.2 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| controller.strategy | string | `"RollingUpdate"` |  |
| env | object | See below | environment variables. See [application docs](https://docs.miguelndecarvalho.pt/projects/speedtest-exporter/) for more details. |
| env.TZ | string | `"UTC"` | Set the container timezone |
| externalsecrets.enabled | bool | `false` |  |
| externalsecrets.secrets.fritz-creds.data[0].key | string | `"secrets-tf/data/services/router-fritz-box/users/admin"` |  |
| externalsecrets.secrets.fritz-creds.data[0].name | string | `"FRITZ_HOSTNAME"` |  |
| externalsecrets.secrets.fritz-creds.data[0].property | string | `"endpoint"` |  |
| externalsecrets.secrets.fritz-creds.data[1].key | string | `"secrets-tf/data/services/router-fritz-box/users/admin"` |  |
| externalsecrets.secrets.fritz-creds.data[1].name | string | `"FRITZ_USERNAME"` |  |
| externalsecrets.secrets.fritz-creds.data[1].property | string | `"username"` |  |
| externalsecrets.secrets.fritz-creds.data[2].key | string | `"secrets-tf/data/services/router-fritz-box/users/admin"` |  |
| externalsecrets.secrets.fritz-creds.data[2].name | string | `"FRITZ_PASSWORD"` |  |
| externalsecrets.secrets.fritz-creds.data[2].property | string | `"password"` |  |
| image.pullPolicy | string | `"IfNotPresent"` | image pull policy |
| image.repository | string | `"pdreker/fritz_exporter"` | image repository |
| image.tag | string | `"v2.0.0"` | image tag |
| metrics.enabled | bool | See values.yaml | Enable and configure a Prometheus serviceMonitor for the chart under this key. |
| metrics.serviceMonitor.labels | object | `{}` |  |
| service | object | See values.yaml | Configures service settings for the chart. |

