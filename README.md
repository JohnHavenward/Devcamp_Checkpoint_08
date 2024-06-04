<p id="checkpoint-08"></p>

# CHECKPOINT 08

[¿Qué tipo de bucles hay en JS?](#bucles)</br>
[¿Cuáles son las diferencias entre const, let y var?](#tipos-de-variables)</br>
[¿Qué es una función de flecha?](#función-flecha)</br>
[¿Qué es la deconstrucción de variables?](#deconstrucción-de-variables)</br>
[¿Qué hace el operador de extensión en JS?](#operador-de-extensión)</br>
TODO[¿Qué es la programación orientada a objetos?](#programación-orientada-a-objetos)</br>
[¿Qué es una promesa en JS?](#promesas)</br>
[¿Qué hacen async y await por nosotros?](#async-y-await)</br>

</br></br></br></br>



<p id="bucles"></p>

## BUCLES

Los bucles son estructuras que nos permiten modificar el flujo de ejecución del código repitiendo un bloque de código múltiples veces. A cada repetición se la denomina iteración.

Existen cinco tipos de bucles en JavaScript:

- Bucles `for`
- Bucles `for in`
- Bucles `for of`
- Bucles `while`
- Bucles `do while`

En todos los tipos de bucles podemos alterar el flujo de ejecución con las declaraciones `break` y `continue`. 

</br></br>


### BUCLE FOR

El bucle `for` itera un número de veces determinado por un índice que se define al inicio del mismo junto con una condición que deberá cumplir en cada iteración. Este índice se actualiza al final de cada iteración y si no se sigue cumpliendo la condición especificada, el bucle finaliza.
      
#### SINTAXIS

La definición del bucle `for` contiene tres expresiones:

- **Expresión 1:** define el índice y se ejecuta solo una vez al comenzar el bucle
- **Expresión 2:** especifica la condición que debe cumplir el índice para ejecutar el bloque de código
- **Expresión 3:** define la actualización del índice y se ejecuta al final de cada iteración

```js
for (expresión 1; expresión 2; expresión 3) {
      //bloque de código a ejecutar
};
```

</br>


#### EJEMPLO

```js
let cuentaAtrás = [];


for (let i = 5; i > 0; i--) { 
      cuentaAtrás.push(i);
}


console.log(cuentaAtrás); //[5, 4, 3, 2, 1]
```

</br></br>


### BUCLE FOR IN

El bucle `for in` es especialmente útil para iterar las propiedades de un objeto. El bloque de código se ejecuta para cada una de las propiedades en el orden en el que estas han sido definidas dentro del objeto. 
   
#### SINTAXIS

```js
for (propiedad in objeto) {
      //bloque de código a ejecutar
};
```

</br>


#### EJEMPLO

```js
let joya = {tipo:"anillo", peso:"7g", material: "oro"};
let copia = {};


for (let propiedad in joya) {
      copia[propiedad + "_copia"] = joya[propiedad];
}


console.log(copia); //{tipo_copia: "anillo", peso_copia: "7g", material_copia: "oro"}
```

</br></br>


### BUCLE FOR OF

Los bucles `for of` ejecutan el bloque de código una vez por cada elemento de un objeto iterable. Normalmente este suele ser un *array* y la cantidad de iteraciones a realizar viene predefinida por la cantidad de elementos existentes dentro del objeto iterable.
    
#### SINTAXIS

```js
for (elemento of iterable) {
      //bloque de código a ejecutar
};
```

</br>


#### EJEMPLO

```js
let listaPalabras = ["Atardecer", "Castillo", "Incienso", "Montaña"];
let iniciales = [];


let text = "";
for (let palabra of listaPalabras) {
      iniciales.push(palabra[0]);
}


console.log(iniciales); //["A", "C", "I", "M"]
```

</br></br>


### BUCLE WHILE

Con los bucles `while` podemos ejecutar un bloque de código un número indeterminado de veces siempre y cuando se cumpla una condición previamente definida. Esta condición es evaluada al comienzo de cada iteración y debemos asegurarnos de que en algún momento deje de cumplirse.
   
#### SINTAXIS

```js
while (condición) {
      //bloque de código a ejecutar
};
```

</br>


#### EJEMPLO

```js
let semana = [];


while (semana.length < 7) {
      semana.push("D" + (semana.length + 1));
}


console.log(semana); //["D1", "D2", "D3", "D4", "D5", "D6", "D7"]
```

</br>


Si durante la ejecución del bucle la condición no se deja de cumplir en alguna de las iteraciones, se producirá un bucle infinito y no podrá continuar ejecutándose el resto del programa.

Es por ello que en esta clase de bucles suele ser frecuente la definición de una variable de indexado. Esta se define antes del bucle y nos permite partir de un valor de referencia para poder controlar las iteraciones realizadas.

```js
let i = 0;


while (i < 50) {
      i += 1;
}


console.log(i); //50
```

</br></br>


### BUCLE DO WHILE

El comportamiento del bucle `do while` es muy parecido al del bucle `while`. La principal diferencia es que en un bucle `do while` siempre se ejecuta primero el código antes de evaluar la condición. Esto garantiza que el código es ejecutado al menos una vez.
 
#### SINTAXIS

```js
do {
      //bloque de código a ejecutar
}
while (condición);
```

</br>


#### EJEMPLO

```js
let i = 0;


do {
      i += 100;
}
while (i < 25);


console.log(i); //100
```

</br></br>


### BREAK Y CONTINUE

Se puede alterar el flujo normal de un bucle sin importar el punto de ejecución en el que se encuentre. Existen dos formas diferentes:

- hacer que el bucle finalice directamente
- hacer que la iteración actual finalice directamente y comience la siguiente 

</br>


La declaración `break` rompe el flujo del bucle y este finaliza directamente.

```js
let i = 0;


while (i < 10) {
      if (i == 5) {
            break;
      }
      i += 1;
}


console.log(i); //5
```

</br>


La declaración `continue` termina de ejecutar la iteración actual y comienza directamente la siguiente.

```js
let frutas = ["manzana", "plátano", "fresa", "piña"];
let listaCompra = [];


for (fruta of frutas) {
      if (fruta == "plátano") {
            continue;
      }
      listaCompra.push(fruta);
}


console.log(listaCompra); //["manzana", "fresa", "piña"]
```

</br></br>


### BUCLES ANIDADOS

Podemos definir un bucle dentro de otro bucle. En este tipo de estructuras el bucle interno se ejecuta una vez por cada iteración del bucle externo.

```js
let filas = ["A", "B", "C"];
let columnas = [1, 2, 3];
let tablero = [];


for (fila of filas) {
      let filaTablero = [];
      for (columna of columnas) {
            filaTablero.push(fila + columna);
      }
      tablero.push(filaTablero);
}


console.log(tablero); //[["A1", "A2", "A3"], ["B1", "B2", "B3"], ["C1", "C2", "C3"]]
```

</br></br></br></br>



###### [Inicio](#checkpoint-08)

<p id="tipos-de-variables"></p>

## TIPOS DE VARIABLES

El tipo de datos contenido por una variable en JavaScript depende del valor asignado, no se define de forma explícita. Sin embargo, al declarar la variable sí debemos especificar de qué tipo de variable se trata. Existen tres tipos disponibles en JavaScript y son los siguientes: 

- `var`
- `let`
- `const`

</br>


Estos tres tipos presentan comportamientos parecidos y son algunas de sus propiedades las que los hacen diferenciarse. Conocer y entender estas diferencias es vital para poder seleccionar el tipo de variable adecuado para cada situación concreta.

</br>


### VAR

Antes de la versión ES6 de JavaScript `var` era el único tipo de variable disponible. Se declara con la palabra clave `var` y no es necesario asignar un valor inicial.

```js
var unaVariable = "Llueve";

var otraVariable;
```

<br>


#### REASIGNACIÓN

A una variable de tipo `var` se le pueden reasignar valores tantas veces como se desee.

```js
var miVariable = "Hola mundo";

miVariable = 13;

miVariable = true;
```

</br>


#### REDECLARACIÓN

Una variable de tipo `var` puede declararse múltiples veces en el programa sin causar ningún error.

```js
var miVariable = "Hola mundo";

var miVariable = 13;

var miVariable = true;
```

</br>


> **NOTA:** Esto puede parecer algo ventajoso pero puede generar problemas en el código si sobrescribimos variables de forma no intencionada.

</br>


#### ÁMBITO DE USO

Una variable `var` puede tener dos ámbitos de uso en función de dónde sea declarada: global y local. La variable podrá ser solamente accedida en ese ámbito.

```js
var variableGlobal = "Ámbito global";


function mostrarVariables() {
      var variableLocal = "Ámbito local";
      console.log(variableGlobal + " y "+variableLocal);    
}

mostrarVariables(); //Ámbito global y Ámbito local


console.log(variableGlobal); //Ámbito global
console.log(variableLocal); //error
```

</br>
 

Sin embargo, hay una situación concreta en la que el uso de variables de tipo `var` puede darnos resultados inesperados. Cuando definimos dos variables `var` de idéntico nombre en ámbitos diferentes, una global y la otra local, podemos esperar que ambas se comporten de forma independiente. Sin embargo, cuando cambiamos el valor de la variable local también lo hará la global. Se trata de la misma variable y no puede tener valores diferentes para cada uno de los ámbitos de uso. 

```js
var saludo = "Hola";


if (true) {
      var saludo = "Buenas tardes";
      console.log(saludo); //Buenas tardes
}


console.log(saludo) //Buenas tardes
```

</br>


Es por ello que para evitar este tipo de potenciales problemas se añadieron las variables de tipo `let` y `const`, las cuales se comportan de la manera esperada en estas situaciones.

</br>


#### HOISTING

Una variable `var` se beneficia del *hoisting* llevado a cabo por JavaScript ya que nos permite hacer referencia a una variable incluso antes de haber sido declarada. Sin embargo, hay que tener en cuenta que el valor inicial de la variable siempre será `undefined`.

```js
console.log(miVariable); //undefined

var miVariable = 10;
```

</br>


### LET

Las variables de tipo `let` son consideradas la versión moderna de las de tipo `var` ya que presentan una serie de comportamientos diferentes que las hacen más apropiadas para un desarrollo más seguro y fácil de mantener.

Se declaran con la palabra clave `let` y no es necesario asignar un valor inicial.

```js
let unaVariable = 28;

let otraVariable;
```

</br>


#### REASIGNACIÓN

A una variable de tipo `let` se le puede reasignar un nuevo valor las veces deseadas.

```js
let miVariable = "Hola mundo";

miVariable = 13;

miVariable = true;
```

</br>


#### REDECLARACIÓN

La redeclaración de variables `let` no es posible y hacerlo nos dará error.

```js
let miVariable = [1, 2, 3];

let miVariable; //error
```

</br>


#### ÁMBITO DE USO

El ámbito de uso de las variables `let` es siempre el bloque de código en el que han sido declaradas y no serán accesibles desde fuera de este.

```js
tareas = 5


if (tareas > 0) {
      let mensaje = "Hay tareas pendientes";
}


console.log(mensaje); //error
```

</br>


Cuando definimos dos variables `let` de idéntico nombre en dos bloques de código diferentes, ambas se comportan como variables independientes. Incluso en el caso de que uno de los bloques esté contenido dentro del otro, ambas variables seguirán comportándose de manera independiente la una de la otra.

```js
let saludo = "Hola";


if (true) {
      let saludo = "Buenas tardes";
      console.log(saludo); //Buenas tardes
}


console.log(saludo) //Hola
```

</br>


#### HOISTING

Una variable `let` no se beneficia del *hoisting* de JavaScript y no puede hacerse referencia a ella antes de su declaración. Si lo hacemos JavaScript nos mostrará un error.

```js
console.log(miVariable); //error

let miVariable = 10;
```

</br>


### CONST

La variable `const` debe su nombre al hecho de que su valor es constante y único. Este valor debe ser siempre asignado al ser declarada la variable `const` o de lo contrario JavaScript nos dará un error.

```js
const fuerzaGravedad = 9.80665;

const variableConstante; //error
```

</br>


#### REASIGNACIÓN

Una variable de tipo `const` no admite la reasignación de valores y hacerlo nos dará error.
 
```js
const variableConstante = "Valor inicial";

variableConstante = "Valor nuevo"; //error
```

</br>


#### REDECLARACIÓN

La redeclaración de variables `const` no es posible y hacerlo nos dará error.

```js
const variableConstante  = "Valor inicial";

const variableConstante  = "Valor alternativo"; //error
```

</br>


#### ÁMBITO DE USO

El ámbito de uso de las variables `const` es siempre el bloque de código en el que han sido declaradas y no serán accesibles desde fuera de este.

```js
function calcularPerímetro(radio) {
      const pi = 3.14159265359;
      
      return 2 * pi * radio;
}


console.log(pi); //error
```

</br>


Cuando definimos dos variables `const` de idéntico nombre en dos bloques de código diferentes, ambas se comportan como variables independientes. Incluso en el caso de que uno de los bloques esté contenido dentro del otro, ambas variables seguirán comportándose de manera independiente la una de la otra.

```js
const saludo = "Hola";


if (true) {
      const saludo = "Buenas tardes";
      console.log(saludo); //Buenas tardes
}


console.log(saludo) //Hola
```

</br>


#### HOISTING

En lo que respecta al *hoisting*, las variables `const` no son inicializadas y por eso no pueden usarse antes de haber sido declaradas.

```js
console.log(variableConstante); //error

const variableConstante = "Valor constante";
```

</br>


### TABLA COMPARATIVA

A continuación se muestra una tabla en la que se comparan las diferentes propiedades de cada uno de los tres tipos de variables disponibles en JavaScript.

</br>


| PROPIEDADES                | `var`            | `let`    | `const`   |
| :------------------------- | :--------------: | :------: | :-------: |
| Necesario inizializar      | No               | No       | Sí        |
| Reasignación               | Sí               | Sí       | No        |
| Redeclaración              | Sí               | No       | No        |
| Ámbito de uso              | global / local   | bloque   | bloque    |
| Inicialización *Hoisting*  | `undefined`      | No       | No        |

</br></br></br></br>



###### [Inicio](#checkpoint-08)

<p id="función-flecha"></p>

## FUNCIÓN FLECHA

La función flecha es un tipo especial de expresión de función introducido por primera vez en la versión ES6 de JavaScript.
Al igual que la expresión de función, se trata de una función anónima asociada a una variable. Sin embargo, la función flecha destaca por proporcionar una sintaxis más abreviada y de fácil lectura.

Las funciones flecha prescinden de la palabra clave `function` y usan un símbolo de flecha `=>` para su definición.

```js
sumar = (a, b, c) => {
      let total = 0;
      
      total += a;
      total += b;
      total += c;
      
      return total;
}


console.log(sumar(2, 2, 6)); //10
```

</br>


Además, en el caso de que la función solo tenga una sentencia y esta devuelva un único valor podemos incluso prescindir de la palabra clave `return` y las llaves `{}`.

```js
sumar = (a, b, c) => a + b + c;

console.log(sumar(2, 2, 6)); //10
```

</br>


Por último, en el caso de que la función tenga un solo parámetro podemos prescindir también de los paréntesis `()`.

```js
saludo = nombre => `Hola, mi nombre es ${nombre}`;

console.log(saludo("Romina")); //Hola, mi nombre es Romina
```

</br>


### THIS

La principal característica que diferencia a las funciones flecha es el comportamiento de la palabra clave `this`. En este tipo de función `this` siempre hace referencia al objeto donde ha sido definida la función y no al objeto que la llama.


```js
const mostrarFlecha = () => console.log(this.valor);


function mostrarNormal() {
      console.log(this.valor);      
}
      

const miObjeto = {
      ejecutarMostrarFlecha: mostrarFlecha,
      ejecutarMostrarNormal: mostrarNormal,
      valor: 10
}


miObjeto.ejecutarMostrarFlecha(); //undefined
miObjeto.ejecutarMostrarNormal(); //10
```

</br>


### USOS COMUNES

Debido a la brevedad y facilidad de lectura que proporcionan las funciones flecha, su uso es habitual en una amplia variedad de situaciones.

Un ejemplo claro es la evaluación sencilla de variables.

```js
const par = (n) => (n % 2 == 0 ? "Sí" : "No");

console.log(par(8)); //Sí
console.log(par(9)); //No
console.log(par(3)); //No


const mayor = (a, b, c) => ((a > b ? a : b) > c ? (a > b ? a : b) : c);

console.log(mayor(3, 5, 2)); //5
console.log(mayor(8, 4, 7)); //8
console.log(mayor(6, 1, 9)); //9
```

</br>


Las funciones flecha también son muy útiles para el trabajo con *arrays*.

```js
let arr = [5, 6, 13, 0, 1, 18, 23];


let suma = arr.reduce((a, b) => a + b);
let pares = arr.filter((v) => v % 2 == 0);
let doble = arr.map((v) => v * 2);


console.log(suma); //66
console.log(pares); //[6, 0, 18]
console.log(doble); //[10, 12, 26, 0, 2, 36, 46]
```

</br>


De igual forma, las funciones flecha resultan ser idóneas para escribir cadenas de promesas más concisas.

```js
hacerAlgo()
      .then((resultado) => doSomethingElse(resultado))
      .then((nuevoResultado) => doThirdThing(nuevoResultado))
      .then((resultadoFinal) => {
        console.log(`El resultado final es: ${resultadoFinal}`);
      })
      .catch(failureCallback);
```

</br></br></br></br>



###### [Inicio](#checkpoint-08)

<p id="deconstrucción-de-variables"></p>

## DECONSTRUCCIÓN DE VARIABLES

La deconstrucción de variables es una expresión que nos permite asignar el valor de varias variables a la vez en una sola línea de código. Las variables son agrupadas y asignadas como conjunto a otra agrupación de variables o valores. Las variables son asignadas así al elemento correspondiente en el otro conjunto, situado este en la parte derecha de la expresión.

```js
let valores = [18, "Verde", {x: 2, y: -5}];

let [edad, color, coordenadas] = valores;


console.log(edad); //18
console.log(color); //Verde
console.log(coordenadas); //{x: 2, y: -5}
```

</br>


Un uso práctico de la deconstrucción de variables es para poder declarar múltiples variables y asignarles un valor.

```js
let [a, b, c, d] = [1, 2, 3, 4];


console.log(a); //1
console.log(b); //2
console.log(c); //3
console.log(d); //4
```

</br>


### USO CON ARRAYS

Cuando usamos la deconstrucción de variables con *arrays* es muy importante tener en cuenta el orden en el que se definen las variables contenidas dentro del *array*, ya que se asignan en ese orden a los elementos contenidos en el *array* de la parte derecha.

En el caso de que la variable no tenga un elemento correspondiente en el otro conjunto, se le asigna el valor `undefined`.

```js
let [a, b, c] = [3, 9];


console.log(a); //3
console.log(b); //9
console.log(c); //undefined
```

</br>


Además, es posible asignar un valor por defecto a las variables para el caso en que no se les asigne un valor en la desconstrucción de variables.

```js
let a, b;

[a = 34, b = 71] = [15];


console.log(a); //15
console.log(b); //71
```

</br>


Si lo deseamos podemos dejar posiciones vacías en el *array* ignorando así los elementos correspondientes a esas posiciones.

```js
const datosObjeto = ["37cm", "dato no importante", "500gr"]

const [longitud, , peso] = datosObjeto;


console.log(longitud); //37cm
console.log(peso); //500gr
```

</br>


Un uso muy común de la deconstrucción de variables es para intercambiar el valor de dos valores sin necesidad de recurrir a una tercera variable temporal.

```js
let a = 30;
let b = 80;


[a, b] = [b, a];


console.log(a); //80
console.log(b); //30
```

</br>


Cunado una función retorna un *array* de valores, resulta muy útil usar la deconstrucción de variables para recoger estos valores en variables independientes.

```js
function calcularOperaciones(a, b) {
      let suma = a + b;
      let resta = a - b;
      let multiplicación = a * b;
      let división = a / b;
      
      return [suma, resta, multiplicación, división];
}


let [suma, resta, multiplicación, división] = calcularOperaciones(5, 2);


console.log(suma); //7
console.log(resta); //3
console.log(multiplicación); //10
console.log(división); //2.5
```

</br>


### USO CON OBJETOS

Cuando se usa la deconstrucción de variables con objetos, los valores correspondientes de los dos conjuntos son los que tienen el mismo nombre de propiedad.

```js
let objeto = { a: 10, b: 20, c: 30}

let {c, a, b} = objeto;


console.log(a); //10
console.log(b); //20
console.log(c); //30
```

</br>


También es posible asignar un nombre a la variable que no sea el de la propiedad del objeto. Para ello añadimos el símbolo `:` y el nombre después de la propiedad. 

```js
const información = { dato1: "Andrés" , dato2: 35 };
const { dato1: nombre, dato2: edad } = información;


console.log(nombre); //Andrés
console.log(edad); //35
```

</br>


Es posible asignar un valor por defecto a las variables para el caso en que no se les asigne un valor en la desconstrucción de variables.

```js
const { evento, día, hora = "no definida" } = { evento: "reunión", día: "martes" };


console.log(evento); //reunión
console.log(día); //martes
console.log(hora); //no definida
```

</br>


Cuando pasamos un objeto como argumento a una función, la deconstrucción de variables facilita que la función tome las propiedades necesarias para usarlas directamente y que no haga falta expresar `objeto.propiedad` cada vez que se usa una propiedad del objeto.

```js
const visitante = {
      nombre: "Pablo",
      apellido: "García", 
      altura: 185,
      peso: 78,
      nacionalidad: "colombiana"
}


function mostrarDatos({nombre, apellido, nacionalidad}) {
      console.log(` ${nombre} ${apellido}, nacionalidad ${nacionalidad}`);
}


mostrarDatos(visitante); //Pablo García, nacionalidad colombiana
```

</br>


Incluso podemos especificar propiedades anidadas para que la función las tome como argumentos. Para ello debemos usar nuevamente la deconstrucción de variables con las propiedades anidadas.

```js
const mueble = {
      tipo: "mesa",
      ubicación: "comedor", 
      color: "azul",
      medidas: {
            anchura: 90,
            profundidad: 200,
            altura: 70
      } 
}


function mostrarDatos({tipo, ubicación, medidas: {anchura, profundidad} }) {
      console.log(`El mueble es una ${tipo}, se encuentra en el ${ubicación} y mide ${anchura}x${profundidad}cm`);
}


mostrarDatos(mueble); //El mueble es una mesa, se encuentra en el comedor y mide 90x200cm
```

</br></br></br></br>



###### [Inicio](#checkpoint-08)

<p id="operador-de-extensión"></p>

## OPERADOR DE EXTENSIÓN

El operador de extensión toma un objeto iterable y expande todos sus elementos permitiéndonos operar con ellos individualmente en vez de como una agrupación. Este operador se representa con tres puntos `...` y siempre se escribe inmediatamente antes del objeto iterable a expandir.

```js
const objetoIterable = [1, 2, 3];

const [a, b, c] = [...objetoIterable];


console.log(a); //1
console.log(b); //2
console.log(c); //3
```

</br>


Se trata de un operador de uso muy versátil ya que puede emplearse con varios propósitos en función de con qué tipo de objeto estemos trabajando. 

</br>


### USO CON ARRAYS

El operador de extensión `...` permite concatenar fácilmente dos o más *arrays*.

```js
const primeraParte = [1, 2];
const segundaParte = [3, 4];
const terceraParte = [5, 6];

const variableCompleta = [...primeraParte, ...segundaParte, ...terceraParte];


console.log(variableCompleta); //[1, 2, 3, 4, 5, 6]
```

</br>


También resulta de gran utilidad cuando se necesita integrar un *array* dentro de otro.

```js
const parteCentral = [3, 4, 5];

const variableCompleta = [1, 2, ...parteCentral ,6];


console.log(variableCompleta); //[1, 2, 3, 4, 5, 6]
```

</br>


### USO CON CADENAS

Podemos usar el operador `...` para separar individualmente los diferentes caracteres de un cadena.

```js
let cadena = "Sapo azul";

let caracteres = [...cadena];


console.log(caracteres); //["S", "a", "p", "o", " ", "a", "z", "u", "l"]
```

</br>


### USO CON OBJETOS

También podemos usar el operador `...` con un objeto para separar cada una de sus propiedades de forma individual.

Al crear un objeto a partir de las propiedades individuales de varios objetos hay que tener en cuenta que dado que un objeto no puede tener más de una propiedad iguales, el último objeto con ella será el que determine su valor.

```js
const datos = {
      título: 'Los Juegos del Hambre',
      autor: 'Suzanne Collins',
      edición: 'primera'
}


const otrosDatos = {
      editorial: 'MOLINO',
      páginas: '400',
      edición: 'segunda'
}


const datosCompletos = {...datos, ...otrosDatos}


console.log(datosCompletos);
//{título: "Los Juegos del Hambre", autor: "Suzanne Collins", edición: "segunda", editorial: "MOLINO", páginas: "400"}
```

</br>


### USO CON ARRAYS COMO ARGUMENTOS DE FUNCIÓN

JavaScript no nos permite pasar un *array* como argumento directamente a una función. Sin embargo, el operador `...` separa en elementos el *array* de forma que la función los acepte como argumentos individuales.

```js
let dimensiones = [2, 7, 3];


function calcularVolumen(anchura, profundidad, altura) {
      return anchura * profundidad * altura;
          
}


console.log(calcularVolumen(...dimensiones)); //42
```

</br>


### USO CON DECONSTRUCCIÓN DE VARIABLES

Usado junto a la deconstrucción de variables el operador `...` nos permite asignar a un *array* el resto de variables que han quedado sin asignar en la deconstrucción. 


```js
const [a, b, ...resto] = [1, 2, 3, 4, 5];


console.log(resto); //[3, 4, 5]
```

</br>


### USO CON PARÁMETROS DE FUNCIÓN

Al usar el operador `...` en el último parámetro de una función, el resto de argumentos pasados en la llamada se agrupan en un *array* que puede ser manipulado en el código de la misma. Esto permite que la función admita un número indefinido de argumentos.

```js
function sumar(a, b, ...c) {
      let resultado = a + b;

      c.forEach(n => resultado += n);
      
      return resultado;
}


console.log(sumar(3,5)); //8
console.log(sumar(9,2,6)); //17
console.log(sumar(7,4,1,8)); //20
```

</br></br></br></br>



###### [Inicio](#checkpoint-08)

<p id="programación-orientada-a-objetos"></p>

## PROGRAMACIÓN ORIENTADA A OBJETOS

Python es un lenguaje de programación orientado a objetos y por tanto emplea los conceptos de clase y objeto. La programación orientada a objetos está basada en cuatro principios o pilares básicos que son los siguientes:

- **Herencia** - reutilizar el código compartiéndolo entre varios objetos.
- **Encapsulamiento** - proteger la información de manipulaciones no autorizadas.
- **Abstracción** - representar y manejar conceptos complejos de manera simplificada.
- **Polimorfismo** - ejecutar la misma orden con varios objetos y que respondan de formas diferentes.

</br>


Las clases son la pieza clave para poder cumplir esos principios y en esencia lo que hacen es agrupar una serie de variables y funciones en un único elemento. Una vez definido, ese elemento puede ser construido múltiples veces y cada copia es única e independiente del resto. Las clases pueden entenderse así como las "plantillas" o "modelos" que son usados para producir objetos nuevos.

</br>

Puede resultar útil para entender el concepto de una clase fijarse en el mito de la cueva descrito por Platón. En él la idea de un objeto es el único verdadero o perfecto y puede verse como la clase. El resto son solo sombras proyectadas y se corresponden con los objetos creados a partir de esa clase.

La clase es la parte teórica que no podemos encontrar directamente presente en la realidad pero que identificamos fácilmente en los objetos reales que la representan.

</br>

![Mito de la cueva](/images/mito_cueva.png)

</br></br>


En python cada objeto pertenece a una clase y es la que la hace tener ciertas funciones y variables asociadas a ella.

Para definir una clase debemos usar la palabra reservada `class` junto a su nombre. Por convenio la primera letra del nombre de una clase siempre de escribe en mayúsculas. Vemos un ejemplo a continuación:

</br>

```python
class Vehículo:
    color = "rojo"
    ruedas = 4
    
               
print(f'El vehículo es de color {Vehículo.color} y tiene {Vehículo.ruedas} ruedas.')
#El vehículo es de color rojo y tiene 4 ruedas.
```

</br>


### INSTANCIAS

La creación de una instancia, también llamada instanciación de una clase, es el proceso de crear un objeto a partir de la plantilla definida por la clase. 

Una clase puede tener tantas instancias creadas como se quiera.

Para acceder a los métodos y atributos de la instancia se usa el operador `.` tal y como vemos a continuación:

</br>

```python
class Alerta:
    def __init__(self, identificador, hora):
        self.identificador = identificador
        self.hora = hora
  
    def informar(self):
        print(f'La alerta "{self.identificador}" está programada para las {self.hora}h')


alerta_1 = Alerta("Reunión", "10:30")
alerta_2 = Alerta("Comida", "14:00")


print(alerta_1.identificador) #Reunión
alerta_2.informar() #La alerta "Comida" está programada para las 14:00h
```
</br>


Para eliminar una instancia creada podemos usar la palabra clave `del`. Vemos su uso siguiendo con el ejemplo anterior:

</br>

```python
del alerta_1
del alerta_2
```

</br>


### CONSTRUCTOR

Cuando una instancia de una clase es creada se ejecuta automáticamente el método `__init__()`. Este método es el constructor de la clase y se encarga de recibir los argumentos y asignarlos a la instancia. De esta forma podemos asignar de forma sencilla y breve información a cada una de las instancias creadas.

El constructor debe estar definido dentro de la clase y hacer uso del parámetro `self` para hacer referencia a la instancia creada.

Cuando creamos una instancia no es necesario hacer ninguna referencia al método `__init__()`, simplemente debemos pasar todos los argumentos definidos en él y omitir el argumento `self` ya que este es pasado de forma implícita.

Podemos ver un ejemplo del uso de un constructor a continuación:

```python
class Pasajero:
    def __init__(self, nombre, apellido, edad):
        self.nombre = nombre
        self.apellido = apellido
        self.edad = edad


pasajero_1 = Pasajero("Ismael", "García", 57)
pasajero_2 = Pasajero("Helena", "Salgado", 44)
pasajero_3 = Pasajero("Lucía", "Blanco", 31)
```

</br>


### ATRIBUTOS

Un atributo es una variable que forma parte de una clase. La única diferencia con una variable normal de python es que un atributo siempre debe estar asociado a una clase.

Una clase puede contener tantos atributos como se quiera.

Hay dos tipos de atributos dentro de una clase:

- Atributos de clase
- Atributos de instancia

</br>


Los atributos de clase son comunes a todas las instancias y se definen directamente dentro de la clase. El valor de un atributo de clase es único y compartido por todas las instancias y la propia clase. Si alguno de los objetos asociados a ella cambia su valor lo hace también para el resto. Podemos ver un ejemplo de ello a continuación:

</br>

```python
class Concursante:
    premio_acumulado = 300
  
    def __init__(self, nombre):
        self.nombre = nombre


concursante_1 = Concursante("Sonia")
concursante_2 = Concursante("Ruth")
concursante_3 = Concursante("Nicolás")


print(Concursante.premio_acumulado) #300

Concursante.premio_acumulado += 50
print (concursante_1.premio_acumulado) #350

Concursante.premio_acumulado += 100
print (concursante_2.premio_acumulado) #450

Concursante.premio_acumulado += 250
print (concursante_3.premio_acumulado) #700
```
</br>


Los atributos de instancia son propios de cada instancia y se definen dentro del método `__init__()`. Cada instancia tiene un valor propio para cada atributo.  Si una instancia cambia el valor de su atributo no afecta al resto de las instancias. Además la clase en sí no tiene definidos estos atributos y por tanto no tiene acceso a ellos. Podemos ver la definición y uso de atributos de instancia en el siguiente ejemplo:

</br>

```python
class Cuenta:
  def __init__(self, titular, fondos):
    self.titular = titular
    self.fondos = fondos


cuenta_1 = Cuenta("Carmen", 1900)
cuenta_2 = Cuenta("Antonio", 2700)

print (cuenta_1.titular + " : " + str(cuenta_1.fondos) + "$") #Carmen : 1900$ 
print (cuenta_2.titular + " : " + str(cuenta_2.fondos) + "$") #Antonio : 2700$
```
</br>


##### PROPIEDADES

Las propiedades son un tipo especial de atributo de instancia que se definen con el decorador `@property`. La principal diferencia de una propiedad es que permiten un acceso controlado a ella en los procesos de lectura y escritura  de esta. Esto permite hacer comprobaciones e incluso realizar algún cálculo de forma automática cuando se acceda a su valor.

Para ello se definen dos métodos:

- el método *getter*: se encarga de la lectura del atributo
- el método *setter*: se encarga de la escritura del atributo

</br>


Podemos ver un ejemplo del uso de propiedades a continuación:

</br>

```python
class Casa:
    def __init__(self, precio):
        self.__precio = precio

    @property
    def precio(self):
        return self.__precio

    @precio.setter
    def precio(self, nuevo_valor):
        if nuevo_valor != "":
            print(f'Modificando el precio a {nuevo_valor}')
            self.__precio = nuevo_valor
        else:
            print("Error. Se debe pasar un valor")
            

mansión = Casa("1.200.000€")

mansión.precio = "900.000€"
#Modificando el precio a 900.000€

print(mansión.precio)
#900.000€
```
</br>


Nótese que aunque por su sintaxis un atributo puede parecer un método no se usa el símbolo `()` cuando se hace referencia a él. 
</br>


### MÉTODOS

Un método es una función que forma parte de una clase. La única diferencia con una función normal de python es que un método siempre debe estar asociado a una clase. Se pueden definir tantos métodos como se quiera dentro de una clase.

Cuando definimos un método el primer parámetro siempre debe ser `self`. Este hace referencia a la instancia que la llama y sirve para acceder a sus atributos y métodos. El uso de del nombre *self* es totalmente arbitrario y simplemente se trata de una convención.

Existen principalmente cuatro tipos diferentes de métodos y son los siguientes:

- Métodos de instancia
- Métodos de clase
- Métodos estáticos
- Métodos abstractos

</br>


##### MÉTODOS DE INSTANCIA

Los métodos de instancia son los métodos definidos normalmente dentro de la clase. Aparte de `self` pueden definir otros parámetros tal y como vemos en el siguiente ejemplo:

</br>

```python
class Trapo:
    def limpiar(self, objeto):
        print(f'Limpiando {objeto}')


mi_trapo = Trapo()


mi_trapo.limpiar("mesa") #Limpiando mesa
mi_trapo.limpiar("silla") #Limpiando silla
```

</br>


##### MÉTODOS DE CLASE

Los métodos de clase se definen con el decorador `@classmethod` y usan el parámetro `cls` en lugar de `self`. Este parámetro hace referencia a la clase del objeto y no a la instancia. Es por ello que solo pueden acceder y modificar a la clase y en ningún caso pueden hacerlo a la propia instancia.

Pueden llamarse desde la clase o la instancia indistintamente. Vemos un ejemplo a continuación:

</br>

```python
class Concursante:
    premio_acumulado = 0
  
    @classmethod
    def acumular_premio(cls, premio):
        cls.premio_acumulado += premio


concursante_1 = Concursante()
concursante_2 = Concursante()


print(Concursante.premio_acumulado) #0

Concursante.acumular_premio(50)
print(Concursante.premio_acumulado) #50

concursante_1.acumular_premio(100)
print(Concursante.premio_acumulado) #150

concursante_2.acumular_premio(100)
print(Concursante.premio_acumulado) #250
```

</br>


##### MÉTODOS ESTÁTICOS

Los métodos estáticos se definen con el decorador `@staticmethod` y no tienen como parámetro ni la instancia ni la clase. Es por ello por lo que el uso de estos métodos previenen el poder modificarlas y son usados como métodos que aportan utilidades concretas.

Los métodos estáticos se pueden ver como funciones normales con la particularidad de que van ligadas a una clase concreta. En el siguiente ejemplo se muestra su uso:

</br>

```python
class Matemáticas:
    @staticmethod
    def sumar(a, b):
        return a + b
        
    @staticmethod
    def multiplicar(a, b):
        return a * b


print(Matemáticas.sumar(5, 3)) #8
print(Matemáticas.multiplicar(5, 3)) #15
```

</br>


##### MÉTODOS ABSTRACTOS

Los métodos abstractos son aquellos que son declarados pero no tienen una implementación directa en la clase. Su finalidad es que las clases que hereden de esta estén obligadas a hacer su propia implementación de este método.

Se definen con el decorador `@abstractmethod` (incluido en el módulo `abc` de python) y son frecuentemente usados para crear interfaces que faciliten la comunicación entre diferentes clases. Vemos un ejemplo a continuación:

</br>

```python
from abc import abstractmethod

class Herramienta:    
    @abstractmethod
    def describir_funcionamiento(self):
        pass
      

class Taladro(Herramienta):
    def describir_funcionamiento():
        print("Esta herramienta sirve para hacer agujeros.")
        
Taladro.describir_funcionamiento() #Esta herramienta sirve para hacer agujeros.
```
</br>



### HERENCIA

La herencia es un proceso mediante el cual se puede crear una clase hija o *child* que hereda de una clase padre o *parent*.
Esto permite que la clase hija acceda a los métodos y atributos definidos por la clase padre. Igualmente una clase hija puede definir sus propios métodos y atributos o incluso sobrescribir los de la clase padre.

Se puede crear una clase hija simplemente pasando como parámetro la clase padre de la que queremos heredar. Vemos un ejemplo de ello a continuación:

</br>

```python
class Animal:
    tamaño = "grande"
    patas = 4
    vuelo = False
    
    @classmethod
    def describir(cls):
        print(f'Este animal es {cls.tamaño}, tiene {cls.patas} patas y {"puede volar" if cls.vuelo else "no puede volar"}.')
    

class Gato(Animal):
    tamaño = "mediano"
    
    
class Pájaro(Animal):
    tamaño = "pequeño"
    patas = 2
    vuelo = True
    
    
Gato.describir() #Este animal es mediano, tiene 4 patas y no puede volar.

Pájaro.describir() #Este animal es pequeño, tiene 2 patas y puede volar.
```

</br>


El proceso de la herencia de clases resulta muy ventajoso porque nos permite ahorrarnos la repetición de código y nos ayuda a tener bien organizadas todas nuestras clases. Facilita el mantenimiento del programa y la implementación de nuevas funcionalidades.

Sin embargo, esto requiere un esfuerzo previo para saber cómo vamos a planificar la herencia entre las diferentes clases. Se debe hacer en función de qué clases se parecen más y por tanto comparten un mayor número de métodos y atributos.

</br>


Podemos ver una comparación práctica de la herencia de clases viendo la clasificación de los distintos organismos que se hace en biología. Cada especie comparte muchas similitudes con otras especies a diferentes niveles. Por ejemplo, dos especies son más parecidas si comparten la familia que si solo comparten el reino.

</br>

![Arquitectura de un aplicación web](/images/biological_classification.png)

</br>


Podemos ver en el siguiente ejemplo el uso de la herencia para definir múltiples clases que comparten parcialmente las misma funcionalidad:
 
</br>

```python
class Invento:
    fecha = "Desconocida"
    inventor = "Desconocido"
    
    def __init__(self, propietario, identificador):
        self.propietario = propietario
        self.identificador = identificador

    def describir(self):
        pass

    def mostrar_datos(self):
        print("Nombre: " + type(self).__name__ + "  Fecha: " + str(self.fecha) + "  Inventor: " + self.inventor)


class Teléfono(Invento):
    fecha = 1876
    inventor = "Alexander Graham Bell"

    def describir(self):
        print("El teléfono es un dispositivo de telecomunicación creado para transmitir señales acústicas a distancia por medio de señales eléctricas.")


class Imprenta(Invento):
    fecha = 1440
    inventor = "Johannes Gutenberg"

    def describir(self):
        print("La imprenta es un método mecánico destinado a reproducir textos e imágenes sobre papel, vitela, tela u otro material.")

    def dato_curioso(self):
        print("La biblia de Gutenberg fue el primer libro impreso de la historia y se imprimió con un total de 42 líneas por cada página.")


class Telescopio(Invento):
    fecha = 1608
    inventor = "Hans Lippershey"

    def describir(self):
        print("El telescopio es un instrumento óptico que permite observar objetos lejanos con mucho más detalle que a simple vista")


teléfono_963 = Teléfono("Museo Metropolitano", "ET-963")
imprenta_120 = Imprenta("Biblioteca Antigua", "GG-120")
telescopio_568 = Telescopio("Planetario Central", "FH-568")


teléfono_963.mostrar_datos() #Nombre: Teléfono  Fecha: 1876  Inventor: Alexander Graham Bell
teléfono_963.describir() #El teléfono es un dispositivo de telecomunicación creado para transmitir señales acústicas a distancia por medio de señales eléctricas.

imprenta_120.mostrar_datos() #Nombre: Imprenta  Fecha: 1440  Inventor: Johannes Gutenberg
imprenta_120.describir() #La imprenta es un método mecánico destinado a reproducir textos e imágenes sobre papel, vitela, tela u otro material.
imprenta_120.dato_curioso() #La biblia de Gutenberg fue el primer libro impreso de la historia y se imprimió con un total de 42 líneas por cada página.

telescopio_568.mostrar_datos() #Nombre: Telescopio  Fecha: 1608  Inventor: Hans Lippershey
telescopio_568.describir() #El telescopio es un instrumento óptico que permite observar objetos lejanos con mucho más detalle que a simple vista
```

</br>


Los métodos de la clases heredadas pueden clasificarse en tres tipos diferentes:

- Heredados directamente de la clase padre: mostrar_datos()
- Heredados de la clase padre pero modificados: describir()
- Creados en la clase hija por lo tanto no existentes en la clase padre: dato_curioso()

</br></br>


Por último cabe mencionar que podemos hacer uso de de la función `super()` desde la clase hija para acceder a los métodos de la clase padre y poder ampliar el constructor. Vemos un ejemplo de ello a continuación:

</br>

```python
class Construcción:
    def __init__(self, altura):
        self.altura = altura
        print(f'Se trata de una construcción {self.altura}.')

        
class Casa(Construcción):
    def __init__(self, altura, material):
        super().__init__(altura)
        self.material = material
        print(f'En concreto una casa de {self.material}.')
 
          
mi_casa = Casa("alta", "piedra")
#Se trata de una construcción alta.
#En concreto una casa de piedra.
```

</br>


### POLIMORFISMO

El término polimorfismo tiene origen en las palabras griegas *polys* (muchos) y *morpho* (formas). Este concepto aplicado a la programación hace referencia a que los objetos de diferentes clases pueden ser accedidos utilizando el mismo interfaz pero que pueden tomar diferentes formas en su respuesta.

Según el principio de polimorfismo podemos llamar a la misma función en diferentes objetos que no pertenecen a la misma clase.
La respuesta a esa llamada debe estar garantizada y ser diferente y específica para cada objeto. Los comportamientos obtenidos deben así ser distintos y "tomar diferentes formas".

Esta característica permite que sin alterar el código existente de un programa se puedan incorporar nuevos comportamientos y funciones aportando así flexibilidad en el diseño del software. Para hacerlo simplemente se agregan nuevas clases cuyo único requisito es que deben tener implementados todos los métodos necesarios usados por el programa.

Una manera fácil de asegurarse de ello es que las diferentes clases hereden de la misma clase padre y que esta tenga métodos abstractos definidos en ella. Esto garantiza que todas las clases hija definan esos métodos y por tanto puedan comunicarse con el mismo interfaz.

</br>


Vemos un ejemplo de todo ello a continuación:

</br>

```python
from abc import abstractmethod

class Forma:   
    @abstractmethod
    def calcular_perímetro():
        pass
      
    @abstractmethod
    def calcular_área():
        pass
      

class Cuadrado(Forma):
    def calcular_perímetro():
        print("Se suman los cuatro lados")

    def calcular_área():
        print("Se multiplica la base por la altura")
        
        
class Triángulo(Forma):
    def calcular_perímetro():
        print("Se suman los tres lados")

    def calcular_área():
        print("Se multiplica la base por la altura y se divide entre dos")


Cuadrado.calcular_perímetro() #Se suman los cuatro lados
Cuadrado.calcular_área() #Se multiplica la base por la altura

Triángulo.calcular_perímetro() #Se suman los tres lados
Triángulo.calcular_área() #Se multiplica la base por la altura y se divide entre dos
```

</br></br></br></br>



###### [Inicio](#checkpoint-08)

<p id="promesas"></p>

## PROMESAS

Las promesas de JavaScript son una herramienta para poder trabajar con código que se debe ejecutar de forma asíncrona. Un caso de uso muy habitual es para pedir archivos a un servidor remoto. El código debe solicitar el archivo y esperar a que el servidor le de una respuesta. Esta respuesta puede ser o no el archivo solicitado. En caso de error el programa debe ejecutar código alternativo.

Las promesas son especialmente idóneas para ese tipo de casos porque son capaces de ejecutarse de forma asíncrona y pueden reaccionar tanto a una respuesta exitosa como a una fallida. 

Una promesa puede estar en uno de los siguientes estados:

- **Pending (Pendiente):** la promesa se encuentra en el estado inicial, ni cumplida ni rechazada
- **Fulfilled (Cumplida):** la promesa se ha completado con éxito
- **Rejected (Rechazada):** la promesa ha fallado

</br>


Todas las promesas se basan en el objeto `Promise` que está predefinido en JavaScript. Para crear una promesa nueva debemos usar la palabra clave `new` seguida de `Promise` y una función que debe aceptar dos argumentos. Estos dos argumentos son dos funciones y suelen tener por convenio los nombres `resolve` y `reject`. La función `resolve` indica que la promesa se cumple y la función `reject` que la promesa no se cumple. 

La función recibe así estos dos argumentos y evalúa en su código si se cumple o no la promesa. Cuando se cumple llama a la función `resolve` pasando como argumento el valor o mensaje deseado. Igualmente, para el caso en que la promesa no se cumple, el código llama a la función `reject` pasando esta vez un error como argumento.

```js
let cumplirPromesa = true;

let miPromesa = new Promise(function(resolve, reject) {
      if (cumplirPromesa) {
            resolve("Promesa cumplida");
      }
      else {
            reject("Promesa rechazada");
      }
});
```

</br>


Todos los objetos `Promise` contienen un método de nombre `then`. Este acepta dos funciones como argumentos, la primera se ejecuta si la promesa se cumple y la segunda si no lo hace. Ambas funciones deben tener un único parámetro que es el valor o error que devolverá la propia promesa al ejecutarse y por convenio es llamado `response` para la primera, y `error` para la segunda.

Al llamar al método `then` comienza la ejecución de la promesa y se prolonga hasta obtener una respuesta.

```js
function ejecutarPromesa(cumplirPromesa) {
      return new Promise(function(resolve, reject) {
            if (cumplirPromesa) {
                  resolve("Promesa cumplida");
            }
            else {
                  reject("Promesa rechazada");
            }
      });
};


ejecutarPromesa(true).then(
      function(response) { console.log("Ejecución normal: " + response) }, //Ejecución normal: Promesa cumplida
      function(error) { console.log("Ha ocurrido un error: " + error) }
);



ejecutarPromesa(false).then(
      function(response) { console.log("Ejecución normal: " + response) },
      function(error) { console.log("Ha ocurrido un error: " + error) } //Ha ocurrido un error: Promesa rechazada
);
```

</br>


Los objetos `Promise` contienen también un método de nombre `catch`. Este método equivale a `then` con la diferencia de que solo recibe la función a ejecutar cuando la promesa no se cumple y por ello siempre se coloca después del método `then`. 

```js
function ejecutarPromesa(cumplirPromesa) {
      return new Promise(function(resolve, reject) {
            if (cumplirPromesa) {
                  resolve("Promesa cumplida");
            }
            else {
                  reject("Promesa rechazada");
            }
      });
};


ejecutarPromesa(false)
      .then(response => console.log("Ejecución normal: " + response))
      .catch(error => console.log("Ha ocurrido un error: " + error)); //Ha ocurrido un error: Promesa rechazada
```

</br>


### ENCADENADO DE PROMESAS

Es posible encadenar varias promesas para que se ejecuten de forma secuencial. Cada promesa devuelve una nueva promesa que se ejecuta tras resolverse la anterior.

```js
let primeraPromesa = new Promise( (resolve) => 
      setTimeout(() => resolve('Promesa 1 cumplida'), 2000)
);

let segundaPromesa = new Promise( (resolve) =>
      setTimeout(() => resolve('Promesa 2 cumplida'), 4000)
);

let terceraPromesa = new Promise( (resolve) => 
      setTimeout(() => resolve('Promesa 3 cumplida'), 6000)
);


primeraPromesa
      .then(response => {console.log(response); return segundaPromesa})
      .then(response => {console.log(response); return terceraPromesa})
      .then(response => {console.log(response)})
      .catch(error => {console.log("hola " + error)});


//CONSOLA:
//Promesa 1 cumplida (tras 2 segundos)
//Promesa 2 cumplida (tras 4 segundos)
//Promesa 3 cumplida (tras 6 segundos)
```

</br>


### OTROS MÉTODOS

Existen otros métodos en el objeto `Promise` que pueden resultar muy útiles en determinadas situaciones.

- `Promise.all()`
- `Promise.allSettled()`
- `Promise.any()`
- `Promise.race()`
- `Promise.resolve()`
- `Promise.reject()`

</br>


#### Promise.all()

El método `Promise.all()` devuelve una promesa que se cumple cuando todas las promesas en el argumento iterable han sido concluidas con éxito, o bien rechaza la petición con el motivo pasado por la primera promesa que es rechazada.

```js
let primeraPromesa = new Promise( (resolve) => 
      setTimeout(() => resolve('Promesa 1 cumplida'), 2000)
);

let segundaPromesa = new Promise( (resolve) => 
      setTimeout(() => resolve('Promesa 2 cumplida'), 4000)
);

let terceraPromesa = new Promise( (resolve) => 
      setTimeout(() => resolve('Promesa 3 cumplida'), 6000)
);


Promise.all([primeraPromesa, segundaPromesa, terceraPromesa])
      .then(response => console.log(response)); //["Promesa 1 cumplida", "Promesa 2 cumplida", "Promesa 3 cumplida"]
```

</br>


#### Promise.allSettled()

El método `Promise.allSettled()` toma un iterable de promesas como entrada y devuelve una única promesa. Esta promesa se cumple cuando todas las promesas del objeto iterable se cumplen y devuelve un *array* con los resultados de cada promesa. Aunque una promesa sea rechazada siempre se terminan de ejecutar el resto antes de dar una respuesta.

```js
let primeraPromesa = new Promise( (resolve, reject) => 
      setTimeout(() => reject('Promesa 1 rechazada'), 2000)
);

let segundaPromesa = new Promise( (resolve) => 
      setTimeout(() => resolve('Promesa 2 cumplida'), 4000)
);

let terceraPromesa = new Promise( (resolve, reject) => 
      setTimeout(() => reject('Promesa 3 rechazada'), 6000)
);


Promise.allSettled([primeraPromesa, segundaPromesa, terceraPromesa])
      .then(response => console.log(response)) //[{status: "rejected", reason: "Promesa 1 rechazada"}, {status: "fulfilled", value: "Promesa 2 cumplida"}, {status: "rejected", reason: "Promesa 3 rechazada"}] (tras 6 segundos)
```

</br>


#### Promise.any()

El método `Promise.any()` toma un iterable de promesas como entrada y devuelve una única promesa. Esta promesa se cumple cuando se cumple al menos una de las promesas del iterable y lo hace con el valor correspondiente. Sin embargo, la promesa es rechazada cuando todas las promesas del iterable son rechazadas y se pasa un objeto `AggregateError` que contiene los diferentes motivos de rechazo.

```js
let primeraPromesa = new Promise( (resolve, reject) => 
      setTimeout(() => reject('Promesa 1 cumplida'), 2000)
);

let segundaPromesa = new Promise( (resolve, reject) => 
      setTimeout(() => reject('Promesa 2 cumplida'), 4000)
);

let terceraPromesa = new Promise( (resolve) => 
      setTimeout(() => resolve('Promesa 3 cumplida'), 6000)
);


Promise.any([primeraPromesa, segundaPromesa, terceraPromesa])
      .then(response => console.log(response)); //Promesa 3 cumplida (tras 6 segundos)
```

</br>


#### Promise.race()

El método `Promise.race()` retorna una promesa que se cumplirá o no tan pronto como una de las promesas del argumento iterable se cumpla o se rechace, con el valor o razón de rechazo de esta.

```js
let primeraPromesa = new Promise( (resolve) => 
      setTimeout(() => resolve('Promesa 1 cumplida'), 4000)
);

let segundaPromesa = new Promise( (resolve) => 
      setTimeout(() => resolve('Promesa 2 cumplida'), 2000)
);

let terceraPromesa = new Promise( (resolve) => 
      setTimeout(() => resolve('Promesa 3 cumplida'), 6000)
);


Promise.race([primeraPromesa, segundaPromesa, terceraPromesa])
      .then(response => console.log(response)); //Promesa 2 cumplida (tras 2 segundos)
```

</br>


#### Promise.resolve()

El método `Promise.resolve()` retorna un objeto `Promise` que es resuelto con el valor indicado.

```js
Promise.resolve("Promesa cumplida")
      .then(response => console.log(response)); //Promesa cumplida
```

</br>


#### Promise.reject()

El método `Promise.reject()` retorna un objeto `Promise` que es rechazado por la razón especificada.

```js
Promise.reject("Ha habido un error")
      .catch(error => console.log(error)); //Ha habido un error
```

</br></br></br></br>



###### [Inicio](#checkpoint-08)

<p id="async-y-await"></p>

## ASYNC Y AWAIT

Las palabras clave `async` y `await` sirven para trabajar de forma sencilla con promesas en JavaScript. Además, el código escrito resulta más fácil de leer y comprender.

</br>


### ASYNC

Al escribir `async` antes de la definición de una función, esta se convierte en asíncrona. Esto implica que la función puede ejecutarse de forma asíncrona y además devuelve una promesa cuando no se hace de forma explícita. 

```js
async function funcionAsincrona() {
      return "Hola Mundo";
};
```

</br>


El código equivalente a una función `async` sería el siguiente:

```js
function funcionAsincrona() {
      return Promise.resolve("Hola Mundo");
};
```

</br>


### AWAIT

Una función `async` nos permite usar la palabra clave `await` dentro de su código. Se debe usar junto con una función que devuelva una promesa y sirve para suspender la ejecución de la función asíncrona mientras se espera a que se resuelva la promesa. Una vez resuelta esta, el código continua la ejecución normal.

```js
function ejecutarPromesa(tiempo) {
      return new Promise(resolve => {
            setTimeout(() => resolve('Promesa cumplida'), tiempo)
      });
};


async function funcionAsincrona() {
      let mensaje = await ejecutarPromesa(2000);
      console.log(mensaje);
}

funcionAsincrona(); //Promesa cumplida (tras 2 segundos)
```

</br>


### USO CON PROMESAS ENCADENADAS

La ventaja de usar `async` y `await` se puede ver claramente en el encadenamiento de promesas. Nos evita la necesidad de configurar explícitamente las cadenas de promesas y controlar el flujo de ejecución de promesas resulta más fácil de hacer. Además el código obtenido es más sencillo y fácil de leer.

```js
function iniciarPromesa(promesa) {
      return new Promise((resolve) => {
            setTimeout(() => resolve(promesa + " cumplida"), 2000)
      });
};


async function ejecutarPromesas() {
      console.log(await iniciarPromesa("Promesa 1"));
      console.log(await iniciarPromesa("Promesa 2"));
      console.log(await iniciarPromesa("Promesa 3"));
};


ejecutarPromesas();


//CONSOLA:
//Promesa 1 cumplida (tras 2 segundos)
//Promesa 2 cumplida (tras 4 segundos)
//Promesa 3 cumplida (tras 6 segundos)
```

</br>


Junto a `async` y `await` podemos usar un bloque `try...catch` para controlar un posible error cuando se rechaza alguna de las promesas.

```js
function iniciarPromesa(promesa, cumplirPromesa) {
      return new Promise((resolve, reject) => {
            setTimeout(() => (cumplirPromesa ? resolve(promesa + " cumplida") : reject(promesa + " rechazada")), 2000)
      });
};


async function ejecutarPromesas() {
      try {
            console.log(await iniciarPromesa("Promesa 1", true));
            console.log(await iniciarPromesa("Promesa 2", true));
            console.log(await iniciarPromesa("Promesa 3", false));
            console.log(await iniciarPromesa("Promesa 4", true));
      }
      catch (error) {
            console.log("ERROR: " + error);
      }
};


ejecutarPromesas();


//CONSOLA:
//Promesa 1 cumplida (tras 2 segundos)
//Promesa 2 cumplida (tras 4 segundos)
//ERROR: Promesa 3 rechazada (tras 6 segundos)
```

</br></br></br>