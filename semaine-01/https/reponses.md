Exercice21
- Le chiffrement Symetrique est une methode de chiffrement utilisant une cle secrete pour la communication entre deux individus son avantage est sa rapidite ses inconvenients sont la non garantit de l'authenticite de l'auteur et le fait de devoir partager la cle secrete entre les deux individus Algorithmes populaires DES(obsolete), AES
- Le chiffrement Asymetrique qui est beaucoup plus robuste que celui sysmetrique car il est base sur deux cle donc une cle prive(pour dechiffrer les messages), une cle publique pour leurs chiffrer et donc cette methode garanti donc la confidentialite de maniere partielle mais reste fragile face MTITM tout comme le chiffrement symetrique et est beaucoup trop couteuse en ressources de calculs. RSA, ECC
- Le Hachage qui est une methode de cryptographie a sens unique et donc impossible de dechiffrer un message hache. il garanti donc l'integrite des donnees car un message a une meme empreinte de taille fixe.MD5(Obsolete),SHA-256,3
- La signature numerique qui combine la cryptographie symetrique au hachage et donc un hash de document est chiffree avec la cle privee de l'emeteur donc garnntissant en plus de la confidentialite et de l'integrite, l'authenticite de l'emetteur.

## Exercice 22: Echange de Diffie-Hellman
Imaginons que deux Personnes A et B souhaitenet communiquer et ne veulent pas echanger la cle secrete de communication. Une methode rend ceci possible DIffie-Hellman qui fonctionne comme suit : Le premiere echange (de synchronisation ou de reconnaissance) il s'echangent des cle publiques avec des mots ou nombres  puis deduidsent de ceux- ci la meme cle secretesans toute fois avoir commmunique la meme cle secrete. SOn fonctionnement mathematique est le suivant :
- 1er echanges les deux s'echangent des cles publiques qu'on appellera KA pour A et KB pour B qu'ils ont choisit aleatoirement, deux nombre `p` et `g` tels que  ``` p est premier et g<=p```.
NB: Les cles publiques sont obtenues par les formules du genre ${KA} \equiv  g^{kA} [p]$
- 2e vue que les cle publiques et priveees sint donc liees mathematiquement, on peut donc contineur au prochain echange : chacun va effectuer es calculs avec sa cle privee pour deduire la cle secrete des prochains echanges ${ks} \equiv {KA}^{kB}[p]$ $(=)$ $ks \equiv {KB}^{kA}[p]$ 

### ECDHE (Elliptic Curve Diffie-Hellman Ephemeral)
Cette methode est une evolution de celle de Diffie-Hellman dans le sens ou elle utilise des courbes Elliptiques plutot que de simples fonction modulaires et don per met d'avoir des cle plus petites et donc moins gourmande en ressources tout en garantisaasnt un niveau de securite similaire. Deplus le cote Ephemere garanti que meme si l'attaquant retrouve la cle priveede l'un il ne pourra pas lire les discussions precedentes car pour chaque connection/synchronisation ou discussion, la cle utilisee est supprimee ou ouliee definitivement en fin de session donc apres une nouvelle session une nouvelle cle est utilisee


## Exercice 23 
 Si un attaquant intercepte le tout premier échange Diffie-Hellman pour s'interposer (attaque de l'homme du milieu ou MitM), les mathématiques seules ne permettent pas de savoir à qui on parle réellement. Pour résoudre ce problème, le protocole TLS s'appuie sur des certificats X.509 et une chaîne de confiance.
Lors de la poignée de main TLS (TLS Handshake), le client vérifie l'identité du serveur grâce aux certificats des Autorités de Certification (CA) racines préinstallés dans son navigateur. Il utilise la clé publique de la CA pour vérifier la signature numérique figurant sur le certificat du serveur. L'Autorité de Certification agit ainsi comme tiers de confiance garantissant la légitimité du certificat.
Une fois le certificat validé, le client en extrait la clé publique du serveur. Pour bloquer toute attaque MitM, le serveur signe les paramètres de l'échange Diffie-Hellman avec sa clé privée (qu'il est le seul à détenir), et le client vérifie cette signature à l'aide de la clé publique du certificat. Cela garantit l'authenticité du serveur avant de lancer la communication chiffrée.
Un certificat X.509 est constitué notamment de :
- La clé publique du serveur ;
- Le domaine principal (Subject / Common Name) et les sous-domaines associés (Subject Alternative Names - SAN) ;
- Le nom et les références de l'Autorité de Certification émettrice (Issuer) ;
- L'algorithme de signature utilisé par la CA ;
- La période de validité (dates de début et d'expiration) ;
- La signature numérique de l'Autorité de Certification. »


Pour continuer nous allons analyser vle reusltat Openssl vers github.com
On a dans la reponse plusieurs sections
dont une pre section avec les depth=x et donc plus x est eleve plus il est eleve dans la chaine de certification et donc le maximum est donc l'autorite de certification reconnue par le navigateur ou le SE (AUtorite racine) avec leur subject
- Puis on a la section concernat la chaine de certification qui precise  a chaque niveau :
    - Le subject avec le Common Name (CN), C reconnu par le petit `s`
    - `i` (issuer) qui est l'intermediaire de certification avec son subject ou dans d'autre cas l'autorite qui deleivre le certificat en cours du niveau
    - `a` qui concerne l'algorithme de signature
    - `v` qui concerne la periode de validite avec des Not-Before pour le debute et Not After pour l'exxpiration

- La section de certifact du serveur qui contenient les informations tels que le subject et et les informatio de l'intermediaire (issuer) bref toutes les ifno du certificat encours encode en Base64
- Les details de connection
    - details de signature
    - detail de verification SSL (OK si certifica ok) avec code de verification 0 si tout est ok
    - Les detail du Handshake TLS avec la version + Protocole, l'algorithme complet de chiffrement,

Remarque : L'integrite garantie par une fonction de hachage seule permet juste de savoir qu'un message n'a pas ete altere apres comparaison des differents hashs mais ne garanti pas qu'un MitM puisse l'intercepter et renvoyer un nouveau message avec un hash valide tandisque l'authenticite assure par une signature numerique garanti qu'un message recu de A est bel et bien de A protegeant des MITM en plus d'assurer l'integrite via des hashs


Exercie 24 :
CLientHello 
```
Frame 98: Packet, 1110 bytes on wire (8880 bits), 1110 bytes captured (8880 bits) on interface wlp2s0, id 0
Internet Protocol Version 4, Src: 10.160.13.175, Dst: 104.18.32.47
Transmission Control Protocol, Src Port: 49388, Dst Port: 443, Seq: 1349, Ack: 1, Len: 1044
[2 Reassembled TCP Segments (2392 bytes): #97(1348), #98(1044)]
Transport Layer Security
    [Stream index: 4]
    TLSv1.3 Record Layer: Handshake Protocol: Client Hello
        Content Type: Handshake (22)
        Version: TLS 1.0 (0x0301)
        Length: 2387
        Handshake Protocol: Client Hello
            Handshake Type: Client Hello (1)
            Length: 2383
            Version: TLS 1.2 (0x0303)
            Random: aab5f0afdebf44f847fe56bc906aec7edc3e29bb6e662f90827f9ecdf085633a
            Session ID Length: 32
            Session ID: 04b9a95836f539317876cc8818826eecc8062fea58beed7dff7e1ce9d95ec1fb
            Cipher Suites Length: 32
            Cipher Suites (16 suites)
            Compression Methods Length: 1
            Compression Methods (1 method)
            Extensions Length: 2278
            Extension: server_name (len=19) name=ab.chatgpt.com
            Extension: extended_master_secret (len=0)
            Extension: renegotiation_info (len=1)
            Extension: supported_groups (len=16)
            Extension: ec_point_formats (len=2)
            Extension: application_layer_protocol_negotiation (len=14)
            Extension: status_request (len=5)
            Extension: delegated_credentials (len=10)
            Extension: signed_certificate_timestamp (len=0)
            Extension: key_share (len=1327) X25519MLKEM768, x25519, secp256r1
            Extension: early_data (len=0)
            Extension: supported_versions (len=5) TLS 1.3, TLS 1.2
            Extension: signature_algorithms (len=24)
            Extension: psk_key_exchange_modes (len=2)
            Extension: record_size_limit (len=2)
            Extension: compress_certificate (len=7)
            Extension: encrypted_client_hello (len=537)
            Extension: pre_shared_key (len=235)
            [JA4: t13d1618h2_86a278354501_e7cacf613b58]
            [JA4_r: t13d1618h2_002f,0035,009c,009d,1301,1302,1303,c00a,c013,c014,c02b,c02c,c02f,c030,cca8,cca9_0005,000a,000b,000d,0012,0017,001b,001c,0022,0029,002a,002b,002d,0033,fe0d,ff01_0403,0503,0603,0804,0805,0806,0401,0501,0601,0203,0201]
            [JA3 Fullstring: 771,4865-4867-4866-49195-49199-52393-52392-49196-49200-49162-49171-49172-156-157-47-53,0-23-65281-10-11-16-5-34-18-51-42-43-13-45-28-27-65037-41,4588-29-23-24-25-256-257,0]
            [JA3: d24b7dfdd322352d64122479f5466f55]

```
ServerHello
```
Frame 105: Packet, 1454 bytes on wire (11632 bits), 1454 bytes captured (11632 bits) on interface wlp2s0, id 0
Internet Protocol Version 4, Src: 104.18.32.47, Dst: 10.160.13.175
Transmission Control Protocol, Src Port: 443, Dst Port: 49388, Seq: 1, Ack: 2399, Len: 1388
Transport Layer Security
    [Stream index: 4]
    TLSv1.3 Record Layer: Handshake Protocol: Server Hello
        Content Type: Handshake (22)
        Version: TLS 1.2 (0x0303)
        Length: 1216
        Handshake Protocol: Server Hello
            Handshake Type: Server Hello (2)
            Length: 1212
            Version: TLS 1.2 (0x0303)
            Random: 84f2b4f6bdc613c9f556f8447995729e45449991005a8867989348efc1992ef0
            Session ID Length: 32
            Session ID: 04b9a95836f539317876cc8818826eecc8062fea58beed7dff7e1ce9d95ec1fb
            Cipher Suite: TLS_AES_128_GCM_SHA256 (0x1301)
            Compression Method: null (0)
            Extensions Length: 1140
            Extension: pre_shared_key (len=2)
            Extension: key_share (len=1124) X25519MLKEM768
            Extension: supported_versions (len=2) TLS 1.3
            [JA3S Fullstring: 771,4865,41-51-43]
            [JA3S: 2b0648ab686ee45e0e7c35fcfb0eea7e]
    TLSv1.3 Record Layer: Change Cipher Spec Protocol: Change Cipher Spec
        Content Type: Change Cipher Spec (20)
        Version: TLS 1.2 (0x0303)
        Length: 1
        Change Cipher Spec Message
    TLSv1.3 Record Layer: Application Data Protocol: Hypertext Transfer Protocol
        Opaque Type: Application Data (23)
        Version: TLS 1.2 (0x0303)
        Length: 147
        Encrypted Application Data […]: facc7fcebda407365e211d135345777d219fd6c04cc775d47d1418bb9d9aceef8dffef3fb8fee1cce2d21ed9ae70eba7e3029a62e321622bc3af468b4d0fa07e1ebb11dcbb78d4a834e6a53df28b7e3f050f29aa83ac7ae7fab3b38c89287a5628d24a5525eb1
        [Application Data Protocol: Hypertext Transfer Protocol]
    TLS segment data (9 bytes)
```

Une negociation TLS1.3 se fait en poignee de main CLientHello et ServerHello
Dans le CLientHello,on a :
- La version du protocole : TLSv1.3
- Le type : Handshake Protocol: CLient Hello
- La taille (Length de la requete)
- La version supportee 1.2
- L'identifiant de session
- La liste des algorithmes de chiffrements supportees : Cipher SUites
- Les Methodes de decompression compatibles
- Les extensions qui presente tout ce que le client sait faire ou peut faire en matiere de cryptographie tels que :
    - Le nom du serveur ici ab.chatgpt.com
    - Les versions supportees : 1.3 et 1.2 
    - La version chiffree du client Hello empechant un tier, un intermediaire de savoir le domaine precis visite
    - Le certificat de compression

Dans le serverHello la reponse du serveur a ce client Heloo avec la certification. VUe qu'on est en TLS1.3 il est donc impossible de discerner les informations du certificat qui est chiffre mais on peut neanmoins avoir le type SeverHello, la version TLS et bien d'autres
