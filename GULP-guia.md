# 3.Gulp

## 3.1.Organización

* Carpeta de trabajo: `src`
* Carpeta de publicación: `dist`
* Dentro de `src`: `img`, `scss`, `css` y `js`
* Dentro de `dist`: `img`, `scss`, `css` y `js`
* Instalaremos: `node_modules`
* Tasks: `gulpfile.js`
* Info del proyecto: `package.json`

## 3.2.Instalación de Gulp

1. Instalar por terminal (Linux/Mac) o descargar el instalador (Windows) descargando el ejecutable en [nodejs.org](https://nodejs.org)
2. A través de la terminal comprobar qué versión tenemos de node.js tenemos instalado. ``node -v``. _Podemos usar el la termianl de [GitBash](https://git-scm.com/)_
3. Ahora instalamos gulp ``npm install -g gulp`` Para Mac o Linux ``npm sudo install -g gulp``
4. Para asegurarnos de que se ha instalado correctamente ``gulp -v``

## 3.3.Instalación de entorno

_Por primera vez_

1. Creamos package.json: `npm init`
2. Para que nuestra terminal reconozca los comandos de gulp: `npm install --global gulp-cli`
3. Instalamos node_modules: `npm i gulp --save-dev`
4. Creamos y configuramos nuestro gulpfile.js añadiendo las funciones que necesitemos
5. Instalamos cada función con su código correspondiente

_En base al package.json_

1. Creamos las carpetas
2. Situamos el gulpfile.js y package.json en la raiz de nuestro proyecto
3. Instalamos node_modules: `npm i gulp --save-dev`
4. Instalar lo referenciado en .json: `npm i`