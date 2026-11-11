10. 
```
Frame 1: Packet, 66 bytes on wire (528 bits), 66 bytes captured (528 bits) on interface \Device\NPF_{EFF0126D-FCDE-4785-98CB-403F5C91DF50}, id 0
Ethernet II, Src: Dell_d9:3e:7d (ec:f4:bb:d9:3e:7d), Dst: VMware_1c:e3:19 (00:0c:29:1c:e3:19)
Internet Protocol Version 4, Src: 192.168.200.135, Dst: 192.168.200.21
Transmission Control Protocol, Src Port: 6711, Dst Port: 2000, Seq: 0, Len: 0
    Source Port: 6711
    Destination Port: 2000
    [Stream index: 0]
    [Stream Packet Number: 1]
    [Conversation completeness: Complete, WITH_DATA (31)]
    [TCP Segment Len: 0]
    Sequence Number: 0    (relative sequence number)
    Sequence Number (raw): 3714759466
    [Next Sequence Number: 1    (relative sequence number)]
    Acknowledgment Number: 0
    Acknowledgment number (raw): 0
    1000 .... = Header Length: 32 bytes (8)
    Flags: 0x002 (SYN)
    Window: 64240
    [Calculated window size: 64240]
    Checksum: 0x1215 [unverified]
    [Checksum Status: Unverified]
    Urgent Pointer: 0
    Options: (12 bytes), Maximum segment size, No-Operation (NOP), Window scale, No-Operation (NOP), No-Operation (NOP), SACK permitted
    [Timestamps]
    [Client Contiguous Streams: 1]
    [Server Contiguous Streams: 1]
```
Dans cette capture tcp d'un segment on discerne aisement le port source et de destination respectivement dans les enregsitrements Source Port 6711 et destination Port : 2000


11. Dans une connection TCP il y'a ce que l'on appelle une connection ou une synchronisation en 3 poignees de main (ThreeWays Handshake)
Dans la capture [capture.pcapng](capture.pcapng) on observe une conversation TCP en trois temps :
- 1. Demande de connection vers le destinataire via un flag ou drapeau SYN avec un numero de sequence relatif 0 NB: volontairement je n'ai pas mis le numero reel ou absolu de sequence
- 2. Reponse du destinataire avec les flags SYN et ACK Syn pour une demande de synchronisation venant du estinataire et ACK pour l'accuse de reception dela demande recue
- 3. ACk pour l'acquitement :ici c'est pour etre sure que l'emetteur a bien recu la demade venant du destinataire

12. La fermeture d'une connection tcp implique que l'un demande un arret de synchronisation et de meme pour l'autre dans des condition normale via principalement le flag FIN et ACK pour les acquitements
et dans des conditions anormales  le flag RST est utilisee

- FIN : Flag de demande de fermeture de conversation ou de communication TCP
- ACK : C'est une flag d'acquitement pour signaler qu'un message a bel et bien ete recu
- RST : fermeture de connection forcee ou avortee

13. COmparaison TCP vs UDP
Tous deux ont en commun d'etre des protocoles de transports tres prisees mais leurs usages different en fonction des besoins et necessite:
-TCP est plus utilise dans le cadre du web du a sa fiabilite etdu fait  qu'il garanti l'integrite des communication et la connetion effective entre les deux temrinaux tandisque UDP favorise la vitesse pure a la fiabilite et donc cnsomme moins de bande passante que tcp car lleger est plus adapte pour des streamings appels video ou autres car est plus adapte pour le temps reel.