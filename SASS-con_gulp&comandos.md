# 1.SASS

## 1.1.Instalación de Ruby

1. En Windows hay que descargar [Ruby](http://rubyinstaller.org/), instalarlo y reiniciar el ordenador.
2. Escribir en la consola ``gem install sass``
3. Istalar Compass ``gem install compass`` que nos brinda código CSS común para nuestros proyectos.

## 1.2.Instalación de SASS en GULP

1. El `gulpfile.js´ debe llevar este código:
```
//tarea default, le indicamos que antes de realizarla
//ejecute las tareas puestas en la array (second param)
gulp.task('default', function() {
    //BROWSER-SYNC
    browserSync.init({
        server: { baseDir: "./dist" },
        //archivos que queremos que esté mirando
        files: ['./dist/css/main.css']
    });
    //WATCH: ejecuta la tarea cuando hay un cambio en un archivo, el que le indiquemos
    //las tareas watch interesa hacerlas siempre sobre las extensiones
    gulp.watch('./src/scss/**/*.scss', ['css']);
    //nuevo watch que mira a los html
    gulp.watch('./src/*.html', ['html']);
    gulp.watch('./dist/*.html').on('change', browserSync.reload);
})
```

2. E instalarlo en elentorno de trabajo: `npm install gulp-sass --save-dev´

## 1.3.Workflow e Imports

1. Generamos el archivo central: main.scss _Donde irán los imports_
2. Creamos los partial: `_nombre.scss`
3. En el main.scss pondremos los imports: `@import: 'nombredelpartial';`
4. Para hacer 1 watch: `sass --watch scss/nombredelarchivo.scss:dist/css/main.css` _Cada vez que guarde, _automáticamente gulp sobreescribirá el main.css con los cambios
5. Ejecutar variable `gulp default´ para iniciar el life edit junto al watch general
6. Podemos comprimir el código resultante: `--style compressed`

## 1.4.Variables

1. Generamos un partial para las variables
2. Creamos aquí las variables: `$color: #333333;`
3. Aplicamos nuestra variable: `$color`

## 1.5.Mixings

1. Creamos un partial para los mixings
2. Los ponemos así: `@mixin nombre {border: 1px;}`
3. Para aplicarlo usamos: `@include nombre`

_Podemos variar el mixing puntualmente_ `@include nombre (#666)`