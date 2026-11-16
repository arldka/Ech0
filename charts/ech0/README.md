# Ech0 Helm chart

[Ech0](https://github.com/lin-snow/Ech0) is a self-hosted, lightweight personal microblog (timeline) platform.

## Install

```bash
helm repo add ech0 https://lin-snow.github.io/Ech0
helm repo update
helm install ech0 ech0/ech0 --set config.JWT_SECRET="$(openssl rand -hex 32)"
```

## Configuration

| Key | Description | Default |
|-----|-------------|---------|
| `replicaCount` | Number of replicas | `1` |
| `image.repository` | Container image | `sn0wl1n/ech0` |
| `image.tag` | Image tag (defaults to chart `appVersion`) | `""` |
| `service.type` / `service.httpPort` | Service type and port | `ClusterIP` / `6277` |
| `ingress.*` | Ingress configuration | disabled |
| `httpRoute.*` | Gateway API HTTPRoute configuration | disabled |
| `config.JWT_SECRET` | JWT signing secret. **Change this in production.** | `Hello Echos` |
| `persistence.*` | PVC for `/app/data` (SQLite + uploads) | see `values.yaml` |
| `extraEnv` | Extra environment variables | `[]` |
| `resources`, `autoscaling`, `nodeSelector`, `tolerations`, `affinity` | Standard scheduling/scaling knobs | see `values.yaml` |

See [`values.yaml`](values.yaml) for the complete list. Other server settings are documented in
[docs/usage/configuration.md](https://github.com/lin-snow/Ech0/blob/main/docs/usage/configuration.md).

## Upgrade

```bash
helm repo update
helm upgrade ech0 ech0/ech0
```

## License

AGPL-3.0-only.
