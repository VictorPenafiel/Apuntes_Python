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
              (1,): Para crear una tupla de un elemento se debe colocar una coma   
	Bytes
		bytes
##### Secuencias Mutables:
	Listas 
		list []: Puede contener objetos de diferentes tipos, separados por coma y un espacio. Todo elemento de una lista posee un indice interno que parte en subcero [0].
         "slicing" (o rodaje) es una técnica para extraer partes específicas de secuencias como listas, tuplas, cadenas de texto y rangos, por medio de su indice.
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

variable: Espacio de memoria donde colocar datos, por buenas practicas se escribe en minusculas
constante: Espacio de memoria no modificable, por buenas practicas se escribe en mayusculas
parametro: Es un elemento que podrá ser utilizado dentro de la función para realizar sus calculos.  
argumento: Son los valores que tomará el parametro para ser utilizado dentro de la función.

*args: Permiten utilizar tantos parámetros como sean necesarios sin la necesidad que sean definidos a priori  
*kwargs: Permite un numero indeterminado de argumentos, pero estos argumentos deben incluir un nombre, ya que el nombre del argumento pasara a la función 

## Funcion
Abstracción y condensación de código en un objeto (script), con un nombre asociado que realiza una serie de tareas y devuelve un valor. 


def: Se ocupa para definir funciones, seguida del nombre de la función y la lista de parametros formales entre parentesis

    def mi_funcion (x,x1):

- `funcion`: print()
- `objeto.funcion`: "ejemplo".upper()
- `clase.funcion`: LinearRegression().fit(x,y)
- `modulo.funcion`: math.sqrt()


refactorización: Proceso de reorganizacion de código, evitando redundancia y condensando código repetido en funciones. Todo esto con el proceso de tener un código más entendible y claro.

docstring: Documentación interna que tienen las funciones y permiten describir sus parámetros, usos y retornos.

-----------------------------------------------------------------------------------------------------------------
#### Expresiones lambda

Las expresiones lambda nos permiten crear funciones "anónimas", es decir, sin nombre. Básicamente, esto significa que podemos crear funciones ad-hoc rápidamente sin necesidad de definir correctamente una función usando def.

Los objetos de función devueltos al ejecutar expresiones lambda funcionan exactamente igual que los creados y asignados por def.

Existe una diferencia clave que hace que lambda sea útil en roles especializados:

El cuerpo de lambda es una expresión única, no un bloque de declaraciones.

Debido a que se limita a una expresión, una lambda es menos general que una def.

lambda está diseñado para codificar funciones simples y def maneja las tareas más grandes y complejas.

Las funciones def son reutilizables, las lambda no.

    lambda num: num ** 2

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
Clase: Corresponde al conjunto de atributos y metodos que permiten definir un objeto.
Instancia = objeto. 
Instanciar: Crear un objeto a partir de una clase.
Objeto: Corresponde al conjunto de datos "atributo" y metodos definidos por la clase a la cual pertenece, en una instancia especifica de ella. Crear una instancia de una clase.
Atributo: Caracteristicas inherentes de una entidad, que la definen y que en su conjunto pueden representar un estado de la misma.

atributo => python
campo => Django
columna => Bases de datos

class: se ocupa para definir clases, seguida del nombre de la clase y dos puntos (:), y luego el cuerpo de la clase. El cuerpo de la clase contiene definiciones de métodos y atributos, que pueden ser públicos o privados según su acceso.

    class Complex:
        def __init__(self, realpart, imagpart):
            self.r = realpart
            self.i = imagpart

    x = Complex(3.0, -4.5)
    x.r, x.i


## Control de flujo
[Herramienta para Visualizar la ejecución del programa](https://cscircles.cemc.uwaterloo.ca/visualize)

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

### Python comprehensions: Corresponde a un tipo de sintaxis exclusivo de Python que permite condensar de manera muy concisa algunas problemáticas específicas del ciclo for.

    # Crear una lista con los cuadrados de los números del 1 al 5
    cuadrados = [x**2 for x in range(1, 6)]
    print(cuadrados)  # Output: [1, 4, 9, 16, 25]

### Dict comprehensions: Es una forma concisa de crear nuevos diccionarios a partir de iterables existentes. Se utiliza para crear diccionarios de manera más rápida y legible, en comparación con la creación mediante bucles for tradicionales.

    nuevo_diccionario = {clave: valor for elemento in iterable if condicion}


{ k:V for k,v in dictionary.items()}

### Comentarios
    # Esto es un comentario en Python   
    """ Esto es un bloque de código
     comentado en Python"""
    # '''Esto es un string
        que ocupa varias
        lineas. 
    '''
-----------------------------------------------------------------------------------------------------------------

## Metodos
Acciones que las entidades pueden realizar, desde ellas (argumentos) o hacia ellas (operaciones). Función que pertenece a una clase especifica.

    La forma de llamar un metodo se llama notacion de punto  
	    objeto.metodo(argumentos)

    dir() te muestra el "contenido" de un objeto, es decir, qué atributos y métodos tiene disponibles para ser usados.

método estático: Es aquel que se puede llamar directamente desde la clase, sin que se tenga que crear una instanciade ella.
   ```python
@staticmethod 
    #toma como argumento la función definida a continuación del decorador
    '''
    class HerramientasUtiles:
    """
    Una clase simple para agrupar algunas herramientas generales.
    """

    @staticmethod
    def saludar():
        """
        Este es un método estático muy básico.
        Simplemente imprime un saludo.
        No necesita ninguna información de un objeto (instancia) de HerramientasUtiles.
        """
        print("¡Hola desde una herramienta útil!")

    # --- Cómo usarlo ---

    # Puedes llamar al método estático directamente desde la clase.
    # ¡No necesitas crear un objeto!
    HerramientasUtiles.saludar()

    # Esto significa que NO tienes que hacer esto:
    # mi_objeto = HerramientasUtiles()
    # mi_objeto.saludar()
    '''

método constructor: Se ejecuta automáticamente al momento de crear una instancia de la clase, sin necesidad de ser llamado. Constructor de los atributos de una clase para asociar parametros a los atributos

'''
__init__(self)
    # Asignar valores en el cuerpo del método
    # Asignar valores desde parametros del método
    # Asignar valores desde parametros del método con valores por defecto

    def __init__(self,_nombre, _color, _poder):
        self.nombre = _nombre
        self.color = _color
        self.poder = _poder
'''

    self: Para poder acceder a las caracteristicas del objeto nombre, color, poder: Atributos = caracteristicas
    
__setattr__
    # Dar valores a los atributos de una instancia
    # Modificar el estado de un objeto
'''
    class EjemploSetAttr:
    def __init__(self):
        # Inicializamos un atributo para ver la diferencia
        self.atributo_existente = "original"
    
    def __setattr__(self, nombre, valor):
        print(f"Asignando valor '{valor}' al atributo '{nombre}'")
        super().__setattr__(nombre, valor)

    # Crear una instancia
    obj = EjemploSetAttr()

    # Asignar varios atributos
    obj.nuevo_atributo = "primero"
    obj.otro_atributo = 42
    obj.atributo_existente = "modificado"

    # Mostrar los valores asignados
    print("\nVerificando los valores asignados:")
    print("Valor de atributo_existente:", obj.atributo_existente)
    print("Valor de nuevo_atributo:", obj.nuevo_atributo)
    print("Valor de otro_atributo:", obj.otro_atributo)

    # Modificar un atributo existente
    obj.nuevo_atributo = "modificado"
    print("\nDespués de modificar nuevo_atributo:")
    print("Valor de nuevo_atributo:", obj.nuevo_atributo)
'''

método no estático: Son capaces de modificar el valor de los atributos de una instancia de la clase

@property
    #Definir una propiedad de la clase, posible definir mutador.
'''
    getters "accsesadores"
        Permiten acceder al valor de un atributo en una instancia

    setters "mutadores"
        Permiten modificar el valor de un atributo en una instancia


    class Ejemplo:
    def __init__(self):
        self._valor = 0
    
    @property
    def valor(self):
        return self._valor
    
    @valor.setter
    def valor(self, nuevo_valor):
        self._valor = nuevo_valor

    # Crear una instancia
    obj = Ejemplo()

    # Asignar un valor (usando el setter)
    obj.valor = 42
    print(f"Valor asignado: {obj.valor}")

    # Modificar el valor
    obj.valor = 100
    print(f"Valor modificado: {obj.valor}")

    # Mostrar que es un atributo privado
    print(f"\nValor interno (_valor): {obj._valor}")
'''

@abstractmethod
    El decorador @abstractmethod en Python se utiliza para definir métodos abstractos en clases abstractas.

    Abstraccion: Es necesario importar la clase ABC del módulo abc como argumento de la clase abstracta y el decorador @abstractmethod para definir al menos 1 método abstracto dentro de ella. Permite disponibilizar solamente la información esencial para definir un objeto

    encapsulamiento: Oculta el estado del objeto, condicionando la forma en que se entrega o modifica
    colaboración: Una clase debe ser instanciada dentro de otra
    composición: Una clase tiene un atributo que es instancia de otra clase, la que posee el atributo se denomina "clase compuesta", mientras la clase a la cual pertenece el atributo de la clase compuesta "clase componente" 
'''
    from abc import ABC, abstractmethod

    class Animal(ABC):
        @abstractmethod
        def hacer_sonido(self):
            pass

    class Perro(Animal):
        def hacer_sonido(self):
            return "Guau!"

    class Gato(Animal):
        def hacer_sonido(self):
            return "Miau!"

    # Crear instancias y probar
    perro = Perro()
    gato = Gato()

    print(perro.hacer_sonido())  # Guau!
    print(gato.hacer_sonido())   # Miau!

    # Intentar crear una instancia de Animal (fallará)
    try:
        animal = Animal()
    except TypeError as e:
        print("\nError al crear Animal:", e)
```
## Herencia en Python
La herencia permite que una clase hija herede atributos y métodos de una clase padre existente
cursa.app
. En Python, esto se implementa usando paréntesis después del nombre de la clase para especificar la clase padre.

La herencia y el polimorfismo son dos conceptos fundamentales en la programación orientada a objetos (POO) que trabajan juntos para permitir la creación de código más flexible y reutilizable

apuntes.de
. Veamos cómo funcionan en Python:
Herencia en Python

La herencia permite que una clase hija herede atributos y métodos de una clase padre existente

cursa.app
. En Python, esto se implementa usando paréntesis después del nombre de la clase para especificar la clase padre.
Analizando el resultado del primer bloque interactivo:
1. El código funciona perfectamente, mostrando:
   - Acceso a atributos heredados (nombre)
   - Acceso a atributos propios (raza)
   - Comportamiento del método sobrescrito (hacer_sonido)

Sin embargo, falta mostrar el polimorfismo, que es la segunda parte crucial de la pregunta. Necesito:
1. Agregar un ejemplo de polimorfismo que demuestre cómo diferentes objetos responden de manera diferente al mismo método
2. Usar el mismo contexto de animales para mantener la coherencia
3. Mostrar un ejemplo práctico de cómo se utiliza el polimorfismo en una lista de objetos

El primer ejemplo estableció bien la base de la herencia, ahora necesito completar la respuesta con el polimorfismo.
Polimorfismo en Python

El polimorfismo permite que objetos de diferentes clases respondan de manera diferente al mismo método
. En nuestro ejemplo de animales, podemos ver cómo diferentes especies responden de forma única al método hacer_sonido:
---------------------------------------------------------------------------------------------------

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
    find
        Busca una subcadena y devuelve su índice.
    replace
        Reemplaza una subcadena con otra.
    split
        Divide la cadema en una lista de palabras.
```
### Metodos basicos de lista

```python
    append(x) 
        Agrega elementos al final de la lista
    insert(i,x) 
        Agrega el elemento x en la posicion i especificada
    pop() 
        Elimina el ultimo elemento de la lista y lo imprime
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
    values 
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

Este código utiliza la instrucción with, que asegura que el archivo se cierre automáticamente después de que se complete el bloque de código, incluso si ocurren errores.

    with open("mi_archivo.txt", "r") as archivo:
        contenido = archivo.read()
        print(contenido)
----------------------------------------------------------------------------------------------------------------

## Librerias
Extensiones del lenguaje que añaden funcionalidades

    ramdom.choice()
    "libreria.argumento"

- `pip freeze`: Ver que tipo de librerias posee Pyhton.
- `pip install`: Instalar librerias por medio de pip.



Módulo math:
El módulo math en Python ofrece funciones matemáticas avanzadas para cálculos complejos.
Incluye operaciones como raíces cuadradas (sqrt), funciones trigonométricas (sin, cos), logaritmos
(log), constantes como pi (pi) y e (e). Es útil para proyectos que requieren precisión matemática y
cálculos científicos

Módulo statistics:
El módulo statistics en Python proporciona funciones para cálculos estadísticos comunes, como
media (mean), mediana (median), moda (mode) y desviación estándar (stdev). Facilita el análisis de
datos sin necesidad de escribir algoritmos complejos, siendo ideal para proyectos de ciencia de
datos y análisis estadístico.
```