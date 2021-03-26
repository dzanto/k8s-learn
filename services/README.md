#### K8s service types:
- ClusterIP - IP только внутри k8s cluster (default). Автоматически создается в любом случае.
- NodePort - Определенный порт на всех worker nodes
- ExternalName - DNS CNAME Record
- LoadBalancer - только в Cloud Clusters (например AWS, GCP, Azure)

#### Создаем сервис для deploy c ClusterIP
```
kubectl expose deployment my-deploy-name --type=ClusterIP --port 80
```
Посомтреть текущие сервисы: будет показан тип сервиса и clusterIP, при обращении к этому IP будет доступ к приложению по типу лоадбалансера. Обратиться можно только по внутреннему ClusterIP
```
kubectl get services
или
kubectl get svc
```
Удалить сервис:
```
kubectl delete svc my-deploy-name
```
#### Создаем сервис для deploy с NodePort
```
kubectl expose deployment my-deploy-name --type=NodePort --port 80
```
В текуших сервисах будет отображен порт, а в описании нодов можно найти ExternalIP, по ним можно обратиться к приложению извне
```
kubectl get services
kubectl describe nodes | grep ExternalIP
```
Удалить сервис:
```
kubectl delete svc my-deploy-name
```
#### LoadBalancer servise
```
kubectl expose deployment my-deploy-name --type=LoadBalancer --port 80
```
в списке сервисов будет доступен servise with ExternalIP, при обращении к которому будет работать LoadBalancer
```
kubectl get svc
```
### Запуск сервисов из манифест файлов
