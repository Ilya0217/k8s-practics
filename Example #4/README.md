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