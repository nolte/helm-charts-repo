# keycloak

![Version: 3.4.1](https://img.shields.io/badge/Version-3.4.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

Preconfigured keycloak Deployment

## Source Code

* <https://codecentric.github.io/helm-charts>
* <https://github.com/codecentric/helm-charts/tree/master/charts/keycloak>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://codecentric.github.io/helm-charts | keycloak | 18.1.0 |
| https://nolte.github.io/helm-charts-repo/ | argo-workflows-execution(argo-workflow-mixin) | 0.4.2 |
| https://nolte.github.io/helm-charts-repo/ | externalsecrets(external-secrets-manifests) | 0.1.2 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| argo-workflows-execution.cmTfStaticEndpoints.create | bool | `true` |  |
| argo-workflows-execution.configurationWorkflows.post-install.extraAnnotations."vault.hashicorp.com/agent-inject-secret-keycloak" | string | `"secrets-tf/services/IdentityAccessManagement/users/admin"` |  |
| argo-workflows-execution.configurationWorkflows.post-install.extraAnnotations."vault.hashicorp.com/agent-inject-template-keycloak" | string | `"{{- with secret \"secrets-tf/services/IdentityAccessManagement/users/admin\" -}}\nexport KEYCLOAK_USER={{ .Data.data.username }}\nexport KEYCLOAK_PASSWORD={{ .Data.data.password }}\n{{- end }}\n"` |  |
| argo-workflows-execution.configurationWorkflows.post-install.extraSourceElements[0] | string | `"source /vault/secrets/keycloak"` |  |
| argo-workflows-execution.configurationWorkflows.post-install.source.path | string | `"./src/applications/keycloak/configuration/baseline"` |  |
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
| client_id | string | `"admin-cli"` |  |
| externalsecrets.enabled | bool | `true` |  |
| externalsecrets.secrets.keycloak-admin-user.data[0].key | string | `"secrets-tf/data/services/IdentityAccessManagement/users/admin"` |  |
| externalsecrets.secrets.keycloak-admin-user.data[0].name | string | `"KEYCLOAK_PASSWORD"` |  |
| externalsecrets.secrets.keycloak-admin-user.data[0].property | string | `"password"` |  |
| externalsecrets.secrets.keycloak-admin-user.data[1].key | string | `"secrets-tf/data/services/IdentityAccessManagement/users/admin"` |  |
| externalsecrets.secrets.keycloak-admin-user.data[1].name | string | `"KEYCLOAK_USER"` |  |
| externalsecrets.secrets.keycloak-admin-user.data[1].property | string | `"username"` |  |
| httpProxy.create | bool | `false` |  |
| httpProxy.fqdn | string | `"keycloak.smart-home.k8sservices.local"` |  |
| httpProxy.tls.secretName | string | `"cert-manager/wildcard-duckdns-org-tls"` |  |
| keycloak.extraEnvFrom | string | `"- secretRef:\n    name: 'keycloak-admin-user'\n"` |  |
| terraformModule.address | string | `"https://github.com/nolte/argo-charts.git//src/applications/keycloak/configuration/baseline?ref=master"` |  |

