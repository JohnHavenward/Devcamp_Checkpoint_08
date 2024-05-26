

# PREGUNTAS TEÓRICAS

TODO[¿Qué tipo de bucles hay en JS?](#bucles)</br>
[¿Cuáles son las diferencias entre const, let y var?](#tipos-de-variables)</br>
TODO[¿Qué es una función de flecha?](#funciones-flecha)</br>
TODO[¿Qué es la deconstrucción de variables?](#deconstrucción-de-variable)</br>
TODO[¿Qué hace el operador de extensión en JS?](#operador-de-extensión)</br>
TODO[¿Qué es la programación orientada a objetos?](#programación-orientada-a-objetos)</br>
TODO[¿Qué es una promesa en JS?](#promesas)</br>
TODO[¿Qué hacen async y await por nosotros?](#async-y-await)</br>

</br></br></br></br>




# BUCLES

# TIPOS DE VARIABLES

El tipo de datos contenido por una variable en JavaScript depende del valor asignado, no se define de forma explícita. Sin embargo, al declarar la variable sí debemos especificar de qué tipo de variable se trata. Existen tres tipos disponibles en JavaScript y son los siguientes: 

- `var`
- `let`
- `const`

</br>


Estos tres tipos presentan comportamientos parecidos y son algunas de sus propiedades las que los hacen diferenciarse. Conocer y entender estas diferencias es vital para poder seleccionar el tipo de variable adecuado para cada situación concreta.

</br>


### VAR

Antes de la versión ES6 de JavaScript `var` era el único tipo de variable disponible.

Se declaran con la palabra clave `var` y no es necesario asignar un valor inicial.

```js
var unaVariable = "Llueve";

var otraVariable;
```

<br>


##### REASIGNACIÓN

A una variable de tipo `var` se le pueden reasignar valores tantas veces como se desee.

```js
var miVariable = "Hola mundo";

miVariable = 13;

miVariable = true;
```

</br>


##### REDECLARACIÓN

Una variable de tipo `var` puede declararse múltiples veces en el programa sin causar ningún error.

```js
var miVariable = "Hola mundo";

var miVariable = 13;

var miVariable = true;
```

</br>


> **NOTA:** Esto puede parecer algo ventajoso pero puede generar problemas en el código si sobrescribimos variables de forma no intencionada.

</br>


##### ÁMBITO DE USO

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


##### HOISTING

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


##### REASIGNACIÓN

A una variable de tipo `let` se le puede reasignar un nuevo valor las veces deseadas.

```js
let miVariable = "Hola mundo";

miVariable = 13;

miVariable = true;
```

</br>


##### REDECLARACIÓN

La redeclaración de variables `let` no es posible y hacerlo nos dará error.

```js
let miVariable = [1, 2, 3];

let miVariable; //error
```

</br>


##### ÁMBITO DE USO

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


##### HOISTING

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


##### REASIGNACIÓN

Una variable de tipo `const ` no admite la reasignación de valores y hacerlo nos dará error.
 
```js
const variableConstante = "Valor inicial";

variableConstante = "Valor nuevo"; //error
```

</br>


##### REDECLARACIÓN

La redeclaración de variables `const` no es posible y hacerlo nos dará error.

```js
const variableConstante  = "Valor inicial";

const variableConstante  = "Valor alternativo"; //error
```

</br>


##### ÁMBITO DE USO

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


##### HOISTING

En lo que respecta al *hoisting*, las variables `const` no son inicializadas y por eso no pueden usarse antes de haber sido declaradas.

```js
console.log(variableConstante); //error

const variableConstante = "Valor constante";
```

</br>


### TABLA COMPARATIVA

A continuación se muestra una tabla en la que se comparan las diferentes propiedades de cada uno de los tres tipos de variables disponibles en JavaScript.

</br>


| PROPIEDADES                       |     | `var`                               | `let`           | `const`         |
| :-------------------------------- | --- | :---------------------------------: | :-------------: | :-------------: |
| Necesario inizializar al declarar |     | No                                  | No              | Sí              |
| Reasignación                      |     | Sí                                  | Sí              | No              |
| Redeclaración                     |     | Sí                                  | No              | No              |
| Ámbito de uso                     |     | global y local                      | bloque          | bloque          |
| Comportamiento del *Hoisting*     |     | inicializada como </br> `undefined` | no inicializada | no inicializada |

</br></br></br></br>




# FUNCIONES FLECHA

# DECONSTRUCCIÓN DE VARIABLE

# OPERADOR DE EXTENSIÓN

El operador extensión toma un objeto iterable y expande todos sus elementos permitiéndonos operar con ellos individualmente en vez de como una agrupación. Este operador se representa con tres puntos `...` y siempre se escribe inmediatamente antes del objeto iterable.

```js
const objetoIterable = [1, 2, 3];

const [a, b, c] = [...objetoIterable];
```

```js
const [contenedor] = [1, 2, 3];
```


```js
const primeraParte = [1, 2, 3];
const segundaParte = [4, 5, 6];


const variableCompletaSinSpread = [primeraParte, segundaParte];
const variableCompleta = [...primeraParte, ...segundaParte];


console.log(variableCompletaSinSpread);
//[[1, 2, 3], [4, 5, 6]]

console.log(variableCompleta);
//[1, 2, 3, 4, 5, 6]
```





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




```js
const [a, b, ...resto] = [1, 2, 3, 4, 5];

console.log(resto); //[3, 4, 5]
```




</br></br></br></br>




# PROGRAMACIÓN ORIENTADA A OBJETOS

# PROMESAS

# ASYNC Y AWAIT