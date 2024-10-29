# Proyecto Django
### Crear el proyecto.
	pip install django
	django-admin startproject nombre_dado
### Levantar servidor Django:
    Entrar al directorio del proyecto
        cd nombre_dado
        python manage.py migrate
        python manage.py startapp web

###  Agregar esta app a la lista de aplicaciones instaladas, debemos abrir el archivo settings.py presente en el directorio de
la app principal de nuestro proyecto y agregarla a la lista de, INSTALLED_APPS

'nombre_dado.apps.Nombre_dadoConfig',

### Si tengo una base de datos ya creada ocupar:
    python manage.py inspectdb >web\models.py
Para obtener el modelo de la base y copiarlo en el archivo models.py


###  Crear views para listar y agregar.
    producto/views.py
	
###  Luego, dentro del directorio de la app web se debe crear un directorio llamada templates y a continuación dentro de ella crear los html que uno necesite ocupar.
index.html, about.html y welcome.html

###  Para habilitar las tres URLs distintas, se deben crear tres vistas en el archivo views.py dentro de la carpeta web. Cada vista debe retornar un render con los datos necesarios para desplegar cada uno de los archivos HTML creados anteriormente.

#### Crear las vistas que se encargan de recibir solicitudes HTTP y devolver respuestas HTTP:
Crear las vistas en forma de Funcion o Clases

    def recetas(request):
    return render(request, 'recetas.html', {})
	
	Configurar urls.py en la aplicación creada y asociarlas a las vistas correspondientes:
	    config/urls.py
	    from django.urls import path, include
    urlpatterns = [
        path('admin/', admin.site.urls),
        path('producto/', include('producto.urls')),
    ]

###  Crear una plantilla base, se debe crear un archivo llamado base.html en la carpeta web/templates que contenga la estructura general de la web a mostrar, usando blocks y marcando con fondos de colores (background) cada sección para mostrar de manera más explícita la separación entre éstas (opcional).

###  Una vez creado el archivo base.html, debes reemplazar el contenido de tus archivos index.html, about.html y welcome.html para que, extiendan la plantilla base utilizando. 
	{% extends 'base.html' %}
	
    Luego reemplazar el contenido (block content) por el contenido correspondiente a cada una de las vistas (mensaje).
	{% block 'content' %}
	<div>
    	mensaje
	</div>
	{% endblock  'content' %}

###  Añadir bootstrap a nuestro sitio web, debemos agregar los archivos css y JavaScript de Bootstrap.

### crear forms.py en la aplicacion creada y define los formularios necesarios en 'forms.py'
	producto/forms.py
	form django import forms
	class ProductoForm(forms.ModelForm)
    
### instalar librerias para formularios y bootstrap.
	pip install crispy-bootstrap5
	pip install django-bootstrap-v5
	pip install django-crispy-forms
    
### configurar librerias.
	config/settigs.py
	INSTALLED_APPS:
	'bootstrap5',  # bootstrap 5
    	'crispy_forms',  # crispy forms 
    	'crispy_bootstrap5'

	CRISPY_ALLOWED_TEMPLATE_PACKS = "bootstrap5"
	CRISPY_TEMPLATE_PACK = 'bootstrap5'

### Para poder mostrar un contenido estático (como imágenes, videos,etc) se debe crear la carpeta web/static
	Agregar  class=“container” a todos los templates de tu proyecto, para que Bootstrap pueda funcionar.

#### Manejo de contenido estático
    static
    Para agregar contenido desde un archivo colocar al inicio del html:
        {% load static %}
    
    Despues se modifica cada ruta de los archivos que se quiere agregar, colocando:
        {% static "más nombre del archivo con extension" %} 

### Levantar el proyecto.
      python manage.py runserver
      
-----------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------

## Instalación y verificación
### Instalar django
    pip install django=="numero de version"
### Verificar el estado de la instalacion
    python -m django version
### Ver comando disponibles en Django
    python -m django help

--------------------------------------------------------------------------------------------------------------

### Gestión de dependencias
● pip install -r requirements.txt -> para instalar las dependencias desde un archivo  
● pip freeze > requirements.txt -> para generar un respaldo de los paquetes instalados creando un
archivo requirements.txt  
● pip install astral==2.2 -> para instalar una versión específica de un paquete que necesitemos, en
este ejemplo astral 2.2  

-----------------------------------------------------------------------------------------------------------------

## Operaciones Comunes:

#### Informacion general de comandos de Django
	python manage.py help

#### Informacion detallada de un comando especifico de Django
	py manage.py help nombre_subcomando
 
#### Crear proyecto
    python -m django startproject "nombre proyecto"

#### Acceder a la carpeta creada. Crear aplicacion
    python manage.py startapp "nombre proyecto"-----manage.py "archivo para activar la iniciacion del proyecto"

#### Generar archivos de migracion. 
    python manage.py makemigrations
Las migraciones son archivos que contienen cambios en el esquema de la base de datos. El comando makemigrations analiza los modelos definidos en tu proyecto y genera los archivos de migración correspondientes que luego podrán ser aplicados a la base de datos.

#### Mostrar el estado de las migraciones en tu proyecto. 
	python manage.py showmigrations
Indica qué migraciones han sido aplicadas y cuáles están pendientes de aplicación. Puedes utilizarlo para verificar el estado de las migraciones y asegurarte de que todo esté sincronizado correctamente.

#### Aplicar los cambios creados por makemigrations
	python manage.py migrate
Ejecuta los archivos de migración pendientes en el orden adecuado para asegurar que la estructura de la base de datos esté sincronizada con los modelos definidos en tu proyecto.

#### Crear super usuario
	python manage.py createsuperuser

#### Restablecer la base de datos al estado en que estaba inmediatamente después de que migrate fue ejecutado.
	py manage.py flush

#### Ejecutar nuestro proyecto de manera local
	python manage.py runserver

#### Permite observar el SQL antes de aplicar una determinada migración,
	python manage.py sqlmigrate app migration_name: 

#### Iniciar una sesión interactiva de Django shell.
	python manage.py shell
	Ejemplos:
	import mysite.settings as S
	print(S.__file__)
	print(S.BASE_DIR)

Proporciona una interfaz de línea de comandos para interactuar con tu proyecto Django. Puedes ejecutar consultas de base de datos, crear, modificar o eliminar objetos, realizar pruebas, entre otras tareas.

#### Inicia una consola interactiva de la base de datos. 
	python manage.py dbshell

Te permite acceder directamente a la línea de comandos de tu base de datos, lo que puede ser útil para ejecutar consultas SQL personalizadas o realizar tareas específicas directamente en la base de datos.

#### Exporta los datos de la base de datos en formato JSON o YAML. 
	python manage.py dumpdata 
Puedes especificar qué modelos o aplicaciones deseas incluir en la exportación. Es útil para realizar copias de seguridad de los datos o para transferirlos entre diferentes entornos.

#### Ejecuta todas las pruebas definidas en los archivos tests.py de tus aplicaciones y muestra los resultados en la consola.
	 python manage.py test 
	 
#### Inicia un servidor de desarrollo con una copia de la base de datos en memoria y cargando datos de prueba.
	python manage.py testserver 
	
#### Muestra las diferencias entre los archivos de configuración de Django (settings.py) y la configuración actual de tu proyecto. 
	python manage.py diffsettings

Puedes utilizarlo para ver los cambios realizados en la configuración o para solucionar problemas relacionados con la configuración de tu proyecto.
-----------------------------------------------------------------------------------------------------------------

#### Integración con una base de datos existente por medio de Django
    python manage.py inspetdb > web/models.py

#### Integración con una base de datos existente por medio de pgAdmin 
    \COPY "peliculas" FROM 'C:\Users\usuario\peliculas.csv' WITH CSV;

#### python manage.py migrate > log.txt
    > log.txt
    El operador > es un redireccionamiento de flujo en Unix/Linux.
    En este caso, redirige la salida estándar (normalmente mostrada en la consola) hacia un archivo llamado log.txt. La salida de estos procesos (información, advertencias, errores) se captura en el archivo log.txt.

-----------------------------------------------------------------------------------------------------------------

## Formularios de contexto. Sirven para interactuar con el usuario.

### Formulario Form

    from django import forms
    class ContactFormForm(forms.Form):
        customer_email = forms.EmailField(label='Correo')
        customer_name = forms.CharField(max_length=64, label='Nombre')
        message = forms.CharField(label='Mensaje')

### Formulario clase Modal Form, creación de un formulario basado en un modelo. Un modelo corresponde a una tabla de una base de datos y sus atributos corresponden a las columnas de una tabla.

    from .models import ContacForm
    class ContactFormModelForm(forms.ModelForm):
        class Meta:
            model = ContactForm
            fields = ['customer_email','customer_name', 'message']

### El formulario es procesado por una vista en views.py
    class ContactFormForm(forms.Form):
        customer_email = forms.EmailField(label='Correo')
        customer_name = forms.CharField(max_length=64, label='Nombre')
        message = forms.CharField(label='Mensaje')
        