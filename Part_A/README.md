# Часть A: Основы Docker

## Задача 1: Установка Docker и настройка пользователя без привилегий

**Статус:** ❌ Не выполнена

### Требуемые скриншоты:
- [ ] Вывод `docker --version` без использования `sudo`
- [ ] Успешный запуск `docker run hello-world`

### Команды для выполнения:
```bash
# Установка Docker (Debian/Ubuntu)
sudo apt-get update
sudo apt-get install docker.io -y

# Добавление пользователя в группу docker
sudo usermod -aG docker $USER
newgrp docker

# Проверка установки
docker --version
docker run hello-world
```

### Примечания:
- Если команда newgrp не сработает, выйдите и заново войдите в систему
- Проверьте, что `docker run` работает БЕЗ `sudo`

---

## Задача 2: Жизненный цикл контейнера Hello-World

**Статус:** ❌ Не выполнена

### Требуемые скриншоты:
- [ ] Вывод `docker run hello-world`
- [ ] Вывод `docker ps -a` с перечислением контейнера
- [ ] Вывод `docker ps -a` после удаления контейнера

### Команды для выполнения:
```bash
# Запуск контейнера
docker run hello-world

# Список всех контейнеров (включая остановленные)
docker ps -a

# Удаление контейнера по ID или имени
docker rm <CONTAINER_ID>

# Проверка удаления
docker ps -a
```

---

## Задача 3: Интерактивный контейнер Debian с установкой пакета

**Статус:** ❌ Не выполнена

### Требуемые скриншоты:
- [ ] Установка `nano` в контейнере
- [ ] `nano` установлен после перезапуска контейнера
- [ ] В новом контейнере `nano` НЕ установлен
- [ ] Жизненный цикл контейнера (`docker ps -a` на разных этапах)

### Команды для выполнения:
```bash
# Создание интерактивного контейнера Debian
docker run -it debian /bin/bash

# Внутри контейнера:
apt-get update
apt-get install nano -y
nano
exit

# Список контейнеров
docker ps -a

# Перезапуск контейнера
docker start <CONTAINER_ID>
docker attach <CONTAINER_ID>

# Внутри контейнера: проверка nano
which nano
exit

# Удаление контейнера
docker rm <CONTAINER_ID>

# Новый контейнер Debian
docker run -it debian /bin/bash

# Внутри: проверка что nano НЕ установлен
which nano  # Должен вывести: nano not found
exit

# Очистка
docker ps -a
docker rm <CONTAINER_ID>
```

---

## Задача 4: Daemon контейнер с Nginx

**Статус:** ❌ Не выполнена

### Требуемые скриншоты:
- [ ] Команда `docker run -d --name my_nginx nginx`
- [ ] Вывод `docker ps` с работающим контейнером
- [ ] Окно браузера с доступом к nginx (http://localhost)
- [ ] Вывод `docker logs my_nginx`

### Команды для выполнения:
```bash
# Запуск daemon контейнера nginx
docker run -d --name my_nginx nginx

# Список работающих контейнеров
docker ps

# Получение IP-адреса Docker хоста
hostname -I

# Просмотр логов
docker logs my_nginx

# Доступ из браузера: http://localhost или http://<DOCKER_IP>
```

---

## Задача 5: Контейнер NextCloud с настройкой SQLite

**Статус:** ❌ Не выполнена

### Требуемые скриншоты:
- [ ] Команда создания контейнера
- [ ] Вывод `docker ps` с работающим NextCloud
- [ ] Окно браузера с интерфейсом NextCloud (http://localhost:8080)
- [ ] Вывод `docker logs nextcloud`

### Команды для выполнения:
```bash
# Создание контейнера NextCloud с пользовательским именем БД
docker run -d \
  --name nextcloud \
  -p 8080:80 \
  -e SQLITE_DB=mydb \
  nextcloud

# Ожидание загрузки (30-60 секунд)
sleep 60

# Проверка статуса
docker ps

# Просмотр логов
docker logs nextcloud

# Доступ из браузера: http://localhost:8080
```

### Примечания:
- NextCloud будет доступен через веб-интерфейс
- Может потребоваться выполнить первичную настройку
- Подождите несколько минут до полной загрузки

