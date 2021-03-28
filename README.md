# Kubernetes

### Основные объекты K8s
- pod (в переводе - стручок) - объект в котором работает один или несколько containers
- deployment - сет одинаковых pods, нужен для Auto Scaling и для обновления container image, держит минимальное кол-во работающих pods
- service - предоставляет доступ к deployment через:
  + ClusterIP
  + NodePort
  + LoadBalancer
  + ExternalName
- Nodes - сервера где все это работает
- Cluster - логическое объединение Nodes
