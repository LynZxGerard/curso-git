# Curso de Git  / Orozco Mariscal Daniel Alejandro

Este es un repositorio para el Curso de Git/Github en el que pondre en practica los temas vistos en el curso

## Apuntes del curso

*   cd c:
*   mkdir repo
*   cd repo
*   git init
<br><br>

  ============ CHECKOUT ============

git checkout Test.txt 
*   es como un ctrl+z de un archivo que no se ha subido al repositorio
  

<br><br>
============ RESET ===============

git reset --hard
*   es tambien como un ctrl+z pero de cambios que ya se comitearon
*   Elimina TODOS LOS COMMITS seleccionados y los mueve al lugar de trabajo
*   Eliminando lo que teniamos antes en el area de trabajo
*   Hay que guardar todos los archivos del area de trabajo antes de ejecutarlo

git reset --soft 7f4e9a5
*   Se resetean los commits que se hicieron para moverlos al area de staging

git reset --soft head~1 (cambiar el 1 por x)
*   Se mueve X commits hacia atras y mueve los restantes a staging


git reset --mixed 7f4e9a5 
*   Elimina el commit y lo mueve a staging



<br><br>
============ COMMIT ==============

git commit -m "mensaje" -a
*   Actualiza en el repositorio algun cambio hecho con su respectivo mensaje

git commit --ammend
*   Permite modificar el mensaje del ultimo commit hecho (en donde esta el HEAD)       



<br><br>
============ STATUS =============  

git status
*   Demuestra el status del repositorio

git status -s
*   Demuestra el status pero mas corto
        ROJO = Cambio sin ADD ni COMMIT
        VERDE = Cambio sin COMMIT

    *   M = Modificado
    *  A = Agregado (creado)
    * ?? = Aun no agregado

<br><br>
============ ADD =============

git add notas.txt
*   Agrega a repositorio un archivo para esperar que lo comiteen
*   Se agregan archivos nuevos como archivos eliminados para demostrar que se necesita borrar un archivo del repositorio

<br><br>
============ DIFF =============

git diff --staged
*   Muestra la diferencia entre versiones
    *    ROJO = Version vieja
    *  VERDE = Version nueva

git diff cbbdd89 7f4e9a5
*   Muestra la diferencia entre versiones especificas de commits hechos cuando los buscas con un (git log --oneline)
    * ROJO = Version vieja
    * VERDE = Version nueva

git diff --name-only cbbdd89 7f4e9a5
*   Muestra nombres de los archivos que cambiaron en los commits insertados

git dif --word-diff cbbdd89 7f4e9a5
*   Muestra los cambios TEXTUALES que se hicieron en los commits insertados

<br><br>
============ LOG =============

git log
*   Demuestra los cambios comiteados

git log --oneline
*   Demuestra los mensajes de todos los commits hechos con sus codigos (abreviados a 7 caracteres)

<br><br>
============ REBASE =============

git rebase -i head~3
*   En este caso selecciona los ultimos 3 commits hechos y te permite modificarlos por VScode
*   De la lista de commits que ser ven en el VScode cambiar la palabra "pick" por "edit" para seleccionar una

git rebase --continue
*   Para que vuelvan a aparecer los demas commits que no seleccionamos
*   Una vez hecho esto, cambiara TODOS LOS HASH

<br><br>
============ BRANCH =============

git branch
*   Demuestra todas las ramas que existen en el repositorio

git checkout nombre-del-branch
*   Te mueves al branch indicado

git switch nombre-del-branch
*   Te mueves al branch indicado  (*RECOMENDADO)

git checkout -b nombre_del_branch
*   Crea una rama derivada de la que estemos ubicados

git switch -c nombre-del-branch
*   Crea una rama y te mueve hacia ella

git branch -d nombre-del-branch
*   Elimina un branch, SALIR DEL branch si es que estamos en el que queremos eliminar

git branch -m nombre-branch-viejo nombre-branch-nuevo
*   Hay que estar en una rama distinta a la que queremos editar

git branch -m nuevo-nombre-branch
*   Estando dentro del branch a editar, solo poner el nuevo nombre}

<br><br>
============ .gitignore =============

*.txt
*   Ignora todos los archivos que terminen con la extension indicada

!archivo.txt
*   Hace una excepcion de no ignorar el archivo indicado

fotos/
*   Ignora todos los archivos de una carpeta (fotos)

.gitignore_global

git config --global core.excludesfile c:/.gitignore_global
*   Para hacer un .gitignore global


EN RESUMEN
	! = No ignorar (excepcion)
	* = Ignorar

<br><br>
============ alias =============

git config --global alias.nombre-del-comando
*   Crea un alias para ejecutar una instruccion para facilitar su uso cuando es muy larga

git log --oneline --all --graph --pretty=format:'%C(auto)%h%d %s %C(black)%C(bold)%cr'
*   Muestra de manera grafica las ramas y hace cuanto tiempo se modificaron


<br><br>
============ reflog =============

git reflog
*   Muestra todas las veces que se movio el head
*   Se usa para recuperar un commit que se "elimino" para recuperar su referencia al mismo mediante su hash

<br><br>
============ clone =============<br>
git clone https://github.com/LynZxGerard/curso-git.git
*   Clona un repositorio de github como https directo a la pc

<br><br>
============ push =============<br>
git push origin
*   Empuja los cambios commiteados al origin
*   Pedira validar las credenciales de tu usuario en github

         UsarToken>Github>Settings>DeveloperSettings>PersonalAccessTokens>TokenClassic


<br><br>
# NOTAS

1. Cuando aparece un " \ No newline at end of file  (END) "
    PRESIONAR "q" para continuar usando git
   
<br><br>    
2. Cambiar los HASH y abreviarlos a una cantidad distinta de 7 digitos (para 10000000 digitos)
    git config --global core.abbrev 1000000
    
<br><br>
3. CASES
*   Kebab case   ejemplo-de-kebab-case
*   Camel Case   ejemploDeCamelCase
*   Snake Case   ejemplo_de_un_snake_case
	
<br><br>
4. MERGE

   Es cuando se hace una rama separada del main para hacer algun fix y al ser exitoso se hace el MERGE con la rama master.
<br><br>
5. MERGE CONFLICTS

*   ACCEPT CURRENT CHANGE
		Se hace el merge pero dejando lo que hay en el master
  
*   ACCEPT INCOMING CHANGE
		Se hace el merge pero dejando lo que hay en el otro branch

*   ACCEPT BOTH CHANGES
		Acepta ambos, mezclandolos

*   COMPARE CHANGES
		Muestra ambos para ver cual aceptar

<br><br>	
6. .gitignore
	al aplicar un gitignore, los cambios a ignorar solo se haran despues de hacerle commit a ese archivo, ya que los archivos que estaban antes de su creacion ya estan siendo rastreados por git por default
        

