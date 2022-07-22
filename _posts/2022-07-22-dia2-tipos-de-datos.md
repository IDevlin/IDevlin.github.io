---
title:  "Dia 2: Tipos de datos en JavaScript"
categories: JavaScript
tags: 30DiasDeJS  
toc: true
toc_sticky: true
sidebar:
    nav: docs
---

## Tipos de datos

> Los tipos de datos se refieren a las caracteristicas del dato y se pueden dividir en dos 

1. Datos Primitivos 
Son datos que no pueden ser modificados pueden asignarse a una variable pero no son mutables

2. Datos No Primitivos

### Datos Primitivos 

1. Numeros 
2. Strings
3. Booleans
4. Null
5. Undefined 
6. Simbol

### Datos No Primitivos

1. Objects
2. Arrays

## Ejercicios 

### Nivel 1

 1. Declare una variable llamada challenge y asígnele un valor inicial '30 días de JavaScript'.
 ```js
 let challenge = '30 días de JavaScript'
 ```

2. Imprime la cadena en la consola del navegador usando console.log()
```js
console.log(challenge);
 ```
 
3. Imprime la longitud de la cadena en la consola del navegador usando console.log()
```js
console.log(challenge.longitud)
 ```
4. Cambie todos los caracteres de la cadena a letras mayúsculas usando el método toUpperCase()
```js
let uppercase = challenge.toLocaleUpperCase()
 ```

5. Cambia todos los caracteres de la cadena a letras minúsculas usando el método toLowerCase()
```js
let minúsculas = challenge.toLowerCase()
 ```

6. Corta (segmenta) la primera palabra de la cadena usando el método substr() o substring()
```js
let cut = challenge.substring(0,2)
 ```

7. Separe la frase Days Of JavaScript de 30 Days Of JavaScript.
```js
let cut = challenge.substring(2,21)
 ```

8. Comprueba si la cadena contiene una palabra Script usando el método include()
```js
let incluye = challenge.include('Script')
 ```

9. Dividir la cadena en una matriz usando el método split()
```js
console.log(challenge.split()) // -> ["30 días de JavaScript"]
 ```

10. Dividir la cadena 30 días de JavaScript en el espacio usando el método split()
```js
console.log(challenge.split(' ')) // Dividir en una matriz en el espacio -> ["30", "Días", "De", "JavaScript"]
 ```

### Nivel 2 

 4. Compruebe si parseFloat('9.8') es igual a 10 si no redondearlo  exactamente a 10.
 ```js
let stringNum = '9.8'
let numRound = Math.round(parseFloat(stringNum))
 ```

5. Compruebe si 'on' se encuentra tanto en Python como en la jerga
 ```js
let frase = 'python, jerga'
let palabraEncontrada = /on/g
consola.log(frase.match(palabra encontrada))
 ```

6. Espero que este curso no esté lleno de jerga. Compruebe si hay jerga en la oración.
 ```js
let jargon = 'I hope this course is not full of jargon'
console.log(jargon.match('jargon'))
 ```
7. Generar un número aleatorio entre 0 y 100 inclusive.
 ```js
/*let randomNum = Math.random()
let randomZerotoCent = randomNum * 101
console.log(Math.round(randomZerotoCent))*/
función randomNum(){
return Math.floor(Math.random() * 101);
}
 ```

8. Genera un número aleatorio entre 50 y 100 inclusive.
 ```js
console.log(Math.floor( Math.random() * (100 - 50) + 50))
 ```

9. Genera un número aleatorio entre 0 y 255 inclusive.
 ```js
console.log(Math.floor(Math.random() * 256))
 ```

10. Acceda a los caracteres de la cadena 'JavaScript' utilizando un número aleatorio.
 ```js
let cadena = 'JavaScript'
console.log(cadena[Math.floor(Math.random()*cadena.length)])
 ```

11. Use console.log() y caracteres de escape para imprimir el siguiente patrón.
 ```js
/* 1 1 1 1 1
   2 1 2 4 8
   3 1 3 9 27
   4 1 4 16 64
   5 1 5 25 125 */
   consola.log('1 1 1 1 1\n2 1 2 4 8\n3 1 3 9 27\n4 1 4 16 64\n5 15 25 125 125')
 ```

12. Use substr para separar la frase because because because de la siguiente oración: 'You cannot end a sentence with because because because is a conjunction'
 ```js
let sentenciaBecause = 'You cannot end a sentence with because because because is a conjunction'
console.log(sentenceBecause.substring(31,54))// because because because 
 ```

### Nivel 3

1. 'Love is the best thing in this world. Some found their love and some are still looking for their love.' Cuente el número de palabras love en esta oración.
 ```js
var str = "'Love is the best thing in this world. Some found their love and some are still looking for their love.'";
var wordCount = str.match(/love/gim).length;
console.log(wordCount);//3
 ```

2. Use match() para contar el número de todas las palabras because en la siguiente oración: 'You cannot end a sentence with because because because is a conjunction'
```js
let sentence = 'No puedes terminar una oración con porque porque porque es una conjunción'
 console.log(sentence.match(/porque/gm).longitud)
 ```

3. Limpia el siguiente texto y encuentra la palabra más frecuente (pista, usa replace y expresiones regulares).
sentence = '%I $am@% a %tea@cher%, &and& I lo%#ve %te@a@ching%;. The@re $is no@th@ing; &as& mo@re rewarding as educa@ting &and& @emp%o@weri@ng peo@ple. ;I found tea@ching m%o@re interesting tha@n any ot#her %jo@bs. %Do@es thi%s mo@tiv#ate yo@u to be a tea@cher!? %Th#is 30#Days&OfJavaScript &is al@so $the $resu@lt of &love& of tea&ching'

```js
const sentence = '%I $am@% a %tea@cher%, &and& I lo%#ve %te@a@ching%;. The@re $is no@th@ing; &as& mo@re rewarding as educa@ting &and& @emp%o@weri@ng peo@ple. ;I found tea@ching m%o@re interesting tha@n any ot#her %jo@bs. %Do@es thi%s mo@tiv#ate yo@u to be a tea@cher!? %Th#is 30#Days&OfJavaScript &is al@so $the $resu@lt of &love& of tea&ching'

 let cleanSentence = sentence.replace([/%!@&?$&;/g],'');
 ```

4. Calcula el ingreso anual total de la persona extrayendo los números del siguiente texto. 'Él gana 5000 euros de salario por mes, bono anual de 10000 euros, cursos en línea de 15000 euros por mes.'
let text = 'Él gana 5000 euros de salario por mes, 10000 euros de bono anual, 15000 euros de cursos en línea por mes.'
```js
let textSplit = text.split(' ')
let salario = parseInt(textSplit[2])
let bonus = parseInt(textSplit[8])
let cursos = parseInt(textSplit[12])
let annualIncome = salario + bonificación + cursos
consola.log(annualIncome) //30000
```