###### K8s service type
Cluster IP - IP только внутри k8s cluster (default). Автоматически создается в любом случае.
NodePort - Определенный порт на всех worker nodes
ExternalName - DNS CNAME Record
LoadBalancer - только в Cloud Clusters (например AWS, GCP, Azure)
