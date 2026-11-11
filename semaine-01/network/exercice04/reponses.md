Voici  une requete ARP obetnue :
```
Frame 1: Packet, 42 bytes on wire (336 bits), 42 bytes captured (336 bits) on interface wlp2s0, id 0
Ethernet II, Src: aa:bb:cc:dd:ee:ff (aa:bb:cc:dd:ee:ff), Dst: CIMSYS33:44:55 (00:11:22:33:44:55)
Address Resolution Protocol (request)
    Hardware type: Ethernet (1)
    Protocol type: IPv4 (0x0800)
    Hardware size: 6
    Protocol size: 4
    Opcode: request (1)
    Sender MAC address: aa:bb:cc:dd:ee:ff (aa:bb:cc:ee:ff)
    Sender IP address: 10.42.0.107
    Target MAC address: 00:00:00_00:00:00 (00:00:00:00:00:00)
    Target IP address: 10.42.0.1

```
Voici une reponse :
```
Frame 2: Packet, 42 bytes on wire (336 bits), 42 bytes captured (336 bits) on interface wlp2s0, id 0
Ethernet II, Src: CIMSYS33:44:55 (00:11:22:33:44:55), Dst: aa:bb:cc:dd:ee:ff (aa:bb:cc:dd:ee:ff)
Address Resolution Protocol (reply)
    Hardware type: Ethernet (1)
    Protocol type: IPv4 (0x0800)
    Hardware size: 6
    Protocol size: 4
    Opcode: reply (2)
    Sender MAC address: CIMSYS33:44:55 (00:11:22:33:44:55)
    Sender IP address: 10.42.0.1
    Target MAC address: aa:bb:cc:dd:ee:ff (aa:bb:cc:dd:ee:ff)
    Target IP address: 10.42.0.107
```
Dans cet extrait de capture d'une conversation ARP on peut dire qu'a la premiere connection entre les deux appareils, l'un qui souhaite comminiquer avec l'autre fais une requete ARP broadcast pour connaitre l'adresse MAC de l'appareil a partir d'une adresse ip dont il dispose et souhaite cmmuniquer : dans ce cas c'est une requete du genre a qui apprtient l'ip 10.42.0.1 ? puis au sein du reseau l'equipement qui se reconnait sous cet ip renvoit une reponse ARP avec son adresse MAC dans quelque chose du genre : c'est moi a l'adresse MAC 00:11:22:33:44:55. Ainsi celui qui emet la requete peut enregistrer l'adresse dans sa table ARP pendant un certain temps.