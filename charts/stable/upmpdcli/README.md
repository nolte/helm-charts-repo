# upmpdcli

![Version: 0.0.1](https://img.shields.io/badge/Version-0.0.1-informational?style=flat-square) ![AppVersion: v0.0.1](https://img.shields.io/badge/AppVersion-v0.0.1-informational?style=flat-square)

upmpdcli Receiver

**Homepage:** <https://github.com/nolte/helm-charts-repo/tree/master/charts/stable/upmpdcli>

## Source Code

* <https://github.com/nolte/docker-upmpdcli>

## Requirements

Kubernetes: `>=1.16.0-0`

| Repository | Name | Version |
|------------|------|---------|
| https://library-charts.k8s-at-home.com | common | 4.3.0 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| args[0] | string | `"-m"` |  |
| args[1] | string | `"3"` |  |
| args[2] | string | `"-l"` |  |
| args[3] | string | `"0"` |  |
| args[4] | string | `"-h"` |  |
| args[5] | string | `"localhost"` |  |
| args[6] | string | `"-p"` |  |
| args[7] | string | `"32767"` |  |
| args[8] | string | `"-P"` |  |
| args[9] | string | `"1900"` |  |
| controller.strategy | string | `"Recreate"` |  |
| env.TZ | string | `"UTC"` | Set the container timezone |
| image.pullPolicy | string | `"IfNotPresent"` | image pull policy |
| image.repository | string | `"nolte/upmpdcli"` | image repository |
| image.tag | string | `"v0.9.1"` | image tag |
| persistence.config.enabled | bool | `true` | Enables or disables the persistence item |
| persistence.config.mountPath | string | `"/var/lib/upmpdcli/.config/"` |  |
| persistence.config.name | string | `"upmpdcli-config"` |  |
| persistence.config.type | string | `"configMap"` |  |
| service | object | See values.yaml | Configures service settings for the chart. |
| upmpdcli.config | string | `"# Path to an external file with radio definitions.\nradiolist = /usr/share/upmpdcli/radio_scripts/radiolist.conf\n\n# Local Media Server parameters\nuprcltitle = Local Music\n# Upmpdcli Radios plugin parameters\nupradiostitle = Upmpdcli Radio List\n"` |  |

## Usage

```bash

export UPMPDCLI_NAMESPACE=audio-station

helm upgrade -i upmpdcli . -n $UPMPDCLI_NAMESPACE --create-namespace

helm delete upmpdcli -n $UPMPDCLI_NAMESPACE

kubectl -n $UPMPDCLI_NAMESPACE logs $(kubectl -n $UPMPDCLI_NAMESPACE get pods -l app.kubernetes.io/name=upmpdcli -ojson | jq -r '.items[0].metadata.name') -f
```

## Links

* [nolte/docker_compose-audiostation](https://github.com/nolte/docker_compose-audiostation/blob/master/docker-compose.yml)
