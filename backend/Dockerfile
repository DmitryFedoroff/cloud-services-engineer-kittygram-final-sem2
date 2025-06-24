# Используем официальный образ Python 3.10 в качестве базового
FROM python:3.10

# Устанавливаем рабочую директорию внутри контейнера
WORKDIR /app

# Копируем файл зависимостей
COPY requirements.txt .

# Устанавливаем зависимости без кэширования
RUN pip install -r requirements.txt --no-cache-dir

# Копируем весь исходный код проекта в контейнер
COPY . .

# Запускаем Gunicorn-сервер на порту 9000
CMD ["gunicorn", "--bind", "0.0.0.0:9000", "kittygram_backend.wsgi"]
