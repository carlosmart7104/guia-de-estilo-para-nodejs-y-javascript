# Guía de estilo para Node.js

Alerta!, incompleto. Este documento está siendo traducido ahora.

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
* [2 Espacios para la sangría](#2-espacios-para-la-sangría)
* [Saltos de línea](#saltos-de-línea)
* [No dejar espacios en blanco](#no-dejar-espacios-en-blanco)
* [Utilice punto y coma](#utilice-punto-y-coma)
* [80 caracteres por línea](#80-caracteres-por-línea)
* [Use comillas simples](#use-comillas-simples)
* [Las llaves de apertura van en la misma línea](#las-llaves-de-apertura-van-en-la-misma-línea)
* [Declare una variable por sentencia var](#declare-una-variable-por-sentencia-var)

### Convenciones de nomenclatura
* [Use lowerCamelCase para las variables, propiedades y nombres de funciones](#use-lowercamelcase-para-las-variables-propiedades-y-nombres-de-funciones)
* [Use UpperCamelCase para nombres de clase](#use-uppercamelcase-para-nombres-de-clase)
* [Use MAYÚSCULAS para las constantes](#use-mayúsculas-para-las-constantes)

### Variables
* [Creación de Objetos / Matrices](#creación-de-objetos--matrices)

### Condicionales
* [Utilice el operador ===](#utilice-el-operador-)
* [Utilice el operador ternario en multiples líneas](#utilice-el-operador-ternario-en-multiples-líneas)
* [Utilice condiciones descriptivas](#utilice-condiciones-descriptivas)

### Funciones
* [Escriba funciones pequeñas](#escriba-funciones-pequeñas)
* [Retorne rápidamente las funciones](#retorne-rápidamente-las-funciones)
* [Nombre sus closures](#nombre-sus-closures)
* [No use closures anidados](#no-use-closures-anidados)
* [Concatene los métodos claramente](#concatene-los-métodos-claramente)

### Comentarios
* [Use diagonales para los comentarios](#use-diagonales-para-los-comentarios)

### Miscelanea
* [Object.freeze, Object.preventExtensions, Object.seal, with, eval](#objectfreeze-objectpreventextensions-objectseal-with-eval)
* [Requieres al inicio](#requieres-al-principio)
* [Getters y setters](#getters-y-setters)
* [No extienda prototypes incorporados](#no-extienda-prototypes-ya-incorporados)

## Formateo

### 2 Espacios para la sangría

Utilice 2 espacios para indentar el código y un jure que nunca mezclará tabs y
espacios, es un tipo especial de infierno que le está esperando de algún modo.

### Saltos de línea

Los saltos de línea de estilo UNIX, use (`\ n`), y un carácter de nueva línea como el último carácter de un archivo. 
Los saltos de línea de estilo de Windows (`\ r \ n`) están prohibidos dentro de cualquier repositorio.

### No dejar espacios en blanco

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

```js
foo var = 'bar';
```

*Incorrecto:*

```js
foo var = "bar";
```
### Las llaves de apertura van en la misma línea

Sus llaves de apertura van en la misma línea que el comunicado.

*Correcto:*

```js
if (true) {
  console.log ('Ganaste!');
}
```

*Incorrecto:*

```js
if (true)
{
  console.log ('Perdiste :C');
}
```

También, observe el uso de espacios en blanco antes y después de la declaración de estado.

### Declare una variable por sentencia var

Declare una variable por sentencia var, hace que sea más fácil editar el orden de las líneas. 
Sin embargo, ignore la [Crockford] [crockfordconvention] cuando se trata de declarar variables más profundas dentro de una función, sólo hay que poner las declaraciones siempre que tenga sentido.

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

### Use lowerCamelCase para las variables, propiedades y nombres de funciones

Las variables, propiedades y nombres de funciones deben usar `lowerCamelCase`. 
Ellos también deben ser descriptivos. 
Las abreviaturas en variables de carácter individual y poco frecuente generalmente deben ser evitados.

*Correcto:*

```js
var adminUser = db.query('SELECT * FROM users ...');
```

*Incorrecto:*

```js
var admin_user = db.query('SELECT * FROM users ...');
```

### Use UpperCamelCase para nombres de clase

Los nombres de clase deben ser capitalizados usando `UpperCamelCase`.

*Correcto:*

```js
function BankAccount() {
}
```

*Incorrecto:*

```js
function bank_Account() {
}
```

## Use MAYÚSCULAS para las constantes

Las constantes deben ser declaradas como variables regulares o propiedades de clase estáticos, utilizando todas las letras mayúsculas.

*Correcto:*

```js
var SECOND = 1 * 1000;

function File() {
}
File.FULL_PERMISSIONS = 0777;
```

*Incorrecto:*

```js
const SECOND = 1 * 1000;

function File() {
}
File.fullPermissions = 0777;
```

[const]: https://developer.mozilla.org/en/JavaScript/Reference/Statements/const

## Variables

### Creación de Objetos / Matrices

Utilice coma al final y ponga declaraciones *breves* en una sola línea. Sólo entrecomille claves cuando el intérprete lo requiera:

*Correcto:*

```js
var a = ['hello', 'world'];
var b = {
  good: 'code',
  'is generally': 'pretty',
};
```

*Incorrecto:*

```js
var a = [
  'hello', 'world'
];
var b = {"good": 'code'
        , is generally: 'pretty'
        };
```

## Condicionales

### Utilice el operador ===

La programación no se trata de recordar [reglas estúpidas] [comparisonoperators]. Use el operador de igualdad triple, ya que funcionará como se espera.

*Correcto:*

```js
var a = 0;
if (a !== '') {
  console.log('winning');
}

```

*Incorrecto:*

```js
var a = 0;
if (a == '') {
  console.log('losing');
}
```

[comparisonoperators]: https://developer.mozilla.org/en/JavaScript/Reference/Operators/Comparison_Operators

### Utilice el operador ternario en multiples líneas

El operador ternario no debe utilizarse en una sola línea. 
Divídalo en varias líneas.

*Correcto:*

```js
var foo = (a === b)
  ? 1
  : 2;
```

*Incorrecto:*

```js
var foo = (a === b) ? 1 : 2;
```

### Utilice condiciones descriptivas

Cualquier condición no trivial debe ser asignada a una función o variable con un nombre que la describa:

*Correcto:*

```js
var isValidPassword = password.length >= 4 && /^(?=.*\d).{4,}$/.test(password);

if (isValidPassword) {
  console.log('winning');
}
```

*Incorrecto:*

```js
if (password.length >= 4 && /^(?=.*\d).{4,}$/.test(password)) {
  console.log('losing');
}
```

## Funciones

### Escriba funciones pequeñas

Mantenga sus funciones cortas. 
Una buena función cabe en una diapositiva que las personas en
la última fila de una sala grande pueden leer cómodamente. 
Aún contando con que ellos no tengan una visión perfecta y debe limitarse a aproximadamente 15 líneas de código por función.

### Retorne rápidamente las funciones

Para evitar profundidad de anidamiento de las declaraciones if, devuelva el valor de una función tan pronto como sea posible.

*Correcto:*

```js
function isPercentage(val) {
  if (val < 0) {
    return false;
  }

  if (val > 100) {
    return false;
  }

  return true;
}
```

*Incorrecto:*

```js
function isPercentage(val) {
  if (val >= 0) {
    if (val < 100) {
      return true;
    } else {
      return false;
    }
  } else {
    return false;
  }
}
```

O para este ejemplo particular, también puede estar bien para acortar las cosas aún mejor:

```js
function isPercentage(val) {
  var isInRange = (val >= 0 && val <= 100);
  return isInRange;
}
```

### Nombre sus closures

Siéntase libre de dar a sus closures un nombre. 
Esto demuestra que usted se preocupa por ellos, y producirá mejores seguimientos de stack, heap y esquemas de cpu.

*Correcto:*

```js
req.on('end', function onEnd() {
  console.log('winning');
});
```

*Incorrecto:*

```js
req.on('end', function() {
  console.log('losing');
});
```

### No use closures anidados

Utilice los closures, pero no los anide. 
De lo contrario, el código se convertirá en un desastre.

*Correcto:*

```js
setTimeout(function() {
  client.connect(afterConnect);
}, 1000);

function afterConnect() {
  console.log('winning');
}
```

*Incorrecto:*

```js
setTimeout(function() {
  client.connect(function() {
    console.log('losing');
  });
}, 1000);
```


### Concatene los métodos claramente

Si desea encadenar métodos se debe utilizar un método por línea.
También debe sangrar estos métodos lo que hace más fácil denotar que son parte de la misma cadena.

*Correcto:*

```js
User
  .findOne({ name: 'foo' })
  .populate('bar')
  .exec(function(err, user) {
    return true;
  });
````

*Incorrecto:*

```js
User
.findOne({ name: 'foo' })
.populate('bar')
.exec(function(err, user) {
  return true;
});

User.findOne({ name: 'foo' })
  .populate('bar')
  .exec(function(err, user) {
    return true;
  });

User.findOne({ name: 'foo' }).populate('bar')
.exec(function(err, user) {
  return true;
});

User.findOne({ name: 'foo' }).populate('bar')
  .exec(function(err, user) {
    return true;
  });
````

## Comentarios

### Use diagonales para los comentarios

Utilice diagonales tanto para una sola línea como para múltiples líneas de comentarios. 
Trate de escribir comentarios que expliquen los mecanismos de nivel superior o aclaren segmentos difíciles de su código. 
No use los comentarios para replantear las cosas triviales.

*Correcto:*

```js
// 'ID_SOMETHING=VALUE' -> ['ID_SOMETHING=VALUE', 'SOMETHING', 'VALUE']
var matches = item.match(/ID_([^\n]+)=([^\n]+)/));

// This function has a nasty side effect where a failure to increment a
// redis counter used for statistics will cause an exception. This needs
// to be fixed in a later iteration.
function loadUser(id, cb) {
  // ...
}

var isSessionValid = (session.expires < Date.now());
if (isSessionValid) {
  // ...
}
```

*Incorrecto:*

```js
// Execute a regex
var matches = item.match(/ID_([^\n]+)=([^\n]+)/);

// Usage: loadUser(5, function() { ... })
function loadUser(id, cb) {
  // ...
}

// Check if the session is valid
var isSessionValid = (session.expires < Date.now());
// If the session is valid
if (isSessionValid) {
  // ...
}
```

## Miscelanea

### Object.freeze, Object.preventExtensions, Object.seal, with, eval

Mierdas locas que es probable que nunca necesite. 
Manténgase alejado de ellas.

### Requieres al principio

Ponga siempre los requieres en la parte superior del archivo para ilustrar claramente sus dependencias. Además de dar una visión general de los demás en un vistazo rápido de las dependencias y posible impacto de la memoria, que permite determinar si necesitan un archivo package.json si optan por utilizar el archivo en otro lugar.

### Getters y setters (Captadores y definidores)

No utilice setters, causan más problemas para las personas que tratan de utilizar su software de los que pueden resolver.

Siéntase libre de utilizar getters que están libres de los [efectos secundarios] [efecto secundario], al igual que proporcionar una propiedad length para una colección de clases.

[efecto secundario]: http://en.wikipedia.org/wiki/Side_effect_(computer_science)

### No extienda prototypes ya incorporados

No extienda el prototype de objetos nativos de JavaScript. 
Tu yo del futuro estará por siempre agradecido.

*Correcto:*

```js
var a = [];
if (!a.length) {
  console.log('winning');
}
```

*Incorrecto:*

```js
Array.prototype.empty = function() {
  return !this.length;
}

var a = [];
if (a.empty()) {
  console.log('losing');
}
```
