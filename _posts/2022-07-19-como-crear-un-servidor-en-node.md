---
title:  "Crear Servidor en Node"
categories: Node 
tags: backend 
toc: true
toc_sticky: true
sidebar:
    nav: docs
---

## 1. Introducción

> Al entrar a una pagina web por medio de un navegador lo que sucede es una solicitud a otro equipo o computadora en internet que a su vez esta devolviendo una respuesta; esa respuesta es la pagina web que vemos.

Un servidor web recibe solicitudes [http][http] de un usuario que usa un navegador y el servidor devuelve respuestas en formato [JSON][json], HTML etc desde una [APi][api].
Para que un servidor web devuelva una respuesta se requiere mucho codigo, este codigo esta dividido en frontend y backend; front es la parte visual del contenido como se presentan los datos y el back es la parte en como estos datos se intercambian.

Node permite usar JavaScript para escribir codigo backend de servidor 

### En que se basa la comunicación
Establecer un lenguaje y un medio comun entre las diferentes maquinas.
Cuando hablamos en establecer comunicación entre sistemas separados se dispone de una guia o estandar que establece una serie de reglas y responsabilidades para llevar a cabo esta comunicacion, es lo que se conoce como modelos. [estandar de intercomunicación de sistemas (OSI)][modelo-OSI] diferentes maquinas conectadas a una red en comun.

#### URL 

Para comunicarnos utilizamos una cadena de texto (url) como identificador del host y del recurso 

![partes url](/assets/images/Partes-URL-o-URI.png)

## 2. Protocolo HTTP 

Es un estandar que nos va a permitir recibir y enviar mensajes de otras maquinas, se basa en un sistema de peticion respuesta, el cliente solicita algo y el servidor es el que responde. la maquina tambien puede tomar rol de cliente si esta es la que hace la peticion a otros servidores. Contiene ciertas funcionalidades para ajustar el funcionamiento de capas interiores de la comunicacion.
 > Solicitud HTTP 
 
![Protocolo HTTP](/assets/images/protocolo-http.png)

+ **Linea inicial del mensaje o request line**
  
  idetifica el verbo permite definir que tipo de accion queremos realizar sobre la ruta solicitada en este caso GET

+ **Cabecera o headers**

  tienen formato de objeto key value define el host y el metodo de autenticación

+ **Cuerpo / body**

  como este caso es una GET una solicitud no devulve nada con otros verbos si podremos introducir un tipo de información 

> Respuesta HTTP

El servidor procesa la solicitud y emite una respuesta; similar a la solicitud pero con algunas diferencias en la primera linea y en las cabeceras 

+ **Status line**

  Define el codigo de respuesta que indica si su petición se ha podido satisfacer o se produjo un error

+ **Cabecera o headers**

  Ofrecen información de utilidad para el navegador ejemplo el tipo de dato

+ **Cuerpo / body / payload**

  Con el tipo de cotenido que se solicito, en este caso con información ya que si retornamos datos como respuesta

  ## 3. HTTP en Node

  Node nos da herramientas para poder comunicarnos con el Sistema operativo y en red tendremos acceso a librerias para facilitar esto,
  la idea es montar un servidor que se comunique mediante HTTP.
  Node dispone de librerias nativas o propias como 

  + Nativo - http
  + Terceros - express, fastify, hapy, koa...  

  ### Paso 1: instalaciones y dependencias 

  + Previamente tener instalado Node e iniciar la consola en VS code con ctrl + ñ
  + Inicializar un package json dentro de la carpeta con el comando npm init -- y 

  ```js
$ npm init --y
```
 Esto nos creara un archivo json dentro de nuestro proyecto con cierta información

 ```js
{
  "name": "web-server",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "type": "module",
  "scripts": {
    "test": "echo \ "Error: no test specified\ && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
   
  }
}
```

   + instalar una dependencia llamada **nodemon** para facilitar el desarrollo y evitar estar ejecutando constantemente el archivo

   ```js
$ npm -i -E -D nodemon
```
   + Si desea trabajar con modulos (opcional tambien puede utilizar **require()** ) agregar en el archivo package json la siguente linea

   ```js
$ "type": "module"
```
   + Para ejecutar nodemon puedes agregar en la propiedad **"scripts"** de json una palabra clave para llamar la ejecucion y un valor con la palabra nodemon seguido del archivo .js donde vas a crear el servidor ejemplo:

   ```js
    "scripts":
        "dev": "nodemon index.js"
   ```
   Para ejecutarlo solo escribes en la consola: 

   ```js
    $ npm run dev
   ```
### Paso 2: 

En este punto vamos a utilizar la libreria nativa de http usando el module. dentro de un archivo .js;
esto nos devolvera una instancia de tipo servidor

```js
    import {createServer} from 'http';

createServer()
   ```

CreateServer es una funcion que se ha importado de node que como su nombre lo indica crea un servidor no obstante este servidor necesita otra funcion para ser escuchado en este caso usaremos otra funcion llamada **listen()** que debe recibir como primer parametro el puerto por el que va a escuchar al servidor

```js
    import {createServer} from 'http';

 const httpServer = createServer()

   httpServer.listen(3000)
   ```
Hasta este momento tenemos un servidor y un listener pero estamos hablando de un protocolo de peticion y respuesta el server debe tener una funcion que maneje ambas una **require** y una **respond**

```js
    import {createServer} from 'http';

    let objeto = { firtsName : 'name',
lastName: 'lastname'}

 const httpServer = createServer((req, res) => {
     console.log(JSON.stringify(objeto))

     res.end()
 })

   httpServer.listen(3000)
   ```
Como vemos si escribimos en el navegador http://localhost:3000 obtendremos como respuesta un string que representa un objeto de JavaScript












[modelo-OSI]: https://www.guru99.com/images/1/092119_0729_LayersofOSI1.png
[json]:     https://#/
[http]: https://#
[api]: https://#




