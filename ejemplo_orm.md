<!-- 
## Paso a Paso: Proyecto Django - Creación de un Sistema de Laboratorios

### 1. Crear la Base de Datos

#### Iniciar sesión en una sesión interactiva de postgresql: 
    sudo -u postgres psql

#### Creación de la base de Datos:
    CREATE DATABASE db_final_orm;

#### Creando el usuario:
    CREATE USER userdjango WITH PASSWORD 'userdjango';

#### Asignando el usuario a la base de datos:
    GRANT ALL PRIVILEGES ON DATABASE db_final_orm TO userdjango;


### 1.2.1 Crear un nuevo proyecto Django que debe ser construido a partir de un ambiente virtual
    mkvirtualenv django-psql-orm
   - Ubicación: C:\PycharmProjects\practica_final_orm_django
   - Entorno virtual: Virtualenv, Python 3.11
   - Nombre de la aplicación: laboratorio

### 1.2.2 Instalar paquetes requeridos
#### Django (framework)
        pip install django
#### psycopg2 (conector de PostgreSQL)
        
    pip install psycopg2

###  1.2.3 Inicializar el proyecto y la aplicación
   ```bash
   cd C:\PycharmProjects\practica_final_orm_django
   django-admin startproject config
   cd config
   django-admin startapp laboratorio
   ```

###  1.2.3 Inicializar el proyecto y la aplicación
   ```python
   INSTALLED_APPS = [
       ...
       'laboratorio.apps.LaboratorioConfig',
   ]
   ```

<!-- ### 1.2.5 Configurar la base de datos en `settings.py`
   ```python
   DATABASES = {
       "default": {
           "ENGINE": "django.db.backends.postgresql",
           "NAME": "practica_final_orm_django",
           "USER": "userdjango",
           "PASSWORD": "userdjango",
           "HOST": 'localhost',
           "PORT": "5432",
       }
   }
   ``` -->

### 1.2.6 Realizar migraciones y crear el superusuario
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   python manage.py createsuperuser
   ```

1.3 Ejecutar el proyecto
   ```bash
   python manage.py runserver
   ```

### 2. Crear el Modelo

<!-- 2.1 Crear los modelos en `models.py` (Ejemplo)

```python
from datetime import date
from django.core.validators import MinValueValidator
from django.db import models

class Laboratorio(models.Model):
    nombre = models.CharField(max_length=20)

    def __str__(self):
        return self.nombre

class DirectorGeneral(models.Model):
    nombre = models.CharField(max_length=200)
    laboratorio = models.OneToOneField(Laboratorio, on_delete=models.CASCADE)

    def __str__(self):
        return self.nombre

class Producto(models.Model):
    nombre = models.CharField(max_length=40)
    laboratorio = models.ForeignKey(Laboratorio, on_delete=models.CASCADE)
    f_fabricacion = models.DateField(validators=[MinValueValidator(limit_value=date(2015, 1, 1))])
    p_costo = models.DecimalField(max_digits=10, decimal_places=2)
    p_venta = models.DecimalField(max_digits=10, decimal_places=2)

    def __str__(self):
        return self.nombre -->
```

### 2.2 Realizar migraciones y actualizar la base de datos

```bash
python manage.py makemigrations
python manage.py migrate
```

### 2.3 Registrar los modelos en `admin.py`

```python
from django.contrib import admin
from .models import Laboratorio, DirectorGeneral, Producto

class LaboratorioAdmin(admin.ModelAdmin):
    fields = ['nombre']
    list_display = ('id','nombre')
    list_display_links = ['nombre']

class DirectorGeneralAdmin(admin.ModelAdmin):
    list_display = ('id', 'nombre', 'laboratorio')
    ordering = ('nombre',)
    list_display_links = ['nombre','laboratorio']
    list_per_page = 2

class ProductoAdmin(admin.ModelAdmin):
    fields = ['nombre', 'laboratorio', 'f_fabricacion', 'p_costo','p_venta']
    list_display = ('id','nombre', 'laboratorio', 'f_fabricacion', 'p_costo', 'p_venta')
    list_display_links = ['nombre', 'laboratorio']
    ordering = ('nombre','laboratorio')
    list_filter = ('nombre', 'laboratorio')

admin.site.register(Laboratorio, LaboratorioAdmin)
admin.site.register(DirectorGeneral, DirectorGeneralAdmin)
admin.site.register(Producto, ProductoAdmin)
```

### 2.4 Realizar migraciones y ejecutar el servidor

```bash
python manage.py makemigrations
python manage.py migrate
python manage.py runserver
```


### 2.5. Agregar Jazzmin al Panel de Administración (Opcional)

Jazzmin es un tema personalizado para el panel de administración de Django que brinda un aspecto moderno y elegante. A continuación, te mostraré cómo agregar Jazzmin a tu proyecto:

2.5.1 Instalar Jazzmin

Instala el paquete de Jazzmin en tu entorno virtual:

```bash
pip install jazzmin
```

2.5.2 Configurar Jazzmin

Agrega 'jazzmin' a la lista de aplicaciones instaladas en tu archivo `settings.py`:

```python
INSTALLED_APPS = [
    ...
    'jazzmin',
    'laboratorio.apps.LaboratorioConfig',
]
```

2.5.3 Personalizar la Configuración de Jazzmin

En tu archivo `settings.py`, agrega la configuración de Jazzmin al final del archivo:

```python
# Configuración de Jazzmin
JAZZMIN_SETTINGS = {
    "site_title": "Laboratorio Admin",
    "site_header": "Laboratorio Administration",
    "site_logo": "path/to/your/logo.png",  # Ruta al logotipo de tu sitio
    "welcome_sign": "Bienvenido al panel de administración de Laboratorio",
    "search_model": "laboratorio.Producto",  # Modelo para buscar en la barra de búsqueda
    "user_avatar": None,  # Puedes establecer la ruta al avatar de usuario si lo deseas
    "show_sidebar": True,
    "navigation_expanded": False,
    "hide_apps": [],
    "hide_models": [],
    "order_with_respect_to": [],
}
```

2.5.4 Agregar la URL de Jazzmin

En tu archivo `config/urls.py`, agrega la URL de Jazzmin al patrón de URL de Django:

```python
from django.urls import path
from django.contrib import admin
from django.conf import settings

urlpatterns = [
    ...
    path('admin/', admin.site.urls),
]

# Agregar la URL de Jazzmin solo en modo DEBUG
if settings.DEBUG:
    urlpatterns += [path('admin/', include('jazzmin.urls'))]
```

2.5.5 Ejecutar el Servidor y Acceder al Nuevo Panel de Administración

```bash
python manage.py runserver
```

---

2.6 Añadir usuarios, laboratorios y productos a través del Admin
   - Realizar los cambios y guardarlos

### 3. Realizar Consultas

3.1 Ingresar a la Shell de Python

```bash
python manage.py shell
```

3.2 Importar Modelos

```python
from laboratorio.models import Laboratorio, DirectorGeneral, Producto
```

3.3 Realizar Consultas (Ejemplo)

```python
laboratorios = Laboratorio.objects.all()
print('\n'.join(str(lab.nombre) for lab in laboratorios))
```

### 4. Realizar Cambios al Modelo

4.1 Guardar una nueva migración con un alias específico

```bash
python manage.py makemigrations --name actualizado_campos
python manage.py migrate
```

4.2 Consultar las migraciones existentes

```bash
python manage.py showmigrations
```

### 5. CRUD (Create, Read, Update, Delete)

5.1 Crear carpetas de plantillas
   - Crear la carpeta `templates` en el directorio de la aplicación

5.2 Configurar URLs

En `config/urls.py`:

```python
from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('laboratorio/', include('laboratorio.urls')),
    path('', include('laboratorio.urls'))
]
```

5.3 Crear archivos `laboratorio/urls.py` y `laboratorio/views.py`

5.4 Crear controladores en `views.py` para las vistas del CRUD

```python
from django.shortcuts import render, redirect
from .models import Laboratorio

# Controladores-vistas para CRUD
def insertar_lab(request):
    if request.method == "POST":
        nombre = request.POST['lab_nombre']
        ciudad = request.POST['lab_ciudad']
        pais = request.POST['lab_pais']
        laboratorio = Laboratorio(nombre=nombre, ciudad=ciudad, pais=pais)
        laboratorio.save()
        return redirect('mostrar-lab/')
    else:
        return render(request, 'insertar-lab.html')

# obtener los Laboratorios
def mostrar_lab(request):
    laboratorios = Laboratorio.objects.all()
    num_visits = request.session.get('num_visits', 0)
    request.session['num_visits'] = num_visits + 1
    context = {
        'laboratorios':laboratorios,
        'num_visits': num_visits,
    }
    print(laboratorios.values())
    return render(request,'mostrar-lab.html', context)
# Editar Laboratorio
def editar_lab(request,pk):
    laboratorio = Laboratorio.objects.get(id=pk)
    # if request.method == 'POST':
    # return redirect('/crudapp/mostrar')
    context = {
        'laboratorio': laboratorio,
    }
    return render(request=request, template_name='editar-emp.html', context=context)
def actualizar_laboratorio(request, id):
    lab_nombre = request.POST['lab_nombre']
    lab_ciudad = request.POST['lab_ciudad']
    lab_pais = request.POST['lab_pais']
    laboratorio = Laboratorio.objects.get(id=id)
    laboratorio.nombre= lab_nombre
    laboratorio.ciudad = lab_ciudad
    laboratorio.pais = lab_pais
    laboratorio.save()
    return redirect('/laboratorio/mostrar-lab')

# Eliminar Laboratorio
def eliminar_lab(request, pk):
    laboratorio = Laboratorio.objects.get(id=pk)
    if request.method == 'POST':
    laboratorio.delete()
    return redirect('/laboratorio/mostrar-lab')
    context = {
        'laboratorio': laboratorio,
    }
    return render(request, 'eliminar-lab.html', context)

```
### template
laboratorio/templates/mostrar-lab-html

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Buscar Empleados</title>
    <style>
        table {
            border: 8px outset;
            border-spacing: 10px;
            padding: 20px;
            margin-left: auto;
            margin-right: auto;
        }
        th,
        td {
            padding: 5px;
            border: 1px solid;
        }
    </style>
</head>
<body>
    <h2 style="text-align:center">Informacion de Laboratorios</h2>
    <table align="center" style="margin: 0px auto;">
        <thead>
            <tr>
                <th>Nombre</th>
                <th>Ciudad</th>
                <th>Pais</th>
                <th>Edit</th>
                <th>Delete</th>
            </tr>
        </thead>
        <tbody>
            {% for laboratorio in laboratorios %}
            <tr>
                <td>{{laboratorio.nombre}}</td>
                <td>{{laboratorio.ciudad}}</td>
                <td>{{laboratorio.pais}}</td>
                <td>
                    <a href="/laboratorio/editar/{{laboratorio.pk}}">Actualizar</a>
                </td>
                <td>
                    <a href="/laboratorio/eliminar/{{laboratorio.pk}}">Eliminar</a>
                </td>
            </tr>
            {% endfor %}
        </tbody>
    </table>
    <br><br>
    <div class="alert alert-danger" role="alert">
        ¿Información de los Laboratorios?
    </div>
    <p>
        <a href="{% url 'insertar-lab' %}"><-- Ir a la pagina de Inicio</a>
    </p>
    <p>Usted ha visitado esta página {{ num_visits }} veces.</p>
</body>
</html>
```

laboratorio/templates/insertar-lab.html

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Empleados</title>
    <style>
        table {
            border: 8px outset;
            border-radius: 10px;
            border-spacing: 10px;
            padding: 20px;
            margin-left: auto;
            margin-right: auto;
        }
        th,
        td {
            padding: 5px;
        }
    </style>
</head>
<body>
    <h2 style="text-align:center">Ingresar los Datos del Laboratorio</h2>
    <form method="POST">
        {% csrf_token %}
        <table style="width:50%" align="center">
            <tr>
                <td>Nombre:</td>
                <td><input type="text" placeholder="Ingrese el nombre del laboratorio" name="lab_nombre"></td>
            </tr>
            <tr>
                <td>Ciudad</td>
                <td><input type="text" placeholder="Ingrese la Ciudad del Laboratorio" name="lab_ciudad"></td>
            </tr>
            <tr>
                <td>Pais</td>
                <td><input type="text" placeholder="Ingrese el Pais del Laboratorio" name="lab_pais"></td>
            </tr>
            <tr>
                <td colspan="2" align="center"><input type="submit" class="btn btn-success"></td>
            </tr>
        </table>
        <br><br>
        <div class="alert alert-danger" role="alert">
            ¿Información de los Laboratorios?
        </div>
        <p>
            <a href="{% url 'mostrar-lab' %}">Ir a información del los laboratorios--></a>
        </p>
    </form>
</body>
</html>
```

laboratorio/templates/editar-lab.html

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Actualizar Laboratorio</title>
    <style>
        table {
            border: 8px outset;
            border-radius: 10px;
            border-spacing: 10px;
            padding: 20px;
            margin-left: auto;
            margin-right: auto;
        }
        th, td {
            padding: 5px;
        }
    </style>
</head>
<body>
    <h2 style="text-align:center">Actualizar Laboratorio</h2>
    <form action="actualizar-laboratorio/{{ laboratorio.id }}" method="POST">
        {% csrf_token %}
        <table style="width:50%" align="center">
            <tr>
                <td>Nombre</td>
                <td><input type="text" value="{{ laboratorio.nombre }}" name="lab_nombre"></td>
            </tr>
            <tr>
                <td>Ciudad</td>
                <td><input type="text" value="{{ laboratorio.ciudad }}" name="lab_ciudad"></td>
            </tr>
            <tr>
                <td>Pais</td>
                <td><input type="text" value="{{ laboratorio.pais }}" name="lab_pais"></td>
            </tr>
            <tr>
                <td colspan="2" align="center"><input type="submit" class="btn btn-success"></td>
            </tr>
        </table>
    </form>
</body>
</html>
```

laboratorio/templates/eliminar-lab.html

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Eliminar un Laboratorio</title>
</head>
<body>
    <form action="" method="POST">
        {% csrf_token %}
        <br><br>
        <div class="alert alert-danger" role="alert">
            Estas seguro que deseas eliminar el laboratorio: "{{ laboratorio.nombre }}"?
        </div>
        <p>
            <a href="{% url 'mostrar-lab' %}"><-- Retornar</a>
        </p>
        <p>
            <input class="btn btn-danger" type="submit" value="Confirm">
        </p>
    </form>
</body>
</html>
```

### Realice unas pruebas unitarias al modelo Laboratorio 
laboratorio/tests.py

```python
from django.test import TestCase
from django.test import SimpleTestCase
from django.urls import reverse
from .models import Laboratorio

class LaboratorioTests(TestCase):
    @classmethod
    def setUpTestData(cls):
        cls.laboratorio = Laboratorio.objects.create(
            nombre="Laboratorio 1",
            ciudad='Ciudad 1',
            pais='Pais 1'
        )

    def test_laboratorio_content(self):
        self.assertEqual(self.laboratorio.nombre, "Laboratorio 1")
        self.assertEqual(self.laboratorio.ciudad, "Ciudad 1")
        self.assertEqual(self.laboratorio.pais, "Pais 1")

    def test_existe_url_correcta(self):
        response = self.client.get("/laboratorio/")
        self.assertEqual(response.status_code, 200)

    def test_pagina(self):
        response = self.client.get(reverse("mostrar-lab"))
        self.assertEqual(response.status_code, 200)
        self.assertTemplateUsed(response, "mostrar-lab.html")
        self.assertContains(response, "Informacion de Laboratorios")
```
### Ejecutar la prueba:
    python manage.py test laboratorio
---
