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