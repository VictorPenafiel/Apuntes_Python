## Trabajando con Templates:

1) Construir el documento .html con la estructura, estilos y demás componentes deseados.
Esto implica que, el contenido dinámico (o contenido a insertar selectivamente) deben ser 
especificados mediante variable con prefijo $.  Ejm:   $nombre

2) En el script de Python realizar las siguiente instrucciones:

from string import Template

## Cargar el archivo html (como lectura de archivo de texto plano). Coloque el nombre deseado

    with open('prueba01.html','r') as infile:
        entrada = infile.read()

## Crear objeto Template con la variable recién recibida (entrada)

    document_template = Template(entrada)

## Definir los valores de las variable que se aspiran insertar en el template.
    sec = "0008"  
    nom = "Victor"  
    fecha = "28/01/2024"  

## Inyectar los valores anteriores al template

document_template_nuevo = document_template.substitute(seccion = sec, nombre = nom, fecha = fecha)

### Debe crearse nueva variable que reciba el resultado de la inyección.
### Al inyectar las variables respectivas dentro del substitute, debe respetarse el siguiente formato:
    nombre_var_html = nombre_var_python.  
Si hay mas de 1 variable, separar por comas.

## Ahora, generamos el archivo de salida:

with open('salida.html','w') as outfile:
    outfile.write(document_template_nuevo)