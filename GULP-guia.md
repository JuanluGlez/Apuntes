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
2. A través de la termina comprobar qué versión tenemos de node.js tenemos instalado. ``node -v``. _Podemos usar el la termianl de [GitBash](https://git-scm.com/)_
3. Ahora instalamos gulp ``npm install -g gulp`` Para Mac o Linux ``npm sudo install -g gulp``
4. Para asegurarnos de que se ha instalado correctamente ``gulp -v``

## 3.3.Instalación de entorno

_Por primera vez_

1. Creamos package.json: `npm init`
2. Para que nuestra terminal reconozca los comandos de gulp: `npm install --global gulp-cli`
3. Instalamos node_modules: `npm i gulp --save-dev`
4. Creamos y configuramos nuestro gulpfile.js añadiendo las funciones que necesitemos _Ver más abajo posibles configuraciones_
5. Instalamos cada función con su código correspondiente

_En base al package.json_

1. Creamos las carpetas
2. Situamos el gulpfile.js y package.json en la raiz de nuestro proyecto
3. Instalamos node_modules: `npm i gulp --save-dev`
4. Instalar lo referenciado en .json: `npm i`

## 3.3 Crear nuestro gulpfile.js
```
var gulp = require('gulp');
var sass = require('gulp-sass');
var autoprefixer = require('gulp-autoprefixer');
//plumber por defecto, pero le añadiremos el onError de Nahuel
var plumber = require('gulp-plumber');
//beepbeep y colors son ajenos a gulp, valen para mas cosas, por eso
//no llevan gulp- delante
var beep = require('beepbeep'); //permite mandar sonidos en la terminal
var colors = require('colors'); //permite poner colores en lso mensajes de la terminal
//al mismo tiempo que crea la variable la ejecuta
var browserSync = require('browser-sync').create();
var imagemin = require('gulp-imagemin'); //compresión de las imágenes sin pérdidas
var pngquant = require('imagemin-pngquant');

//gulp-plumber de Nahuel
//MENSAJE DE ERROR
var onError = function(err) {
    beep([200, 200]);
    console.log(
        '\n\n****************************************************\n'.bold.gray +
        '*****************'.bold.gray + ' \(╯°□°)╯'.bold.red + ' ︵ '.bold.gray + 'ɹoɹɹǝ '.bold.blue + '*****************'.bold.gray +
        '\n****************************************************\n\n'.bold.gray +
        String(err) +
        '\n\n*******************************************************\n\n'.bold.gray);
    this.emit('end');
};

//css es el nombre que le ponemos nosotros a la f(x), 
//puede ser el que queramos
gulp.task('css', function() {
    return gulp.src('src/scss/main.scss')
        //pipe encadena todas las funciones que le añadamos
        .pipe(plumber({
            errorHandler: onError
        }))
        .pipe(sass())
        .pipe(autoprefixer({
            browsers: [
                'last 2 versions',
                '> 1%'
            ]
        }))
        .pipe(gulp.dest('dist/css'));
});

//HTML (no necesita variable previa, ya viene x defecto con gulp)
gulp.task('html', function() {
    return gulp.src('src/*.html')
        .pipe(gulp.dest('dist'));
});

//IMAGEMIN
gulp.task('imgmin', function() {
    return gulp.src('src/img/*')
        .pipe(imagemin({
            progressive: true,
            svgoPlugins: [{removeViewBox: false}],
            use: [pngquant()]
        }))
        .pipe(gulp.dest('dist/img'));

});


//tarea default, le indicamos que antes de realizarla
//ejecute las tareas puestas en la array (second param)
gulp.task('default', function() {
    //BROWSER-SYNC
    browserSync.init({
        server: { baseDir: "./dist" },
        //archivos que queremos que esté mirando
        files: ['./dist/css/style.css']
    });
    //WATCH: ejecuta la tarea cuando hay un cambio en un archivo, el que le indiquemos
    //las tareas watch interesa hacerlas siempre sobre las extensiones
    gulp.watch('./src/scss/**/*.scss', ['css']);
    //nuevo watch que mira a los html
    gulp.watch('./src/*.html', ['html']);
    gulp.watch('./dist/*.html').on('change', browserSync.reload);
})

//tarea default, le indicamos que antes de realizarla
//ejecute las tareas puestas en la array (second param)
/*gulp.task('default',['css'], function(){
	
});*/
´´´
## 3.4 Workflow con gulp

* Para iniciar una tarea en gulp: `gulp nombre-de-latarea´
* Ir a un directorio: `cd y nombre del directorio`
* Paso atrás: `cd ..`
* Ver items de directorio actual: `ls -l`
* Crear nuevo directorio `mkdir nombre`
* Crear un archivo: `touch nombredelarchivo.extensión`
* Con las flechas arriba y abajo vemos el historial de las teclas que hemos ido usando
* Abrir programa o directorio: `open .`