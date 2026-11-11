J'ai etabli un reseau entre mon PC et tellephone via connection wi-Fi du pc au telephone et donc j'ai du filtrer les autres echanges lors de la capture avec `ip.addr=IP_PC && ip.addr=IP_TEL` puis utiliser un outil tel que tshark en CLI pour supprimer les conversation non interessantes. 
Dans le but d'anonymiser les IP et Mac j'ai utiliser un `tcpprep` pour trier et repertorier les conversation venant de mon PC et les sauvegarder dans un fichier texte temporaire puis j'ai utilise `tcprewrite` pour reecrire la capture avec les ip/ mac que j'ai choisi au hasard 

```

Frame 26: Packet, 98 bytes on wire (784 bits), 98 bytes captured (784 bits)
Ethernet II, Src: aa:bb:cc:dd:ee:ff (aa:bb:cc:dd:ee:ff), Dst: CIMSYS_33:44:55 (00:11:22:33:44:55)
    Destination: CIMSYS_33:44:55 (00:11:22:33:44:55)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Source: aa:bb:cc:dd:ee:ff (aa:bb:cc:dd:ee:ff)
    Type: IPv4 (0x0800)
    [Stream index: 0]
Internet Protocol Version 4, Src: 10.0.0.2, Dst: 10.0.0.1
    0100 .... = Version: 4
    .... 0101 = Header Length: 20 bytes (5)
    Differentiated Services Field: 0x00 (DSCP: CS0, ECN: Not-ECT)
    Total Length: 84
    Identification: 0xd29f (53919)
    010. .... = Flags: 0x2, Don't fragment
    ...0 0000 0000 0000 = Fragment Offset: 0
    Time to Live: 64
    Protocol: ICMP (1)
    Header Checksum: 0x5407 [validation disabled]
    [Header checksum status: Unverified]
    Source Address: 10.0.0.2
    Destination Address: 10.0.0.1
    [Stream index: 0]
Internet Control Message Protocol
Frame 26: Packet, 98 bytes on wire (784 bits), 98 bytes captured (784 bits)
Ethernet II, Src: aa:bb:cc:dd:ee:ff (aa:bb:cc:dd:ee:ff), Dst: CIMSYS_33:44:55 (00:11:22:33:44:55)
    Destination: CIMSYS_33:44:55 (00:11:22:33:44:55)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Source: aa:bb:cc:dd:ee:ff (aa:bb:cc:dd:ee:ff)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Type: IPv4 (0x0800)
    [Stream index: 0]
Internet Protocol Version 4, Src: 10.0.0.2, Dst: 10.0.0.1
    0100 .... = Version: 4
    .... 0101 = Header Length: 20 bytes (5)
    Differentiated Services Field: 0x00 (DSCP: CS0, ECN: Not-ECT)
    Total Length: 84
    Identification: 0xd29f (53919)
    010. .... = Flags: 0x2, Don't fragment
    ...0 0000 0000 0000 = Fragment Offset: 0
    Time to Live: 64
    Protocol: ICMP (1)
    Header Checksum: 0x5407 [validation disabled]
    [Header checksum status: Unverified]
    Source Address: 10.0.0.2
    Destination Address: 10.0.0.1
    [Stream index: 0]
Internet Control Message Protocol
    Type: Echo (ping) request (8)
    Code: 0
    Checksum: 0x194b [correct]
    [Checksum Status: Good]
    Identifier (BE): 38255 (0x956f)
    Identifier (LE): 28565 (0x6f95)
    Sequence Number (BE): 1 (0x0001)
    Sequence Number (LE): 256 (0x0100)
    [Response frame: 27]
    ICMP Data: f53df46a0000000097c8090000000000101112131415161718191a1b1c1d1e1f202122232425262728292a2b2c2d2e2f3031323334353637
```
Dans cet exemple de trame on a les adresses ip suivantes comme consulte dans la section du protocole IP au niveau de Src et Dst:
- **PC**:10.0.0.2 : c'est l'adresse IP source du PC qui a emit le PING
- **TEL**:10.0.0.1 : C'est l'adresse IP de destination du PING ecrit dans la comande
Les adreses IP via le protocole IP permettent le routage des pacquets demaniere logique entre des equipements de differents reseau ou du meme resuea physique
Les adresses MAC sont : comme dans la section Ethernet II :
- **PC**(Src): aa:bb:cc:dd:ee:ff C'est l'adresse MAC obtenu a partir de l'IP de source
- **TEL**(Dst): 00:11:22:33:44:55 C'est l'adresse MAC de destination
Le MAC assure la communication physique entre les equipements physique d'un meme reseau physique sans routage