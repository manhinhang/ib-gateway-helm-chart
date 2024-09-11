# IB Gateway

# Install

## Use custom values.yaml

myValue.yaml

```yaml
secrets:
  ib-account-id: "123456"
  ib-account-pwd: "123456"
  ib-trading-mode: "paper" # paper or live
ib-gateway:
  healthcheck-api-enabled: true # optional, default is false
```

```bash
helm upgrade --install  ib-gateway charts/ib-gateway -f myValue.yaml
```

## Use inline config

```bash
helm upgrade --install  ib-gateway . --set secrets.ib-account-id=123456 --set secrets.ib-account-pwd=123456 --set secrets.ib-trading-mode=paper 
```

# Port Forward

```bash
kubectl --namespace default port-forward svc/ib-gateway 4002:4002
```
