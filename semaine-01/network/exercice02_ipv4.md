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
## Exercice 3
Adresse IP : 192.168.50.75/28

Détermine :
1. Le masque.
2. L'adresse réseau.
3. Le broadcast.
4. La plage d'adresses utilisables.
5. Le nombre d'hôtes utilisables.
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