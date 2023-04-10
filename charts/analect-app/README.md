# analect-app

![Version: 0.1.74](https://img.shields.io/badge/Version-0.1.74-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.0.0](https://img.shields.io/badge/AppVersion-1.0.0-informational?style=flat-square)

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
| deployment | object | `{"enabled":false}` | deployment Disabled Deployment |
| deployment.enabled | bool | `false` | enabled default false |
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
| namespace.enabled | bool | `true` |  |
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
| sealedSecrets.encryptedData | string | `"AgAD3JXWoNYTIoLXEYYyBchFBGj3eOvaOmOm5MThH7/mz9OoD1IwojloaTiD2tj+HxcRRq+N8N8FnixafAKsWB+2rFY3sBUZlVym/bcZZekw4ba/6pxE8x6gdnbKxeQgyqCPRp3R+XGgHm/1sH5ZFyKqCOOqO32gs8TXCQKUjPuT6oJA9WQbdasMxr7sdu/hXF6RsBNLebhT03mJl5GNcJn6Hy3rY4ZahvDckiCCziKLhl7ThLTDOlU5lD7HOO7sUXjqS69A2O/K4Uen6br4J/x7WyHMzY7YvPtqlDq9kVKtSls78BcNjxp1uwYynGoEV3WIKuwJZL47cV5L6caFvE/SQDt0kVfWLeMttLuAERCsvzG+SpxjKc2tL2zB3ExHO8cMcIRT/X5DM4Zoo9ZC1CF7kOw+YWYSUrvtUFlTxpklQXKi2m8x/mNWhtB3ZAUPfepz8e3Uvo4+cKgYQSehSWKlF6KcY5VSd72vKgSZJBLebfs5+hcrM7sg4+AphkeU2ek3pYRKEdDHnmU3LPSYobzEOCSiqy03uyZG+LiF7mnj1lt06hdZkzelqPmnHSMGJ1tWGzEi0QeRthaQ977zBDsqy8S+nfkH2RWBYaabLrEMFoiTPwbE+ejAt0MrJyLBTNiJP+lCgRGnWcU75bcRkHIRs0S69ytastuFuf05De6fvxIPd/ATy4AqPdAbFKzWpBgwJno+TUuy97ctc/jPTs1M6jwmxrMj8P87RZbxABv1TbAehCqfvUKyhK7vgOv//phe+Gp+JxqQ66zsqOxxN6Xp+4XkQwRCSGmmnr+eQrNEhkcfR+39beBIv89L9pF9dqKMx1LfjGmrOVgdVy8cOEaHe93Zr2bAGXCVY6dUOi0KpmAqWlYqHPT9C6XKhmzniRk4TTHJrEMmutKh2Y+oOg=="` |  |
| tolerations | list | `[]` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.7.0](https://github.com/norwoodj/helm-docs/releases/v1.7.0)
