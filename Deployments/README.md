### Deployments
Деплоймент состоит из подов(в поде бежит контейнер)

Просмотр списока деполйментс
```
kubectl get deploy
```
Создаем деплой (можно писать кратко deploy)
```
kubectl create deployment dzanto-deploy --image nginx:latest
```
при создании деплоя создается pod

Просмотр описания deployment
```
kubectl describe deployments dzanto-deploy
```
#### Scaling: масштабирование, указываем количество реплик
```
kubectl scale deployment dzanto-deploy --replicas 2
```
при создании масштабирования создается replica set
```
kubectl get rs
```
#### AutoScaling: автомасштабирование
```
kubectl autoscale deployment dzanto-deploy --min=1 --max=3 --cpu-percent=80
```
##### hpa - horizontal pod autoscaler
при создании автомасштабирования создается объект hpa отображающий текущую нагрузку и кол-во текущих подов
```
kubectl get hpa
```
#### Обновление образов и история версий развертывания
Просмотр истории версий образов:
```
kubectl rollout history deployment/dzanto-deploy
kubectl rollout status deployment/dzanto-deploy
```
Установка нового образа в контейнер:
```
kubectl set image deployment/dzanto-deploy nginx=nginx:latest --record
```
после установки нового образа в истории добавится запись об обновлении с номером 
Что бы вернуться на предыдушую версию образа используем undo или указываем точный номер из history:
```
kubectl rollout undo deployment/dzanto-dep
kubectl rollout undo deployment/dzanto-dep --to-revision=3
```
Если версия образа указана как latest, можно сделать просто рестарт deployment, и образ обновиться на latest версию
```
kubectl rollout restart deployment/dzanto-deploy
```
### Запуска deployment из манифест файла my-deployment.yaml
Запуск и удаление deployment с помощью yaml файла:
```
kubectl apply -f my-deployment.yaml
kubectl delete -f my-deployment.yaml
```
пример файла my-deployment.yaml
