Exemple de requete :
```
Frame 18: Packet, 775 bytes on wire (6200 bits), 775 bytes captured (6200 bits)
Ethernet II, Src: Xerox_00:00:00 (00:00:01:00:00:00), Dst: fe:ff:20:00:01:00 (fe:ff:20:00:01:00)
Internet Protocol Version 4, Src: 145.254.160.237, Dst: 216.239.59.99
Transmission Control Protocol, Src Port: 3371, Dst Port: 80, Seq: 1, Ack: 1, Len: 721
Hypertext Transfer Protocol
    […] GET /pagead/ads?client=ca-pub-2309191948673629&random=1084443430285&lmt=1082467020&format=468x60_as&output=html&url=http%3A%2F%2Fwww.ethereal.com%2Fdownload.html&color_bg=FFFFFF&color_text=333333&color_link=000000&color_url=666633&co
    Host: pagead2.googlesyndication.com\r\n
    User-Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.6) Gecko/20040113\r\n
    Accept: text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,image/jpeg,image/gif;q=0.2,*/*;q=0.1\r\n
    Accept-Language: en-us,en;q=0.5\r\n
    Accept-Encoding: gzip,deflate\r\n
    Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7\r\n
    Keep-Alive: 300\r\n
    Connection: keep-alive\r\n
    Referer: http://www.ethereal.com/download.html\r\n
    \r\n
    [Response in frame: 27]
    [Full request URI […]: http://pagead2.googlesyndication.com/pagead/ads?client=ca-pub-2309191948673629&random=1084443430285&lmt=1082467020&format=468x60_as&output=html&url=http%3A%2F%2Fwww.ethereal.com%2Fdownload.html&color_bg=FFFFFF&color]

```
Reponse : 
```
Frame 27: Packet, 214 bytes on wire (1712 bits), 214 bytes captured (1712 bits)
Ethernet II, Src: fe:ff:20:00:01:00 (fe:ff:20:00:01:00), Dst: Xerox_00:00:00 (00:00:01:00:00:00)
Internet Protocol Version 4, Src: 216.239.59.99, Dst: 145.254.160.237
Transmission Control Protocol, Src Port: 80, Dst Port: 3371, Seq: 1431, Ack: 722, Len: 160
[2 Reassembled TCP Segments (1590 bytes): #26(1430), #27(160)]
Hypertext Transfer Protocol
    HTTP/1.1 200 OK\r\n
        Response Version: HTTP/1.1
        Status Code: 200
        [Status Code Description: OK]
        Response Phrase: OK
    P3P: policyref="http://www.googleadservices.com/pagead/p3p.xml", CP="NOI DEV PSA PSD IVA PVD OTP OUR OTR IND OTC"\r\n
    Content-Type: text/html; charset=ISO-8859-1\r\n
    Content-Encoding: gzip\r\n
    Server: CAFE/1.0\r\n
    Cache-control: private, x-gzip-ok=""\r\n
    Content-length: 1272\r\n
    Date: Thu, 13 May 2004 10:17:14 GMT\r\n
    \r\n
    [Request in frame: 18]
    [Time since request: 971.397000 milliseconds]
    [Request URI […]: /pagead/ads?client=ca-pub-2309191948673629&random=1084443430285&lmt=1082467020&format=468x60_as&output=html&url=http%3A%2F%2Fwww.ethereal.com%2Fdownload.html&color_bg=FFFFFF&color_text=333333&color_link=000000&color_url=]
    [Full request URI […]: http://pagead2.googlesyndication.com/pagead/ads?client=ca-pub-2309191948673629&random=1084443430285&lmt=1082467020&format=468x60_as&output=html&url=http%3A%2F%2Fwww.ethereal.com%2Fdownload.html&color_bg=FFFFFF&color]
    Content-encoded entity body (gzip): 1272 bytes -> 3608 bytes
    File Data: 3608 bytes
Line-based text data: text/html (3 lines)
```
14. 
On a une requete HTTP plus haut dans celle-ci on a:
- la methode GET qui est utilisee, 
- l'URI de la ressource demandee
La version de http ici HTTP/1.1
- Le Host qui est nom de domaine du serveur destinataire de la requete http ici c'est pagead2.googlesyndication.com
- User-Agent : qui le canal ou l'outil utilise qui peut etre un navigateur comme dans l'exemple Mozilla
- Accept-Language sont les langages supportee ou preferentiel de l'utilisateur via le canal(navigateur)
- Accept-Encoding: SOnt les encodages supportees
...
VUe qu'on est dans une requete GET generalement on a pas de body ou de corps mais dans cette requete ce sont des parametres qui nt ete injecte dans l'URL

15. Dans la reponse http plus haut on a :
- La version http : 1.1
- Le code de statut : 200 OK. Cet element permet de savoir si tout se passe correctement en general il sont definis par les developpeurs. 2XX Succes, 3XX redirection, 4XX erreur client, 5XX erreur serveur
- Content-Type : Le type de cokntenu de la reponse ici on a text/html on auraait pu avoir une image ou d'autres elements 
- L'encodage du corps de la reponse
- cache control pour le cache ici on a la valeur private qui signifie que l'enregistrement du cache est seulement autorise dans le navigateur du client on peut aussi avoir public ici les serveurs intermediaires peuvent les mettre en cache, max-age la TTL maximale du cache
- La date 
- le contenu au niveau de File Data

16. Comparaisons GET,POST, PUT, PATCH, DELETE
-Idempotence: la meme requete appliquee plusieurs fois donne le me resultat ou effet : GET, PUT, PATCH
- Usages : 
    - GET est utilise pour acceder a une resource sans la modifier (Lecture) exple une page web ,une image, etc.
    - POST est utilisee dans les formulaires generalement pur envoyer des infromations au serveur
    - PUT utilise pour des modifications integrale d'un element(plus utilisees dans des API)
    -PATCH Modification partielle
    - DELETE suppression
- Risques :
    - GET : Aucun cote serveur mais is le serveur n'est pas fiable le client recupere une resource potentiellemnt dangereuse
    - POST : RIsquee car no idempotente
    - PUT : pour modifier un enregistrement il faut carement inscrire les valeures de tous les champs dans le cas contraire elles seront ecrasees
    - PATCH : Moins risquee pour des mises a jour que PUT
    - DELETE : Tres dangereuc si mal gere

17. Fais dans 14

18. En observant des Cookies voici ce que je remarquedans la console du navigateur :
Le Name (variable d'identification du cooie exple id, lang, etc.)
La valeur qui est la valeur de la varaible Name( id =ddfsf)
Expiration : La date precise d'expiration du Cookie
HttpOnly: Si valeur est `true` il est impossible de voir le cookie avec le javascript et donc protection supplementaire contre le XSS
Path : "/" qui donne les uri ou url du site pour lesquelles le cookie est valable si on a  "/" toutes les pages du site peuvent le consulter ou l'utiliser
Domain : le site autorise a recevoir le cookie
SameSite: Ici c'est pour preciser si le cookie peut etre envoye via un lien externe
Secure : Si true le cookie n'est utilisable qu'en hhtps
Taille : la taille en octets du cookie


Lors de la creation/modification des COoie Tout se passe dans la reponse du serveur via l'attribut Set-Cookie dans l'entete http de la requette avec toutes les variables et valuer du Cookie
Lors de la transmission c'est au niveau de la requete : sur l'enregistrement Cookie avec tous les attributs du cookie envoye au serveur
19. 
Le mecanisme de session cote serveur fonctionne ainsi : lorsque l'utilisateur cree un compte ou se connecte, une session est cree avec un identifiant cote serveur et un stockage est cree dans lequel 'identifiant de session est associe aux informations de l'utilisateur et donc renvoyer sous forme de COokkie dans la majeur partie des cas et donc a chaque nouvelle reconnection le navigateur soumet le cookie de session puis le serveur recupere l'identifiant et retrouve ses informations. Ce mecanisme est donc statefull cote serveur et necessite beaucoup de stockage lorsque e nombre d'utilisateurs devient exponetiellement grand ou meme complexe a gerer avec de nombreux serveurs.
Le mecanisme JWT(JsonWeb TOken) ici lorsque l'utilisateur fourni ses identifiants de connection le serveur cree un jeton contenant une signature dans l'entete, un pay load contenant la cke secrete ouis revoit ce je =ton au client qui sera stocke via un cookie ou le localstorage. A chaque requete le serveur recupere le jeton et recalcule la ginature a partir de sa cle secrete et verifie que la signature correspond reelement ou si le jeton est valide. JWT est donc stateless car le serveur ne stocke rien

20.
Le cache est u mecanisme permettant  d'economiser de la bande passante en sauvegardant temporairement des ressources sur le poste du client. Il fonctionne ainsi :
premiere requete le navigateur demande une ressource exmple une page web maintenant le serveur repond avec un enregistrement http Cache-Control si on a max-age=7200  alors le navigateur a pour autorisation de garder la ressource en cache pendant 7200s (plus besoin de la retelecharger pour l'utiliser ou la consulter car les requete seront dirige vers le cache plutot que vers le serveur) apres ce temps la ressource devient obsolete et donc l'acces necessitera une nouvelle requete vers le serveur 
Les validateurs ETag et Last-Modified viennent  regler certaines situation de cache expire mais de ressource similaire :
ETag fonctionne sur le hash du contenu et/ou de sa version tandisque Last-Modified sur la date de modification.

En cas d'expiration du cache:
- Avant celui-ci lors de la mise en cache le serveur fournit Last-Modified ou ETag
- Puis apres expiration le navigateur envoie des attributs If-Modified-Since ou If-None-Match et le serveur compare 
- Repoonse du serveur : encas de non changement un 304 Not Modified est envoye au navigateur dans le cas contraire un 200 OK