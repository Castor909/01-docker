# Инструкции: Как выполнить задание

## 📋 Краткий план действий

### Часть A - 5 основных задач
1. ✅ Установка Docker и настройка пользователя
2. ✅ Hello-World контейнер
3. ✅ Debian контейнер с nano
4. ✅ Nginx daemon контейнер
5. ✅ NextCloud с SQLite

### Часть B - Nginx на порту 8181
1. ✅ Создание контейнера `servidor_web`
2. ✅ Доступ через веб-браузер
3. ✅ Список локальных образов
4. ✅ Удаление контейнера

---

## 🚀 Быстрый старт

### Шаг 1: Ознакомление
1. Прочитайте [Part_A/README.md](Part_A/README.md) - описание всех задач
2. Прочитайте [Part_B/README.md](Part_B/README.md) - описание задач части B
3. При необходимости используйте [DOCKER_COMMANDS_REFERENCE.md](DOCKER_COMMANDS_REFERENCE.md) - справочник команд

### Шаг 2: Выполнение задач
**Переходите по файлам:**
- Для **часть A**: открывайте [Part_A/README.md](Part_A/README.md)
- Для **часть B**: открывайте [Part_B/README.md](Part_B/README.md)

### Шаг 3: Документирование
1. Выполняйте команды из файлов
2. Берите скриншоты как указано
3. Сохраняйте скриншоты в соответствующих папках:
   - Скриншоты Части A → в папку `Part_A/screenshots/`
   - Скриншоты Части B → в папку `Part_B/screenshots/`

### Шаг 4: Коммит и отправка
```bash
# Добавьте все файлы в git
git add .

# Создайте коммит
git commit -m "Part A and B: Docker assignment completed with screenshots"

# Отправьте на сервер
git push origin main
```

---

## 📸 Где сохранять скриншоты

**Структура папок:**
```
01-docker/
├── Part_A/
│   ├── README.md
│   └── screenshots/
│       ├── task_1_docker_version.png
│       ├── task_1_hello_world.png
│       ├── task_2_docker_run.png
│       ├── task_2_ps_with_container.png
│       ├── task_2_ps_after_deletion.png
│       ├── task_3_nano_install.png
│       ├── task_3_nano_after_restart.png
│       ├── task_3_nano_not_installed.png
│       ├── task_3_ps_lifecycle.png
│       ├── task_4_nginx_run.png
│       ├── task_4_ps_running.png
│       ├── task_4_browser_access.png
│       ├── task_4_logs.png
│       ├── task_5_nextcloud_run.png
│       ├── task_5_ps_running.png
│       ├── task_5_browser_access.png
│       └── task_5_logs.png
└── Part_B/
    ├── README.md
    └── screenshots/
        ├── task_1_create_container.png
        ├── task_1_ps_running.png
        ├── task_2_browser_port_8181.png
        ├── task_3_docker_images.png
        ├── task_4_stop_container.png
        ├── task_4_ps_stopped.png
        ├── task_4_rm_container.png
        └── task_4_ps_deleted.png
```

---

## ⏰ Сроки

**Дедлайн:** 23 октября 23:59

Рекомендуемый график:
- **День 1-2:** Часть A задачи 1-2 (установка и базовые команды)
- **День 3-4:** Часть A задачи 3-4 (контейнеры и daemon)
- **День 5:** Часть A задача 5 (NextCloud)
- **День 6-7:** Часть B (удалённая работа)
- **День 8:** Финализация и коммит

---

## 💡 Полезные советы

### Перед началом
- ✅ Убедитесь что установлен Docker
- ✅ Проверьте подключение к интернету (для загрузки образов)
- ✅ Имейте под рукой браузер (для тестирования услуг)
- ✅ Убедитесь что у вас есть место на диске (~2 ГБ)

### Во время выполнения
- 📍 Внимательно читайте требования каждой задачи
- 📍 Копируйте команды полностью (включая флаги)
- 📍 Дождитесь полной загрузки контейнеров (особенно NextCloud)
- 📍 Если ошибка - смотрите логи: `docker logs <NAME>`

### Со скриншотами
- 📸 Включайте адресную строку браузера (чтобы было видно http://localhost:...)
- 📸 Показывайте полный вывод команд (без обрезания)
- 📸 Одно действие = один скриншот
- 📸 Используйте инструмент скриншотов ОС (Print Screen, Gnome Screenshot и т.д.)

### Если что-то не работает
1. **Прочитайте ошибку в консоли**
2. **Смотрите логи контейнера:** `docker logs <NAME>`
3. **Проверьте команду:** убедитесь что она скопирована правильно
4. **Очистите и переделайте:** `docker rm <NAME> && docker run ...`
5. **Смотрите справочник:** [DOCKER_COMMANDS_REFERENCE.md](DOCKER_COMMANDS_REFERENCE.md)

---

## 🔍 Как использовать файлы этого репозитория

### Файл: [TASKS_GUIDE_EN.md](TASKS_GUIDE_EN.md)
**Английская версия** со всеми командами - используйте как справочник

### Файлы: [Part_A/README.md](Part_A/README.md) и [Part_B/README.md](Part_B/README.md)
**Подробные инструкции** с требуемыми скриншотами для каждой задачи

### Файл: [DOCKER_COMMANDS_REFERENCE.md](DOCKER_COMMANDS_REFERENCE.md)
**Справочник команд Docker** - ищите здесь если забыли синтаксис команды

### Этот файл (INSTRUCTIONS_RU.md)
**Инструкции и план действий** - начните отсюда!

---

## ✨ Готов к работе!

Вы готовы начинать! Переходите к [Part_A/README.md](Part_A/README.md) и следуйте инструкциям там.

**Удачи в выполнении задания! 🎯**

