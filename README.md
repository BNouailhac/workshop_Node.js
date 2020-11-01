# workshop_Node.js
Workshop pour faire ces premiers pas dans le développement web via le langage node.js

----------------------------
## Qu'est-ce que Node.js ?
Node.js est une plateforme logicielle libre en JavaScript orientée vers les applications réseaux. Durant ce workshop nous allons nous concentrer sur la création de serveur Http pour du web.

----------------------------
## 1. étape :
Commençons par préparer notre projet :

- Premièrement installer Node.js sur votre plateforme (https://nodejs.org/en/).

![https://nodejs.org/en/](https://github.com/BNouailhac/workshop_Node.js/blob/main/img/Site_install.png)

- Une fois cela fait, nous allons créer notre premier fichier node.js, nommons le "my_node.js".

----------------------------
## 2. étape :
Nous venons de créer notre premier fichier, maintenant nous allons créer notre premier programme Node.js en faisant un Hello word:

- tout d'abord on fait un include de module:
```
var http = require('http');
```
> on inclue un module en faisant 'require()', on inclue 'http' qui va nous permettre de créer un serveur http avec la variable http.

- Votre application a désormais accès au module HTTP et est capable de créer un serveur comme ceci :
```
http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/html'});
  res.end('Hello World!');
}).listen(3000);
```
> Ce code va donc créer un serveur qui affiche le résultat de la fonction qui lui est mis en paramètre et qui sera héberger sur le port 3000 localhost de votre ordinateur. 'req' et 'res' les arguments de la fonction sont respectivement les requêtes envoyer par le client au serveur et la réponse que fait le serveur au client.

----------------------------
## 3. étape :
Lançons notre premier programme maintenant faite ```node my_node.js``` et ouvrer http://localhost:3000/ dans votre navigateur pour voir le résultat.

![Résultat hello world](https://github.com/BNouailhac/workshop_Node.js/blob/main/img/R%C3%A9sultat_hello_world.png)

----------------------------
## 4. étape :
Allons plus loin maintenant et programmons notre propre module:

- On va créer un nouveau fichier pour notre module 'my_module.js' et écrire cette fonction qui renvoi la date dedans :
```
exports.myDateTime = function () {
  return Date();
};
```
> Attention le 'exports' est très importants c'est ce qui fait que la fonction sera récupérable dans notre fichier 'my_node.js'.

----------------------------
## 5. étape :
Maintenant utilisons le dans notre fichier 'my_node.js' comme cela :

- On rajoute l'appel du module en haut du fichier : ```var dt = require('./my_module'); ```
- Et on change notre serveur pour appeler la fonction de notre module :
```
http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/html'});
  res.write("The date and time are currently: " + dt.myDateTime());
  res.end();
}).listen(3000);
```
> Lancez le programme pour vérifier si cela a bien fonctionné.

![Résultat my_module](https://github.com/BNouailhac/workshop_Node.js/blob/main/img/R%C3%A9sultat_my_module.png)

----------------------------
## 6. étape :
Voyons ensemble une dernière chose avant de finir la gestion des évènements :

- Faisons un fichier à part pour tester cela 'my_event.js' et écrivons se code à l'intérieur :
```
var events = require('events'); // on appell le module responsable des évènements

var eventEmitter = new events.EventEmitter(); //on initialiser notre utilisateur d'évènement.

var myEventHandler = function () {
  console.log('I hear a scream!');
}

eventEmitter.on('scream', myEventHandler); // appel la fonction 'myEventHandler' si un scream est réceptioné

eventEmitter.emit('scream'); // envoi un scream.
```
> ici nous n'avons pas programmé de serveur mais un simple code qui pour terminal à tester comme auparavant en faisant 'node my_event.js' pour avoir ce résultat :

![Résultat Event](https://github.com/BNouailhac/workshop_Node.js/blob/main/img/R%C3%A9sultat_Event.png)

----------------------------
## 7. étape :
Ce sera tout pour ce worshop mais n'hésitez pas à continuer de votre côté directement à partir de la documentation officielle : https://nodejs.org/en/docs/ .

