# argo-workflows

![Version: 0.8.1](https://img.shields.io/badge/Version-0.8.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

Preconfigured argo workflows Deployment

## Source Code

* <https://github.com/argoproj/argo-helm/tree/master/charts/argo-workflows>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://argoproj.github.io/argo-helm | argoworkflows(argo-workflows) | 0.13.1 |
| https://nolte.github.io/helm-charts-repo/ | argoworkflowmixin(argo-workflow-mixin) | 0.3.0 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| argoworkflowmixin.role.tfState.create | bool | `true` |  |
| argoworkflowmixin.role.tfState.name | string | `"argo-workflows-execution"` |  |
| argoworkflowmixin.role.type | string | `"ClusterRole"` |  |
| argoworkflowmixin.role.vaultInjector.create | bool | `true` |  |
| argoworkflowmixin.role.vaultInjector.name | string | `"argo-workflows-execution"` |  |
| argoworkflowmixin.roleBinding.tfState.create | bool | `false` |  |
| argoworkflowmixin.roleBinding.type | string | `"Role"` |  |
| argoworkflowmixin.roleBinding.vaultInjector.create | bool | `false` |  |
| argoworkflowmixin.serviceAccount.annotations | object | `{}` |  |
| argoworkflowmixin.serviceAccount.create | bool | `false` |  |
| argoworkflowmixin.serviceAccount.name | string | `"argo-workflows-execution"` |  |
| httpProxy.create | bool | `false` |  |
| httpProxy.fqdn | string | `"argo.smart-home.k8sservices.local"` |  |
| httpProxy.tls.secretName | string | `"cert-manager/wildcard-duckdns-org-tls"` |  |

