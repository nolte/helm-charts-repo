# keycloak

![Version: 2.0.4](https://img.shields.io/badge/Version-2.0.4-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

Preconfigured keycloak Deployment

## Source Code

* <https://codecentric.github.io/helm-charts>
* <https://github.com/codecentric/helm-charts/tree/master/charts/keycloak>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://codecentric.github.io/helm-charts | keycloak | 17.0.3 |
| https://nolte.github.io/helm-charts-repo/ | argo-workflows-execution(argo-workflow-mixin) | 0.2.1 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| argo-workflows-execution.cmTfStaticEndpoints.create | bool | `true` |  |
| argo-workflows-execution.role.tfState.create | bool | `false` |  |
| argo-workflows-execution.role.tfState.name | string | `"argo-workflows-execution"` |  |
| argo-workflows-execution.role.type | string | `"ClusterRole"` |  |
| argo-workflows-execution.role.vaultInjector.create | bool | `false` |  |
| argo-workflows-execution.role.vaultInjector.name | string | `"argo-workflows-execution"` |  |
| argo-workflows-execution.roleBinding.tfState.create | bool | `true` |  |
| argo-workflows-execution.roleBinding.type | string | `"Role"` |  |
| argo-workflows-execution.roleBinding.vaultInjector.create | bool | `true` |  |
| argo-workflows-execution.serviceAccount.create | bool | `true` |  |
| client_id | string | `"admin-cli"` |  |
| httpProxy.create | bool | `false` |  |
| httpProxy.fqdn | string | `"keycloak.smart-home.k8sservices.local"` |  |
| httpProxy.tls.secretName | string | `"cert-manager/wildcard-duckdns-org-tls"` |  |
| keycloak.extraEnvFrom | string | `"- secretRef:\n    name: 'keycloak-admin-user'\n"` |  |
| terraformModule.address | string | `"https://github.com/nolte/argo-charts.git//src/applications/keycloak/configuration/baseline?ref=master"` |  |

