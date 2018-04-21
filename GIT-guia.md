# 1.Github

Esta es una pequeña guía para retomar github cuando llevo un tiempo sin usarlo.
_Versión 2.0_ `Última actualización 14 abril 2018´

## Antes de emepezar, recordar los comandos de la consola

* Ir a un directorio: `cd y nombre del directorio`
* Paso atrás: `cd ..`
* Ver items de directorio actual: `ls -l`
* Crear nuevo directorio `mkdir nombre`
* Crear un archivo: `touch nombredelarchivo.extensión`
* Con las flechas arriba y abajo vemos el historial de las teclas que hemos ido usando
* Abrir programa o directorio: `open .`

## 1.1.Configuración de la terminal

Si nunca hemos usado git nos tenemos que bajar [GitBash](https://git-scm.com/) y configurar la terminal con nuestros datos y el repositorio remoto con el que vamos a trabajar.

* Comprobar cual es la configuración actual `git config --global --list´
* Si hay otro usuario que no queremos: Primero, elimina el usuario actual (nombre y correo): `git config --global --unset-all user.name´ `git config --global --unset-all user.email´
* Nombre: `git config –global user.name “nombre”`
* Email: `git config global user.email example@example.com`

## 1.2.Flujo de trabajo con git, el día a día

* Crear .git si no lo tiene: `git init`donde se almacenará la info de este repo: las ramas, comentarios y el HEAD
* Añadir origen: `git remote add origin https://github.com/example.git`
* Crear un readme si es un nuevo proyecto, con la info de dicho proyecto: `touch README.md´ con la diguiente info:

```
### Folders ###

node_modules

### Windows ###
# Windows image file caches
Thumbs.db
ehthumbs.db

# Folder config file
Desktop.ini

# Recycle Bin used on file shares
$RECYCLE.BIN/

# Windows Installer files
*.cab
*.msi
*.msm
*.msp

# Windows shortcuts
*.lnk 
´´´


* Crear gitignore si es un nuevo proyecto: `touch .gitignore´
1. Comprobar qué se se ha añadido al HEAD: `git status`
2. Bajarme lo que está en el repo: `git pull origin master`
3. Comprobar los commits anteriores: `git log´
3. Si quiero añadir algún archivo al HEAD para subirlo: `git add nombredelarchivo ó Añadir todo git add .`
4. Creo un comentario descriptivo: `git commit -m “mensaje-descriptivo”`
5. Subir al repo: `git push origin nombre-de-la-rama`

### 1.2.1.Ramas

* Saber en qué rama estamos: `git branch`
* Crear nueva rama: `git branch nombre-de-la-rama`
* Cambiar de rama: `git checkout nombre-de-la-otra-rama`
* Crear y cambiar de rama simultáneamente: `git checkout -b nombre-de-la-rama`
* Cambiar el nombre de la rama: `git branch -m nombre-antiguo nombre-nuevo`
* Eliminar rama local: `git branch -d nombre-de-la-rama`
* Eliminar rama remota: `git push origin --delete nombre_rama`
* Forzar eliminar rama: `git branch -D nombre-de-la-rama`
* Listado de todas las cosas que podemos hacer: `git branch -h`

## 1.2.2.Deshaciendo cosas

* Para deshacer el git add: `git reset HEAD <archivo>...`
* Para deshacer el git add en todos los archivos: `git reset HEAD .`
* Eliminar archivo en local y remoto: `git rm miarchivo.php` y comitear
* Eliminar una carpeta en local y remoto: `git rm -r micarpeta`
* Eliminar rama local: `git branch -d nombre-de-la-rama`
* Eliminar rama remota: `git push origin --delete nombre_rama`
* Forzar eliminar rama: `git branch -D nombre-de-la-rama`

### 1.2.3.Merge

_Cuando no hay cambios es master_

1. Ir a master: `git checkout master`
2. Mergear la rama: `git merge nombre-de-la-rama`

_Cuando si hay cambios en master pero no hay conflicto despues de intentar mergear_

1. Ir a master: `git checkout master`
2. Mergear la rama: `git merge nombre-de-la-rama
3. Hacemos un commit: `git commit -m “mensaje-descriptivo”` _Nos pide hacer un commit debido a que junta los cambios de ambas ramas en un nuevo commit_

_Qué hacer cuando hay conflicto chungo despues de intentar mergear_

1. Comprobar qué conflictos hay: `git status`
2. Pasamos a nuestro editor y vemos esta estructura nuestro código dividido por símbolos de mayor y menos que, y unas barras.
3. Eliminamos esto que nos ha generado, salvo lo que nos queramos quedar.
4. Añadimos: `git add nombre-del-archivo`
5. Comiteamos: `git commit -m "mensaje-descriptivo"`
6. Con vim resolvemos el conflicto: `:wq (sintaxis de vim)`

## 1.3.Alias, Atajos de teclado

_Para hacer atajos cuando usamos combinaciones de comandos_

* Crearlo: `Git config --global alias.nombredelalias 'comandos de git'`
* Ver todos nuestros alias: `git config --global --get-regexp`
* Eliminar un alias: `git config --global --unset alias.nombredelalias`

## 1.4 Github pages

### 1.4.1 Usar las plantillas de github

_En la página de Github, usando sus plantillas con markdown_

1. Ir al repo en cuestión, en master
2. Ir a settings y bajar hasta la sección `GitHub Pages`
3. Botón: Launch automatic page generator
4. Introducir el texto con Markdown
5. Elegir plantilla y seguir pasos

### 1.4.2 Subir mi proyecto web

_Subir archivos a gh-pages_

1. Crear rama con nombre: `gh-pages`
2. Push: con el index en la raiz y demás carpetas
3. Para visitar la página: `http://nombre-de-usuario.github.io/nombre-del-repo`