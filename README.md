# helm-charts-repo

Mono Repo for a set of Helm Charts, used from Private HomeLab Clusters.

## Chart Readme

```sh
helm-docs -t ../../README.md.gotmpl -t README.md.gotmpl
```

## Chart Testing

```sh
export CHART_TYPE=stable
export CHART=snapcast-server

task chart:ct-lint
```