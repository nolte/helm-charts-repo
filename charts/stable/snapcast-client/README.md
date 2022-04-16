# snapcast-client

![Version: 0.1.2](https://img.shields.io/badge/Version-0.1.2-informational?style=flat-square) ![AppVersion: v0.2.6](https://img.shields.io/badge/AppVersion-v0.2.6-informational?style=flat-square)

Multi Room Music Client

**Homepage:** <https://github.com/nolte/helm-charts-repo/tree/master/charts/stable/snapcast-server>

## Source Code

* <https://github.com/badaix/snapcast>
* <https://github.com/nolte/docker-snapcast>

## Requirements

Kubernetes: `>=1.16.0-0`

| Repository | Name | Version |
|------------|------|---------|
| https://library-charts.k8s-at-home.com | common | 4.3.0 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| args | list | `["-h","rpi-snapcast-server-public"]` | Override the command(s) for the default container |
| controller.strategy | string | `"Recreate"` |  |
| env.TZ | string | `"UTC"` | Set the container timezone |
| image.pullPolicy | string | `"IfNotPresent"` | image pull policy |
| image.repository | string | `"nolte/snapcast-client"` | image repository |
| image.tag | string | `"v0.26.0"` | image tag |
| persistence.hostpathmounts-data.enabled | bool | `true` |  |
| persistence.hostpathmounts-data.hostPath | string | `"/dev/snd"` |  |
| persistence.hostpathmounts-data.mountPath | string | `"/dev/snd"` |  |
| persistence.hostpathmounts-data.type | string | `"hostPath"` |  |
| securityContext.privileged | bool | `true` |  |
| service | object | See values.yaml | Configures service settings for the chart. |

## Usage

```sh
export SNAPCAST_NAMESPACE=audio-station
 helm upgrade -i station . -n $SNAPCAST_NAMESPACE --create-namespace

 helm delete station -n -n $SNAPCAST_NAMESPACE
```