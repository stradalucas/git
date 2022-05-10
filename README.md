# Git

Fuente: <br>
https://diegomalagon.com/lista-de-comandos-utiles-de-git/ <br>
https://www.hostinger.com.ar/tutoriales/comandos-de-git


Aprenderse toda la lista de comandos de Git es algo imposible. Con el tiempo dominamos los suficientes. Sin embargo, de vez en cuando necesitamos buscar alguno que sabemos que existe pero no recordamos. Aquí dejo la lista de comandos útiles de Git y que no necesitamos aprender de memoria.

## **Después de instalar Git**

Asignar tu nombre y correo para que tus commits queden firmados con estos datos. Al menos el correo debe coincidir con el que uses en plataformas como Github, Gitlab o Bitbucket. En las configuraciones de las plataformas puedes añadir más de un correo por si usas Git en varios computadores con diferentes correos, por ejemplo, el personal y el del trabajo.

```
git config --global user.name "<tunombre>"
git config --global user.email <tucorreo>
```

Configuración para cuando se realice un "git push" solo se suban los cambios de la rama actual.

```
git config --global push.default simple

```

Para evitar inconvenientes con el formato de los archivos cuando se trabaja en un equipo de desarrolladores que usan diferentes sistemas operativos se debe aplicar una de estas configuraciones.

```
git config --global core.autocrlf input	Si usan únicamente Linux y Mac.
git config --global core.autocrlf false	si usan únicamente Windows.
```

## **Clonar o iniciar un repositorio**
```
git clone <url>	Clonar un repositorio en mi computador.
git status	Ver el estado de los archivos en el repositorio.
```

## **Agregar o modificar repositorios remotos**

```
git remote add upstream <url>	Agregar repositorio remoto paralelo (upstream, o cualquier otro nombre).
git remote set-url origin <nueva-url>	Modificar url de un repositorio remoto.
git remote -v	Ver todos los repositorios remotos.
git remote r <nombre>	Remover un repositorio remoto.
git remote show origin	Ver estado de las ramas del repositorio remoto y local.
```

## **Agregar archivos al escenario**
```
git add --all	Todos los archivos (nuevos o modificados).
git add *.js	Por extensión.
git add src/	Por carpeta
```

## **Consignar cambios**
```
git commit -a -m "Mensaje descriptivo"	Agrega todos los cambios al escenario y los guarda.
git commit --amend -m "Mensaje descriptivo"	Corrige el último commit. Cambios en archivos y también el mensaje.
```

## **Subir y bajar consignaciones del repositorio remoto**

```  
git pull origin <rama>	Descarga las consignaciones del repositorio remoto y realiza la mezcla con el repositorio local.
git fetch origin <rama>	Descarga las consignaciones del repositorio remoto pero no realiza la mezcla con el repositorio local.
git pull	Descarga las consignaciones del repositorio remoto y realiza la mezcla con el repositorio local para la rama actual. Además, descarga todas las referencias a ramas y tags.
```

## **Revertir cambios**

```  
git reset --hard HEAD	Deshace todos los cambios sin consignar.
git stash	Deshacer/ocultar los cambios del escenario actual.
git stash pop	Restaurar cambios ocultos del escenario actual.
git reset --soft HEAD^	Devuelve al commit anterior.
git reset --hard HEAD^	Deshace completamente los cambios hasta la penúltima consignación.
git reset --hard HEAD^^	Deshace completamente los cambios de las últimas 2 consignaciones.
```

## **Branch - Ramas**
```  
git branch -r	Muestra las ramas en el repositorio remoto.
git branch <nombre>	Crea una rama.
git checkout -b <nombre>	Agregar una rama y moverse a esta.
git checkout <rama>	Cambiar al escenario de otra rama en el repositorio local.
git checkout -t origin/<rama>	Cambiar al escenario de una rama del repositorio remoto.
git checkout -b <nuevonombre> origin/<ramaremota>	Agregar al repositorio local una rama remota con un nombre distinto.
git merge <rama>	Mezclar consignaciones de una rama a la rama actual.
git branch -d <rama>	Eliminar rama local.
git branch -D <rama>	Forzar eliminación de rama local.
git push origin :<rama>	Eliminar rama del repositorio remoto.
git remote prune origin	Eliminar referencias de ramas remotas que ya no existen.
```

## **Etiquetas - Tags - Releases**
```
git tag -n	Ver lista de tags con el mensaje.
git tag -a <nombre> -m "<mensaje>"	Agregar tag.
git checkout <tag>	Moverse al escenario de un tag.
git push --tags	Subir todos los tags nuevos al repositorio remoto.
git clone -b <tag> <url-repository>	Clonar un tag específico de un repositorio.
git tag -d <tag>	Eliminar un tag del repositorio local.
git push origin :refs/tags/<tag>	Eliminar un tag del repositorio remoto.
```

## **Comparaciones**
```
git diff HEAD	Cambios de la última consignación.
git diff HEAD^	Cambios de la penúltima consignación.
git diff HEAD~5	Cambios de 5 consignaciones atrás.
git diff <archivo>	Ver cambios de un archivo específico.
git diff 4fb063f..f5a6ff9	Ver diferencias entre 2 commits.
git diff <rama1> <rama2>	Ver diferencias entre 2 ramas.
git blame <archivo> --date short	Conocer las historia de un cambio que no se entiende.
```
  
## **Eliminar seguimiento de archivos**
```
git rm --cache <archivo>	Elimina el archivo del escenario y todo su historial del repositorio.
```

## **Historial de consignaciones**
```
git log --oneline	Muestra la lista de consignaciones de manera resumida.
git log -5	Muestra las últimas 5 o x consignaciones.
git log --since=1.minute.go	Muestra las consignaciones desde hace un minuto.
git log --since=1.day.ago	Muestra las consignaciones desde hace un día.
git log --since=1.month.ago --until=2.weeks.ago	Muestra las consignaciones desde hace un mes hasta hace 2 semanas.
git log --since=2014-01-01 --until=2018-12-21	Muestra las consignaciones entre 2 fechas.
```

## **Alias**

Y para agilizar el trabajo estos son los alias para los comandos que más uso. Podemos crear el alias con el nombre que queramos para cualquier comando. Aquí estan los mios.
```
git config --global alias.br branch	br para branch
git config --global alias.ci commit	ci para commit
git config --global alias.st status	st para status
git config --global alias.aa 'add --all'	aa para add --all (agregar todo)
git config --global alias.lol 'log --oneline'	lol para ver commits en formato corto
git config --global alias.lg 'log --pretty="format:%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset" --abbrev-commit'	log formato amplio de una sola linea
```

Espero sea de tu utilidad y pases por aquí de vez en cuando. Recuerda que lo estaré actualizando según lo vea necesario. Gracias.

[Comandos de GIT Básicos - Guía Completa (hostinger.com.ar)](https://www.hostinger.com.ar/tutoriales/comandos-de-git)|


# **Comandos de GIT básicos**

Aquí hay algunos comandos básicos de GIT que debes conocer:

- **git init** creará un nuevo repositorio local GIT. El siguiente comando de Git creará un repositorio en el directorio actual:

```
git init
```

- Como alternativa, puedes crear un repositorio dentro de un nuevo directorio especificando el nombre del proyecto:

```
git init [nombre del proyecto]
```

- **git clone** se usa para copiar un repositorio. Si el repositorio está en un servidor remoto, usa:

```
git clone nombredeusuario@host:/path/to/repository

```

- A la inversa, ejecuta el siguiente comando básico para copiar un repositorio local:

```
git clone /path/to/repository
```

- **git add** se usa para agregar archivos al área de preparación. Por ejemplo, el siguiente comando de Git básico indexará el archivo temp.txt:

```
git add <temp.txt>
```

- **git commit** creará una instantánea de los cambios y la guardará en el directorio git.

```
git commit –m “El mensaje que acompaña al commit va aquí”
```

- 
    
    Ten en cuenta que los cambios confirmados no llegarán al repositorio remoto.
    
- **git config** puede ser usado para establecer una configuración específica de usuario, como el email, nombre de usuario y tipo de formato, etc. Por ejemplo, el siguiente comando se usa para establecer un email:

```
git config --global user.email tuemail@ejemplo.com
```

- La opción -global le dice a GIT que vas a usar ese correo electrónico para todos los repositorios locales. Si quieres utilizar diferentes correos electrónicos para diferentes repositorios, usa el siguiente comando:

```
git config --local user.email tuemail@ejemplo.com
```

- **git status** muestra la lista de los archivos que se han cambiado junto con los archivos que están por ser preparados o confirmados.

```
git status
```

- **git push** se usa para enviar confirmaciones locales a la rama maestra del repositorio remoto. Aquí está la estructura básica del código:

```
git push  origin <master>
```

- 
    
    Reemplaza <master> con la rama en la que quieres enviar los cambios cuando no quieras enviarlos a la rama maestra.
    
- **git checkout** crea ramas y te ayuda a navegar entre ellas. Por ejemplo, el siguiente comando crea una nueva y automáticamente se cambia a ella:

```
command git checkout -b <branch-name>
```

- Para cambiar de una rama a otra, sólo usa:

```
git checkout <branch-name>
```

- **git remote** te permite ver todos los repositorios remotos. El siguiente comando listará todas las conexiones junto con sus URLs:

```
git remote -v
```

- Para conectar el repositorio local a un servidor remoto, usa este comando:

```
git remote add origin <host-or-remoteURL>
```

- Por otro lado, el siguiente comando borrará una conexión a un repositorio remoto especificado:

```
git remote <nombre-del-repositorio>
```

- **git branch** se usa para listar, crear o borrar ramas. Por ejemplo, si quieres listar todas las ramas presentes en el repositorio, el comando debería verse así:

```
git branch

```

- Si quieres borrar una rama, usa:

```
 git branch -d <branch-name>
```

- **git pull** fusiona todos los cambios que se han hecho en el repositorio remoto con el directorio de trabajo local.

```
git pull
```

- **git merge** se usa para fusionar una rama con otra rama activa:

```
git merge <branch-name>
```

- **git diff** se usa para hacer una lista de conflictos. Para poder ver conflictos con respecto al archivo base, usa:

```
git diff --base <file-name>
```

- El siguiente comando se usa para ver los conflictos que hay entre ramas antes de fusionarlas:

```
git diff <source-branch> <target-branch>
```

- Para ver una lista de todos los conflictos presentes usa:

```
git diff
```

- **git tag** marca commits específicos. Los desarrolladores lo usan para marcar puntos de lanzamiento como v1.0 y v2.0.

```
git tag 1.1.0 <instert-commitID-here>
```

- **git log** se usa para ver el historial del repositorio listando ciertos detalles de la confirmación. Al ejecutar el comando se obtiene una salida como ésta:

```
commit 15f4b6c44b3c8344caasdac9e4be13246e21sadw
Author: Alex Hunter <alexh@gmail.com>
Date:   Mon Oct 1 12:56:29 2016 -0600
```

- **git reset** sirve para resetear el index y el directorio de trabajo al último estado de confirmación.

```
git reset - -hard HEAD
```

- **git rm** se puede usar para remover archivos del index y del directorio de trabajo.

```
git rm filename.txt
```

- **git stash** guardará momentáneamente los cambios que no están listos para ser confirmados. De esta manera, pudes volver al proyecto más tarde.

```
git stash
```

- **git show** se usa para mostrar información sobre cualquier objeto git.

```
git show
```

- **git fetch** le permite al usuario buscar todos los objetos de un repositorio remoto que actualmente no se encuentran en el directorio de trabajo local.

```
git fetch origin
```

- **git ls-tree** te permite ver un objeto de árbol junto con el nombre y modo de cada ítem, y el valor blob de SHA-1. Si quieres ver el HEAD, usa:

```
git ls-tree HEAD
```

- **git cat-file** se usa para ver la información de tipo y tamaño de un objeto del repositorio. Usa la opción -p junto con el valor SHA-1 del objeto para ver la información de un objeto específico, por ejemplo:

```
git cat-file –p d670460b4b4aece5915caf5c68d12f560a9fe3e4
```

- **git grep** le permite al usuario buscar frases y palabras específicas en los árboles de confirmación, el directorio de trabajo y en el área de preparación. Para buscar por www.hostinger.com en todos los archivos, usa:

```
git grep “www.hostinger.com”
```

- **gitk** muestra la interfaz gráfica para un repositorio local. Simplemente ejecuta:

```
gitk
```

- **git instaweb** te permite explorar tu repositorio local en la interfaz GitWeb. Por ejemplo:

```
git instaweb –http=webrick
```

- **git gc** limpiará archivos innecesarios y optimizará el repositorio local.

```
git gc
```

- **git archive** le permite al usuario crear archivos zip o tar que contengan los constituyentes de un solo árbol de repositorio. Por ejemplo:

```
git archive - -format=tar master
```

- **git prune** elimina los objetos que no tengan ningún apuntador entrante.

```
git prune
```

- **git fsck** realiza una comprobación de integridad del sistema de archivos git e identifica cualquier objeto corrupto

```
git fsck
```

- **git rebase** se usa para aplicar ciertos cambios de una rama en otra. Por ejemplo:

```
git rebase master
```

# **Hoja de trucos de los comandos de GIT en .pdf**

Si estás empezando con GIT, puede ser difícil recordar incluso los comandos básicos. Por eso, hemos preparado una hoja de trucos de GIT para ayudarte a dominar el software. Guarda el archivo en tus dispositivos o imprímelo para tenerlo siempre listo cuando tengas que recordar los comandos de GIT
