# Javascript y jQuery

#### Recopilatorio de funciones en js y jQuery
Este recopilatorio es más genérico que la sección de js en el documento MD "Comand-list". Pretende recopilar combinaciones de funciones.

## Index
1. Sustitución de clases
2. Smooth Scrolling
3. Acordeón (mostrar +)
4. Animaciones al hacer clic

# 1.Sustitución de clases
Hay dos formas de hacerlo, con toggle o con condicionales. La más fácil es con toggle.

## 1.1.Con toggle

### 1.1.1. Creamos 2 clases: la primera para estilar el botón, la segunda para añadir el texto al botón y la tercera para hacer el cambio.

```
.class1 {
    margin: 0px 0px 80px;
    padding: 10px 40px;
}

.class2 {
    background-color: greenyellow;
}
```
2. Añadimos un id al botón `id="changestyle"` en el HTML
3. En la hoja js añadimos este código:

```
$(document).on("ready", main);

function main(){
    $("#changestyle").on("click", cambiarTexto);
}

function cambiarTexto(){
    $(this).toggleClass("class2");
}

```

## 1.2.Sustitución de clases con condicionales

1. Creamos 2 clases: la primera para estilar el botón, la segunda para añadir el texto al botón y la tercera para hacer el cambio.

```
.class1 {
    margin: 0px 0px 80px;
    padding: 10px 40px;
}

.class2 {
    background-color: greenyellow;
}
```
2. Añadimos un id al botón `id="changestyle"` en el HTML
3. En la hoja js añadimos este código:

```
$(document).on("ready", main);

function main(){
    $("#changestyle").on("click", cambiarTexto);
    }

function cambiarTexto(){
    if($(this).hasClass("class2")){
        $(this).removeClass("class2");
    }else{
        $(this).addClass("class2")
    }
}

```
# 2.Smooth scrolling

1. Insertar antes de `</body>` del html: 
`<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.0/jquery.min.js"></script>`
2. Poner debajo el link de la hoja js: `<script src="js/nombre.js"></script>`
3. En la hoja js poner:

```$(document).ready(function(){
	$('a[href^="#"]').on('click',function (e) {
	    e.preventDefault();
	    var target = this.hash;
	    var $target = $(target);
	    $('html, body').stop().animate({
	        'scrollTop': $target.offset().top
	    }, 900, 'swing', function () {
	        window.location.hash = target;
	    });
	});
});
```

# 3.Acordeón(mostrar +)

1. Poner esto en la hoja js:

```
$('.toggle').click(function() {
    if ($(this).siblings().is(':visible')) {
        $(this).siblings().slideUp();
        $(this).siblings().find('.inner:visible').slideUp();
    } else {
        $(this).parent().parent().find('inner:visible').slideUp();
        $(this).siblings().slideToggle();
    };
});
```

2. Necesitamos lincar el jquery.js ```<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.0/jquery.min.js"></script>``` antes del `</body>` y del link de nuestro .js
3. Esto debe ir en nuestro style.css:

```
ul .inner {
  overflow: hidden;
  display: none;
}
ul .inner.show {
  display: block;
}
ul li a.toggle {
  width: 100%;
  display: block;
  transition: background .3s ease;
```
4. La estructura del HTML debe ser así:

```
<ul class="accordion">
        <ul class="inner" id="container">
            <a href="#p1"><li class="accordion-li">Opción1</li></a>
            <a href="#p2"><li class="accordion-li">Opción2</li></a>
            <a href="#p3"><li class="accordion-li">Opción3</li></a>
        </ul>
```

4. Crear el botón "ver más"

4.1. Creamos 3 clases: la primera para estilar el botón, la segunda para añadir el texto al botón y la tercera para hacer el cambio.

```
.port-btn-seemore {
    margin: 0px 0px 80px;
    padding: 10px 40px;
}

.port-btn-seemore:before {
    content: "Ver más";
}

.port-btn-seeless:before {
    content: "Ver menos";
    background-color: greenyellow;
}
```
4.2. Añadimos un id al botón `id="seemore"` en el HTML
4.3. En la hoja js añadimos este código

```
$(document).on("ready", main);

function main(){
    $("#seemore").on("click", cambiarTexto);
}

function cambiarTexto(){
    $(this).toggleClass("port-btn-seeless");
}

```

## 5.4.Animaciones al hacer click

1. Hay que hacer dos clases: una con los estilos y otra con la animación
2. También hacemos dos id: uno con un nombre y al otro le añadimos un 2. Esto lo hacemos para poder aplicar la animación a más de un elemento.
3. Colocamos en el html, tanto la clase con los estilos, como el id1 en unos y el id2 en otros.
4. Definimos en el estilo de la animación cómo queremos que sea.
5. Las animaciones están en la carpeta de `01 Resourses`, en el archivo `animate.css`


```
$(document).on("ready", first);

function first(){
    $("#id1, #id2").on("click", second);
}

function second(){
    $(this).toggleClass("animationclass");
}
```