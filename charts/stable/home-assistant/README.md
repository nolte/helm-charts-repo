# home-assistant

![Version: 2.4.0](https://img.shields.io/badge/Version-2.4.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

Extended Home Assistant Deployment, with optional Project Contour HTTPProxy support
and using External Secrets for Direct load Credentials from Vault Secret Backend.

**Homepage:** <https://github.com/nolte/helm-charts-repo/tree/main/charts/stable/home-assistant>

## Source Code

* <https://github.com/nolte/helm-charts-repo/tree/main/charts/stable/home-assistant>
* <https://github.com/k8s-at-home/charts/tree/master/charts/stable/home-assistant>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://k8s-at-home.com/charts/ | homeassistant(home-assistant) | 13.3.0 |
| https://nolte.github.io/helm-charts-repo/ | externalsecrets(external-secrets-manifests) | 0.1.3 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| certificate.create | bool | `false` |  |
| externalsecrets.enabled | bool | `false` |  |
| homeassistant.additionalContainers.hassConfigurator.image | string | `"causticlab/hass-configurator-docker:latest"` |  |
| homeassistant.additionalContainers.hassConfigurator.name | string | `"hass-configurator"` |  |
| homeassistant.additionalContainers.hassConfigurator.volumeMounts[0].mountPath | string | `"/hass-config"` |  |
| homeassistant.additionalContainers.hassConfigurator.volumeMounts[0].name | string | `"config"` |  |
| homeassistant.additionalContainers.hassConfigurator.volumeMounts[1].mountPath | string | `"/root/.ssh"` |  |
| homeassistant.additionalContainers.hassConfigurator.volumeMounts[1].name | string | `"gitsecret"` |  |
| homeassistant.controller.annotations."reloader.stakater.com/auto" | string | `"true"` |  |
| homeassistant.envFrom[0].secretRef.name | string | `"home-assistant-creds"` |  |
| homeassistant.global.fullnameOverride | string | `"home-assistant"` |  |
| homeassistant.ingress.main.annotations."nginx.org/websocket-services" | string | `"home-assistant"` |  |
| homeassistant.ingress.main.enabled | bool | `false` |  |
| homeassistant.ingress.main.hosts[0].host | string | `"home-assistant.local"` |  |
| homeassistant.ingress.main.hosts[0].paths[0].path | string | `"/"` |  |
| homeassistant.ingress.main.ingressClassName | string | `"nginx"` |  |
| homeassistant.persistence.config.enabled | bool | `true` |  |
| homeassistant.persistence.config.mountPath | string | `"/config"` |  |
| homeassistant.persistence.gitsecret.enabled | bool | `true` |  |
| homeassistant.persistence.gitsecret.mountPath | string | `"/root/.ssh"` |  |
| homeassistant.persistence.gitsecret.type | string | `"custom"` |  |
| homeassistant.persistence.gitsecret.volumeSpec.secret.defaultMode | int | `256` |  |
| homeassistant.persistence.gitsecret.volumeSpec.secret.optional | bool | `true` |  |
| homeassistant.persistence.gitsecret.volumeSpec.secret.secretName | string | `"git-creds"` |  |
| homeassistant.resources.limits.cpu | int | `2` |  |
| homeassistant.resources.limits.memory | string | `"2048Mi"` |  |
| homeassistant.resources.requests.cpu | int | `1` |  |
| homeassistant.resources.requests.memory | string | `"1024Mi"` |  |
| httpProxy.create | bool | `false` |  |
| httpProxy.fqdn | string | `"home-assistant.smart-home.k8sservices.local"` |  |
| httpProxy.tls.secretName | string | `"cert-manager/wildcard-duckdns-org-tls"` |  |

## Usage

**Without Vault support create 2 secrets, `git-creds` and `home-assistant-creds`.**

```sh

kubectl -n home-assistant create secret generic git-creds \
  --from-literal=id_rsa="$(pass internet/project/homeassistant/deploymentkey/id_rsa)" \
  --from-literal=id_rsa.pub="$(pass internet/project/homeassistant/deploymentkey/id_rsa.pub)" \
  --from-literal=known_hosts="$(ssh-keyscan -t rsa github.com)"

```

```sh
kubectl -n home-assistant delete secret home-assistant-creds

kubectl -n home-assistant create secret generic home-assistant-creds \
  --from-literal=GOOGLE_CLIENT_ID="$(pass internet/google.com/projects/home-assistant-274616/client_id)" \
  --from-literal=GOOGLE_CLIENT_SECRET="$(pass internet/google.com/projects/home-assistant-274616/client_secret)" \
  --from-literal=OPENWEATHERMAP_API_KEY="$(pass network/homeassistant/openweather/apikey)" \
  --from-literal=FRITZBOX_USERNAME="$(pass network/homeassistant/fritzbox/user)" \
  --from-literal=FRITZBOX_PASSWORD="$(pass network/homeassistant/fritzbox/password)" \
  --from-literal=GITHUB_ACCESS_TOKEN="$(pass internet/github.com/nolte/servics/home-assistant/token)" \
  --from-literal=HUE_ENDPOINT=192.168.178.29
```

Using Env Variables for make scripts a bit more flexible.

```yaml
...
  env:
    HUE_ENDPOINT: "192.168.0.17"
    MQTT_ENDPOINT: mosquitto.mosquitto.svc
...
```

