# IB Gateway


## Usage

[Helm](https://helm.sh) must be installed to use the charts.  Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

  helm repo add ib-gateway https://manhinhang.github.io/ib-gateway-helm-chart/

If you had already added this repo earlier, run `helm repo update` to retrieve
the latest versions of the packages.  You can then run `helm search repo
ib-gateway` to see the charts.


### Use custom values.yaml

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
helm upgrade --install  ib-gateway ib-gateway/ib-gateway-f myValue.yaml
```

### Use inline config

```bash
IB_ACCOUNT_ID=123456
IB_ACCOUNT_PWD=123456
IB_TRADING_MODE=paper

helm upgrade --install  ib-gateway ib-gateway/ib-gateway \
--set secrets.ib-account-id=${IB_ACCOUNT_ID} \
--set secrets.ib-account-pwd=${IB_ACCOUNT_PWD} \
--set secrets.ib-trading-mode=${IB_TRADING_MODE} 
```

## Port Forward

```bash
kubectl --namespace default port-forward svc/ib-gateway 4002:4002
```
