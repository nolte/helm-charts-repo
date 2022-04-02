# powerdns

![Version: 1.1.1](https://img.shields.io/badge/Version-1.1.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

extendet powerdns chart

## Source Code

* <https://github.com/k8s-at-home/charts/tree/master/charts/stable/powerdns>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://k8s-at-home.com/charts | powerdns | 4.1.0 |
| https://nolte.github.io/helm-charts-repo/ | argo-workflows-execution(argo-workflow-mixin) | 0.2.0 |

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

