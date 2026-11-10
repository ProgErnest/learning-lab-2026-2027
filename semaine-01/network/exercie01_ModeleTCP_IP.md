## Tout d'abord qu'est ce que le Modele TCP/IP? 
- Le Modele *TCP/IP* est une evolution du modele OSI dans le sens ou celui-ci ressemble plus concretement a ce qui se passe reellemnt dans les ordinateur la ou le modele OSI agit a des fins de recherche puis resolution des problemes le modele TCP/IP transcrit exactement ce quise passe dans la configuration du reseau.
- **Le Modele OSI** est un ensemble de 7 couches (Physique,Liaison, Reseau, Transport, presentation, session, application) qui regissent les normes de communications entre differents equipements et terminaux au seins d'un reseau informatique.
- **Le Modele TCP** qui est une version simplifiee et concrete du *Modele OSI*(trop theorique) contenant 4 couches (Acces reseau, Internet, Transport, Application)

## Les differentes couches du Modele TCP/IP
### 1. La couche d'acces reseau :
#### Description
    Cette couche est une association des couches physiques et liaisons du Modele OSI son role est d'assurer l'interconnectivite au sein d'un meme reseau local, des equipements physiques via des adresses MAC.
#### Protocole
    Le protocole le plus connu et utilise ici est **Ethernet** qui assure la communication entre equipements par cables ou non filaires en utilisant des adresses MAC  pour transmettre les informations sous formes de trames voir bits au niveau physique pur.
    D'autres protocoles sont aussi reconnus a savoir : Wi-Fi ou PPP ou meme par abus ARP
### 2. La couche Internet 
#### Description
    Cette couche est chargee du routage et l'acheminement des paquets entre differents reseaux afin de garantir une communication IP entre equipements de reseaux differents
#### Protocole
    Le protocole principal est IP(Internet Protocol) qui gere donc l'adressage et le routage des paquets. Il existe en deux versions IPv4 et Ipv6.
    D'autres protocoles sont : 
    - ICMP(Internet Control Message Protocole) pour tester la connectiviter IP entre deux equipements
    - IGMP...

### 3. La couche Transport
#### Description
    Cette couche est chargee du transport de datagrammes ou segments entre de bout-en-bout entre differents equipements via en plus de l'IO des ports pour relier des services.
#### Protocole
    Ici on a deux protocoles populaires et tres souvent utilisees :
    - TCP(Tranmission Control Protocol) qui est un protocole de transport fiable qui garanti au maximum possible l'integrite des communication avec une verification de connectivite entre les equipements(3-ways handshake), le paquet envoye doit etre exactement celui recu via des ackitements, fermeture de la connection
    - UDP(User Datagram Protocol) est un protocole plus rapide que TCP mais qui ne garanti pas l'integrite des donnees

    -QUIC....
### 4. La couche Application
#### Description
    C'est une association des couches presentation session et application du model OSI. Il est le niveau le plus eleve visible et configurable sur les terminaux.
#### Protocoles
    - DNS(Domain Name System) : Il assure la gestion des noms de domaines et leurs resolutions en IP et vis versa
    - DHCP(Dynamic Host Contrl Protocol) : Protocole garantissant l'attribution automatique des adresses IP dans un reseau
    - HTTP(HyperText Transfert Protocol) : Il assure la communication web mode client serveur via des requetes web, fichiers et du code html
    - FTP(File Transfert Protocol) : IL assure le transfert de fichiers
    - SSH(Secure Shell) : qui est protocole permettant via un canal chiffre de manipuler un serveur ou un equipement a distance via des coomandes shell et un transfert de fichiers
    - TLS: protocole garantissant un chiffrement et confidentialite de communications entre equipement et une authentification via des certificats. 
    - HTTPS(HTTP  over TLS/SSL): est une version securisee ou chiffree HTTP garantisant la confidentialite des echanges
    - SMTP(Simple Mail Transfert Procol): Il gere l'envoi des mails
    - POP3(Post Office Protocol) : Pour le telechargementdes couriels(mails)
    - IMAP(Internet Message Acces Protocol): permet de consulter les couriels en ligne
