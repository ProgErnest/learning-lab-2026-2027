EX04 — Comprendre le fonctionnement du protocole ARP
Objectif : Comprendre comment une machine découvre l'adresse MAC correspondant à une adresse IP sur son réseau local.

Travail à effectuer :
1. Sur Ubuntu, ouvre un terminal.
2. Consulte la table ARP (ou table des voisins) de ta machine.
3. Choisis une autre machine connectée à ton réseau local.
4. Supprime uniquement l'entrée ARP correspondant à cette machine, si elle existe.
5. Ouvre Wireshark et démarre une capture.
6. Depuis ton terminal, envoie un ping vers cette machine.
7. Dans Wireshark, recherche les paquets ARP générés.
8. Identifie :
   - La requête ARP (ARP Request).
   - L'adresse IP recherchée.
   - L'adresse MAC de destination utilisée dans la requête Ethernet.
   - La réponse ARP (ARP Reply).
   - L'adresse MAC communiquée en réponse.
9. Explique pourquoi ta machine a besoin de connaître l'adresse MAC de destination avant de pouvoir lui envoyer les données sur le réseau local.
Livrable attendu :
- Une capture Wireshark montrant la requête et la réponse ARP.
- Une explication chronologique du processus ARP.
Attention : Ne vide pas toute ta table ARP. Supprime uniquement l'entrée concernée. Si tu ne disposes pas d'une deuxième machine, nous pourrons adapter l'exercice avec deux machines virtuelles.