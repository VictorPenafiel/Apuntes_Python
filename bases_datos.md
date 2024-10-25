
POSTGRESQL 8.3 PSQL CHEAT SHEET
  http://www.postgresonline.com/special_feature.php?sf_name=postgresql83_psql_cheatsheet

* Modificar variables de entornos

* Agregar siguientes rutas para que reconozca la terminal los comandos psql
C:\Program Files\PostgreSQL\15\bin
C:\Program Files\PostgreSQL\15\lib

Comandos más usados:
● PASSWORD: Asigna una contraseña al usuario creado.
● ENCRYPTED PASSWORD: Le asigna una contraseña encriptada al usuario creado.
● UNENCRYPTED PASSWORD: Le asigna una contraseña no encriptada al usuario creado.
● VALID UNTIL: La cuenta expirará en la fecha indicada.
● CREATEDB: Permite al usuario crear bases de datos.
● NOCREATEDB: No permite al usuario crear bases de datos.
● SUPERUSER: Puede crear otros usuarios (volveremos a ver esto más adelante).
● NOSUPERUSER: No puede crear otros usuarios.

Permisos para los usuarios
Una vez creados los usuarios, se pueden cambiar los permisos con los siguientes comandos:
● Para dar acceso a todos los privilegios de una base de datos:
GRANT ALL PRIVILEGES ON DATABASE database_name TO nombre_usuario;
● Quitar privilegios de una base de datos:  
REVOKE ALL PRIVILEGES ON DATABASE database_name FROM nombre_usuario;
● Para dar permiso de creación de una base de datos se usa:
ALTER USER nombre_usuario CREATEDB;
● Para el caso de querer transformar al usuario en superuser:
ALTER USER myuser WITH SUPERUSER;
● Remover el superusuario:
ALTER USER username WITH NOSUPERUSER;


* Tipos de datos más comunes son:

Enteros:
SMALLINT: entero de 2 bytes (rango: -32,768 a 32,767)
INTEGER: entero de 4 bytes (rango: -2,147,483,648 a 2,147,483,647)
BIGINT: entero de 8 bytes (rango: -9,223,372,036,854,775,808 a 9,223,372,036,854,775,807)
SERIAL: tipo especial que se utiliza para crear una columna de identidad autoincremental.

Números de punto flotante:
FLOAT: Numero decimales de 32 bits de precisión
REAL: número de punto flotante de 4 bytes
DOUBLE PRECISION: número de punto flotante de 8 bytes
NUMERIC(p, s): número decimal con precisión arbitraria (p) y escala (s)

Texto y caracteres:
CHAR(n): cadena de caracteres de longitud fija
VARCHAR(n): cadena de caracteres de longitud variable con límite máximo (n)
TEXT: cadena de caracteres de longitud variable sin límite máximo
Booleanos:

BOOLEAN: valor booleano (true o false)

Fecha y hora:
DATE: fecha (formato: "YYYY-MM-DD")
TIME: hora sin zona horaria (formato: "HH:MI:SS")
TIMESTAMP: fecha y hora con zona horaria (formato: "YYYY-MM-DD HH:MI:SS")
INTERVAL: intervalo de tiempo
Otros tipos de datos:

UUID: identificador único universal
JSON / JSONB: tipo de datos para almacenar objetos JSON
ARRAY: matriz de valores de un tipo de datos específico

----------------------------------------------------------------------------------------------------------------------------
* Comandos PostgreSQL
\c 
  nombre_base Conectarse a una base de datos específica
\l 
  Listar todas las bases de datos existentes
\? 
  Ayuda
\du 
  Listar todos los usuarios en el motor
\dt 
  Listar todas las relaciones (o tablas) existentes en una base de datos específica
\q 
  Salir de la consola de PostgreSQL
\! 
  Obtener informacion del sistema y salir sin cerrar psql shell
\h 
  Mostrar la lista de comandos
\conninfo 
  Mostrar detalles del usuario conectado
--------------------------------------------------------------------------------------------------------------
*Usuarios
Crear un usuario:
  CREATE USER nombre_usuario WITH PASSWORD passworrd_asignado;
Eliminar usuarios
  DROP USER nombre_usuario;
Ver los usuarios existentes en la base de datos, se usa el comando
  \du
Cambiar contraseña de usuario
  \password "nombre de usuario"
Usuarios que tienen acceso a la base de datos
  SELECT nombre_usuario FROM pg_user;
Limitar a un usuario, se debe hacer lo siguiente:
  CREATE USER nombre_usuario WITH comando_opcional;
  

 --------------------------------------------------------------------------------------------------------------
 *Conexiones
Conectarse desde cualquier consola a una base de datos
  psql -U username -W -d database_name 

*Administración de la Base de datos
Para iniciar a la base de datos hay que cambiar de usuario y ejecutar el siguiente comando:
  sudo su -l postgres
Entrar mediante la terminal a la base de datos
  psql
Crear base de datos
  CREATE DATABASE nombre;
Crear titulo de base de datos
  \C POST
Crear tablas
  CREATE TABLE POST ()
Ver tabla creada
  select * from post;
Modificar tabla, agregando una columna
  ALTER TABLE "nombre base de datos" ADD "nombre nuevo atriburo" "Tipo de datos"
Agregar datos a columna creada
  UPDATE "nombre base de datos" SET "nombre columna creada" = 'dato' WHERE "especificar identificador como id=1" ;
Eliminar usuario
  DELETE FROM "nombre base" WHERE "especificar identificador como id=1";
Elimar base de datos
  DROP DATABASE "nombre";
Vincular 2 tablas de una base de datos
  CREATE TABLE "nombre tabla"(id_comentario SERIAL, id_post INT, fecha_creacion TIMESTAMP, contenido VARCHAR(255), FOREIGN KEY(id_post) REFERENCES post(id));

*Manipulación de Datos y Administración en PostgreSQL
Creación de tablas
  CREATE TABLE nombre_tabla (columnas);
Ver la estructura que tiene nuestra tabla, podemos usar el comando:
  SELECT * FROM nombre_tabla;
Inserción de datos en una tabla
  INSERT INTO nombre_tabla (columna1, columna2, columna3) VALUES (valor1,valor2, valor3);
Actualización de registros
  UPDATE nombre_tabla SET columna1=valor_nuevo WHERE condicion;
Eliminación de registro
  Eliminar toda la tabla
    DELETE FROM tabla;
  Seleccionar qué registros queremos borrar
    DELETE FROM tabla WHERE condicion;
    
*Restricciones
● NOT NULL: La columna no puede tener valores NULL.
● UNIQUE: Todos los valores de la columna deben ser diferentes unos a otros.
● SERIAL: Restringe a que el valor numérico sea autoincremental.
● PRIMARY KEY: Aplica la clave primaria.
● FOREIGN KEY: Sirve para enlazar 2 tablas, normalmente referente a una clave
primaria.
● CHECK: Todos los valores de una columna deben satisfacer una condición en
específico.
● DEFAULT: Le da un valor por defecto a aquellos registros que no tengan un valor
asignado.
● INDEX: Sirve para crear y recuperar datos de forma rápida.

*Transacciones
El sistema permite que se ejecuten todas las sentencias SQL que necesitemos
  BEGIN ó START 
Guarda los cambios de la transacción
  COMMIT 
Retrocede los cambios realizados
  ROLLBACK 
Guarda el punto de partida al cual volver a la hora de aplicar ROLLBACK
  SAVEPOINT 
Le asigna nombre a la transacción
  SET TRANSACTION 
Para desactivar AUTOCOMMIT
  \set AUTOCOMMIT off
Para comprobar que está activado AUTOCOMMIT
  \echo :AUTOCOMMIT

*Exportación y Restauración
Dump para exportar una base de datos
  pg_dump -U nombre_usuario nombre_db > db.sql
Dump para exportar todas las bases de datos
  sudo su - postgres
  pg_dumpall > /directorio/dumpall.sql
Restaurar una base de datos
  sudo su - postgres
  psql -U postgres nombredb < archivo_restauracion.sql
Restaurar todas las bases de datos
  sudo su - postgres
  psql -f /var/lib/pgsql/backups/dumpall.sql mydb
 
---------------------------------------------------------------------------------------------------------------------------
  
  Conector de postgres con Django
  cambiar motor de base de datos a conectar en el settings.py
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'adl-test',
        'USER' : 'postgres',
        'PASSWORD': '12345',
        'HOST' :'127.0.0.1',
        'PORT': '5432',
    }
}

En el terminal con el ambiente activo instalar conectores de postgres:
    pip install psycopg2
    
---------------------------------------------------------------------------------------------------------------------------
*Normalización y formas normales
Primera Forma Normal (1FN):
La 1FN establece que cada columna de una tabla debe contener un solo valor 
y no debe haber duplicación de datos.

producto_id, nombre, categoria_id, nombre, precio

tabla categorias
PK categoria_id, nombre

tabla productos
PK producto_id, nombre, precio, FK categoria_id


Segunda Forma Normal (2FN):
La 2FN establece que una tabla debe cumplir con la 1FN y que cada columna
no clave(ni pk, ni fk) debe depender completamente de la clave primaria.

tabla categorias
PK categoria_id, nombre

tabla productos
PK producto_id, nombre, FK precio_id FK categoria_id

tabla precios
PK precio_id, precio, FK producto_id


Tercera Forma Normal (3FN):
La 3FN establece que una tabla debe cumplir con la 2FN 
y que no debe haber dependencias transitivas.

tabla categorias
PK categoria_id, nombre

tabla productos
PK producto_id, nombre, FK precio_id, FK categoria_id

tabla precios
PK precio_id, precio, FK producto_id

Desformalizacación

tabla categorias
PK categoria_id, nombre

tabla productos
PK producto_id, nombre, precio, FK categoria_id

-----------------------------------------------------------------------------------------------------------
Transacciones con PostgreSQL:

PostgreSQL admite transacciones para garantizar la integridad de los datos y mantener la consistencia de la base de datos.

Propiedades ACID:

Atomicidad: Una transacción se considera atómica, lo que significa que todas las operaciones dentro de una transacción se realizan como una unidad indivisible. Si alguna operación dentro de la transacción falla, todas las operaciones se deshacen (rollback), y si todas las operaciones tienen éxito, se confirman (commit).

Consistencia: Las transacciones en PostgreSQL deben mantener la consistencia de la base de datos. Esto significa que las transacciones deben llevar la base de datos desde un estado válido a otro estado válido, sin violar las restricciones de integridad definidas en la base de datos.

Aislamiento: La propiedad de aislamiento garantiza que cada transacción se ejecute de manera aislada de otras transacciones concurrentes. Esto evita que las transacciones interfieran entre sí y garantiza la coherencia de los datos.

Durabilidad: Una vez que una transacción ha sido confirmada (commit), sus cambios se vuelven permanentes y se mantendrán incluso en caso de fallos del sistema o reinicios posteriores.

DCL (Data Control Language):
El DCL se utiliza en PostgreSQL para controlar los permisos y privilegios en la base de datos. 

GRANT: Concede privilegios a los usuarios o roles sobre objetos de base de datos.
REVOKE: Revoca los privilegios previamente otorgados a los usuarios o roles sobre objetos de base de datos.

TCL (Transaction Control Language):
El TCL se utiliza en PostgreSQL para controlar las transacciones y los cambios en la base de datos

BEGIN: Inicia una transacción explícitamente.
COMMIT: Confirma una transacción, guardando los cambios realizados.
ROLLBACK: Deshace una transacción, revirtiendo los cambios realizados.
SAVEPOINT: Establece un punto de guardado dentro de una transacción, lo que permite deshacer solo parte de los cambios realizados.
RELEASE SAVEPOINT: Elimina un punto de guardado previamente establecido.
ROLLBACK TO SAVEPOINT: Deshace los cambios realizados después de un punto de guardado específico, sin deshacer los cambios anteriores a ese punto.

-------------------------------------------------------------------------------------------
*Operaciones Join en PostgreSQL
INNER JOIN: El INNER JOIN se utiliza para combinar las filas 
de dos o más tablas en función de una condición de coincidencia. 
Devuelve solo las filas que tienen una coincidencia en ambas tablas.

SELECT *
FROM tabla1
INNER JOIN tabla2 ON tabla1.columna = tabla2.columna;


LEFT JOIN (o LEFT OUTER JOIN): El LEFT JOIN se utiliza para combinar todas las filas 
de la tabla izquierda con las filas coincidentes de la tabla derecha. 
Si no hay una coincidencia en la tabla derecha, se devolverá NULL para los campos de la tabla derecha.

SELECT *
FROM tabla1
LEFT JOIN tabla2 ON tabla1.columna = tabla2.columna;



RIGHT JOIN (o RIGHT OUTER JOIN): El RIGHT JOIN se utiliza para combinar todas las filas 
de la tabla derecha con las filas coincidentes de la tabla izquierda.
Si no hay una coincidencia en la tabla izquierda, se devolverá NULL para los campos de la tabla izquierda.

SELECT *
FROM tabla1
RIGHT JOIN tabla2 ON tabla1.columna = tabla2.columna;


FULL JOIN (o FULL OUTER JOIN): El FULL JOIN se utiliza para combinar todas las filas de ambas tablas, 
incluyendo las filas que no tienen coincidencias en la otra tabla. 
Si no hay una coincidencia, se devolverá NULL para los campos correspondientes de la tabla opuesta.

SELECT *
FROM tabla1
FULL JOIN tabla2 ON tabla1.columna = tabla2.columna;

--------------------------------------------------------------------------------------------------------
Es importante tener en cuenta que los operadores OUTER JOIN (LEFT OUTER JOIN, RIGHT OUTER JOIN y FULL OUTER JOIN) 
son compatibles en PostgreSQL y se pueden utilizar para realizar consultas que involucren combinaciones externas izquierdas, derechas o completas. 
El operador OUTER es opcional y se puede omitir en las cláusulas JOIN. Por ejemplo, LEFT JOIN y LEFT OUTER JOIN son equivalentes en PostgreSQL.


--Obtener los clientes que no tienen órdenes asociadas
--Obtener los clientes que tienen órdenes asociadas
--Obtener los artículos que no han sido incluidos en ninguna orden
--Obtener las órdenes realizadas por clientes que pertenecen a una ciudad específica
--Obtener todas las órdenes junto con la información del cliente y el artículo correspondiente
--Obtener los clientes que han realizado órdenes de un artículo específico
--Obtener el total gastado por cada cliente en todas las órdenes
--Obtener los clientes que no han realizado ninguna orden
--Obtener los artículos con su precio y el número de órdenes en las que se han vendido
