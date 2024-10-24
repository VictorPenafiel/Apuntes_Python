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

Tipos de datos

## Números
	Entero
		int: Precisión fija, convertida en long en caso de overflow
		long: Precisión arbitraria
		bool: Verdadero o falso, valor booleano
	
	Punto flotante
		float: Parte fraccional

	Complejos
		complex: Parte real y parte imaginaria, la cual se nombra con una j
-----------------------------------------------------------------------------------------------------------------
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
-----------------------------------------------------------------------------------------------------------------
## Conjunto
	Sets:
		set {}: mutable, sin duplicados, sin orden
	Frozen set:
		frozenset: inmutable, sin duplicados, sin orden
-----------------------------------------------------------------------------------------------------------------
## Mappings
	Diccionarios:
		dict {}: Grupo clave:valor, se acceden solo por clave, son delimitados por {}
	“Matriz asociativa”
-----------------------------------------------------------------------------------------------------------------
## Callable "invocable"
	Funciones
	Métodos
	Clases
-----------------------------------------------------------------------------------------------------------------
## Modulos

-----------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------
La forma de llamar un metodo se llama notacion de punto
	objeto.metodo(argumentos)

## Metodos basicos de string

    count
        "Contar" Cuenta el numero de veces que aparece un caracter
    upper "Mayusculas" Transforma el string a mayusculas
    lower "Minusculas" Transforma el string a minusculas
    title "Titulo" Mayusculas solo a la primera letra de cada palabra
    capitalize Poner la primera letra en mayusculas
    length "largo" Contar el numero de caracteres de un string
    join "Unir" Unir muchos elementos separados de un string
    f "formato" Interpolacion al trabajar con un string
    :.xf indica el numero de decimales

## Metodos basicos de lista

    append(x) Agrega elementos al final de la lista
    insert(i,x) Agrega el elemento x en la posicion i especificada
    pop() Elimina elultimo elemento de la lista y lo imprime
    remove() Elimina un elemento especifico
    reverse() Invertir el orden de los elementos
    sort() Ordenar los elementos de forma ascendente
    sorted() Ordenar los elementos de forma ascendente
    	reverse=true Ordena de manera descendente
    index() Retorna indice

## Metodos basicos de diccionarios
Para definir diccionarios {}
Para acceder a uno []

    pop Eliminar una llave junto a su valor, obteniendo el valor determinado
    del Eliminar una llave junto a su valor
    update Unir 2 diccionarios
    keys Entregara una lista con todos las claves de un diccioanrio
    valves Entregara una lista con todos los valores de un diccioanrio
    items Entregara una lista con los pares clave-valor de un diccionario
    get Permite entregar un mensaje en caso de no encontrar una clave valor predeterminado none

## Ver que tipo de librerias posee Python
    pip freeze
## Ver version de pip
    pip --version
## Actualizacion de pip 
    pip install --upgrade pip setuptools wheel
## Para intalar librerias por medio de pip
    pip install"nombre  de libreria"
  
    open("archivo.txt", "r")
    
    r – Lectura únicamente.
    w – Escritura únicamente, reemplazando el contenido actual del archivo o bien creándolo si es inexistente.
    a – Escritura únicamente, manteniendo el contenido actual y añadiendo los datos al final del archivo.
    w+, r+ o a+ – Lectura y escritura.