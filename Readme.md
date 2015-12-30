# Guía de estilo para Node.js

Esta es una guía para escribir código Node.js coherente y estéticamente agradable.
Se inspira en lo que es popular dentro de la comunidad, y algunas
opiniones personales.

Hay una .jshintrc que hace cumplir estas normas tan estrechamente como sea posible. 
Puedes o bien utilizar ese y ajustarlo o utilizar [este script] (https://gist.github.com/kentcdodds/11293570) para hacer tu propia versión.

Esta guía fue creada por [Félix Geisendörfer] (http://felixge.de/) y está
licenciada bajo la licencia [CC BY-SA 3.0] (http://creativecommons.org/licenses/by-sa/3.0/). 
Se le anima a descargar este repositorio y hacer los ajustes necesarios de acuerdo a sus preferencias.

! [Licencia Creative Commons] (http://i.creativecommons.org/l/by-sa/3.0/88x31.png)

## Tabla de contenido

### Formateo
* [2 Espacios para la identación](#2-espacios-para-la-indentación)
* [Nuevas lineas](#nuevas-lineas)
* [No dejar espacios en blanco](#no-dejar-espacios-en-blanco)
* [Use punto y coma](#use-punto-y-coma)
* [80 caracteres por línea](#80-caracteres-por-línea)
* [Usar comillas simples](#usar-comillas-simples)
* [Las llaves de apertura van en la misma línea] (#las-llaves-de-apertura-van-en-la-misma-línea)
* [Declarar las variables con la sentencia var] (#declarar-las-variables-con-la-sentencia-var)

### Convenciones de nomenclatura
* [Usar lowerCamelCase para las variables, propiedades y nombres de funciones] (#ssar-lowercamelcase-para-las-variables-propiedades-y-nombres-de-funciones)
* [Usar UpperCamelCase en nombres de clase] (#usar-uppercamelcase-en-nombres-de-clase)
* [Usar MAYÚSCULAS para Constantes] (#usar-mayusculas-para-constantes)

### Variables
* [Creación de Objetos/ Arrays] (#creacion-de-objetos--arrays)

### Condicionales
* [Uso del operador ===] ( uso-del-operador-)
* [El uso de varias líneas del operador ternario] (#el-uso-de-varias-lineas-del-operador-ternario)
* [Uso de condiciones descriptivas] (#uso-de-condiciones-descriptivas)

### Funciones
* [Escriba funciones pequeñas] (#escriba-funciones-pequeñas)
* [Retorne a funciones anteriores] (#Retorne-a-funciones-anteriores)
* [Nombre sus closures] (#nombre-sus-closures)
* [No usar closures anidados] (#no-usar-closures-anidados)
* [Concatenar Métodos] (#concatenar-metodos)

### Comentarios
* [Usar barras para comentarios] (#usar-barras-para-comentarios)

### Miscelanea
* [Object.freeze, Object.preventExtensions, Object.seal, with, eval] (#objectfreeze-objectpreventextensions-objectseal-with-eval)
* [Requieres al inicio] (#requieres-al-inicio)
* [Getters y setters] (#getters-y-setters)
* [No extienda prototypes incorporados] (#no-extienda-prototypes-incorporados)

## Formateo

### 2 Espacios para la sangría

Utilice 2 espacios para indentar el código y un jure que nunca mezclará tabs y
espacios, es un tipo especial de infierno que le está esperando de algún modo.

### Saltos de línea

Los saltos de línea de estilo UNIX, use (`\ n`), y un carácter de nueva línea como el último carácter de un archivo. 
Los saltos de línea de estilo de Windows (`\ r \ n`) están prohibidos dentro de cualquier repositorio.

### Sin espacios en blanco al terminar

Al igual que se cepilla los dientes después de cada comida, limpie todo el conjunto de espacios en blanco en los archivos de JS antes de hacer un commit. De lo contrario el olor a podrido de la negligencia y el descuido finalmente le dejará sin colaboradores y / o compañeros de trabajo.

### Utilice punto y coma

Según [scientific research] [hnsemicolons], el uso de punto y coma es un valor fundamental de nuestra comunidad. 
Tenga en cuenta los puntos de [the opposition] [], pero sea un tradicionalista cuando se trata de abusar de los mecanismos de corrección de errores para
placeres sintácticos baratos.

the opposition]: http://blog.izs.me/post/2353458699/an-open-letter-to-javascript-leaders-regarding
[hnsemicolons]: http://news.ycombinator.com/item?id=1547647

### 80 caracteres por línea

Limíte sus líneas a 80 caracteres. Sí, las pantallas se han vuelto mucho más grandes en los últimos años, pero su cerebro no tiene la capacidad.
Utilice el espacio adicional para la pantalla dividida, su editor soporta eso, ¿verdad?

### Use comillas simples

Use comillas simples, a menos que usted esté escribiendo JSON.

*Correcto:*

`` `js
foo var = 'bar';
`` `

*Incorrecto:*

`` `js
foo var = "bar";
`` `
### Llaves de apertura van en la misma línea

Sus llaves de apertura van en la misma línea que el comunicado.

*Correcto:*

`` `js
if (true) {
  console.log ('Ganaste!');
}
`` `

*Incorrecto:*

`` `js
if (true)
{
  console.log ('Perdiste :C');
}
`` `

También, observe el uso de espacios en blanco antes y después de la declaración de estado.

### Declarar una variable por sentencia var

Declarar una variable por sentencia var, que hace que sea más fácil de volver a reordenar las líneas. 
Sin embargo, ignora la [Crockford] [crockfordconvention] cuando se trata de declarar variables más profundas dentro de una función, sólo hay que poner las declaraciones siempre que tenga sentido.

*Correcto:*

```js
var keys   = ['foo', 'bar'];var values = [23, 42];

var object = {};
while (keys.length) {
  var key = keys.pop();
  object[key] = values.pop();
}
```

*Incorrecto:*

```js
var keys = ['foo', 'bar'],
    values = [23, 42],
    object = {},
    key;

while (keys.length) {
  key = keys.pop();
  object[key] = values.pop();
}
```

[crockfordconvention]: http://javascript.crockford.com/code.html

### Convenciones de nomenclatura
