## Comandos de terminal (Unix/Linux)

1) pwd | mostrar directorio donde estamos
2) cd/nombre directorio | cambiar directorio
3) cd .. | ir al directorio anterior
4) ls -la | listar carpetas, permisos y archivos ocultos
ls - lah  | Tamaño de los archivos
ls -rlh   | ver directorios con permisos y tamaños
ls -Rh  | ver directorios y subdirectorios
ls -Rlh   | ver directorios con permisos y tamaños y sus subdirectorios
ls - l     | Ver permisos y rutas
	d = directory
	r = read
	w = write
	x = executable
d[usuario{r|w|x}]
[grupo{r|w|x}]
[otro{r|w|x}]
./: directorio actual
../: directorio padre
./: directorio actual
./archivoOculto o directorio 

5) ls | listar carpetas y archivos
6) mkdir nombreCarpeta | crear una carpeta o directorio
7) touch index.html | crea un archivo, agregar extensión
8) cp nombreArchivo carpeta/nombreArchivoCopia
9) rm index.html | elimina un archivo
10) mv index.html carpetaDestino/ | mover un archivo
11) rm -rf nombreDirectorio | elimina carpeta y archivos
12) mv nombreArchivoActual nombreArchivoNuevo
13) history   |  historial
    !+numero del historial | Se ejecuta dicho comando
14) clear    |  limpiar registros de la terminal
15) cat		|  Se utiliza para visualizar, unir y crear archivos. «cat ejemplo. txt» muestra el contenido de «ejemplo»
-----------------------------------------------------------------------------------------------------------------------

## ¿Cómo agregar una carpeta/proyecto existente a un nuevo repositorio GIT (en GitHub) ?

1) Abrir Git bash
2) Cambiarse al directorio del proyecto existente a subir.
3) Inicializar repositorio local. Ejecute:  
	git init
4) Agregar el contenido y cambios realizados Ejecute:  
	git add .
5) Pasar el contenido del proyecto al head.  Ejecute:  
	git commit -m "Commit inicial"
6) Ir al sitio github.com.  Crear repositorio vacío con el nombre del proyecto.
7) Una vez creado el repositorio vacío, copiar la dirección del mismo seleccionado la opción SSH.
	git@github.com:cegb/prueba04.git
8) Regresar al Git bash. Vamos a hacer la conexión del repo local con el remoto (github).(Ésto se hace una sola vez).
	git remote add origin git@github.com:cegb/prueba04.git
9) Realizar push. Ejecute: 
	git push origin master

PD:
Si le aparece error de NO registro local de nombre de usuario y/o Email:
	Ejecute:  
	git config --global user.name "Pedro Pérez"
	git config --global user.email "pedro.perez@gmail.com"

Permite visualizar todas las versiones de un proyecto
	git log
Muestra todas las diferencias desde el ultimo commit guardado
	git diff
	
Agregar cambio a rama principal
git add .
git commit -m "Comentario"
git push origin master
	
-----------------------------------------------------------------------------------------------------------------------
1) Crear repositorio remoto en Github vacío (sin readme, ni .gitignore)
2) Creamos un archivo env_log.txt
3) Creamos un entorno virtual e instalamos las dependencias
4) Pegamos los comandos de creación del entorno virtual e instalación de dependencias y sus resultados en env_log.txt
5) Creamos un proyecto django
6) Creamos un archivo tree.txt
7) Utilizamos el comando tree /f /a "ruta proyecto" > tree.txt para registrar en el archivo tree.txt la estructura del proyecto en su estado inicial
8) Visitamos gitignore.io - Create Useful .gitignore Files For Your Project (toptal.com) y buscamos por django para generar un .gitignore
9) Creamos un readme.md en la carpeta de proyecto django
10) Seguimos algunas de las instrucciones de la opción A de github para proceder, sobre el directorio de nuestro proyecto en el siguiente orden: 2, 5, 3, 4, 6 y 7

-----------------------------------------------------------------------------------------------------------------------

## Clonar
git clone + llave HTTPS
git pull Manter actualizaciones del reposotorio, para actualizar en caso de cambio de repositorio


¿Cómo hacer un clone de una carpeta/proyecto remoto existente(en GitHub) en una carpeta local en mi disco ?

1) Ingresar al repositorio remoto Github a clonar. (Puede ser propio o de un tercero)	
Copiar la dirección HTTPS o SSH de dicho repo.
2) Abrir Git Bash. Ubicarse en la carpeta local donde queremos recibir la carpeta del nuevo proyecto.
3) Ejecute: git clone git@github.com:cegb/prueba04.git
	Aquí se descarga el contenido del repo remoto.
4) Comience a hacer los cambios que corresponda.

Recordar (posteriormente):
Al agregar nuevos archivos/carpetas luego debemos hacer:
1) Abrir Git bash
2) Cambiarse al directorio del proyecto existente clonado.
3) Agregar el contenido al stage. Ejecute:  git add .
4) Pasar el contenido del proyecto al head.  Ejecute:  git commit -m "Descripción de los cambios ... etc"
5) Realizar push. Ejecute: git push origin master


-----------------------------------------------------------------------------------------------------------------

## ¿Cómo crear llave SSH local y conectar al servicio Github?

Requisitos: 
* Tener preinstalado el GIT (https://git-scm.com/downloads)
* Tener cuenta activa en Github

Procedimiento:
EN GIT BASH:
1) Abrir Git Bash.
2) Ejecutar: ls -al ~/.ssh
	Es para saber si ya hay alguna llave creada previamente. (si es así, salte al paso 5)
	Las llaves usualmente se identifican como: id_rsa o nombres similares.
	Si no existe la carpeta, se observará un error como: ~/.ssh doesn't exist
	
3) Generar la nueva llave. Ejecutar: ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
	Coloque el mismo email que utilizó para registrarse en Github
	Se le solicitará un passphrase. Dejar en blanco.

4) Verifique que se han creado las llaves. Ejecute: ls -al ~/.ssh
	Ahora deben aparecer los archivos:  id_rsa  y  id_rsa.pub
	
5) Active el SSH-Agent.  Ejecute:  eval "$(ssh-agent -s)"

6) Agregue la llave privada al agente. Ejecute: ssh-add ~/.ssh/id_rsa

7) Copiar el contenido de la llave PÚBLICA en el portapapeles. Para ello, ejecute:  cat ~/.ssh/id_rsa.pub
	Podrá observar en el terminal el contenido de la llave. 
	Debe seleccionar cuidadosamente (con el cursor) el texto que se observa --> clic Botón derecho --> Copiar

EN EL SITIO DE GITHUB:
8) Ingresar con su usuario GitHub al sitio.
9) Hacer clic en su avatar (esquina superior derecha) y seleccionar "Settings" (o configuración).
10) En el menú lateral izquierdo, seleccionar "SSH and GPG keys".
11) Pulsar el botón verde "New SSH Key".
12) Coloque un título descriptivo. Ej: Notebook de Pedro.
13) En el campo "Key" --> Pegar la llave PÚBLICA que se copió en el paso 7.  --> Presione "Add SSH Key".

14) Una vez realizado estos pasos, ya estará disponible la comunicación automática entre tu equipo y GitHub.
	De aquí en adelante puedes clonar repositorios o crear nuevos, sin necesidad de estar colocando repetidamente
	tus datos de usuario/clave.
	
15) Como paso opcional, puede probar la comunicación con Github. Ejecute: ssh -T git@github.com

-----------------------------------------------------------------------------------------------------------------


## Comandos Git

&& Se ocupa para concatenar comandos git 
1) git status | ver status del repositorio
2) git config --global user.name "nombreUsuario" Configuramos el parametro de autor
3) git config --global user.email "tucorreo@gmail.com"
4) git config --list | listar configuración git
5) git init | inicializar repositorio
6) git add index.html | añadimos un archivo
7) git add . | añadimos todos los archivos
8) git rm --cached index.html | retiramos el archivo
9) git commit -m "comentario" | agregar comentario
10) git log permite revisar todas las versiones de un proyecto
    git log --oneline | estructura de comentarios y ramas
11) git branch -m main | cambiar nombre
12) git branch -m nombreRama nombreNuevo | 
13) git checkout numeroComentario | llevarnos al comentario
14) git checkout nombreRama | llevarnos hacia la rama
15) git reset = Descompone el archivo, pero conserva el contenido del mismo
        git reset --soft HEAD~ | regresar el último comentario
16) git remote add origin https://github.com/{usuario}/{repo}.git
17) git remote set-url origin git@github.com:adrianedutecno/iguanapage.git
18) git remote rename nombreActual nombreNuevo | renombrar repositorio
19) git remote -v | visualizar repositorios remotos
20) git remote show | visualizar nombre repositorio
21) 
    git config = Establece el nombre  del autor, el correo y demas parametros que git utiliza por defecto
    git config --global init.defaultBranch nombreRama | nombre rama default
22) git remote rm nombreRepositorio | eliminar repositorio
23) git branch | en que rama estamos ubicados
24) git branch nombreRama | crea una rama
25) git merge nombreRamaDatosNuevos | realizar un merge o unión de datos entre ramas
26) git checkout -b nombreRama | crea una rama nombreRama y nos lleva hacia ella
27) git clone 'nombre de repositorio' Clonar repositorio
28) git diff nos muestra todas la diferencia de desde el último commit guardado
29) git restore Nombre de archivo.extension = restaura archivos


-----------------------------------------------------------------------------------------------------------------
## Comandos Git para llaves SSH y GitHub

1) ls -la ~/.ssh | consultar si existe una llave ssh en nuestro pc
2) ssh-keygen -t rsa -b 4096 -C "tucorre@gmail.com" | crear una llave ssh
3) se nos pedira si queremos aceptar la ruta de creación, seleccionar ruta default
4) se nos pedira entrar una passphrase, se puede dejar vacío, o una frase sencilla
5) eval "$(ssh-agent -s)" | consultar por el agente ssh y activarlo
6) ssh-add ~/.ssh/id_rsa | añadimos una clave privada
7) cat ~/.ssh/id_rsa.pub | leer la llave publica dentro de la terminal
8) ir a github, luego ingresar a settings del perfil e ir a ssh and gpg keys

 

---------------------------------------------------------------------------------------------------------------


    git add .
    git branch -M main
    git remote add origin git@github.com:VictorPenafiel/-----------------.git
    git push -u origin main

## /* para resolver problema de origin"

git add .
git remote rm origin
git remote add origin 

------------------------------------------------------------------------------------------------
## Para crear pagina en pages

    git branch gh-pages
    git checkout 'gh-pages'
    git merge master (cuidado aca)
    git push origin gh-pages