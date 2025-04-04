# Python
Lenguaje interpretado multiparadigma y multiplataforma.  
El interprete de Pyhton funciona como un evaluador de expresiones.  
Python es un interprete de comandos (instrucciones)  
Los archivos fuentes de Pyhton son codificados en UTF-8

# Tipos de operadores
### Operadores de asignacion
Permiten realizar una operacion sobre una variable, pero a la vez sobreescribir esa misma variable.

    = Asignacion
    += Incremento y asignacion
    	+=1 Aumenta de 1 en 1
    -= Decremento y asignacion
    *= Multiplicacion y asignacion
    /= Division y asignacion

## Operador aritmetico
    + Suma
    - Resta
    - Negacion
    * Multiplicacion
    ** Exponente o potencia
    / Division: Numero real
    // Divison entera: Solo numero entero
    % Modulo: Resto del numero entero

### Operador Booleano (Comparar valores)
    == Igual a
    != Distinto a
    < Menor que
    > Mayor que
    <= Menor o igual que
    >= Mayor o igual que

### Operador Binario
    & and
    | or
    ^ Xor
    ~ Not
    << Desplazamiento izquierda
    >> Desplazamiento derecha 


-----------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------

# Tipos de datos

### Números
	Entero
		int: Precisión fija, convertida en long en caso de overflow
		long: Precisión arbitraria
		bool: Verdadero o falso, valor booleano
	
	Punto flotante
		float: Parte fraccional

	Complejos
		complex: Parte real y parte imaginaria, la cual se nombra con una j

### Secuencias
##### Secuencias Inmutables:
	Strings
		str " ": Cadena de texto
	Tuples
		tuple (): Puede contener objetos de diferentes tipos
	Bytes
		bytes
##### Secuencias Mutables:
	Listas 
		list []: Puede contener objetos de diferentes tipos, separados por coma. Todo elemento de una lista posee un indice interno que parte en subcero [0]
	Byte arrays
		bytearray

### Conjunto
	Sets:
		set {}: mutable, sin duplicados, sin orden
	Frozen set:

### Mappings
	Diccionarios:
		dict {}: Grupo clave:valor, se acceden solo por clave, son delimitados por {}
	“Matriz asociativa”

### Callable "invocable"
	Funciones
	Métodos
	Clases

### Modulos

-----------------------------------------------------------------------------------------------------------------
# POO (Programación orientada a objetos)

Paradigma de programación que se centra en almacenar comportamientos y caracteristicas similares a objetos

## Funcion
Abstracción y condensación de código en un objeto (script), con un nombre asociado que realiza una serie de tareas y devuelve un valor. 


def: Se ocupa para definir funciones, seguida del nombre de la función y la lista de parametros formales entre parentesis

    def mi_funcion (x,x1):

- `funcion`: print()
- `objeto.funcion`: "ejemplo".upper()
- `clase.funcion`: LinearRegression().fit(x,y)
- `modulo.funcion`: math.sqrt()


variable: Espacio de memoria donde colocar datos
constante: Espacio de memoria no modificable
parametro: Es un elemento que podrá ser utilizado dentro de la función para realizar sus calculos.  
argumento: Son los valores que tomará el parametro para ser utilizado dentro de la función.

*args: Permiten utilizar tantos parámetros como sean necesarios sin la necesidad que sean definidos a priori  
*kwargs: Permite un numero indeterminado de argumentos, pero estos argumentos deben incluir un nombre, ya que el nombre del argumento pasara a la función 


refactorización: Proceso de reorganizacion de código, evitando redundancia y condensando código repetido en funciones. Todo esto con el proceso de tener un código más entendible y claro.

docstring: Documentación interna que tienen las funciones y permiten describir sus parámetros, usos y retornos. 

#### Estilo google

```python
    def function_with_types_in_docstring(param1, param2):
    """Example function with types documented in the docstring.

    `PEP 484`_ type annotations are supported. If attribute, parameter, and
    return types are annotated according to `PEP 484`_, they do not need to be
    included in the docstring:

    Args:
        param1 (int): The first parameter.
        param2 (str): The second parameter.

    Returns:
        bool: The return value. True for success, False otherwise.
    """

    def elevar (base, exponente):
    """[summary]

    Args:
        base([type]:[description])
        exponente([type]:[description])

    Returns:
        [type]:[description]
        """return base**exponente"""
    """
    
```
[PEP 484](https://www.python.org/dev/peps/pep-0484/)

[Genera docstrings y comentarios en Python con Vertex AI](https://cloud.google.com/vertex-ai/generative-ai/docs/prompt-gallery/samples/code_generation_generate_python_docstrings__and__comments_25?hl=es-419)

## Clase
Clase: Corresponde al conjunto de atributos y metodos que permiten definir un objeto
Instancia = objeto. 
Instanciar: Crear un objeto a partir de una clase.
Objeto: Corresponde al conjunto de datos "atributo" y metodos definidos por la clase a la cual pertenece, en una instancia especifica de ella. Crear una instancia de una clase.
Atributo: Caracteristicas inherentes de una entidad, que la definen y que en su conjunto pueden representar un estado de la misma

class: se ocupa para definir clases, seguida del nombre de la clase y dos puntos (:), y luego el cuerpo de la clase. El cuerpo de la clase contiene definiciones de métodos y atributos, que pueden ser públicos o privados según su acceso.

    class Complex:
        def __init__(self, realpart, imagpart):
            self.r = realpart
            self.i = imagpart

    x = Complex(3.0, -4.5)
    x.r, x.i


## Control de flujo
Sentencias condicionales: Nos permiten comprobar condiciones y hacer que nuestros programas se comporten de una forma u otra dependiendo de esta condición.
    if:
        Las ordenes se ejecutan si la condición es verdadera.
    else:
        Las ordenes se ejecutan si la condición es verdadera o falsa
    elif:
        Es una secuencia: 
            if
                else
## bucle o ciclo
Sentencias que nos permiten repetir la ejecución de una o más instrucciones un cierto numero de veces.

    for: 
        Itera sobre un rango de valores.  
    while: 
        Ejecuta una o más operaciones mientras se cumpla una condicion. Itera sobre todos los valores.

    break: 
        Permite salir de un ciclo for.  
    continue: 
        Le indica al loop que debe de continuar iterando.  
    pass:
        Marcador de posición en situaciones en las que una sentencia es sintácticamente necesaria, pero no se requiere ninguna acción. 

python comprehensions: Corresponde a un tipo de sintaxis exclusivo de Python que permite condensar de manera muy concisa algunas problemáticas específicas del cico for
### Comentarios
    # Esto es un comentario en Python   
    """ Esto es un bloque de código
     comentado en Python"""
-----------------------------------------------------------------------------------------------------------------


## Metodos
Acciones que las entidades pueden realizar, desde ellas (argumentos) o hacia ellas (operaciones). Función que pertenece a una clase especifica.

    La forma de llamar un metodo se llama notacion de punto  
	    objeto.metodo(argumentos)

método estático: Es aquel que se puede llamar directamente desde la clase, sin que se tenga que crear una instanciade ella.
   ```python
    @staticmethod 
    #toma como argumento la función definida a continuación del decorador

método constructor: Se ejecuta automáticamente al momento de crear una instancia de la clase, sin necesidad de ser llamado. Constructor de los atributos de una clase para asociar parametros a los atributos

    __init__(self)
    # Asignar valores en el cuerpo del método
    # Asignar valores desde parametros del método
    # Asignar valores desde parametros del método con valores por defecto

    def __init__(self,_nombre, _color, _poder):
        self.nombre = _nombre
        self.color = _color
        self.poder = _poder

self: Para poder acceder a las caracteristicas del objeto
nombre, color, poder: Atributos = caracteristicas
    
    __setattr__
    # Dar valores a los atributos de una instancia
    # Modificar el estado de un objeto

método no estático: Son capaces de modificar el valor de los atributos de una instancia de la clase

    @property
    #Definir una propiedad de la clase, posible definir mutador.

    getters "accsesadores"
        Permiten acceder al valor de un atributo en una instancia

    setters "mutadores"
        Permiten modificar el valor de un atributo en una instancia
    @abstractmethod
    Abstraccion: Es necesario importar la clase ABC del módulo abc como argumento de la clase abstracta y el decorador @abstractmethod para definir al menos 1 método abstracto dentro de ella. Permite disponibilizar solamente la información esencial para definir un objeto

    encapsulamiento: Oculta el estado del objeto, condicionando la forma en que se entrega o modifica
    colaboración: Una clase debe ser instanciada dentro de otra
    composición: Una clase tiene un atributo que es instancia de otra clase, la que posee el atributo se denomina "clase compuesta", mientras la clase a la cual pertenece el atributo de la clase compuesta "clase componente" 
```

### Metodos basicos de string

```python
    count
        "Contar" Cuenta el numero de veces que aparece un caracter
    upper
        "Mayusculas" Transforma el string a mayusculas
    lower 
        "Minusculas" Transforma el string a minusculas
    title 
        "Titulo" Mayusculas solo a la primera letra de cada palabra
    capitalize 
        Poner la primera letra en mayusculas
    length 
        "largo" Contar el numero de caracteres de un string
    join 
        "Unir" Unir muchos elementos separados de un string
    f 
        "formato" Interpolacion al trabajar con un string
    :.xf 
        x indica el numero de decimales
```
### Metodos basicos de lista

```python
    append(x) 
        Agrega elementos al final de la lista
    insert(i,x) 
        Agrega el elemento x en la posicion i especificada
    pop() 
        Elimina elultimo elemento de la lista y lo imprime
    remove() 
        Elimina un elemento especifico
    reverse() 
        Invertir el orden de los elementos
    sort() 
        Ordenar los elementos de forma ascendente
    sorted() 
        Ordenar los elementos de forma ascendente
    	reverse=true Ordena de manera descendente
    index() 
        Retorna indice
```

#### Metodos basicos de diccionarios
Para definir diccionarios {}  
Para acceder a uno []

```python
    pop 
        Eliminar una llave junto a su valor, obteniendo el valor determinado
    del 
        Eliminar una llave junto a su valor
    update 
        Unir 2 diccionarios
    keys 
        Entregara una lista con todos las claves de un diccioanrio
    valves 
        Entregara una lista con todos los valores de un diccioanrio
    items 
        Entregara una lista con los pares clave-valor de un diccionario
    get 
        Permite entregar un mensaje en caso de no encontrar una clave valor predeterminado none
```

### Ver que tipo de librerias posee Python
    pip freeze
### Ver version de pip
    pip --version
### Actualizacion de pip 
    pip install --upgrade pip setuptools wheel
### Para intalar librerias por medio de pip
    pip install"nombre  de libreria"

### Modos de apertura
    open("archivo.txt", "r")
    
    El segundo argumento en open() especifica cómo se va a usar el archivo:

    r
        Lectura únicamente.
    w
        Escritura únicamente, reemplazando el contenido existente o creando el archivo si no existe.
    a
        Escritura únicamente, agregando contenido al final del archivo sin sobrescribir lo existente.
    r+, w+, o a+
        Lectura y escritura simultáneas.

----------------------------------------------------------------------------------------------------------------


## Librerias
Extensiones del lenguaje que añaden funcionalidades

    ramdom.choice()
    "libreria.argumento"

- `pip freeze`: Ver que tipo de librerias posee Pyhton.
- `pip install`: Instalar librerias por medio de pip.

```