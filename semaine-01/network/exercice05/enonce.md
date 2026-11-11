EX05 — Comprendre la communication entre deux réseaux grâce à un routeur
Objectif : Comprendre pourquoi un routeur est nécessaire pour permettre à deux machines appartenant à des réseaux IP différents de communiquer.

Travail à effectuer :
1. Ouvre Cisco Packet Tracer.
2. Crée une topologie comprenant :
   - Deux ordinateurs (PC-A et PC-B).
   - Un routeur.
   - Deux commutateurs (switches).
3. Connecte PC-A au premier switch et PC-B au deuxième switch.
4. Connecte chaque switch à une interface du routeur.
5. Configure les adresses IP suivantes :
Équipement	Adresse IP	Masque	Passerelle
PC-A	192.168.1.10	255.255.255.0	192.168.1.1
PC-B	192.168.2.10	255.255.255.0	192.168.2.1


6. Configure les deux interfaces du routeur :
   - Interface connectée au réseau de PC-A : 192.168.1.1/24.
   - Interface connectée au réseau de PC-B : 192.168.2.1/24.
7. Vérifie que les interfaces du routeur sont actives.
8. Depuis PC-A, effectue un ping vers PC-B.
9. Utilise le mode Simulation de Packet Tracer pour observer les paquets échangés.
10. Analyse le trajet des paquets et réponds aux questions suivantes :
    - Pourquoi PC-A ne peut-il pas communiquer directement avec PC-B sans passer par un routeur ?
    - Quel est le rôle de la passerelle par défaut ?
    - Quelle est l'adresse MAC de destination utilisée par PC-A lorsqu'il envoie un paquet vers PC-B ?
    - L'adresse IP de destination change-t-elle lorsque le paquet traverse le routeur ?
    - Quelles informations de la trame Ethernet sont modifiées au passage du routeur ?
Livrable attendu :
- Le fichier Packet Tracer (.pkt) avec la topologie fonctionnelle.
- Une capture du ping réussi.
- Une ou plusieurs captures du mode Simulation.
- Des réponses argumentées aux cinq questions.