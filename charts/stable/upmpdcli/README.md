# upmpdcli



This chart will be a part of the [docker_compose-audiostation](https://github.com/nolte/docker_compose-audiostation) migration.

**WIP**
## Usefull commands

```bash

export UPMPDCLI_NAMESPACE=audio-station

helm upgrade -i upmpdcli . -n $UPMPDCLI_NAMESPACE --create-namespace 

helm delete upmpdcli -n $UPMPDCLI_NAMESPACE

kubectl -n $UPMPDCLI_NAMESPACE logs $(kubectl -n $UPMPDCLI_NAMESPACE get pods -l app.kubernetes.io/name=upmpdcli -ojson | jq -r '.items[0].metadata.name') -f
```

## Links

* [nolte/docker_compose-audiostation](https://github.com/nolte/docker_compose-audiostation/blob/master/docker-compose.yml)