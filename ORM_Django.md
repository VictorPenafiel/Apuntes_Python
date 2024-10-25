## Configuración de Proyecto Django con PostgreSQL

### Instalación de PostgreSQL y pgAdmin

1. Instala PostgreSQL como base de datos.

2. Instala pgAdmin como gestor de base de datos.

### Creación y Configuración de Base de Datos

1. Crea una base de datos en PostgreSQL:

   ```sql
   CREATE DATABASE db_practica_orm;
   ```

2. Crea un usuario y contraseña:

   ```sql
   CREATE USER user_db WITH PASSWORD 'user_db';
   ```

3. Asigna permisos al usuario:

   ```sql
   GRANT ALL PRIVILEGES ON DATABASE db_practica_orm TO postgres;
   GRANT ALL PRIVILEGES ON DATABASE db_practica_orm TO user_db;
   ```

### crear el proyecto
    pip install django
    django-admin startproject config

### crear la aplicación
    cd config
    django-admin startapp producto
Agregar esta app a la lista de aplicaciones instaladas, debemos abrir el archivo settings.py presente en el directorio de
la app principal de nuestro proyecto y agregarla a la lista de, INSTALLED_APPS

'nombre_dado.apps.Nombre_dadoConfig',

### Configuración de la Base de Datos

1. Instala el conector para PostgreSQL:

   ```bash
   py -m pip install psycopg[binary]
   ```

2. En `config/settings.py`, agrega la configuración de la base de datos:

   ```python
   DATABASES = {
       'default': {
           'ENGINE': 'django.db.backends.postgresql',
           'NAME': 'db_practica_orm',
           'USER': 'postgres',
           'PASSWORD': 'admin',
           'HOST': '127.0.0.1',
           'PORT': '5432',
       }
   }
   ```

### crear modelos para la aplicación, en el archivo models.py dentro de tu aplicación:

    from django.db import models

    class Producto(models.Model):
        nombre = models.CharField(max_length=100)
        precio = models.DecimalField(max_digits=10, decimal_places=2)
        categoria = models.ForeignKey('Categoria', on_delete=models.CASCADE)

    class Categoria(models.Model):
        nombre = models.CharField(max_length=50)


1. Genera los archivos de migración:

   ```bash
   python manage.py makemigrations
   ```

2. Aplica las migraciones:

   ```bash
   python manage.py migrate
    python manage.py sqlmigrate aplicacion 0001
    "nombre_aplicacion" "numero de migracion" en Snake case(Las migraciones en Django suelen numerarse secuencialmente (0001, 0002, etc.))
   ```

### Creación de Vistas y Plantillas

1. Crea las vistas para listar y agregar productos en `producto/views.py`.

2. Crea una carpeta `templates` dentro de la aplicación `producto/templates`.

3. Crea archivos HTML para listar, agregar, editar y eliminar productos. Crear una plantilla base, se debe crear un archivo llamado base.html en la carpeta web/templates que contenga la estructura general de la web a mostrar, usando blocks y marcando con fondos de colores (background) cada sección para mostrar de manera más explícita la separación entre éstas (opcional).
    
	base.html -> estructura base
		include: navbar.html -> barra de navegación

	layout.html -> template a reutilizar
		extends: base.html -> estructura base

	index.html -> página principal
		extends: layout.html -> template a reutilizar

	lista_libros.html -> página para listar libros
		extends: layout.html -> template a reutilizar

	crear_libro.html -> página de creación
		extends: layout.html -> template a reutilizar

	editar_libro.html -> página de edición
		extends: layout.html -> template a reutilizar

4. Crear las vistas que se encargan de recibir solicitudes HTTP y devolver respuestas HTTP
    def recetas(request):
    return render(request, 'recetas.html', {})

5. Configurar urls.py en la aplicación creada y asociarlas a las vistas correspondientes:
	    config/urls.py
	    from django.urls import path, include
    urlpatterns = [
        path('admin/', admin.site.urls),
        path('producto/', include('producto.urls')),
    ]
    producto/views.py

### Creación de Formularios

1. Crea un archivo `forms.py` en la aplicación `producto`.

2. Define los formularios necesarios en `forms.py`.

### crear forms.py en la aplicacion creada y define los formularios necesarios en 'forms.py'
	producto/forms.py
	form django import forms
	class ProductoForm(forms.ModelForm)
    
### instalar librerias para formularios y bootstrap
	pip install crispy-bootstrap5
	pip install django-bootstrap-v5
	pip install django-crispy-forms
    
### configurar librerias, las librerias deben ser colocadas antes que nuestra aplicación
	config/settigs.py

	INSTALLED_APPS:
	'bootstrap5',  # bootstrap 5
    	'crispy_forms',  # crispy forms 
    	'crispy_bootstrap5'

	CRISPY_ALLOWED_TEMPLATE_PACKS = "bootstrap5"
	CRISPY_TEMPLATE_PACK = 'bootstrap5'
	
### Para poder mostrar un contenido estático (como imágenes, videos,etc) se debe crear la carpeta web/static
    	Agregar  class=“container” a todos los templates de tu proyecto, para que Bootstrap pueda funcionar.

    Manejo de contenido estático
    static
    Para agregar contenido desde un archivo colocar al inicio del html:
        {% load static %}
    Despues se modifica cada ruta de los archivos que se quiere agregar, colocando:
        {% static "más nombre del archivo con extension" %}

### levantar el proyecto
	python manage.py runserver