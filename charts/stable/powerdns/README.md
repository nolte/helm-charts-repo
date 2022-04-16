# powerdns

![Version: 1.3.2](https://img.shields.io/badge/Version-1.3.2-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

extendet powerdns chart

## Source Code

* <https://github.com/k8s-at-home/charts/tree/master/charts/stable/powerdns>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://k8s-at-home.com/charts | powerdns | 4.1.0 |
| https://nolte.github.io/helm-charts-repo/ | argo-workflows-execution(argo-workflow-mixin) | 0.4.2 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| argo-workflows-execution.cmTfStaticEndpoints.create | bool | `true` |  |
| argo-workflows-execution.configurationWorkflows.post-install.extraAnnotations."vault.hashicorp.com/agent-inject-secret-pdnsaccess" | string | `"secrets-tf/services/dns/users/root"` |  |
| argo-workflows-execution.configurationWorkflows.post-install.extraAnnotations."vault.hashicorp.com/agent-inject-template-pdnsaccess" | string | `"{{- with secret \"secrets-tf/services/dns/users/root\" -}}\nexport PDNS_API_KEY={{ .Data.data.token }}\n{{- end }}\n"` |  |
| argo-workflows-execution.configurationWorkflows.post-install.extraEnv[0].name | string | `"PDNS_SERVER_URL"` |  |
| argo-workflows-execution.configurationWorkflows.post-install.extraEnv[0].value | string | `"http://powerdns-webserver.{{.Release.Namespace}}.svc:8081"` |  |
| argo-workflows-execution.configurationWorkflows.post-install.extraSourceElements[0] | string | `"source /vault/secrets/pdnsaccess"` |  |
| argo-workflows-execution.configurationWorkflows.post-install.source.path | string | `"./src/applications/powerdns/configuration/baseline"` |  |
| argo-workflows-execution.configurationWorkflows.post-install.source.repo | string | `"https://github.com/nolte/argo-charts.git"` |  |
| argo-workflows-execution.configurationWorkflows.post-install.source.revision | string | `"master"` |  |
| argo-workflows-execution.configurationWorkflows.post-install.terraform.action | string | `"apply"` |  |
| argo-workflows-execution.configurationWorkflows.post-install.type | string | `"terragrunt"` |  |
| argo-workflows-execution.configurationWorkflows.post-install.workflow | bool | `true` |  |
| argo-workflows-execution.role.tfState.create | bool | `false` |  |
| argo-workflows-execution.role.tfState.name | string | `"argo-workflows-execution"` |  |
| argo-workflows-execution.role.type | string | `"ClusterRole"` |  |
| argo-workflows-execution.role.vaultInjector.create | bool | `false` |  |
| argo-workflows-execution.role.vaultInjector.name | string | `"argo-workflows-execution"` |  |
| argo-workflows-execution.roleBinding.tfState.create | bool | `true` |  |
| argo-workflows-execution.roleBinding.type | string | `"Role"` |  |
| argo-workflows-execution.roleBinding.vaultInjector.create | bool | `true` |  |
| argo-workflows-execution.serviceAccount.create | bool | `true` |  |

