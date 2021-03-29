### Поднятие Кластера в AWS Elastic Kubernetes Service
Необходимо установить:
- awscli - для аутинтефикации и запуска команд AWS (в amazon linux он уже установлен) 
- kubectl - для управления k8s кластера
- eksctl - для создания k8s кластера в Amazon Elastic Kubernetes Service

Установить creditional для пользователя AWS:
```
export AWS_ACCESS_KEY_ID=AKIAYV
export AWS_SECRET_ACCESS_KEY=9VBe3
export AWS_DEFAULT_REGION=eu-north-1
```
  
### Создание кластера из манифест файла
Создаем yaml файл (например cluster.yaml)

Создаем кластер:
```
eksctl create cluster -f cluster.yaml
```
Удаляем кластер:
```
eksctl delete cluster -f cluster.yaml
```
  
Дополнительные команды:
```
kubectl version
kubectl version --client
kubectl cluster-info
kubectl get nodes
eksctl version
```
Место хранения конфигурации kubectl с k8s cluster
~/.kube/config
