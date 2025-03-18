# Выполненное домашнее задание к занятию «Средство визуализации Grafana» - Боровик А.А.

## Задание повышенной сложности

**При решении задания 1** не используйте директорию [help](./help) для сборки проекта. Самостоятельно разверните grafana, где в роли источника данных будет выступать prometheus, а сборщиком данных будет node-exporter:

- grafana;
- prometheus-server;
- prometheus node-exporter.

За дополнительными материалами можете обратиться в официальную документацию grafana и prometheus.

В решении к домашнему заданию также приведите все конфигурации, скрипты, манифесты, которые вы 
использовали в процессе решения задания.

**При решении задания 3** вы должны самостоятельно завести удобный для вас канал нотификации, например, Telegram или email, и отправить туда тестовые события.

В решении приведите скриншоты тестовых событий из каналов нотификаций.

## Обязательные задания

### Задание 1
 
1. Используя директорию [help](./help) внутри этого домашнего задания, запустите связку prometheus-grafana.
2. Зайдите в веб-интерфейс grafana, используя авторизационные данные, указанные в манифесте docker-compose.
3. Подключите поднятый вами prometheus, как источник данных.
4. Решение домашнего задания — скриншот веб-интерфейса grafana со списком подключенных Datasource.

**Ответ:**

Grafana, prometheus-server и node-exporter устанавливал путём скачивания бинарников с официальных сайтов.

Конфиг файл для prometheus создал следующий:

[Конфиг](https://github.com/Lex-Chaos/10-monitoring-03-grafana-hw/blob/main/files/prometheus.yml)

[Grafana](https://github.com/Lex-Chaos/10-monitoring-03-grafana-hw/blob/main/img/Task_1.png)

## Задание 2

Изучите самостоятельно ресурсы:

1. [PromQL tutorial for beginners and humans](https://valyala.medium.com/promql-tutorial-for-beginners-9ab455142085).
2. [Understanding Machine CPU usage](https://www.robustperception.io/understanding-machine-cpu-usage).
3. [Introduction to PromQL, the Prometheus query language](https://grafana.com/blog/2020/02/04/introduction-to-promql-the-prometheus-query-language/).

Создайте Dashboard и в ней создайте Panels:

- утилизация CPU для nodeexporter (в процентах, 100-idle);
- CPULA 1/5/15;
- количество свободной оперативной памяти;
- количество места на файловой системе.

Для решения этого задания приведите promql-запросы для выдачи этих метрик, а также скриншот получившейся Dashboard.

**Ответ:**

[CPU_Util](https://github.com/Lex-Chaos/10-monitoring-03-grafana-hw/blob/main/img/Task_2-CPU_Util.png)

[CPULA](https://github.com/Lex-Chaos/10-monitoring-03-grafana-hw/blob/main/img/Task_2-CPULA.png)

[Mem_free](https://github.com/Lex-Chaos/10-monitoring-03-grafana-hw/blob/main/img/Task_2-Mem_free.png)

[Disk_free](https://github.com/Lex-Chaos/10-monitoring-03-grafana-hw/blob/main/img/Task_2-Disk_free.png)

## Задание 3

1. Создайте для каждой Dashboard подходящее правило alert — можно обратиться к первой лекции в блоке «Мониторинг».
2. В качестве решения задания приведите скриншот вашей итоговой Dashboard.

**Ответ:**

Сделал оповещение по Email. Для этого произвёл настройку SMPT в конфиге Grafana:

```
[smtp]
enabled = true
host = smtp.yandex.ru:465
user = a.a.borovik@yandex.ru
# If the password contains # or ; you have to wrap it with triple quotes. Ex """#password;"""
password = ******
cert_file =
key_file =
skip_verify = false
from_address = a.a.borovik@yandex.ru
from_name = Grafana
encrypted_connection = SSL
ehlo_identity =
startTLS_policy =
enable_tracing = false
```

[Dashboard](https://github.com/Lex-Chaos/10-monitoring-03-grafana-hw/blob/main/img/Task_3-Dashboard.png)

[Dashboard](https://github.com/Lex-Chaos/10-monitoring-03-grafana-hw/blob/main/img/Task_3-Alert.png)

## Задание 4

1. Сохраните ваш Dashboard.Для этого перейдите в настройки Dashboard, выберите в боковом меню «JSON MODEL». Далее скопируйте отображаемое json-содержимое в отдельный файл и сохраните его.
2. В качестве решения задания приведите листинг этого файла.

**Ответ:**

[Dashboard](https://github.com/Lex-Chaos/10-monitoring-03-grafana-hw/blob/main/files/My_Dashboard.json)
---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
