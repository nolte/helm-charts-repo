# external-dns

![Version: 0.5.0](https://img.shields.io/badge/Version-0.5.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

Wrapped External DNS deployment, with External Secrets Support.

## Source Code

* <https://artifacthub.io/packages/helm/bitnami/external-dns>
* <https://github.com/bitnami/charts/tree/master/bitnami/external-dns>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://charts.bitnami.com/bitnami | externaldns(external-dns) | 6.6.0 |
| https://nolte.github.io/helm-charts-repo/ | externalsecrets(external-secrets-manifests) | 0.1.3 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| externaldns.pdns.apiUrl | string | `"http://powerdns-webserver.powerdns.svc"` |  |
| externaldns.pdns.secretName | string | `"pdns-access"` |  |
| externaldns.provider | string | `"pdns"` |  |
| externalsecrets.enabled | bool | `false` |  |
| externalsecrets.secrets.pdns-access.data[0].key | string | `"secrets-tf/data/services/dns/users/root"` |  |
| externalsecrets.secrets.pdns-access.data[0].name | string | `"pdns_api_key"` |  |
| externalsecrets.secrets.pdns-access.data[0].property | string | `"token"` |  |

## Usage

