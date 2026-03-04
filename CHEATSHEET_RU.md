# 🚀 Шпаргалка Docker - Самые важные команды

## Часть A - Задача 1: Установка Docker

```bash
# Установка
sudo apt-get update && sudo apt-get install docker.io -y

# Добавление в группу docker (без sudo)
sudo usermod -aG docker $USER && newgrp docker

# Проверка
docker --version && docker run hello-world
```

---

## Часть A - Задача 2: Hello-World контейнер

```bash
# Запуск контейнера
docker run hello-world

# Список контейнеров
docker ps -a

# Удаление контейнера (замените <ID> на ID из docker ps -a)
docker rm <ID>
```

---

## Часть A - Задача 3: Debian + nano

### Создание контейнера и установка nano
```bash
docker run -it debian /bin/bash
# Внутри контейнера выполните:
apt-get update && apt-get install nano -y
nano
exit
```

### Проверка что контейнер существует и перезапуск
```bash
# Список с ID
docker ps -a

# Перезапуск контейнера (замените <ID> на ваш ID)
docker start <ID>
docker attach <ID>
# Проверка что nano остался
which nano
exit
```

### Удаление старого и создание нового контейнера
```bash
# Удалить старый контейнер
docker rm <ID>

# Создать новый Debian контейнер
docker run -it debian /bin/bash
# Проверить что nano НЕ установлен
which nano
exit
```

---

## Часть A - Задача 4: Nginx daemon

```bash
# Создание и запуск
docker run -d --name my_nginx nginx

# Проверка статуса
docker ps

# IP адрес для браузера
hostname -I

# Просмотр логов
docker logs my_nginx

# Доступ в браузер: http://localhost (по умолчанию порт 80)
```

---

## Часть A - Задача 5: NextCloud

```bash
# Создание контейнера
docker run -d \
  --name nextcloud \
  -p 8080:80 \
  -e SQLITE_DB=mydb \
  nextcloud

# Ожидание загрузки
sleep 60

# Проверка
docker ps

# Логи (дождитесь до готовности)
docker logs nextcloud

# Доступ в браузер: http://localhost:8080
```

---

## Часть B: Nginx на порту 8181

### Задача 1: Создание контейнера
```bash
# Создание
docker run -d --name servidor_web -p 8181:80 nginx

# Проверка
docker ps
docker inspect servidor_web
```

### Задача 2: Веб доступ
```bash
# Браузер → http://localhost:8181
# Или используйте IP адрес:
firefox http://$(hostname -I | awk '{print $1}'):8181
```

### Задача 3: Список образов
```bash
docker images
```

### Задача 4: Удаление контейнера
```bash
# Остановка
docker stop servidor_web

# Проверка что остановлен
docker ps -a | grep servidor_web

# Удаление
docker rm servidor_web

# Проверка что удален
docker ps -a | grep servidor_web
```

---

## ⚡ Команды первой помощи

### Если контейнер не запускается
```bash
# Смотрите логи
docker logs <NAME>

# Удалите и создайте заново
docker rm -f <NAME>
```

### Если Docker требует sudo
```bash
# Проверьте группу
groups $USER

# Добавьте в группу
sudo usermod -aG docker $USER && newgrp docker
```

### Если нужно очистить систему
```bash
# Удалить остановленные контейнеры
docker container prune

# Удалить неиспользуемые образы
docker image prune

# Очистить всё
docker system prune -a
```

---

## 📋 Получение ID контейнера или образа

```bash
# Вывод с одним столбцом (только ID)
docker ps -aq              # все контейнеры
docker ps -q               # работающие контейнеры
docker images -q           # все образы

# Пример использования
CONTAINER_ID=$(docker ps -aq | head -1)
docker rm $CONTAINER_ID
```

---

## 🎯 Проверочный лист перед сдачей

### Часть A:
- [ ] Задача 1: Docker установлен, работает без sudo
- [ ] Задача 2: Hello-world запущен и удален
- [ ] Задача 3: Debian контейнер с nano, проверка что он не копируется в новый
- [ ] Задача 4: Nginx работает, доступен в браузере
- [ ] Задача 5: NextCloud работает, доступен в браузере

### Часть B:
- [ ] Задача 1: Контейнер `servidor_web` создан и работает
- [ ] Задача 2: Доступен на http://localhost:8181
- [ ] Задача 3: `docker images` показывает все образы
- [ ] Задача 4: Контейнер остановлен и удален

### Оформление:
- [ ] Все скриншоты сохранены в правильных папках
- [ ] Каждый скриншот подписан и понятен
- [ ] Репозиторий обновлён (git push)

---

## 📚 Полезные ссылки

- [Docker Documentation](https://docs.docker.com/)
- [Docker Hub - найти образы](https://hub.docker.com/)
- [Nginx образ](https://hub.docker.com/_/nginx)
- [Debian образ](https://hub.docker.com/_/debian)
- [NextCloud образ](https://hub.docker.com/_/nextcloud)

---

**Помните:** Если что-то не ясно - смотрите [DOCKER_COMMANDS_REFERENCE.md](DOCKER_COMMANDS_REFERENCE.md) для получения полной справки!

