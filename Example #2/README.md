# Задача #2

- **1) Создай Persistent Volume типа hostPath (размер 500Мб, тип доступа RWO)**
- **2) Создай соотвествующий Persistent Volume Claim для него**
- **3) Создай Pod, который каждые десять секунд пишет текущее время в файл index.html через PVC**
- **4) Опционально: запусти Pod с nginx, который сможет раздать этот index.html (так как RWO оба пода должны быть запущены на одной ноде, нужно убедиться, что это работает в кластере с любым количеством узлов)**

## Документация, которая поможет:
- https://kubernetes.io/docs/concepts/storage/persistent-volumes/
- https://kubernetes.io/docs/tasks/configure-pod-container/image-volumes/