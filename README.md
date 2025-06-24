# 🐈 Kittygram - Социальная сеть для размещения фотографий котиков

[![Deploy Status](https://img.shields.io/badge/deploy-passing-brightgreen)](http://89.169.185.94)
[![Docker](https://img.shields.io/badge/docker-ready-blue)](https://hub.docker.com/u/dmitryfedoroff)
[![Terraform](https://img.shields.io/badge/terraform-v1.8.3-purple)](https://www.terraform.io/)
[![Python](https://img.shields.io/badge/python-3.10-blue)](https://www.python.org/)

## Описание проекта

**Kittygram** — это современная социальная сеть для любителей кошек, где пользователи могут делиться фотографиями своих питомцев, добавлять информацию о них и отмечать их достижения. Проект реализован с использованием современных DevOps-практик и развернут в облачной инфраструктуре Yandex Cloud.

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

### Frontend
| Технология | Версия | Описание |
|------------|--------|----------|
| React | 17.x | UI библиотека |
| React Router | 5.x | Маршрутизация |
| Node.js | 18 | JavaScript runtime |

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
├── backend/                      # Django приложение
│   ├── cats/                     # Основное приложение
│   ├── kittygram_backend/        # Настройки проекта
│   ├── Dockerfile                # Docker образ backend
│   ├── requirements.txt          # Python зависимости
│   └── manage.py                 # Django управление
│
├── frontend/                     # React приложение
│   ├── src/                      # Исходный код
│   ├── public/                   # Статические файлы
│   ├── Dockerfile                # Docker образ frontend
│   └── package.json              # Node.js зависимости
│
├── nginx/                        # Конфигурация Nginx
│   ├── nginx.conf                # Основная конфигурация
│   └── Dockerfile                # Docker образ nginx
│
├── infra/                        # Terraform конфигурация
│   ├── vm.tf                     # Виртуальная машина
│   ├── vpc.tf                    # Сетевая инфраструктура
│   ├── storage.tf                # S3 хранилище для tfstate
│   ├── provider.tf               # Провайдер Yandex Cloud
│   ├── variables.tf              # Переменные
│   ├── outputs.tf                # Выходные данные
│   └── init/                     # Скрипты инициализации
│       └── vm-install.yml        # Cloud-init конфигурация
│
├── .github/workflows/            # GitHub Actions
│   ├── deploy.yml                # Основной pipeline деплоя
│   └── terraform.yml             # Управление инфраструктурой
│
├── tests/                        # Автотесты
│   ├── test_connection.py        # Тесты доступности
│   ├── test_dockerhub_images.py  # Тесты Docker образов
│   └── test_files.py             # Тесты структуры проекта
│
├── docker-compose.production.yml # Production конфигурация
├── .env.example                  # Пример переменных окружения
├── tests.yml                     # Конфигурация тестов
└── kittygram_workflow.yml        # Локальная копия workflow
```

## Быстрый старт

### Предварительные требования

- Docker и Docker Compose
- Git
- Доступ к серверу с Ubuntu 24.04 LTS

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

4. **Применение миграций и сбор статики**
```bash
docker-compose -f docker-compose.production.yml exec -T kitty_backend python manage.py migrate
docker-compose -f docker-compose.production.yml exec -T kitty_backend python manage.py collectstatic --noinput
```

5. **Создание суперпользователя (опционально)**
```bash
docker-compose -f docker-compose.production.yml exec kitty_backend python manage.py createsuperuser
```

## Развертывание в Production

### Автоматическое развертывание через GitHub Actions

При push в ветку `main` автоматически запускается pipeline, который:

1. Проверяет код линтером (flake8)
2. Собирает Docker образы
3. Публикует образы в DockerHub
4. Разворачивает приложение на сервере
5. Запускает автотесты
6. Отправляет уведомление в Telegram

### Ручное развертывание инфраструктуры через Terraform

1. **Настройка Terraform**
```bash
cd infra/
terraform init
```

2. **Планирование изменений**
```bash
terraform plan
```

3. **Применение конфигурации**
```bash
terraform apply -auto-approve
```

4. **Получение информации о созданных ресурсах**
```bash
terraform output
```

## Конфигурация секретов

### GitHub Secrets для CI/CD

| Секрет | Описание | Пример значения |
|--------|----------|-----------------|
| **Docker Hub** |
| `DOCKERHUB_USERNAME` | Имя пользователя Docker Hub | `xxxxxxxxxxxxxx` |
| `DOCKERHUB_PASSWORD` | Access Token Docker Hub | `dckr_pat_xxxxx` |
| **SSH подключение** |
| `SERVER_IP` | IP адрес сервера | `89.169.185.94` |
| `SSH_USERNAME` | Имя пользователя SSH | `xxxxxxxxxxxxxx` |
| `SSH_PRIVATE_KEY` | Приватный SSH ключ | `-----BEGIN RSA PRIVATE KEY-----...` |
| **База данных** |
| `POSTGRES_USER` | Пользователь PostgreSQL | `kittygram_user` |
| `POSTGRES_PASSWORD` | Пароль PostgreSQL | `secure_password` |
| `POSTGRES_DB` | Имя базы данных | `kittygram` |
| `DB_HOST` | Хост базы данных | `kitty_postgres` |
| `DB_PORT` | Порт базы данных | `5432` |
| **Приложение** |
| `SECRET_KEY` | Django Secret Key | `xxxxxxxxxxxxxx` |
| **Уведомления** |
| `TELEGRAM_TO` | ID получателя в Telegram | `xxxxxxxxxxxxxx` |
| `TELEGRAM_TOKEN` | Токен бота Telegram | `7860549976:xxxxx` |

### Terraform Secrets для Yandex Cloud

| Секрет | Описание | Где получить |
|--------|----------|--------------|
| `YC_CLOUD_ID` | ID облака | Консоль Yandex Cloud |
| `YC_FOLDER_ID` | ID каталога | Консоль Yandex Cloud |
| `YC_KEY_JSON` | Service Account ключ (base64) | `yc iam key create` |
| `SSH_KEY` | Публичный SSH ключ | `ssh-keygen -t rsa` |
| `YC_ACCESS_KEY` | Access Key для S3 | Консоль Yandex Cloud |
| `YC_SECRET_KEY` | Secret Key для S3 | Консоль Yandex Cloud |

## Docker образы

Все образы автоматически публикуются в Docker Hub:

| Образ | Описание | Размер |
|-------|----------|--------|
| `dmitryfedoroff/kittygram_backend:latest` | Django приложение с Gunicorn | ~450MB |
| `dmitryfedoroff/kittygram_frontend:latest` | React приложение | ~350MB |
| `dmitryfedoroff/kittygram_gateway:latest` | Nginx reverse proxy | ~25MB |

## CI/CD Pipeline

### Основной workflow (deploy.yml)

1. **Matrix · Check PEP8** - параллельный прогон линтеров на нескольких версиях Python.
   *2 джоба, суммарно < 30 с; жесткое соблюдение стиля гарантировано еще до сборки образа.*

2. **Push to DockerHub** - сборка Docker-образов, тегирование по `SHA`-коммиту и публикация.
   *~ 2 мин. 09 сек.; выводимое имя тега совпадает с коротким хэшем, что упрощает traceability.*

3. **Deploy to remote server** - выкладка на удаленный VPS через `scp` + `ssh`.
   *~ 5 мин. 55 сек.; запускаются миграции БД, перезапускаются сервисы, проверяются health-probes.*

4. **Run Auto Tests** - быстрый smoke-suite, который стреляет по свежему продовому URL.
   *9 сек. - и ты точно знаешь, что endpoints отвечают 200 OK, а не 502 Bad Gateway.*

5. **Send Message to Telegram** — бот публикует зеленый отчет. *10 сек. на форматирование, и команда уже хлопает в ладоши в общем чате.*

<details>
<summary><b>Скриншот</b></summary>

![CI/CD Pipeline Execution](screenshots/screenshot_02.png)
</details>

### Уведомление об успешном деплое в моем Telegram-боте [**@KittyBot"**](https://t.me/my_kitty_messenger_bot)

<details>
<summary><b>Скриншот</b></summary>

![Уведомление в Telegram-боте](screenshots/screenshot_01.png)
</details>


### Terraform workflow (terraform.yml)

Запускается вручную через GitHub Actions с выбором действия:
- `plan` - просмотр планируемых изменений
- `apply` - применение изменений
- `destroy` - удаление инфраструктуры

## Мониторинг и Health Checks

### Docker Compose Health Checks

| Сервис | Команда проверки | Интервал | Таймаут |
|--------|------------------|----------|---------|
| `kitty_postgres` | `pg_isready -U ${POSTGRES_USER}` | 10s | 5s |
| `kitty_backend` | TCP проверка порта 9000 | 10s | 5s |

### Endpoints для мониторинга

- **Основное приложение**: http://89.169.185.94/
- **Админ-панель Django**: http://89.169.185.94/admin/
- **API документация**: http://89.169.185.94/api/

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
| GET | `/api/cats/` | Список всех котиков (с пагинацией) |
| POST | `/api/cats/` | Добавление нового котика |
| GET | `/api/cats/{id}/` | Информация о котике |
| PATCH | `/api/cats/{id}/` | Обновление информации |
| DELETE | `/api/cats/{id}/` | Удаление котика |

### Достижения
| Метод | Endpoint | Описание |
|-------|----------|----------|
| GET | `/api/achievements/` | Список всех достижений |
| POST | `/api/achievements/` | Добавление достижения |

## Переменные окружения

Пример файла `.env`:

```env
# PostgreSQL
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password

# Django
SECRET_KEY=your-secret-key-here
DEBUG=False

# Database connection
DB_HOST=kitty_postgres
DB_PORT=5432
```

## Контакты

- **Автор**: Дмитрий Федоров
- **Эл. почта**: [fedoroffx@gmail.com](mailto:fedoroffx@gmail.com)
- **Telegram**: [https://t.me/dmitryfedoroff](https://t.me/dmitryfedoroff)