## Operadores de asignacion
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

## Operador Booleano (Comparar valores)
    == Igual a
    != Distinto a
    < Menor que
    > Mayor que
    <= Menor o igual que
    >= Mayor o igual que

## Operador Binario
    & and
    | or
    ^ Xor
    ~ Not
    << Desplazamiento izquierda
    >> Desplazamiento derecha 


-----------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------

# Tipos de datos

## Números
	Entero
		int: Precisión fija, convertida en long en caso de overflow
		long: Precisión arbitraria
		bool: Verdadero o falso, valor booleano
	
	Punto flotante
		float: Parte fraccional

	Complejos
		complex: Parte real y parte imaginaria, la cual se nombra con una j

## Secuencias
#### Secuencias Inmutables:
	Strings
		str " ": Cadena de texto
	Tuples
		tuple (): Puede contener objetos de diferentes tipos
	Bytes
		bytes
#### Secuencias Mutables:
	Listas 
		list []: Puede contener objetos de diferentes tipos, separados por coma. Todo elemento de una lista posee un indice interno que parte en subcero [0]
	Byte arrays
		bytearray

## Conjunto
	Sets:
		set {}: mutable, sin duplicados, sin orden
	Frozen set:

## Mappings
	Diccionarios:
		dict {}: Grupo clave:valor, se acceden solo por clave, son delimitados por {}
	“Matriz asociativa”

## Callable "invocable"
	Funciones
	Métodos
	Clases

## Modulos

-----------------------------------------------------------------------------------------------------------------
### Funcion: fragmento de codigo con un nombre asociado que realiza una serie de tareas y devuelve un valor

def: Se ocupa para definir funciones, seguida del nombre de la función y la lista de parametros formales entre parentesis

    def mi_funcion (x,x1):

-----------------------------------------------------------------------------------------------------------------



La forma de llamar un metodo se llama notacion de punto  
	objeto.metodo(argumentos)

## Metodos basicos de string

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

## Metodos basicos de lista

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

## Metodos basicos de diccionarios
Para definir diccionarios {}  
Para acceder a uno []

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

## Ver que tipo de librerias posee Python
    pip freeze
## Ver version de pip
    pip --version
## Actualizacion de pip 
    pip install --upgrade pip setuptools wheel
## Para intalar librerias por medio de pip
    pip install"nombre  de libreria"

## Modos de apertura
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
