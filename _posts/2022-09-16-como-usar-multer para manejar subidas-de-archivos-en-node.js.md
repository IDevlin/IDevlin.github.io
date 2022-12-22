---
title:  "Cómo usar Multer para manejar subidas de archivos en Node.js"
categories: backend 
tags: JavaScript
toc: true
toc_sticky: true
sidebar:
    nav: docs
---

## 1. Que es Multer

Multer es una biblioteca de Node.js que se utiliza para manejar las solicitudes HTTP que incluyen archivos, como las subidas de archivos. Con Multer, puedes procesar y almacenar fácilmente los archivos subidos en tu aplicación Node.js.

Para empezar a usar Multer, primero debes instalarlo mediante npm:

```js

npm install multer

```
Una vez instalado, puedes usar Multer en tu aplicación de la siguiente manera:

```js
const multer = require('multer');

// configurar multer
const storage = multer.diskStorage({
  destination: function (req, file, cb) {
    cb(null, './public/uploads/');
  },
  filename: function (req, file, cb) {
    cb(null, file.originalname);
  }
});

const upload = multer({ storage: storage });

// usar multer en tu ruta de subida de archivos
app.post('/upload', upload.single('archivo'), (req, res) => {
  // procesar el archivo subido
});
```
En este ejemplo, estamos configurando Multer para que almacene los archivos subidos en la carpeta './public/uploads/' en nuestro servidor. También estamos estableciendo el nombre del archivo subido como el nombre original del archivo.

Luego, estamos usando Multer en nuestra ruta de subida de archivos mediante la función upload.single(). Esta función toma el nombre del campo de archivo en el formulario de subida de archivos (en este caso, 'archivo') y procesa el archivo subido. Una vez que el archivo ha sido procesado, puedes acceder a él a través de la propiedad req.file.

También puedes usar Multer para procesar varios archivos a la vez utilizando la función upload.array() en lugar de upload.single(). Esto es útil si tienes un formulario de subida de archivos con varios campos de archivo.

Por ejemplo:

```js
app.post('/upload', upload.array('archivos', 12), (req, res) => {
  // procesar los archivos subidos
});
```
Además de procesar y almacenar archivos subidos, Multer también proporciona varias funciones útiles para validar los archivos subidos. Por ejemplo, puedes establecer restricciones de tamaño de archivo, tipo de archivo y nombre de archivo mediante el uso de filtros de Multer. Esto te permite asegurar que solo se suban archivos válidos y que cumplan con las especificaciones de tu aplicación.

Por ejemplo:

```js
const fileFilter = (req, file, cb) => {
  if (file.mimetype === 'image/jpeg' || file.mimetype === 'image/png') {
    cb(null, true);
  } else {
    cb(new Error('Solo se admiten archivos JPEG y PNG'), false);
  }
};

const upload = multer({
  storage: storage,
  fileFilter: fileFilter,
  limits: {
    fileSize: 1024 * 1024 * 5 // solo se admiten archivos de hasta 5 MB
  }
});
```

En este ejemplo, estamos utilizando un filtro de Multer para permitir solo archivos JPEG y PNG y estableciendo un límite de tamaño de archivo de 5 MB. Si un archivo subido no cumple con estas restricciones, Multer devolverá un error y no procesará el archivo.

En resumen, Multer es una herramienta muy útil para manejar las subidas de archivos en aplicaciones Node.js. Con su facilidad de uso y sus diversas opciones de configuración, puedes procesar y almacenar archivos subidos de manera sencilla y segura en tu aplicación.
 

