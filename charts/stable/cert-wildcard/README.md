# cert-wildcard

![Version: 0.2.2](https://img.shields.io/badge/Version-0.2.2-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.16.0](https://img.shields.io/badge/AppVersion-1.16.0-informational?style=flat-square)

A Helm chart for Kubernetes

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| dnsName | string | `"dev44-just-homestyle.duckdns.org"` |  |
| fullnameOverride | string | `""` |  |
| issuerName | string | `"cert-manager-webhook-duckdns-production"` |  |
| nameOverride | string | `""` |  |
| tlsDelegation.create | bool | `false` |  |

