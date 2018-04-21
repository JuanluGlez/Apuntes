# Javascript y jQuery

#### Recopilatorio de funciones en js y jQuery
Este recopilatorio es más genérico que la sección de js en el documento MD "Comand-list". Pretende recopilar combinaciones de funciones.

## Index

1. Sustitución de clases

# 1.Sustitución de clases

## 1.1.Con toggle

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