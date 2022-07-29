---
title:  "Dia 3: Operadores booleanos y Date Object"
categories: JavaScript
tags: 30DiasDeJS  
toc: true
toc_sticky: true
sidebar:
    nav: docs
---


## Ejercicios

### Nivel 1

> El valor booleano es verdadero o falso.

1). Escriba tres declaraciones de JavaScript que proporcionen un valor veraz.

```js
let white = true
      white ? console.log('is white'): console.log('is no white')

    let lunes = true
    lunes? console.log('inicio de semana'): console.log('fin de semana')

    let road = true
    road ? console.log('road is open'): console.log('road is close')
```
    

2). Escriba tres declaraciones de JavaScript que proporcionen un valor falso.

    ```js
    let door = false
    door? console.log(`la puerta está cerrada`):console.log(`la puerta está abierta`)

    let noche = falso
    noche? console.log('es de dia'): console.log('es de noche')
```

3). Averigüe primero el resultado de la siguiente expresión de comparación sin usar console.log(). Después de decidir el resultado, confírmelo usando console.log()

 ```js
//i. 4 > 3 true
//ii. 4 >= 3 true
//iii 4 < 3 true
//v. 4 <= 3 false
//iv. 4 == 4 true
// vi. 4 === 4 true
//vii. 4 != 4 false
// viii. 4 !== 4 false
//ix. 4 != '4' true
//X. 4 == '4' true
//xi. 4 === '4' false
```

4). Encuentre la longitud de Python y la jerga y haga una declaración de comparación falsa.

```js
console.log('wordJargon'.length!=='wordPython'.length)
```
 
5). Utilice el objeto Date para realizar las siguientes actividades

+ ¿Qué año es hoy?

```js
const now = new Date()
const year = now.getFullYear()
```

+ ¿Cuál es el mes de hoy como número?

```js
const month = now.getMonth()+1
```

+ ¿Cuál es la fecha de hoy?

```js
const fecha = ahora.getDate()
```

+ ¿Cuál es el día de hoy como un número?

```js
const day = now.getDay()
```

+ ¿Cuál es el hora actual?

```js
const hours = now.getHours()
```

+ ¿Cuáles son los minutos actuales?

```js
consoele.log(now.getMinutes())
```
+ Averigüe el número de segundos transcurridos desde el 1 de enero de 1970 hasta ahora.

```js
const allSeconds = Date.now()
```

### Nivel 2

1). Escriba un script que solicite al usuario que ingrese la base y la altura del triángulo y calcule el área de un triángulo (área = 0,5 x b x h).

```js
let base = parseInt(prompt('base', 'ingresar base'))
let altura = parseInt(prompt('Altura','Ingresar altura'))
let ​​areaTriangulo = base * altura * 0.5
consola.log(areaTriangulo)
```

2). Escriba un script que solicite al usuario que ingrese el lado a, el lado b y el lado c del triángulo y calcule el perímetro del triángulo (perímetro = a + b + c)

```js
let sideA = parseInt(prompt('Lado a', 'Ingresar lado a'))
let sideB = parseInt(prompt('Lado b', 'Ingresar lado b'))
let sideC = parseInt(prompt('Lado c', 'Ingresar lado c'))
let perimetro = sideA + sideB + sideC
consola.log(perimetro)
```

3). Obtenga el largo y el ancho usando el indicador y calcule el área del rectángulo (área = largo x ancho y el perímetro del rectángulo (perímetro = 2 x (largo + ancho))

```js
let length = parseInt(prompt('length', 'Enter length')) 
let width = parseInt(prompt('Height','Enter width'))
let areaRectangle = length * width 
console.log(areaTriangle)
let perimeterRectangle = 2 * (length + width)
console.log(perimeterRectangle)
```

4). Obtenga el radio usando el indicador y calcule el área de un círculo (área = pi x r x r) y la circunferencia de un círculo (c = 2 x pi x r) donde pi = 3.14.

```js
const PI = 3.14
let radius = parseInt(prompt('Radius', 'Enter radius'))
let area = PI * (radius**2)
console.log(area)
let circunference = 2 * PI * radius
console.log(circunference)
```

5). Calcular la pendiente, la intersección x y la intersección y de y = 2x -2

```js
//Calculating the y-intercept
let x = 0;
let y = 2*x - 2; 
console.log(y);  //-2

//Calculating the x-intercept
let y = 0;
let x = y/2 + 2;
console.log(x);  //2
```
6). La pendiente es m = (y2-y1)/(x2-x1). Encuentra la pendiente entre el punto (2, 2) y el punto (6,10)

```js
let slope = console.log(`Slope is${(2, 2) / (6, 10)}`); // 0.2
```

8). Calcular el valor de y (y = x2 + 6x + 9). Trate de usar diferentes valores de x y averigüe en qué valor de x y es 0.

```js
let ​​xs1 = 2
let ​​xs2 = 6
let ​​y = xs1 + xs2 + 9
console.log(y)
```

9). Escriba un script que solicite al usuario que ingrese las horas y la tarifa por hora. Calcular el salario de la persona
+ Ingrese horas: 40
+ Introducir tarifa por hora: 28
+ Su ganancia semanal es 1120

```js
let payHours = parseInt(prompt('Hours', 'Enter hours worked'))
let ratePerHour = parseInt(prompt('Rate per hour', 'Enter rate per hour $'))
let earnings = payHours * ratePerHour
console.log(earnings)
```

10). Si la longitud de su nombre es mayor que 7, diga que su nombre es largo; de lo contrario, diga que su nombre es corto.

```js
let name = 'Jose'
name.length > 7 ? console.log('your name is long'): console.log('name is short') 

function namesLength(name){
  name= prompt('enter name'), name.length > 7 ? console.log('your name is long'): console.log('name is short');}
```

11). Compare la longitud de su nombre y la longitud de su apellido y debería obtener este resultado.

```js
let firstName = 'Jose'
let lastName = 'linardo'
let compareNames = firstName.length > lastName.length ? console.log('Your first name ' + firstName + 'is longer than your family name ' + lastName): console.log('your first name ' + firstName + 'is smaller than your family name ' + lastName)
```

12). Declare dos variables miEdad y suEdad y asígneles valores iniciales y miEdad y suEdad.

```js
let myAge = parseInt(prompt('my age'))
let yourAge = parseInt(prompt('your age'))
let compareAges =  myAge > yourAge ? console.log(`I am ${(myAge-yourAge)}years older than you.`): console.log(`I am ${(yourAge-myAge)} years young than you`)
```

13). Usando el aviso, obtenga el año en que nació el usuario y, si el usuario tiene 18 años o más, permita que el usuario conduzca, si no, dígale que espere una cierta cantidad de años.

+ Ingrese el año de nacimiento: 1995
+ Tienes 25 años. Tienes la edad suficiente para conducir.

+ Introduzca el año de nacimiento: 2005
+ Tienes 15 años. Podrás conducir después de 3 años.

```js
let birthYear = prompt('Enter your Birth year')
let minAge = 18
if(birthYear.length===4){
let age_ = now.getFullYear()-parseInt(birthYear)
const ageToDrive =  age_< 18? console.log(`You are. ${age_} You will be allowed to drive after ${(minAge-age_)} years`): console.log(`You are ${age_} You are old enough to drive`)}
else{ alert('Please enter your complete birth year.It should not be less than 4 numbers' )
}  
```

14). Escriba un script que solicite al usuario que ingrese el número de años. Calcular el número de segundos que puede vivir una persona. Supongamos que alguien vive solo cien años
Ingrese el número de años que vive: 100
Viviste 3153600000 segundos.

```js
let numberOfSeconds = parseInt(prompt('Enter years'))*(60*60 *24*365)
console.log(numberOfSeconds)
```

15). Cree un formato de hora legible por humanos usando el objeto de fecha y hora

+ AAAA-MM-DD HH:mm

```js
const ahora_= nueva Fecha()
let dia_ = `${(ahora_.getDate())}`.padStart(2,'0');
 let mes_ = `${(ahora_.getMonth()+1)}`.padStart(2,'0');
 let año_ = ahora_.getFullYear();
 const fecha_ = ahora_.getDate();
 dejar minutos = ahora_.getMinutes()
 const horas_ = ahora_.getHours()
console.log(`${año_}/${mes_}/${día_}/${horas_}:${minutos}`);
```

+ AAAA-MM-DD HH:mm

```js
console.log(`${año_}/${mes_}/${día_}/${horas_}:${minutos}`);
```

+ DD/MM/AAAA HH:mm*/

```js
console.log(`${día_}/${mes_}/${año_}/${horas_}:${minutos}`);
```

## Nivel 3

1). Crear un formato de hora legible por humanos usando el objeto de fecha y hora. La hora y el minuto deben ser siempre dos dígitos (7 horas deben ser 07 y 5 minutos deben ser 05)
   almohadillaInicio(2,'0')
  i.AAAA-MM-DD HH:mm ej. 20120-01-02 07:05

```js
const now_= new Date()
let day = `${(now_.getDate())}`.padStart(2,'0');
 let month = `${(now_.getMonth()+1)}`.padStart(2,'0');
 let year = now_.getFullYear();
 const date = now_.getDate();
 let minutes = now_.getMinutes()
 const hours = now_.getHours()
console.log(`${year}/${month}/${day}/${hours}:${minutes}`);
```


