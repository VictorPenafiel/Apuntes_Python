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
   GRANT ALL PRIVILEGES ON DATABASE db_practica_orm TO user_db;
   
   en caso que no funcione
   GRANT postgres TO user_db
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
   pip install psycopg2
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
  py -m pip install psycopg[binary]
   ```

2. Aplica las migraciones:

   ```bash
    python manage.py migrate
    python manage.py sqlmigrate aplicacion 0001
    "nombre_aplicacion" "numero de migracion" en snake case(Las migraciones en Django suelen numerarse secuencialmente (0001, 0002, etc.))
   ```

### Creación de Vistas y Plantillas

#### Crea las vistas para listar y agregar productos en `producto/views.py`.

####  Crea una carpeta `templates` dentro de la aplicación `producto/templates`.

####  Crea archivos HTML para listar, agregar, editar y eliminar productos. Crear una plantilla base, se debe crear un archivo llamado base.html en la carpeta web/templates que contenga la estructura general de la web a mostrar, usando blocks y marcando con fondos de colores (background) cada sección para mostrar de manera más explícita la separación entre éstas (opcional).
    
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

####  Crear las vistas que se encargan de recibir solicitudes HTTP y devolver respuestas HTTP
    def recetas(request):
    return render(request, 'recetas.html', {})

#### Configurar urls.py en la aplicación creada y asociarlas a las vistas correspondientes:  

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



-----------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------

# Uso del ORM de Django  
El ORM (Object-Relational Mapping) de Django te permite interactuar con bases de datos relacionales utilizando objetos Python en lugar de SQL directo.

### Definir un Modelo
### Crea una aplicación de Django: python manage.py startapp nombre_app
### Define tu modelo en el archivo models.py dentro de tu aplicación:
    from django.db import models

    class Producto(models.Model):
        nombre = models.CharField(max_length=100)
        precio = models.DecimalField(max_digits=10, decimal_places=2)
        categoria = models.ForeignKey('Categoria', on_delete=models.CASCADE)

    class Categoria(models.Model):
        nombre = models.CharField(max_length=50)

### realizar migraciones
    python manage.py makemigrations
    python manage.py migrate
    python manage.py sqlmigrate aplicacion 0001

### Crear un registro
    producto = Producto(nombre="Producto 1", precio=29.99, categoria=categoria_objeto)
    producto.save()

### Actualizar un registro
    producto = Producto.objects.get(pk=1)
    producto.nombre = "Nuevo Nombre"
    producto.save()

### Eliminar un registro
    producto = Producto.objects.get(pk=1)
    producto.delete()
    Consultas

### Obtener todos los productos
    productos = Producto.objects.all()

### Obtener productos con precio mayor a $20
    productos_caros = Producto.objects.filter(precio__gt=20)

### Obtener un producto por su nombre
    producto = Producto.objects.get(nombre="Producto 1")

### Conteo de productos por categoría
    conteo_por_categoria = Producto.objects.values('categoria__nombre').annotate(conteo=models.Count('categoria'))


-----------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------


## Consultas de filtrado utilizan ORM

### Casos típicos de uso
#### registro
	Modelo.objects.get(*args, **kwargs)
	
#### Todos los registros
	Modelo.objects.all()
	En SQL : SELECT * FROM app_modelo

#### Algunso registros
#### Cumplen filtros
	Modelo.objects.filter (**kwargs)
#### No cumplen filtros
	Modelo.objects.exclude (**kwargs)
Ambos métodos pueden encadenarse

#### Rango de registros
	Modelo.objects.metodo() [i:j:k]

-----------------------------------------------------------------------------------------------------------------
## Consultas Avanzadas

### Consulta usando JOIN (relaciones)
    productos_categoria = Producto.objects.filter(categoria__nombre="Electrónicos")
    
### Consulta con OR y AND
    from django.db.models import Q
    productos_filtrados = Producto.objects.filter(Q(precio__gt=10) | Q(categoria__nombre="Ropa"))

### Consulta con JOIN y condiciones complejas
    productos_interesantes = Producto.objects.filter(Q(precio__lt=50) & Q(categoria__nombre="Electrónicos"))
    Relaciones
    ForeignKey: Para relaciones uno a muchos.
    OneToOneField: Para relaciones uno a uno.
    ManyToManyField: Para relaciones muchos a muchos.
    class Orden(models.Model):
    cliente = models.ForeignKey('Cliente', on_delete=models.CASCADE)
    productos = models.ManyToManyField(Producto)

    class Cliente(models.Model):
        nombre = models.CharField(max_length=100)
    
Estos son solo ejemplos básicos del uso del ORM de Django. Puedes consultar la documentación oficial de Django para más detalles y ejemplos avanzados.

-----------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------
## Iniciar Sesion

    def iniciar_sesion(request):
        if request.method == 'POST':  # si el request es de tipo post
            username = request.POST['username']  # captura username del request
            password = request.POST['password']  # captura password del request
            user = authenticate(request, username=username, password=password)  # se captura el usuario encontrado
            if user is not None:  # si el usuario autenticado no viene vacio, quiere decir es validas sus credenciales
                login(request, user)
                return redirect('lista_vehiculos')
            else:
                messages.error(request, 'Usuario o password inválidas')
                return render(request, 'login.html')
        return render(request, 'login.html')  # tipo get
    
    </li>
    <li class="float-right">
    <a class="nav-link text-primary fs-5" href="#"> Hola, {{user.username}}</a>
    </li>
    
    
    {% if perms.vehiculo.add_vehiculo %}
    
    {% load bootstrap5 %}
    {% load static %}
    {% block content %}
    
    <nav class="navbar navbar-bg-dark navbar-expand-lg ">
      <div class="container-fluid">
        <a class="navbar-brand text-primary" href="{% url 'index' %}">
          <img src="{% static 'vehiculo/img/autoCHICO.jpg' %}" alt="autoCHICO">
        </a>
        <button class="navbar-toggler bg-primary" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <a class="nav-link text-primary" aria-current="page" href="{% url 'index' %}">Inicio</a>
            </li>
            <li class="nav-item">
              <a class="nav-link text-primary" href="{% url 'lista_vehiculos' %}">Listar</a>
            </li>
            {% if perms.vehiculo.add_vehiculo %}
            <li class="nav-item">
              <a class="nav-link text-primary" href="{% url 'add' %}" >Agregar</a>
            </li>
    
            {% elif user.is_authenticated %}
            <li class="nav-item">
              <a class="nav-link text-warning" href="#" >Sin permiso para agregar vehiculos</a>
            </li>
             {% endif %}
    
    
    
          </ul>
    
          <ul class="navbar-nav ml-auto mb-2 mb-lg-0">
            {% if user.is_authenticated %}
             <li class="nav-item">
              <a class="nav-link text-primary fs-5" href="{% url 'logout' %}" >Cerrar Sesion</a>
            </li>
            <li class="float-right">
              <a class="nav-link text-primary fs-5" href="#"> Hola, {{user.username}}</a>
            </li>
            {% else %}
            <li class="nav-item">
              <a class="nav-link text-primary fs-5" href="{% url 'login' %}" >Iniciar Sesion</a>
            </li>
            {% endif %}
          </ul>
    
        </div>
      </div>
    </nav>
    {% endblock %}

-----------------------------------------------------------------------------------------------------------------
### permisos por usuario

    from django.contrib.auth.models import User, Permission

    usuario = User.objects.get(username='usuariotest')

    usuario.get_all_permissions()


### permisos para un modelo en especifico

    from book.models import Book
    
    from django.contrib.contenttypes.models import ContentType
    
    from django.contrib.auth.models import Permission
    
    content_type=ContentType.objects.get_for_model(Book)
    
    book_permissions=Permission.objects.filter(content_type=content_type)
    
    [permiso.codename for permiso in book_permissions]
    