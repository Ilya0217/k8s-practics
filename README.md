# k8s-practics

# Задача #1

- **1) Создай Pod с именем "demo" из образа "nginx" последней версии.**
- **2) Добавь в него init контейнер с именем "setup" и образом "busybox".**
- **3) Настрой init контейнер таким образом, чтобы он создавал файл “index.html” и писал в него строку "hello world". Этот файл, должен располагаться в каталоге, который nginx будет раздавать по умолчанию (/usr/share/nginx/html).**

## Документация, которая поможет:
- https://kubernetes.io/docs/concepts/workloads/pods/init-containers/
- https://kubernetes.io/docs/concepts/storage/volumes/#emptydir
- https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/

# Задача #2

- **1) Создай Persistent Volume типа hostPath (размер 500Мб, тип доступа RWO)**
- **2) Создай соотвествующий Persistent Volume Claim для него**
- **3) Создай Pod, который каждые десять секунд пишет текущее время в файл index.html через PVC**
- **4) Опционально: запусти Pod с nginx, который сможет раздать этот index.html (так как RWO оба пода должны быть запущены на одной ноде, нужно убедиться, что это работает в кластере с любым количеством узлов)**

## Документация, которая поможет:
- https://kubernetes.io/docs/concepts/storage/persistent-volumes/
- https://kubernetes.io/docs/tasks/configure-pod-container/image-volumes/

## Задача #3

- **1) Используйте только императивный подход (команды kubectl)**
- **2) Создайте  deployment с именем demo, образом nginx и пятью репликами.**
- **3) Создайте сервис типа ClusterIp и именем demo-service, который дает постоянный IP адрес демплойменту demo внутри кластера.**
- **4) Воспользуйтесь временным подом, чтобы зарезолвить имя сервиса внутри того же неймспейса. Используйте утилиту nslookup.**
- **5) Создайте namespace с именем demo и с помощью временного пода попытайтесь зарезолвить сервис demo-service по имени. Процесс будет чем-то отличаться?**
- **6) Удалите все созданные ресурсы из кластера.**

## Задача #4

- **0) (если используете миникуб) создайте 3 кластера с именами k8s-1, k8s-2 и k8s-3**
- **1) Выведите названия всех kubectl контекстов, на экран в столбик.**
- **2) Выведите на экран текущий контекст.**
- **3) Переключитесь на первый созданный контекст с помощью kubectl.**

Документация, которая поможет:
- https://kubernetes.io/docs/reference/kubectl/generated/kubectl_config/kubectl_config_current-context/


**Ответ**
0) : 
 - minikube start --driver=docker --profile=k8s-2 minikube start --driver=docker --profile=k8s-1
 - minikube start --driver=docker --profile=k8s-2 minikube start --driver=docker --profile=k8s-2
 - minikube start --driver=docker --profile=k8s-2 minikube start --driver=docker --profile=k8s-3

1) : 
 - kubectl config get-contexts -o name | column -t

2) :
 - kubectl config current-context

3) :
 - kubectl config use-context k8s-1

 ## Задача #5

- **1) Создайте два пода с именами nginx и redis (образы nginx и redis)**
- **2) Ваша задача создать их таким образом, чтобы они всегда запускались на одной ноде, вне зависимости от количества узлов в кластере.**
- **3) Нельзя пользоваться nodeName и nodeSelector.**
- **4) Нельзя изменять сам кластер, только манифесты этих двух подов.**

## Задача #6

- **1) Тебе понадобиться кластер с CNI, который поддерживает network policy (миникуб умеет)**
- **2) Создай два нэймспейса dev1 и dev2**
- **3) Создай по одному поду в каждом нэймспейсе с разными именами (demo-dev1 и demo-dev2) и образом nginx**
- **4) Проверь, что ты можешь сделать http запрос из demo-dev2 пода к поду demo-dev2**
- **5) Создай сетевую политику с именем deny-all для всех подов в dev2 неймспейсе. Она должна блокировать весь трафик к подам в dev2.**
- **6) Проверьте, что теперь запрос блокируется.**
- **7) Создай сетевую политику с именем kube-demo которая разрешает входящий трафик от подов в dev1 к подам в dev2 неймспейсе на порт 80.**
- **8) Проверьте, что теперь вы можете снова сделать http запрос из demo-dev2 пода к поду demo-dev2.**

## Задача #7

**1) Создай под с именем demo, c образом nginx, в дефолтном неймспейсе.**
**2) Сконфигурируй LivenessProbe для пода. Реализуй ее в виде запуска команды true**
**3) Сконфигурируй ReadinessProbe для пода. Должна чекать адрес http://readiness-service:80**
**4) Запусти под и проверь его статус.**
**5) Теперь создай необходимые ресурсы, чтобы перевести под demo в состояние Ready.**