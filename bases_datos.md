
(descargar)[https://www.postgresql.org/download/]


## PostgreSQL 8.3 PSQL Cheat Sheet

- PSQL Cheat Sheet: [PostgreSQL 8.3 PSQL Cheat Sheet](http://www.postgresonline.com/special_feature.php?sf_name=postgresql83_psql_cheatsheet)

### Modificar Variables de Entorno

Agrega las siguientes rutas para que la terminal reconozca los comandos `psql`:

```plaintext
C:\Program Files\PostgreSQL\15\bin
C:\Program Files\PostgreSQL\15\lib
```

### Tipos de Datos Más Comunes

#### Enteros:

- `SMALLINT`: Entero de 2 bytes (rango: -32,768 a 32,767)
- `INTEGER`: Entero de 4 bytes (rango: -2,147,483,648 a 2,147,483,647)
- `BIGINT`: Entero de 8 bytes (rango: -9,223,372,036,854,775,808 a 9,223,372,036,854,775,807)
- `SERIAL`: Tipo especial para columna de identidad autoincremental.

#### Números de Punto Flotante:
- `FLOAT`: Numero decimales de 32 bits de precisión
- `REAL`: Punto flotante de 4 bytes.
- `DOUBLE`: Números decimales de 64 bits de precisión con hasta 15 dígitos decimales.
- `DOUBLE PRECISION`: Punto flotante de 8 bytes.
- `NUMERIC(p, s)`: Decimal con precisión arbitraria (p) y escala (s).

#### Texto y Caracteres:

- `CHAR(n)`: Cadena de caracteres de longitud fija.
- `VARCHAR(n)`: Cadena de caracteres de longitud variable con límite máximo (n).
- `TEXT`: Cadena de caracteres de longitud variable sin límite máximo.

#### Booleanos:

- `BOOLEAN`: Valor booleano (true o false).

#### Fecha y Hora:

- `DATE`: Fecha (formato: "YYYY-MM-DD").
- `TIME`: Hora sin zona horaria (formato: "HH:MI:SS").
- `TIMESTAMP`: Fecha y hora con zona horaria (formato: "YYYY-MM-DD HH:MI:SS").
- `INTERVAL`: Intervalo de tiempo.

#### Otros Tipos de Datos:

- `UUID`: Identificador único universal.
- `JSON` / `JSONB`: Almacena objetos JSON.
- `ARRAY`: Matriz de valores de un tipo de datos específico.


-----------------------------------------------------------------------------------------------------------------------

## Normalización y Formas Normales

### Primera Forma Normal (1FN)

La 1FN establece que cada columna de una tabla debe contener un solo valor y no debe haber duplicación de datos.

    producto_id, nombre, categoria_id, nombre, precio

    tabla categorias
    PK categoria_id, nombre

    tabla productos
    PK producto_id, nombre, precio, FK categoria_id
    
### Segunda Forma Normal (2FN)

La 2FN establece que una tabla debe cumplir con la 1FN y que cada columna no clave (ni pk, ni fk) debe depender completamente de la clave primaria.
    tabla categorias
    PK categoria_id, nombre

    tabla productos
    PK producto_id, nombre, FK precio_id FK categoria_id

    tabla precios
    PK precio_id, precio, FK producto_id

### Tercera Forma Normal (3FN)

La 3FN establece que una tabla debe cumplir con la 2FN y que no debe haber dependencias transitivas.
    tabla categorias
    PK categoria_id, nombre

    tabla productos
    PK producto_id, nombre, FK precio_id, FK categoria_id

    tabla precios
    PK precio_id, precio, FK producto_id

### Desformalizacación

    tabla categorias
    PK categoria_id, nombre

    tabla productos
    PK producto_id, nombre, precio, FK categoria_id

-----------------------------------------------------------------------------------------------------------

## Transacciones en PostgreSQL

Las transacciones en PostgreSQL garantizan la integridad y consistencia de la base de datos mediante propiedades ACID:

    Atomicidad
        Una transacción se considera atómica, lo que significa que todas las operaciones dentro de una transacción se realizan como una unidad indivisible. Si alguna operación dentro de la transacción falla, todas las operaciones se deshacen (rollback), y si todas las operaciones tienen éxito, se confirman (commit).
    Consistencia
        Las transacciones en PostgreSQL deben mantener la consistencia de la base de datos. Esto significa que las transacciones deben llevar la base de datos desde un estado válido a otro estado válido, sin violar las restricciones de integridad definidas en la base de datos.
    Aislamiento
        La propiedad de aislamiento garantiza que cada transacción se ejecute de manera aislada de otras transacciones concurrentes. Esto evita que las transacciones interfieran entre sí y garantiza la coherencia de los datos.
    Durabilidad
        Una vez que una transacción ha sido confirmada (commit), sus cambios se vuelven permanentes y se mantendrán incluso en caso de fallos del sistema o reinicios posteriores.

-----------------------------------------------------------------------------------------------------------------------
Structured Query Language: Es el lenguaje estándar para la administración de bases de datos relacionales.  
SQL = DDL + DCL +DML + DQL+ TCL

## DDL (Data Definition Language)
- `CREATE`: Se usa para crear una base de datos, tabla, vistas, etc.
- `ALTER`:  Se utiliza para modificar la estructura, por ejemplo añadir o borrar columnas de una tabla.
- `DROP`:  Para eliminar objetos del esquema..
- `TRUNCATE`: Para eliminar todos los registros de una tabla.
- `COMMENT`: Para agregar comentarios al diccionario de datos.
- `RENAME`: Para renombrar objetos existentes.

## DCL (Data Control Language)
El DCL se utiliza en PostgreSQL para controlar los permisos y privilegios en la base de datos:

- `GRANT`: Concede privilegios a los usuarios o roles sobre objetos de la base de datos.
- `REVOKE`: Revoca los privilegios previamente otorgados a los usuarios o roles sobre objetos de la base de datos.
- `DENY`: Deniega un permiso a una entidad de seguridad. Evita que la entidad de seguridad herede permisos por su pertenencia a grupos o roles.

## DML (Data Manipulation Language)

- `INSERT`: Con esta instrucción podemos insertar los valores en una base de datos
- `UPDATE`: Sirve para modificar los valores de uno o varios registros.
- `DELETE`: Se utiliza para eliminar las filas de una tabla.

## DQL (Data Query Language)

- `SELECT`:  Para recuperar datos de la base de datos.

## TCL (Transaction Control Language)

El TCL se utiliza en PostgreSQL para controlar las transacciones y los cambios en la base de datos:

- `BEGIN`: Inicia una transacción explícitamente.
- `COMMIT`: Confirma una transacción, guardando los cambios realizados.
- `ROLLBACK`: Deshace una transacción, revirtiendo los cambios realizados.
- `SAVEPOINT`: Establece un punto de guardado dentro de una transacción.
- `RELEASE SAVEPOINT`: Elimina un punto de guardado previamente establecido.
- `ROLLBACK TO SAVEPOINT`: Deshace los cambios realizados después de un punto de guardado específico.


-----------------------------------------------------------------------------------------------------------------------
## Comandos PostgreSQL

- `\c database_name`: Conectarse a una base de datos específica.
- `\l`: Listar todas las bases de datos existentes.
- `\?`: Mostrar ayuda.
- `\du`: Listar todos los usuarios en el motor.
- `\dt`: Listar todas las relaciones (o tablas) existentes en una base de datos específica.
- `\q`: Salir de la consola de PostgreSQL.
- `\!`: Obtener información del sistema y salir sin cerrar la shell de psql.
- `\h`: Mostrar la lista de comandos disponibles.
- `\conninfo`: Mostrar detalles del usuario conectado.

### Usuarios

- Crear un usuario: `CREATE USER nombre_usuario WITH PASSWORD 'passworrd_asignado';`
- Eliminar usuarios: `DROP USER nombre_usuario;`
- Ver los usuarios existentes en la base de datos: `\du`
- Cambiar contraseña de usuario: `\password "nombre de usuario"`
- Usuarios que tienen acceso a la base de datos: `SELECT nombre_usuario FROM pg_user;`
- Limitar a un usuario: `CREATE USER nombre_usuario WITH comando_opcional;`

### Comandos Más Usados

- `PASSWORD`: Asigna una contraseña al usuario creado.
- `ENCRYPTED PASSWORD`: Asigna una contraseña encriptada al usuario creado.
- `UNENCRYPTED PASSWORD`: Asigna una contraseña no encriptada al usuario creado.
- `VALID UNTIL`: La cuenta expirará en la fecha indicada.
- `CREATEDB`: Permite al usuario crear bases de datos.
- `NOCREATEDB`: No permite al usuario crear bases de datos.
- `SUPERUSER`: Puede crear otros usuarios (veremos esto más adelante).
- `NOSUPERUSER`: No puede crear otros usuarios.

### Permisos para los Usuarios

Una vez creados los usuarios, se pueden cambiar los permisos con los siguientes comandos:

- Para dar acceso a todos los privilegios de una base de datos: `GRANT ALL PRIVILEGES ON DATABASE database_name TO nombre_usuario;`
- Quitar privilegios de una base de datos: `REVOKE ALL PRIVILEGES ON DATABASE database_name FROM nombre_usuario;`
- Para dar permiso de creación de una base de datos se usa: `ALTER USER nombre_usuario CREATEDB;`
- Para transformar al usuario en superusuario: `ALTER USER myuser WITH SUPERUSER;`
- Remover el superusuario: `ALTER USER username WITH NOSUPERUSER;`

---------------------------------------------------------------------------------------------------------------------------


### Conexiones

- Conectarse desde cualquier consola a una base de datos: `psql -U username -W -d database_name`

### Administración de la Base de Datos

- Iniciar la base de datos cambiando de usuario: `sudo su -l postgres`
- Entrar a la base de datos mediante la terminal: `psql`
- Crear base de datos: `CREATE DATABASE nombre;`
- Crear título de base de datos: `\C POST`
- Crear tablas: `CREATE TABLE POST ();`
- Ver tabla creada: `SELECT * FROM post;`
- Modificar tabla, agregando una columna: `ALTER TABLE "nombre base de datos" ADD "nombre nuevo atributo" "Tipo de datos";`
- Agregar datos a columna creada: `UPDATE "nombre base de datos" SET "nombre columna creada" = 'dato' WHERE "especificar identificador como id=1";`
- Eliminar usuario: `DELETE FROM "nombre base" WHERE "especificar identificador como id=1";`
- Eliminar base de datos: `DROP DATABASE "nombre";`
- Vincular 2 tablas de una base de datos: `CREATE TABLE "nombre tabla" (id_comentario SERIAL, id_post INT, fecha_creacion TIMESTAMP, contenido VARCHAR(255), FOREIGN KEY(id_post) REFERENCES post(id));`


## Manipulación de Datos y Administración en PostgreSQL

### Creación de Tablas

```sql
-- Creación de una tabla
CREATE TABLE nombre_tabla (columnas);

-- Ver la estructura de la tabla
SELECT * FROM nombre_tabla;
```

### Inserción de Datos en una Tabla

```sql
-- Inserción de datos
INSERT INTO nombre_tabla (columna1, columna2, columna3) VALUES (valor1, valor2, valor3);
```

### Actualización de Registros

```sql
-- Actualización de registros
UPDATE nombre_tabla SET columna1 = valor_nuevo WHERE condicion;
```

### Eliminación de Registros

```sql
-- Eliminar toda la tabla
DELETE FROM tabla;

-- Seleccionar qué registros queremos borrar
DELETE FROM tabla WHERE condicion;
```

### Restricciones

- `NOT NULL`: La columna no puede tener valores NULL.
- `UNIQUE`: Todos los valores de la columna deben ser diferentes entre sí.
- `SERIAL`: Restringe el valor numérico para que sea autoincremental.
- `PRIMARY KEY`: Define la clave primaria.
- `FOREIGN KEY`: Enlaza dos tablas, normalmente referente a una clave primaria.
- `CHECK`: Todos los valores de una columna deben satisfacer una condición específica.
- `DEFAULT`: Asigna un valor por defecto a los registros sin valor asignado.
- `INDEX`: Crea y recupera datos de forma rápida.

### Transacciones

```sql
-- Inicio de una transacción
BEGIN;

-- Guardar los cambios de la transacción
COMMIT;

-- Revertir los cambios realizados
ROLLBACK;

-- Guardar el punto de partida para aplicar rollback
SAVEPOINT;

-- Asignar nombre a la transacción
SET TRANSACTION;

-- Desactivar AUTOCOMMIT
\set AUTOCOMMIT off;

-- Comprobar si AUTOCOMMIT está activado
\echo :AUTOCOMMIT;
```
-----------------------------------------------------------------------------------------------------------------------

### Exportación y Restauración

```bash
# Exportar una base de datos
pg_dump -U nombre_usuario nombre_db > db.sql

# Exportar todas las bases de datos
sudo su - postgres
pg_dumpall > /directorio/dumpall.sql

# Restaurar una base de datos
sudo su - postgres
psql -U postgres nombredb < archivo_restauracion.sql

# Restaurar todas las bases de datos
sudo su - postgres
psql -f /var/lib/pgsql/backups/dumpall.sql mydb
```


## Conexión de PostgreSQL con Django

Para conectar PostgreSQL con Django, puedes cambiar el motor de la base de datos en el archivo `settings.py` de tu proyecto. Aquí tienes un ejemplo de cómo configurarlo:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'adl-test',
        'USER': 'postgres',
        'PASSWORD': '12345',
        'HOST': '127.0.0.1',
        'PORT': '5432',
    }
}
```

Después de configurar el motor de base de datos, instala el conector PostgreSQL utilizando el siguiente comando en tu terminal con el entorno virtual activo:

```bash
pip install psycopg2
```

## Operaciones JOIN en PostgreSQL

- `INNER JOIN`: Combina filas de dos o más tablas en función de una condición de coincidencia.
- `LEFT JOIN`: Combina filas de la tabla izquierda con las filas coincidentes de la tabla derecha.
- `RIGHT JOIN`: Combina filas de la tabla derecha con las filas coincidentes de la tabla izquierda.
- `FULL JOIN`: Combina todas las filas de ambas tablas, incluyendo las filas sin coincidencias.

#### Es importante tener en cuenta que los operadores OUTER JOIN (LEFT OUTER JOIN, RIGHT OUTER JOIN y FULL OUTER JOIN) son compatibles en PostgreSQL y se pueden utilizar para realizar consultas que involucren combinaciones externas izquierdas, derechas o completas. 
####   El operador OUTER es opcional y se puede omitir en las cláusulas JOIN. Por ejemplo, LEFT JOIN y LEFT OUTER JOIN son equivalentes en PostgreSQL.

