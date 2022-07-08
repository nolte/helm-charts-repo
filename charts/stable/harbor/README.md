# harbor

![Version: 0.2.3](https://img.shields.io/badge/Version-0.2.3-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

Preconfigured harbor Deployment

## Source Code

* <https://github.com/goharbor/harbor-helm>
* <https://github.com/goharbor/harbor>
* <https://goharbor.io/>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://helm.goharbor.io | harbor | 1.9.2 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| harbor.expose.ingress.hosts.core | string | `"harbor.smart-home.k8sservices.local"` |  |
| harbor.expose.ingress.hosts.notary | string | `"notary.smart-home.k8sservices.local"` |  |
| httpProxy.create | bool | `false` |  |
| httpProxy.fqdn | string | `"harbor.smart-home.k8sservices.local"` |  |
| httpProxy.tls.secretName | string | `"cert-manager/wildcard-duckdns-org-tls"` |  |

