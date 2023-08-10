# Используем базовый образ с поддержкой Python
FROM python:3.9


# Установка зависимостей
RUN apt-get update && apt-get install -y nginx postgresql-client && rm -rf /var/lib/apt/lists/*


# Установка Django и Gunicorn
RUN pip install gunicorn


# Создание и переход в рабочую директорию
WORKDIR /app


# Установка зависимостей Python
COPY requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt


# Копирование проекта
COPY . /app/


# Копирование конфига nginx
COPY nginx.conf /etc/nginx/sites-available/default


# Открытие порта 80
EXPOSE 80


# Запуск Gunicorn и nginx (без демона для фонового режима)
CMD ["./start.sh"]