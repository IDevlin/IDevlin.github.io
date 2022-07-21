---
title:  "Request HTTP en Node"
categories: Node 
tags: backend 
toc: true
toc_sticky: true
sidebar:
    nav: docs
---

## 1. Analisis  

> Ya vimos en él [anterior post][como-crear-servidor-en-node] como crear una única función capaz de responder a cualquier solicitud HTTP, pero incapaz de distinguir que necesita el usuario, para poder hacer esa distinción necesitamos datos que nos del cliente como la ruta, las cabeceras, el verbo, el body, esa información nos permite decidir que hacer en el servidor y como responder a esas solicitudes. Además veremos la complejidad y porque es útil usar una infraestructura como **Express** para facilitar el desarrollo


### 1.1 ¿Qué necesitamos?


Hemos dicho que una solicitud http tiene varias cosas: un verbo/método para indicar que quiere hacer el cliente (PUT, POST etc…)


+ Nos falta el verbo

+ Nos falta el path/ruta para identificar el recurso

+ Nos falta las cabeceras 

+ En ciertos casos el body/payload


```js

console.clear()

import {createServer} from 'http';

let objeto = {name : 'valor',

age: 32}

const httpserver = createServer( ( req, res) = {

    //verbo o método para indicar que hacer el cliente 

    console.log(req.method)
    //el path o la ruta para identificar el recurso 

    console.log(req.url)
    //las cabeceras

    console.log(req.headers)
    //el body o payloads

    console.log('Petición recibida')

    res.end(JSON.stringify(objeto))

});


httpserver.listen(3000)

```

Como vemos en el código anterior con **console.log(req.)** si hacemos una petición podremos ver en la consola las partes que componen el protocolo HTTP; El verbo, **GET PUT..** la parte que pertenece al **Path/Ruta/url** y los headers 



## 1.2 Obteniendo el body (STREAM)


Aquí se complica un poco mas, el server se ejecuta por eventos así que la función del body se ejecuta cuando recibe un evento pero por cuestiones de rendimiento el body no lo trae por completo cuando se ejecuta el verbo, el path y el header porque el body como puede ser un archivo pequeño de 30 MB puede ser uno de 500MB entonces el body lo debemos componer, lo que ofrece Node en este caso es un **STREAM** es como una tubería que transmite los datos y tienes que ir acumulando estos datos que van a venir por ese stream hasta formar el body por medio de un evento


```js

console.clear()

import {createServer} from 'http';

const httpserver = createServer( ( req, res) = {

    //verbo o método para indicar que hacer el cliente 
    console.log(req.method)

    //el path o la ruta para identificar el recurso 
    console.log(req.url)

    //las cabeceras
    console.log(req.headers)

    //el body o payloads
    let data = '';

    let chunkIndex = 0;

   req.on('data', (chunk) = {

     {data += chunk}

     chunkIndex ++;

     console.log(chunkIndex)

   })

   req.on('end', ()= {

    console.log(data)

    res.end('RECIBIDO')

   })

});

httpserver.listen(3000)

```

Cuando ejecutamos el req.method, el req.url y el req.headers aun no tenemos el body, solo se tiene una intefaz con la cual se va obteniendo trozos del body para ir conformándolo. El req tiene un sistema de eventos **req.on()** podemos indicar al evento al que queremos reaccionar en este caso cuando se reciba data atrevés del **STREAM** vamos a conformar ese body, entonces se pasa como segundo parámetro una función que será el listener de ese evento 'data', en esta función recibiremos un **chunk** o fragmento que lo que hace esta interfaz es ir dividiendo el body en partes, esto permite liberar memoria porque cargar body uy grandes es un problema, entonces tomamos él data y lo concatenamos con el **chunk** se crea una variable **chunkIndex** y la aumentamos con ++ en cada ejecución para ver cuantas veces se ejecuta. Luego el **res.end()** debe ir condicional a que se obtenga todo él data así que para eso usamos el otro evento **req.on('end')** de esa manera cuando se acaba de ejecutar todas las veces necesarias y obtener toda la data y toda la información responde


Para probar esto podemos ir a [https://json-generator.com/] [json-generator] y con **thunder client** en la parte del body agregar un json de más de 100kb para ver en la consola cuantas veces se ejecuta la función que serian los fragmentos del body que pasan por el **STREAM** con esto entendemos el concepto de eventos, el stream de datos y la bondad de la librería.

![thunder-client](/assets/images/chunk-data.png)


[json-generator]: https://json-generator.com/
[como-crear-servidor-en-node]: https://idevlin.github.io/node/como-crear-un-servidor-en-node/