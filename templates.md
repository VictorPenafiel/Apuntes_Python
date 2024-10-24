# Trabajando con Templates

## 1. Construcción del documento HTML

Construir el documento .html con la estructura, estilos y demás componentes deseados. Esto implica que el contenido dinámico (o contenido a insertar selectivamente) deben ser especificados mediante variables con prefijo $. Por ejemplo: `$nombre`

## 2. Proceso en Python

### Importación de módulos

python from string import Template


### Carga y procesamiento del archivo HTML

python
Cargar el archivo html (como lectura de archivo de texto plano). Coloque el nombre deseado

with open('prueba01.html','r') as infile: entrada = infile.read()
Crear objeto Template con la variable recién recibida (entrada)

document_template = Template(entrada)


### Definición y sustitución de valores

python
Definir los valores de las variables que se aspiran insertar en el template

sec = "0008" nom = "Carlos" fecha = "28/01/2022"
Inyectar los valores anteriores al template

document_template_nuevo = document_template.substitute(seccion = sec, nombre = nom, fecha = fecha)


### Generación del archivo de salida

python
Ahora, generamos el archivo de salida:

with open('salida.html','w') as outfile: outfile.write(document_template_nuevo)


### Puntos clave a considerar

- Debe crearse una nueva variable que reciba el resultado de la inyección.
- Al inyectar las variables respectivas dentro del substitute, debe respetarse el siguiente formato:
  nombre_var_html = nombre_var_python. Si hay más de una variable, separar por comas.
