
# Poblar tablas con datos de prueba en Django usando `django-seed`

En el desarrollo de aplicaciones Django, es común necesitar datos de prueba (dummy data) para poder realizar pruebas y asegurarnos de que nuestra aplicación funciona correctamente. Afortunadamente, existe una herramienta llamada `django-seed` que nos permite poblar nuestras tablas de manera fácil y rápida.

Este post explica cómo utilizar django-seed, una herramienta práctica para poblar tablas en Django con datos de prueba de manera eficiente. La guía detalla los pasos necesarios para instalar, configurar y generar registros automáticos en las bases de datos, ayudando a los desarrolladores a optimizar sus procesos de prueba y desarrollo.

## Pasos para usar `django-seed`

### 1. Instalar las dependencias necesarias

Primero, necesitamos instalar el paquete `django-seed`, que es el que nos permitirá generar los datos de prueba. Si estás utilizando PostgreSQL como base de datos, también deberás instalar `psycopg`. Para instalar ambos paquetes, ejecuta el siguiente comando:

```bash
pip install django-seed psycopg
```

Si usas otro sistema de base de datos, como MySQL o SQLite, instala el adaptador correspondiente para tu base de datos (por ejemplo, `mysqlclient` para MySQL).

### 2. Agregar `django-seed` a `INSTALLED_APPS`

Una vez que hayas instalado las dependencias, debes agregar `django_seed` a la lista de `INSTALLED_APPS` en tu archivo `settings.py` de la siguiente manera:

```python
INSTALLED_APPS = [
    ...
    "django_seed",
]
```

Esto le permite a Django reconocer el paquete y utilizarlo para poblar las tablas.

### 3. Generar datos de prueba

Con todo configurado, ya puedes usar `django-seed` para poblar las tablas de tus modelos con datos de prueba.

- **Para poblar todas las tablas de una app (en este ejemplo `pacientes`)**:

```bash
python manage.py seed pacientes --number=10
```

Esto generará 10 registros aleatorios en todas las tablas asociadas al modelo `pacientes`.

- **Para poblar una tabla específica dentro de una app**:

```bash
python manage.py seed pacientes.[nombre_de_la_tabla] --number=10
```

Reemplaza `[nombre_de_la_tabla]` con el nombre real de la tabla que deseas poblar. Puedes cambiar el número `10` a la cantidad de registros que desees.

### Notas adicionales

- Puedes ajustar el número de registros utilizando el parámetro `--number=...`.
- Si trabajas con otro motor de base de datos, como MySQL o SQLite, asegúrate de instalar el adaptador correspondiente.
- `django-seed` utiliza tus modelos de Django para generar los datos de prueba, por lo que puedes tener control total sobre el tipo de datos que se generarán en función de tus modelos.

## Conclusión

`django-seed` es una herramienta muy útil para poblar tus tablas con datos de prueba rápidamente y facilitar el proceso de desarrollo en Django. Con solo unos simples pasos, puedes generar datos aleatorios que te permitirán probar tu aplicación de manera efectiva.

---

**¡Espero que esta guía te sea útil para agilizar el desarrollo de tu proyecto en Django!**
