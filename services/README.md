#### K8s service type
##### ClusterIP - IP только внутри k8s cluster (default). Автоматически создается в любом случае.
##### NodePort - Определенный порт на всех worker nodes
##### ExternalName - DNS CNAME Record
##### LoadBalancer - только в Cloud Clusters (например AWS, GCP, Azure)
Создаем сервис для deploy 
```
kubectl expose deployment dzanto-deploy --type=ClusterIP --port 80
```
