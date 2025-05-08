# Despliegue en Render

## Pasos para desplegar tu proyecto Django en Render

1. **Sube tu proyecto a un repositorio en GitHub.**
2. **Asegúrate de tener los archivos `requirements.txt`, `Procfile` y `.env` (este último solo como ejemplo, no lo subas a GitHub).**
3. **Entra a [Render.com](https://render.com) y crea un nuevo servicio web.**
4. **Conecta tu cuenta de GitHub y selecciona el repositorio de tu proyecto.**
5. **Configura las variables de entorno en Render usando los valores de tu `.env`.**
6. **Render detectará automáticamente el `Procfile` y usará Gunicorn para ejecutar tu app.**
7. **En la sección de configuración avanzada, asegúrate de que el build command sea:**
   ```
   pip install -r requirements.txt
   python manage.py migrate
   python manage.py collectstatic --noinput
   ```
8. **Guarda y despliega. Render instalará dependencias, migrará la base de datos y servirá los archivos estáticos.**

### Notas importantes
- En `settings.py`, `ALLOWED_HOSTS` debe incluir `.onrender.com`.
- Usa variables de entorno para la base de datos y el secreto.
- No subas tu archivo `.env` real a GitHub.

¡Listo! Tu proyecto estará disponible en la URL que Render te proporcione.