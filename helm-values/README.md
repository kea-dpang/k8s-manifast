# Helm Chart
본 프로젝트에서 사용한 helm chart는 다음과 같습니다:
|Chart|URL|
|---|---|
|cpo|https://kubernetes.github.io/cloud-provider-openstack|
|prometheus-community|https://prometheus-community.github.io/helm-charts|
|grafana|https://grafana.github.io/helm-charts|
|metrics-server|https://kubernetes-sigs.github.io/metrics-server/|
|ingress-nginx|https://kubernetes.github.io/ingress-nginx|

## Usage
본 프로젝트에서 사용한 helm chart, values를 사용하기 위한 명령은 다음과 같습니다.

### Cloud Provider Openstack
```bash
helm repo add cpo https://kubernetes.github.io/cloud-provider-openstack
helm install cinder-csi cpo/openstack-cinder-csi \
    --version 2.3.0 \
    --set secret.enabled=true \
    --set secret.name=cloud-config \
    --namespace kube-system
```

### Prometheus, Grafana
```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm upgrade --install prometheus prometheus-community/kube-prometheus-stack -f values.yaml -n kube-system
```

### Promtail
```bash
helm repo add grafana https://grafana.github.io/helm-charts
helm upgrade --install promtail grafana/promtail -n loki --create-namespace
```

### Loki
```bash
helm --kubeconfig=$KUBE_CONFIG upgrade --install --namespace=loki logging grafana/loki -f values.yaml --set loki.auth_enabled=false
```

### Metrics-server
```bash
helm repo add metrics-server https://kubernetes-sigs.github.io/metrics-server/
helm upgrade --install metrics-server metrics-server/metrics-server --set hostNetwork.enabled=true --set containerPort=4443
```

### Ingress-nginx
```bash
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm --kubeconfig=$KUBE_CONFIG upgrade --install ingress-nginx ingress-nginx/ingress-nginx \
    --version 4.2.5 \
    --set controller.hostNetwork=true \
    --namespace ingress-nginx --create-namespace
```
