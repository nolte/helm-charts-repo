# gitea

![Version: 1.2.7](https://img.shields.io/badge/Version-1.2.7-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

Preconfigured gitea Deployment

## Source Code

* <https://gitea.com/gitea/helm-chart>
* <https://gitea.io/en-us/>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://dl.gitea.io/charts/ | gitea | 5.0.9 |
| https://nolte.github.io/helm-charts-repo/ | externalsecrets(external-secrets-manifests) | 0.1.3 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| externalsecrets.enabled | bool | `false` |  |
| externalsecrets.secrets.gitea-admin-secret.data[0].key | string | `"secrets-tf/data/services/gitea/users/admin"` |  |
| externalsecrets.secrets.gitea-admin-secret.data[0].name | string | `"username"` |  |
| externalsecrets.secrets.gitea-admin-secret.data[0].property | string | `"username"` |  |
| externalsecrets.secrets.gitea-admin-secret.data[1].key | string | `"secrets-tf/data/services/gitea/users/admin"` |  |
| externalsecrets.secrets.gitea-admin-secret.data[1].name | string | `"password"` |  |
| externalsecrets.secrets.gitea-admin-secret.data[1].property | string | `"password"` |  |
| externalsecrets.secrets.gitea-admin-secret.data[2].key | string | `"secrets-tf/data/services/gitea/users/admin"` |  |
| externalsecrets.secrets.gitea-admin-secret.data[2].name | string | `"email"` |  |
| externalsecrets.secrets.gitea-admin-secret.data[2].property | string | `"email"` |  |
| httpProxy.create | bool | `false` |  |
| httpProxy.fqdn | string | `"gitea.smart-home.k8sservices.local"` |  |
| httpProxy.tls.secretName | string | `"cert-manager/wildcard-duckdns-org-tls"` |  |

```
helm template . --set externalSecret.create=true --set httpProxy.create=true
```