# Tienda Musical - Proyecto Django

Este proyecto es una tienda musical desarrollada con Django y PostgreSQL, preparada para ser desplegada en Railway.

## Configuración para Producción

El proyecto ha sido configurado para su despliegue en producción con las siguientes características:

- Uso de variables de entorno para configuraciones sensibles
- Configuración optimizada de PostgreSQL
- Servicio de archivos estáticos con Whitenoise
- Gunicorn como servidor WSGI

## Requisitos

- Python 3.11
- PostgreSQL
- Cuenta en Railway

## Pasos para el Despliegue en Railway

1. **Crear un nuevo proyecto en Railway**
   - Inicia sesión en [Railway](https://railway.app/)
   - Crea un nuevo proyecto
   - Selecciona "Deploy from GitHub repo"

2. **Configurar Variables de Entorno**
   - En la sección "Variables" de tu proyecto en Railway, configura las siguientes variables:
     - `SECRET_KEY`: Tu clave secreta de Django
     - `DEBUG`: False
     - `ALLOWED_HOSTS`: .railway.app,localhost,127.0.0.1
     - `DATABASE_URL`: Se configura automáticamente al añadir PostgreSQL

3. **Añadir PostgreSQL**
   - En tu proyecto de Railway, añade un servicio de PostgreSQL
   - Railway configurará automáticamente la variable `DATABASE_URL`

4. **Desplegar la Aplicación**
   - Railway detectará automáticamente el archivo Procfile y desplegará la aplicación
   - El proceso de construcción instalará las dependencias del archivo requirements.txt

5. **Ejecutar Migraciones**
   - Una vez desplegada la aplicación, ejecuta las migraciones desde la terminal de Railway:
     ```
     python manage.py migrate
     ```

6. **Crear Superusuario (opcional)**
   - Para acceder al panel de administración:
     ```
     python manage.py createsuperuser
     ```

7. **Recopilar Archivos Estáticos**
   - Ejecuta el siguiente comando para recopilar los archivos estáticos:
     ```
     python manage.py collectstatic --noinput
     ```

## Estructura del Proyecto

El proyecto está organizado en las siguientes aplicaciones:

- `productos`: Gestión de productos musicales
- `usuarios`: Gestión de perfiles de usuario

## Notas Importantes

- La aplicación está configurada para usar Whitenoise para servir archivos estáticos en producción
- Se utiliza dj-database-url para configurar la conexión a la base de datos
- Gunicorn se utiliza como servidor WSGI en producción

## Mantenimiento

Para actualizar la aplicación, simplemente realiza cambios en el repositorio y Railway se encargará de desplegar automáticamente los cambios.