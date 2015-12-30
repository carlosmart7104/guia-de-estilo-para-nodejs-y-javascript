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
* [Las llaves de apertura van en la misma línea](#Las-llaves-de-apertura-van-en-la-misma-línea)
* [Declarar las variables con la sentencia var](#Declarar-las-variables-con-la-sentencia-var)

### Convenciones de nomenclatura
* [Usar lowerCamelCase para las variables, propiedades y nombres de funciones] (#Usar-lowerCamelCase para las variables-propiedades-y-nombres-de-

funciones)
* [Usar UpperCamelCase en nombres de clase] (#usar-uppercamelcase-en-nombres-de-clase)
* [Usar MAYÚSCULAS para Constantes] (#usar-mayusculas-para-constantes)

### Variables
* [Creación de Objetos/ Arrays] (#creacion-de-objetos--arrays)

### Condicionales
* [Uso del operador ===] ( uso-del-operador-)
* [El uso de varias líneas del operador ternario] (#el-uso-de-varias-lineas-del-operador-ternario)
* [Uso de condiciones descriptivas] (#uso-de-condiciones-descriptivas)

### Funciones
* [Escribe funciones pequeñas] (#escribe-funciones-pequeñas)
* [Retorna a funciones anteriores] (#Retorna-a-funciones-anteriores)
* [Nombre sus closures] (#nombre-sus-closures)
* [No usar closures anidados] (#no-usar-closures-anidados)
* [Concatenar Métodos] (#concatenar-metodos)

### Comentarios
* [Usar barras para comentarios] (#usar-barras-para-comentarios)
