### Set Up:
- Login en la [pagina de firebase](https://console.firebase.google.com) y crear aplicación.

### Run:
1. Se instala el cliente de firebase (para usarlo desde la consola).
```
npm install -g firebase-tools
```
1. Inicializamos el proyecto en firebase.
```
firebase login
firebase init
```
1. Si no queremos usar el public directory ponemos esto en el firebase.json.
```
{
  "hosting": {
    "public": "./",
    "ignore": [
      "firebase.json",
      "**/.*",
      "**/node_modules/**",
      "functions"
    ]
  }
}
```
1. Configuramos firebase para que funcione en el index.html.
```javascript
var config = {
    apiKey: "AIzaSyCenq79TaadFmKLx1XkQ2KwuJ_klBOwAjs",
    authDomain: "proyecto-presentacion.firebaseapp.com",
    databaseURL: "https://proyecto-presentacion.firebaseio.com",
    storageBucket: "proyecto-presentacion.appspot.com",
    messagingSenderId: "866855153681"
};
firebase.initializeApp(config);
```
1. A trabajar.
```
firebase serve
```

### How-To:

#### Crear una nueva entrada:

1. Generar Key:
```javascript
firebase.database().ref().child('nombre de la child').push().key;
```
2. Guardar los datos:
```javascript
var updates = {};
updates['/nombre de la child/' + la key] = la info a postear;
```
3. Actualizar la DB:
```javascript
firebase.database().ref().update(updates);
```

#### Cargar entradas:
```javascript
firebase.database().ref('/nombre de la child/').once('value').then(function(response) {
  console.log(response.val());
});
```
