Деплоймент состоит из подов(в поде бежит контейнер)

список деполйментс
kubectl get deploy

создаем деплой (можно писать кратко deploy)
kubectl create deployment dzanto-deploy --image nginx:latest
при создании деплоя создается pod

описание деплоя
kubectl describe deployments dzanto-deploy

Scaling: масштабирование, указываем количество реплик
kubectl scale deployment dzanto-deploy --replicas 2
при создании масштабирования создается replica set
kubectl get rs

AutoScaling: автомасштабирование
kubectl autoscale deployment dzanto-deploy --min=1 --max=3 --cpu-percent=80
при создании автомасштабирования создается объект hpa отображающий текущую нагрузку и кол-во текущих подов
hpa - horizontal pod autoscaler
kubectl get hpa

история версий развертывания
kubectl rollout history deployment/dzanto-deploy
kubectl rollout status deployment/dzanto-deploy

установить новый образ в контейнер:
kubectl set image deployment/dzanto-deploy nginx=nginx:new_version1 --record
после выполнения в истории добавится запись с номером

вернуться на предыдушую версию образа
kubectl rollout undo deployment/dzanto-dep
или указать точный номер из истории:
kubectl rollout undo deployment/dzanto-dep --to-revision=3

если в версия образа указана как latest, можно сделать просто рестарт deployment, и образ обновиться на latest версию
kubectl rollout restart deployment/dzanto-deploy

для запуска deployment из манифест файла my-deployment.yaml выполняем команду:
kubectl apply -f my-deployment.yaml

пример файла my-deployment.yaml
###
apiVersion: apps/v1
kind: Deployment
metadata:
  # имя deployment
  name: my-web-deploy
  labels:
    app: my-k8s-app
spec:
  # указываем количество реплик
  replicas: 2
  selector:
    # указываем с какими pods этот deploy будет работать project: kgb
    matchLabels:
      project: kgb
  #далее описание pod
  template:
    metadata:
      labels: 
        #у пода указываем label project: kgb
        project: kgb
    spec:
    # спецификация пода
      containers:
      - name: kgb-web
        image: nginx:latest
        ports:
        - containerPort: 80 
# добавялем autoscaler, можно в этот же файл через --- или в отдельный файл
---
apiVersion: autoscaling/v2beta1
kind: HorizontalPodAutoscaler
metadata:
  name: my-autoscaling
spec:
  # описываем, что будем автоскейлить
  scaleTargetRef:
    apiVersion: apps/v2beta1v1
    kind: Deployment
    # имя my-web-deploy берем из описания deployment
    name: my-web-deploy
  minReplicas: 2
  maxReplicas: 4
  # в зависимости от каких ресурсов масштабировать
  metrics:
  - type: Resource
    resource:
      name: cpu
      targetAverageUtilization: 70
  - type: Resource
    resource:
      name: memory
      targetAverageUtilization: 80
