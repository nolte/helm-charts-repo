# argo-workflow-mixin

![Version: 0.4.3](https://img.shields.io/badge/Version-0.4.3-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.16.0](https://img.shields.io/badge/AppVersion-1.16.0-informational?style=flat-square)

A Helm chart for Kubernetes

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| cmTfStaticEndpoints.create | bool | `false` |  |
| cmTfStaticEndpoints.keycloak | string | `"http://keycloak-http.keycloak.svc"` |  |
| cmTfStaticEndpoints.s3 | string | `"http://minio.minio.svc"` |  |
| cmTfStaticEndpoints.vaultEndpoint | string | `"http://vault.vault.svc:8200"` |  |
| configurationWorkflows | object | `{}` |  |
| fullnameOverride | string | `""` |  |
| global.workflow.terragrunt.image | string | `"alpine/terragrunt:1.2.4"` | Default terragrunt Container version |
| nameOverride | string | `""` |  |
| role.tfState.create | bool | `false` |  |
| role.tfState.name | string | `"argo-workflows-execution"` |  |
| role.type | string | `"ClusterRole"` |  |
| role.vaultInjector.create | bool | `false` |  |
| role.vaultInjector.name | string | `"argo-workflows-execution"` |  |
| roleBinding.tfState.create | bool | `false` |  |
| roleBinding.type | string | `"Role"` |  |
| roleBinding.vaultInjector.create | bool | `false` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.create | bool | `false` |  |
| serviceAccount.name | string | `"argo-workflows-executer"` |  |

