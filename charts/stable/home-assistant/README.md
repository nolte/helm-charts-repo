

# home-assistant

![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

Extended Home Assistant Deployment, with optional Project Contour HTTPProxy support
and using External Secrets for Direct load Credentials from Vault Secret Backend.

## Source Code

* <https://github.com/nolte/helm-charts-repo/tree/main/charts/stable/home-assistant>
* <https://github.com/k8s-at-home/charts/tree/master/charts/stable/home-assistant>

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| https://k8s-at-home.com/charts/ | homeassistant(home-assistant) | 12.0.1 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| assistantCreds.create | bool | `true` |  |
| assistantCreds.data[0].key | string | `"secrets-tf/data/third-party-services/google.com/projects/home-assistant"` |  |
| assistantCreds.data[0].name | string | `"GOOGLE_CLIENT_ID"` |  |
| assistantCreds.data[0].property | string | `"client_id"` |  |
| assistantCreds.data[1].key | string | `"secrets-tf/data/third-party-services/google.com/projects/home-assistant"` |  |
| assistantCreds.data[1].name | string | `"GOOGLE_CLIENT_SECRET"` |  |
| assistantCreds.data[1].property | string | `"client_secret"` |  |
| assistantCreds.data[2].key | string | `"secrets-tf/data/third-party-services/openweathermap.org/projects/home-assistant"` |  |
| assistantCreds.data[2].name | string | `"OPENWEATHERMAP_API_KEY"` |  |
| assistantCreds.data[2].property | string | `"token"` |  |
| assistantCreds.data[3].key | string | `"secrets-tf/data/services/router-fritz-box/users/admin"` |  |
| assistantCreds.data[3].name | string | `"FRITZBOX_USERNAME"` |  |
| assistantCreds.data[3].property | string | `"username"` |  |
| assistantCreds.data[4].key | string | `"secrets-tf/data/services/router-fritz-box/users/admin"` |  |
| assistantCreds.data[4].name | string | `"FRITZBOX_PASSWORD"` |  |
| assistantCreds.data[4].property | string | `"password"` |  |
| assistantCreds.data[5].key | string | `"secrets-tf/data/third-party-services/github.com/apitoken/home-assistant"` |  |
| assistantCreds.data[5].name | string | `"GITHUB_ACCESS_TOKEN"` |  |
| assistantCreds.data[5].property | string | `"token"` |  |
| certificate.create | bool | `false` |  |
| gitCreds.create | bool | `true` |  |
| homeassistant.additionalContainers.hassConfigurator.image | string | `"causticlab/hass-configurator-docker:latest"` |  |
| homeassistant.additionalContainers.hassConfigurator.name | string | `"hass-configurator"` |  |
| homeassistant.additionalContainers.hassConfigurator.volumeMounts[0].mountPath | string | `"/hass-config"` |  |
| homeassistant.additionalContainers.hassConfigurator.volumeMounts[0].name | string | `"config"` |  |
| homeassistant.additionalContainers.hassConfigurator.volumeMounts[1].mountPath | string | `"/root/.ssh"` |  |
| homeassistant.additionalContainers.hassConfigurator.volumeMounts[1].name | string | `"gitsecret"` |  |
| homeassistant.controller.annotations."reloader.stakater.com/auto" | string | `"true"` |  |
| homeassistant.env.DENON_ENDPOINT | string | `"192.168.0.27"` |  |
| homeassistant.env.FIRETV_ENDPOINT | string | `"192.168.0.20"` |  |
| homeassistant.env.FRITZBOX_ENDPOINT | string | `"192.168.0.1"` |  |
| homeassistant.env.HARMONY_ENDPOINT | string | `"192.168.0.32"` |  |
| homeassistant.env.HUE_ENDPOINT | string | `"192.168.0.17"` |  |
| homeassistant.env.MQTT_ENDPOINT | string | `"mosquitto.mosquitto.svc"` |  |
| homeassistant.env.PHILIPSTV_ENDPOINT | string | `"192.168.0.24"` |  |
| homeassistant.envFrom[0].secretRef.name | string | `"home-assistant-creds"` |  |
| homeassistant.global.fullnameOverride | string | `"home-assistant"` |  |
| homeassistant.initContainers.gitsync.args[0] | string | `"set -e; if [ -d \"/config/.git\" ]; then git -C \"/config\" pull || true; else if [ \"$(ls -A /config)\" ]; then git clone --branch ${GIT_BRANCH} --depth 2 \"${GIT_REPO}\" /tmp/repo; cp -rf /tmp/repo/.git \"/config\"; cd \"/config\"; git checkout -f; else git clone --branch ${GIT_BRANCH} --depth 2 \"${GIT_REPO}\" \"/config\"; fi; fi; if [ -f \"/root/.ssh/git-crypt-key\" ]; then cd /config; git-crypt unlock \"/root/.ssh/git-crypt-key\"; fi;"` |  |
| homeassistant.initContainers.gitsync.command[0] | string | `"/bin/sh"` |  |
| homeassistant.initContainers.gitsync.command[1] | string | `"-c"` |  |
| homeassistant.initContainers.gitsync.env[0].name | string | `"GIT_BRANCH"` |  |
| homeassistant.initContainers.gitsync.env[0].value | string | `"feature/minimized-config"` |  |
| homeassistant.initContainers.gitsync.env[1].name | string | `"GIT_REPO"` |  |
| homeassistant.initContainers.gitsync.env[1].value | string | `"git@github.com:nolte/home-assistant-config.git"` |  |
| homeassistant.initContainers.gitsync.image | string | `"k8sathome/git-crypt:2020.11.15"` |  |
| homeassistant.initContainers.gitsync.imagePullPolicy | string | `"IfNotPresent"` |  |
| homeassistant.initContainers.gitsync.name | string | `"git-sync"` |  |
| homeassistant.initContainers.gitsync.volumeMounts[0].mountPath | string | `"/config"` |  |
| homeassistant.initContainers.gitsync.volumeMounts[0].name | string | `"config"` |  |
| homeassistant.initContainers.gitsync.volumeMounts[1].mountPath | string | `"/root/.ssh"` |  |
| homeassistant.initContainers.gitsync.volumeMounts[1].name | string | `"gitsecret"` |  |
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

```

