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
 
## Sintaxis

```js

const formData = new FormData([formElement])

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

## 3. Servidor que recibira la peticion del formulario

```js
import express, { json, text } from "express";
import multer from "multer";
import cors from 'cors'
import fs from 'fs'
const upload = multer({dest: 'images/', limits: {fieldNameSize: 10000000} })


const app = express()
app.use(json())
app.use(text())
app.use(cors())
app.use(express.urlencoded({ extended: true }));

app.post('/',upload.single('image'),(req, res)=> {
  const img = fs.readFileSync(req.file.path)
 console.log(img )
  res.send('recibido').status(200)
})

app.listen(3001, ()=> {
    console.log( 'app en el puerto 3001')
})
```
 

