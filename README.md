# Домашнее задание к занятию `«Хранение в K8s. Часть 2»` - Пугач Евгений.


---

## `Задание 1. Создать Deployment приложения, использующего локальный PV, созданный вручную.`

1. Создать Deployment приложения, состоящего из контейнеров busybox и multitool.
2. Создать PV и PVC для подключения папки на локальной ноде, которая будет использована в поде.
3. Продемонстрировать, что multitool может читать файл, в который busybox пишет каждые пять секунд в  
   общей директории.
4. Удалить Deployment и PVC. Продемонстрировать, что после этого произошло с PV. Пояснить, почему.

### Ответ:

![Скриншот 1](https://github.com/PugachEV72/Images/blob/master/2024-05-05_14-00-19.png)

После удаления PersistentVolumeClaim, PersistentVolume остаётся и отмечается "released".  
Данный PersistentVolume будет недоступен для новых PersistentVolumeClaim, т.к. содержит данные предыдущего.

5. Продемонстрировать, что файл сохранился на локальном диске ноды. Удалить PV. Продемонстрировать, что  
   произошло с файлом после удаления PV. Пояснить, почему.
6. Предоставить манифесты, а также скриншоты или вывод необходимых команд.

### Ответ:

![Скриншот 2](https://github.com/PugachEV72/Images/blob/master/2024-05-05_14-05-23.png)

При создании PV, я использовал режим ReclaimPolicy: Retain, который говорит, что после удаления PV,  
ресурсы из внешних провайдеров автоматически не удаляются.

![Скриншот 3](https://github.com/PugachEV72/Images/blob/master/2024-05-05_14-07-33.png)

[Ссылка на Deployment](https://github.com/PugachEV72/kuber-homeworks-2.2/blob/main/deploymet-manually.yaml)

[Ссылка на PV](https://github.com/PugachEV72/kuber-homeworks-2.2/blob/main/pv-manually.yaml)

[Ссылка на PVC](https://github.com/PugachEV72/kuber-homeworks-2.2/blob/main/pvc-manually.yaml)

---

## `Задание 2. Создать Deployment приложения, которое может хранить файлы на NFS с динамическим созданием PV.`

1. Включить и настроить NFS-сервер на MicroK8S.

### Ответ:

![Скриншот 4](https://github.com/PugachEV72/Images/blob/master/2024-05-05_14-26-50.png)

![Скриншот 5](https://github.com/PugachEV72/Images/blob/master/2024-05-05_14-30-56.png)

![Скриншот 6](https://github.com/PugachEV72/Images/blob/master/2024-05-05_14-43-42.png)

2. Создать Deployment приложения состоящего из multitool, и подключить к нему PV, созданный автоматически на сервере NFS.
3. Продемонстрировать возможность чтения и записи файла изнутри пода.
4. Предоставить манифесты, а также скриншоты или вывод необходимых команд.

### Ответ:

![Скриншот 7](https://github.com/PugachEV72/Images/blob/master/2024-05-05_20-17-39.png)

[Ссылка на Deployment](https://github.com/PugachEV72/kuber-homeworks-2.2/blob/main/deployment-nfs.yaml)

[Ссылка на PVC](https://github.com/PugachEV72/kuber-homeworks-2.2/blob/main/pvc-nfs.yaml)

---
