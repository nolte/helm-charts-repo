# Mopidy

Simple Helm Chart for running [mopidy](https://github.com/mopidy/mopidy) inside a k8s Cluster.


Copy files to container

```bash

kind load docker-image nolte/mopidy:dirty

helm upgrade -i mopidy-test . --create-namespace 

helm delete mopidy-test

kubectl port-forward svc/mopidy-test 6680

kubectl cp ~/Musik/NeonSchwarZ/Metropolis/B01CPJ7Z6A_\(disc_1\)_01_-_Dies_das_Ananas.mp3  $(kubectl get pods -l app.kubernetes.io/name=mopidy -ojson | jq -r '.items[0].metadata.name'):/var/lib/mopidy/media/01_-_Dies_das_Ananas.mp3


kubectl cp ~/Musik  $(kubectl get pods -l app.kubernetes.io/name=mopidy -ojson | jq -r '.items[0].metadata.name'):/var/lib/mopidy/media/

kubectl logs $(kubectl get pods -l app.kubernetes.io/name=mopidy -ojson | jq -r '.items[0].metadata.name') -f


kubectl exec -ti $(kubectl get pods -l app.kubernetes.io/name=mopidy -ojson | jq -r '.items[0].metadata.name') -- /bin/bash


kubectl exec $(kubectl get pods -l app.kubernetes.io/name=mopidy -ojson | jq -r '.items[0].metadata.name') -- mopidy local scan
```


## Links

* [badaix/snapcast/](https://github.com/badaix/snapcast/) 
* [medoc92/upmpdcli](https://framagit.org/medoc92/upmpdcli)
* [mopidy/mopidy](https://github.com/mopidy/mopidy)
* [nolte/docker_compose-audiostation](https://github.com/nolte/docker_compose-audiostation/blob/master/docker-compose.yml)