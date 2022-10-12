10.33.16.99
00001010.00100001.000100 11.01100011

mask
255.255.252.0

1111 1111.1111 1111.1111 1100.0000 0000

New-NetIPAddress


192.168.128.64/22

192.168.128.1
192.168.128.254
192.168.128.255



PS C:\Users\Ranvin> ping 192.168.128.240

Envoi d’une requête 'Ping'  192.168.128.240 avec 32 octets de données :
Réponse de 192.168.128.240 : octets=32 temps=1 ms TTL=128
Réponse de 192.168.128.240 : octets=32 temps=2 ms TTL=128
Réponse de 192.168.128.240 : octets=32 temps=1 ms TTL=128
Réponse de 192.168.128.240 : octets=32 temps=2 ms TTL=128

Statistiques Ping pour 192.168.128.240:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 1ms, Maximum = 2ms, Moyenne = 1ms
PS C:\Users\Ranvin>

commande pour changer l'adresse passerelle 
netsh int ip set address "XXX" address=192.168.1.10 mask=255.255.255.0 gateway=192.168.1.1
netsh int ipv4 set dnsservers name="XXXXX"  source=static address="192.168.1.1" validate=no

arp -a ip de mon bînome
Interface : 192.168.128.2 --- 0x13
  Adresse Internet      Adresse physique      Type
  192.168.128.100       84-69-93-52-2e-d1     dynamique
  224.0.0.22            01-00-5e-00-00-16     statique
PS C:\Windows\system32>

adresse Mac du réseau
Interface : 192.168.128.2 --- 0x13
  Adresse Internet      Adresse physique      Type
  192.168.128.100       84-69-93-52-2e-d1     dynamique 

  commande pour vider la table arp 
  arp -d 
on voit quil questionne la passerelle pour savoir qui est 192.168.128.100

                    dhcp
