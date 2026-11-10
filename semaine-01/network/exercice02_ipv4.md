Analyser une adresse IPv4, son masque, son réseau, son broadcast et sa plage d'adresses utilisables.
# Série 1 — Fondamentaux ★

## Exercice 1
Adresse IP : 192.168.1.25/24

### Détermine :
1. Le masque de sous-réseau en décimal.
2. L'adresse réseau.
3. L'adresse de broadcast.
4. La première adresse IP utilisable.
5. La dernière adresse IP utilisable.
6. Le nombre total d'adresses.
7. Le nombre d'adresses utilisables.
### Reponses :
1. 255.255.255.0
2. 192.168.1.0/24
3. 192.168.1.255/24
4. 192.168.1.1/24
5. 192.168.1.254/24
6. 256
7. 254

## Exercice 2
Adresse IP : 172.16.10.130/26

Détermine les mêmes éléments que dans l'exercice 1.

### Reponses :
1. 255.255.255.192
2. 172.16.10.128/26
3. 172.16.10.191/26
4. 172.16.10.129/26
5. 172.16.10.190/26
6. 64
7. 62 
## Exercice 3
Adresse IP : 192.168.50.75/28

Détermine :
1. Le masque.
2. L'adresse réseau.
3. Le broadcast.
4. La plage d'adresses utilisables.
5. Le nombre d'hôtes utilisables.

### Reponses :
1. 255.255.255.240
2. 192.168.50.64/28
3. 192.168.50.79/28
4. 192.168.50.65 -> 192.168.50.78
5. 14
# Série 2 — Approfondissement ◆
## Exercice 4
Adresse IP : 10.0.5.200/20

Détermine :
- Le masque décimal.
- L'adresse réseau.
- Le broadcast.
- La plage utilisable.
- Le nombre d'hôtes utilisables.
Attention : le préfixe /20 ne correspond pas à un découpage classique sur un seul octet.
### Reponses :
- 255.255.240.0

- 10.0.0.0/20
- 10.0.15.255/20
- 10.0.0.1/20 - 10.0.15.254/20
- 4094
## Exercice 5
Tu disposes du réseau :

192.168.10.0/24

Tu dois le diviser en 4 sous-réseaux de taille égale.

Pour chaque sous-réseau, détermine :
- L'adresse réseau.
- Le masque et le préfixe CIDR.
- L'adresse de broadcast.
- La plage d'adresses utilisables.
- Le nombre d'hôtes utilisables.
### Reponses
La division en 4 sous reseau inclu de trouver le nouveau prefixe on a 2^n >= 4 (=) n>=2 on va prendre 2 le nouveau prefixe sera de 24+2=26
1. Reseau A :
- 192.168.10.0/26
- 255.255.255.192/26
- 192.168.10.63/26
- 192.168.10.1/26 -> 192.168.10.62/26
- 62
2. Reseau B :
- 192.168.10.64/26
- 255.255.255.192/26
- 192.168.10.127/26
- 192.168.10.65/26 -> 192.168.10.126/26
- 62
3. Reseau C :
- 192.168.10.128/26
- 255.255.255.192/26
- 192.168.10.191/26
- 192.168.10.129/26 -> 192.168.10.190/26
- 62
4. Reseau D :
- 192.168.10.192/26
- 255.255.255.192/26
- 192.168.10.255/26
- 192.168.10.193/26 -> 192.168.10.254/26
- 62
## Exercice 6
Tu disposes du réseau :

192.168.20.0/24

Tu dois créer des sous-réseaux capables d'accueillir respectivement :
- Service A : 100 machines.
- Service B : 50 machines.
- Service C : 25 machines.
- Service D : 10 machines.
Trouve un plan d'adressage adapté en utilisant le VLSM (Variable Length Subnet Mask).

Justifie l'ordre d'attribution des sous-réseaux et vérifie qu'il n'existe aucun chevauchement.
### Reponses
Selon l'enonce les reseau sont deja classe du plus grand au plus petit donc oncommence par le reseau A.
1. Reseau A :
cherchons le prefixe : 2^n>=100 n>=7 car 2^7=128>=100le prefixe sera de 32-7=25 on a deux sous reseaux
Sous reseau A : 
- Adresse reseau : 192.168.20.0/25
- Masque : 255.255.255.128/25
- Broadcast : 192.168.20.127/25
- plage utilisable : 192.168.20.1/25 -> 192.168.20.126/25
- 126
NB : Le VLSM favorisant l'economie des adresse on va utiliser pour le prochain reseau l'adresse 192.168.20.128/25 car 126-100=26<50
2. Reseau B :
cherchons le prefixe : 2^n>=50 n>=6 car 2^6=64>=50 le prefixe sera de 32-6=26 on a 4 sous reseaux donc deux impossibles a utiliser donc il en reste 2
Sous reseau B : 
- Adresse reseau : 192.168.20.128/26
- Masque : 255.255.255.192/26
- Broadcast : 192.168.20.191/26
- plage utilisable : 192.168.20.129/26 -> 192.168.20.190/26
- 62
NB : Le VLSM favorisant l'economie des adresse on va utiliser pour le prochain reseau l'adresse 192.168.20.192/26 car 62-50=12<25
3. Reseau C :
cherchons le prefixe : 2^n>=25 n>=5 car 2^5=32>=25 le prefixe sera de 32-5=27 on a 8 sous reseaux donc 6 impossibles a utiliser donc il en reste 2
Sous reseau C : 
- Adresse reseau : 192.168.20.192/27
- Masque : 255.255.255.224/27
- Broadcast : 192.168.20.223/27
- plage utilisable : 192.168.20.193/27 -> 192.168.20.222/27
- 30
NB : Le VLSM favorisant l'economie des adresse on va utiliser pour le prochain reseau l'adresse 192.168.20.224/27 car 30-25=5<10
4. Reseau D :
cherchons le prefixe : 2^n>=10 n>=4 car 2^4=16>=10 le prefixe sera de 32-4=28 on a 16 sous reseaux donc 14 impossibles a utiliser donc il en reste 2
Sous reseau D : 
- Adresse reseau : 192.168.20.224/28
- Masque : 255.255.255.240/28
- Broadcast : 192.168.20.239/28
- plage utilisable : 192.168.20.225/28 -> 192.168.20.238/28
- 14
NB : Le VLSM favorisant l'economie des adresse on va utiliser pour le prochain reseau l'adresse 192.168.20.224/27 car 30-25=5<10
# Série 3 — Mise en situation ◆
## Exercice 7 — Diagnostic réseau
Un administrateur configure deux machines :
Machine	Adresse IP	Masque
PC-A	192.168.1.10	255.255.255.0
PC-B	192.168.2.20	255.255.255.0


Questions :
1. Ces deux machines appartiennent-elles au même sous-réseau ?
2. Peuvent-elles communiquer directement au niveau IP sans routeur ?
3. Quel équipement ou mécanisme permettrait leur communication ?
4. Que se passerait-il si PC-A avait plutôt le masque 255.255.0.0 ?
## Exercice 8 — Détection d'une mauvaise configuration
Un réseau utilise :
- Adresse réseau : 192.168.30.0/27
- PC-A : 192.168.30.10/27
- PC-B : 192.168.30.20/27
- PC-C : 192.168.30.35/27
- Passerelle : 192.168.30.31
Identifie :
1. Les adresses correctement configurées.
2. Les adresses incorrectes.
3. Le problème éventuel concernant la passerelle.
4. Les corrections nécessaires.