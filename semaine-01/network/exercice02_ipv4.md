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
- 10.0.15.255/30
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
1. Reseau A :
- 192.168.10.128/26
- 255.255.255.192/26
- 192.168.10.191/26
- 192.168.10.129/26 -> 192.168.10.190/26
- 62
1. Reseau A :
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
cherchons le prefixe : 2^n>=100 n>=7 le prefixe sera de 32-7=25 on a deux sous reseaux
Sous reseau A :
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