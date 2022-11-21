Serveur VPN
Le but de ce sujet est de monter votre propre serveur VPN.
Il est possiiiible de faire ça avec des VMs, mais c'est vraiment + intéressant si vous avez une serveur distant, disponible sur internet.
Pour ça :

avoir un PC ou une raspberry à la maison, accessible derrière votre box
louer un serveur en ligne (je vous recommande cette option, demandez-moi pour + d'infos)


En plus de monter un serveur VPN, on va en profiter pour vitefé sécuriser la machine qui accueille le VPN.

Vous pouvez utiliser n'importe quel OS GNU/Linux sur la machine distante, mais comme pour les cours, je vous recommande Rocky Linux. PAR CONTRE je vous recommande Rocky 8 (on a utilisé Rocky 9 en cours).

L'idée globale est la suivante :

s'assurer qu'on peut joindre la machine à distance
s'y connecter en SSH
mettre en place quelques bonnes pratiques de sécurité

gestion d'utilisateurs
serveur SSH


installer le serveur VPN sur la machine à distance
s'y connecter avec un client adapté


I. Setup machine distante
Assurez-vous d'être connecté SSH à la machine distante pour la suite.
Vous pouvez sauter cette section si vous voulez, c'est simplement le minimum syndical pour dormir sur ses deux oreilles quand vous avez un serveur en ligne.

1. Utilisateurs
➜ Création d'utilisateur

si ce n'est pas déjà fait, créez-vous un utilisateur (ne pas utiliser root)
assurez-vous qu'il a la possibilité d'utiliser sudo pour accéder aux droits root

sur un système Rocky, il suffit d'ajouter votre utilisateur au groupe wheel





Suivant quel hébergeur vous avez choisi c'est possible que ce soit déjà fait.


2. Serveur SSH

A. Connexion par clé
➜ Génération d'une paire de clé SUR LE CLIENT

SUR LE CLIENT, sur votre PC
je répète, c'est sur le client, sur votre PC
vous allez générer une clé privée, qui sera un fichier sur votre PC, qui remplacera l'utilisation d'un mot de passe
on considère que c'est + sécurisé que l'utilisation d'un mot de passe


# étape à réaliser sur VOTRE PC
$ ssh-keygen -t rsa -b 4096


➜ Assurez-vous d'avoir une connexion sans mot de passe à la machine

Vraiment, faitez-le sinon vous bloquerez votre propre accès à l'étape suivante.


B. SSH Server Hardening
Je vais pas ré-écrire la roue, y'a 10000 articles pour faire ça sur le web. Je vous link un fichier de conf qui contient les clauses importantes à changer dans votre fichier de conf.

Vous pouvez google "ssh server hardening" et/ou me demander pour + de clarté.


II. Serveur VPN
Il existe deux solutions de référence dans le monde open-source/Linux pour mettre en place un serveur VPN : OpenVPN et WireGuard. Je vous laisse faire vos propres recherches si vous voulez une idée de la diff
Là non plus je vais pas ré-écrire la roue, je vous renvoie vers l'excellent guide de Digital Ocean pour mettre en place Wireguard sur une machine Rocky 8.
Si vous suivez ce guide, vous pouvez sautez la partie concernant l'IPv6, pour mieux maîtriser ce que vous faites.

III. Rendu attendu

un fichier markdown sur votre dépôt habituel

dans un dossier tp5
ce fichier markdown rend compte de l'ensemble des étapes pour arriver au serveur VPN fonctionnel

je veux donc voir apparaître toutes les commandes tapées
aussi, tous les fichiers de configuration



Initial Server Setup with Rocky Linux 8

```ssh rocky@51.68.70.139```

```sudo dnf install nano```

```sudo su```

```usermod -aG wheel rocky```

```sur mon terminal ssh-keygen -b 4096``` 

```nano ~/.ssh/authorized_keys```

>clé pub

```ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQDjkVSpFGRCC66BjMLIxWoF+eYk6/DPmjpLsMTA6OLegHAq+IZA2LwaiO64lJEyN2wZtefq3agjcziQEuDPw6NlBsh22ekUl8SEkXReUXE3KGsWaf69DR1ss27+DQ1lKzCh8XtVmVIh7bywrEH5DznOJnlCGihiZ+5ivRZ8dtZy3uorH4N8E60oQWRdsi5YhvzimcfH79FZJNbg4yhDjMoJ3jn3SsWjNYNnH+G15vlGw3j7Z2Czq41LXp0uLrHo7V9UYp43o2b62q58Ssxmer5ad/8lXRFc4KfuWOZBntiq2CqahaLTYncJBVgDj+BRiP6CRvk+0ijhN5BsABQeGkHccW6EZkPdg5RQU7LS2vP4cDEMoJDjguTpiM7Jk67r3oXdKwKMTZF3EmhqJIxO4wXiLNcjTbQcw5lu4Qa9pWSDwsg8e1zgsB2Z33bj88szaRefzvukEfeC/m+ySwgrtf6B2HVunl/zo3nwqFgZQfAxjuA4wR3+Jn13rQZHod82wbOvzu+x6obSKx8mlgzxaClwYI33ftWYtZoQDhmcHib4XMivJjSLLDT/0mo4HTaQtFY2DAqeh3daPDdILtrnllGJmT1D9/tGa6c/uMS/1UqNl9bXD+WHVma3RCsubdJ0dlRRgFvKcwFvz79+Lcq4OQu+g3c8qaprbjPKrK362N9qGw== ranvin@Timothee```

Step 1 — Installing WireGuard and Generating a Key Pair

```sudo dnf install elrepo-release epel-release```

```sudo dnf install kmod-wireguard wireguard-tools```

```wg genkey | sudo tee /etc/wireguard/private.key```
```sudo chmod go= /etc/wireguard/private.key```

```sudo cat /etc/wireguard/private.key | wg pubkey | sudo tee /etc/wireguard/public.key```

```clé privé wg=   4Pc8+RK30KDE+ZEYRZpd1/Li3bi94BwlNlsvSTdReXU=```

```clé pub wg = 4Gv0Ft5dj/BjgrzzhFlKsnE57T6vPZYbLf8hA7SkpzU=```


Step 2 — Choosing IPv4 and IPv6 Addresses

```10.8.0.1/24```



Step 3 — Creating a WireGuard Server Configuration

```sudo nano /etc/wireguard/wg0.conf```

>/etc/wireguard/wg0.conf
[Interface]
PrivateKey = 4Pc8+RK30KDE+ZEYRZpd1/Li3bi94BwlNlsvSTdReXU=
Address = 10.8.0.1/24, 
ListenPort = 51820
SaveConfig = true

Step 4 — Adjusting the WireGuard Server’s Network Configuration

```sudo nano /etc/sysctl.conf```

```net.ipv4.ip_forward=1```

````sudo sysctl -p```

```Output
net.ipv4.ip_forward = 1```


Step 5 — Configuring the WireGuard Server’s Firewall

```dnf install firewalld -y```

```systemctl start firewalld```

```systemctl status firewalld```

>See system logs and 'systemctl status firewalld.service' for details.
[rocky@vps-823031fd ~]$ sudo systemctl start firewalld
[rocky@vps-823031fd ~]$ systemctl status firewalld
● firewalld.service - firewalld - dynamic firewall daemon
   Loaded: loaded (/usr/lib/systemd/system/firewalld.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2022-11-20 18:02:49 UTC; 45s ago
     Docs: man:firewalld(1)
 Main PID: 137517 (firewalld)
    Tasks: 2 (limit: 10836)
   Memory: 25.5M
   CGroup: /system.slice/firewalld.service
           └─137517 /usr/libexec/platform-python -s /usr/sbin/firewalld --nofork --nopid

>Nov 20 18:02:48 vps-823031fd.vps.ovh.net systemd[1]: Starting firewalld - dynamic firewall daemon...
Nov 20 18:02:49 vps-823031fd.vps.ovh.net systemd[1]: Started firewalld - dynamic firewall daemon.
Nov 20 18:02:49 vps-823031fd.vps.ovh.net firewalld[137517]: WARNING: AllowZoneDrifting is enabled. This is considered an insecu>
lines 1-13/13 (END)

```sudo firewall-cmd --zone=public --add-port=51820/udp --permanent```

```sudo firewall-cmd --zone=internal --add-interface=wg0 --permanent```

```sudo firewall-cmd --zone=public --add-rich-rule='rule family=ipv4 source address=10.8.0.0/24 masquerade' --permanent```

```sudo firewall-cmd --reload```

```sudo firewall-cmd --zone=public --list-all```

>public (active)
  target: default
  icmp-block-inversion: no
  interfaces: eth0
  sources:
  services: cockpit dhcpv6-client ssh
  ports: 51820/udp
  protocols:
  forward: no
  masquerade: no
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
        rule family="ipv4" source address="10.8.0.0/24" masquerade

```sudo firewall-cmd --zone=internal --list-interfaces```


```wg0```

Step 6 — Starting the WireGuard Server

```sudo systemctl enable wg-quick@wg0.service```

```Created symlink /etc/systemd/system/multi-user.target.wants/wg-quick@wg0.service → /usr/lib/systemd/system/wg-quick@.service.```

```sudo systemctl start wg-quick@wg0.service```

```sudo systemctl status wg-quick@wg0.service```

>● wg-quick@wg0.service - WireGuard via wg-quick(8) for wg0
   Loaded: loaded (/usr/lib/systemd/system/wg-quick@.service; enabled; vendor preset: disabled)
   Active: active (exited) since Sun 2022-11-20 18:35:46 UTC; 10s ago
     Docs: man:wg-quick(8)
           man:wg(8)
           https://www.wireguard.com/
           https://www.wireguard.com/quickstart/
           https://git.zx2c4.com/wireguard-tools/about/src/man/wg-quick.8
           https://git.zx2c4.com/wireguard-tools/about/src/man/wg.8
  Process: 4776 ExecStart=/usr/bin/wg-quick up wg0 (code=exited, status=0/SUCCESS)
 Main PID: 4776 (code=exited, status=0/SUCCESS)

>Nov 20 18:35:46 vps-823031fd.vps.ovh.net systemd[1]: Starting WireGuard via wg-quick(8) for wg0...
Nov 20 18:35:46 vps-823031fd.vps.ovh.net wg-quick[4776]: [#] ip link add wg0 type wireguard
Nov 20 18:35:46 vps-823031fd.vps.ovh.net wg-quick[4776]: [#] wg setconf wg0 /dev/fd/63
Nov 20 18:35:46 vps-823031fd.vps.ovh.net wg-quick[4776]: [#] ip -4 address add 10.8.0.1/24 dev wg0
Nov 20 18:35:46 vps-823031fd.vps.ovh.net wg-quick[4776]: [#] ip link set mtu 1420 up dev wg0
Nov 20 18:35:46 vps-823031fd.vps.ovh.net systemd[1]: Started WireGuard via wg-quick(8) for wg0.

Step 7 — Configuring a WireGuard Peer

```sudo dnf install elrepo-release epel-release```

```sudo dnf install kmod-wireguard wireguard-tools```

```wireguard windows 11 clé pub 1iC5nwZfbQ8MNQ+ssIat0CUn8b7a0N1qqeEWta8MPCY=```

```PrivateKey = gMGJ+VsMD9s0wg4KpxJtIJbNImpZDKwb/qs8mRQO/lw=```

```sudo wg set wg0 peer 1iC5nwZfbQ8MNQ+ssIat0CUn8b7a0N1qqeEWta8MPCY= allowed-ips 10.8.0.2```


Step 8 — Adding the Peer’s Public Key to the WireGuard Server

```sudo wg```

>[rocky@vps-823031fd ~]$ sudo wg
interface: wg0
  public key: 4Gv0Ft5dj/BjgrzzhFlKsnE57T6vPZYbLf8hA7SkpzU=
  private key: (hidden)
  listening port: 51820

>peer: 1iC5nwZfbQ8MNQ+ssIat0CUn8b7a0N1qqeEWta8MPCY=

Step 9 — Connecting the WireGuard Peer to the Tunnel

>[Interface]
PrivateKey = gMGJ+VsMD9s0wg4KpxJtIJbNImpZDKwb/qs8mRQO/lw=
Address = 10.8.0.2/24
[Peer]
PublicKey = 4Gv0Ft5dj/BjgrzzhFlKsnE57T6vPZYbLf8hA7SkpzU=
AllowedIPs = 10.8.0.0/24
Endpoint = 51.68.70.139:51820


```ping -c 1 10.8.0.1```

```>Envoi d’une requête 'Ping'  10.8.0.1 avec 32 octets de données :
Réponse de 10.8.0.1 : octets=32 temps=45 ms TTL=64
Réponse de 10.8.0.1 : octets=32 temps=46 ms TTL=64
Réponse de 10.8.0.1 : octets=32 temps=47 ms TTL=64
Réponse de 10.8.0.1 : octets=32 temps=46 ms TTL=64
Statistiques Ping pour 10.8.0.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 43ms, Maximum = 48ms, Moyenne = 46ms
  
  ```sudo nano /etc/ssh/sshd_config```
  
    >PermitRootLogin no