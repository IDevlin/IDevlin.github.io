---
title:  "Datos de un formulario con new FormData"
categories: frontend, backend 
tags: JavaScript
toc: true
toc_sticky: true
sidebar:
    nav: docs
---

## 1. Introducción

En este articulo trata del manejo de formularios HTML y como los objetos FormData son de mucha ayuda para manipularlos y enviarlos atravez del protocolo http
 
New FormData es una clase de JavaScript que se utiliza para obtener y enviar datos de formularios de HTML. Con FormData, puedes recopilar y enviar datos de formularios de manera sencilla y eficiente, incluso si el formulario incluye archivos subidos.

Para empezar a usar FormData, primero debes obtener una instancia de FormData a partir de un formulario de HTML. Por ejemplo:

```js
const form = document.querySelector('form');
const formData = new FormData(form);
```
## 2. Un formulario con file en en front
 Empecemos con un elmento form, lo marcamos con un id para selecionarlo
 Creamos una funcion para enviar los datos por medio de un addEventListener; esta funcion recibira como parametro un evento de tipo submit le pasamos como parametro del objeto formData el evento con su target y este lo enviamos en en body del la funcion fetch
 Creamos una funcion para enviar los datos por medio de un addEventListener
```js
<form id="form">
  <input type="text" name="name" >
  <input type="text" name="surname" >
  <input name="image" type="file" id="file">
  <input type="submit">
</form>

const form = document.getElemenById('form');

form.addEventListener('submit', send);

const send = (e) => {
 e.preventDefault()
 const formData = new FormData(e.target)
 fetch('http://localhost:3001/',{
    method: 'POST',
    body: formData
 })
};

```

Una vez que tienes una instancia de FormData, puedes usarla para obtener los datos del formulario de la siguiente manera:
```js
const nombre = formData.get('nombre');
const apellido = formData.get('apellido');
const edad = formData.get('edad');
```

En este ejemplo, estamos obteniendo los datos del campo 'nombre', 'apellido' y 'edad' del formulario. FormData también puede ser utilizado para obtener archivos subidos a través de campos de archivo de formulario:
```js
const archivo = formData.get('archivo');
```
Una vez que has obtenido los datos del formulario, puedes utilizarlos como desees en tu aplicación. Por ejemplo, puedes enviarlos a un servidor mediante una solicitud HTTP utilizando una librería como Axios:

```js
axios.post('/enviar', formData).then(response => {
  console.log(response);
});
```

FormData también puede ser utilizado para agregar y eliminar datos del formulario dinámicamente. Por ejemplo, si deseas agregar un nuevo campo al formulario, puedes hacerlo de la siguiente manera:

```js
formData.append('nuevoCampo', 'valor');
```

Para eliminar un campo del formulario, puedes utilizar el método delete:

```js
formData.delete('nombre');
```

En resumen, FormData es una clase muy útil para obtener y enviar datos de formularios de HTML. Con su facilidad de uso y capacidad para manejar tanto datos como archivos subidos, es una herramienta esencial para cualquier desarrollador web.

 

