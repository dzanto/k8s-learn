### PODs создание и управление
После запуска кластера и нодов можем запустить поды с контейнерами
Запускаем POD с именем hello
```
kubectl run hello --image=nginx --port=80
```
просмотр списка запущенных подов
```
kubectl get pods
```
удалить pod с именем hello
```
kubectl delete pods hello
```
получить описание pod
```
kubectl describe pods hello
```
запустить команду date на поде hello и запустить shell интерактивно:
```
kubectl exec hello -- date
kubectl exec -it hello -- sh
```
Просмотр лога пода
```
kubectl logs hello
```
перенаправить порт пода на порт хоста с которого запускается команда
```
kubectl port-forward hello 7777:80
```
POD можно запустить из манифест файла (пример my-web.yaml)
запуск и удаление POD из yaml файла
```
kubectl apply -f my-web.yaml
kubectl delete -f my-web.yaml
```
в yaml файле можно менять image без дестроя POD, после чего еше раз запустить apply и образ обновится
в yaml файле можно описать несколько контейнеров (пример my-duble-pod.yaml)
