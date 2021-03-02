# JS-Front-CouteauSuisse_MD



## Nos objectifs principaux en front

- Cibler un élement
  - `document.getElementById('selector')` 
  - `document.querySelector('.selector')`
  - `document.querySelectorAll('.selector')`
  - `element.previousElementSibling`
  - `element.nextElementSibling`
  - `element.closest('.selector')`
- Créer des élements
  - `document.createElement('div')`
  - `template.content.cloneNode(true)`
- Modifier des élements
  - `element.textContent`
  - `element.classList`
  - `element.style`
  - `element.setAttribute('nom', 'valeur')`
- Récupérer la valeur d'un attribut 
  -`element.getAttribute('nom')` 
- Insérer des élements
  - `parent.appendChild(enfant);`
  - `parent.prepend(enfant);`
  - `voisin.before(nouveauVoisin);`
  - `voisin.after(nouveauVoisin);`
- Retirer des élément
  - ``A remplir: removeChild, remove`` 
- Réagir à un événement
  - `element.addEventListener('click', funtion() {});`
  - `element.addEventListener('submit', funtion() {});`
  - `element.addEventListener('dblclick', funtion() {});`
- Récupérer les valeur d'un fomulaire
  - `inputElement.value`
  - `new FormData(formElement);`
    - Manipuler le formData
      - `FormData.append(`name`, valeur)`
      - ` FormData.get(`name`)`


- Utiliser le DOM pour écrire une donnée
  - les attributs custom data-*suffix* ou _dataset_
```js
// on prefixe nos attributs custom avec data-
// Ainsi ils seront automatiquement repris dans la propriété dataset de l'element dans un objet avec chaque propriété en camelCase
// <input data-test="toto" data-list-id="4"
document.querySelector('input').dataset; 
/* nous donne
{
  test: "toto",
  listId: "4",
}
*/
```
- Faire des requêtes HTTP en ajax
  - `fetch()`

## Exemples de fetch

### Par défaut, du get

```js
fetch('http://monapi.com/faitqqch');
```

### Possible de spécifier la méthode (POST, PATCH, PUT, ...)

On passe en 2nd argument un objet spécifiant la méthode et le corps de la requete

```js
fetch('http://monapi.com/faitqqch', {
  method: 'POST',
  body: data
});
```

### Utilisation de la valeur de retour

On travaille dans une fonction asynchrone pour pouvoir attendre le retour de nos promesses

```js
const fetchSomething = async function() {
  const response = await fetch('http://monapi.com/faitqqch');
  const body = await response.json();
  if (response.status === 200) {
      console.log(body);
  }
  else {
      console.error('Il y a eu un problème');
  }
}
```

### Gestion des erreurs avec try/catch

S'il y a eu un soucis l'api ne renverra peut etre pas nos données mais un message d'erreur. On peut alors jeter une erreur pour réagir de manière adapter

```js
const fetchSomething = async function() {
  try {
    const response = await fetch('http://monapi.com/faitqqch');
    const body = await response.json();
    if (response.status === 200) {
      console.log(body);
    }
    else {
      throw new Error(body);
    }
  } catch(error) {
    alert('Il y a eu un soucis');
    console.error(error);
  }
}
```
