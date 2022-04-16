# mopidy

![Version: 0.1.2](https://img.shields.io/badge/Version-0.1.2-informational?style=flat-square) ![AppVersion: v0.0.1](https://img.shields.io/badge/AppVersion-v0.0.1-informational?style=flat-square)

Hackable Music Server

**Homepage:** <https://github.com/nolte/helm-charts-repo/tree/master/charts/stable/mopidy>

## Source Code

* <https://github.com/mopidy/mopidy>
* <https://mopidy.com/>
* <https://github.com/wernight/docker-mopidy>

## Requirements

Kubernetes: `>=1.16.0-0`

| Repository | Name | Version |
|------------|------|---------|
| https://library-charts.k8s-at-home.com | common | 4.3.0 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| controller.strategy | string | `"Recreate"` |  |
| env.TZ | string | `"UTC"` | Set the container timezone |
| image.pullPolicy | string | `"IfNotPresent"` | image pull policy |
| image.repository | string | `"nolte/mopidy"` | image repository |
| image.tag | string | `"v3.2.0-4"` | image tag |
| mopidy.config | string | `"[local]\ndata_dir = /var/lib/mopidy/local\nmedia_dir = /var/lib/mopidy/media\n\n[http]\nhostname = 0.0.0.0\n\n[mpd]\nhostname = 0.0.0.0\nenabled = true\nport = 6600\npassword =\nmax_connections = 20\nconnection_timeout = 60\nzeroconf = Mopidy MPD server on $hostname\ncommand_blacklist = listall,listallinfo\ndefault_playlist_scheme = m3u\n\n[spotify]\nenabled = {{.Values.mopidy.spotify.enabled}}\n\n[audio]\noutput = audioresample ! audioconvert ! audio/x-raw,rate=48000,channels=2,format=S16LE ! wavenc ! tcpclientsink host={{.Values.mopidy.snapcast.server.host}}\n"` |  |
| mopidy.snapcast.server.host | string | `"snapcast-server"` |  |
| mopidy.spotify.enabled | bool | `false` |  |
| persistence.cache.enabled | bool | `true` | Enables or disables the persistence item |
| persistence.cache.mountPath | string | `"/var/lib/mopidy/.cache"` |  |
| persistence.cache.type | string | `"emptyDir"` |  |
| persistence.config.enabled | bool | `true` | Enables or disables the persistence item |
| persistence.config.mountPath | string | `"/var/lib/mopidy/.config/mopidy"` |  |
| persistence.config.name | string | `"mopidy-config"` |  |
| persistence.config.type | string | `"configMap"` |  |
| persistence.local.enabled | bool | `true` | Enables or disables the persistence item |
| persistence.local.mountPath | string | `"/var/lib/mopidy/local"` |  |
| persistence.local.type | string | `"emptyDir"` |  |
| persistence.media | object | See below | Default persistence for configuration files. |
| persistence.media.enabled | bool | `true` | Enables or disables the persistence item |
| persistence.playlists.enabled | bool | `true` | Enables or disables the persistence item |
| persistence.playlists.mountPath | string | `"/var/lib/mopidy/playlists"` |  |
| persistence.playlists.type | string | `"emptyDir"` |  |
| podSecurityContext.fsGroup | int | `29` |  |
| podSecurityContext.runAsGroup | int | `29` |  |
| podSecurityContext.runAsUser | int | `105` |  |
| securityContext.privileged | bool | `true` |  |
| service | object | See values.yaml | Configures service settings for the chart. |

## Usage

```sh
kind load docker-image nolte/mopidy:dirty
```

```bash

export MOPIDY_NAMESPACE=audio-station

helm upgrade -i mopidy . -n $MOPIDY_NAMESPACE --create-namespace

helm delete mopidy -n -n $MOPIDY_NAMESPACE

kubectl port-forward -n $MOPIDY_NAMESPACE  svc/mopidy 6680

kubectl -n $MOPIDY_NAMESPACE logs $(kubectl -n $MOPIDY_NAMESPACE get pods -l app.kubernetes.io/name=mopidy -ojson | jq -r '.items[0].metadata.name') -f
```

Copy files to container

```sh
kubectl -n $MOPIDY_NAMESPACE cp ~/Musik  $(kubectl get pods -l app.kubernetes.io/name=mopidy -n $MOPIDY_NAMESPACE  -ojson | jq -r '.items[0].metadata.name'):/var/lib/mopidy/media/

kubectl -n $MOPIDY_NAMESPACE exec $(kubectl get pods -l app.kubernetes.io/name=mopidy -n $MOPIDY_NAMESPACE  -ojson | jq -r '.items[0].metadata.name') -- mopidy local scan
```

## Links

* [badaix/snapcast/](https://github.com/badaix/snapcast/)
* [medoc92/upmpdcli](https://framagit.org/medoc92/upmpdcli)
* [mopidy/mopidy](https://github.com/mopidy/mopidy)
* [nolte/docker_compose-audiostation](https://github.com/nolte/docker_compose-audiostation/blob/master/docker-compose.yml)

