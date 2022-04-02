# cert-manager-webhook-duckdns

![Version: 0.2.3](https://img.shields.io/badge/Version-0.2.3-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

Preconfigured Certmanager Duckdns Deployment

## Source Code

* <https://github.com/ebrianne/helm-charts/tree/master/charts/cert-manager-webhook-duckdns>
* <https://github.com/ebrianne/cert-manager-webhook-duckdns>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://nolte.github.io/ebrianne-helm-charts | certmanagerwebhookduckdns(cert-manager-webhook-duckdns) | 1.2.4 |
| https://nolte.github.io/helm-charts-repo/ | externalsecrets(external-secrets-manifests) | 0.1.1 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| certmanagerwebhookduckdns.clusterIssuer.production.create | bool | `true` |  |
| certmanagerwebhookduckdns.clusterIssuer.staging.create | bool | `true` |  |
| certmanagerwebhookduckdns.fullnameOverride | string | `"cert-manager-webhook-duckdns"` |  |
| certmanagerwebhookduckdns.secret.existingSecret | bool | `true` |  |
| certmanagerwebhookduckdns.secret.existingSecretName | string | `"duckdns-token"` |  |
| externalsecrets.enabled | bool | `true` |  |
| externalsecrets.secrets.duckdns-token.data[0].key | string | `"secrets-tf/data/third-party-services/duckdns.org/api"` |  |
| externalsecrets.secrets.duckdns-token.data[0].name | string | `"token"` |  |
| externalsecrets.secrets.duckdns-token.data[0].property | string | `"token"` |  |

