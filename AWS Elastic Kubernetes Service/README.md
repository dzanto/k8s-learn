Необходимо установить:
  awscli - для аутинтефикации и запуска команд AWS (в amazon linux он уже установлен) 
  kubectl - для управления k8s кластера
  eksctl - для создания k8s кластера в Amazon Elastic Kubernetes Service

Установить creditional для пользователя AWS
  export AWS_ACCESS_KEY_ID=AKIAYV3OF6JKOLFTW5LA
  export AWS_SECRET_ACCESS_KEY=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
  export AWS_DEFAULT_REGION=eu-north-1
  
Создание кластера из манифест файла (например cluster.yaml):
Создаем файл cluster.yaml с содержимым:
###
apiVersion: eksctl.io/v1alpha5
kind: ClusterConfig

metadata:
  name: dzanto-cluster
  region: eu-north-1

nodeGroups:
  - name: ng-1
    instanceType: t3.micro
    desiredCapacity: 2 #желаемое емкость(количество) инстансов
  - name: ng-2
    instanceType: t3.micro
    desiredCapacity: 2
###

Создаем кластер:
  eksctl create cluster -f cluster.yaml
Удаляем кластер:
  eksctl delete cluster -f cluster.yaml
  
Дополнительные команды:
kubectl version
kubectl version --client
kubectl cluster-info
kubectl get nodes - список нодов в кластере

eksctl version

Место хранения конфигурации kubectl с k8s cluster
~/.kube/config