---
title:  "Express en Node"
categories: backend
tags: Node Express
toc: true
toc_sticky: true
sidebar:
    nav: docs
---

## 1. Introduccion

> En el articulo [Request HTTP en Node][request-en-node] vimos que el uso de **http** nativo de Node par crear un server es mas complejo por la cantidad de cosas que hay que gestionar. Ahora usaremos Express y veremos que nos aporta  


### 1.2  Instalacion de Express

Antes que nada para poder usar express debemos instalarlo como dependecia; Para esto en nuestra consola agregamos el siguiente comando:
```js
$ npm i -E express
```
### 1.3 importar la funcion 'express' 

En un archivo.js llamaremos a la funcion. Esta funcion lo que hace es sustituir el createServer de http que usamos de forma nativa con Node
```js
import express from 'express';
```
### 1.4 Usar 'express'

Podemos crear una constante en este caso la llamare serverExpress para usar la funcion 

```js
import express from 'express';

cosnt serverExpress = express()
```
### 1.5 Agregar el listen()
Esta funcion tambien tiene un listen que recibe como primer parametro el puerto que va a usar para escuchar y como segundo parametro una funcion callback que se va ejecutar cuando este escuchando. Definimos una constante PORT para almacenar el puerto en ese caso usare el puerto 3000 de mi maquina local 

```js
import express from 'express';

const PORT = 3000
cosnt serverExpress = express()

serverExpress.listen(PORT, () => {
    console.log(`Servidor creado en el puerto ${PORT}`)
})
```
### 1.6 Endpoints

Express contiene unos metodos que nos ayudan a diferenciar en funcion del metodo solicitado (GET. PUT. POST etc..)
a estas funciones les podemos pasar un **PATH/Ruta** que sera la url y luego como segundo parametro un callback que recibira un reques y un response   

```js
import express from 'express';

const PORT = 3000
cosnt serverExpress = express()

serverExpress.get('/mi-cuenta', (req, res) => {
    res.send('Tu Cuenta')
})

serverExpress.listen(PORT, () => {
    console.log(`Servidor creado en el puerto ${PORT}`)
})
```
Con la linea **serverExpress.get()** lo que haremos es filtrar para que caso **(la url)** se va ejecutar la función que se pasa como segundo parametro. Es decir cuando un cliente con una url con con el metodo GET a la ruta '/mi-cuenta' se ejecutara la función callback. De esta manera ya podremos empezar a filtrar la funcionalidad que queremos en nuesto PATH

Aveces la rutas no son exactas podemos enviar un parametro que se quiere obtener por ejemplo un identificador de la cuenta, 
para esto tenemos la sintaxis de dos puntos **:** lo que decimos es toda cuenta que este despues de **:** sera el id de la cuenta. Usamos el **req.params** para definir todos lo parametros que queremos en ese **PATH** tambien podemos usar query.

```js
import express from 'express';

const PORT = 3000
cosnt serverExpress = express()

serverExpress.get('/mi-cuenta/:idcuenta/:otroid', (req, res) => {
    console.log(req.params.idcuenta)
    res.send('Tu Cuenta')
})

serverExpress.listen(PORT, () => {
    console.log(`Servidor creado en el puerto ${PORT}`)
})
```
## 1.7 Headers 
Para los headers podemos usar la propiedad **req.headers**. se puede obtener como un objeto o tambien el **re.get('accept')** con una propiedad a ver si exixte
```js
import express from 'express';

const PORT = 3000
cosnt serverExpress = express()

serverExpress.get('/mi-cuenta/:idcuenta/:otroid', (req, res) => {
    console.log(req.headers);
    console.log(req.get('accept'));
    console.log(req.params.idcuenta);
    res.send('Tu Cuenta')
})

serverExpress.listen(PORT, () => {
    console.log(`Servidor creado en el puerto ${PORT}`)
})
```
## 1.8 Response
El response ya lo tenenemos, tenemos el **status()** el **send()** y algunos otros metodos mas, podriamos devolver un objeto un string 

```js
import express from 'express';

const PORT = 3000
cosnt serverExpress = express()

serverExpress.get('/mi-cuenta/:idcuenta/:otroid', (req, res) => {
    console.log(req.headers);
    console.log(req.get('accept'));
    console.log(req.params.idcuenta);
    res.status(401)
    res.send('Tu Cuenta')
})

serverExpress.listen(PORT, () => {
    console.log(`Servidor creado en el puerto ${PORT}`)
})
```

## 1.9 Parsear el Body

En http nativo de Node teniamos que hacer un stream de datos acumulandolos; Con express usaremos una funcion parser 
que transforma la data que nos llega en un tipo de dato Json, Xml, Form-encore, Graphql etc...

### 1.9.1 Middleware

 Un Middleware es una funcion que se ejcuta para multiples endpoints, se puede definir funciones que sean comunes a un grupo de endpoints por ejemplo que permita admitir un cierto formato. Express trae una serie de Middlewares, que se van encargar de ejecutar una funcion de forma previa a lo que seria la logica del endpoint.   
```js

import express from 'express';

const PORT = 3000;
cosnt serverExpress = express();

// funcionan para todos los PATH 
serverExpresss.use(express.json()); //Middleware para admitir formato json
serverExpresss.use(express.text()); //Middleware para admitir formato texto

serverExpress.post('/mi-cuenta/:idcuenta/:otroid', (req, res) => {
    console.log(req.body);
   
    res.send('Tu Cuenta');
})

serverExpress.put('/producto/:idproducto', (req, res) => {
    console.log(req.body);
   
    res.send('Tu Producto');
})

serverExpress.listen(PORT, () => {
    console.log(`Servidor creado en el puerto ${PORT}`);
})
```







[request-en-node]: https://idevlin.github.io/backend/request-http-en-node/ 