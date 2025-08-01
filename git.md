
## Comandos de Terminal (Unix/Linux)

1.  **`pwd`**: **Muestra el directorio** donde te encuentras actualmente.
2.  **`cd /nombreDirectorio`**: **Cambia el directorio** actual al especificado.
3.  **`cd ..`**: Te **lleva al directorio anterior** (padre).
4.  **`ls -la`**: **Lista carpetas, permisos y archivos ocultos**.
    * **`ls -lah`**: Muestra el **tamaño de los archivos** en un formato legible para humanos.
    * **`ls -rlh`**: **Ver directorios con permisos y tamaños**, listados en orden inverso.
    * **`ls -Rh`**: **Ver directorios y subdirectorios** de forma recursiva.
    * **`ls -Rlh`**: **Ver directorios con permisos, tamaños y sus subdirectorios** de forma recursiva.
    * **`ls -l`**: **Ver permisos y rutas** detalladamente.
        * `d`: Indica un **directorio**.
        * `r`: Permiso de **lectura** (read).
        * `w`: Permiso de **escritura** (write).
        * `x`: Permiso de **ejecución** (executable).
        * `d[usuario{r|w|x}]`: Permisos para el **propietario** del archivo/directorio.
        * `[grupo{r|w|x}]`: Permisos para el **grupo**.
        * `[otro{r|w|x}]`: Permisos para **otros usuarios**.
        * `./`: Representa el **directorio actual**.
        * `../`: Representa el **directorio padre**.
5.  **`ls`**: **Lista las carpetas y archivos** en el directorio actual.
6.  **`mkdir nombreCarpeta`**: **Crea una carpeta o directorio** con el nombre especificado.
7.  **`touch index.html`**: **Crea un archivo** vacío; puedes agregarle una extensión (`.html` en este caso).
8.  **`cp nombreArchivo carpeta/nombreArchivoCopia`**: **Copia un archivo** a una nueva ubicación y/o con un nuevo nombre.
9.  **`rm index.html`**: **Elimina un archivo**.
10. **`mv index.html carpetaDestino/`**: **Mueve un archivo** a un directorio de destino.
11. **`rm -rf nombreDirectorio`**: **Elimina una carpeta y todo su contenido** de forma recursiva y forzada (¡usar con precaución!).
12. **`mv nombreArchivoActual nombreArchivoNuevo`**: **Renombra un archivo**.
13. **`history`**: Muestra el **historial de comandos** ejecutados.
    * **`! + numeroDelHistorial`**: **Ejecuta un comando específico** del historial por su número.
14. **`clear`**: **Limpia los registros de la terminal** (la pantalla).
15. **`cat`**: Se utiliza para **visualizar, unir y crear archivos**. Por ejemplo, `cat ejemplo.txt` muestra el contenido de `ejemplo.txt`.
16. **`sudo su`**: **Habilita el usuario root** (superusuario), permitiendo ejecutar comandos con privilegios elevados.
17. **`zip`**: **Comprime ficheros en archivos `.zip`**.
18. **`unzip`**: **Extrae archivos de archivos `.zip`**.
19. **`clear`**: (Repetido, pero funcional) **Limpia la ventana del terminal**.
20. **`wget`**: **Descarga un archivo de Internet directamente** a la terminal.

---

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
Clonar repositorio

    git clone + llave HTTPS

Manter actualizaciones del reposotorio, para actualizar en caso de cambio de repositorio

    git pull 

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

### EN EL SITIO DE GITHUB:  

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

---

## Comandos Git

* **`&&`** : Se utiliza para concatenar comandos Git.

1.  **`git status`** : Permite **ver el estado** del repositorio.
2.  **`git config --global user.name "nombreUsuario"`** : Configura el parámetro de **autor globalmente**.
3.  **`git config --global user.email "tucorreo@gmail.com"`** : Configura el **correo electrónico del autor globalmente**.
4.  **`git config --list`** : **Lista la configuración** actual de Git.
5.  **`git init`** : **Inicializa** un nuevo repositorio Git.
6.  **`git add index.html`** : **Añade un archivo** específico (`index.html`) al área de preparación.
7.  **`git add .`** : **Añade todos los archivos** modificados al área de preparación.
8.  **`git rm --cached index.html`** : **Retira un archivo** del área de preparación sin borrarlo del disco.
9.  **`git commit -m "comentario"`** : **Agrega un comentario** al commit.
    * **`git commit --amend`** : Una manera práctica de **modificar el commit más reciente**.
10. **`git log`** : Permite **revisar todas las versiones** de un proyecto.
    * **`git log --oneline`** : Muestra un **formato más conciso** de comentarios y ramas del historial.
11. **`git branch -m main`** : **Cambia el nombre** de la rama actual a `main`.
12. **`git branch -m nombreRama nombreNuevo`** : **Renombra una rama** específica.
13. **`git checkout numeroComentario`** : Nos **lleva a un comentario** específico (usando su hash).
14. **`git checkout nombreRama`** : Nos **cambia a la rama** especificada.
15. **`git reset`** : **Descompone el archivo** (lo saca del área de preparación), pero **conserva su contenido**.
    * **`git reset --soft HEAD~`** : **Regresa el último commit** (lo deshace, pero mantiene los cambios).
16. **`git remote add origin https://github.com/{usuario}/{repo}.git`** : **Agrega un repositorio remoto** llamado `origin`.
17. **`git remote set-url origin git@github.com:adrianedutecno/iguanapage.git`** : **Establece una nueva URL** para el repositorio remoto `origin`.
18. **`git remote rename nombreActual nombreNuevo`** : **Renombra un repositorio remoto**.
19. **`git remote -v`** : **Visualiza los repositorios remotos** con sus URLs.
20. **`git remote show`** : **Visualiza el nombre** y otros detalles del repositorio remoto.
21. **`git config`** : **Establece el nombre del autor**, el correo y demás parámetros que Git utiliza por defecto.
    * **`git config --global init.defaultBranch nombreRama`** : Configura el **nombre de la rama por defecto** para nuevos repositorios.
22. **`git remote rm nombreRepositorio`** : **Elimina un repositorio remoto**.
23. **`git branch`** : Muestra **en qué rama estamos ubicados** y lista todas las ramas locales.
24. **`git branch nombreRama`** : **Crea una nueva rama** con el nombre especificado.
25. **`git merge nombreRamaDatosNuevos`** : Realiza un **merge o unión de datos entre ramas**.
26. **`git checkout -b nombreRama`** : **Crea una rama (`nombreRama`) y nos cambia** a ella inmediatamente.
27. **`git clone 'Nombre de repositorio'`** : **Clona un repositorio** existente.
28. **`git diff`** : Nos **muestra todas las diferencias** desde el último commit guardado.
29. **`git restore NombreDeArchivo.extension`** : **Restaura archivos** a su estado en el último commit o en el área de preparación.
30. **`git pull origin master`** : **Actualiza el repositorio local** con los cambios del repositorio remoto (`origin`) de la rama `master`.

---

## Comandos Git para llaves SSH y GitHub


1.  **`ls -la ~/.ssh`**: Permite **consultar si ya existe una llave SSH** en tu equipo.
2.  **`ssh-keygen -t rsa -b 4096 -C "tucorreo@gmail.com"`**: **Crea una nueva llave SSH**.
    * `-t rsa`: Especifica el tipo de cifrado RSA.
    * `-b 4096`: Define el tamaño de la clave en bits para mayor seguridad.
    * `-C "tucorreo@gmail.com"`: Agrega un comentario para identificar la clave, usualmente tu correo.
3.  **Seleccionar ruta default**: Cuando se te pida la ruta de creación, simplemente **acepta la ruta por defecto** (`~/.ssh/id_rsa`).
4.  **Entrar una passphrase**: Se te pedirá una *passphrase*. Puedes **dejarla vacía** (presionando Enter dos veces) para no tener que ingresarla cada vez que uses la clave, o ingresar una **frase sencilla** si deseas una seguridad adicional.
5.  **`eval "$(ssh-agent -s)"`**: **Consulta por el agente SSH y lo activa**, lo que te permite usar tus claves sin tener que ingresarlas constantemente.
6.  **`ssh-add ~/.ssh/id_rsa`**: **Añade tu clave privada** (la que acabas de crear) al agente SSH.
7.  **`cat ~/.ssh/id_rsa.pub`**: **Lee el contenido de tu llave pública** directamente en la terminal. Necesitarás copiar este contenido.
8.  **Ir a GitHub y configurar**: Navega a GitHub, luego ve a la **configuración de tu perfil (`Settings`)** y busca la sección **`SSH and GPG keys`**. Ahí deberás añadir el contenido de tu llave pública.

---



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