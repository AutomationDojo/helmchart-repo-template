# Usage

## Installing the Chart

```bash
helm repo add CHART_NAME https://GITHUB_OWNER.github.io/CHART_NAME
helm repo update
helm install CHART_NAME CHART_NAME/CHART_NAME -f values.yaml
```

## Upgrading

```bash
helm repo update
helm upgrade CHART_NAME CHART_NAME/CHART_NAME -f values.yaml
```

## Uninstalling

```bash
helm uninstall CHART_NAME
```
