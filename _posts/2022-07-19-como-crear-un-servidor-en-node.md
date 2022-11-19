---
title:  "Crear Servidor en Node"
categories: backend 
tags: Node
toc: true
toc_sticky: true
sidebar:
    nav: docs
---

## 1. Introducción


 Al entrar a una página web por medio de un navegador lo que sucede es una solicitud a otro equipo o computadora en internet que a su vez está devolviendo una respuesta; esa respuesta es la página web que vemos.



Un servidor web recibe solicitudes [http][http] de un usuario que usa un navegador y el servidor devuelve respuestas en formato [JSON][json], HTML etc. desde una [APi][api].

Para que un servidor web devuelva una respuesta se requiere mucho código, este código está dividido en frontend y backend; front es la parte visual del contenido como se presentan los datos y el back es la parte en como estos datos se intercambian.



Node permite usar JavaScript para escribir código backend de servidor 



### En que se basa la comunicación

Establecer un lenguaje y un medio común entre las diferentes máquinas.

Cuando hablamos en establecer comunicación entre sistemas separados se dispone de una guía o estándar que establece una serie de reglas y responsabilidades para llevar a cabo esta comunicación, es lo que se conoce como modelos. [estándar de intercomunicación de sistemas (OSI)][modelo-OSI] diferentes máquinas conectadas a una red en común.



#### URL 



Para comunicarnos utilizamos una cadena de texto (url) como identificador del host y del recurso 



![partes url](/assets/images/Partes-URL-o-URI.png)



## 2. Protocolo HTTP 



Es un estándar que nos va a permitir recibir y enviar mensajes de otras máquinas, se basa en un sistema de petición respuesta, el cliente solicita algo y el servidor es el que responde. La máquina también puede tomar rol de cliente si esta es la que hace la petición a otros servidores. Contiene ciertas funcionalidades para ajustar el funcionamiento de capas interiores de la comunicación.

  Solicitud HTTP 

 

![Protocolo HTTP](/assets/images/protocolo-http.png)



+ **Línea inicial del mensaje o request line**

  

  Identifica el verbo permite definir que tipo de acción queremos realizar sobre la ruta solicitada en este caso GET



+ **Cabecera o headers**



  Tienen formato de objeto key value define el host y el método de autenticación



+ **Cuerpo / body**



  Como este caso es una GET una solicitud no devuelve nada con otros verbos si podremos introducir un tipo de información 



 Respuesta HTTP



El servidor procesa la solicitud y emite una respuesta; similar a la solicitud, pero con algunas diferencias en la primera línea y en las cabeceras 



+ **Status line**



  Define el código de respuesta que indica si su petición se ha podido satisfacer o se produjo un error



+ **Cabecera o headers**



  Ofrecen información de utilidad para el navegador ejemplo el tipo de dato



+ **Cuerpo / body / payload**



  Con el tipo de contenido que se solicitó, en este caso con información, ya que si retornamos datos como respuesta



  ## 3. HTTP en Node



  Node nos da herramientas para poder comunicarnos con el Sistema operativo y en red tendremos acceso a librerías para facilitar esto,

  la idea es montar un servidor que se comunique mediante HTTP.

  Node dispone de librerías nativas o propias como 



  + Nativo - http

  + Terceros - express, fastify, hapy, koa...  





### Paso 1. Instalaciones 



  + Previamente tener instalado Node e iniciar la consola en VS code con ctrl + ñ

  + Inicializar un package json dentro de la carpeta con el comando npm init -- y 

  ```js

$ npm init --y

```

 Esto nos creará un archivo json dentro de nuestro proyecto con cierta información


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

   + Si desea trabajar con módulos (opcional también puede utilizar **require()** ) agregar en el archivo package json la siguiente línea



   ```js

$ "type": "module"

```

   + Para ejecutar nodemon puedes agregar en la propiedad **"scripts"** de json una palabra clave para llamar la ejecución y un valor con la palabra nodemon seguido del archivo .js donde vas a crear el servidor ejemplo:



   ```js

    "scripts":

        "dev": "nodemon index.js"

   ```

   Para ejecutarlo solo escribes en la consola: 

   ```js

    $ npm run dev

   ```

### Paso 2. Creando el servidor 



En este punto vamos a utilizar la librerías nativa de http usando él module. Dentro de un archivo .js;

esto nos devolverá una instancia de tipo servidor



```js

    import {createServer} from 'http';

createServer()

   ```



CreateServer es una función que se ha importado de node que como su nombre lo indica crea un servidor no obstante este servidor necesita otra función para ser escuchado en este caso usaremos otra función llamada **listen()** que debe recibir como primer parámetro el puerto por el que va a escuchar al servidor



```js

    import {createServer} from 'http';

 const httpServer = createServer()

   httpServer.listen(3000)

   ```

Hasta este momento tenemos un servidor y un listener, pero estamos hablando de un protocolo de petición y respuesta el server debe tener una función que maneje ambas una **require** y una **respond**



```js

    import {createServer} from 'http';

    let objeto = { firtsName : 'name',

lastName: 'lastname'}



 const httpServer = createServer((req, res) = {

     console.log(JSON.stringify(objeto))

     res.end()

 })

   httpServer.listen(3000)

   ```



## 4. Peticiones con Thunder client



Una de las opciones para probar nuestras solicitudes HTTP es usar una extensión de visual studio llamada thunder client



Como vemos si escribimos en el navegador http://localhost:3000 obtendremos como respuesta un string que representa un objeto de JavaScript



![thunder client ](/assets/images/thunder-client.png)



## 5. Conclusiones

hasta el momento cubrimos lo básico de montar un servidor con las funciones nativas de Node, pero ahora tenemos más problemas, no sabemos la ruta tampoco el método, para todas las rutas nos va a devolver lo mismo, solo tenemos una única función para todos los verbos (GET, POS, DELETE etc…) y todos los métodos; ahora lo que necesitamos es filtrar esta solicitud; vemos la complejidad que realmente tiene todo esto y porque existen librerías de terceros como express para facilitar el desarrollo en el próximo post [Request HTTP en node][request-en-node]




[modelo-OSI]: https://www.guru99.com/images/1/092119_0729_LayersofOSI1.png
[json]:     https://#/
[http]: https://#
[api]: https://#
[request-en-node]: https://idevlin.github.io/backend/request-http-en-node/



