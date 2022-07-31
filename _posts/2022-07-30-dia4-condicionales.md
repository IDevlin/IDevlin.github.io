---
title:  "Dia 4: Condicionales"
categories: JavaScript
tags: 30DiasDeJS  
toc: true
toc_sticky: true
sidebar:
    nav: docs
---

## Condicionales

> Las declaraciones condicionales se utilizan para tomar decisiones basadas en diferentes condiciones. De forma predeterminada, las declaraciones en el script de JavaScript se ejecutan secuencialmente de arriba a abajo. Si la lógica de procesamiento lo requiere.
Las condiciones se pueden implementar de las siguientes maneras:

+ if
+ if else
+ switch
+ ternary operator ?


## Ejercicios 


### Nivel 1

1). Obtenga la entrada del usuario usando el indicador ("Ingrese su edad:"). Si el usuario tiene 18 años o más, brinde comentarios: 'Tiene la edad suficiente para conducir', pero si no tiene 18 años, brinde otro comentario que indique que debe esperar la cantidad de años que necesita para cumplir 18.

```js
let yourAge = prompt('Enter you age')
if(yourAge >= 18){
console.log('you are old enough to drive')
}else {
console.log(`You are left whih ${(18 - yourAge )} to drive`)
}
```

2). Compare los valores de myAge y yourAge usando if... else. Según la comparación, registre el resultado en la consola indicando quién es mayor (tú o yo). Use prompt(“Ingrese su edad:”) para obtener la edad como entrada.

```js
let myAge = prompt('Enter my age')
let yourAge_ = prompt('Enter your age')
if(myAge<yourAge_){
    console.log(`You are ${yourAge_ - myAge} years older than me.`)}
    else if(myAge>yourAge_){
        console.log(`I am ${myAge - yourAge_} years older than you`)
    }else{
        console.log('we are same age')
    }
```

3). Si a es mayor que b, devuelva 'a es mayor que b', de lo contrario, 'a es menor que b'. Trate de implementarlo de maneras

```js
let a = 4
 let b = 3
 
 if(a>b){
console.log(`${a} is greater than ${b}`)
 }else if(a<b){
     console.log(`${a} is less than ${b}`)
 }else{
     console.log(`${a} is equal ${b}`)
 }

 a > b ? console.log('a is greater than b'):a<b? console.log('a is less than b'): console.log('a is equal b');
```

4). Los números pares son divisibles por 2 y el resto es cero. ¿Cómo verifica si un número es par o no usando JavaScript?

```js
let num =  prompt('Enter number')
if(num % 2 === 0){
    console.log(`${num}is an even number`)
}else{
    console.log(`${num} is an odd number`)
}
```

### Nivel 2

1). Write a code which can give grades to students according to theirs scores:
80-100, A
70-89, B
60-69, C
50-59, D
0-49, F

```js
let scores = prompt('Enter score')
if(  scores<= 100 && scores>=80){
console.log(`your score es A`)
}else if(scores>=70 && scores<=89){
    console.log('your score is B')
}else if(scores >=60 && scores<=69){
    console.log('your score is C')
}else if(scores >=50 && scores<=59){
    console.log('your score is D')
}else if(scores >=0 && scores<=49){
    console.log('Your score es F')
}else{
    console.log('Max score is 100')
}
```

2). Comprueba si la temporada es Otoño, Invierno, Primavera o Verano. Si la entrada del usuario es:
° Septiembre, Octubre o Noviembre, la temporada es Otoño.
° Diciembre, Enero o Febrero, la temporada es Invierno.
° Marzo, Abril o Mayo, la temporada es Primavera
° Junio, Julio o Agosto, la temporada es Verano

```js
let season = prompt('Enter month')
season = season.toLowerCase()
if(season==='september' || season === 'october'|| season==='november'){
    console.log('Season is Autumn')
}else if(season==='december'|| season==='january'|| season==='february'){
    console.log('the season is Spring')
}else{
    console.log('the season is Summer')
}
```
3). Comprueba si un día es fin de semana o laborable. Su secuencia de comandos tomará el día como entrada.

```js
let daysOfWeek = ['monday', 'tuesday', 'wedsnesday','thursday',  'friday', 'saturday', 'sunday'];

let input = prompt('Enter day').toLowerCase();
 input === daysOfWeek[5] || input === daysOfWeek[6]? console.log(`${input[0].toUpperCase() + input.slice(1)} is a weekend`):
input === daysOfWeek[0] || input === daysOfWeek[1] || input === daysOfWeek[2] || input === input[3] || input === daysOfWeek[4]? console.log(`${input[0].toUpperCase() + input.slice(1)} is a day working`):console.log(`${input} no es un dia de la semana`);
```

### Nivel 3

1). Escriba un programa que diga el número de días en un mes.

```js
const months = {"january": 1, "february": 2, "march":3, "april": 4, "may": 5, "june": 6, "july": 7, "august": 8, "september": 9, "october": 10, "november": 11, "december": 12 };

let daysInMonth = new Date(2022, months[prompt('Enter Month').toLowerCase], 0).getDate();
console.log(daysInMonth);
```

