# 🐈 Kittygram - Социальная сеть для размещения фотографий котиков

[![Deploy Status](https://img.shields.io/badge/deploy-passing-brightgreen)](http://89.169.185.94)
[![Docker](https://img.shields.io/badge/docker-ready-blue)](https://hub.docker.com/u/dmitryfedoroff)
[![Terraform](https://img.shields.io/badge/terraform-v1.8.3-purple)](https://www.terraform.io/)
[![Python](https://img.shields.io/badge/python-3.10-blue)](https://www.python.org/)
[![Django](https://img.shields.io/badge/django-3.2.3-green)](https://www.djangoproject.com/)
[![React](https://img.shields.io/badge/react-17.0.2-61DAFB?logo=react)](https://reactjs.org/)
[![PostgreSQL](https://img.shields.io/badge/postgresql-13.10-336791?logo=postgresql)](https://www.postgresql.org/)
[![Nginx](https://img.shields.io/badge/nginx-1.22.1-009639?logo=nginx)](https://nginx.org/)
[![Node.js](https://img.shields.io/badge/node.js-18-339933?logo=node.js)](https://nodejs.org/)
[![Yandex Cloud](https://img.shields.io/badge/yandex%20cloud-deployed-blue?logo=yandex)](https://cloud.yandex.ru/)
[![CI/CD](https://img.shields.io/github/workflow/status/DmitryFedoroff/cloud-services-engineer-kittygram-final-sem2/Deploy?label=CI%2FCD)](https://github.com/DmitryFedoroff/cloud-services-engineer-kittygram-final-sem2/actions)
[![License](https://img.shields.io/badge/license-Educational-yellow)](LICENSE)

<!-- Динамические бейджи -->
[![Last Commit](https://img.shields.io/github/last-commit/DmitryFedoroff/cloud-services-engineer-kittygram-final-sem2)](https://github.com/DmitryFedoroff/cloud-services-engineer-kittygram-final-sem2/commits/main)
[![Repo Size](https://img.shields.io/github/repo-size/DmitryFedoroff/cloud-services-engineer-kittygram-final-sem2)](https://github.com/DmitryFedoroff/cloud-services-engineer-kittygram-final-sem2)
[![Code Size](https://img.shields.io/github/languages/code-size/DmitryFedoroff/cloud-services-engineer-kittygram-final-sem2)](https://github.com/DmitryFedoroff/cloud-services-engineer-kittygram-final-sem2)
[![Top Language](https://img.shields.io/github/languages/top/DmitryFedoroff/cloud-services-engineer-kittygram-final-sem2)](https://github.com/DmitryFedoroff/cloud-services-engineer-kittygram-final-sem2)

<!-- Бейджи для Docker Hub -->
[![Docker Backend](https://img.shields.io/docker/v/dmitryfedoroff/kittygram_backend?label=backend&logo=docker)](https://hub.docker.com/r/dmitryfedoroff/kittygram_backend)
[![Docker Frontend](https://img.shields.io/docker/v/dmitryfedoroff/kittygram_frontend?label=frontend&logo=docker)](https://hub.docker.com/r/dmitryfedoroff/kittygram_frontend)
[![Docker Gateway](https://img.shields.io/docker/v/dmitryfedoroff/kittygram_gateway?label=gateway&logo=docker)](https://hub.docker.com/r/dmitryfedoroff/kittygram_gateway)

<!-- Социальные бейджи -->
[![Stars](https://img.shields.io/github/stars/DmitryFedoroff/cloud-services-engineer-kittygram-final-sem2?style=social)](https://github.com/DmitryFedoroff/cloud-services-engineer-kittygram-final-sem2/stargazers)
[![Forks](https://img.shields.io/github/forks/DmitryFedoroff/cloud-services-engineer-kittygram-final-sem2?style=social)](https://github.com/DmitryFedoroff/cloud-services-engineer-kittygram-final-sem2/network/members)

## Описание проекта

**Kittygram** - это современная социальная сеть для любителей кошек, где пользователи могут делиться фотографиями своих питомцев, добавлять информацию о них и отмечать их достижения. Проект реализован с использованием современных DevOps-практик и развернут в облачной инфраструктуре Yandex Cloud.

## Технологический стек

### Backend

| Технология | Версия | Описание |
|------------|--------|----------|
| Python | 3.10 | Основной язык программирования |
| Django | 3.2.3 | Web-фреймворк |
| Django REST Framework | 3.12.4 | API фреймворк |
| Djoser | 2.1.0 | Аутентификация и управление пользователями |
| PostgreSQL | 13.10 | База данных |
| Gunicorn | 20.1.0 | WSGI HTTP сервер |
| Pillow | 9.0.0 | Обработка изображений |
| webcolors | 1.11.1 | Конвертация HEX цветов в названия |
| psycopg2-binary | 2.9.3 | PostgreSQL адаптер |
| python-dotenv | 1.0.1 | Управление переменными окружения |

### Frontend

| Технология | Версия | Описание |
|------------|--------|----------|
| React | 17.0.2 | UI библиотека |
| React Router | 5.2.0 | Маршрутизация |
| React DOM | 17.0.2 | DOM рендеринг |
| Node.js | 18 | JavaScript runtime |
| http-server | 14.1.1 | Статический веб-сервер |

### DevOps & Infrastructure

| Технология | Версия | Описание |
|------------|--------|----------|
| Docker | latest | Контейнеризация |
| Docker Compose | 3.9 | Оркестрация контейнеров |
| Nginx | 1.22.1 | Веб-сервер и reverse proxy |
| Terraform | 1.8.3 | Infrastructure as Code |
| GitHub Actions | - | CI/CD pipeline |
| Yandex Cloud | - | Облачная платформа |

## Структура проекта

```
cloud-services-engineer-kittygram-final-sem2/
├── backend/                       # Django приложение
│   ├── cats/                      # Основное приложение
│   │   ├── migrations/            # Миграции БД
│   │   ├── models.py              # Модели Cat, Achievement, AchievementCat
│   │   ├── serializers.py         # Сериализаторы с Base64ImageField
│   │   ├── views.py               # ViewSets для API
│   │   ├── admin.py               # Админ-панель
│   │   └── apps.py                # Конфигурация приложения
│   ├── kittygram_backend/         # Настройки проекта
│   │   ├── settings.py            # Основные настройки Django
│   │   ├── urls.py                # URL маршруты
│   │   ├── wsgi.py                # WSGI точка входа
│   │   └── asgi.py                # ASGI точка входа
│   ├── Dockerfile                 # Multi-stage сборка
│   ├── .dockerignore              # Исключения для Docker
│   ├── requirements.txt           # Python зависимости
│   ├── manage.py                  # Django управление
│   └── README.md                  # Документация backend
│
├── frontend/                      # React приложение
│   ├── src/                       # Исходный код
│   │   ├── components/            # React компоненты
│   │   │   ├── app/               # Главный компонент с роутингом
│   │   │   ├── header/            # Шапка с навигацией
│   │   │   ├── footer/            # Подвал сайта
│   │   │   ├── main-page/         # Список котиков
│   │   │   ├── card-page/         # Страница котика
│   │   │   ├── add-card-page/     # Добавление котика
│   │   │   ├── edit-card-page/    # Редактирование котика
│   │   │   ├── sign-in/           # Вход в систему
│   │   │   ├── sign-up/           # Регистрация
│   │   │   ├── pagination-box/    # Компонент пагинации
│   │   │   ├── main-card/         # Карточка котика
│   │   │   ├── popup/             # Модальное окно
│   │   │   └── ui/                # UI компоненты
│   │   ├── utils/                 # Утилиты
│   │   │   ├── api.js             # API клиент
│   │   │   ├── constants.js       # Константы (цвета, URL)
│   │   │   └── context.js         # React Context для пользователя
│   │   ├── fonts/                 # Шрифты (Inter, Exo)
│   │   ├── images/                # Изображения
│   │   └── index.js               # Точка входа React
│   ├── public/                    # Статические файлы
│   ├── Dockerfile                 # Node 18 + http-server
│   ├── .dockerignore              # Исключения для Docker
│   ├── package.json               # Node.js зависимости
│   └── package-lock.json          # Lock-файл зависимостей
│
├── nginx/                         # Конфигурация Nginx
│   ├── nginx.conf                 # Роутинг и proxy настройки
│   └── Dockerfile                 # Минималистичный образ
│
├── infra/                         # Terraform конфигурация
│   ├── vm.tf                      # VM с 2 vCPU, 2GB RAM, 20GB HDD
│   ├── vpc.tf                     # VPC с 3 подсетями и Security Group
│   ├── storage.tf                 # S3 bucket для tfstate
│   ├── provider.tf                # Yandex Cloud провайдер + S3 backend
│   ├── variables.tf               # Переменные Terraform
│   ├── outputs.tf                 # Выходные данные (IP, имя VM)
│   └── init/                      # Скрипты инициализации
│       └── vm-install.yml         # Cloud-init с Docker установкой
│
├── .github/workflows/             # GitHub Actions
│   ├── deploy.yml                 # 5-шаговый pipeline деплоя
│   └── terraform.yml              # IaC управление (plan/apply/destroy)
│
├── tests/                         # Pytest автотесты
│   ├── conftest.py                # Fixtures для тестов
│   ├── test_connection.py         # Тесты доступности и API
│   ├── test_dockerhub_images.py   # Проверка публичности образов
│   └── test_files.py              # Валидация структуры проекта
│
├── screenshots/                   # Скриншоты для документации
├── docker-compose.production.yml  # Production конфигурация с volumes
├── .env.example                   # Пример переменных окружения
├── .gitignore                     # Git исключения
├── tests.yml                      # Конфигурация для автотестов
├── pytest.ini                     # Настройки pytest
├── README.md                      # Документация
└── kittygram_workflow.yml         # Копия основного workflow
```

## Быстрый старт

### Предварительные требования

- Docker версии 20.10+ и Docker Compose 2.0+
- Git
- Доступ к серверу с Ubuntu 24.04 LTS
- Минимум 2GB RAM и 20GB свободного места

### Локальная разработка

1. **Клонирование репозитория**

```bash
git clone https://github.com/DmitryFedoroff/cloud-services-engineer-kittygram-final-sem2.git
cd cloud-services-engineer-kittygram-final-sem2
```

2. **Создание файла переменных окружения**

```bash
cp .env.example .env
# Отредактируйте .env и укажите необходимые значения
```

3. **Запуск контейнеров**

```bash
docker-compose -f docker-compose.production.yml up -d
```

4. **Ожидание готовности сервисов (health checks)**

```bash
# Проверка статуса
docker-compose -f docker-compose.production.yml ps

# Просмотр логов
docker-compose -f docker-compose.production.yml logs -f
```

5. **Применение миграций и сбор статики**

```bash
docker-compose -f docker-compose.production.yml exec -T kitty_backend python manage.py migrate
docker-compose -f docker-compose.production.yml exec -T kitty_backend python manage.py collectstatic --noinput
```

6. **Создание суперпользователя (опционально)**

```bash
docker-compose -f docker-compose.production.yml exec kitty_backend python manage.py createsuperuser
```

## Развертывание в Production

### Автоматическое развертывание через GitHub Actions

При push в ветку `main` автоматически запускается pipeline, который:

1. **Tests (Matrix testing)** - Проверка кода линтером flake8 на Python 3.9 и 3.10
   - Игнорируемые правила: E123, E301, E302, E501, W291, W292, W293, F401
   - Время выполнения: ~30 сек.

2. **Build & Push** - Сборка и публикация Docker образов
   - backend: FROM python:3.10, WORKDIR /app, Gunicorn на порту 9000
   - frontend: FROM node:18, сборка React, http-server на порту 8000
   - gateway: FROM nginx:1.22.1 с кастомной конфигурацией
   - Время выполнения: ~2 мин.

3. **Deploy** - Развертывание на сервере
   - Загрузка .env файла через SSH
   - Копирование docker-compose.production.yml через SCP
   - Проверка/установка docker-compose
   - Pull образов и перезапуск стека
   - Ожидание health checks (PostgreSQL --> Backend)
   - Выполнение миграций и сбор статики
   - Время выполнения: ~6 мин.

4. **Auto Tests** - Запуск pytest тестов
   - Проверка доступности сайта
   - Проверка работы API endpoints
   - Валидация статических файлов
   - Время выполнения: ~10 сек.

5. **Telegram Notification** - Отправка уведомления
   - Информация о коммите и авторе
   - Ссылка на GitHub
   - Время выполнения: ~10 сек.

### Terraform workflow (terraform.yml)

Запускается вручную через GitHub Actions с выбором действия:

#### Создаваемые ресурсы:

1. **Compute Instance**
   - Имя: vm-kittygram
   - Платформа: standard-v1
   - Ресурсы: 2 vCPU (20% guaranteed), 2 Гбайта RAM
   - Диск: 20 Гбайт SSD
   - ОС: Ubuntu 24.04 LTS с OS Login
   - Автоматическая установка Docker через cloud-init

2. **Сетевая инфраструктура**
   - VPC: infra-network
   - Подсети: 3 зоны доступности (ru-central1-a/b/d)
   - Security Group: порты 22 (SSH) и 80 (HTTP)
   - Внешний IP: включен

3. **Object Storage**
   - Bucket: kittygram-tf-state-gorban
   - Versioning: включен
   - Lifecycle: хранение старых версий 180 дней
   - ACL: private

## Конфигурация секретов

### GitHub Secrets для CI/CD

| Секрет | Описание | Пример значения |
|--------|----------|-----------------|
| **Docker Hub** |
| `DOCKERHUB_USERNAME` | Имя пользователя Docker Hub | `your-username` |
| `DOCKERHUB_PASSWORD` | Access Token Docker Hub | `dckr_pat_xxxxx` |
| **SSH подключение** |
| `SERVER_IP` | IP адрес сервера | `89.169.185.94` |
| `SSH_USERNAME` | Имя пользователя SSH | `admin` |
| `SSH_PRIVATE_KEY` | Приватный SSH ключ (RSA) | `-----BEGIN RSA PRIVATE KEY-----...` |
| **База данных** |
| `POSTGRES_USER` | Пользователь PostgreSQL | `kittygram_user` |
| `POSTGRES_PASSWORD` | Пароль PostgreSQL | `kittygram_password` |
| `POSTGRES_DB` | Имя базы данных | `kittygram` |
| `DB_HOST` | Хост базы данных | `kitty_postgres` |
| `DB_PORT` | Порт базы данных | `5432` |
| **Приложение** |
| `SECRET_KEY` | Django Secret Key | `d79r*4!jmazv@q)q...` |
| **Уведомления** |
| `TELEGRAM_TO` | ID получателя в Telegram | `123456789` |
| `TELEGRAM_TOKEN` | Токен бота Telegram | `1234567890:ABCDefGhIjKLMNOPqrSTuvwxYZ` |

### Terraform Secrets для Yandex Cloud

| Секрет | Описание | Где получить |
|--------|----------|--------------|
| `YC_CLOUD_ID` | ID облака | Консоль Yandex Cloud --> Обзор |
| `YC_FOLDER_ID` | ID каталога | Консоль Yandex Cloud --> Каталоги |
| `YC_KEY_JSON` | Service Account ключ (base64) | `yc iam key create --service-account-name terraform --output key.json` |
| `SSH_KEY` | Публичный SSH ключ | `ssh-keygen -t rsa -b 2048` |
| `YC_ACCESS_KEY` | Access Key для S3 | `yc iam access-key create --service-account-name terraform` |
| `YC_SECRET_KEY` | Secret Key для S3 | Выводится при создании access-key |

## Docker образы

Все образы автоматически публикуются в Docker Hub с тегом `latest`:

| Образ | Описание | Базовый образ | Особенности |
|-------|----------|---------------|-------------|
| `dmitryfedoroff/kittygram_backend:latest` | Django приложение | python:3.10 | Gunicorn, healthcheck на порту 9000 |
| `dmitryfedoroff/kittygram_frontend:latest` | React приложение | node:18 | Production build, http-server |
| `dmitryfedoroff/kittygram_gateway:latest` | Nginx reverse proxy | nginx:1.22.1 | Шаблонизация конфигурации |

### Docker Compose сервисы

| Сервис | Порты | Волюмы | Зависимости |
|--------|-------|--------|-------------|
| `kitty_postgres` | 5432:5432 | pg_data:/var/lib/postgresql/data | - |
| `kitty_backend` | 9000 (internal) | static, media | kitty_postgres (healthy) |
| `kitty_frontend` | 8000 (internal) | frontend_build | - |
| `kitty_gateway` | 80:80 | frontend_build, static, media | kitty_backend, kitty_frontend |


## CI/CD Pipeline

### Основной workflow (deploy.yml)

1. **Matrix · Check PEP8** - параллельный прогон линтеров на нескольких версиях Python.
   *2 джоба, суммарно < 30 сек.; жесткое соблюдение стиля гарантировано еще до сборки образа.*

2. **Push to DockerHub** - сборка Docker-образов, тегирование по `SHA`-коммиту и публикация.
   *~ 2 мин. 09 сек.; выводимое имя тега совпадает с коротким хэшем, что упрощает traceability.*

3. **Deploy to remote server** - выкладка на удаленный VPS через `scp` + `ssh`.
   *~ 5 мин. 55 сек.; запускаются миграции БД, перезапускаются сервисы, проверяются health-probes.*

4. **Run Auto Tests** - быстрый smoke-suite, который стреляет по свежему продовому URL.
   *9 сек. - и ты точно знаешь, что endpoints отвечают 200 OK, а не 502 Bad Gateway.*

5. **Send Message to Telegram** - бот публикует зеленый отчет. *10 сек. на форматирование, и команда уже хлопает в ладоши в общем чате.*

<details>
<summary><b>Скриншот</b></summary>

![CI/CD Pipeline Execution](screenshots/screenshot_02.png)
</details>

### Terraform workflow (terraform.yml)

Запускается вручную через `workflow_dispatch` с выбором действия:
- `plan` - просмотр планируемых изменений (~30 сек.)
- `apply` - применение изменений (~2-3 мин. для новой инфраструктуры)
- `destroy` - удаление инфраструктуры (~1-2 мин.)

## Уведомления

### Telegram-бот [KittyBot](https://t.me/my_kitty_messenger_bot)

После успешного деплоя отправляется сообщение с информацией:
- Статус деплоя
- Автор коммита
- Сообщение коммита
- Ссылка на коммит в GitHub

<details>
<summary><b>Скриншот</b></summary>

![Telegram Notification](screenshots/screenshot_01.png)
</details>

## Мониторинг и Health Checks

### Docker Compose Health Checks

| Сервис | Команда проверки | Интервал | Таймаут | Повторные попытки |
|--------|------------------|----------|---------|-------------------|
| `kitty_postgres` | `pg_isready -U ${POSTGRES_USER} -d ${POSTGRES_DB}` | 10 сек. | 5 сек. | 5 |
| `kitty_backend` | Python socket check на localhost:9000 | 10 сек. | 5 сек. | 5 |

### Endpoints для мониторинга

- **Основное приложение**: http://89.169.185.94/
- **Админ-панель Django**: http://89.169.185.94/admin/
- **API Root**: http://89.169.185.94/api/
- **Статические файлы**: http://89.169.185.94/static/
- **Медиа файлы**: http://89.169.185.94/media/

### Nginx маршрутизация

| Location | Proxy Pass | Особенности |
|----------|------------|-------------|
| `/api/` | `http://kitty_backend:9000/api/` | API endpoints |
| `/admin/` | `http://kitty_backend:9000/admin/` | Django admin |
| `/media/` | `/var/html/media/` | Загруженные изображения |
| `/static/admin/` | `/var/html/static/admin/` | Статика админки |
| `/static/rest_framework/` | `/var/html/static/rest_framework/` | DRF статика |
| `/` | `/usr/share/nginx/html/` | React приложение |

## API Endpoints

### Аутентификация

| Метод | Endpoint | Описание |
|-------|----------|----------|
| POST | `/api/users/` | Регистрация пользователя |
| POST | `/api/token/login/` | Получение токена |
| POST | `/api/token/logout/` | Выход из системы |
| GET | `/api/users/me/` | Информация о текущем пользователе |

### Котики

| Метод | Endpoint | Описание |
|-------|----------|----------|
| GET | `/api/cats/?page={n}` | Список всех котиков (пагинация по 10) |
| POST | `/api/cats/` | Добавление нового котика |
| GET | `/api/cats/{id}/` | Информация о котике |
| PATCH | `/api/cats/{id}/` | Обновление информации |
| DELETE | `/api/cats/{id}/` | Удаление котика |

#### Формат данных котика:

```json
{
  "id": 1,
  "name": "Мурзик",
  "color": "#FFA500",  // При отправке - HEX код, в ответе - название "orange"
  "birth_year": 2020,
  "age": 5,  // Вычисляется автоматически (текущий год - birth_year)
  "owner": 1,  // Read-only, устанавливается автоматически из токена
  "image": "data:image/jpeg;base64,...",  // Base64 encoded
  "achievements": [
    {
      "id": 1,
      "achievement_name": "Мышелов"
    }
  ]
}
```

### Достижения

| Метод | Endpoint | Описание |
|-------|----------|----------|
| GET | `/api/achievements/` | Список всех достижений |
| POST | `/api/achievements/` | Добавление достижения |
| GET | `/api/achievements/{id}/` | Детали достижения |
| PUT | `/api/achievements/{id}/` | Обновление достижения |
| DELETE | `/api/achievements/{id}/` | Удаление достижения |

## Переменные окружения

### Обязательные переменные

```env
# === PostgreSQL ===
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password

# === Django ===
SECRET_KEY=your-secret-key-here

# === Database connection ===
DB_HOST=kitty_postgres
DB_PORT=5432
```

### Опциональные переменные

```env
# === Django settings ===
DEBUG=False        # Не используйте True в production
ALLOWED_HOSTS=*    # Рекомендуется указать конкретные домены

# === Gunicorn ===
WEB_CONCURRENCY=4  # Количество воркеров
```

## Контакты

- **Автор**: Дмитрий Федоров
- **Эл. почта**: [fedoroffx@gmail.com](mailto:fedoroffx@gmail.com)
- **Telegram**: [https://t.me/dmitryfedoroff](https://t.me/dmitryfedoroff)