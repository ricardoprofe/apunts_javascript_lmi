# Validació de formularis

En aquest apartat veurem la validació de les dades introduïdes en formularis HTML. Cal recordar que l'estàndard **HTML5** ja proporciona un validació bàsica per a alguns tipus de inputs (`type="email"`, `type="number"`, etc) així com altres restriccions (`maxlength`, `min`, `max`, `required`, etc). Però en aquests apunts farem tota la validació amb codi JavaScript, per tant el tipus dels inputs serà `type="text"` i no usarem cap altra restricció.

## Validació bàsica

El primer pas serà validar les camps requerits. Això es pot detectar si el valor introduït és igual a la cadena buida (`""`).

Per exemple, si tenim el següent formulari:

```html
<form action="#" onsubmit="">
    <label for="nom"><strong>Nom</strong></label>
    <input type="text" name="nom" id="nom">

    <button type="button" onclick="validar()">Enviar</button>
</form>
```

La funció `validar()` validaria que el `input` **nom** no és buit:

```javascript
function validar() {
  let nom = document.getElementById("nom").value;
  if (nom == "") {
    alert("El nom no pot estar buit");
  }
}
```

L'ús de `alert` no és recomanat per a mostrar informació a l'usuari. Al seu lloc és millor fer-ho mostrant el text de l'error al costat, dalt o baix de l'input. Per a això podem usar un element de text que inicialment estarà buit i on podrem mostrar el text de l'error:

```html
<form action="#" onsubmit="">
    <label for="nom"><strong>Nom</strong></label>
    <input type="text" name="nom" id="nom">
    <span class="error" id="nomErr"></span><br>

    <button type="button" onclick="validar()">Enviar</button>
</form>

<script>
function validar() {
  let nom = document.getElementById("nom").value;
  if (nom == "") {
    document.getElementById('nomErr').innerHTML = 'Camp requerit';
  }
}
</script>
```

En aquest exemple estariem mostrant l'error dins del `span` amb `id` *"nomErr"*. Las classe *"error"* ens servirà per a assignar un estil CSS a tos els missatges d'error.
