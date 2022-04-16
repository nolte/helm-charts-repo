# snapcast-server

![Version: 0.1.2](https://img.shields.io/badge/Version-0.1.2-informational?style=flat-square) ![AppVersion: v0.2.6](https://img.shields.io/badge/AppVersion-v0.2.6-informational?style=flat-square)

Multi Room Music Server

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
| args | list | `["-c","/tmp/snapserver/snapserver.conf"]` | Override the args for the default container |
| controller.strategy | string | `"Recreate"` |  |
| env.TZ | string | `"UTC"` | Set the container timezone |
| image.pullPolicy | string | `"IfNotPresent"` | image pull policy |
| image.repository | string | `"nolte/snapcast-server"` | image repository |
| image.tag | string | `"v0.26.0"` | image tag |
| persistence.snapserver-config.enabled | bool | `true` | Enables or disables the persistence item |
| persistence.snapserver-config.mountPath | string | `"/tmp/snapserver/"` |  |
| persistence.snapserver-config.name | string | `"snapserver-config"` |  |
| persistence.snapserver-config.type | string | `"configMap"` |  |
| service | object | See values.yaml | Configures service settings for the chart. |
| snapcastServer.config | string | `"[http]\ndoc_root = /usr/share/snapserver/snapweb\n\n[stream]\nstream = tcp://0.0.0.0:4953?name=mopidy_tcp\n"` |  |

```sh
export SNAPCAST_NAMESPACE=audio-station
 helm upgrade -i station . -n $SNAPCAST_NAMESPACE --create-namespace

 helm delete station -n -n $SNAPCAST_NAMESPACE
```