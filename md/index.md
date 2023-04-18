# JavaScript bàsic

## Inclusió de JavaScript en HTML

 Podem incloure el codi JavaScript dins del codi HTML amb l'etiqueta `<script>`:

```html 
<!DOCTYPE html>
<html>
    <head>
        <script>            
            document.getElementById("missatge").innerHTML = "Hola món";           
        </script>
    </head>
...
```

L'etiqueta `<script>` pot anar dins de `<head>` o dins de `<body>`, però és preferible posar-la al final de `<body>` per tal d'accelerar la càrrega de la pàgina:

```html
...

<body>

...

    <script>        
        document.write("Hola món");
    </script>

</body>
</html>
```

> És possible tindre vàries etiquetes `<script>` en un document HTML.

També podem incloure codi JavaScript directament en el codi HTML, com a valor  d'un atribut. Generalment s'utilitza per a associar un esdeveniment, com el clic d'un botó, a una acció JavaScript:

```html
<button type="button" onclick="document.write('Hola món');">Saludar</button>
```

Però la forma més usual d'incloure codi JavaScript és per mitjà d'arxius externs. Això té l'advantatge de que el mateix codi és accessible per vàries pàgines: 

```html
<script src="scriptExtern.js"></script> 
```

> Els scripts en arxius externs solen tindre l'extensió **.js** i no s'escriuen entre etiquetes `<script>`.

## Eixida de dades

Hi ha vàries formes de mostrar dades amb Javascript.

### Amb `document.write`

```html
<!DOCTYPE html>
<html>
<body>

    <script>
        document.write("<h1>Hola món</h1>");
    </script>

</body>
</html>
``` 

> Aquest mètode escriu directament al document HTML. Si s'invoca una vegada ja s'ha carregat la pàgina, esborrarà tot el contingut HTML.
>
> Es recomana usar aquest mètode només per a testing.

### Accedint als element pel seu ID

Consisteix en associar un id a l'element HTML en què volem mostrar la informació, accedir a ell amb el mètode **`document.getElementById`** i canviar el seu HTML intern (propietat ***innerHTML***):

```html
<body>

    <p id="missatge"></p>

    <script>
        document.getElementById("missatge").innerHTML = "Hola món";
    </script>

</body>
</html>
```

### Amb `window.alert`

El mètode `window.alert` mostra un diàleg d'alerta:

```html
<button type="button" onclick="window.alert('Hola món')">Saludar</button>
```

Es pot omitir l'objecte `window`:

```html
<button type="button" onclick="alert('Hola món')">Saludar</button>
```

Aquest mètode no s'utilitza molt en l'actualitat, ja que es considera que mostrar aquest tipus de diàlegs és intrusiu.

### Eixida per consola

Amb `console.log()` podem escriure directament a la consola del navegador. Aquesta opció és útil per a depurar:

```html
<script>
    console.log("Hola món");
</script>
```

## Lectura de dades

La forma més normal de llegir dades de l'usuari amb JavaScript és per mitjà d'**inputs de formularis**. Generalment accedim a l'input pel seu **id** i llegim el valor introduït per l'usuari (**value**):

```html
<form>
    <input type="text" name="nom" id="nom">
    <button type="button" onclick="alert('Hola ' + document.getElementById('nom').value);">Enviar</button>
</form>
```

També podem utilizar el mètode `window.prompt`:

```html
<body>
    <p id="missatge"></p>    
    <script>
        nom = window.prompt("Com et diuen?");
        document.getElementById('missatge').innerHTML = "Hola " + nom;
    </script>
</body>
```

## Sintàxi bàsica

Cada sentència finalitza mb un punt i coma (**`;`**):

```javascript
alert('Hola');
alert('Món');
```

A l'igual que en altres llenguatges, es recomana escriure una sentència per línia.

> El punt i coma no es obligatori escriure'l si escrivim una sentència per línia, però es recomana fer-ho.

### Comentaris

JavaScript admet comentaris d'una línia i de vàries línies:

```javascript
//Aquest és un comentari d'una línia
//Aquest és un altre comentari d'una línia

/* Aquest és
un comentari
de vàries 
línies*/
```

## Variables

Les variables es declaren amb la paraula reservada `let`:

```javascript
let nom; //Declaració sense assignació
let edat = 15; //Declaració amb assignació
```

Una vegada declarada una variable, es pot accedir a ella i modificar el seu contingut:

```javascript
let missatge;
missatge = "Hola";
console.log(missatge); //mostra 'Hola' per consola 
```

Els noms de les variables només poden incloure lletres, dígits o els símbols `$` i` _`. El primer caràcter no pot ser un dígit.

```javascript
//Noms vàlids:
let nomAlumne;
let a123;
let _edat;
let $;
let _;

//Noms no vàlids:
let nom-alumne;
let 1abc;
```

### Constants

Les constants són variables a les quals s'assigna un valor en el moment de la seua creació i aquest no pot ser modificat:

```javascript
const GRAVETAT = 9.8;
```

## Tipus de dades

JavaScript és un llenguatge **dinàmicament tipat**, el que significa que una variable pot tindre un valor d'un tipus i després tindre un valor d'un tipus diferent.

JavaScript té un nombre molt reduït de tipus de dades: numèriques, cadenes de caràcters i booleanes.

### Number

Representa números enters i amb decimals.

```javascript
let edat = 51;
let area = 4.56;
```

### String

Representa cadenes de caràcters. Es pot escriure amb cometes simples, dobles o invertides. 

```javascript
let cad1 = "Hola";
let cad2 = 'Món';
let cad3 = `El valor de cad1 és: ${cad1}`;
```

Les cometes invertides permeten interpretar variables i operacions dins dels  delimitadors `${ }`.

### Boolean

Les variables booleanes poden tindre els valors true o false. Generalment guarden el resultat d'una comparació.

```javascript
let casat = false;
let actiu = true;
```

### Altres valors

Quan una variable ha sigut declarada però no se li ha assignat cap valor, té el tipus **`undefined`**:

```javascript
let nom;
console.log(nom); //Mostra undefined
```

El valor **`null`** s'utilitza per a representar valors inexistents o desconeguts:

```javascript
let alumne = null;
console.log(alumne); //Mostra null
```

El valor **`Infinity`** s'obté al dividir un número entre 0:

```javascript
console.log(1 / 0); //Mostra Infinity
```

El valor **`NaN`** significa **Not a Number**. S'obté quan una operació dónaria un resultar matemàtic erroni:

```javascript
console.log("Hola" / 2); //Mostra NaN
```

### L'operador `typeof`

L'operador `typeof` retorna un string amb el tipus de la variable o del valor que escrivim a continuació:

```javascript
let nom = "Pepa";
let edat = 15;
let actiu = true;
console.log(nom); // Mostra "string"
console.log(edat); // Mostra "number"
console.log(actiu); // Mostra "boolean"
console.log(nom / edat); // Mostra NaN
```

## Operadors matemàtics

Els operadors matemàstics bàsics són la **suma**, **resta**, **multiplicació** i **divisió**. A ells podem afegir els operadors de **mòdul** (calcula el residu de la resta entera) i l'operador d'**exponenciació**. Els seus símbols són:

* Suma: **`+`**,
* Resta: **`-`**,
* Multiplicació: **`*`**,
* Divisió: **`/`**,
* Mòdul: **`%`**,
* Exponenciació: **`**`**

Exemples:

```javascript
console.log(8 % 3) // 2
console.log(2 ** 3) // 8
```

També tenim altres operadors unaris com la negació (**`-`**).

```javascript
let num = 5;
console.log(-num) // -5
```

### Concatenació de strings

L'operador binari `**+**` usat amb cadenes, torna la concatenació de les 2 cadenes. Si un dels 2 operands és una cadena, conveteix l'altre operand en cadena i els concatena.

```javascript
let cad1 = "Hola ";
let cad2 = "Món";
let num = 5;
let bool = true;

console.log(cad1 + cad2); // "Hola Món"
console.log(cad1 + num); // "Hola 5"
console.log(cad1 + bool); // "Hola true"
```

### Assignació

L'operador assignació `**=**` significa que s'assigna a la variable de la part esquerra de l'operador, el valor resultat d'avaluar la part dreta:

```js
let num = (3 + 4) * 2;
console.log(num); // 14
```

### Increment, decrement i operadors abreviats

L'**increment** **`++`** augmenta el valor d'una variable en 1. El **decrement** **`--`** disminueix el seu valor en 1:

```js
let num = 1;
num++;
console.log(num); // 2
num--
console.log(num); // 1
```

Aquests 2 operadors es poden usar darrere de la variable (**post-increment** o **post-decrement**) o davant (**pre-increment** o **pre-decrement**). La diferència és que amb els operadors **post**, primer s'avalua el valor de la variable i després es modifica, mentre que amb els operadors **pre**, primer es modifica i després s'avalua:

```js
let num = 1;
console.log(num++); // 1
let num2 = 1;
console.log(++num); // 2
```

També tenim els operadors abreviats com en altres llenguatges, que combinen una operació aritmètica amb una assignació:

```js
let num = 1;
num += 5; // num = num + 5
console.log(num); // 6
```

Els operadors abreviats són: **`+=`**, **`-=`**, **`*=`**, **`/=`**, **`%=`**, **`**=`**.


### Precedència d'operadors

Si una operació té més d'un operador, el seu ordre de prioritat es defneix generalment amb les mateixes regles que coneixem de matemàtiques.

En la següent taula es mostren els valors de precedència que té cada operador, a major valor major precedència:

| Precedència| Nom | Signe |
|------------|------|------|
| 16 | post-increment | `.. ++` |
| 16 | post-decrement | `.. --` |
| 15 | pre-increment | `++ ..` |
| 15 | pre-decrement | `-- ..` |
| 15 | negació unaria | `-` |
| 14 | exponenciació | `**` |
| 13 | multiplicació | `*` |
| 13 | divisió | `/` |
| 13 | mòdul | `%` |
| 12 | suma | `+` |
| 12 | resta | `-` |
| 2 | asignacions | `=`, `+=`, etc.|

A l'igual que en matemàtiques, si 2 operadors tenen la mateixa precedència, s'avaluen d'esquerra a dreta i els **parèntesis** poden modificar la preferència agrupant operacions.

## Operadors de comparació

Els operadors de comparació retornen un valor **booleà**. Són els següents:

| Operador | Descripció |
|------------|------|
| ==  | 	igual |
| ===  | 	igualtat estricta (mateix valor i mateix tipus) |
| != 	 | distint |
| !==  | 	desigualtat estricta (distint valor i distint tipus) |
| >  | 	major |
| <  | 	menor |
| >=  | 	major o gual |
| <=  | 	menor o igual |
| ?  | 	operador ternari |

En comparar valors de diferents tipus, JavaScript converteix els valors a números:

``` js
console.log( '1' > 0 ); // true, la cadena '1' es converteix en el número 1
console.log( '01' == 1 ); // true
```

Per a valors booleans, `true` es converteix en `1` i `false` en `0`.

``` js
console.log( true == 1 ); // true
console.log( false == 0 ); // true
```

L'operador d'igualtat estricta comprova els valors sense convertir els tipus:

``` js
console.log( 0 === false ); // false
console.log( '01' == 1 ); // false
```

## Sentencies condicionals

Les **sentències condicionals** s'utilitzen quan volem trencar l'estructura seqüencial del codi. Ens permet fer salts a altres parts del codi depenent d'unes determinades condicions.

### if - else

La sentència **`if (...)`** avalua l'expressió booleana entre els parèntesis i executa el bloc de codi a continuació si el resultat de l'expressió és `true`:

``` js
let edat = 18;

if (edat >= 18) {
    console.log("Eres major d'edat");
}
```

Podem afegir la sentència **`else`** per a que s'execute un bloc de codi alternatiu si l'avaluació de l'expressió entre parèntesis és `false`:

``` js
if (edat >= 18) {
    console.log("Eres major d'edat");
} else {
    console.log("Eres menor d'edat");
}
```

Si tenim més d'una condició, podem utilitzar **`else if`** per a avaluar-les totes:

``` js
if (edat < 0) {
    console.log("Encara no has nascut!");
} else if (edat < 18) {
    console.log("Eres menor d'edat");
} else {
    console.log("Eres major d'edat");
}
```

### Operador ternari **`?`**

L'**operador ternari** s'utilitza per a simplificar una expressió `if else`. És especialment útil en assignacions.

Per exemple, el següent codi:

``` js
let missatge = edat >= 18 ? "Eres major d'edat" : "Eres menor d'edat";
console.log(missatge);
```

Seria l'equivalent a:

``` js
let missatge;

if (edat >= 18) {
    missatge = "Eres major d'edat";
} else {
    missatge = "Eres menor d'edat";
}

console.log(missatge);
```

### Operadors lògics

Els **operadors lògics** són:

| Operador | Valor | Descripció |	Exemple `(x = 5; y = 2;`) |
|------------|------|------|------|
| `&&`  | `and`  | `true` si les 2 expressions són `true`	| `(x < 6 && y > 1) // true` 	 |
| `\|\|`  | 	`or`  | `true` si almenys una de les 2 expressions és `true`	|	`(x == 4 \|\| y == 1) // false` 	 |
| `!`  | 	`not` 	 | Negació de l'expressió | `!(x == 5) // false` |

Aquests operadors poden combinar-se en vàries expressions, tenint en compte que l'odre de precedència és:

**`NOT > AND > OR`**

Per exemple:

``` js
let x = 6, y = 2, z = 0;
if (x > 5 && (y == 2 || z != 0) && !(z < 1)) // true
```

### `switch - case`

La sentència **`switch - case`** és similar a l'estructura `if - else if - else` i s'utilitza per a simplificar aquesta quan tenim moltes condicions:

``` js
switch(condicio) {
  case 'valor1':  // if (condicio === 'valor1')
    ...
    break;

  case 'valor2':  // if (condicio === 'valor2')
    ...
    break;

  default:
    ...
    break;
}
```

Els valors poden ser numèrics o cadenes.

La condició s'avalua sempre amb l'**operador d'igualtat estricta `===`**.

La sentència **`break`** causa l'eixida de l'estructura `switch`. No és necessària, però en general s'utilitza ja que una vegada es compleix la condició, el `case` que coincideix amb aquesta actua com a punt d'entrada, execuntatn-se les instruccions de tots els case a continuació d'aquest. Per exemple:

```js
let x = 0;
switch (x) {
  case 0:
    num = "Zero";
  case 1:
    num = "U";
  case 2:
    num = "Dos";
    break;
  case 3:
    num = "Tres";
    break;
}

console.log(num) // "Dos"
```

En aquest codi si `x` val 0 o 1 el valor mostrat seria `"Dos"` ja que no tenim una sentència `break` per a eixir del `switch`.

Per últim, la sentència **`default`** s'utilitza per a executar codi quan la condició no coincideix amb cap `case`. Si `default` està al final del `switch`, no és necessari el `break`.