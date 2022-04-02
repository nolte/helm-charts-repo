# vault

![Version: 0.6.1](https://img.shields.io/badge/Version-0.6.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

Preconfigured Vault Deployment

## Source Code

* <https://github.com/hashicorp/vault-helm>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://helm.releases.hashicorp.com | vault | 0.19.0 |
| https://nolte.github.io/helm-charts-repo/ | argo-workflows-execution(argo-workflow-mixin) | 0.2.0 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| address | string | `"http://vault.{{ .Release.Namespace }}.svc:8200"` |  |
| argo-workflows-execution.cmTfStaticEndpoints.create | bool | `false` |  |
| argo-workflows-execution.role.tfState.create | bool | `false` |  |
| argo-workflows-execution.role.tfState.name | string | `"argo-workflows-execution"` |  |
| argo-workflows-execution.role.type | string | `"ClusterRole"` |  |
| argo-workflows-execution.role.vaultInjector.create | bool | `false` |  |
| argo-workflows-execution.role.vaultInjector.name | string | `"argo-workflows-execution"` |  |
| argo-workflows-execution.roleBinding.tfState.create | bool | `true` |  |
| argo-workflows-execution.roleBinding.type | string | `"Role"` |  |
| argo-workflows-execution.roleBinding.vaultInjector.create | bool | `true` |  |
| argo-workflows-execution.serviceAccount.create | bool | `true` |  |
| httpProxy.create | bool | `false` |  |
| httpProxy.fqdn | string | `"vault.smart-home.k8sservices.local"` |  |
| httpProxy.tls.secretName | string | `"cert-manager/wildcard-duckdns-org-tls"` |  |
| vault.server.ingress.enabled | bool | `false` |  |

## Links

* https://github.com/external-secrets/external-secrets
* https://www.linkedin.com/pulse/secret-management-kubernetes-external-secrets-hashicorp-stephen-kuntz