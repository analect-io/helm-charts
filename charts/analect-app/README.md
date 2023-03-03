# analect-app

![Version: 0.1.68](https://img.shields.io/badge/Version-0.1.68-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.0.0](https://img.shields.io/badge/AppVersion-1.0.0-informational?style=flat-square)

Helm Charts for default Analect Application

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| analect-io | info@analect.com |  |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| ServiceAccount | object | `{"annotations":{},"enabled":true}` | ServiceAccount A service account provides an identity for processes that run in a Pod, about more: https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/ |
| ServiceAccount.annotations | object | `{}` | Annotations to add to the service account |
| ServiceAccount.enabled | bool | `true` | Specifies whether a service account should be created |
| affinity | object | `{}` |  |
| argoRollouts | object | `{"enabled":true,"revisionHistoryLimit":5,"strategy":{"dynamicStableScale":true,"steps":[{"setWeight":5},{"pause":{"duration":"10s"}},{"setWeight":20},{"pause":{"duration":"10s"}},{"setWeight":40},{"pause":{"duration":"10s"}},{"setWeight":60},{"pause":{"duration":"10s"}},{"setWeight":80},{"pause":{"duration":"10s"}}]}}` | ResourceQuota provides constraints that limit aggregate resource consumption per namespace |
| argoRollouts.enabled | bool | `true` | Specifies whether a resource quota should be created |
| autoscaling | object | `{"enabled":true,"maxReplicas":4,"minReplicas":2,"targetCPUUtilizationPercentage":70}` | autoscaling is the main object of autoscaling |
| autoscaling.enabled | bool | `true` | enabled is the flag to sinalize this funcionality is enabled |
| autoscaling.maxReplicas | int | `4` | maxReplicas is the number of maximum scaling pods |
| autoscaling.minReplicas | int | `2` | minReplicas is the number of mim pods to be running |
| autoscaling.targetCPUUtilizationPercentage | int | `70` | targetCPUUtilizationPercentage is the percentage of CPU utilization do Scaling |
| cluster | string | `"cluster.local"` | cluster Set Cluster Name |
| container.port | int | `8080` | port is the port your application runs under |
| env | list | `[]` |  |
| envFrom | list | `[]` |  |
| image.pullPolicy | string | `"IfNotPresent"` | pullPolicy is the prop to setup the behavior of pull police. options is: IfNotPresent \| allways |
| image.repository | string | `""` | repository: is the registry of your application ex:556684128444.dkr.ecr.us-east-1.amazonaws.com/YOU-APP-ECR-REPO-NAME if empty this helm will auto generate the image using aws.registry/values.name:values.image.tag |
| image.tag | string | `"latest"` | especify the tag of your image to deploy |
| imagePullSecrets.name | string | `"ghcr-secret"` |  |
| ingress | object | `{"enabled":true}` | ingress Ingress exposes HTTP and HTTPS routes from outside the cluster to services within the cluster. |
| ingress.enabled | bool | `true` | enable ingress |
| istioInjection | object | `{"enabled":true}` | istioInjection enable istio injection |
| livenessProbe.httpGet.path | string | `"/health-check/liveness"` |  |
| livenessProbe.httpGet.port | int | `8080` |  |
| livenessProbe.initialDelaySeconds | int | `15` |  |
| livenessProbe.periodSeconds | int | `10` |  |
| migration.enabled | bool | `false` | enable liquibase migration |
| name | string | `""` | name is the github repository name of this application deploy |
| network | object | `{"domain":"analect.com","service":{"port":80,"type":"ClusterIP"}}` | Network |
| network.domain | string | `"analect.com"` | domain Set Default Domain |
| network.service | object | `{"port":80,"type":"ClusterIP"}` | service An abstract way to expose an application running on a set of Pods as a network service. |
| network.service.port | int | `80` | port is the port your application runs under |
| nodeSelector | object | `{}` |  |
| peerAuthentication | object | `{"enabled":true}` | PeerAuthentication defines how traffic will be tunneled (or not) to the sidecar. |
| peerAuthentication.enabled | bool | `true` | enable PeerAuthentication |
| probe.enabled | bool | `true` |  |
| quota | object | `{"enabled":true,"resources":{"hard":{"limits.cpu":"2","limits.memory":"2Gi","requests.cpu":"1","requests.memory":"1Gi"}}}` | ResourceQuota provides constraints that limit aggregate resource consumption per namespace |
| quota.enabled | bool | `true` | Specifies whether a resource quota should be created |
| readinessProbe.httpGet.path | string | `"/health-check/readiness"` |  |
| readinessProbe.httpGet.port | int | `8080` |  |
| readinessProbe.initialDelaySeconds | int | `15` |  |
| readinessProbe.periodSeconds | int | `10` |  |
| resources.limits.cpu | string | `"100m"` |  |
| resources.limits.memory | string | `"128Mi"` |  |
| resources.requests.cpu | string | `"50m"` |  |
| resources.requests.memory | string | `"64Mi"` |  |
| sealedSecrets.enabled | bool | `true` |  |
| sealedSecrets.encryptedData | string | `"AgBgz4x/fWN2X0zvKx2OLyUYY8mlYtk0Ts18mROOHmT4rGWZK2pgdO7evsKCvxFaMvD7gzqgXEGu2fhExWF+XwijTD6nKRlSmwc9Odn9Xelo+xdppUn+lLiNseREQoXMUa/WHwPhsnZUUFLXyHFa72keoOqFsCKqtaEs8E+qnPfXcGBexV1NEIJfbJYJcUdHKNs/VzsQ6Cccr1odz6rlsDZn8NAi8FkPh0w7e4EELvhiqwZuTdzhXrNeNxemd2KmVAUZ+8rsJtpj1sp7qdVNnHDW6l+tGoDHnV88DBpoi9XuX54gddhYu15HeNagiwC6HPFs/aaWa/6FAIDcKgQWI7YKs4JrjNd0glpn3Nwh04fs6wLFD/hbjkn/S/ny0Kj/SS/tyX4eeDSNQlvHtcY6SlfJ3ujTw4hH0yj2cl0eJfFWxHpic6X5uxp3guhhDHZMtXNqlNyd4ezLMOO60AI0PKWByLUnQyql82xm5e2XJ/+xQp2rfDvezbcgGMbCfG3iJEfVTddj6nkE78TIFPleQrNGsXq0zgP34OwziT6PK97+DcXuJhl0grmPQQ8wB/beJ1ftpUdpdm38upPXVoEq8KNiTAvePZ3m5HUujDoHGi9h+giJpIAgYsqd7d2SHpGoGDts8GTo7z5EIwlzGCZvHNYg/09jT/Cl+J0tQGSwJgpYajjhWXEiiVKXxgZo3EfWA+i6O7mhjyvXPIOwNHRne6BAp0TbwSNkDXYr2GL+vMWurhvkTEqeWkRahpt/ACkGiLGGmdADh0t3X5ADSmWEKiy13b+Pfsif3HW8VwWtIHP+MNSSK3/Uj4baqhUKpGP2h0H2YEO939oHq3aeiKwCKJXRI5SfKFzO5Qxv90O94i2DB5lidE5hEL4EXAUcCQQ3mEmn4Wulb39XaL5m/vQMBg=="` |  |
| tolerations | list | `[]` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.7.0](https://github.com/norwoodj/helm-docs/releases/v1.7.0)
