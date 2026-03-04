# Справочник команд Docker

## Основные команды

### Информация о системе
```bash
# Версия Docker
docker --version

# Информация о Docker
docker info

# Статус демона
systemctl status docker
```

### Работа с образами
```bash
# Список образов
docker images

# Подробный список образов
docker images -a

# Поиск образа на Docker Hub
docker search nginx

# Загрузка образа
docker pull ubuntu:22.04

# Удаление образа
docker rmi <IMAGE_ID>

# Удаление всех неиспользуемых образов
docker image prune
```

### Работа с контейнерами

#### Создание и запуск
```bash
# Запуск контейнера в интерактивном режиме
docker run -it ubuntu /bin/bash

# Запуск контейнера в фоне (daemon)
docker run -d --name my_container nginx

# Запуск с пробросом портов
docker run -d -p 8080:80 --name my_web nginx
# Формат: -p HOST_PORT:CONTAINER_PORT

# Запуск с переменными окружения
docker run -d -e MYSQL_ROOT_PASSWORD=password mysql

# Запуск с монтированием папки
docker run -d -v /host/path:/container/path nginx

# Запуск с ограничениями ресурсов
docker run -d --memory=256m --cpus=0.5 nginx
```

#### Просмотр информации
```bash
# Список работающих контейнеров
docker ps

# Список всех контейнеров (включая остановленные)
docker ps -a

# Информация о контейнере
docker inspect <CONTAINER_ID>

# Логи контейнера
docker logs <CONTAINER_NAME>

# Логи в реальном времени
docker logs -f <CONTAINER_NAME>

# Последние N строк логов
docker logs --tail 50 <CONTAINER_NAME>

# Статистика контейнера
docker stats <CONTAINER_NAME>
```

#### Управление контейнерами
```bash
# Остановка контейнера
docker stop <CONTAINER_NAME>

# Запуск остановленного контейнера
docker start <CONTAINER_NAME>

# Перезапуск контейнера
docker restart <CONTAINER_NAME>

# Пауза контейнера
docker pause <CONTAINER_NAME>

# Возобновление контейнера
docker unpause <CONTAINER_NAME>

# Удаление контейнера
docker rm <CONTAINER_NAME>

# Принудительное удаление работающего контейнера
docker rm -f <CONTAINER_NAME>

# Удаление всех остановленных контейнеров
docker container prune
```

#### Вход в контейнер
```bash
# Вход в работающий контейнер
docker exec -it <CONTAINER_NAME> /bin/bash

# Выполнение команды в контейнере
docker exec <CONTAINER_NAME> whoami

# Копирование файла из контейнера
docker cp <CONTAINER_NAME>:/path/in/container /path/on/host

# Копирование файла в контейнер
docker cp /path/on/host <CONTAINER_NAME>:/path/in/container
```

### Очистка системы
```bash
# Удаление всех остановленных контейнеров
docker container prune

# Удаление всех неиспользуемых образов
docker image prune

# Удаление всех неиспользуемых объектов (контейнеры, образы, сети, тома)
docker system prune

# То же самое с удалением томов
docker system prune -a --volumes
```

---

## Советы и трюки

### Быстрые команды
```bash
# Получить ID последнего контейнера
LAST_CONTAINER=$(docker ps -lq)

# Остановить все работающие контейнеры
docker stop $(docker ps -q)

# Удалить все контейнеры
docker rm $(docker ps -aq)

# Удалить все образы
docker rmi $(docker images -q)
```

### Полезные флаги
- `-d` - запуск в фоне (daemon)
- `-it` - интерактивный режим с терминалом
- `-p` - проброс портов (HOST:CONTAINER)
- `-e` - переменные окружения
- `-v` - монтирование томов
- `--name` - имя контейнера
- `--rm` - автоматическое удаление при остановке
- `-f` - принудительное выполнение операции

### Форматы портов и томов
```bash
# Проброс портов
-p 8080:80              # http://localhost:8080 → контейнер:80
-p 127.0.0.1:8080:80   # только локально
-p 8080:80/udp         # UDP протокол

# Монтирование томов
-v /host/path:/container/path       # читать-писать
-v /host/path:/container/path:ro    # только чтение
-v my_volume:/container/path        # именованный том
```

---

## Решение проблем

### Docker требует sudo
```bash
# Проверьте что пользователь в группе docker
groups $USER

# Если нет, добавьте
sudo usermod -aG docker $USER

# Примените изменения
newgrp docker

# Проверьте
docker ps
```

### Контейнер не запускается
```bash
# Проверьте логи
docker logs <CONTAINER_NAME>

# Проверьте детали контейнера
docker inspect <CONTAINER_NAME>

# Удалите и создайте заново
docker rm <CONTAINER_NAME>
docker run ...
```

### Порт уже занят
```bash
# Найдите процесс использующий порт
sudo lsof -i :8080

# Или используйте другой портов
docker run -p 8081:80 nginx
```

### Нет места на диске
```bash
# Очистите неиспользуемые объекты
docker system prune -a

# Проверьте размер
docker system df
```

---

## Полезные ссылки

- [Docker Documentation](https://docs.docker.com/)
- [Docker Hub](https://hub.docker.com/)
- [Nginx на DockerHub](https://hub.docker.com/_/nginx)
- [Debian на DockerHub](https://hub.docker.com/_/debian)
- [NextCloud на DockerHub](https://hub.docker.com/_/nextcloud)
- [MySQL на DockerHub](https://hub.docker.com/_/mysql)

