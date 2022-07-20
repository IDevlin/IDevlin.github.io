---
title:  "JavaScript: introducción"
categories: JavaScript 
tags: 30DiasDeJS 
toc: true
toc_sticky: true
sidebar:
    nav: docs
---

# Dia 1. Introducción

>Antes de empezar es necesario instalar y configurar algunas herramientas para visualizar y procesar el código de JavaScript para ejecutarlo en un navegador

## 1. Instalar visual studio code

![Instalacion visual studio](/assets/images/vs-code.png)

## 2. Instalar Node.js

![Instalar Node](/assets/images/node.png)

## 3. Metodo console.log()

+ Es una función que permite visualizar el resultado del código en la consola 

```html
<script> 
console.log('Hola Mundo');
</script>
```
+ Puede llevar múltiples argumentos
  + Acepta comillas simples(' '), comillas dobles(" "), comillas invertidas(``)

## 4. comentarios

Es una parte del código que no es código, cuando el programa se ejecuta el comentario se ignora, sirve para información de partes del código o para mensajes para otros desarrolladores

+ Comentario de una sola línea
```js
// Comentario de una sola linea.
```

+ Comentario multilínea
```js
/*
Este es un comentarios en varias lineas o
comentario multilinea
*/
```

## 5. Insertar JavaScript en una página web

### a) Dentro de una etiqueta HTML

```html
<body>
  <button onclick = "alert('Hola!')">Click<button>
</body>
  ```

### b) Dentro del documento HTML
  + Puede escribirse tanto en el body como en el head/**body**

```html
<script>
  console.log('Welcome!');
</script>
```

### c) Archivo externo de JS
  + ⚠️Normalmente va al **final** del código en el **body** por temas de carga y optimizacion
  
```html
<body>
  <script src = "introduction.js"></script>
</body>
```
+ Es recomedable ponerlo antes de la etiqueta(`</body>`)

### d) Múltiples archivos externos de Js
  + Se pueden agregar múltiples archivos externos de JavaScript

  ```html
<body>
  <script src = "introduction.js"></script>
  <script src = "main.js"></script>
</body>
```

## 5. Tipos de datos

### Datos Primitivos

En JavaScript debemos trabajar con valores y esos valores tienen un tipo específico de dato dependiendo de su propósito dentro del código

+ Number - para representar numeros (-,0,+) 
+ Strings - cualquier tipo de dato para representar cadenas de texto  ' ', " ", ``
+ Boolean - true / false
+ undefined 
    + cuando no existe un valor asignado
    + Si una función no retorna nada, retorna undefined
+ null - un valor vacio o nulo
+ Object - es una estructura que permite relacionar funciones y valores mediante Key y value (propiedad y valor)


## 6. Variables

Podríamos imaginar las variables como vinculaciones o tentáculos; una sola declaración puede definir múltiples vinculaciones

### Como declarar una variable

Para declarar una variable podemos usar `var`, `let`, y `const`.
`var` es la forma en la que se declaraban las variables en JavaScript previo al 2015, La palabra `const` representa una constante. Se recomienda usar `let` en lugar de `var` por temas de scoope o entornos de ejecucion

### Reglas para nombrar variables


El nombre de la variable...
+ no puede empezar con números
+ no acepta caracteres especiales exepto $ y _
+ es recomendable seguir la convencion camelCase
+ no acepta espacios
+ deberias usar nombres descriptivos
```js
let nuevaVariable = value;
```

