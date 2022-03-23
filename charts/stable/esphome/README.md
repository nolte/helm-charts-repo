# esphome

![Version: 0.3.0](https://img.shields.io/badge/Version-0.3.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

Pre Configured ESPHome Deployment, with example values for use a git init container to receive configurations from a repository.

## Source Code

* <https://github.com/k8s-at-home/charts/tree/master/charts/stable/esphome>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://k8s-at-home.com/charts/ | esphome | 8.2.0 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| httpProxy.create | bool | `false` |  |
| httpProxy.fqdn | string | `"esphome.smart-home.k8sservices.local"` |  |
| httpProxy.tls.secretName | string | `"cert-manager/wildcard-duckdns-org-tls"` |  |

## Usage

For using Configurations from Git Repository take a look to `values-gitsync.yaml`.

```yaml
...
    helm:
      ...
      parameters:
        - name: esphome.initContainers.gitsync.env[1].value
          value: "git@github.com:nolte/esphome-configs.git"
      valueFiles:
        - values-gitsync.yaml
....
```
*Example ArgoCD Application.*

### Preconditions

#### Secret with SSH Deployment key

Required a k8s Secret `git-creds` for Github Project Access.

```sh
kubectl -n esphome create secret generic git-creds \
  --from-literal=id_rsa="$(pass internet/project/homeassistant/deploymentkey/id_rsa)" \
  --from-literal=id_rsa.pub="$(pass internet/project/homeassistant/deploymentkey/id_rsa.pub)" \
  --from-literal=known_hosts="$(ssh-keyscan -t rsa github.com)"
```

