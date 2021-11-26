### Задача 1: Работа с секретами через утилиту kubectl в установленном minikube: </br>
Выполните приведённые ниже команды в консоли, получите вывод команд. Сохраните задачу 1 как справочный материал </br>
Как создать секрет? </br>
openssl genrsa -out cert.key 4096</br>
`openssl req -x509 -new -key cert.key -days 3650 -out cert.crt -subj '/C=RU/ST=Perm/L=Perm/CN=k8s-master1'` </br>
`kubectl create secret tls domain-cert --cert=certs/cert.crt --key=certs/cert.key` </br>
Как просмотреть список секретов?: </br>
`kubectl get secrets` </br>
`kubectl get secret` </br>
![Kuber_get_secrets](https://github.com/murzinvit/screen/blob/b8f6e007bf90a45e56ddc56f63fbdf0dfa0621d4/Kuber_get_secrets.jpg) </br>
Как просмотреть секрет?: </br>
`kubectl get secret domain-cert` </br>
`kubectl describe secret domain-cert` </br>
![Kuber_get_secrets](https://github.com/murzinvit/screen/blob/617ab181d0afe34c74b66d9cea246dc94d1fafe2/Kuber_describe_secret_.jpg) </br>
Как получить информацию в формате YAML и/или JSON?: </br>
`kubectl get secret domain-cert -o yaml` </br>
`kubectl get secret domain-cert -o json` </br>
![get_secret_yaml](https://github.com/murzinvit/screen/blob/99de1e865194e26874a64e217c87236125e7e7c2/Kuber_get_secret_yaml.jpg) </br>
Как выгрузить секрет и сохранить его в файл?: </br>
`kubectl get secrets -o json > secrets.json` </br>
`kubectl get secret domain-cert -o yaml > domain-cert.yml` </br>
![upload_secrets_yam](https://github.com/murzinvit/screen/blob/cc7ed18274f1f06e8c60f70fb5d10d8ced11c2c2/Kuber_upload_secrets_yaml.jpg) </br>
Как удалить секрет?: </br>
`kubectl delete secret domain-cert` </br>
![delete_secrets](https://github.com/murzinvit/screen/blob/08111ed4dd0616d6fdc7b95e0956508af8ea5add/Kuber_delete_secrets.jpg) </br>
Как загрузить секрет из файла?: </br>
`kubectl apply -f domain-cert.yml` </br>
![secret_from_file](https://github.com/murzinvit/screen/blob/5ce359cc14789b517c72ef74024ffe88629d0276/Kuber_upload_secret_from_file.jpg) </br>

### Задача 2 (*): Работа с секретами внутри модуля </br>
Выберите любимый образ контейнера, подключите секреты и проверьте их доступность как в виде переменных окружения, так и в виде примонтированного тома </br>
