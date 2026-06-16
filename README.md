# effective-mobile-devops-test

## Описание

Проект состоит из двух контейнеров:

- **backend** - HTTP-сервер на Python, отвечающий на запросы текстом `Hello from Effective Mobile!`
- **nginx** - reverse proxy, принимающий HTTP-запросы на порту 80 и перенаправляющий их на backend

## Используемые технологии

- Python 3.9
- Nginx
- Docker
- Docker Compose

## Структура проекта

```text
├── backend/
│   ├── Dockerfile
│   └── app.py
├── nginx/
│   └── nginx.conf
├── docker-compose.yml
├── .gitignore
└── README.md
```

## Запуск проекта

Склонировать репозиторий:

```bash
git clone https://github.com/KarpovetsIlya/effective-mobile-devops-test.git
cd effective-mobile-devops-test
```

Запустить контейнеры:

```bash
docker compose up --build
```

## Проверка работоспособности

После запуска выполнить:

```bash
curl http://localhost
```

Ожидаемый результат:

```text
Hello from Effective Mobile!
```

Также можно открыть в браузере:

```text
http://localhost
```

## Архитектура

```text
Client
   |
   v
Nginx (80)
   |
   v
Backend (8080)
```

Backend не публикует порт наружу и доступен только внутри Docker-сети. Все внешние запросы принимаются контейнером Nginx и проксируются на backend
