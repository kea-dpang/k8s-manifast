# k8s-manifest
## 프로젝트 개요
이 저장소는 자사 복지몰 서비스 'DPANG'의 Kubernetes Manifest 파일의 관리 공간입니다. 해당 저장소는 GitOps를 위한 공간으로 Github Actions와 ArgoCD를 통해 CI/CD가 진행됩니다

![GitOps](https://github.com/kea-dpang/k8s-manifast/assets/74820505/7f5f914d-abd3-4764-a5bd-4203eb35727c)

## 담당자
- Wesley
- Eric

## 레포지토리 구조
이 레포지토리는 크게 'backend', 'elasticsearch', 'helm-values' 세 가지 디렉토리로 구성되어 있습니다.

```
├── README.md
├── backend
│   ├── auth-server
│   │   ├── auth-server-deployment.yaml
│   │   └── auth-server-service.yaml
│   ├── eureka-server
│   │   ├── eureka-server-deployment.yaml
│   │   └── eureka-server-service.yaml
│   ├── event-server
│   │   ├── event-server-deployment.yaml
│   │   └── event-server-service.yaml
│   ├── faq-server
│   │   ├── faq-server-deployment.yaml
│   │   └── faq-server-service.yaml
│   ├── gateway-server
│   │   ├── gateway-server-deployment.yaml
│   │   └── gateway-server-service.yaml
│   ├── image-upload-server
│   │   ├── image-upload-server-deployment.yaml
│   │   └── image-upload-server-service.yaml
│   ├── ingress
│   │   └── path-ingress.yaml
│   ├── item-server
│   │   ├── item-server-deployment.yaml
│   │   └── item-server-service.yaml
│   ├── mileage-server
│   │   ├── mileage-server-deployment.yaml
│   │   └── mileage-server-service.yaml
│   ├── notification-server
│   │   ├── notification-server-deployment.yaml
│   │   └── notification-server-service.yaml
│   ├── order-server
│   │   ├── order-server-deployment.yaml
│   │   └── order-server-service.yaml
│   ├── qna-server
│   │   ├── qna-server-deployment.yaml
│   │   └── qna-server-service.yaml
│   ├── seller-server
│   │   ├── seller-server-deployment.yaml
│   │   └── seller-server-service.yaml
│   └── user-server
│       ├── user-server-deployment.yaml
│       └── user-server-service.yaml
├── elasticsearch
│   ├── elasticsearch
│   │   └── elasticsearch-sts.yaml
│   ├── kibana
│   │   ├── kibana-config.yaml
│   │   └── kibana-deploy.yaml
│   └── logstash
│       ├── README.md
│       ├── logstash-config.yaml
│       └── logstash-deploy.yaml
└── helm-values
    ├── loki
    │   └── values.yaml
    └── prometheus
        └── values.yaml
```

### backend
'backend' 디렉토리는 다음과 같은 서브 디렉토리를 포함하고 있습니다. 각 서브 디렉토리는 해당하는 서버의 deployment 및 service yaml 파일을 포함하고 있습니다.

### elasticsearch
'elasticsearch' 디렉토리는 'elasticsearch', 'kibana', 'logstash' 세 가지 서브 디렉토리를 포함하고 있습니다.

### helm-values
'helm-values' 디렉토리는 'loki'와 'prometheus' 두 가지 서브 디렉토리를 포함하고 있고, 각각의 서브 디렉토리는 해당 서비스의 values.yaml 파일을 포함하고 있습니다.

본 프로젝트에서 사용한 helm chart는 다음과 같습니다:
|Chart|Github URL|
|---|---|
|prometheus-community|https://prometheus-community.github.io/helm-charts|
|grafana|https://grafana.github.io/helm-charts|
|cpo|https://kubernetes.github.io/cloud-provider-openstack|
|metrics-server|https://kubernetes-sigs.github.io/metrics-server/|
|ingress-nginx|https://kubernetes.github.io/ingress-nginx|
