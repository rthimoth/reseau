ipconfig /all
adresse physique mac 4C-03-4F-E7-6A-FD

adresse physique 08-8F-C3-46-88-EC

passerelle routeur 10.33.19.254

arp -a 
Interface : 10.33.16.199 --- 0xa
  Adresse Internet      Adresse physique      

  10.33.19.254          00-c0-e7-e0-04-4e     
  
  
  panneau de configuration/réseau et partage/connexion/propriété/protocole ipv4 
  perte de connexion
  On perd la connexion car le routeur ne trouve plus mon pc?
  Ou car  l'adresse est  déjà utiliser 
 
 
  ipv4 10.33.16.199
  masque sous réseau 255.255.252.0

.
PS C:\Users\Ranvin>ip modifié panneau de configuration/réseau et partage/connexion/propriété/protocole ipv4 10.10.10.110
            masque sous réseau 255.255.255.0

ip config l'ip à changer

ping 
Envoi d’une requête 'Ping'  10.10.10.240 avec 32 octets de données :
Réponse de 10.10.10.240 : octets=32 temps=1 ms TTL=128
Réponse de 10.10.10.240 : octets=32 temps=2 ms TTL=128
Réponse de 10.10.10.240 : octets=32 temps=1 ms TTL=128
Réponse de 10.10.10.240 : octets=32 temps=1 ms TTL=128

arp
PS C:\Users\Ranvin> arp /a 10.10.10.110

Interface : 10.33.16.199 --- 0xa
  Adresse Internet      Adresse physique      Type
  10.10.10.110          bc-6e-e2-d3-54-28     dynamique
PS C:\Users\Ranvin>


 ping 1.1.1.1

Envoi d’une requête 'Ping'  1.1.1.1 avec 32 octets de données :
Réponse de 1.1.1.1 : octets=32 temps=21 ms TTL=55
Réponse de 1.1.1.1 : octets=32 temps=21 ms TTL=55
Réponse de 1.1.1.1 : octets=32 temps=22 ms TTL=55
Réponse de 1.1.1.1 : octets=32 temps=30 ms TTL=55

Statistiques Ping pour 1.1.1.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 21ms, Maximum = 30ms, Moyenne = 23ms
PS C:\Users\Ranvin>

PS C:\Users\Ranvin> tracert

Utilisation : tracert [-d] [-h SautsMaxi] [-j ListeHôtes] [-w délai]
              [-R] [-S srcaddr] [-4] [-6] nom_cible

Options :
   -d                 Ne pas convertir les adresses en noms d’hôtes.
   -h SautsMaxi       Nombre maximum de sauts pour rechercher la cible.
   -j ListeHôtes      Itinéraire source libre parmi la liste des hôtes
                      (IPv4 uniquement).
   -w délai           Attente d’un délai en millisecondes pour chaque réponse.
   -R                 Chemin de suivi (IPv6 uniquement).
   -S srcaddr         Adresse source à utiliser (IPv6 uniquement).
   -4                 Force utilisant IPv4.
   -6                 Force utilisant IPv6

sur le pc client 

PS C:\Users\Ranvin\Desktop\netcat-1.11> .\nc.exe
Cmd line: cwrong
PS C:\Users\Ranvin\Desktop\netcat-1.11> .\nc.exe
Cmd line: 192.168.137.240 8888
coucou
mdr

visualiser la connexion

  Proto  Adresse locale         Adresse distante       État
  TCP    0.0.0.0:135            0.0.0.0:0              LISTENING
  RpcSs
 [svchost.exe]
  TCP    0.0.0.0:445            0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    0.0.0.0:902            0.0.0.0:0              LISTENING
 [vmware-authd.exe]
  TCP    0.0.0.0:912            0.0.0.0:0              LISTENING
 [vmware-authd.exe]
  TCP    0.0.0.0:5040           0.0.0.0:0              LISTENING
  CDPSvc
 [svchost.exe]
  TCP    0.0.0.0:8888           0.0.0.0:0              LISTENING
 [nc.exe]
  TCP    0.0.0.0:49664          0.0.0.0:0              LISTENING
 [lsass.exe]
  TCP    0.0.0.0:49665          0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    0.0.0.0:49666          0.0.0.0:0              LISTENING
  Schedule
 [svchost.exe]
  TCP    0.0.0.0:49667          0.0.0.0:0              LISTENING
  EventLog
 [svchost.exe]
  TCP    0.0.0.0:49668          0.0.0.0:0              LISTENING
 [spoolsv.exe]
  TCP    0.0.0.0:49670          0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    0.0.0.0:51318          0.0.0.0:0              LISTENING
  PolicyAgent
 [svchost.exe]
  TCP    10.33.16.199:139       0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    10.33.16.199:57826     52.112.120.16:443      ESTABLISHED
 [Teams.exe]
  TCP    10.33.16.199:57830     52.114.76.238:443      ESTABLISHED
 [Teams.exe]
  TCP    10.33.16.199:57832     20.199.120.151:443     ESTABLISHED
  WpnService
 [svchost.exe]
  TCP    10.33.16.199:57951     162.159.136.234:443    ESTABLISHED
 [Discord.exe]
  TCP    10.33.16.199:58777     64.233.167.188:5228    ESTABLISHED
 [chrome.exe]
  TCP    10.33.16.199:58946     51.144.164.215:443     CLOSE_WAIT
 [Code.exe]
  TCP    10.33.16.199:58956     8.8.4.4:443            TIME_WAIT
  TCP    10.33.16.199:58957     216.58.198.195:443     TIME_WAIT
  TCP    10.33.16.199:58958     142.250.201.174:443    TIME_WAIT
  TCP    10.33.16.199:58959     142.250.179.67:443     TIME_WAIT
  TCP    10.33.16.199:58960     216.58.204.99:443      TIME_WAIT
  TCP    10.33.16.199:58962     8.8.4.4:443            ESTABLISHED
 [chrome.exe]
  TCP    10.33.16.199:58963     216.58.213.131:443     ESTABLISHED
 [chrome.exe]
  TCP    10.33.16.199:58967     23.215.190.43:443      CLOSE_WAIT
 [SearchHost.exe]
  TCP    10.33.16.199:58968     2.18.245.145:443       CLOSE_WAIT
 [SearchHost.exe]
  TCP    10.33.16.199:58969     52.109.28.20:443       TIME_WAIT
  TCP    127.0.0.1:6463         0.0.0.0:0              LISTENING
 [Discord.exe]
  TCP    127.0.0.1:58951        0.0.0.0:0              LISTENING
 [Code.exe]
  TCP    192.168.56.1:139       0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    192.168.129.1:139      0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    192.168.137.1:139      0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    192.168.137.1:58767    0.0.0.0:0              LISTENING
 [alg.exe]
  TCP    192.168.232.1:139      0.0.0.0:0              LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    [::]:135               [::]:0                 LISTENING
  RpcSs
 [svchost.exe]
  TCP    [::]:445               [::]:0                 LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    [::]:49664             [::]:0                 LISTENING
 [lsass.exe]
  TCP    [::]:49665             [::]:0                 LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    [::]:49666             [::]:0                 LISTENING
  Schedule
 [svchost.exe]
  TCP    [::]:49667             [::]:0                 LISTENING
  EventLog
 [svchost.exe]
  TCP    [::]:49668             [::]:0                 LISTENING
 [spoolsv.exe]
  TCP    [::]:49670             [::]:0                 LISTENING
 Impossible d’obtenir les informations de propriétaire
  TCP    [::]:51318             [::]:0                 LISTENING
  PolicyAgent
 [svchost.exe]
  TCP    [::1]:49669            [::]:0                 LISTENING
 [jhi_service.exe]
  UDP    0.0.0.0:53             *:*
  SharedAccess
 [svchost.exe]
  UDP    0.0.0.0:500            *:*
  IKEEXT
 [svchost.exe]
  UDP    0.0.0.0:4500           *:*
  IKEEXT
 [svchost.exe]
  UDP    0.0.0.0:5050           *:*
  CDPSvc
 [svchost.exe]
  UDP    0.0.0.0:5353           *:*
 [msedge.exe]
  UDP    0.0.0.0:5353           *:*
 [msedge.exe]
  UDP    0.0.0.0:5353           *:*
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*
 [msedge.exe]
  UDP    0.0.0.0:5353           *:*
 [msedge.exe]
  UDP    0.0.0.0:5353           *:*
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*
 [msedge.exe]
  UDP    0.0.0.0:5353           *:*
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*
 [msedge.exe]
  UDP    0.0.0.0:5353           *:*
  Dnscache
 [svchost.exe]
  UDP    0.0.0.0:5353           *:*
 [msedge.exe]
  UDP    0.0.0.0:5353           *:*
 [msedge.exe]
  UDP    0.0.0.0:5353           *:*
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*
 [msedge.exe]
  UDP    0.0.0.0:5353           *:*
 [msedge.exe]
  UDP    0.0.0.0:5353           *:*
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*
 [chrome.exe]
  UDP    0.0.0.0:5353           *:*
 [chrome.exe]
  UDP    0.0.0.0:5355           *:*
  Dnscache
 [svchost.exe]
  UDP    0.0.0.0:54356          *:*
  SharedAccess
 [svchost.exe]
  UDP    0.0.0.0:54358          *:*
  SharedAccess
 [svchost.exe]
  UDP    0.0.0.0:57312          *:*
  Dnscache
 [svchost.exe]
  UDP    0.0.0.0:60050          *:*
 [Teams.exe]
  UDP    0.0.0.0:60334          *:*
 [Teams.exe]
  UDP    0.0.0.0:61159          *:*
  Dnscache
 [svchost.exe]
  UDP    0.0.0.0:64579          *:*
  SharedAccess
 [svchost.exe]
  UDP    10.33.16.199:137       *:*
 Impossible d’obtenir les informations de propriétaire
  UDP    10.33.16.199:138       *:*
 Impossible d’obtenir les informations de propriétaire
  UDP    10.33.16.199:1900      *:*
  SSDPSRV
 [svchost.exe]
  UDP    10.33.16.199:2177      *:*
  QWAVE
 [svchost.exe]
  UDP    10.33.16.199:54354     *:*
  SSDPSRV
 [svchost.exe]
  UDP    127.0.0.1:1900         *:*
  SSDPSRV
 [svchost.exe]
  UDP    127.0.0.1:54355        *:*
  SSDPSRV
 [svchost.exe]
  UDP    127.0.0.1:63840        127.0.0.1:63840
  iphlpsvc
 [svchost.exe]
  UDP    127.0.0.1:64580        *:*
  SharedAccess
 [svchost.exe]
  UDP    192.168.56.1:137       *:*
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.56.1:138       *:*
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.56.1:1900      *:*
  SSDPSRV
 [svchost.exe]
  UDP    192.168.56.1:2177      *:*
  QWAVE
 [svchost.exe]
  UDP    192.168.56.1:54351     *:*
  SSDPSRV
 [svchost.exe]
  UDP    192.168.129.1:137      *:*
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.129.1:138      *:*
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.129.1:1900     *:*
  SSDPSRV
 [svchost.exe]
  UDP    192.168.129.1:2177     *:*
  QWAVE
 [svchost.exe]
  UDP    192.168.129.1:54353    *:*
  SSDPSRV
 [svchost.exe]
  UDP    192.168.137.1:67       *:*
  SharedAccess
 [svchost.exe]
  UDP    192.168.137.1:68       *:*
  SharedAccess
 [svchost.exe]
  UDP    192.168.137.1:137      *:*
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.137.1:138      *:*
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.137.1:1900     *:*
  SSDPSRV
 [svchost.exe]
  UDP    192.168.137.1:2177     *:*
  QWAVE
 [svchost.exe]
  UDP    192.168.137.1:54350    *:*
  SSDPSRV
 [svchost.exe]
  UDP    192.168.232.1:137      *:*
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.232.1:138      *:*
 Impossible d’obtenir les informations de propriétaire
  UDP    192.168.232.1:1900     *:*
  SSDPSRV
 [svchost.exe]
  UDP    192.168.232.1:2177     *:*
  QWAVE
 [svchost.exe]
  UDP    192.168.232.1:54352    *:*
  SSDPSRV
 [svchost.exe]
  UDP    [::]:500               *:*
  IKEEXT
 [svchost.exe]
  UDP    [::]:547               *:*
  SharedAccess
 [svchost.exe]
  UDP    [::]:4500              *:*
  IKEEXT
 [svchost.exe]
  UDP    [::]:5353              *:*
 [msedge.exe]
  UDP    [::]:5353              *:*
 [chrome.exe]
  UDP    [::]:5353              *:*
 [msedge.exe]
  UDP    [::]:5353              *:*
  Dnscache
 [svchost.exe]
  UDP    [::]:5353              *:*
 [chrome.exe]
  UDP    [::]:5353              *:*
 [msedge.exe]
  UDP    [::]:5353              *:*
 [chrome.exe]
  UDP    [::]:5353              *:*
 [chrome.exe]
  UDP    [::]:5353              *:*
 [msedge.exe]
  UDP    [::]:5353              *:*
 [msedge.exe]
  UDP    [::]:5353              *:*
 [chrome.exe]
  UDP    [::]:5355              *:*
  Dnscache
 [svchost.exe]
  UDP    [::]:54357             *:*
  SharedAccess
 [svchost.exe]
  UDP    [::]:54359             *:*
  SharedAccess
 [svchost.exe]
  UDP    [::]:60050             *:*
 [Teams.exe]
  UDP    [::]:60334             *:*
 [Teams.exe]
  UDP    [::]:61159             *:*
  Dnscache
 [svchost.exe]
  UDP    [::1]:1900             *:*
  SSDPSRV
 [svchost.exe]
  UDP    [::1]:54349            *:*
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::506:872:2664:ac97%18]:53  *:*
  SharedAccess
 [svchost.exe]
  UDP    [fe80::506:872:2664:ac97%18]:1900  *:*
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::506:872:2664:ac97%18]:2177  *:*
  QWAVE
 [svchost.exe]
  UDP    [fe80::506:872:2664:ac97%18]:54344  *:*
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::3d98:a1b0:6c0e:ab0c%42]:1900  *:*
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::3d98:a1b0:6c0e:ab0c%42]:2177  *:*
  QWAVE
 [svchost.exe]
  UDP    [fe80::3d98:a1b0:6c0e:ab0c%42]:54345  *:*
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::7086:50d2:b830:2fb3%15]:1900  *:*
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::7086:50d2:b830:2fb3%15]:2177  *:*
  QWAVE
 [svchost.exe]
  UDP    [fe80::7086:50d2:b830:2fb3%15]:54346  *:*
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::d9ec:d417:a35a:46d2%8]:1900  *:*
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::d9ec:d417:a35a:46d2%8]:2177  *:*
  QWAVE
 [svchost.exe]
  UDP    [fe80::d9ec:d417:a35a:46d2%8]:54347  *:*
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::e019:f445:1dc0:5a11%10]:1900  *:*
  SSDPSRV
 [svchost.exe]
  UDP    [fe80::e019:f445:1dc0:5a11%10]:2177  *:*
  QWAVE
 [svchost.exe]
  UDP    [fe80::e019:f445:1dc0:5a11%10]:54348  *:*
  SSDPSRV
 [svchost.exe]
PS C:\Users\Ranvin\netcat-1.11>


dans windows defender avancée nouvelle règle ensuite on configure
PS C:\Users\Ranvin\netcat-1.11> .\nc.exe 192.168.137.240 1026
kjik

 ipconfig
  Serveur DHCP . . . . . . . . . . . . . : 10.33.19.254
 Bail obtenu. . . . . . . . . . . . . . : mercredi 5 octobre 2022 09:05:55
   Bail expirant. . . . . . . . . . . . . : jeudi 6 octobre 2022 09:05:55

   2 DNS 

                google

   PS C:\Users\Ranvin> nslookup google.com
Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    google.com
Addresses:  2a00:1450:4007:808::200e
          216.58.215.46

              ynov

              PS C:\Users\Ranvin> nslookup ynov.com
Serveur :   dns.google
Address:  8.8.8.8

Réponse ne faisant pas autorité :
Nom :    ynov.com
Addresses:  2606:4700:20::681a:be9
          2606:4700:20::ac43:4ae2
          2606:4700:20::681a:ae9
          104.26.10.233
          172.67.74.226
          104.26.11.233

 On trouve donc les adresses ip d'ynov et google.


dnslookup

       
PS C:\Users\Ranvin> nslookup 78.34.2.17
Serveur :   dns.google
Address:  8.8.8.8

Nom :    cable-78-34-2-17.nc.de
Address:  78.34.2.17

*** dns.google ne parvient pas à trouver 104.26.10.233 : Non-existent domain
PS C:\Users\Ranvin> nslookup 231.34.113.12
Serveur :   dns.google
Address:  8.8.8.8

On ne trouve pas de résultat pour l'adresse ip 231.34.113.12 car elle n'est pas associé a un domaine 

On trouve bien "Nom :    cable-78-34-2-17.nc.de" pour l'adresse 78.34.2.17

 