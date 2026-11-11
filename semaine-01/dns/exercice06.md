
## EX06	Examiner la configuration DNS de ta machine Linux.
### Preuve attendue:
	Résultats de commandes et interprétation.


## 1. `resolvectl status`
Cette commande permet d'observer l'etat dns de toutes les interfaces reseaux 
```bash
user@user:~$ resolvectl status
Global
         Protocols: -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
  resolv.conf mode: stub

Link 2 (enp0s31f6)
    Current Scopes: none
         Protocols: -DefaultRoute -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
     Default Route: no

Link 3 (wlp2s0)
    Current Scopes: DNS
         Protocols: +DefaultRoute -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
Current DNS Server: 10.0.13.162
       DNS Servers: 10.0.13.162
     Default Route: yes

Link 4 (virbr0)
    Current Scopes: none
         Protocols: -DefaultRoute -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
     Default Route: no

Link 5 (docker0)
    Current Scopes: none
         Protocols: -DefaultRoute -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
     Default Route: no

Link 6 (br-cdc22ae759c4)
    Current Scopes: none
         Protocols: -DefaultRoute -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
     Default Route: no

Link 7 (br-58fbd2d7c7d5)
    Current Scopes: none
         Protocols: -DefaultRoute -LLMNR -mDNS -DNSOverTLS DNSSEC=no/unsupported
     Default Route: no
```
On s'interessera particulierement a l'interface 3 wp2s0:
Current Scope ici permet de savoir si le dns est actif dans le cas acif on a le resusltat : `DNS` et dans le cas contraire `none`
Current DNS Server donne l'adresse IP du serveur dns utilise, 
DNS Servers : liste tous les serveurs DNS actifs

## 2. `dig` ou `nslookup`
Ces commandes permettent d'effectuer une requete dns. `dig url_site` pour une requete dns et `dig -x ip_adr` pour une requete inversee 
```bash
user:~$ dig chatgpt.com

; <<>> DiG 9.20.24-1ubuntu0.3-Ubuntu <<>> chatgpt.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 22160
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;chatgpt.com.                   IN      A

;; ANSWER SECTION:
chatgpt.com.            65      IN      A       104.18.32.47
chatgpt.com.            65      IN      A       172.64.155.209

;; Query time: 1 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Wed Nov 11 20:45:46 WAT 2026
;; MSG SIZE  rcvd: 72
```
On a la une reponse de type A donc en Ipv4 avec l'adresse du serveur renvoyee
```bash
0:~$ dig -x 172.64.155.209

; <<>> DiG 9.20.24-1ubuntu0.3-Ubuntu <<>> -x 172.64.155.209
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 14852
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;209.155.64.172.in-addr.arpa.   IN      PTR

;; AUTHORITY SECTION:
64.172.in-addr.arpa.    307     IN      SOA     cruz.ns.cloudflare.com. dns.cloudflare.com. 2387399959 10000 2400 604800 1800

;; Query time: 185 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Wed Nov 11 20:51:30 WAT 2026
;; MSG SIZE  rcvd: 118
```
Ici on a une requete de type PTR pour Pointer (resolution inverse) qui traduit une ip en un nom de domaine
Ici on a une section Authority pour le serveur faisant authorite pour l'ip fournie ici SOA vers cloudflare