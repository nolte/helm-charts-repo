# forecastle

![Version: 0.2.15](https://img.shields.io/badge/Version-0.2.15-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

Preconfigured forecastle Deployment

## Source Code

* <https://stakater.github.io/stakater-charts>
* <https://github.com/stakater/Forecastle/tree/master/deployments/kubernetes/chart/forecastle>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://stakater.github.io/stakater-charts | forecastle | v1.0.91 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| httpProxy.create | bool | `false` |  |
| httpProxy.fqdn | string | `"forecastle.smart-home.k8sservices.local"` |  |
| httpProxy.tls.secretName | string | `"cert-manager/wildcard-duckdns-org-tls"` |  |

