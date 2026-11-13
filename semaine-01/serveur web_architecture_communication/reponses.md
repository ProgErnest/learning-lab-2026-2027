Exercie26:
Une capture locale via l'interface loop back a ete lancee pour verifier les communications avec mon serveur local sous Ubuntu d'une application Django au port 8001 donc j'ai affiche l'interface de connection puis entre certains parametres de connection puis validees

Exercice 27 : Reverse Proxy architecture e tproxy
C'est quoi un reverse Proxy ?
Un reverse Proxy est donc un intermediaire en tre un serveur web et les requetes venant du web qui  permet de gerer kes terminaisons tls, le routage des requetes, masquer l'architecture interne du serveur, gerer les fichiers statiques et meme les connection lentes, loadbalancing et ;a haute dispo, le cache, compression et optimisation du reseau.

#### Differences entre un serveur implementant cela et un seveur nue
Sans reverse proxy, l'architecture du serveur est mis a nu face au personnes malveillantes et donc le serveur proxy est une surcouche de protection reseau (ip, ports, etc.) face a ces dangers de securie
Sans reverse proxy la gestion de tls, des routage et repartition entre serveurs devient couteuse en ressources car les langages ou framework utilisees pour le web sont beaucoup moins performant que ceux avec lesquels les reverse proxy sont developpe et auss pour des bespons de centralisation

Ecxercice 28 : 
J'ai demarre un serveur Django sur mon pc puis effectue une action et capture dans wireshark. 
Pour l'analyse j'ai decouvert qu'on pouvait analyser cette requete a plusieurs nniveaux: 
- Au niveau du client via l'onglet Network des outils de developpements ou l'on peut consulter la liste des requetes et des reponses du serveur,  tout en ayant une vue complete des entetes http et elrus valeurs et meme des delais
- Au niveau du serveur DJango via ses logs qui liste les requetes recues etles codes de reponse

Bref : Le client envoie une requete web que le sserveur / l'application backnd repond via http

Exercice 29 : 
Le CORS: Cross Origin ressource Sharing estt un mecanisme d'assouplissement de la barriere SOP(Same Origin Policy ) des navigateur ( le SOP empche tout site ou service A de communiquer ou d'exploiter les ressources d'un site ou service B) en permettant aux deux sites de communiquer via un mecanisme d'autorisation explicite dans les entetes http.
Requete SImple vs Prefligth on a vu plus haut que les requetes simples  suivent un mecanism e en deux temps requete (GET ou POST) reponse du serveur en http or dans des mmecanismes plus complexes impliquants d'autres methoodes http risquees telles que PUT, PATCH ou `DELETE` ou meme des requetes en JSON Le navigateur utilise des requetes pleflight (OPTION) via la methode http OPTION pour demander au serveur s'il peut  ou s'il a l'autorisation d'executer la requete. puis le serveur repond. DNa s le ca sd'une reponse positive, le navigateur envoie maintenant la requete et dans le cas contraire il ne fait rienr