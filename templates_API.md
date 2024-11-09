## Api (application program interface)
Interfaz de acceso que permite comunicar programas.

Librerias necesarias para trabajar con APIs

- `requests`: Libreria para conectarnos a APIs.
- `json`: (JavaScript object notation) Es un formato ligero de intercambio de datos. La libreria json es necesaria ya que permite interpretar el string entregado por request a objetos Python

## Api  rest (representational state transfer)
Interfaz estructurada que se caracteriza por tener 4 métodos para interactuar con ella. Modelo de arquitectura web basado en protocolo HTTP.
 
- `GET`: Consultar un recurso.
- `POST`: Crear un recurso.
- `PUT`: Editar un recurso.
- `DELETE`: Borrar un recurso.

### Postman
Aplicación que permite interactuar con APIs de manera fácil. Nos entrega el codigo necesario para conectarnos a la API
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
#### Debe crearse nueva variable que reciba el resultado de la inyección.  
#### Al inyectar las variables respectivas dentro del substitute, debe respetarse el siguiente formato:  
    nombre_var_html = nombre_var_python.  
Si hay mas de 1 variable, separar por comas.

## Ahora, generamos el archivo de salida:

    with open('salida.html','w') as outfile:
        outfile.write(document_template_nuevo)