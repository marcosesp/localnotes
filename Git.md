Git:

Es un sistema de control de versiones distribuido. Es utilizado principalmente en el desarrollo de software, pero puede manejar cualquier tipo de archivos.
Su objetivo es llevar un registro de los cambios de un proyecto, facilitar el trabajo colaborativo y permitir volver a versiones anteriores en caso necesario.

Control de versiones:

Permite guardar un historial completo de todos los cambios que se realizan en un proyecto, cada cambio se guarda con un "commit", que incluye lo siguiente:
- Los archivos modificados.
- El autor.
- La fecha y la hora.
- Un mensaje descriptivo.

Distribucion:

Cada persona clona un repositorio y con este obtiene una copia completa del historial del proyecto, no solo la ultima version. Esto significa que se puede trabajar
sin conexion a internet, y mas tarde sincronizar los cambios en un servidor central como (Github, Gitlab o Bitbucket).

Como funciona git (flujo basico)

Repositorio:

Es una carpeta que contiene el proyecto y el historia de cambios, puede estar en una maquina local o en un servidor remoto.

Areas de trabajo:
- Working Directory: donde editas los archivos.
- Staging Area (index): donde seleccionas los archivos que quieres incluir en el siguiente commit
- Repositorio Local: donde se guarda la historia de los commits.
- Repositorio Remoto: Copia centralizada en un servidor (opcional)

Flujo de trabajo:

- git config --global: Este seria de las primeras configuraciones que se estaria realizando en un proyecto.
Esto mayormente se utilizaia pra setear nuestro ambiente de manera global y no por proyectos. es decir
esto afectaria todos los proyecto que creemos a partir de aqui. Esta configuracion se guarda dentro de un archivo
en el home del usuario que realizo esta configuracion dentro de un archivo llamado .gitconfig.

Ejemplo inicial con git config

- git config --global user.name Marcos # para setear un nombre a nuestro archivo de configuracion global.
- git config --global user.email marcosef24@gmail.com # para setear un correo a nuestro archivo de configuraciones global
- git config --global core.editor "code --wait" # para setear visual studio code como editor de texto por defecto.
- git config --global -e # para abrir visual studio code, en este caso como indicamos en lo anterior "code --wait", esto lo que esperara a que cerremos el vscode.
- git config --global core.autocrlf "true" para windows e "input" para linux o mac. 

- git init: Se utiliza para inicializar la carpeta en la que estamos como proyecto de git
- git add "archivo o carpeta": mueve el archivo modificado al area de Staging.
- git commit -m "mensaje": Guarda los cambios en el repositorio local.
- git push: Envia tus commits al repositorio remoto
- git pull: Descarga y fusiona cambios del repositorio remoto.
- git log
- git reflog
- git status

Entendiendo el flujo de trabajo

- Computador
- git add "archivo o carpeta": mueve el archivo modificado al area de Staging. Usado para verificar lo que eventualmente paseromos a nuestro repositorio final.
- stage
 Etapa intermeda para indicar los cambios que efectuamos que pasaran al repo, una vez revisado aqui podremos en caso de que no queramos pasar cambios devolverlos
es decir sacarlos de la etapa stage. En caso de que queramos pasarlo todo ya se hara con el commit.
- commit git commit -m "mensaje": 
Cuando se realiza el git commit, ya en esta etapa los archivos que estan aqui se quitan del estado del staging(estado anterior) y ya con los archivos en este estado
estamos listo para subirlos a nuestro repositorio (nube).
- server

herramientas graficas de git
- sourcetree
- gitkraken
- githubdesktop


Table 1.1. Git Quick Reference
Command	Description
git clone URL 	Clone an existing Git project from the remote repository at URL into the current directory.
git status 	    Display the status of files in the working tree.
git add file 	Stage a new or changed file for the next commit.
git rm file 	Stage removal of a file for the next commit.
git reset 	    Unstage files that have been staged for the next commit.
git commit 	    Commit the staged files to the local repository with a descriptive message.
git push 	    Push changes in the local repository to the remote repository.
git pull 	    Fetch updates from the remote repository to the local repository and merge them into the working tree.
git revert   	Create a new commit, undoing the changes in the referenced commit. You can use the commit hash that identifies the commit, although there are other ways to reference a commit.
git init 	    Create a new project.
git log 	    Display the commit log messages.
git show     	Shows what was in the change set for a particular commit hash.

--Iniciando proyecto en git

Lo primero es crear un proyecto en git y asignarle un nombre
Crear la carpeta del proyecto y luego inicalizarla con git init. Esto hara que el proyecto sea utilizado para git
luego conectamos el proyecto con el repositorio remoto creando una llave ssh que luego adicionaremos en git debido a que el acceso por contraseña esta deshabilitado por defecto.

