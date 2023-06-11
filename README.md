#  Проект Kittygram

## Описание проекта

Данный учебный проект является финальным результатом изучения Docker и технологий Cl и CD

## Стек технологий

- Python 3.9
- Django
- djangorestframework 
- djoser
- nginx
- gunicorn
- postgresql


## Как запустить проект:
Установить программу контейнеризации Docker (версия 4.19.0), так же необходимо зарегистрироваться на DockerHub.

Клонировать репозиторий:
```
git clone git@github.com:maximandreychuk/kittygram_final.git
cd kittygram_final
```
Cоздать и активировать виртуальное окружение, установить зависимости:
```
python3 -m venv venv && \ 
    source venv/scripts/activate && \
    python -m pip install --upgrade pip && \
    pip install -r backend/requirements.txt
```

В терминале выполнить команду:
```
docker compose -f docker-compose.production.yml up
```
После последовательно в терминале выполнить команды для миграций и сбора статики:
```
sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate

sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic

sudo docker compose -f docker-compose.production.yml exec backend cp -r collected_static/. ../backend_static/static/
```

## Автор
Андрейчук Максим
https://github.com/maximandreychuk
