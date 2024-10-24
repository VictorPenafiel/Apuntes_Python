Comandos de terminal (Unix/Linux)

    pwd: mostrar directorio donde estamos
    cd nombre_directorio: cambiar directorio
    cd ..: ir al directorio anterior
    ls -la: listar carpetas, permisos y archivos ocultos
        ls -lah: Tamaño de los archivos
        ls -rlh: ver directorios con permisos y tamaños
        ls -Rh: ver directorios y subdirectorios
        ls -l: Ver permisos y rutas
            d: directorio
            r: read
            w: write
            x: executable
            d[usuario{r|w|x}]: permisos del usuario
            [grupo{r|w|x}]: permisos del grupo
            [otro{r|w|x}]: permisos de otro
            ./: directorio actual
            ../: directorio padre
            ./archivoOculto o directorio: archivo oculto o directorio

    ls: listar carpetas y archivos
    mkdir nombreCarpeta: crear una carpeta o directorio
    touch index.html: crea un archivo, agregar extensión
    cp nombreArchivo carpeta/nombreArchivoCopia: copiar archivo
    rm index.html: eliminar un archivo
    mv index.html carpetaDestino/: mover un archivo
    rm -rf nombreDirectorio: eliminar carpeta y archivos
    mv nombreArchivoActual nombreArchivoNuevo: renombrar archivo
    history: historial
        !+numero del historial: ejecuta el comando del historial
    clear: limpiar registros de la terminal
    cat: se utiliza para visualizar, unir y crear archivos. Ejemplo: cat ejemplo.txt muestra el contenido de ejemplo.txt

Crear una carpeta/proyecto existente en un nuevo repositorio GIT (en GitHub)

    Abrir Git bash
    Cambiarse al directorio del proyecto existente a subir.
    Inicializar repositorio local: git init
    Agregar el contenido y cambios realizados: git add .
    Pasar el contenido del proyecto al head: git commit -m "Commit inicial"
    Ir al sitio github.com. Crear repositorio vacío con el nombre del proyecto.
    Una vez creado el repositorio vacío, copiar la dirección del mismo seleccionada la opción SSH.
    Regresar al Git bash. Vamos a hacer la conexión del repo local con el remoto (github).
    Realizar push: git push origin master

PD: Si aparece error de NO registro local de nombre de usuario y/o Email: Ejecutar: git config --global user.name "Pedro Pérez" git config --global user.email "pedro.perez@gmail.com"

Permitir visualizar todas las versiones de un proyecto: git log Muestra todas las diferencias desde el último commit guardado: git diff

Agregar cambio a rama principal: git add . git commit -m "Comentario" git push origin master
Clonar un repositorio existente en GitHub

    Ingresar al repositorio remoto Github a clonar. Copiar la dirección HTTPS o SSH del repo.
    Abrir Git Bash. Ubicarse en la carpeta local donde queremos recibir la carpeta del nuevo proyecto.
    Ejecutar: git clone git@github.com:cegb/prueba04.git
    Comenzar a hacer los cambios que corresponda.

Recordar (posteriormente): Al agregar nuevos archivos/carpetas:

    Abrir Git bash
    Cambiarse al directorio del proyecto existente clonado.
    Agregar el contenido al stage: git add .
    Pasar el contenido del proyecto al head: git commit -m "Descripción de los cambios... etc"
    Realizar push: git push origin master

Crear llave SSH local y conectar al servicio Github

Requisitos:

    Tener preinstalado el GIT (https://git-scm.com/downloads)
    Tener cuenta activa en Github

Procedimiento: EN EL GIT BASH:

    Abrir Git Bash.
    Ejecutar: ls -al ~/.ssh
    Generar la nueva llave: ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    Verificar que se han creado las llaves: ls -al ~/.ssh
    Activar el SSH-Agent: eval "$(ssh-agent -s)"
    Agregar la llave privada al agente: ssh-add ~/.ssh/id_rsa
    Copiar el contenido de la llave PÚBLICA en el portapapeles: cat ~/.ssh/id_rsa.pub
    EN EL SITIO DE GITHUB:
    Ingresar con su usuario GitHub al sitio.
    Hacer clic en su avatar (esquina superior derecha) y seleccionar "Settings" (o configuración).
    En el menú lateral izquierdo, seleccionar "SSH and GPG keys".
    Presionar el botón verde "New SSH Key".
    Colocar un título descriptivo. Ej: Notebook de Pedro.
    En el campo "Key" pegar la llave PÚBLICA que se copió en el paso 7.
    Una vez realizado estos pasos, ya estará disponible la comunicación automática entre tu equipo y GitHub.
    Como paso opcional, puede probar la comunicación con Github: ssh -T git@github.com

Comandos Git básicos

    git status: ver status del repositorio
    git config --global user.name "nombreUsuario": configurar parámetro de autor
    git config --global user.email "tucorreo@gmail.com"
    git config --list: listar configuración git
    git init: inicializar repositorio
    git add index.html: añadir un archivo
    git add.: añadir todos los archivos
    git rm --cached index.html: retirar el archivo
    git commit -m "comentario": agregar comentario
    git log: revisar todas las versiones de un proyecto
    git branch -m main: cambiar nombre de rama
    git branch -m nombreRama nombreNuevo: cambiar nombre de rama
    git checkout numeroComentario: llevarse al comentario
    git checkout nombreRama: llevarse hacia la rama
    git reset = Descompone el archivo, pero conserva el contenido del mismo
    git reset --soft HEAD~: regresar el último comentario
    git remote add origin https://github.com/{usuario}/{repo}.git
    git remote set-url origin git@github.com:adrianedutecno/iguanapage.git
    git remote rename nombreActual nombreNuevo: renombrar repositorio
    git remote -v: visualizar repositorios remotos
    git remote show: visualizar nombre repositorio
    git remote rm nombreRepositorio: eliminar repositorio
    git branch: verificar en qué rama estamos ubicados
    git branch nombreRama: crear una rama
    git merge nombreRamaDatosNuevos: realizar un merge o unión de datos entre ramas
    git checkout -b nombreRama: crea una rama y nos lleva hacia ella
    git clone 'nombre de repositorio': clonar repositorio
    git diff: mostrar todas las diferencias desde el último commit guardado
    git restore Nombre de archivo.extension: restaurar archivos

Comandos Git para llaves SSH y GitHub

    ls -la ~/.ssh: consultar si existe una llave ssh en nuestro pc
    ssh-keygen -t rsa -b 4096 -C "tucorre@gmail.com": crear una llave ssh
    Se nos pedirá aceptar la ruta de creación, seleccionar ruta default
    Se nos pedirá entrar una passphrase, se puede dejar vacío, o una frase sencilla
    eval "$(ssh-agent -s)": consultar por el agente ssh y activarlo
    ssh-add ~/.ssh/id_rsa: añadir una clave privada
    cat ~/.ssh/id_rsa.pub: leer la llave publica dentro de la terminal
    Ir a github, luego ingresar a settings del perfil e ir a ssh and gpg keys

Para resolver problemas de origen:

git add .
git remote rm origin
git remote add origin 

Para crear página en pages:

git branch gh-pages
git checkout 'gh-pages'
git merge master (cuidado aquí)
git push origin gh-pages
