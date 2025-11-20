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

- Computador:
- git add "archivo o carpeta": mueve el archivo modificado al area de Staging. Usado para verificar lo que eventualmente paseromos a nuestro repositorio final.
- stage:
 Etapa intermeda para indicar los cambios que efectuamos que pasaran al repo, una vez revisado aqui podremos en caso de que no queramos pasar cambios devolverlos
 es decir sacarlos de la etapa stage. En caso de que queramos pasarlo todo ya se hara con el commit.
- commit: git commit -m "mensaje": 
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

- Lo primero es crear un proyecto en git y asignarle un nombre.
- Crear la carpeta del proyecto y luego inicalizarla con git init. Esto hara que el proyecto sea utilizado para git.
- Conectamos el proyecto con el repositorio remoto creando una llave ssh que luego adicionaremos en git debido a que el acceso por contraseña
  esta deshabilitado por defecto.

--Generando la llave ssh

ssh-keygen -t si quieres elegir entre diferentes algoritmos de encriptacion (rsa, ecdsa, dsa) entre otros. Puedes dejarlo como esta y luego copiar 
la llave publica en el servidor remoto de git
para poder autenticar por llave.

--Finalizando la configuracion del proyecto

- Luego de haber creado la llave e inicializado el proyecto podemos probar conexion hacia git con:
* ssh -T git@github.com, deberia salir el mensaje: 
Hi marcosesp! You've successfully authenticated, but GitHub does not provide shell access.

Nota: Si deseas ver todo el flujo para validar de que tu llave esta siendo utilizada puede adicionar la opcion -v
* ssh -Tv git@github.com

Si la conexion se establecio correctamente procederemos a crear la conexion hacia el repositorio que acabamos de crear en el servidor en este caso se llama "localnotes"
primero validaremos que conexiones remotas existen, como es un proyecto nuevo deberia de estar vacio. Esto lo haremos con:
* git remote -v

Nota importante: si al momento de comenzar a trabajar un proyecto, si se realiza un git clone desde una url de un proyecto, git por defecto agrega el origin como 
https, que fue como se clono, para poder eliminar o cambiar el origin se pueden realizar de la siguiente forma.

para eliminarlo:
 * git remote remove origin
 * git remote rm origin

para cambiarlo:
 * git remote set-url origin git@github.com:marcosesp/localnotes.git

para adicionar otro origin adicional:
 * git remote add ssh-origin git@github.com:marcosesp/localnotes.git  

Luego crearemos nuestra conexion hacia ese repositorio en particular esto lo haremos configurando lo siguiente:
* git remote add origin git@github.com:marcosesp/localnotes.git

Una vez configurado el repositorio remoto al cual subiremos todos nuestros cambios procederemos a pasarlos por los diferentes stages.

* git add "archivo.txt"
* git commit -m "Agregando primer archivo.txt"

Validar nombre de la rama en la que estamos trabajando en este caso la master por loque el push debe ser con ese nombre:
* git push -u origin master

Con este proceso acabamos de subir el archivo.txt al repositorio creado localnotes.

-- trabajando con git
* git branch me permite crear un nuevo branch pero para poder cambiar al nuevo branch habria que utilizar git checkout

* git checkout -b "newbranch": Permite crear un nuevo branch y realizar el cambio a ese nuevo branch.

--Restore, checkout y mas

* restore: git restore sirve par deshacer cambios no confirmados es decir que aun no han sido comitiados en el directorio de trabajo o para restaurar
archivos desde un commit especifico, desde el staging area o desde otra rama. git restore no modifica commits, solo modifica el working directory o staging
area.

* git restore archivo.txt

Esto elimina tus cambios no guradados en archivo.txt y lo deja tal como estaba en el head.



