После запуска кластера и нодов можем запустить поды с контейнерами
Запускаем POD с именем hello
kubectl run hello --image=nginx --port=80

просмотр запущенных подов
kubectl get pods

удалить pod с именем hello
kubectl delete pods hello

получить описание pod
kubectl describe pods hello

запустить команду date на поде hello
kubectl exec hello -- date
запустить шелл интерактивно
kubectl exec -it hello -- sh

посмотрел логи пода
kubectl logs hello

перенаправить порт пода на порт хоста с которого запускается команда
kubectl port-forward hello 7777:80

создаем манифест yaml файл с описанием пода, например my-web.yaml

запуск пода из yaml файла
kubectl apply -f my-web.yaml

удалить под из yaml файла
kubectl delete -f my-web.yaml

в yaml файле можно менять image без дестроя ПОДА, после чего еше раз запустить apply и образ обновится

в yaml файле можно описать несколько контейнеров 
