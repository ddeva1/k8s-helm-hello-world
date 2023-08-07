# k8s-helm-hello-world

This repository contains 1 nginx chart that is used to deploy helloworld to kubernetes.

## Validate Chart

```
helm lint ./k8s-helm-hello-world
```
```
Output
==> Linting ./k8s-helm-hello-world
[INFO] Chart.yaml: icon is recommended

1 chart(s) linted, 0 chart(s) failed
```

## Check and validate output of the chart in rendered templates

```
helm template ./k8s-helm-hello-world
```
```
Output
---
# Source: nginx-chart/templates/configmap.yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: release-name-index-html-configmap
  namespace: default
data:
  index.html: |
    <html>
    <h1>Welcome</h1>
    </br>
    <h1>Hi! I got deployed in dev Environment using Helm Chart </h1>
    </html
---
# Source: nginx-chart/templates/service.yaml
apiVersion: v1
kind: Service
metadata:
  name: release-name-service
spec:
  selector:
    app.kubernetes.io/instance: release-name
  type: ClusterIP
  ports:
    - protocol: TCP
      port: 80
      targetPort: 9000
---
```

## Installing
Install helloworld chart

helm install --name myfirstapp chartmuseum/myfirstapp
