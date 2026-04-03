# Задание 2: Использование Yandex Mirror Registry

## Цель

Научиться использовать альтернативные Docker-репозитории (зеркала) вместо Docker Hub.

---

## Yandex Mirror

**URL**: `cr.yandex/mirror/`

Формат образа:
```dockerfile
FROM cr.yandex/mirror/<образ>:<тег>
```

**Примеры:**
- `cr.yandex/mirror/python:3.11-slim`
- `cr.yandex/mirror/node:18-alpine`
- `cr.yandex/mirror/nginx:alpine`
- `cr.yandex/mirror/ubuntu:22.04`

---

## Задание

Написать Dockerfile, который:
1. Использует базовый образ **из Yandex Mirror**: `cr.yandex/mirror/python:3.11-slim`
2. Устанавливает рабочую директорию `/app`
3. Устанавливает переменную окружения `REGISTRY="Yandex Mirror"`
4. Копирует `app.py`
5. Работает от пользователя `1001`
6. Открывает порт `8080`


## Выполнение

### Шаг 1: Собрать образ

### Шаг 2: Запустить контейнер 

### Шаг 3: Проверить

```bash
# Проверить логи
docker logs yandex-app

# Проверить в браузере
# http://localhost:8080

# Проверить переменную
docker exec yandex-app env | grep REGISTRY
```


РЕЗУЛЬТАТ:
worker@ubuntu:~/practice$ curl http://localhost:8080

        <html>
        <head><title>Task 2</title></head>
        <body style="font-family: Arial; text-align: center; padding: 50px;">
            <h1>Задание 2 выполнено!</h1>
            <h2>Yandex Mirror Registry</h2>
            <p>Registry: <strong>Yandex Mirror</strong></p>
            <p>Базовый образ: <code>cr.yandex/mirror/python:3.11-slim</code></p>
        </body>
        </html>
        worker@ubuntu:~/practice$ 


----