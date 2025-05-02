# Задача #1

- **1) Создай Pod с именем "demo" из образа "nginx" последней версии.**
- **2) Добавь в него init контейнер с именем "setup" и образом "busybox".**
- **3) Настрой init контейнер таким образом, чтобы он создавал файл “index.html” и писал в него строку "hello world". Этот файл, должен располагаться в каталоге, который nginx будет раздавать по умолчанию (/usr/share/nginx/html).**

## Документация, которая поможет:
- https://kubernetes.io/docs/concepts/workloads/pods/init-containers/
- https://kubernetes.io/docs/concepts/storage/volumes/#emptydir
- https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/