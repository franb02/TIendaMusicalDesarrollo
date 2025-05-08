release: python manage.py migrate && python manage.py collectstatic --noinput
web: gunicorn tienda_musical.wsgi